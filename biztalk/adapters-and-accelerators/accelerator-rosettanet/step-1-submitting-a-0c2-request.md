---
title: "步驟 1： 提交 0c2 要求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 698c4a43-20b9-46b7-ab66-1dfa24232024
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 089ad320f9363e1a3284af863512c89bcb67167d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-submitting-a-0c2-request"></a><span data-ttu-id="1695c-102">步驟 1： 提交 0 C 2 要求</span><span class="sxs-lookup"><span data-stu-id="1695c-102">Step 1: Submitting a 0C2 Request</span></span>
<span data-ttu-id="1695c-103">在此步驟中，您將使用「0C2 - 非同步測試要求夥伴介面程序 (PIP)」來準備並提交要求。</span><span class="sxs-lookup"><span data-stu-id="1695c-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for an 0C2 - Asynchronous Test Request.</span></span> <span data-ttu-id="1695c-104">此 PIP 可以確保兩個不同組織之間的非同步通訊管道正常運作。</span><span class="sxs-lookup"><span data-stu-id="1695c-104">This PIP ensures that an asynchronous communication channel is working correctly between two different organizations.</span></span> <span data-ttu-id="1695c-105">此 PIP 遵循與其他非同步雙向動作 PIP (例如「3A4 - 訂單要求 PIP」) 相同的模式。</span><span class="sxs-lookup"><span data-stu-id="1695c-105">This PIP follows the same pattern as other asynchronous double action PIPs, such as the 3A4 - Request Purchase Order PIP.</span></span>  
  
### <a name="to-submit-a-0c2---asynchronous-test-request"></a><span data-ttu-id="1695c-106">提交 0C2 - 非同步測試要求</span><span class="sxs-lookup"><span data-stu-id="1695c-106">To submit a 0C2 - Asynchronous Test Request</span></span>  
  
1.  <span data-ttu-id="1695c-107">在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。</span><span class="sxs-lookup"><span data-stu-id="1695c-107">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="1695c-108">在**提交訊息**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1695c-108">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="1695c-109">使用</span><span class="sxs-lookup"><span data-stu-id="1695c-109">Use this</span></span>|<span data-ttu-id="1695c-110">動作</span><span class="sxs-lookup"><span data-stu-id="1695c-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1695c-111">**主要組織**</span><span class="sxs-lookup"><span data-stu-id="1695c-111">**Home Organization**</span></span>|<span data-ttu-id="1695c-112">型別**FABRIKAM**。</span><span class="sxs-lookup"><span data-stu-id="1695c-112">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="1695c-113">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="1695c-113">**Partner Organization**</span></span>|<span data-ttu-id="1695c-114">型別**CONTOSO**。</span><span class="sxs-lookup"><span data-stu-id="1695c-114">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="1695c-115">**Pip 代碼**</span><span class="sxs-lookup"><span data-stu-id="1695c-115">**Pip Code**</span></span>|<span data-ttu-id="1695c-116">型別**0c2**。</span><span class="sxs-lookup"><span data-stu-id="1695c-116">Type **0C2**.</span></span>|  
    |<span data-ttu-id="1695c-117">**Pip 版本**</span><span class="sxs-lookup"><span data-stu-id="1695c-117">**Pip Version**</span></span>|<span data-ttu-id="1695c-118">型別**R01.02**。</span><span class="sxs-lookup"><span data-stu-id="1695c-118">Type **R01.02**.</span></span>|  
    |<span data-ttu-id="1695c-119">**Pip 執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="1695c-119">**Pip Instance ID**</span></span>|<span data-ttu-id="1695c-120">型別**0C2_Test**。</span><span class="sxs-lookup"><span data-stu-id="1695c-120">Type **0C2_Test**.</span></span> <span data-ttu-id="1695c-121">**重要事項：**您必須確定**PIP**都是唯一的每個您送出以避免發生重複訊息識別碼錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-121">**Important:**  You must make sure that the **PIP** is unique for each message that you submit to avoid duplicate message ID errors.</span></span> <span data-ttu-id="1695c-122">如果將來要執行 0C2 測試，您必須變更此欄位。</span><span class="sxs-lookup"><span data-stu-id="1695c-122">If you run the 0C2 test in the future, you will have to change this field.</span></span>|  
    |<span data-ttu-id="1695c-123">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="1695c-123">**Message Category**</span></span>|<span data-ttu-id="1695c-124">型別**動作**。</span><span class="sxs-lookup"><span data-stu-id="1695c-124">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="1695c-125">使用 [記事本] 或其他文字編輯器，開啟中的 0C2_Request.xml 檔案\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾，然後複製並貼上內容**服務內容**lobwebapplication 的欄位。</span><span class="sxs-lookup"><span data-stu-id="1695c-125">Using Notepad or another text editor, open the 0C2_Request.xml file in the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1695c-126">若要刪除現有的文字服務內容提交訊息] 表單的欄位中，將游標放在開頭文字，按下並按住**Shift**和**Ctrl**按鈕、 按一下**結束**，然後按一下 [**刪除**。</span><span class="sxs-lookup"><span data-stu-id="1695c-126">To delete the existing text in the Service Content field of the Submit Message form, place the cursor at the beginning of the text, press and hold the **Shift** and **Ctrl** buttons, click **End**, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="1695c-127">按一下**送出**提交 0 C 2 要求至 Contoso 電腦。</span><span class="sxs-lookup"><span data-stu-id="1695c-127">Click **Submit** to submit the 0C2 request to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="1695c-128">確認 Fabrikam 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="1695c-128">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="1695c-129">在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-129">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1695c-130">您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。</span><span class="sxs-lookup"><span data-stu-id="1695c-130">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="1695c-131">接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-131">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="1695c-132">類別 -99 的訊息代表錯誤。</span><span class="sxs-lookup"><span data-stu-id="1695c-132">A category -99 message signifies an error.</span></span> <span data-ttu-id="1695c-133">您可以使用**事件檢視器**來判斷實際的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-133">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="1695c-134">確認 Contoso 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="1695c-134">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="1695c-135">按一下 **[開始]**，依序指向 **[所有程式]**和 **[Microsoft SQL Server]**，然後按一下 **[SQL Server Management Studio]**。</span><span class="sxs-lookup"><span data-stu-id="1695c-135">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="1695c-136">在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="1695c-136">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1695c-137">如果未啟動 SQL Server 代理程式，以滑鼠右鍵按一下，然後再按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="1695c-137">If the SQL Server Agent is not started, right-click it, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="1695c-138">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="1695c-138">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="1695c-139">在\<資料表 > 文字對話方塊方塊中，選取**BTARNDATA**從清單中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1695c-139">In the \<table> text dialog box, select **BTARNDATA** from the list, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="1695c-140">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1695c-140">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="1695c-141">在**查詢**功能表上，按一下  **Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1695c-141">On the **Query** menu, click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="1695c-142">在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-142">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1695c-143">您應該會先收到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。</span><span class="sxs-lookup"><span data-stu-id="1695c-143">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="1695c-144">接著，您應該會收到類別 25 的訊息，表示收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-144">You should then receive a category 25 message signifying the receipt acknowledgement message.</span></span>  
  
8.  <span data-ttu-id="1695c-145">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1695c-145">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="1695c-146">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1695c-146">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="1695c-147">在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="1695c-147">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1695c-148">您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。</span><span class="sxs-lookup"><span data-stu-id="1695c-148">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="1695c-149">您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。</span><span class="sxs-lookup"><span data-stu-id="1695c-149">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1695c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1695c-150">See Also</span></span>  
 <span data-ttu-id="1695c-151">[步驟 2： 提交 0 C 4 查詢](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md) </span><span class="sxs-lookup"><span data-stu-id="1695c-151">[Step 2: Submitting a 0C4 Query](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md) </span></span>  
 [<span data-ttu-id="1695c-152">BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="1695c-152">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)