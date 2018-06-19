---
title: 使用追蹤活動定義檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking, activity definition file
- activity definition file
- activity definition file, about activity definition file
- tracking, managing views
- activity definition file, activity fields
ms.assetid: 0592a844-aad7-4054-b1e7-344f1086f0b1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e6cf33bf62f8ec7924b3f9ff2379f84b2b42775
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009375"
---
# <a name="working-with-the-tracking-activity-definition-file"></a><span data-ttu-id="f0389-102">使用追蹤活動定義檔案</span><span class="sxs-lookup"><span data-stu-id="f0389-102">Working with the Tracking Activity Definition File</span></span>
<span data-ttu-id="f0389-103">活動定義檔案包含追蹤資訊中的程序和訊息活動[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0389-103">The activity definition file contains information about the tracking process and message activities in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f0389-104">您可以使用此檔案以管理追蹤中 BizTalk 商務活動監控 (BAM) 的資料。</span><span class="sxs-lookup"><span data-stu-id="f0389-104"> uses this file to manage data tracking in BizTalk Business Activity Monitoring (BAM).</span></span> <span data-ttu-id="f0389-105">定義檔案是 XML 檔案 (Tracking.xml)，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝在\<*磁碟機*\>: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAMTracking 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0389-105">The definition file is an XML file (Tracking.xml) that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs in the \<*drive*\>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAMTracking folder.</span></span> <span data-ttu-id="f0389-106">Tracking.xml 中定義的活動對於您的目的而言應該很足夠了。</span><span class="sxs-lookup"><span data-stu-id="f0389-106">The activities defined in Tracking.xml may be sufficient for your purposes.</span></span>  
  
 <span data-ttu-id="f0389-107">如需有關追蹤活動、 檢視和資料表的詳細資訊，請參閱[增強追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="f0389-107">For more information about the tracking activities, views, and tables, see [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).</span></span> <span data-ttu-id="f0389-108">如需有關 BAM 的詳細資訊，請參閱 「 商務活動監控 (BAM) 」 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="f0389-108">For more information about BAM, see "Business Activity Monitoring (BAM)" in BizTalk Server Help.</span></span>  
  
## <a name="managing-tracking-views"></a><span data-ttu-id="f0389-109">管理追蹤檢視</span><span class="sxs-lookup"><span data-stu-id="f0389-109">Managing Tracking Views</span></span>  
 <span data-ttu-id="f0389-110">請勿將 BizTalk「追蹤設定檔編輯器」與 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 追蹤一起使用。</span><span class="sxs-lookup"><span data-stu-id="f0389-110">You do not use the BizTalk Tracking Profile Editor with [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracking.</span></span> <span data-ttu-id="f0389-111">追蹤點無法自訂；請勿變更活動定義。</span><span class="sxs-lookup"><span data-stu-id="f0389-111">The tracking points are not customizable; do not change activity definitions.</span></span> <span data-ttu-id="f0389-112">不過，您可以管理 BAM 檢視與部署，</span><span class="sxs-lookup"><span data-stu-id="f0389-112">However, you can manage BAM views and deployment.</span></span> <span data-ttu-id="f0389-113">若要這樣做，您修改[!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表 (Tracking.xls)，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝在\<*磁碟機*\>: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0389-113">To do so, you modify an [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet (Tracking.xls) that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs in the \<*drive*\>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking folder.</span></span> <span data-ttu-id="f0389-114">如需詳細資訊，請參閱下列的＜管理追蹤檢視＞。</span><span class="sxs-lookup"><span data-stu-id="f0389-114">For more information, see "Managing Tracking Views" below.</span></span>  
  
 <span data-ttu-id="f0389-115">如果 Tracking.xml 中定義的檢視還無法滿足您的需求，您也可以依照以下的方式定義對 BAM 中所追蹤資訊的其他檢視。</span><span class="sxs-lookup"><span data-stu-id="f0389-115">If the views defined in Tracking.xml are not sufficient for your needs, you can define different views of the information tracked in BAM as follows.</span></span>  
  
#### <a name="to-create-different-tracking-views"></a><span data-ttu-id="f0389-116">建立不同的追蹤檢視</span><span class="sxs-lookup"><span data-stu-id="f0389-116">To create different tracking views</span></span>  
  
1.  <span data-ttu-id="f0389-117">按一下 **[開始]**，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="f0389-117">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="f0389-118">輸入**cmd**中開啟 文字方塊中，執行 對話方塊中，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f0389-118">Enter **cmd** in the Open text box of the Run dialog box, and then click **OK**.</span></span> <span data-ttu-id="f0389-119">在命令列 對話方塊中，輸入下列程式碼以解除部署 tracking.xml，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="f0389-119">In the command line dialog box, enter the following code to undeploy tracking.xml, then click **OK**:</span></span>  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
    bm remove-all  -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking\<filename\>.xml"  
    ```  
  
2.  <span data-ttu-id="f0389-120">在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，移至*\<磁碟機\>*: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM 追蹤。</span><span class="sxs-lookup"><span data-stu-id="f0389-120">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *\<drive\>*:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM Tracking.</span></span> <span data-ttu-id="f0389-121">按兩下 Tracking.xls。</span><span class="sxs-lookup"><span data-stu-id="f0389-121">Double-click Tracking.xls.</span></span>  
  
3.  <span data-ttu-id="f0389-122">在 [商務活動監控] 中建立一個新的檢視。</span><span class="sxs-lookup"><span data-stu-id="f0389-122">Create a new view in Business Activity Monitoring.</span></span> <span data-ttu-id="f0389-123">如需如何執行這項操作資訊，請參閱 < 管理商務活動監控 」 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="f0389-123">For information about how to do so, see "Managing Business Activity Monitoring" in BizTalk Server Help.</span></span>  
  
4.  <span data-ttu-id="f0389-124">按一下**BAM**，然後按一下 **匯出 XML**。</span><span class="sxs-lookup"><span data-stu-id="f0389-124">Click **BAM**, and then click **Export XML**.</span></span> <span data-ttu-id="f0389-125">移至想要的位置，輸入檔案名稱 （不可以是 Tracking.xml)，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="f0389-125">Move to the desired location, enter a file name (other than Tracking.xml), and then click **Save**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f0389-126">當您在追蹤 XLS 檔案內定義了新的追蹤檢視，並且將此追蹤 XLS 檔案匯出成 XML 檔案時，某些新的欄位名稱可能會稍微有點修改。</span><span class="sxs-lookup"><span data-stu-id="f0389-126">When you define new tracking views in a tracking XLS file, and export an XML file from the tracking XLS file, some of the new field names may be slightly modified.</span></span> <span data-ttu-id="f0389-127">請把您自訂的追蹤 XML 檔案中的這些欄位和 BTARN 安裝程式安裝的標準 tracking.xml 欄位比對，就可以找出並予以更正。</span><span class="sxs-lookup"><span data-stu-id="f0389-127">Correct this by verifying the fields in your customized tracking XML file against the standard tracking.xml field installed by BTARN setup.</span></span>  
  
5.  <span data-ttu-id="f0389-128">部署新的追蹤 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f0389-128">Deploy the new tracking XML file.</span></span> <span data-ttu-id="f0389-129">若要這樣做，請按一下**啟動**，然後按一下 **執行**。</span><span class="sxs-lookup"><span data-stu-id="f0389-129">To do so, click **Start**, and then click **Run**.</span></span> <span data-ttu-id="f0389-130">輸入**cmd**中開啟 文字方塊中，執行 對話方塊中，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f0389-130">Enter **cmd** in the Open text box of the Run dialog box, and then click **OK**.</span></span> <span data-ttu-id="f0389-131">在命令列 對話方塊中，輸入下列程式碼，以部署新的追蹤檔案，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f0389-131">In the command line dialog box, enter the following code to deploy your new tracking file, then click **OK**.</span></span> <span data-ttu-id="f0389-132">建議您最好修改此追蹤 XML 檔案的名稱，以免覆寫預設的 tracking.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="f0389-132">It is recommended that you rename the tracking XML file so that you do not overwrite the default tracking.xml file.</span></span>  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
    bm.exe deploy-all -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2030 Accelerator for RosettaNet\BAMTracking\<filename\>.xml"  
    ```  
  
 <span data-ttu-id="f0389-133">BAM 中追蹤的資訊不包含訊息內容，因為訊息內容存放在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0389-133">The information tracked in BAM does not include the message content, because that is stored in a [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] database.</span></span>  
  
 <span data-ttu-id="f0389-134">您可以使用「商務活動監控管理公用程式」來管理 BAM 追蹤的部署。</span><span class="sxs-lookup"><span data-stu-id="f0389-134">You can manage deployment of BAM tracking by using the Business Activity Monitoring Management Utility.</span></span> <span data-ttu-id="f0389-135">如需有關此公用程式的詳細資訊，請參閱 「 使用商務活動監控管理公用程式 」 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="f0389-135">For more information about this utility, see "Using the Business Activity Monitoring Management Utility" in BizTalk Server Help.</span></span>  
  
## <a name="activity-fields"></a><span data-ttu-id="f0389-136">活動欄位</span><span class="sxs-lookup"><span data-stu-id="f0389-136">Activity Fields</span></span>  
 <span data-ttu-id="f0389-137">以下為活動定義檔案中，訊息活動的欄位：</span><span class="sxs-lookup"><span data-stu-id="f0389-137">The fields of the message activity in the activity definition file are the following:</span></span>  
  
-   <span data-ttu-id="f0389-138">ActivityName</span><span class="sxs-lookup"><span data-stu-id="f0389-138">ActivityName</span></span>  
  
-   <span data-ttu-id="f0389-139">類別目錄</span><span class="sxs-lookup"><span data-stu-id="f0389-139">Category</span></span>  
  
-   <span data-ttu-id="f0389-140">ContentKey</span><span class="sxs-lookup"><span data-stu-id="f0389-140">ContentKey</span></span>  
  
-   <span data-ttu-id="f0389-141">DestinationPartyName</span><span class="sxs-lookup"><span data-stu-id="f0389-141">DestinationPartyName</span></span>  
  
-   <span data-ttu-id="f0389-142">ErrorDescription</span><span class="sxs-lookup"><span data-stu-id="f0389-142">ErrorDescription</span></span>  
  
-   <span data-ttu-id="f0389-143">HasError</span><span class="sxs-lookup"><span data-stu-id="f0389-143">HasError</span></span>  
  
-   <span data-ttu-id="f0389-144">InReplyToMessageID</span><span class="sxs-lookup"><span data-stu-id="f0389-144">InReplyToMessageID</span></span>  
  
-   <span data-ttu-id="f0389-145">IsReceived</span><span class="sxs-lookup"><span data-stu-id="f0389-145">IsReceived</span></span>  
  
-   <span data-ttu-id="f0389-146">MessageTrackingID</span><span class="sxs-lookup"><span data-stu-id="f0389-146">MessageTrackingID</span></span>  
  
-   <span data-ttu-id="f0389-147">NoFPipInstance</span><span class="sxs-lookup"><span data-stu-id="f0389-147">NoFPipInstance</span></span>  
  
-   <span data-ttu-id="f0389-148">PipCode</span><span class="sxs-lookup"><span data-stu-id="f0389-148">PipCode</span></span>  
  
-   <span data-ttu-id="f0389-149">PipInstanceID</span><span class="sxs-lookup"><span data-stu-id="f0389-149">PipInstanceID</span></span>  
  
-   <span data-ttu-id="f0389-150">PiPVersion</span><span class="sxs-lookup"><span data-stu-id="f0389-150">PiPVersion</span></span>  
  
-   <span data-ttu-id="f0389-151">SourcePartName</span><span class="sxs-lookup"><span data-stu-id="f0389-151">SourcePartName</span></span>  
  
-   <span data-ttu-id="f0389-152">時間戳記</span><span class="sxs-lookup"><span data-stu-id="f0389-152">Timestamp</span></span>  
  
 <span data-ttu-id="f0389-153">以下為活動定義檔案中，程序活動的欄位：</span><span class="sxs-lookup"><span data-stu-id="f0389-153">The fields of the process activity in the activity definition file are the following:</span></span>  
  
-   <span data-ttu-id="f0389-154">EndTime</span><span class="sxs-lookup"><span data-stu-id="f0389-154">EndTime</span></span>  
  
-   <span data-ttu-id="f0389-155">InitiatorPartyName</span><span class="sxs-lookup"><span data-stu-id="f0389-155">InitiatorPartyName</span></span>  
  
-   <span data-ttu-id="f0389-156">IsInitiatorRole</span><span class="sxs-lookup"><span data-stu-id="f0389-156">IsInitiatorRole</span></span>  
  
-   <span data-ttu-id="f0389-157">PipCode</span><span class="sxs-lookup"><span data-stu-id="f0389-157">PipCode</span></span>  
  
-   <span data-ttu-id="f0389-158">PipInstanceID</span><span class="sxs-lookup"><span data-stu-id="f0389-158">PipInstanceID</span></span>  
  
-   <span data-ttu-id="f0389-159">PipName</span><span class="sxs-lookup"><span data-stu-id="f0389-159">PipName</span></span>  
  
-   <span data-ttu-id="f0389-160">PipVersion</span><span class="sxs-lookup"><span data-stu-id="f0389-160">PipVersion</span></span>  
  
-   <span data-ttu-id="f0389-161">ResponderPartyName</span><span class="sxs-lookup"><span data-stu-id="f0389-161">ResponderPartyName</span></span>  
  
-   <span data-ttu-id="f0389-162">StartTime</span><span class="sxs-lookup"><span data-stu-id="f0389-162">StartTime</span></span>  
  
-   <span data-ttu-id="f0389-163">狀態</span><span class="sxs-lookup"><span data-stu-id="f0389-163">Status</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0389-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0389-164">See Also</span></span>  
 <span data-ttu-id="f0389-165">[增強的追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="f0389-165">[Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span></span>  
 [<span data-ttu-id="f0389-166">管理設定、憑證、資料庫和安全性</span><span class="sxs-lookup"><span data-stu-id="f0389-166">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)