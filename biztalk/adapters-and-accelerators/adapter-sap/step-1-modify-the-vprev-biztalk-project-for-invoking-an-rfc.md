---
title: 步驟 1： 修改 vPrev BizTalk 專案的叫用 RFC |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, modifying previous version of BizTalk project for invoking an RFC
- migration
ms.assetid: 2d4a6cd7-d216-4e0f-8f82-41e044cd325b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e2624ede6d2710db2d82311c2f452f8be372aa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969647"
---
# <a name="step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc"></a><span data-ttu-id="ac85e-102">步驟 1： 修改 vPrev BizTalk 專案的叫用 RFC</span><span class="sxs-lookup"><span data-stu-id="ac85e-102">Step 1: Modify the vPrev BizTalk Project for Invoking an RFC</span></span>
<span data-ttu-id="ac85e-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="ac85e-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="ac85e-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="ac85e-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="ac85e-105">**目標：** 在此步驟中，您必須進行下列變更以現有的 vPrev BizTalk 專案：</span><span class="sxs-lookup"><span data-stu-id="ac85e-105">**Objective:** In this step, you make the following changes to the existing vPrev BizTalk project:</span></span>  
  
- <span data-ttu-id="ac85e-106">產生中繼資料的使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-106">Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
- <span data-ttu-id="ac85e-107">將叫用 RFC 使用 vPrev SAP 配接器的要求訊息來叫用 RFC 使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-107">Map the request message for invoking the RFC using the vPrev SAP adapter to a request message for invoking the RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
- <span data-ttu-id="ac85e-108">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]vPrev SAP 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="ac85e-108">Map the response message received using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the response message for the vPrev SAP adapter.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="ac85e-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="ac85e-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="ac85e-110">您必須叫用 SD_RFC_CUSTOMER_GET RFC，SAP 系統中的 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ac85e-110">You must have a vPrev BizTalk project to invoke the SD_RFC_CUSTOMER_GET RFC in the SAP system.</span></span>  
  
### <a name="to-modify-the-vprev-biztalk-project"></a><span data-ttu-id="ac85e-111">若要修改 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="ac85e-111">To modify the vPrev BizTalk project</span></span>  
  
1. <span data-ttu-id="ac85e-112">產生中繼資料的使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-112">Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="ac85e-113">您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ac85e-113">You can use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata.</span></span>  
  
    <span data-ttu-id="ac85e-114">如需如何產生 Rfc 的中繼資料的指示，請參閱 <<c0> [ 瀏覽、 搜尋及取得中繼資料，在 SAP 中的 RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="ac85e-114">For instructions on how to generate metadata for RFCs, see [Browse, search and get metadata for RFC operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md).</span></span> <span data-ttu-id="ac85e-115">結構描述產生之後，具有類似名稱的檔案*SapBindingSchema.xsd*會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ac85e-115">After the schema is generated, a file with the name similar to *SapBindingSchema.xsd* is added to the BizTalk project.</span></span> <span data-ttu-id="ac85e-116">此檔案包含的結構描述來叫用使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-116">This file contains the schema for invoking the SD_RFC_CUSTOMER_GET using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
2. <span data-ttu-id="ac85e-117">產生的 SD_RFC_CUSTOMER_GET RFC 的中繼資料時，也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="ac85e-117">Generating the metadata for the SD_RFC_CUSTOMER_GET RFC also creates a port binding file.</span></span> <span data-ttu-id="ac85e-118">在下一個步驟中，此繫結檔案將用於建立 Wcf-custom 傳送埠將訊息傳送至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ac85e-118">In the next step, this binding file will be used to create a WCF-Custom send port to send messages to the SAP system.</span></span> <span data-ttu-id="ac85e-119">作業的 SOAP 動作也會設定為您要為其產生中繼資料作業中。</span><span class="sxs-lookup"><span data-stu-id="ac85e-119">The SOAP action for the operation is also set to the operation for which you generated metadata.</span></span> <span data-ttu-id="ac85e-120">比方說，如果您產生 SD_RFC_CUSTOMER_GET rfc 的中繼資料，傳送埠上的 SOAP 動作中的作業名稱會 「 SD_RFC_CUSTOMER_GET"。</span><span class="sxs-lookup"><span data-stu-id="ac85e-120">For example, if you generate metadata for the SD_RFC_CUSTOMER_GET RFC, the operation name in the SOAP action on the send port will be “SD_RFC_CUSTOMER_GET”.</span></span> <span data-ttu-id="ac85e-121">不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。</span><span class="sxs-lookup"><span data-stu-id="ac85e-121">However, the operation name on the logical send port that you create as part of the orchestration could be different, for example, “Operation_1”.</span></span> <span data-ttu-id="ac85e-122">如此一來，當您將訊息傳送到 SAP 系統使用的傳送埠時，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac85e-122">As a result, when you send messages to the SAP system using the send port, you get an error.</span></span> <span data-ttu-id="ac85e-123">若要避免這個問題，請確定邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="ac85e-123">To prevent this, make sure the operation name on the logical send port in your orchestration is the same as the operation name for which you generated metadata.</span></span>  
  
    <span data-ttu-id="ac85e-124">因此，在本教學課程中，由於您會產生 SD_RFC_CUSTOMER_GET RFC 的中繼資料，變更 「 SD_RFC_CUSTOMER_GET"的邏輯傳送連接埠作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac85e-124">So, in the case of this tutorial, because you generate metadata for the SD_RFC_CUSTOMER_GET RFC, change the name of the logical send port operation to “SD_RFC_CUSTOMER_GET”.</span></span>  
  
3. <span data-ttu-id="ac85e-125">要求訊息中，將使用 vPrev SAP 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-125">For the request message, map the schema generated using vPrev SAP adapter to the schema generated using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
   1. <span data-ttu-id="ac85e-126">將 BizTalk 對應工具加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="ac85e-126">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="ac85e-127">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-127">Right-click the BizTalk project, point to **Add**, and then click **New Item**.</span></span>  
  
       <span data-ttu-id="ac85e-128">在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-128">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="ac85e-129">從右窗格中，選取**地圖**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-129">From the right pane, select **Map**.</span></span> <span data-ttu-id="ac85e-130">指定對應名稱，例如**RequestMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-130">Specify a name for the map, such as **RequestMap.btm**.</span></span> <span data-ttu-id="ac85e-131">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-131">Click **Add**.</span></span>  
  
   2. <span data-ttu-id="ac85e-132">從來源結構描述 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-132">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
   3. <span data-ttu-id="ac85e-133">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev SAP 配接器的要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ac85e-133">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the vPrev SAP adapter.</span></span> <span data-ttu-id="ac85e-134">本教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-134">For this tutorial, select *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*,and then click **OK**.</span></span>  
  
   4. <span data-ttu-id="ac85e-135">在 **來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Request*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-135">In the **Root Node for Source Schema** dialog box, select *SD_RFC_CUSTOMER_GET_Request*, and then click **OK**.</span></span>  
  
   5. <span data-ttu-id="ac85e-136">從目的結構描述 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-136">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
   6. <span data-ttu-id="ac85e-137">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-137">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="ac85e-138">本教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-138">For this tutorial, select *SAP_Migration.SapBindingSchema*, and then click OK.</span></span>  
  
   7. <span data-ttu-id="ac85e-139">在 **目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-139">In the **Root Node for Target Schema** dialog box, select *SD_RFC_CUSTOMER_GET*, and then click **OK**.</span></span>  
  
       <span data-ttu-id="ac85e-140">對應在這兩個結構描述中的個別項目，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ac85e-140">Map the respective elements in both the schemas as illustrated in the following figure.</span></span> <span data-ttu-id="ac85e-141">對應使用 「 字串左空白位置修剪 」 運算質的 CUSTOMER_T 項目。</span><span class="sxs-lookup"><span data-stu-id="ac85e-141">Map the CUSTOMER_T element using a String Left Trim functoid.</span></span> <span data-ttu-id="ac85e-142">若要這樣做，請從**工具箱**，拖曳**字串左空白位置修剪**運算質放在對應工具格線。</span><span class="sxs-lookup"><span data-stu-id="ac85e-142">To do so, from the **Toolbox**, drag the **String Left Trim** functoid and drop it on the mapper grid.</span></span> <span data-ttu-id="ac85e-143">連接**CUSTOMER_T**運算質將來源結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="ac85e-143">Connect the **CUSTOMER_T** element in the source schema to the functoid.</span></span> <span data-ttu-id="ac85e-144">同樣地，連接**CUSTOMER_T**運算質至目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="ac85e-144">Similarly, connect the **CUSTOMER_T** element in the destination schema to the functoid.</span></span> <span data-ttu-id="ac85e-145">下圖說明兩個項目透過運算質的對應方式。</span><span class="sxs-lookup"><span data-stu-id="ac85e-145">The following figure illustrates how the two elements are mapped via the functoid.</span></span>  
  
       <span data-ttu-id="ac85e-146">![對應配接器版本之間的要求訊息](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")</span><span class="sxs-lookup"><span data-stu-id="ac85e-146">![Map the request messages between adapter versions](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="ac85e-147">「 字串左空白位置修剪 」 運算質的詳細資訊，請參閱 「 字串左空白位置修剪運算質 」，網址[ http://go.microsoft.com/fwlink/?LinkId=105774 ](http://go.microsoft.com/fwlink/?LinkId=105774)。</span><span class="sxs-lookup"><span data-stu-id="ac85e-147">For more information about the String Left Trim functoid, see "String Left Trim Functoid" at [http://go.microsoft.com/fwlink/?LinkId=105774](http://go.microsoft.com/fwlink/?LinkId=105774).</span></span>  
  
   8. <span data-ttu-id="ac85e-148">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="ac85e-148">Save the map.</span></span>  
  
4. <span data-ttu-id="ac85e-149">回應訊息，將使用 vPrev SAP 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-149">For the response message, map the schema generated using vPrev SAP adapter to the schema generated using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
   1. <span data-ttu-id="ac85e-150">將 BizTalk 對應工具加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="ac85e-150">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="ac85e-151">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-151">Right-click the BizTalk project, point to **Add**, and click **New Item**.</span></span>  
  
       <span data-ttu-id="ac85e-152">在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-152">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="ac85e-153">從右窗格中，選取**地圖**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-153">From the right pane, select **Map**.</span></span> <span data-ttu-id="ac85e-154">指定對應名稱，例如**ResponseMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-154">Specify a name for the map, such as **ResponseMap.btm**.</span></span> <span data-ttu-id="ac85e-155">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-155">Click **Add**.</span></span>  
  
   2. <span data-ttu-id="ac85e-156">從來源結構描述 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-156">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
   3. <span data-ttu-id="ac85e-157">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac85e-157">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="ac85e-158">本教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-158">For this tutorial, select *SAP_Migration.SapBindingSchema*, and then click **OK**.</span></span>  
  
   4. <span data-ttu-id="ac85e-159">在 **來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GETResponse*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-159">In the **Root Node for Source Schema** dialog box, select *SD_RFC_CUSTOMER_GETResponse*, and then click **OK**.</span></span>  
  
   5. <span data-ttu-id="ac85e-160">從目的結構描述 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-160">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
   6. <span data-ttu-id="ac85e-161">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev SAP 配接器的回應訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ac85e-161">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the vPrev SAP adapter.</span></span> <span data-ttu-id="ac85e-162">本教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-162">For this tutorial, select *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*, and then click **OK**.</span></span>  
  
   7. <span data-ttu-id="ac85e-163">在 **目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Response*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-163">In the **Root Node for Target Schema** dialog box, select *SD_RFC_CUSTOMER_GET_Response*, and then click **OK**.</span></span>  
  
   8. <span data-ttu-id="ac85e-164">對應在這兩個結構描述中的個別項目，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ac85e-164">Map the respective elements in both the schemas as illustrated in the following figure.</span></span>  
  
       <span data-ttu-id="ac85e-165">![對應的回應訊息，配接器版本之間](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")</span><span class="sxs-lookup"><span data-stu-id="ac85e-165">![Map the response messages between adapter versions](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")</span></span>  
  
   9. <span data-ttu-id="ac85e-166">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="ac85e-166">Save the map.</span></span>  
  
5. <span data-ttu-id="ac85e-167">儲存並建置 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="ac85e-167">Save and build the BizTalk solution.</span></span> <span data-ttu-id="ac85e-168">以滑鼠右鍵按一下方案，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-168">Right-click the solution, and then click **Build Solution**.</span></span>  
  
6. <span data-ttu-id="ac85e-169">部署該方案。</span><span class="sxs-lookup"><span data-stu-id="ac85e-169">Deploy the solution.</span></span> <span data-ttu-id="ac85e-170">以滑鼠右鍵按一下方案，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="ac85e-170">Right-click the solution, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ac85e-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ac85e-171">Next Steps</span></span>  
 <span data-ttu-id="ac85e-172">建立 Wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 在 BizTalk Server 管理主控台設定協調流程](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)。</span><span class="sxs-lookup"><span data-stu-id="ac85e-172">Create a WCF-Custom send port, and configure it to use the maps you created in this step, as described in [Step 2: Configure the Orchestration in BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac85e-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac85e-173">See Also</span></span>  
 [<span data-ttu-id="ac85e-174">教學課程 2：移轉 SAP RFC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="ac85e-174">Tutorial 2: Migrating an SAP RFC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)