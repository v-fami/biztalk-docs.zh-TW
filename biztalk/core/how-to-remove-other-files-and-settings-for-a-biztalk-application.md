---
title: 如何移除其他檔案和設定 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], deleting settings
- managing [applications], deleting files
- undeploying, settings
- applications, undeploying
- undeploying, files
ms.assetid: b947831a-c988-435c-92ec-45f3fd6967de
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a453af859b36a0fce6cbcbc3da6cce68114a6972
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004671"
---
# <a name="how-to-remove-other-files-and-settings-for-a-biztalk-application"></a><span data-ttu-id="8ea17-102">如何移除 BizTalk 應用程式的其他檔案和設定</span><span class="sxs-lookup"><span data-stu-id="8ea17-102">How to Remove Other Files and Settings for a BizTalk Application</span></span>
<span data-ttu-id="8ea17-103">本主題描述如何移除可能不會移除當您解除安裝應用程式的 BizTalk 應用程式的檔案和設定 (見[如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md))。</span><span class="sxs-lookup"><span data-stu-id="8ea17-103">This topic describes how to remove files and settings for a BizTalk application that may not be removed when you uninstall the application (which is described in [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)).</span></span> <span data-ttu-id="8ea17-104">例如，除非應用程式包含可以在解除安裝時移除憑證、COM 和 COM+ 登錄項目以及 COM 檔案的後置處理指令碼，否則這些項目都不會移除。</span><span class="sxs-lookup"><span data-stu-id="8ea17-104">For example, certificates, COM and COM+ registry entries, and COM files are not removed unless the application included a post-processing script that removed them on uninstallation.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8ea17-105">然後再移除任何共用的項目，請確定沒有其他應用程式使用它們，或應用程式將無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="8ea17-105">Before removing any shared items, make certain that no other applications are using them, or the applications will not function correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ea17-106">建議您使用後置處理指令碼自動執行這項移除作業。</span><span class="sxs-lookup"><span data-stu-id="8ea17-106">We recommend that you automate this removal by using a post-processing script.</span></span> <span data-ttu-id="8ea17-107">如需詳細資訊，請參閱 <<c0> [ 使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea17-107">For more information, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
- <span data-ttu-id="8ea17-108">**刪除憑證。**</span><span class="sxs-lookup"><span data-stu-id="8ea17-108">**Delete Certificates.**</span></span> <span data-ttu-id="8ea17-109">有兩種方法可以從憑證存放區刪除憑證：使用憑證管理員 (certmgr.exe) 命令列工具或憑證嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="8ea17-109">There are two ways to delete certificates from the certificate store: by using the Certificate Manager (certmgr.exe) command-line tool or the Certificates snap-in.</span></span> <span data-ttu-id="8ea17-110">Certmgr.exe 會隨.NET SDK 中，也就是其中一個的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝必要條件。</span><span class="sxs-lookup"><span data-stu-id="8ea17-110">Certmgr.exe is installed with the .NET SDK, which is one of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation prerequisites.</span></span> <span data-ttu-id="8ea17-111">您可以手動執行 certmgr.exe，也可以從後置處理指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="8ea17-111">You can run certmgr.exe manually, or you can run it from a post-processing script.</span></span> <span data-ttu-id="8ea17-112">如需使用 certmgr.exe 的詳細資訊，請參閱[憑證管理員工具 (certmgr.exe)](http://go.microsoft.com/fwlink/?LinkId=56198)羰 Microsoft 寍鯚。</span><span class="sxs-lookup"><span data-stu-id="8ea17-112">For more information about using certmgr.exe, see [Certificate Manager Tool (certmgr.exe)](http://go.microsoft.com/fwlink/?LinkId=56198) at the Microsoft Web site.</span></span>  
  
   <span data-ttu-id="8ea17-113">憑證嵌入式管理單元包含在 Windows Server 2008 和 Windows Vista 中。</span><span class="sxs-lookup"><span data-stu-id="8ea17-113">The Certificates snap-in is included in both Windows Server 2008 and Windows Vista.</span></span> <span data-ttu-id="8ea17-114">若要刪除憑證，請依照作業系統說明中「啟動憑證嵌入式管理單元」所述，開啟嵌入式管理單元，然後再依憑證說明中「刪除憑證」所述，刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="8ea17-114">To delete a certificate, open the snap-in, as described in "Starting the Certificates snap-in" in Help for your operating system, and then delete the certificate as described in "Delete a certificate" in Certificates Help.</span></span>  
  
- <span data-ttu-id="8ea17-115">**從 Windows 登錄中移除組件。**</span><span class="sxs-lookup"><span data-stu-id="8ea17-115">**Remove assemblies from the Windows Registry.**</span></span> <span data-ttu-id="8ea17-116">若要從 Windows 登錄移除 .NET 和 BizTalk 組件，請使用 .NET SDK 中隨附的 regsvcs 或 regasm，.NET SDK 是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的其中一項必要安裝條件。</span><span class="sxs-lookup"><span data-stu-id="8ea17-116">To remove .NET and BizTalk assemblies from the Windows registry, use regsvcs or regasm, which are included with the .NET SDK, which is one of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation prerequisites.</span></span> <span data-ttu-id="8ea17-117">如需參考資訊，請參閱[.NET 服務安裝工具 (Regsvcs.exe)](http://go.microsoft.com/fwlink/?LinkId=56199)並[組件登錄工具 (Regasm.exe)](http://go.microsoft.com/fwlink/?LinkId=56200)羰 Microsoft 寍鯚。</span><span class="sxs-lookup"><span data-stu-id="8ea17-117">For reference information, see [.NET Services Installation Tool (Regsvcs.exe)](http://go.microsoft.com/fwlink/?LinkId=56199) and [Assembly Registration Tool (Regasm.exe)](http://go.microsoft.com/fwlink/?LinkId=56200) at the Microsoft Web site.</span></span>  
  
- <span data-ttu-id="8ea17-118">**從 Windows 登錄中移除 COM 元件。**</span><span class="sxs-lookup"><span data-stu-id="8ea17-118">**Remove COM components from the Windows Registry.**</span></span> <span data-ttu-id="8ea17-119">若要從 Windows 登錄中移除 COM 元件，請使用 regsvr32。</span><span class="sxs-lookup"><span data-stu-id="8ea17-119">To remove COM components from the Windows Registry, use regsvr32.</span></span> <span data-ttu-id="8ea17-120">如需參考資訊，請參閱作業系統「說明」中的「Regsvr32」。</span><span class="sxs-lookup"><span data-stu-id="8ea17-120">For reference information, see "Regsvr32" in Help for your operating system.</span></span> <span data-ttu-id="8ea17-121">此工具包含在 Windows Server 2008 和 Windows Vista Professional 中。</span><span class="sxs-lookup"><span data-stu-id="8ea17-121">This tool is included in both Windows Server 2008 and Windows Vista Professional.</span></span>  
  
- <span data-ttu-id="8ea17-122">**解除安裝組件從全域組件快取 (GAC)。**</span><span class="sxs-lookup"><span data-stu-id="8ea17-122">**Uninstall assemblies from the global assembly cache (GAC).**</span></span> <span data-ttu-id="8ea17-123">組件不會自動從 GAC 中解除安裝。</span><span class="sxs-lookup"><span data-stu-id="8ea17-123">Assemblies are not automatically uninstalled from the GAC.</span></span> <span data-ttu-id="8ea17-124">您可以使用手動方式或使用指令碼從 GAC 中解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="8ea17-124">You can uninstall an assembly from the GAC manually or by using a script.</span></span> <span data-ttu-id="8ea17-125">如需詳細資訊，請參閱 <<c0> [ 如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)。</span><span class="sxs-lookup"><span data-stu-id="8ea17-125">For more information, see [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8ea17-126">必要條件</span><span class="sxs-lookup"><span data-stu-id="8ea17-126">Prerequisites</span></span>  
 <span data-ttu-id="8ea17-127">若要移除本主題中所描述的檔案和設定，您必須依據想要移除的項目，使用具有 Windows 登錄、GAC 或憑證存放區之寫入權限的身分登入。</span><span class="sxs-lookup"><span data-stu-id="8ea17-127">To remove the files and settings described in this topic, you must be logged on with Write permissions on the Windows Registry, the GAC, or the certificate store, depending on what you want to remove.</span></span> <span data-ttu-id="8ea17-128">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea17-128">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea17-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ea17-129">See Also</span></span>  
 <span data-ttu-id="8ea17-130">[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="8ea17-130">[Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="8ea17-131">如何解除安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="8ea17-131">How to Uninstall a BizTalk Application</span></span>](../core/how-to-uninstall-a-biztalk-application.md)