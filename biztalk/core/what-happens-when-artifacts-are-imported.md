---
title: "匯入成品時，會發生什麼情況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing, artifacts
- artifacts, importing
ms.assetid: a83957df-6e16-419a-b693-87985b498cc4
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa252b520f985667820861403a46d39c8527ea07
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="what-happens-when-artifacts-are-imported"></a><span data-ttu-id="ba78b-102">匯入成品時所產生的狀況</span><span class="sxs-lookup"><span data-stu-id="ba78b-102">What Happens When Artifacts Are Imported</span></span>
<span data-ttu-id="ba78b-103">本主題描述匯入成品時所產生的狀況。</span><span class="sxs-lookup"><span data-stu-id="ba78b-103">This topic describes what happens to artifacts when they are imported.</span></span> <span data-ttu-id="ba78b-104">匯入成品的方法有三種，本主題將涵蓋這三種方法：</span><span class="sxs-lookup"><span data-stu-id="ba78b-104">There are three ways to import artifacts, which are covered in this topic:</span></span>  
  
-   <span data-ttu-id="ba78b-105">將 BizTalk .msi 檔案中的成品匯入 BizTalk 群組或應用程式中</span><span class="sxs-lookup"><span data-stu-id="ba78b-105">Importing artifacts in a BizTalk .msi file into a BizTalk group or application</span></span>  
  
-   <span data-ttu-id="ba78b-106">將 .xml 原則檔案匯入 BizTalk 群組中</span><span class="sxs-lookup"><span data-stu-id="ba78b-106">Importing an .xml policy file into a BizTalk group</span></span>  
  
-   <span data-ttu-id="ba78b-107">將繫結檔案匯入 BizTalk 群組或應用程式中</span><span class="sxs-lookup"><span data-stu-id="ba78b-107">Importing a binding file into a BizTalk group or application</span></span>  
  
## <a name="importing-a-biztalk-msi-file"></a><span data-ttu-id="ba78b-108">匯入 BizTalk .msi 檔案</span><span class="sxs-lookup"><span data-stu-id="ba78b-108">Importing a BizTalk .msi file</span></span>  
 <span data-ttu-id="ba78b-109">當您將 BizTalk .msi 檔案匯入 BizTalk 群組或應用程式中時，BizTalk Server 會處理其所包含的成品，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ba78b-109">When you import a BizTalk .msi file into a BizTalk group or application, BizTalk Server handles the artifacts that it contains as follows:</span></span>  
  
-   <span data-ttu-id="ba78b-110">如果您在匯入期間加入從這個應用程式到此群組中其他應用程式的任何參考，則此參考會加入到 BizTalk 管理資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ba78b-110">If during import you added any references from this application to other applications in the group, the reference is added to the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="ba78b-111">如果您指定這個選項，則應用程式中的現有成品會遭到 .msi 檔案中有相同完整名稱和版本號碼 (如果適用的話) 的成品所覆寫。</span><span class="sxs-lookup"><span data-stu-id="ba78b-111">If you specified this option, existing artifacts in the application are overwritten by artifacts in the .msi file that have the same full name and version number (if applicable).</span></span>  
  
-   <span data-ttu-id="ba78b-112">如果已將繫結檔案加入到應用程式中，而且您在匯入期間選取其目標環境，則會套用這些繫結。</span><span class="sxs-lookup"><span data-stu-id="ba78b-112">If binding files have been added to the application, and you select their target environment during import, the bindings are applied.</span></span>  
  
-   <span data-ttu-id="ba78b-113">將會執行設定為在匯入時要執行的前置或後置處理指令碼。</span><span class="sxs-lookup"><span data-stu-id="ba78b-113">Pre- or post-processing scripts that are configured to run on import will run.</span></span>  
  
-   <span data-ttu-id="ba78b-114">以檔案為基礎的成品資料會序列化並儲存在 BizTalk 管理資料庫中，</span><span class="sxs-lookup"><span data-stu-id="ba78b-114">File-based artifact data is serialized and stored in the BizTalk Management database.</span></span> <span data-ttu-id="ba78b-115">這包括組件、虛擬目錄、檔案、指令碼、憑證和 BAM 成品的資料。</span><span class="sxs-lookup"><span data-stu-id="ba78b-115">This includes data for assemblies, virtual directories, files, scripts, certificates, and BAM artifacts.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ba78b-116">基於安全性理由，當匯出私密金鑰時，會從每一個憑證中移除它。</span><span class="sxs-lookup"><span data-stu-id="ba78b-116">For security reasons, the private key is removed from each certificate when it is exported.</span></span> <span data-ttu-id="ba78b-117">因此，不會有任何私密金鑰儲存在 BizTalk 管理資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ba78b-117">Therefore, no private keys are stored in the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="ba78b-118">原則資料會儲存在規則引擎資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ba78b-118">Policy data is stored in the Rule Engine database.</span></span>  
  
-   <span data-ttu-id="ba78b-119">BAM 成品會儲存在 BAM 主要匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ba78b-119">BAM artifacts are stored in the BAM Primary Import database.</span></span> <span data-ttu-id="ba78b-120">BAM 定義會加以部署。</span><span class="sxs-lookup"><span data-stu-id="ba78b-120">BAM definitions are deployed.</span></span>  
  
-   <span data-ttu-id="ba78b-121">已設定 [新增至 MSI 檔案匯入上的全域組件快取] 部署選項的 BizTalk 組件和 .NET 組件會加入到全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="ba78b-121">BizTalk assemblies and .NET assemblies that have the "Add to GAC on import" deployment option configured are added to the global assembly cache (GAC).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba78b-122">由於成品資料是儲存在 BizTalk Server 資料庫中，所以當您之後將應用程式匯出到 .msi 檔案時，BizTalk Server 可從資料庫中擷取與此應用程式和其成品相關的所有組態資訊和資料，並將這些資訊和資料包含在 .msi 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ba78b-122">Because the artifact data is stored in the BizTalk Server databases, when you later export the application into an .msi file, BizTalk Server can retrieve from the databases all of the configuration information and data associated with the application and its artifacts and include it in the .msi file.</span></span> <span data-ttu-id="ba78b-123">當您將此 .msi 檔案匯入其他 BizTalk 群組時，會在新的群組中重新建立所有成品組態資訊和資料。</span><span class="sxs-lookup"><span data-stu-id="ba78b-123">When you import the .msi file into another BizTalk group, all of the artifact configuration information and data is recreated in the new group.</span></span>  
  
 <span data-ttu-id="ba78b-124">當您匯入應用程式之後，您可利用單一實體的方式一起檢視、管理和部署應用程式中的成品，或是使用管理主控台或 BTSTask 來個別檢視、管理和部署。</span><span class="sxs-lookup"><span data-stu-id="ba78b-124">After you import an application, you can view, manage, and deploy the artifacts in the application either together as a single entity or individually by using the Administration console or BTSTask.</span></span> <span data-ttu-id="ba78b-125">如需詳細資訊，請參閱[應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ba78b-125">For more information, see [Application Deployment and Management Tools](../core/application-deployment-and-management-tools.md).</span></span>  
  
## <a name="importing-a-policy"></a><span data-ttu-id="ba78b-126">匯入原則</span><span class="sxs-lookup"><span data-stu-id="ba78b-126">Importing a policy</span></span>  
 <span data-ttu-id="ba78b-127">當您從 .xml 檔案匯入原則時，該原則會加入到規則引擎資料庫。</span><span class="sxs-lookup"><span data-stu-id="ba78b-127">When you import a policy from an .xml file, the policy is added to the Rule Engine database.</span></span> <span data-ttu-id="ba78b-128">該原則不會與 BizTalk 管理資料庫中的任何應用程式有關聯，與匯入 BizTalk .msi 檔案中的原則時不同。</span><span class="sxs-lookup"><span data-stu-id="ba78b-128">Unlike when you import a policy within a BizTalk .msi file, the policy is not associated with any application in the BizTalk Management database.</span></span> <span data-ttu-id="ba78b-129">原則會顯示在 [原則] 節點的\<所有成品\>BizTalk Server 管理主控台中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba78b-129">The policy displays in the Policies node of the \<All Artifacts\> folder in the BizTalk Server Administration console.</span></span> <span data-ttu-id="ba78b-130">當您匯入此原則之後，可以發佈此原則，讓它可供群組中的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="ba78b-130">After importing the policy you can publish it to make it available for applications in the group to use.</span></span> <span data-ttu-id="ba78b-131">如需詳細資訊，請參閱[管理原則](../core/managing-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="ba78b-131">For more information, see [Managing Policies](../core/managing-policies.md).</span></span>  
  
## <a name="importing-a-binding-file"></a><span data-ttu-id="ba78b-132">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="ba78b-132">Importing a binding file</span></span>  
 <span data-ttu-id="ba78b-133">當您將繫結檔案匯入 BizTalk 群組中時，如果目前此群組中有存在任何繫結與匯入之檔案中的繫結同名，則這些繫結會遭到匯入之檔案中的繫結所覆寫，而且會套用此組態。</span><span class="sxs-lookup"><span data-stu-id="ba78b-133">When you import a binding file into a BizTalk group, any bindings that currently exist in the group having the same name as bindings in the imported file are overwritten by the bindings in the imported file, and the configuration is applied.</span></span>  
  
 <span data-ttu-id="ba78b-134">當您將繫結檔案匯入 BizTalk 應用程式中時 (以個別方式或當做應用程式的一部分匯入)，如果目前此應用程式中有存在任何繫結與檔案中的繫結同名，則這些繫結會遭到匯入的繫結所覆寫，而且會套用此組態。</span><span class="sxs-lookup"><span data-stu-id="ba78b-134">When you import a binding file into a BizTalk application either individually or as part of an application, any bindings that currently exist in the application having the same name as bindings in the file are overwritten by the imported bindings, and the configuration is applied.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba78b-135">基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。</span><span class="sxs-lookup"><span data-stu-id="ba78b-135">For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="ba78b-136">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ba78b-136">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="ba78b-137">您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。</span><span class="sxs-lookup"><span data-stu-id="ba78b-137">You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.</span></span> <span data-ttu-id="ba78b-138">如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="ba78b-138">For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="ba78b-139">另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="ba78b-139">See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba78b-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba78b-140">See Also</span></span>  
 <span data-ttu-id="ba78b-141">[會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="ba78b-141">[What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md) </span></span>  
 <span data-ttu-id="ba78b-142">[匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="ba78b-142">[Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md) </span></span>  
 [<span data-ttu-id="ba78b-143">相依性和應用程式部署</span><span class="sxs-lookup"><span data-stu-id="ba78b-143">Dependencies and Application Deployment</span></span>](../core/dependencies-and-application-deployment.md)