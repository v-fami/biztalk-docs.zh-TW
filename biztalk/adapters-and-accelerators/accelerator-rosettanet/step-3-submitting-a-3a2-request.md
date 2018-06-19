---
title: 步驟 3： 提交 3A2 要求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, submitting requests
ms.assetid: 09f22be8-6d7d-48bf-862b-73248bae0506
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312e5980636d211f1e023331826e016eb141eb4b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967532"
---
# <a name="step-3-submitting-a-3a2-request"></a><span data-ttu-id="11d41-102">步驟 3： 提交 3A2 要求</span><span class="sxs-lookup"><span data-stu-id="11d41-102">Step 3: Submitting a 3A2 Request</span></span>
<span data-ttu-id="11d41-103">在此步驟中，您將使用夥伴介面程序 (PIP) 3A2 準備並提交「要求價格與可用性」要求。</span><span class="sxs-lookup"><span data-stu-id="11d41-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 3A2 - Request Price and Availability.</span></span> <span data-ttu-id="11d41-104">這個 PIP 可以讓購買者組織取得特定產品的資訊，例如價格以及可用單位。</span><span class="sxs-lookup"><span data-stu-id="11d41-104">This PIP enables a buyer organization to obtain information about a certain product, such as price and number of available units.</span></span> <span data-ttu-id="11d41-105">購買者稍後可以透過商務規則處理這項資訊，以決定是否要向供應商購買產品。</span><span class="sxs-lookup"><span data-stu-id="11d41-105">The buyer can then process that information through business rules to determine whether to purchase the product from the supplier.</span></span>  
  
### <a name="to-submit-a-3a2---request-price-and-availability"></a><span data-ttu-id="11d41-106">提交 3A2 - 要求價格與可用性</span><span class="sxs-lookup"><span data-stu-id="11d41-106">To submit a 3A2 - Request Price and Availability</span></span>  
  
1.  <span data-ttu-id="11d41-107">在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。</span><span class="sxs-lookup"><span data-stu-id="11d41-107">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="11d41-108">在**提交訊息**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="11d41-108">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="11d41-109">使用</span><span class="sxs-lookup"><span data-stu-id="11d41-109">Use this</span></span>|<span data-ttu-id="11d41-110">動作</span><span class="sxs-lookup"><span data-stu-id="11d41-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="11d41-111">**主要組織**</span><span class="sxs-lookup"><span data-stu-id="11d41-111">**Home Organization**</span></span>|<span data-ttu-id="11d41-112">型別**FABRIKAM**。</span><span class="sxs-lookup"><span data-stu-id="11d41-112">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="11d41-113">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="11d41-113">**Partner Organization**</span></span>|<span data-ttu-id="11d41-114">型別**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="11d41-114">Type **Contoso**.</span></span>|  
    |<span data-ttu-id="11d41-115">**Pip 代碼**</span><span class="sxs-lookup"><span data-stu-id="11d41-115">**Pip Code**</span></span>|<span data-ttu-id="11d41-116">型別**3A2**。</span><span class="sxs-lookup"><span data-stu-id="11d41-116">Type **3A2**.</span></span> <span data-ttu-id="11d41-117">**重要事項：** 為了避免發生重複訊息識別碼錯誤，您必須確定**Pip**都是唯一的每個您所提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-117">**Important:**  To avoid duplicate message ID errors, you must make sure that the **Pip** is unique for each message that you submit.</span></span> <span data-ttu-id="11d41-118">如果您將來要執行 3A2 測試，則必須變更此欄位。</span><span class="sxs-lookup"><span data-stu-id="11d41-118">If you run the 3A2 test in the future, you have to change this field.</span></span>|  
    |<span data-ttu-id="11d41-119">**Pip 版本**</span><span class="sxs-lookup"><span data-stu-id="11d41-119">**Pip Version**</span></span>|<span data-ttu-id="11d41-120">型別**R02.00.00A**。</span><span class="sxs-lookup"><span data-stu-id="11d41-120">Type **R02.00.00A**.</span></span>|  
    |<span data-ttu-id="11d41-121">**Pip 執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="11d41-121">**Pip Instance ID**</span></span>|<span data-ttu-id="11d41-122">型別**3A2_Test**。</span><span class="sxs-lookup"><span data-stu-id="11d41-122">Type **3A2_Test**.</span></span>|  
    |<span data-ttu-id="11d41-123">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="11d41-123">**Message Category**</span></span>|<span data-ttu-id="11d41-124">型別**動作**。</span><span class="sxs-lookup"><span data-stu-id="11d41-124">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="11d41-125">使用 [記事本] 或其他文字編輯器，開啟中的 3A2_Request.xml 檔案*\<磁碟機\>*: \程式 Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾，然後複製並貼上內容**服務內容**欄位LOBWebApplication。</span><span class="sxs-lookup"><span data-stu-id="11d41-125">Using Notepad or another text editor, open the file 3A2_Request.xml in the *\<drive\>*:\ Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
4.  <span data-ttu-id="11d41-126">按一下**送出**提交 3A2 要求至 Contoso 電腦。</span><span class="sxs-lookup"><span data-stu-id="11d41-126">Click **Submit** to submit the 3A2 request to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="11d41-127">確認 Fabrikam 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="11d41-127">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="11d41-128">在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-128">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11d41-129">您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。</span><span class="sxs-lookup"><span data-stu-id="11d41-129">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="11d41-130">接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-130">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="11d41-131">類別 -99 的訊息代表錯誤。</span><span class="sxs-lookup"><span data-stu-id="11d41-131">A category -99 message signifies an error.</span></span> <span data-ttu-id="11d41-132">您可以使用**事件檢視器**來判斷實際的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-132">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="11d41-133">確認 Contoso 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="11d41-133">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="11d41-134">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="11d41-134">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="11d41-135">在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="11d41-135">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="11d41-136">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="11d41-136">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="11d41-137">在\<資料表\>文字方塊中，選取**BTARNDATA**從清單中。</span><span class="sxs-lookup"><span data-stu-id="11d41-137">In the \<table\> text box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="11d41-138">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="11d41-138">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="11d41-139">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="11d41-139">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="11d41-140">在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-140">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11d41-141">您應該會先收到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。</span><span class="sxs-lookup"><span data-stu-id="11d41-141">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="11d41-142">接著，您應該會收到類別 25 的訊息，表示收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-142">You should then receive a category 25 message signifying the receipt acknowledgement message.</span></span>  
  
8.  <span data-ttu-id="11d41-143">在 SQL 視窗中輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="11d41-143">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="11d41-144">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="11d41-144">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="11d41-145">在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="11d41-145">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11d41-146">您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。</span><span class="sxs-lookup"><span data-stu-id="11d41-146">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="11d41-147">您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。</span><span class="sxs-lookup"><span data-stu-id="11d41-147">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d41-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="11d41-148">See Also</span></span>  
 <span data-ttu-id="11d41-149">[步驟 4： 提交 3A4 要求](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md) </span><span class="sxs-lookup"><span data-stu-id="11d41-149">[Step 4: Submitting a 3A4 Request](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md) </span></span>  
 [<span data-ttu-id="11d41-150">BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="11d41-150">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)