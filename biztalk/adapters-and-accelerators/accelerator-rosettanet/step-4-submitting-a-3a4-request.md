---
title: "步驟 4： 提交 3A4 要求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 2d812cbc-51bc-48d5-b0b2-3698d33664ec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2436d33033163b32c4ead0fdab807b7db0b0158f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-submitting-a-3a4-request"></a><span data-ttu-id="bc175-102">步驟 4： 提交 3A4 要求</span><span class="sxs-lookup"><span data-stu-id="bc175-102">Step 4: Submitting a 3A4 Request</span></span>
<span data-ttu-id="bc175-103">在此步驟中，您將使用「3A4 - 訂單要求」的夥伴介面程序 (PIP) 來準備並提交要求。</span><span class="sxs-lookup"><span data-stu-id="bc175-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 3A4 - Request Purchase Order.</span></span> <span data-ttu-id="bc175-104">這個 PIP 可以讓購買者組織提交訂單要求至供應商。</span><span class="sxs-lookup"><span data-stu-id="bc175-104">This PIP enables a buyer organization to submit a purchase order request to a supplier.</span></span> <span data-ttu-id="bc175-105">一般而言，當您使用「3A2 - 要求價格與可用性」PIP 執行產品可用性查詢之後，就會發出「3A4 - 訂單要求」。</span><span class="sxs-lookup"><span data-stu-id="bc175-105">Generally, you request the 3A4 - Request Purchase Order after running a product availability query using the 3A2 - Request Price and Availability PIP.</span></span> <span data-ttu-id="bc175-106">3A4 PIP 是傳送回條確認的非同步 PIP。</span><span class="sxs-lookup"><span data-stu-id="bc175-106">The 3A4 PIP is an asynchronous PIP that sends receipt acknowledgements.</span></span>  
  
 <span data-ttu-id="bc175-107">![&#60;沒有變更 &#62;] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a4flow.gif "RN3_Intro_EETut_3A4Flow")</span><span class="sxs-lookup"><span data-stu-id="bc175-107">![&#60;No Change&#62;](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a4flow.gif "RN3_Intro_EETut_3A4Flow")</span></span>  
  
### <a name="to-submit-a-3a4---request-purchase-order"></a><span data-ttu-id="bc175-108">提交 3A4 - 訂單要求</span><span class="sxs-lookup"><span data-stu-id="bc175-108">To submit a 3A4 - Request Purchase Order</span></span>  
  
1.  <span data-ttu-id="bc175-109">在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。</span><span class="sxs-lookup"><span data-stu-id="bc175-109">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="bc175-110">在**提交訊息**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bc175-110">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="bc175-111">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="bc175-111">**Use this**</span></span>|<span data-ttu-id="bc175-112">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="bc175-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="bc175-113">**主要組織**</span><span class="sxs-lookup"><span data-stu-id="bc175-113">**Home Organization**</span></span>|<span data-ttu-id="bc175-114">型別**FABRIKAM**。</span><span class="sxs-lookup"><span data-stu-id="bc175-114">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="bc175-115">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="bc175-115">**Partner Organization**</span></span>|<span data-ttu-id="bc175-116">型別**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="bc175-116">Type **Contoso**.</span></span>|  
    |<span data-ttu-id="bc175-117">**Pip 代碼**</span><span class="sxs-lookup"><span data-stu-id="bc175-117">**Pip Code**</span></span>|<span data-ttu-id="bc175-118">型別**3A4**。</span><span class="sxs-lookup"><span data-stu-id="bc175-118">Type **3A4**.</span></span>|  
    |<span data-ttu-id="bc175-119">**Pip 版本**</span><span class="sxs-lookup"><span data-stu-id="bc175-119">**Pip Version**</span></span>|<span data-ttu-id="bc175-120">型別**V02.02.00**。</span><span class="sxs-lookup"><span data-stu-id="bc175-120">Type **V02.02.00**.</span></span>|  
    |<span data-ttu-id="bc175-121">**Pip 執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="bc175-121">**Pip Instance ID**</span></span>|<span data-ttu-id="bc175-122">型別**3A4_Test**。</span><span class="sxs-lookup"><span data-stu-id="bc175-122">Type **3A4_Test**.</span></span> <span data-ttu-id="bc175-123">**重要事項：**為了避免發生重複訊息識別碼錯誤，您必須確定**Pip 執行個體識別碼**都是唯一的每個您所提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-123">**Important:**  To avoid duplicate message ID errors, you must make sure that the **Pip Instance ID** is unique for each message that you submit.</span></span> <span data-ttu-id="bc175-124">如果將來要執行 3A4 測試，您必須變更此欄位。</span><span class="sxs-lookup"><span data-stu-id="bc175-124">If you run the 3A4 test in the future, you will have to change this field.</span></span>|  
    |<span data-ttu-id="bc175-125">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="bc175-125">**Message Category**</span></span>|<span data-ttu-id="bc175-126">型別**動作**。</span><span class="sxs-lookup"><span data-stu-id="bc175-126">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="bc175-127">使用 [記事本] 或其他文字編輯器，開啟中的 3A4_Request.xml 檔案\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾，然後複製並貼上內容**服務內容**lobwebapplication 的欄位。</span><span class="sxs-lookup"><span data-stu-id="bc175-127">Using Notepad or another text editor, open the 3A4_Request.xml file in the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
4.  <span data-ttu-id="bc175-128">按一下**送出**提交 3A4 要求至 Contoso 電腦。</span><span class="sxs-lookup"><span data-stu-id="bc175-128">Click **Submit** to submit the 3A4 request to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="bc175-129">確認 Fabrikam 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="bc175-129">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="bc175-130">在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-130">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc175-131">您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。</span><span class="sxs-lookup"><span data-stu-id="bc175-131">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="bc175-132">接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-132">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="bc175-133">類別 -99 的訊息代表錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc175-133">A category -99 message signifies an error.</span></span> <span data-ttu-id="bc175-134">您可以使用**事件檢視器**來判斷實際的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-134">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="bc175-135">確認 Contoso 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="bc175-135">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="bc175-136">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="bc175-136">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="bc175-137">在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="bc175-137">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="bc175-138">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="bc175-138">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="bc175-139">在\<資料表 > 文字對話方塊方塊中，選取**BTARNDATA**從清單中。</span><span class="sxs-lookup"><span data-stu-id="bc175-139">In the \<table> text dialog box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="bc175-140">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="bc175-140">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="bc175-141">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bc175-141">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="bc175-142">在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-142">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc175-143">您應該會先收到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。</span><span class="sxs-lookup"><span data-stu-id="bc175-143">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="bc175-144">接著，您應該會收到類別 25 的訊息，表示收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-144">You should then receive a category 25 message signifying the receipt acknowledegment message.</span></span>  
  
8.  <span data-ttu-id="bc175-145">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="bc175-145">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="bc175-146">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bc175-146">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="bc175-147">在查詢視窗中，在**結果** 窗格中，確認您看到一個外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="bc175-147">In the Query window, in the **Results** pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc175-148">您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。</span><span class="sxs-lookup"><span data-stu-id="bc175-148">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="bc175-149">您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。</span><span class="sxs-lookup"><span data-stu-id="bc175-149">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc175-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc175-150">See Also</span></span>  
 <span data-ttu-id="bc175-151">[雙向動作教學課程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="bc175-151">[Double Action Tutorial](../../adapters-and-accelerators/accelerator-rosettanet/double-action-tutorial.md) </span></span>  
 [<span data-ttu-id="bc175-152">BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="bc175-152">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)