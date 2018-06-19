---
title: 步驟 1： 叫用 RFC 修改 vPrev BizTalk 專案 |Microsoft 文件
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
ms.openlocfilehash: d1f967a268d8baca3ab12f29bbac4b9eccc3cd75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218102"
---
# <a name="step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc"></a><span data-ttu-id="6def7-102">步驟 1： 叫用 RFC 修改 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="6def7-102">Step 1: Modify the vPrev BizTalk Project for Invoking an RFC</span></span>
<span data-ttu-id="6def7-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="6def7-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="6def7-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="6def7-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="6def7-105">**目標：** 在此步驟中，您必須進行下列變更現有 vPrev BizTalk 專案：</span><span class="sxs-lookup"><span data-stu-id="6def7-105">**Objective:** In this step, you make the following changes to the existing vPrev BizTalk project:</span></span>  
  
-   <span data-ttu-id="6def7-106">產生使用 WCF 型 SD_RFC_CUSTOMER_GET RFC 的中繼資料[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-106">Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="6def7-107">叫用使用 vPrev SAP 配接器的要求訊息來叫用使用 WCF 為基礎的 RFC RFC 的要求訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-107">Map the request message for invoking the RFC using the vPrev SAP adapter to a request message for invoking the RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="6def7-108">使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]vPrev SAP 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="6def7-108">Map the response message received using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the response message for the vPrev SAP adapter.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="6def7-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="6def7-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="6def7-110">您必須在 SAP 系統中叫用 SD_RFC_CUSTOMER_GET RFC vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="6def7-110">You must have a vPrev BizTalk project to invoke the SD_RFC_CUSTOMER_GET RFC in the SAP system.</span></span>  
  
### <a name="to-modify-the-vprev-biztalk-project"></a><span data-ttu-id="6def7-111">若要修改 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="6def7-111">To modify the vPrev BizTalk project</span></span>  
  
1.  <span data-ttu-id="6def7-112">產生使用 WCF 型 SD_RFC_CUSTOMER_GET RFC 的中繼資料[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-112">Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="6def7-113">您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6def7-113">You can use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata.</span></span>  
  
     <span data-ttu-id="6def7-114">如需有關如何產生 rfc 的中繼資料的指示，請參閱[瀏覽、 搜尋和 get 中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="6def7-114">For instructions on how to generate metadata for RFCs, see [Browse, search and get metadata for RFC operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md).</span></span> <span data-ttu-id="6def7-115">結構描述產生之後，類似於名稱的檔案*SapBindingSchema.xsd*會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="6def7-115">After the schema is generated, a file with the name similar to *SapBindingSchema.xsd* is added to the BizTalk project.</span></span> <span data-ttu-id="6def7-116">這個檔案包含的結構描述叫用使用 WCF 型 SD_RFC_CUSTOMER_GET [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-116">This file contains the schema for invoking the SD_RFC_CUSTOMER_GET using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="6def7-117">產生 SD_RFC_CUSTOMER_GET RFC 的中繼資料時，也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="6def7-117">Generating the metadata for the SD_RFC_CUSTOMER_GET RFC also creates a port binding file.</span></span> <span data-ttu-id="6def7-118">在下一個步驟中，此繫結檔案，將用來建立 Wcf-custom 傳送埠將訊息傳送至 SAP 系統中。</span><span class="sxs-lookup"><span data-stu-id="6def7-118">In the next step, this binding file will be used to create a WCF-Custom send port to send messages to the SAP system.</span></span> <span data-ttu-id="6def7-119">作業的 SOAP 動作也會設為您產生的中繼資料作業。</span><span class="sxs-lookup"><span data-stu-id="6def7-119">The SOAP action for the operation is also set to the operation for which you generated metadata.</span></span> <span data-ttu-id="6def7-120">比方說，如果您的 SD_RFC_CUSTOMER_GET RFC 產生中繼資料，傳送埠上的 SOAP 動作中的作業名稱會"SD_RFC_CUSTOMER_GET"。</span><span class="sxs-lookup"><span data-stu-id="6def7-120">For example, if you generate metadata for the SD_RFC_CUSTOMER_GET RFC, the operation name in the SOAP action on the send port will be “SD_RFC_CUSTOMER_GET”.</span></span> <span data-ttu-id="6def7-121">不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。</span><span class="sxs-lookup"><span data-stu-id="6def7-121">However, the operation name on the logical send port that you create as part of the orchestration could be different, for example, “Operation_1”.</span></span> <span data-ttu-id="6def7-122">如此一來，當您傳送訊息至 SAP 系統使用的傳送埠時，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="6def7-122">As a result, when you send messages to the SAP system using the send port, you get an error.</span></span> <span data-ttu-id="6def7-123">若要防止這個情況，請確定在邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="6def7-123">To prevent this, make sure the operation name on the logical send port in your orchestration is the same as the operation name for which you generated metadata.</span></span>  
  
     <span data-ttu-id="6def7-124">因此，在此教學課程中，產生 SD_RFC_CUSTOMER_GET RFC 的中繼資料，因為變更名稱"SD_RFC_CUSTOMER_GET"的邏輯傳送連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="6def7-124">So, in the case of this tutorial, because you generate metadata for the SD_RFC_CUSTOMER_GET RFC, change the name of the logical send port operation to “SD_RFC_CUSTOMER_GET”.</span></span>  
  
3.  <span data-ttu-id="6def7-125">要求訊息時，將使用 vPrev SAP 配接器使用 WCF 為基礎所產生的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-125">For the request message, map the schema generated using vPrev SAP adapter to the schema generated using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="6def7-126">將 BizTalk 對應工具加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="6def7-126">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="6def7-127">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="6def7-127">Right-click the BizTalk project, point to **Add**, and then click **New Item**.</span></span>  
  
         <span data-ttu-id="6def7-128">在**加入新項目**對話方塊的左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="6def7-128">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="6def7-129">從右窗格中，選取**對應**。</span><span class="sxs-lookup"><span data-stu-id="6def7-129">From the right pane, select **Map**.</span></span> <span data-ttu-id="6def7-130">指定對應名稱，例如**RequestMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="6def7-130">Specify a name for the map, such as **RequestMap.btm**.</span></span> <span data-ttu-id="6def7-131">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="6def7-131">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6def7-132">從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="6def7-132">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
    3.  <span data-ttu-id="6def7-133">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取 vPrev SAP 配接器的要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="6def7-133">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the vPrev SAP adapter.</span></span> <span data-ttu-id="6def7-134">此教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-134">For this tutorial, select *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*,and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="6def7-135">在**來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Request*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-135">In the **Root Node for Source Schema** dialog box, select *SD_RFC_CUSTOMER_GET_Request*, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="6def7-136">從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="6def7-136">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
    6.  <span data-ttu-id="6def7-137">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-137">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="6def7-138">此教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6def7-138">For this tutorial, select *SAP_Migration.SapBindingSchema*, and then click OK.</span></span>  
  
    7.  <span data-ttu-id="6def7-139">在**目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-139">In the **Root Node for Target Schema** dialog box, select *SD_RFC_CUSTOMER_GET*, and then click **OK**.</span></span>  
  
         <span data-ttu-id="6def7-140">對應的結構描述中的個別項目，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="6def7-140">Map the respective elements in both the schemas as illustrated in the following figure.</span></span> <span data-ttu-id="6def7-141">對應 CUSTOMER_T 項目使用字串左空白位置修剪運算質。</span><span class="sxs-lookup"><span data-stu-id="6def7-141">Map the CUSTOMER_T element using a String Left Trim functoid.</span></span> <span data-ttu-id="6def7-142">若要這樣做，請從**工具箱**，拖曳**字串左空白位置修剪**運算質放在對應工具格線。</span><span class="sxs-lookup"><span data-stu-id="6def7-142">To do so, from the **Toolbox**, drag the **String Left Trim** functoid and drop it on the mapper grid.</span></span> <span data-ttu-id="6def7-143">連接**CUSTOMER_T** 」 運算質來源結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="6def7-143">Connect the **CUSTOMER_T** element in the source schema to the functoid.</span></span> <span data-ttu-id="6def7-144">同樣地，連接**CUSTOMER_T**運算質至目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="6def7-144">Similarly, connect the **CUSTOMER_T** element in the destination schema to the functoid.</span></span> <span data-ttu-id="6def7-145">下圖說明如何透過運算質對應兩個項目。</span><span class="sxs-lookup"><span data-stu-id="6def7-145">The following figure illustrates how the two elements are mapped via the functoid.</span></span>  
  
         <span data-ttu-id="6def7-146">![對應配接器版本之間的要求訊息](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")</span><span class="sxs-lookup"><span data-stu-id="6def7-146">![Map the request messages between adapter versions](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6def7-147">字串左空白位置修剪運算質的詳細資訊，請參閱 「 字串左空白位置修剪運算質 」，網址[http://go.microsoft.com/fwlink/?LinkId=105774](http://go.microsoft.com/fwlink/?LinkId=105774)。</span><span class="sxs-lookup"><span data-stu-id="6def7-147">For more information about the String Left Trim functoid, see "String Left Trim Functoid" at [http://go.microsoft.com/fwlink/?LinkId=105774](http://go.microsoft.com/fwlink/?LinkId=105774).</span></span>  
  
    8.  <span data-ttu-id="6def7-148">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="6def7-148">Save the map.</span></span>  
  
4.  <span data-ttu-id="6def7-149">回應訊息時，將使用 vPrev SAP 配接器使用 WCF 為基礎所產生的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-149">For the response message, map the schema generated using vPrev SAP adapter to the schema generated using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="6def7-150">將 BizTalk 對應工具加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="6def7-150">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="6def7-151">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="6def7-151">Right-click the BizTalk project, point to **Add**, and click **New Item**.</span></span>  
  
         <span data-ttu-id="6def7-152">在**加入新項目**對話方塊的左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="6def7-152">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="6def7-153">從右窗格中，選取**對應**。</span><span class="sxs-lookup"><span data-stu-id="6def7-153">From the right pane, select **Map**.</span></span> <span data-ttu-id="6def7-154">指定對應名稱，例如**ResponseMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="6def7-154">Specify a name for the map, such as **ResponseMap.btm**.</span></span> <span data-ttu-id="6def7-155">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="6def7-155">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6def7-156">從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="6def7-156">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
    3.  <span data-ttu-id="6def7-157">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6def7-157">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="6def7-158">此教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-158">For this tutorial, select *SAP_Migration.SapBindingSchema*, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="6def7-159">在**來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GETResponse*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-159">In the **Root Node for Source Schema** dialog box, select *SD_RFC_CUSTOMER_GETResponse*, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="6def7-160">從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="6def7-160">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
    6.  <span data-ttu-id="6def7-161">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取 vPrev SAP 配接器的回應訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="6def7-161">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the vPrev SAP adapter.</span></span> <span data-ttu-id="6def7-162">此教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-162">For this tutorial, select *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="6def7-163">在**目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Response*，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6def7-163">In the **Root Node for Target Schema** dialog box, select *SD_RFC_CUSTOMER_GET_Response*, and then click **OK**.</span></span>  
  
    8.  <span data-ttu-id="6def7-164">對應的結構描述中的個別項目，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="6def7-164">Map the respective elements in both the schemas as illustrated in the following figure.</span></span>  
  
         <span data-ttu-id="6def7-165">![對應配接器版本之間的回應訊息](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")</span><span class="sxs-lookup"><span data-stu-id="6def7-165">![Map the response messages between adapter versions](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")</span></span>  
  
    9. <span data-ttu-id="6def7-166">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="6def7-166">Save the map.</span></span>  
  
5.  <span data-ttu-id="6def7-167">儲存並建置 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="6def7-167">Save and build the BizTalk solution.</span></span> <span data-ttu-id="6def7-168">以滑鼠右鍵按一下方案，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="6def7-168">Right-click the solution, and then click **Build Solution**.</span></span>  
  
6.  <span data-ttu-id="6def7-169">部署該方案。</span><span class="sxs-lookup"><span data-stu-id="6def7-169">Deploy the solution.</span></span> <span data-ttu-id="6def7-170">以滑鼠右鍵按一下方案，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="6def7-170">Right-click the solution, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6def7-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6def7-171">Next Steps</span></span>  
 <span data-ttu-id="6def7-172">建立 Wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 在 BizTalk Server 管理主控台中設定協調流程](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)。</span><span class="sxs-lookup"><span data-stu-id="6def7-172">Create a WCF-Custom send port, and configure it to use the maps you created in this step, as described in [Step 2: Configure the Orchestration in BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6def7-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6def7-173">See Also</span></span>  
 [<span data-ttu-id="6def7-174">教學課程 2： 移轉 SAP RFC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="6def7-174">Tutorial 2: Migrating an SAP RFC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)