---
title: 步驟 1： 修改 vPrev BizTalk 專案中 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e3e22ac-126b-46ec-a6dc-3421ad721392
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5d55a5535d1f3f2234198d08393a314b1a304e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010567"
---
# <a name="step-1-modify-the-vprev-biztalk-project-in-oracle-database"></a><span data-ttu-id="593fa-102">步驟 1： 修改 vPrev BizTalk 專案中 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="593fa-102">Step 1: Modify the vPrev BizTalk Project in Oracle Database</span></span>
<span data-ttu-id="593fa-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="593fa-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="593fa-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="593fa-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="593fa-105">**目標：** 在此步驟中，您必須進行下列變更以現有的 vPrev BizTalk 專案：</span><span class="sxs-lookup"><span data-stu-id="593fa-105">**Objective:** In this step, you make the following changes to the existing vPrev BizTalk project:</span></span>  
  
- <span data-ttu-id="593fa-106">產生 SCOTT 的 Insert 作業的中繼資料。使用以 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-106">Generate metadata for the Insert operation on the SCOTT.CUSTOMER table using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
- <span data-ttu-id="593fa-107">執行插入作業使用 vPrev Oracle 資料庫配接器的要求訊息來執行 Insert 作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-107">Map the request message for performing an Insert operation using the vPrev Oracle database adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
- <span data-ttu-id="593fa-108">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]vPrev Oracle 資料庫配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="593fa-108">Map the response message received using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the response message for the vPrev Oracle database adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="593fa-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="593fa-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="593fa-110">您必須執行插入作業上 SCOTT vPrev BizTalk 專案。Oracle 資料庫中的 CUSTOMER 資料表。</span><span class="sxs-lookup"><span data-stu-id="593fa-110">You must have a vPrev BizTalk project to perform an Insert operation on the SCOTT.CUSTOMER table in the Oracle database.</span></span>  
  
## <a name="modify-the-vprev-biztalk-project"></a><span data-ttu-id="593fa-111">修改 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="593fa-111">Modify the vPrev BizTalk project</span></span>  
  
1. <span data-ttu-id="593fa-112">產生 SCOTT 的 Insert 作業的中繼資料。使用以 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-112">Generate metadata for the Insert operation on the SCOTT.CUSTOMER table using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="593fa-113">您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="593fa-113">You can use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata.</span></span>  
  
    <span data-ttu-id="593fa-114">如需有關如何產生中繼資料的指示，請參閱 <<c0> [ 取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="593fa-114">For instructions on how to generate metadata, see [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).</span></span> <span data-ttu-id="593fa-115">結構描述產生之後，具有類似名稱的檔案*OracleDBBindingSchema.xsd*會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="593fa-115">After the schema is generated, a file with the name similar to *OracleDBBindingSchema.xsd* is added to the BizTalk project.</span></span> <span data-ttu-id="593fa-116">此檔案包含傳送訊息至執行插入作業在 SCOTT 的結構描述。使用 WCF 型 Oracle 資料庫中的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-116">This file contains the schema for sending a message to perform an Insert operation on the SCOTT.CUSTOMER table in the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
2. <span data-ttu-id="593fa-117">產生插入作業的中繼資料時，也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="593fa-117">Generating the metadata for the Insert operation also creates a port binding file.</span></span> <span data-ttu-id="593fa-118">在下一個步驟中，此繫結檔案將用於建立 Wcf-custom 傳送埠將訊息傳送至 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="593fa-118">In the next step, this binding file will be used to create a WCF-Custom send port to send messages to the Oracle database.</span></span> <span data-ttu-id="593fa-119">作業的 SOAP 動作也會設定為您要為其產生中繼資料作業中。</span><span class="sxs-lookup"><span data-stu-id="593fa-119">The SOAP action for the operation is also set to the operation for which you generated metadata.</span></span> <span data-ttu-id="593fa-120">比方說，如果您產生插入作業的中繼資料，傳送埠上的 SOAP 動作中的作業名稱會是 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="593fa-120">For example, if you generate metadata for the Insert operation, the operation name in the SOAP action on the send port will be “Insert”.</span></span> <span data-ttu-id="593fa-121">不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。</span><span class="sxs-lookup"><span data-stu-id="593fa-121">However, the operation name on the logical send port that you create as part of the orchestration could be different, for example, “Operation_1”.</span></span> <span data-ttu-id="593fa-122">如此一來，當您將訊息傳送到 Oracle 資料庫使用的傳送埠時，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="593fa-122">As a result, when you send messages to the Oracle database using the send port, you get an error.</span></span> <span data-ttu-id="593fa-123">若要避免這個問題，請確定邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="593fa-123">To prevent this, make sure the operation name on the logical send port in your orchestration is the same as the operation name for which you generated metadata.</span></span>  
  
    <span data-ttu-id="593fa-124">因此，本教學課程中，如果您產生插入作業的中繼資料，因為變更名稱"Insert"的邏輯傳送連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="593fa-124">So, in case of this tutorial, because you generate metadata for the Insert operation, change the name of the logical send port operation to “Insert”.</span></span>  
  
3. <span data-ttu-id="593fa-125">要求訊息中，將使用 vPrev Oracle 資料庫配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-125">For the request message, map the schema generated using vPrev Oracle database adapter to the schema generated using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
   1. <span data-ttu-id="593fa-126">將 BizTalk 對應工具加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="593fa-126">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="593fa-127">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="593fa-127">Right-click the BizTalk project, point to **Add**, and click **New Item**.</span></span>  
  
       <span data-ttu-id="593fa-128">在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="593fa-128">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="593fa-129">從右窗格中，選取**地圖**。</span><span class="sxs-lookup"><span data-stu-id="593fa-129">From the right pane, select **Map**.</span></span> <span data-ttu-id="593fa-130">指定對應名稱，例如**RequestMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="593fa-130">Specify a name for the map, such as **RequestMap.btm**.</span></span> <span data-ttu-id="593fa-131">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="593fa-131">Click **Add**.</span></span>  
  
   2. <span data-ttu-id="593fa-132">從來源結構描述 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="593fa-132">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
   3. <span data-ttu-id="593fa-133">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Oracle 資料庫配接器的要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="593fa-133">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the vPrev Oracle database adapter.</span></span> <span data-ttu-id="593fa-134">本教學課程中，選取*Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*。</span><span class="sxs-lookup"><span data-stu-id="593fa-134">For this tutorial, select *Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*.</span></span> <span data-ttu-id="593fa-135">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="593fa-135">Click **OK**.</span></span>  
  
   4. <span data-ttu-id="593fa-136">在 **來源結構描述的根節點**對話方塊中，選取*插入*，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="593fa-136">In the **Root Node for Source Schema** dialog box, select *Insert* and click **OK**.</span></span>  
  
   5. <span data-ttu-id="593fa-137">從目的結構描述 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="593fa-137">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
   6. <span data-ttu-id="593fa-138">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-138">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="593fa-139">本教學課程中，選取*Oracle_Migration.OracleDBBindingSchema*。</span><span class="sxs-lookup"><span data-stu-id="593fa-139">For this tutorial, select *Oracle_Migration.OracleDBBindingSchema*.</span></span> <span data-ttu-id="593fa-140">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="593fa-140">Click **OK**.</span></span>  
  
   7. <span data-ttu-id="593fa-141">在 **目標結構描述的根節點**對話方塊方塊中，選取*插入*，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="593fa-141">In the **Root Node for Target Schema** dialog box, select *Insert* and click **OK**.</span></span>  
  
   8. <span data-ttu-id="593fa-142">對應在這兩個結構描述中的個別項目，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="593fa-142">Map the respective elements in both the schemas as illustrated in the following figure.</span></span>  
  
       <span data-ttu-id="593fa-143">![對應到 Oracle 資料庫所傳送的要求](../../adapters-and-accelerators/adapter-oracle-database/media/4cb59338-40d1-4eb1-bd89-b5a3183959e1.gif "4cb59338-40d1-4eb1-bd89-b5a3183959e1")</span><span class="sxs-lookup"><span data-stu-id="593fa-143">![Map the request sent to the Oracle database](../../adapters-and-accelerators/adapter-oracle-database/media/4cb59338-40d1-4eb1-bd89-b5a3183959e1.gif "4cb59338-40d1-4eb1-bd89-b5a3183959e1")</span></span>  
  
   9. <span data-ttu-id="593fa-144">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="593fa-144">Save the map.</span></span>  
  
4. <span data-ttu-id="593fa-145">回應訊息，將使用 vPrev Oracle 資料庫配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-145">For the response message, map the schema generated using vPrev Oracle database adapter to the schema generated using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
   1. <span data-ttu-id="593fa-146">將 BizTalk 對應工具加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="593fa-146">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="593fa-147">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="593fa-147">Right-click the BizTalk project, point to **Add**, and click **New Item**.</span></span>  
  
       <span data-ttu-id="593fa-148">在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="593fa-148">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="593fa-149">從右窗格中，選取**地圖**。</span><span class="sxs-lookup"><span data-stu-id="593fa-149">From the right pane, select **Map**.</span></span> <span data-ttu-id="593fa-150">指定對應名稱，例如**ResponseMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="593fa-150">Specify a name for the map, such as **ResponseMap.btm**.</span></span> <span data-ttu-id="593fa-151">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="593fa-151">Click **Add**.</span></span>  
  
   2. <span data-ttu-id="593fa-152">從來源結構描述 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="593fa-152">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
   3. <span data-ttu-id="593fa-153">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-153">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="593fa-154">本教學課程中，選取*Oracle_Migration.OracleDBBindingSchema*。</span><span class="sxs-lookup"><span data-stu-id="593fa-154">For this tutorial, select *Oracle_Migration.OracleDBBindingSchema*.</span></span> <span data-ttu-id="593fa-155">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="593fa-155">Click **OK**.</span></span>  
  
   4. <span data-ttu-id="593fa-156">在 **來源結構描述的根節點**對話方塊方塊中，選取*InsertResponse* ，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="593fa-156">In the **Root Node for Source Schema** dialog box, select *InsertResponse* and click **OK**.</span></span>  
  
   5. <span data-ttu-id="593fa-157">從目的結構描述 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="593fa-157">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
   6. <span data-ttu-id="593fa-158">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Oracle 資料庫配接器的回應訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="593fa-158">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the vPrev Oracle database adapter.</span></span> <span data-ttu-id="593fa-159">本教學課程中，選取*Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*。</span><span class="sxs-lookup"><span data-stu-id="593fa-159">For this tutorial, select *Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*.</span></span> <span data-ttu-id="593fa-160">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="593fa-160">Click **OK**.</span></span>  
  
   7. <span data-ttu-id="593fa-161">在 **目標結構描述的根節點**對話方塊中，選取*InsertResponse*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="593fa-161">In the **Root Node for Target Schema** dialog box, select *InsertResponse*, and then click **OK**.</span></span>  
  
   8. <span data-ttu-id="593fa-162">您會發現，符合以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]包含額外*InsertResult*項目。</span><span class="sxs-lookup"><span data-stu-id="593fa-162">You will notice that the schema for the response message conforming to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] contains an additional *InsertResult* element.</span></span> <span data-ttu-id="593fa-163">您必須從結構描述與對應中移除這*InsertResponse*這兩個結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="593fa-163">You must remove this from the schema and map the *InsertResponse* element in both the schemas.</span></span>  
  
       <span data-ttu-id="593fa-164">若要這樣做，請從**工具箱**，拖曳**字串左空白位置修剪**運算質放在對應工具格線。</span><span class="sxs-lookup"><span data-stu-id="593fa-164">To do so, from the **Toolbox**, drag the **String Left Trim** functoid and drop it on the mapper grid.</span></span> <span data-ttu-id="593fa-165">連接**InsertResponse**運算質將來源結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="593fa-165">Connect the **InsertResponse** element in the source schema to the functoid.</span></span> <span data-ttu-id="593fa-166">同樣地，連接**InsertResponse**運算質至目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="593fa-166">Similarly, connect the **InsertResponse** element in the destination schema to the functoid.</span></span> <span data-ttu-id="593fa-167">下圖說明兩個項目透過運算質的對應方式。</span><span class="sxs-lookup"><span data-stu-id="593fa-167">The following figure illustrates how the two elements are mapped via the functoid.</span></span>  
  
       <span data-ttu-id="593fa-168">![對應從 Oracle 資料庫接收的回應](../../adapters-and-accelerators/adapter-oracle-database/media/7fe18f5b-100f-4fe2-ac92-c111629d7fe9.gif "7fe18f5b-100f-4fe2-ac92-c111629d7fe9")</span><span class="sxs-lookup"><span data-stu-id="593fa-168">![Map the response received from Oracle database](../../adapters-and-accelerators/adapter-oracle-database/media/7fe18f5b-100f-4fe2-ac92-c111629d7fe9.gif "7fe18f5b-100f-4fe2-ac92-c111629d7fe9")</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="593fa-169">如需詳細資訊，請參閱 <<c0>  **字串左空白位置修剪運算質** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="593fa-169">For more information, see the **String Left Trim Functoid** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].</span></span>
  
   9. <span data-ttu-id="593fa-170">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="593fa-170">Save the map.</span></span>  
  
5. <span data-ttu-id="593fa-171">儲存並建置 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="593fa-171">Save and build the BizTalk solution.</span></span> <span data-ttu-id="593fa-172">以滑鼠右鍵按一下方案，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="593fa-172">Right-click the solution, and then click **Build Solution**.</span></span>  
  
6. <span data-ttu-id="593fa-173">部署該方案。</span><span class="sxs-lookup"><span data-stu-id="593fa-173">Deploy the solution.</span></span> <span data-ttu-id="593fa-174">以滑鼠右鍵按一下方案，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="593fa-174">Right-click the solution, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="593fa-175">後續步驟</span><span class="sxs-lookup"><span data-stu-id="593fa-175">Next Steps</span></span>  
 <span data-ttu-id="593fa-176">建立 wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 使用 SQL 配接器的 Biztalk Server 管理主控台中設定協調流程](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="593fa-176">Create a WCF-custom send port and configure it to use the maps you created in this step, as described in [Step 2: Configure the Orchestration in Biztalk Server Administration Console using the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="593fa-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="593fa-177">See Also</span></span>  
 <span data-ttu-id="593fa-178">[教學課程： 移轉 BizTalk 專案](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)</span><span class="sxs-lookup"><span data-stu-id="593fa-178">[Tutorial: Migrating BizTalk Projects](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)</span></span>