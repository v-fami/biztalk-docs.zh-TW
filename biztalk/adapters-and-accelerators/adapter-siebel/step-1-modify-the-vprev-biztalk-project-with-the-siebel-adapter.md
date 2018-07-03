---
title: 步驟 1： 修改 vPrev BizTalk 專案與 Siebel 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bd95e2-bd51-420f-8156-6f17cc0e91d6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e03b915abcaef48cf8c31001f6c096e5040a247b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004183"
---
# <a name="step-1-modify-the-vprev-biztalk-project-with-the-siebel-adapter"></a><span data-ttu-id="320b0-102">步驟 1： 修改 vPrev BizTalk 專案與 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="320b0-102">Step 1: Modify the vPrev BizTalk Project with the Siebel adapter</span></span>
<span data-ttu-id="320b0-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="320b0-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="320b0-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="320b0-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="320b0-105">**目標：** 在此步驟中，您必須進行下列變更以現有的 vPrev BizTalk 專案：</span><span class="sxs-lookup"><span data-stu-id="320b0-105">**Objective:** In this step, you make the following changes to the existing vPrev BizTalk project:</span></span>  
  
- <span data-ttu-id="320b0-106">產生使用 WCF 為基礎的商務帳戶元件上的插入作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-106">Generate metadata for the Insert operation on the Account business component using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
- <span data-ttu-id="320b0-107">執行插入作業使用 vPrev Siebel 配接器要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-107">Map the request message for performing an Insert operation using the vPrev Siebel adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
- <span data-ttu-id="320b0-108">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]vPrev Siebel 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="320b0-108">Map the response message received using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to the response message for the vPrev Siebel adapter.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="320b0-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="320b0-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="320b0-110">您必須具有 vPrev BizTalk 專案到 Siebel 系統中執行插入作業帳戶商務元件上。</span><span class="sxs-lookup"><span data-stu-id="320b0-110">You must have a vPrev BizTalk project to perform an Insert operation on the Account business component in the Siebel system.</span></span>  
  
### <a name="to-modify-the-vprev-biztalk-project"></a><span data-ttu-id="320b0-111">若要修改 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="320b0-111">To modify the vPrev BizTalk project</span></span>  
  
1. <span data-ttu-id="320b0-112">產生使用 WCF 為基礎的商務帳戶元件上的插入作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-112">Generate metadata for the Insert operation on the Account business component using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="320b0-113">您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="320b0-113">You can use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata.</span></span>  
  
    <span data-ttu-id="320b0-114">如需有關如何產生中繼資料的指示，請參閱 <<c0> [ 取得 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="320b0-114">For instructions on how to generate metadata, see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).</span></span> <span data-ttu-id="320b0-115">結構描述產生之後，具有類似名稱的檔案*SiebelBindingSchema.xsd*會加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="320b0-115">After the schema is generated, a file with the name similar to *SiebelBindingSchema.xsd* is added to the BizTalk project.</span></span> <span data-ttu-id="320b0-116">此檔案包含傳送訊息至執行插入作業，使用以 WCF 為基礎的商務帳戶元件上的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-116">This file contains the schema for sending a message to perform the Insert operation on the Account business component using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
2. <span data-ttu-id="320b0-117">產生插入作業的中繼資料時，也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="320b0-117">Generating the metadata for the Insert operation also creates a port binding file.</span></span> <span data-ttu-id="320b0-118">在下一個步驟中，此繫結檔案將用於建立 Wcf-custom 傳送埠將訊息傳送至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="320b0-118">In the next step, this binding file will be used to create a WCF-Custom send port to send messages to the Siebel system.</span></span> <span data-ttu-id="320b0-119">作業的 SOAP 動作也會設定為您要為其產生中繼資料作業中。</span><span class="sxs-lookup"><span data-stu-id="320b0-119">The SOAP action for the operation is also set to the operation for which you generated metadata.</span></span> <span data-ttu-id="320b0-120">比方說，如果您產生插入作業的中繼資料，傳送埠上的 SOAP 動作中的作業名稱會是 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="320b0-120">For example, if you generate metadata for the Insert operation, the operation name in the SOAP action on the send port will be “Insert”.</span></span> <span data-ttu-id="320b0-121">不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。</span><span class="sxs-lookup"><span data-stu-id="320b0-121">However, the operation name on the logical send port that you create as part of the orchestration could be different, for example, “Operation_1”.</span></span> <span data-ttu-id="320b0-122">如此一來，當您將訊息傳送至 Siebel 系統使用的傳送埠時，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="320b0-122">As a result, when you send messages to the Siebel system using the send port, you get an error.</span></span> <span data-ttu-id="320b0-123">若要避免這個問題，請確定邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="320b0-123">To prevent this, make sure the operation name on the logical send port in your orchestration is the same as the operation name for which you generated metadata.</span></span>  
  
    <span data-ttu-id="320b0-124">因此，本教學課程中，如果您產生插入作業的中繼資料，因為變更名稱"Insert"的邏輯傳送連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="320b0-124">So, in case of this tutorial, because you generate metadata for the Insert operation, change the name of the logical send port operation to “Insert”.</span></span>  
  
3. <span data-ttu-id="320b0-125">要求訊息中，將使用 vPrev Siebel 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-125">For the request message, map the schema generated using vPrev Siebel adapter to the schema generated using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
   1. <span data-ttu-id="320b0-126">將 BizTalk 對應工具加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="320b0-126">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="320b0-127">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="320b0-127">Right-click the BizTalk project, point to **Add**, and click **New Item**.</span></span>  
  
       <span data-ttu-id="320b0-128">在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="320b0-128">In the **Add New Item** dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="320b0-129">從右窗格中，選取**地圖**。</span><span class="sxs-lookup"><span data-stu-id="320b0-129">From the right pane, select **Map**.</span></span> <span data-ttu-id="320b0-130">指定對應名稱，例如**RequestMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="320b0-130">Specify a name for the map, such as **RequestMap.btm**.</span></span> <span data-ttu-id="320b0-131">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="320b0-131">Click **Add**.</span></span>  
  
   2. <span data-ttu-id="320b0-132">從來源結構描述 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="320b0-132">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
   3. <span data-ttu-id="320b0-133">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Siebel 配接器的要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="320b0-133">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the vPrev Siebel adapter.</span></span> <span data-ttu-id="320b0-134">本教學課程中，選取*Siebel_BussComp_Migration.AccountService_Account_x5d*。</span><span class="sxs-lookup"><span data-stu-id="320b0-134">For this tutorial, select *Siebel_BussComp_Migration.AccountService_Account_x5d*.</span></span> <span data-ttu-id="320b0-135">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="320b0-135">Click **OK**.</span></span>  
  
   4. <span data-ttu-id="320b0-136">在 **來源結構描述的根節點**對話方塊中，選取*插入*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="320b0-136">In the **Root Node for Source Schema** dialog box, select *Insert*, and then click **OK**.</span></span>  
  
   5. <span data-ttu-id="320b0-137">從目的結構描述 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="320b0-137">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
   6. <span data-ttu-id="320b0-138">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-138">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="320b0-139">本教學課程中，選取*Siebel_BussComp_Migration.SiebelDBBindingSchema*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="320b0-139">For this tutorial, select *Siebel_BussComp_Migration.SiebelDBBindingSchema*, and then click **OK**.</span></span>  
  
   7. <span data-ttu-id="320b0-140">在 **目標結構描述的根節點**對話方塊中，選取*插入*，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="320b0-140">In the **Root Node for Target Schema** dialog box, select *Insert*, and then click **OK**.</span></span>  
  
   8. <span data-ttu-id="320b0-141">對應的結構描述中的下列元素： **Currency_Code**， **Current_Volume**， **Customer_Account_Group**，**位置**，**Main_Phone_Number**，**名稱**， **Party_Name**， **Primary_Address_Id**，</span><span class="sxs-lookup"><span data-stu-id="320b0-141">Map the following elements in both the schemas: **Currency_Code**, **Current_Volume**, **Customer_Account_Group**, **Location**, **Main_Phone_Number**, **Name**, **Party_Name**, **Primary_Address_Id**,</span></span>  
  
   9. <span data-ttu-id="320b0-142">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="320b0-142">Save the map.</span></span>  
  
4. <span data-ttu-id="320b0-143">回應訊息，將使用 vPrev Siebel 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-143">For the response message, map the schema generated using the vPrev Siebel adapter to the schema generated using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
   1. <span data-ttu-id="320b0-144">將 BizTalk 對應工具加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="320b0-144">Add a BizTalk mapper to the BizTalk project.</span></span> <span data-ttu-id="320b0-145">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="320b0-145">Right-click the BizTalk project, point to **Add**, and click **New Item**.</span></span>  
  
       <span data-ttu-id="320b0-146">在 [加入新項目] 對話方塊中，從左窗格中，選取**對應檔**。</span><span class="sxs-lookup"><span data-stu-id="320b0-146">In the Add New Item dialog box, from the left pane, select **Map Files**.</span></span> <span data-ttu-id="320b0-147">從右窗格中，選取**地圖**。</span><span class="sxs-lookup"><span data-stu-id="320b0-147">From the right pane, select **Map**.</span></span> <span data-ttu-id="320b0-148">指定對應名稱，例如**ResponseMap.btm**。</span><span class="sxs-lookup"><span data-stu-id="320b0-148">Specify a name for the map, such as **ResponseMap.btm**.</span></span> <span data-ttu-id="320b0-149">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="320b0-149">Click **Add**.</span></span>  
  
   2. <span data-ttu-id="320b0-150">從來源結構描述 窗格中，按一下**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="320b0-150">From the Source Schema pane, click **Open Source Schema**.</span></span>  
  
   3. <span data-ttu-id="320b0-151">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320b0-151">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="320b0-152">本教學課程中，選取*Siebel_BussComp_Migration.SiebelDBBindingSchema*。</span><span class="sxs-lookup"><span data-stu-id="320b0-152">For this tutorial, select *Siebel_BussComp_Migration.SiebelDBBindingSchema*.</span></span> <span data-ttu-id="320b0-153">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="320b0-153">Click **OK**.</span></span>  
  
   4. <span data-ttu-id="320b0-154">在 **來源結構描述的根節點**對話方塊方塊中，選取*InsertResponse* ，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="320b0-154">In the **Root Node for Source Schema** dialog box, select *InsertResponse* and click **OK**.</span></span>  
  
   5. <span data-ttu-id="320b0-155">從目的結構描述 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="320b0-155">From the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
   6. <span data-ttu-id="320b0-156">在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Siebel 配接器的回應訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="320b0-156">In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the vPrev Siebel adapter.</span></span> <span data-ttu-id="320b0-157">本教學課程中，選取*Siebel_BussComp_Migration.AccountService_Account_x5d*。</span><span class="sxs-lookup"><span data-stu-id="320b0-157">For this tutorial, select *Siebel_BussComp_Migration.AccountService_Account_x5d*.</span></span> <span data-ttu-id="320b0-158">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="320b0-158">Click **OK**.</span></span>  
  
   7. <span data-ttu-id="320b0-159">在 **目標結構描述的根節點**對話方塊方塊中，選取*InsertResponse* ，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="320b0-159">In the **Root Node for Target Schema** dialog box, select *InsertResponse* and click **OK**.</span></span>  
  
   8. <span data-ttu-id="320b0-160">地圖**陣列： 字串**來源結構描述中的項目**公開： 字串**與目的結構描述，如下圖所示的項目。</span><span class="sxs-lookup"><span data-stu-id="320b0-160">Map the **array:string** element in the source schema to the **exposed:string** element in the destination schema, as illustrated in the following figure.</span></span>  
  
       <span data-ttu-id="320b0-161">![對應的回應訊息，配接器版本之間](../../adapters-and-accelerators/adapter-siebel/media/6352035b-79c0-4850-a8f7-e4f6581c8532.gif "6352035b-79c0-4850-a8f7-e4f6581c8532")</span><span class="sxs-lookup"><span data-stu-id="320b0-161">![Map the response messages between adapter versions](../../adapters-and-accelerators/adapter-siebel/media/6352035b-79c0-4850-a8f7-e4f6581c8532.gif "6352035b-79c0-4850-a8f7-e4f6581c8532")</span></span>  
  
   9. <span data-ttu-id="320b0-162">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="320b0-162">Save the map.</span></span>  
  
5. <span data-ttu-id="320b0-163">儲存並建置 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="320b0-163">Save and build the BizTalk solution.</span></span> <span data-ttu-id="320b0-164">以滑鼠右鍵按一下方案，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="320b0-164">Right-click the solution, and then click **Build Solution**.</span></span>  
  
6. <span data-ttu-id="320b0-165">部署該方案。</span><span class="sxs-lookup"><span data-stu-id="320b0-165">Deploy the solution.</span></span> <span data-ttu-id="320b0-166">以滑鼠右鍵按一下方案，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="320b0-166">Right-click the solution, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="320b0-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="320b0-167">Next Steps</span></span>  
 <span data-ttu-id="320b0-168">建立 wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 設定協調流程中使用 Oracle 資料庫配接器的 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="320b0-168">Create a WCF-custom send port and configure it to use the maps you created in this step, as described in [Step 2: Configure the Orchestration in BizTalk Server Administration Console to use the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320b0-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="320b0-169">See Also</span></span>  
 [<span data-ttu-id="320b0-170">教學課程 2： 移轉 BizTalk 專案中 Siebel</span><span class="sxs-lookup"><span data-stu-id="320b0-170">Tutorial 2: Migrating BizTalk Projects in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)