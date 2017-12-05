---
title: "建立價格與可用性要求使用 Fabrikam 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating requests
ms.assetid: 6e4f4589-8f01-4b9e-93ee-c9371f32e04a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0619dc77496fd1547505221ff2f437bf486fb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-price-and-availability-request-with-the-fabrikam-sample"></a><span data-ttu-id="974ec-102">使用 Fabrikam 範例建立價格與可用性要求</span><span class="sxs-lookup"><span data-stu-id="974ec-102">Creating a Price and Availability Request with the Fabrikam Sample</span></span>
<span data-ttu-id="974ec-103">在此步驟中，您將使用 LOBWebApplication 工具建立「3A2 價格與可用性」要求。</span><span class="sxs-lookup"><span data-stu-id="974ec-103">In this step, you create a 3A2 Price and Availability request using the LOBWebApplication tool.</span></span>  
  
### <a name="to-submit-a-3a2-price-and-availability-request-to-contoso"></a><span data-ttu-id="974ec-104">提交 3A2 價格與可用性要求至 Contoso</span><span class="sxs-lookup"><span data-stu-id="974ec-104">To submit a 3A2 Price and Availability request to Contoso</span></span>  
  
1.  <span data-ttu-id="974ec-105">在 Internet Explorer 中，移至 http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx。</span><span class="sxs-lookup"><span data-stu-id="974ec-105">In Internet Explorer, move to http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="974ec-106">在**LOBWebApplication**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="974ec-106">On the **LOBWebApplication** page, do the following:</span></span>  
  
    |<span data-ttu-id="974ec-107">使用</span><span class="sxs-lookup"><span data-stu-id="974ec-107">Use this</span></span>|<span data-ttu-id="974ec-108">動作</span><span class="sxs-lookup"><span data-stu-id="974ec-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="974ec-109">**主要組織**</span><span class="sxs-lookup"><span data-stu-id="974ec-109">**Home Organization**</span></span>|<span data-ttu-id="974ec-110">型別**FABRIKAM**。</span><span class="sxs-lookup"><span data-stu-id="974ec-110">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="974ec-111">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="974ec-111">**Partner Organization**</span></span>|<span data-ttu-id="974ec-112">型別**CONTOSO**。</span><span class="sxs-lookup"><span data-stu-id="974ec-112">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="974ec-113">**PIP 代碼**</span><span class="sxs-lookup"><span data-stu-id="974ec-113">**PIP Code**</span></span>|<span data-ttu-id="974ec-114">型別**3A2**。</span><span class="sxs-lookup"><span data-stu-id="974ec-114">Type **3A2**.</span></span>|  
    |<span data-ttu-id="974ec-115">**PIP 版本**</span><span class="sxs-lookup"><span data-stu-id="974ec-115">**PIP Version**</span></span>|<span data-ttu-id="974ec-116">型別**R02.00.00A**。</span><span class="sxs-lookup"><span data-stu-id="974ec-116">Type **R02.00.00A**.</span></span>|  
    |<span data-ttu-id="974ec-117">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="974ec-117">**Message Category**</span></span>|<span data-ttu-id="974ec-118">型別**動作**。</span><span class="sxs-lookup"><span data-stu-id="974ec-118">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="974ec-119">使用 [記事本] 或其他文字編輯器，開啟**3A2_Request.xml**檔案在 C:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder然後複製並貼到文字放到**服務內容**LOBWebApplication 工具中的欄位。</span><span class="sxs-lookup"><span data-stu-id="974ec-119">Using Notepad or another text editor, open the **3A2_Request.xml** file in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder and copy and paste the text into the **Service Content** field in the LOBWebApplication tool.</span></span>  
  
4.  <span data-ttu-id="974ec-120">按一下**送出**提交 3A2 要求至 Contoso。</span><span class="sxs-lookup"><span data-stu-id="974ec-120">Click **Submit** to submit the 3A2 request to Contoso.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="974ec-121">確認 Fabrikam 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="974ec-121">To verify successful communication on the Fabrikam computer</span></span>  
  
1.  <span data-ttu-id="974ec-122">在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-122">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="974ec-123">您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。</span><span class="sxs-lookup"><span data-stu-id="974ec-123">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="974ec-124">接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-124">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="974ec-125">類別 -99 的訊息代表錯誤。</span><span class="sxs-lookup"><span data-stu-id="974ec-125">A category -99 message signifies an error.</span></span> <span data-ttu-id="974ec-126">您可以使用**事件檢視器**來判斷實際的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-126">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
2.  <span data-ttu-id="974ec-127">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="974ec-127">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
3.  <span data-ttu-id="974ec-128">在 連接到伺服器 對話方塊中**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下 **連接**.</span><span class="sxs-lookup"><span data-stu-id="974ec-128">In the Connect to Server dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="974ec-129">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="974ec-129">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
5.  <span data-ttu-id="974ec-130">在**\<資料表\>文字**對話方塊中，選取**BTARNDATA**從清單中。</span><span class="sxs-lookup"><span data-stu-id="974ec-130">In the **\<table\> text** dialog box, select **BTARNDATA** from the list.</span></span>  
  
6.  <span data-ttu-id="974ec-131">在**SQL**視窗中，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="974ec-131">In the **SQL** window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
7.  <span data-ttu-id="974ec-132">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="974ec-132">Click **Execute** to run the SQL statement.</span></span>  
  
8.  <span data-ttu-id="974ec-133">在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-133">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="974ec-134">您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。</span><span class="sxs-lookup"><span data-stu-id="974ec-134">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="974ec-135">您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。</span><span class="sxs-lookup"><span data-stu-id="974ec-135">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span> <span data-ttu-id="974ec-136">您也可以透過 ServiceContent 欄位確認回應結果。</span><span class="sxs-lookup"><span data-stu-id="974ec-136">You can also use the ServiceContent field to verify the response.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="974ec-137">確認 Contoso 電腦成功進行通訊</span><span class="sxs-lookup"><span data-stu-id="974ec-137">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="974ec-138">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="974ec-138">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="974ec-139">在 連接到伺服器 對話方塊中**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下 **連接**.</span><span class="sxs-lookup"><span data-stu-id="974ec-139">In the Connect to Server dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="974ec-140">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="974ec-140">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="974ec-141">在**\<資料表\>文字**對話方塊中，選取**BTARNDATA**從清單中。</span><span class="sxs-lookup"><span data-stu-id="974ec-141">In the **\<table\> text** dialog box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="974ec-142">在**SQL**視窗中，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="974ec-142">In the **SQL** window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="974ec-143">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="974ec-143">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="974ec-144">在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-144">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="974ec-145">您應該會先收到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。</span><span class="sxs-lookup"><span data-stu-id="974ec-145">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="974ec-146">接著，您應該會收到類別 25 的訊息，表示收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-146">You should then receive a category 25 message signifying the receipt acknowledgement message.</span></span>  
  
8.  <span data-ttu-id="974ec-147">在**SQL**視窗中，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="974ec-147">In the **SQL** window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="974ec-148">按一下**Execute**執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="974ec-148">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="974ec-149">在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="974ec-149">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="974ec-150">您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。</span><span class="sxs-lookup"><span data-stu-id="974ec-150">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="974ec-151">您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。</span><span class="sxs-lookup"><span data-stu-id="974ec-151">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974ec-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="974ec-152">See Also</span></span>  
 [<span data-ttu-id="974ec-153">私用程序教學課程</span><span class="sxs-lookup"><span data-stu-id="974ec-153">Private Process Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-process-tutorial.md)