---
title: 應用程式部署的安全性建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, applications
- best practices, applications
- best practices, security
- security, best practices
- applications, best practices
- applications, security
ms.assetid: 77902140-8b4c-437c-af4c-10a12b3bc950
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0402ef23de70150d541dfd672d2af7efe3a924
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231950"
---
# <a name="application-deployment-security-recommendations"></a><span data-ttu-id="c3a05-102">應用程式部署的安全性建議</span><span class="sxs-lookup"><span data-stu-id="c3a05-102">Application Deployment Security Recommendations</span></span>
<span data-ttu-id="c3a05-103">以下是將 BizTalk 應用程式部署在環境中的指導方針：</span><span class="sxs-lookup"><span data-stu-id="c3a05-103">The following are guidelines for deploying BizTalk applications in your environment:</span></span>  
  
-   <span data-ttu-id="c3a05-104">當應用程式匯出至 .msi 檔案時，所有的判別存取控制清單 (DACL) 都會從檔案和資料夾中移除。</span><span class="sxs-lookup"><span data-stu-id="c3a05-104">All discretionary access control lists (DACLs) are removed from files and folders when an application is exported into an .msi file.</span></span> <span data-ttu-id="c3a05-105">從 .msi 檔案安裝應用程式之後，您必須重新設定檔案和資料夾的所有安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c3a05-105">After installing an application from the .msi file, you must reconfigure all security settings on the files and folders.</span></span>  
  
-   <span data-ttu-id="c3a05-106">基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。</span><span class="sxs-lookup"><span data-stu-id="c3a05-106">For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="c3a05-107">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="c3a05-107">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="c3a05-108">您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。</span><span class="sxs-lookup"><span data-stu-id="c3a05-108">You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.</span></span> <span data-ttu-id="c3a05-109">如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-109">For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="c3a05-110">另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-110">See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span> <span data-ttu-id="c3a05-111">如需繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-111">For more information about binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
-   <span data-ttu-id="c3a05-112">部署或解除部署屬性結構描述可能會公開機密資料，而之後可能會在追蹤期間公開機密資訊。</span><span class="sxs-lookup"><span data-stu-id="c3a05-112">Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking.</span></span> <span data-ttu-id="c3a05-113">每當部署或解除部署包含屬性結構描述的組件時，事件檢視器會將事件記錄在 Windows 應用程式事件記錄中。</span><span class="sxs-lookup"><span data-stu-id="c3a05-113">Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log.</span></span> <span data-ttu-id="c3a05-114">您應檢查事件日誌檔中的這些訊息，確保所有組件部署活動都符合任何機密資料的原則</span><span class="sxs-lookup"><span data-stu-id="c3a05-114">You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data.</span></span>  
  
     <span data-ttu-id="c3a05-115">在「事件日誌」中產生的部署訊息為：</span><span class="sxs-lookup"><span data-stu-id="c3a05-115">The message generated to the Event Log for deployment is:</span></span>  
  
     <span data-ttu-id="c3a05-116">**使用者"{1} 」 部署的組件"{0}"包含屬性結構描述。**</span><span class="sxs-lookup"><span data-stu-id="c3a05-116">**The user "{1}" deployed the assembly "{0}" containing property schemas.**</span></span>  
  
     <span data-ttu-id="c3a05-117">對解除部署之事件記錄產生的訊息為：</span><span class="sxs-lookup"><span data-stu-id="c3a05-117">The message generated to the Event Log for undeployment is:</span></span>  
  
     <span data-ttu-id="c3a05-118">**使用者"{1}"已解除部署組件"{0}"包含屬性結構描述。**</span><span class="sxs-lookup"><span data-stu-id="c3a05-118">**The user "{1}" undeployed the assembly "{0}" containing property schemas.**</span></span>  
  
-   <span data-ttu-id="c3a05-119">如果應用程式包含虛擬目錄，請注意虛擬目錄上的安全性設定，就是在應用程式匯出期間產生 .msi 檔案時生效的那些安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c3a05-119">If the application includes a virtual directory, be aware that the security settings on the virtual directory are those in effect when the .msi file is generated during application export.</span></span> <span data-ttu-id="c3a05-120">如果您將應用程式部署到實際執行環境，則在匯出應用程式之前，應該驗證設定是否符合安全性需求。</span><span class="sxs-lookup"><span data-stu-id="c3a05-120">If you are deploying an application into a production environment, before exporting the application, you should verify that the settings meet your security requirements.</span></span>  
  
     <span data-ttu-id="c3a05-121">如果您部署包含虛擬目錄的應用程式，而且目的地環境中已經有虛擬目錄存在，則現有虛擬目錄上的安全性設定將會生效。</span><span class="sxs-lookup"><span data-stu-id="c3a05-121">If, however, you deploy an application that includes a virtual directory, and the virtual directory already exists in the destination environment, the security settings on the existing virtual directory will be in effect.</span></span> <span data-ttu-id="c3a05-122">這些設定不會為了要與您部署之虛擬目錄上的設定相符而變更。</span><span class="sxs-lookup"><span data-stu-id="c3a05-122">They are not changed to match those on the virtual directory you are deploying.</span></span> <span data-ttu-id="c3a05-123">您應該確認現有虛擬目錄的安全性設定是否符合安全性需求。</span><span class="sxs-lookup"><span data-stu-id="c3a05-123">You should verify that the security settings on the existing virtual directory meet your requirements.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="c3a05-124">如果虛擬目錄使用的是 HTTPS (超文字安全傳輸通訊協定) 通訊協定，則在匯出期間不會保留其安全性設定，而且在匯入時，虛擬目錄會繼承根目錄的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c3a05-124">If the virtual directory uses the HTTPS (Hypertext Transfer Protocol over Secure Socket Layer) protocol, its security settings are not preserved during export, and when it is imported, the virtual directory will inherit the security settings of the root.</span></span> <span data-ttu-id="c3a05-125">您應該驗證這些安全性設定是否符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="c3a05-125">You should verify that the security settings meet your requirements.</span></span>  
  
-   <span data-ttu-id="c3a05-126">如果在匯入應用程式時為 Web 服務指定的應用程式集區不存在，則會使用預設的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="c3a05-126">If the application pool specified for a Web service does not exist when you import an application, the default application pool is used.</span></span> <span data-ttu-id="c3a05-127">預設應用程式集區的安全性設定可能不適合您的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="c3a05-127">The security settings on the default application pool may not be appropriate for your requirements.</span></span> <span data-ttu-id="c3a05-128">因此，建議您在匯入應用程式之前，先建立應用程式集區並設定適當的安全性設定，或驗證預設應用程式集區的安全性設定是否適當。</span><span class="sxs-lookup"><span data-stu-id="c3a05-128">We therefore recommend that you either create the application pool and configure the appropriate security settings before importing the application, or verify that the settings on the default application pool are appropriate.</span></span>  
  
-   <span data-ttu-id="c3a05-129">確定您信任所部署 Windows Installer (.msi) 檔案的來源，以避免可能由惡意的 .msi 檔案建立者造成的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="c3a05-129">Ensure that you trust the source of the Windows Installer (.msi) files that you deploy to avoid security issues that can be created by malicious .msi file creators.</span></span> <span data-ttu-id="c3a05-130">如需詳細資訊，請參閱[安全性和 Windows Installer](../core/security-and-windows-installer.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-130">For more information, see [Security and Windows Installer](../core/security-and-windows-installer.md).</span></span>  
  
-   <span data-ttu-id="c3a05-131">確定您具有部署應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="c3a05-131">Ensure you have the permissions to deploy applications.</span></span> <span data-ttu-id="c3a05-132">如需詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-132">For more information, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="c3a05-133">確定只有 BizTalk 系統管理員才能存取組件、繫結檔案和原則檔案，因為它們可能包含重要的商務資料，例如連線和組態資訊。</span><span class="sxs-lookup"><span data-stu-id="c3a05-133">Ensure that only BizTalk administrators have access to the assemblies, binding files, and policy files, as they may contain critical business data such as connectivity and configuration information.</span></span> <span data-ttu-id="c3a05-134">如果您透過網路共用部署應用程式，請對網路共用設定判別存取控制清單 (DACL)，如此只有 BizTalk 系統管理員才能檢視其內容。</span><span class="sxs-lookup"><span data-stu-id="c3a05-134">If you deploy applications through a network share, configure the discretionary access control list (DACL) on the network share so that only BizTalk administrators can view its contents.</span></span> <span data-ttu-id="c3a05-135">如需群組和使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-135">For more information about group and user accounts, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="c3a05-136">當您執行部署作業時，BizTalk Server 會與 BizTalk 管理資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="c3a05-136">When you perform deployment operations, BizTalk Server communicates with the BizTalk Management database.</span></span> <span data-ttu-id="c3a05-137">如果它們之間有防火牆存在，您必須在處理、服務和資料網域之間的防火牆開啟適當的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c3a05-137">If a firewall exists between them, you must open the appropriate ports on the firewall between the processing, services, and data domains.</span></span> <span data-ttu-id="c3a05-138">如需詳細資訊，請參閱[所需的 BizTalk Server 的連接埠](../core/required-ports-for-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a05-138">For more information, see [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="c3a05-139">如果您指向可能包含機密資料之組件、繫結檔案或其他資源檔案的遠端位置，應該考慮來源電腦和執行部署的電腦之間的網路安全性。</span><span class="sxs-lookup"><span data-stu-id="c3a05-139">If you point to a remote location for an assembly, binding file, or other resource file that may contain sensitive data, you should consider network security between source computer and the computer from which you are running deployment.</span></span> <span data-ttu-id="c3a05-140">如果這兩台電腦之間的網路未完全隔絕潛在攻擊者，您應該將目標檔案複製到卸除式媒體，再將它從卸除式媒體複製到執行部署的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c3a05-140">If the network between these two computers is not fully isolated from potential attackers, you should copy the target file to removable media and physically transport it to the computer where you run deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a05-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3a05-141">See Also</span></span>  
 [<span data-ttu-id="c3a05-142">應用程式部署的安全性考量</span><span class="sxs-lookup"><span data-stu-id="c3a05-142">Security Considerations for Application Deployment</span></span>](../core/security-considerations-for-application-deployment.md)