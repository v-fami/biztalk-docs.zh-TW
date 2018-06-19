---
title: 步驟 2： 建立庫存要求結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa9ad9f-b815-4baf-8299-556869b8dde7
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06000a734856c7b9f22e78a2d5a78c4585021a21
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014285"
---
# <a name="step-2-create-the-inventory-request-schema"></a><span data-ttu-id="d2a65-102">步驟 2：建立庫存要求結構描述</span><span class="sxs-lookup"><span data-stu-id="d2a65-102">Step 2: Create the Inventory Request Schema</span></span>
<span data-ttu-id="d2a65-103">![步驟 2，5 個](../core/media/step-2of5.gif "Step_2of5")</span><span class="sxs-lookup"><span data-stu-id="d2a65-103">![Step 2 of 5](../core/media/step-2of5.gif "Step_2of5")</span></span>  
  
 <span data-ttu-id="d2a65-104">**若要完成的時間：** 7 分鐘</span><span class="sxs-lookup"><span data-stu-id="d2a65-104">**Time to complete:** 7 minutes</span></span>  
  
 <span data-ttu-id="d2a65-105">**目標：** 在此步驟中，您會定義庫存補充訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d2a65-105">**Objective:** In this step, you define the schema of the inventory replenishment message.</span></span>  <span data-ttu-id="d2a65-106">倉儲系統會傳送這個訊息，以便要求庫存補充。</span><span class="sxs-lookup"><span data-stu-id="d2a65-106">The warehouse system sends this message for requesting inventory replenishment.</span></span>  <span data-ttu-id="d2a65-107">這是您必須針對此專案建立的其中一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="d2a65-107">This is one of the two schemas you must create for this project.</span></span>  
  
 <span data-ttu-id="d2a65-108">**用途：** XML 不僅會結構和識別資訊與標準化的標記程式碼，不過也會使用結構描述的能力。</span><span class="sxs-lookup"><span data-stu-id="d2a65-108">**Purpose:** XML not only structures and identifies information with standardized markup codes, but also has the ability to use schemas.</span></span> <span data-ttu-id="d2a65-109">結構描述是一種 XML 文件，其運作方式就如同字典，而且會由其他 XML 文件當做參考使用。</span><span class="sxs-lookup"><span data-stu-id="d2a65-109">A schema is an XML document that works like a dictionary and is used as a reference by other XML documents.</span></span> <span data-ttu-id="d2a65-110">結構描述程式碼會定義 XML 項目的拼字以及這些項目所包含的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d2a65-110">The schema code defines the spelling of XML elements and the type of data enclosed by those elements.</span></span> <span data-ttu-id="d2a65-111">使用結構描述可讓程式輕易地處理 XML 文件並確保資訊的結構和類型正確無誤。</span><span class="sxs-lookup"><span data-stu-id="d2a65-111">Using schemas provides an easy way for a program to process XML documents and ensures that the structure and type of information is correct.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2a65-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="d2a65-112">Prerequisites</span></span>  
 <span data-ttu-id="d2a65-113">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="d2a65-113">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="d2a65-114">在開始此步驟之前必須先完成[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a65-114">Before you begin this step you must complete [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d2a65-115">程序</span><span class="sxs-lookup"><span data-stu-id="d2a65-115">Procedures</span></span>  
 <span data-ttu-id="d2a65-116">在[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)，您建立了新[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="d2a65-116">In [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md), you created a new [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project.</span></span>  <span data-ttu-id="d2a65-117">如果您關閉了 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 視窗，就可以使用下列程序來開啟專案。</span><span class="sxs-lookup"><span data-stu-id="d2a65-117">If you close the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window, you can use the following procedure to open the project.</span></span>  <span data-ttu-id="d2a65-118">否則，您可以略過這個程序：「若要開啟 Visual Studio 專案」。</span><span class="sxs-lookup"><span data-stu-id="d2a65-118">Otherwise, you can skip this procedure, “To open the Visual Studio project”.</span></span>  
  
#### <a name="to-open-the-visual-studio-project"></a><span data-ttu-id="d2a65-119">若要開啟 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="d2a65-119">To open the Visual Studio project</span></span>  
  
1.  <span data-ttu-id="d2a65-120">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-120">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="d2a65-121">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-121">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="d2a65-122">在**開啟專案**對話方塊中，瀏覽至**C:\BTSTutorials\EAISolution\EAISolution.sln**方案檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-122">In the **Open Project** dialog box, browse to the **C:\BTSTutorials\EAISolution\EAISolution.sln** solution file, and then click **Open**.</span></span>  
  
 <span data-ttu-id="d2a65-123">在下列程序中，您會將新的結構描述檔案新增至庫存補充訊息的專案。</span><span class="sxs-lookup"><span data-stu-id="d2a65-123">In the following procedure, you add a new schema file to the project for the inventory replenishment message.</span></span>  
  
#### <a name="to-add-a-new-schema-to-the-project"></a><span data-ttu-id="d2a65-124">新增新結構描述至專案</span><span class="sxs-lookup"><span data-stu-id="d2a65-124">To add a new schema to the project</span></span>  
  
1.  <span data-ttu-id="d2a65-125">在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-125">In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="d2a65-126">在**加入新項目-EAISchemas**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d2a65-126">In the **Add New Item - EAISchemas** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="d2a65-127">使用</span><span class="sxs-lookup"><span data-stu-id="d2a65-127">Use this</span></span>|<span data-ttu-id="d2a65-128">動作</span><span class="sxs-lookup"><span data-stu-id="d2a65-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d2a65-129">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="d2a65-129">**Installed Templates**</span></span>|<span data-ttu-id="d2a65-130">按一下**結構描述檔案**，然後按一下 **結構描述**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-130">Click **Schema Files**, then click **Schema**.</span></span>|  
    |<span data-ttu-id="d2a65-131">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d2a65-131">**Name**</span></span>|<span data-ttu-id="d2a65-132">型別**Request.xsd**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-132">Type **Request.xsd**.</span></span>|  
  
3.  <span data-ttu-id="d2a65-133">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-133">Click **Add**.</span></span> <span data-ttu-id="d2a65-134">會出現結構描述樹狀結構與 [XSD] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d2a65-134">The schema tree and XSD pane appear.</span></span> <span data-ttu-id="d2a65-135">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的這個區域稱為「BizTalk 編輯器」。</span><span class="sxs-lookup"><span data-stu-id="d2a65-135">This area of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is referred to as BizTalk Editor.</span></span> <span data-ttu-id="d2a65-136">此外，新結構描述在 [方案總管] 中會顯示於 EAISchemas 專案下方。</span><span class="sxs-lookup"><span data-stu-id="d2a65-136">In addition, your new schema appears in Solution Explorer below the EAISchemas project.</span></span>  
  
     <span data-ttu-id="d2a65-137">![BizTalk 專案的不同部分](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")</span><span class="sxs-lookup"><span data-stu-id="d2a65-137">![Different Parts of BizTalk Project](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")</span></span>  
  
#### <a name="to-add-elements-to-the-schema"></a><span data-ttu-id="d2a65-138">若要將項目新增至結構描述</span><span class="sxs-lookup"><span data-stu-id="d2a65-138">To add elements to the schema</span></span>  
  
1.  <span data-ttu-id="d2a65-139">在 結構描述樹狀目錄中，按一下 **根**節點。</span><span class="sxs-lookup"><span data-stu-id="d2a65-139">In schema tree, click the **Root** node.</span></span>  
  
2.  <span data-ttu-id="d2a65-140">在 [屬性] 窗格中，將值變更**節點名稱**屬性`Request`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d2a65-140">In the Properties pane, change the value of the **Node Name** property to `Request`, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="d2a65-141">在結構描述樹狀目錄中，以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下 **子記錄**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-141">In schema tree, right-click the **Request** node, point to **Insert Schema Node**, and then click **Child Record**.</span></span>  
  
4.  <span data-ttu-id="d2a65-142">型別`Header`做為子記錄，然後按 ENTER 鍵的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d2a65-142">Type `Header` as the new name for the child record, and then press ENTER.</span></span>  
  
5.  <span data-ttu-id="d2a65-143">重複步驟 3 和 4，以建立第二個子記錄**要求** 節點，並將其命名`Items`。</span><span class="sxs-lookup"><span data-stu-id="d2a65-143">Repeat step 3 and 4 to create a second child record for the **Request** node, and name it `Items`.</span></span>  
  
6.  <span data-ttu-id="d2a65-144">在結構描述樹狀目錄中，以滑鼠右鍵按一下**標頭**節點，指向**插入結構描述節點**，然後按一下 **子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-144">In schema tree, right-click the **Header** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span>  
  
7.  <span data-ttu-id="d2a65-145">型別`ReqID`做為項目，並再按 ENTER 鍵的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d2a65-145">Type `ReqID` as the new name for the element, and then press ENTER.</span></span>  
  
8.  <span data-ttu-id="d2a65-146">重複步驟 6 和 7，以建立第二個子欄位項目**標頭** 節點，並將其命名`OrderDate`。</span><span class="sxs-lookup"><span data-stu-id="d2a65-146">Repeat step 6 and 7 to create a second child field element for the **Header** node, and name it `OrderDate`.</span></span>

9.  <span data-ttu-id="d2a65-147">重複步驟 6 和 7，以建立第三個子欄位項目，如**標頭** 節點，並將其命名`GrandTotal`。</span><span class="sxs-lookup"><span data-stu-id="d2a65-147">Repeat step 6 and 7 to create a third child field element for the **Header** node, and name it `GrandTotal`.</span></span>
  
10. <span data-ttu-id="d2a65-148">在結構描述樹狀目錄中，以滑鼠右鍵按一下**項目**節點，指向**插入結構描述節點**，然後按一下 **子記錄**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-148">In schema tree, right-click the **Items** node, point to **Insert Schemas Node**, and then click **Child Record**.</span></span>  
  
11. <span data-ttu-id="d2a65-149">型別`Item`做為子記錄，然後按 ENTER 鍵的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d2a65-149">Type `Item` as the new name for the child record, and then press ENTER.</span></span>  
  
12. <span data-ttu-id="d2a65-150">在結構描述樹狀目錄中，以滑鼠右鍵按一下**項目** 節點，並新增下列子欄位項目：</span><span class="sxs-lookup"><span data-stu-id="d2a65-150">In schema tree, right-click the **Item** node, and add the following child field elements:</span></span>  
  
    -   `Description`  
  
    -   `Quantity`  
  
    -   `UnitPrice`  
  
     <span data-ttu-id="d2a65-151">已完成的 Request.xsd 看起來應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d2a65-151">The completed Request.xsd should look similar to the following figure.</span></span>  
  
     <span data-ttu-id="d2a65-152">![具有要求結構描述的方案總管](../core/media/solutionexplorerwiththerequestschema.gif "SolutionExplorerwiththeRequestSchema")</span><span class="sxs-lookup"><span data-stu-id="d2a65-152">![Solution Explorer with the Request Schema](../core/media/solutionexplorerwiththerequestschema.gif "SolutionExplorerwiththeRequestSchema")</span></span>  
  
 <span data-ttu-id="d2a65-153">當您將節點新增至結構描述時，BizTalk 編輯器就會針對其屬性提供一組預設值。</span><span class="sxs-lookup"><span data-stu-id="d2a65-153">When you add nodes to a schema, BizTalk Editor gives a set of default values for their properties.</span></span>  <span data-ttu-id="d2a65-154">您必須根據需求設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="d2a65-154">You must configure them based on the requirements.</span></span>  
  
#### <a name="to-configure-the-elements"></a><span data-ttu-id="d2a65-155">若要設定項目</span><span class="sxs-lookup"><span data-stu-id="d2a65-155">To configure the elements</span></span>  
  
1.  <span data-ttu-id="d2a65-156">在 結構描述樹狀目錄中，按一下  **OrderDate**來選取它。</span><span class="sxs-lookup"><span data-stu-id="d2a65-156">In schema tree, click **OrderDate** to select it.</span></span>  
  
2.  <span data-ttu-id="d2a65-157">在 [屬性] 窗格中，變更**資料型別**至**xs: datetime**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-157">In the Properties pane, change **Data Type** to **xs:dateTime**.</span></span>  
  
3.  <span data-ttu-id="d2a65-158">重複步驟 1 和 2 來設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2a65-158">Repeat step 1 and 2 to configure the following properties:</span></span>  
  
    |<span data-ttu-id="d2a65-159">元素</span><span class="sxs-lookup"><span data-stu-id="d2a65-159">Element</span></span>|<span data-ttu-id="d2a65-160">屬性</span><span class="sxs-lookup"><span data-stu-id="d2a65-160">Property</span></span>|<span data-ttu-id="d2a65-161">值</span><span class="sxs-lookup"><span data-stu-id="d2a65-161">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="d2a65-162">**GrandTotal**</span><span class="sxs-lookup"><span data-stu-id="d2a65-162">**GrandTotal**</span></span>|<span data-ttu-id="d2a65-163">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="d2a65-163">**Data Type**</span></span>|<span data-ttu-id="d2a65-164">**Xs: decimal**</span><span class="sxs-lookup"><span data-stu-id="d2a65-164">**Xs:decimal**</span></span>|  
    |<span data-ttu-id="d2a65-165">**項目**</span><span class="sxs-lookup"><span data-stu-id="d2a65-165">**Item**</span></span>|<span data-ttu-id="d2a65-166">**Max Occurs**</span><span class="sxs-lookup"><span data-stu-id="d2a65-166">**Max Occurs**</span></span>|<span data-ttu-id="d2a65-167">**未繫結**</span><span class="sxs-lookup"><span data-stu-id="d2a65-167">**Unbounded**</span></span>|  
    |<span data-ttu-id="d2a65-168">**項目**</span><span class="sxs-lookup"><span data-stu-id="d2a65-168">**Item**</span></span>|<span data-ttu-id="d2a65-169">**Min Occurs**</span><span class="sxs-lookup"><span data-stu-id="d2a65-169">**Min Occurs**</span></span>|<span data-ttu-id="d2a65-170">**1**</span><span class="sxs-lookup"><span data-stu-id="d2a65-170">**1**</span></span>|  
    |<span data-ttu-id="d2a65-171">**數量**</span><span class="sxs-lookup"><span data-stu-id="d2a65-171">**Quantity**</span></span>|<span data-ttu-id="d2a65-172">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="d2a65-172">**Data Type**</span></span>|<span data-ttu-id="d2a65-173">**xs:unsignedInt**</span><span class="sxs-lookup"><span data-stu-id="d2a65-173">**xs:unsignedInt**</span></span>|  
  
 <span data-ttu-id="d2a65-174">雖然一個結構描述可以具有許多項目，不過您的應用程式可能只需要您使用其中少數項目進行資料處理。</span><span class="sxs-lookup"><span data-stu-id="d2a65-174">A schema can have many elements, but your application may only require that you use a few of them for your data processing.</span></span> <span data-ttu-id="d2a65-175">為了節省電腦資源，BizTalk Server 不會自動讀取每個結構描述項目。</span><span class="sxs-lookup"><span data-stu-id="d2a65-175">To save computer resources, BizTalk Server doesn't automatically read each schema element.</span></span> <span data-ttu-id="d2a65-176">如果您想要讓 BizTalk Server 讀取特定項目的資料，就必須使用 BizTalk 編輯器來升級該項目的屬性，以便識別該項目。</span><span class="sxs-lookup"><span data-stu-id="d2a65-176">If you want BizTalk Server to read data from a specific element, you must identify that element by using BizTalk Editor to promote its properties.</span></span>  
  
 <span data-ttu-id="d2a65-177">我們將在建立協調流程[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)會根據 GrandTotal 欄位來路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="d2a65-177">The orchestration that we will create in [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md) will base on the GrandTotal field to route messages.</span></span>  <span data-ttu-id="d2a65-178">因此，我們必須升級 GrandTotal 欄位。</span><span class="sxs-lookup"><span data-stu-id="d2a65-178">So we must promote the GrandTotal field.</span></span>  
  
#### <a name="to-promote-an-element"></a><span data-ttu-id="d2a65-179">若要升級項目</span><span class="sxs-lookup"><span data-stu-id="d2a65-179">To promote an element</span></span>  
  
1.  <span data-ttu-id="d2a65-180">在結構描述樹狀目錄中，以滑鼠右鍵按一下**GrandTotal**，指向 **升階**，然後按一下 **快速升級**。</span><span class="sxs-lookup"><span data-stu-id="d2a65-180">In Schema tree, right-click **GrandTotal**, point to **Promote**, and then click **Quick Promotions**.</span></span>  
  
2.  <span data-ttu-id="d2a65-181">按一下**確定**確認新增屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="d2a65-181">Click **OK** to acknowledge adding a property schema.</span></span>  
  
3.  <span data-ttu-id="d2a65-182">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="d2a65-182">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="d2a65-183">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="d2a65-183">What did I just do?</span></span>  
 <span data-ttu-id="d2a65-184">在這個步驟中，您已定義倉儲庫存補充訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="d2a65-184">In this step, you defined the warehouse inventory replenishment message schema.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d2a65-185">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d2a65-185">Next Steps</span></span>  
 <span data-ttu-id="d2a65-186">您會定義要求拒絕訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="d2a65-186">You define the request decline message schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a65-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2a65-187">See Also</span></span>  
 <span data-ttu-id="d2a65-188">[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="d2a65-188">[Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md) </span></span>  
 <span data-ttu-id="d2a65-189">[步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="d2a65-189">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 <span data-ttu-id="d2a65-190">[步驟 4： 建立地圖](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="d2a65-190">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="d2a65-191">[步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="d2a65-191">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 <span data-ttu-id="d2a65-192">[使用 BizTalk 編輯器建立結構描述](../core/creating-schemas-using-biztalk-editor.md) </span><span class="sxs-lookup"><span data-stu-id="d2a65-192">[Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md) </span></span>  
 [<span data-ttu-id="d2a65-193">關於 BizTalk 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="d2a65-193">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)
