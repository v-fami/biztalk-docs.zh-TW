---
title: 步驟 2： 提交 0c4 查詢 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, submitting requests
ms.assetid: ce50b892-c87c-414a-94c5-b40947fec68f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c621b6891b816f72603202bd6f2214882eb4b5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965676"
---
# <a name="step-2-submitting-a-0c4-query"></a><span data-ttu-id="4a5e9-102">步驟 2： 提交 0 C 4 查詢</span><span class="sxs-lookup"><span data-stu-id="4a5e9-102">Step 2: Submitting a 0C4 Query</span></span>
<span data-ttu-id="4a5e9-103">在此步驟中，您將使用夥伴介面程序 (PIP) 0C4 準備並提交「同步測試查詢」要求。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 0C4 - Synchronous Test Query.</span></span> <span data-ttu-id="4a5e9-104">RosettaNet 定義此 PIP，確保兩個不同組織之間的同步通訊管道正常運作。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-104">RosettaNet defines this PIP to make sure a successful synchronous communication channel is working correctly between two different organizations.</span></span> <span data-ttu-id="4a5e9-105">由於此 PIP 具有同步通訊模式，所以 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 不會傳送接收通知。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-105">Because this PIP has a synchronous communication pattern, [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] does not send receipt acknowledgements.</span></span> <span data-ttu-id="4a5e9-106">此 PIP 遵循與其他同步雙向動作 PIP (例如 PIP 2A9 - 查詢技術產品資訊) 相同的模式。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-106">This PIP follows the same pattern as other synchronous double action PIPs, such as PIP 2A9 - Query Technical Product Information.</span></span>  
  
### <a name="to-submit-a-0c4---synchronous-test-query"></a><span data-ttu-id="4a5e9-107">提交 0C4 - 同步測試查詢</span><span class="sxs-lookup"><span data-stu-id="4a5e9-107">To submit a 0C4 - Synchronous Test Query</span></span>  
  
1.  <span data-ttu-id="4a5e9-108">在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-108">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="4a5e9-109">在**提交訊息**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4a5e9-109">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="4a5e9-110">使用</span><span class="sxs-lookup"><span data-stu-id="4a5e9-110">Use this</span></span>|<span data-ttu-id="4a5e9-111">動作</span><span class="sxs-lookup"><span data-stu-id="4a5e9-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4a5e9-112">**主要組織**</span><span class="sxs-lookup"><span data-stu-id="4a5e9-112">**Home Organization**</span></span>|<span data-ttu-id="4a5e9-113">型別**FABRIKAM**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-113">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="4a5e9-114">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="4a5e9-114">**Partner Organization**</span></span>|<span data-ttu-id="4a5e9-115">型別**CONTOSO**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-115">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="4a5e9-116">**Pip 代碼**</span><span class="sxs-lookup"><span data-stu-id="4a5e9-116">**Pip Code**</span></span>|<span data-ttu-id="4a5e9-117">型別**0c4**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-117">Type **0C4**.</span></span>|  
    |<span data-ttu-id="4a5e9-118">**Pip 版本**</span><span class="sxs-lookup"><span data-stu-id="4a5e9-118">**Pip Version**</span></span>|<span data-ttu-id="4a5e9-119">型別**R01.02**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-119">Type **R01.02**.</span></span>|  
    |<span data-ttu-id="4a5e9-120">**Pip 執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="4a5e9-120">**Pip Instance ID**</span></span>|<span data-ttu-id="4a5e9-121">型別**0C4_Test**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-121">Type **0C4_Test**.</span></span> <span data-ttu-id="4a5e9-122">**重要事項：** 為了避免發生重複訊息識別碼錯誤，您必須確定**PIP**都是唯一的每個您所提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-122">**Important:**  To avoid duplicate message ID errors, you must make sure that the **PIP** is unique for each message that you submit.</span></span> <span data-ttu-id="4a5e9-123">如果將來要執行 0C4 測試，您必須變更此欄位。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-123">If you run the 0C4 test in the future, you will have to change this field.</span></span>|  
    |<span data-ttu-id="4a5e9-124">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="4a5e9-124">**Message Category**</span></span>|<span data-ttu-id="4a5e9-125">型別**動作**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-125">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="4a5e9-126">使用 [記事本] 或其他文字編輯器，開啟中的 0C4_Request.xml 檔案*\<磁碟機\>*: \Program Files\Microsoft BizTalk 2009 Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾然後複製並貼上內容**服務內容**lobwebapplication 的欄位。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-126">Using Notepad or another text editor, open the 0C4_Request.xml file in the *\<drive\>*:\Program Files\Microsoft BizTalk 2009 Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
4.  <span data-ttu-id="4a5e9-127">按一下**送出**提交 0 C 4 查詢至 Contoso 電腦。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-127">Click **Submit** to submit the 0C4 query to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="4a5e9-128">確認 Fabrikam 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="4a5e9-128">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="4a5e9-129">在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-129">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a5e9-130">您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-130">You should receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="4a5e9-131">類別 -99 的訊息代表錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-131">A category -99 message signifies an error.</span></span> <span data-ttu-id="4a5e9-132">您可以使用 [事件檢視器] 查看實際的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-132">You can use the Event Viewer to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="4a5e9-133">確認 Contoso 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="4a5e9-133">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="4a5e9-134">按一下 **[開始]**，依序指向 **[所有程式]** 和 **[Microsoft SQL Server]**，然後按一下 **[SQL Server Management Studio]**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-134">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="4a5e9-135">在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-135">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a5e9-136">如果未啟動 SQL Server 代理程式，以滑鼠右鍵按一下，然後再按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-136">If the SQL Server Agent is not started, right-click it, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="4a5e9-137">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-137">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="4a5e9-138">在\<資料表\>文字方塊中，選取**BTARNDATA**從清單中。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-138">In the \<table\> text box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="4a5e9-139">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="4a5e9-139">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="4a5e9-140">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-140">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="4a5e9-141">在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-141">In the Query window, in the Results pane, verify that you see one incoming message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a5e9-142">您應該會看到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-142">You should see a category 10 message that represents the original request that the Fabrikam computer sent.</span></span>  
  
8.  <span data-ttu-id="4a5e9-143">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="4a5e9-143">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="4a5e9-144">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-144">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="4a5e9-145">在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-145">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a5e9-146">您應該會看到類別 50 的訊息，代表 Contoso 對 Fabrikam 傳送的 PIP 0C4 查詢所發出的回應。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-146">You should see a category 50 message that represents the Contoso response to the PIP 0C4 query that Fabrikam sent.</span></span> <span data-ttu-id="4a5e9-147">在雙向動作同步實例中，回應者電腦不會為了回應初查詢訊息而傳送通知給啟動者電腦。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-147">In a double action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial query message.</span></span> <span data-ttu-id="4a5e9-148">回應訊息是做為通知使用。</span><span class="sxs-lookup"><span data-stu-id="4a5e9-148">The response message serves as the acknowledgement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5e9-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a5e9-149">See Also</span></span>  
 <span data-ttu-id="4a5e9-150">[步驟 3： 提交 3A2 要求](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md) </span><span class="sxs-lookup"><span data-stu-id="4a5e9-150">[Step 3: Submitting a 3A2 Request](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md) </span></span>  
 [<span data-ttu-id="4a5e9-151">BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="4a5e9-151">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)