---
title: "管理 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, examples
- utilities, SSOMANAGE
- examples, SSO
- SSOMANAGE command line utility
ms.assetid: f738e344-4d81-4557-b399-68b59c413245
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15a94bf916550d9a2eada9b8f354432b4c154ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-server-sample"></a><span data-ttu-id="59682-102">管理 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="59682-102">Manage (BizTalk Server Sample)</span></span>
<span data-ttu-id="59682-103">「管理單一登入 (SSO)」範例會示範如何建構 .xml 檔案，這類檔案可以與 ssomanage.exe 命令列公用程式搭配使用，執行下列類型的系統管理作業：</span><span class="sxs-lookup"><span data-stu-id="59682-103">The Manage Single Sign-On (SSO) sample demonstrates how to construct .xml files that you can use with the ssomanage.exe command-line utility to perform the following types of administration operations:</span></span>  
  
-   <span data-ttu-id="59682-104">在 SSO 系統層級更新全域資訊</span><span class="sxs-lookup"><span data-stu-id="59682-104">Update global information at the SSO system level</span></span>  
  
-   <span data-ttu-id="59682-105">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="59682-105">Create affiliate applications</span></span>  
  
-   <span data-ttu-id="59682-106">建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="59682-106">Create user mappings</span></span>  
  
 <span data-ttu-id="59682-107">如需企業單一登入的概念性資訊，請參閱[使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="59682-107">For conceptual information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).</span></span>  
  
 <span data-ttu-id="59682-108">如需範例，示範如何以程式設計方式設定 SSO，例如建立分支機構應用程式和使用者對應，請參閱[HTTPSSO （BizTalk Server 範例）](../core/httpsso-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="59682-108">For a sample that shows how to programmatically configure SSO, such as creating affiliate applications and user mappings, see [HTTPSSO (BizTalk Server Sample)](../core/httpsso-biztalk-server-sample.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="59682-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="59682-109">What This Sample Does</span></span>  
 <span data-ttu-id="59682-110">這個範例會針對其中各種作業類型，分別提供一對 XSD 和範例 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="59682-110">This sample includes pairs of XSD and sample .xml files for each of these types of operations.</span></span> <span data-ttu-id="59682-111">範例 .xml 檔案中的值是無效的。</span><span class="sxs-lookup"><span data-stu-id="59682-111">The values in the sample .xml files are not valid.</span></span> <span data-ttu-id="59682-112">您必須變更這些值，才能符合您的特定需求。</span><span class="sxs-lookup"><span data-stu-id="59682-112">You must make changes to the values that are appropriate to your specific requirements.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="59682-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="59682-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="59682-114">*\<範例路徑 >*\SSO\Manage\\</span><span class="sxs-lookup"><span data-stu-id="59682-114">*\<Samples Path>*\SSO\Manage\\</span></span>  
  
 <span data-ttu-id="59682-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="59682-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="59682-116">檔案</span><span class="sxs-lookup"><span data-stu-id="59682-116">File(s)</span></span>|<span data-ttu-id="59682-117">Description</span><span class="sxs-lookup"><span data-stu-id="59682-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59682-118">AffiliateApplication.xml、GlobalInfo.xml、UserMapping.xml</span><span class="sxs-lookup"><span data-stu-id="59682-118">AffiliateApplication.xml, GlobalInfo.xml, UserMapping.xml</span></span>|<span data-ttu-id="59682-119">經過修改之後，即可做為引數，傳遞至命令列公用程式 ssomanage.exe 的範例 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="59682-119">Sample .xml files that you can, after modification, pass as arguments to the command-line utility ssomanage.exe.</span></span>|  
|<span data-ttu-id="59682-120">AffiliateApplication.xsd、GlobalInfo.xsd、UserMapping.xsd</span><span class="sxs-lookup"><span data-stu-id="59682-120">AffiliateApplication.xsd, GlobalInfo.xsd, UserMapping.xsd</span></span>|<span data-ttu-id="59682-121">對應之 .xml 檔案的結構描述檔案，可提供其可能項目和屬性 (Attribute) 的完整描述。</span><span class="sxs-lookup"><span data-stu-id="59682-121">Schema files for the corresponding .xml files, providing complete descriptions of their possible elements and attributes.</span></span> <span data-ttu-id="59682-122">您可以使用這些檔案來驗證從其他來源收到的對應 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="59682-122">You can use these files to validate corresponding .xml files received from other sources.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="59682-123">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="59682-123">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="59682-124">由於這個範例僅包含 XML 結構描述定義語言 (XSD) 和 .xml 檔案，而後者可經過修改，然後傳遞至命令列公用程式 ssomanage.exe，因此在此範例中不需要進行任何建置。</span><span class="sxs-lookup"><span data-stu-id="59682-124">Because this sample consists of only XML Schema definition language (XSD) and .xml files, the latter of which you can modify and then pass to the command-line utility ssomanage.exe, there is nothing to build in this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="59682-125">執行此範例</span><span class="sxs-lookup"><span data-stu-id="59682-125">Running This Sample</span></span>  
 <span data-ttu-id="59682-126">此範例包含的範例 .xml 檔案，將在下列三種不同模式中執行命令列公用程式 ssomanage.exe：</span><span class="sxs-lookup"><span data-stu-id="59682-126">This sample includes sample .xml files for running the command-line utility ssomanage.exe in the following three different modes:</span></span>  
  
-   <span data-ttu-id="59682-127">**更新 SSO 系統層級的全域資訊。**</span><span class="sxs-lookup"><span data-stu-id="59682-127">**Update global information at the SSO system level.**</span></span> <span data-ttu-id="59682-128">若要執行這類作業，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="59682-128">To perform this type of operation, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="59682-129">根據您的特定組態需求，編輯 GlobalInfo.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="59682-129">Edit the file GlobalInfo.xml as required for your specific configuration.</span></span>  
  
    2.  <span data-ttu-id="59682-130">以適當的引數執行 ssomanage.exe 命令列公用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59682-130">Run the ssomanage.exe command-line utility with the appropriate arguments, as follows:</span></span>  
  
        ```  
        ssomanage –updatedb GlobalInfo.xml  
        ```  
  
     <span data-ttu-id="59682-131">確定將 GlobalInfo.xml 檔案中的值編輯成符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="59682-131">Ensure that you edit the values in the file GlobalInfo.xml to match your environment.</span></span> <span data-ttu-id="59682-132">例如，SSO 管理員帳戶必須是有效的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="59682-132">For example, the SSO Admin account must be a valid Windows account.</span></span> <span data-ttu-id="59682-133">SSO 管理員帳戶和 SSO 分支機構管理員帳戶都必須是 Windows 全域網域群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="59682-133">Both the SSO Admin account and SSO Affiliate Admin account must be Windows Global Domain Group accounts.</span></span>  
  
-   <span data-ttu-id="59682-134">**建立分支機構應用程式。**</span><span class="sxs-lookup"><span data-stu-id="59682-134">**Create affiliate applications.**</span></span> <span data-ttu-id="59682-135">若要執行這類作業，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="59682-135">To perform this type of operation, perform the following steps:</span></span>  
  
-   <span data-ttu-id="59682-136">根據您的特定組態需求，編輯 AffiliateApplication.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="59682-136">Edit the file AffiliateApplication.xml as required for your specific configuration.</span></span>  
  
    -   <span data-ttu-id="59682-137">以適當的引數執行 ssomanage.exe 命令列公用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59682-137">Run the command-line utility ssomanage.exe with the appropriate arguments, as follows:</span></span>  
  
        ```  
        ssomanage –createapps AffiliateApplication.xml  
        ```  
  
     <span data-ttu-id="59682-138">您可以同時建立一個以上的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="59682-138">You can create more than one affiliate application at the same time.</span></span>  
  
-   <span data-ttu-id="59682-139">**建立使用者對應。**</span><span class="sxs-lookup"><span data-stu-id="59682-139">**Create user mappings.**</span></span> <span data-ttu-id="59682-140">若要執行這類作業，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="59682-140">To perform this type of operation, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="59682-141">根據您的特定組態需求，編輯 UserMapping.xmlas 檔案。</span><span class="sxs-lookup"><span data-stu-id="59682-141">Edit the file UserMapping.xmlas required for your specific configuration.</span></span>  
  
    2.  <span data-ttu-id="59682-142">以適當的引數執行 ssomanage.exe 命令列公用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59682-142">Run the command-line utility ssomanage.exe with the appropriate arguments, as follows:</span></span>  
  
        ```  
        ssomanage –createmappings UserMapping.xml  
        ```  
  
     <span data-ttu-id="59682-143">您可以同時為一或多個分支機構應用程式建立一個以上的對應。</span><span class="sxs-lookup"><span data-stu-id="59682-143">You can create more than one mapping for one or more affiliate applications at the same time.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="59682-144">註解</span><span class="sxs-lookup"><span data-stu-id="59682-144">Comments</span></span>  
 <span data-ttu-id="59682-145">在變更本範例所提供的範例 .xml 檔案之後 (尤其當這類變更牽涉範圍包括檔案中的機密資訊時)，請確定這些檔案已受檔案系統的妥善保護。</span><span class="sxs-lookup"><span data-stu-id="59682-145">After making changes to the sample .xml files provided with this sample, especially where such changes involve including sensitive information in the files, ensure that these files are well protected in your file system.</span></span> <span data-ttu-id="59682-146">例如，請確定沒有小心地將這類檔案放在共用資料夾中。</span><span class="sxs-lookup"><span data-stu-id="59682-146">For example, ensure that they are not inadvertently placed in a folder that is shared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59682-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59682-147">See Also</span></span>  
 [<span data-ttu-id="59682-148">SSO （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="59682-148">SSO (BizTalk Server Samples Folder)</span></span>](../core/sso-biztalk-server-samples-folder.md)