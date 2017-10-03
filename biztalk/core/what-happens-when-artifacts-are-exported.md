---
title: "匯出成品時，會發生什麼情況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting, artifacts
- artifacts, exporting
ms.assetid: accc9a81-01fb-4da7-a5a5-167835d393a2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d92a65889ea642706ae5c51849748fd8ad085a02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-artifacts-are-exported"></a><span data-ttu-id="130b5-102">匯出成品時所產生的狀況</span><span class="sxs-lookup"><span data-stu-id="130b5-102">What Happens When Artifacts Are Exported</span></span>
<span data-ttu-id="130b5-103">本主題描述匯出成品時所產生的狀況。</span><span class="sxs-lookup"><span data-stu-id="130b5-103">This topic describes what happens when you export artifacts.</span></span> <span data-ttu-id="130b5-104">匯出成品的方法有三種，本主題將涵蓋這三種方法：</span><span class="sxs-lookup"><span data-stu-id="130b5-104">There are three ways to export artifacts, which are covered in this topic:</span></span>  
  
-   <span data-ttu-id="130b5-105">將 BizTalk 應用程式及其成品匯出到 BizTalk .msi (Windows Installer) 檔案</span><span class="sxs-lookup"><span data-stu-id="130b5-105">Exporting a BizTalk application and its artifacts into a BizTalk .msi (Windows Installer) file</span></span>  
  
-   <span data-ttu-id="130b5-106">將原則匯出到 .xml 檔案</span><span class="sxs-lookup"><span data-stu-id="130b5-106">Exporting a policy into an .xml file</span></span>  
  
-   <span data-ttu-id="130b5-107">將繫結匯出到 .xml 檔案</span><span class="sxs-lookup"><span data-stu-id="130b5-107">Exporting bindings into an .xml file</span></span>  
  
## <a name="exporting-a-biztalk-application"></a><span data-ttu-id="130b5-108">匯出 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="130b5-108">Exporting a BizTalk application</span></span>  
 <span data-ttu-id="130b5-109">當您匯出 BizTalk 應用程式以及其所包含的成品時，應用程式組態資訊和成品資料會匯出到 BizTalk .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="130b5-109">When you export a BizTalk application and the artifacts it contains, application configuration information and artifact data is exported into a BizTalk .msi file.</span></span> <span data-ttu-id="130b5-110">大部分的成品資料都是從 BizTalk 管理資料庫匯出，但是有下列幾個例外：</span><span class="sxs-lookup"><span data-stu-id="130b5-110">Most artifact data is exported from the BizTalk Management database, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="130b5-111">原則資料會從該群組的規則引擎資料庫匯出。</span><span class="sxs-lookup"><span data-stu-id="130b5-111">Policy data is exported from the Rule Engine database for the group.</span></span>  
  
-   <span data-ttu-id="130b5-112">虛擬目錄資料如果未存在於管理資料庫中，則會從 Internet Information Services (IIS) Metabase 匯出。</span><span class="sxs-lookup"><span data-stu-id="130b5-112">Virtual directory data is exported from the Internet Information Services (IIS) metabase if it does not exist in the Management database.</span></span> <span data-ttu-id="130b5-113">虛擬目錄尚未明確加入至應用程式時就會發生的情況 (如所述[如何將虛擬目錄新增至應用程式](../core/how-to-add-a-virtual-directory-to-an-application.md)) 或是具有不到此群組從.msi 檔案匯入應用程式從另一個 BizTalk 群組匯出。</span><span class="sxs-lookup"><span data-stu-id="130b5-113">This will be the case when the virtual directory has not been explicitly added to the application (as described in [How to Add a Virtual Directory to an Application](../core/how-to-add-a-virtual-directory-to-an-application.md)) or the application has not been imported into this group from an .msi file that was exported from another BizTalk group.</span></span>  
  
-   <span data-ttu-id="130b5-114">憑證資料如果未存在於管理資料庫中，則會從本機電腦上的「其他人」憑證存放區匯出。</span><span class="sxs-lookup"><span data-stu-id="130b5-114">Certificate data is exported from the Other People certificate store on the local computer, if it does not exist in the Management database.</span></span> <span data-ttu-id="130b5-115">當憑證尚未明確加入至應用程式就會發生的情況 (如所述[如何將憑證新增至應用程式](../core/how-to-add-a-certificate-to-an-application.md)) 或是具有不到這個群組仍在.msi 檔案匯入應用程式從另一個 BizTalk 群組匯出。</span><span class="sxs-lookup"><span data-stu-id="130b5-115">This will be the case when the certificate has not been explicitly added to the application (as described in [How to Add a Certificate to an Application](../core/how-to-add-a-certificate-to-an-application.md)) or the application has not been imported into this group from an .msi file that was exported from another BizTalk group.</span></span> <span data-ttu-id="130b5-116">當您使用具有相關憑證的接收埠匯出應用程式時，將會匯出憑證。</span><span class="sxs-lookup"><span data-stu-id="130b5-116">Certificates are exported when you export an application with a receive port that has a certificate associated with it.</span></span> <span data-ttu-id="130b5-117">匯出時將會從憑證中移除私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="130b5-117">Private keys are removed from certificates on export.</span></span>  
  
 <span data-ttu-id="130b5-118">您可以使用這個 .msi 檔案，將應用程式的成品 (包括其所有資料) 匯入到另一個 BizTalk 群組的應用程式。</span><span class="sxs-lookup"><span data-stu-id="130b5-118">You can use this .msi file to import the application's artifacts, including all of their data, into an application in another BizTalk group.</span></span> <span data-ttu-id="130b5-119">您也可以使用此 .msi 檔案，在電腦上安裝此應用程式。</span><span class="sxs-lookup"><span data-stu-id="130b5-119">You can also use this .msi file to install the application on a computer.</span></span>  
  
## <a name="exporting-a-policy"></a><span data-ttu-id="130b5-120">匯出原則</span><span class="sxs-lookup"><span data-stu-id="130b5-120">Exporting a policy</span></span>  
 <span data-ttu-id="130b5-121">當您使用管理主控台匯出 BizTalk 群組或應用程式的原則時，它會產生包含原則資訊的 .xml 原則檔案。</span><span class="sxs-lookup"><span data-stu-id="130b5-121">When you use the administration console to export a policy for either a BizTalk group or application, it generates an .xml policy file containing the policy information.</span></span> <span data-ttu-id="130b5-122">您可以將此原則檔案匯入另一個 BizTalk 群組，以便在該處建立此原則，好讓該群組中的應用程式可以使用它。</span><span class="sxs-lookup"><span data-stu-id="130b5-122">You can import this policy file into another BizTalk group to create the policy there, so that applications in the group can use it.</span></span> <span data-ttu-id="130b5-123">您也可以使用 BTSTask 匯出應用程式的原則資訊，</span><span class="sxs-lookup"><span data-stu-id="130b5-123">You can also export policy information for an application by using BTSTask.</span></span> <span data-ttu-id="130b5-124">但是，BTSTask 並沒有可匯出原則 .xml 檔案的命令。</span><span class="sxs-lookup"><span data-stu-id="130b5-124">BTSTask, however, does not have a command to export a policy .xml file.</span></span> <span data-ttu-id="130b5-125">您可改為匯出只包含此原則的應用程式 .msi 檔案，</span><span class="sxs-lookup"><span data-stu-id="130b5-125">Instead, you can export an application .msi file that contains only the policy.</span></span> <span data-ttu-id="130b5-126">然後您可以將此 .msi 檔案匯入到另一個群組的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="130b5-126">You can then import the .msi file into an application in another group.</span></span>  
  
## <a name="exporting-bindings"></a><span data-ttu-id="130b5-127">匯出繫結</span><span class="sxs-lookup"><span data-stu-id="130b5-127">Exporting bindings</span></span>  
 <span data-ttu-id="130b5-128">您可以使用管理主控台或 BTSTask 匯出 BizTalk 群組、應用程式或組件的繫結。</span><span class="sxs-lookup"><span data-stu-id="130b5-128">You can use either the administration console or BTSTask to export bindings for a BizTalk group, application, or assembly.</span></span> <span data-ttu-id="130b5-129">當您這樣做時，BizTalk Server 會產生一個 .xml 檔案，其中包含此群組、應用程式或組件的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="130b5-129">When you do this, BizTalk Server generates an .xml file containing the binding information for the group, application, or assembly.</span></span> <span data-ttu-id="130b5-130">當您匯出繫結時，也可以一併匯出此群組的全域合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="130b5-130">When you export bindings, you can also export global party information for the group.</span></span> <span data-ttu-id="130b5-131">之後您可以將此繫結檔案加入到應用程式，或是將它匯入到 BizTalk 群組或應用程式。</span><span class="sxs-lookup"><span data-stu-id="130b5-131">You can then either add this binding file to an application or import it into a BizTalk group or application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130b5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="130b5-132">See Also</span></span>  
 <span data-ttu-id="130b5-133">[會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="130b5-133">[What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md) </span></span>  
 <span data-ttu-id="130b5-134">[匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="130b5-134">[Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md) </span></span>  
 <span data-ttu-id="130b5-135">[匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="130b5-135">[Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md) </span></span>  
 [<span data-ttu-id="130b5-136">如何將繫結檔案新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="130b5-136">How to Add a Binding File to an Application</span></span>](../core/how-to-add-a-binding-file-to-an-application2.md)