---
title: 步驟 2： 建立訊息的 BizTalk 協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47a4fb98-6085-4aeb-ab39-2f2c3858d4e0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bad2f052efa561020ba04060a8290137a08f542
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995359"
---
# <a name="step-2-create-messages-for-biztalk-orchestrations"></a><span data-ttu-id="1bd9b-102">步驟 2： 建立訊息的 BizTalk 協調流程</span><span class="sxs-lookup"><span data-stu-id="1bd9b-102">Step 2: Create Messages for BizTalk Orchestrations</span></span>
<span data-ttu-id="1bd9b-103">![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="1bd9b-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="1bd9b-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="1bd9b-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="1bd9b-105">**目標：** 在此步驟中，方法，您可以將協調流程新增至 BizTalk 專案，並建立您在中產生的結構描述的訊息[步驟 1： 作業產生結構描述](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-105">**Objective:** In this step, you add an orchestration to the BizTalk project and create messages for the schemas you generated in [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1bd9b-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="1bd9b-106">Prerequisites</span></span>  
 <span data-ttu-id="1bd9b-107">您必須先完成[步驟 1： 作業產生結構描述](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-107">You must have completed [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).</span></span>  
  
### <a name="to-create-messages-in-an-orchestration"></a><span data-ttu-id="1bd9b-108">若要建立協調流程中的訊息</span><span class="sxs-lookup"><span data-stu-id="1bd9b-108">To create messages in an orchestration</span></span>  
  
1. <span data-ttu-id="1bd9b-109">將 BizTalk 協調流程新增至 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1bd9b-109">Add a BizTalk orchestration to the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:</span></span>  
  
   1.  <span data-ttu-id="1bd9b-110">從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-110">From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span>  
  
   2.  <span data-ttu-id="1bd9b-111">在 [**加入新項目**] 對話方塊中，從**分類**方塊中，按一下**協調流程檔案**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-111">In the **Add New Item** dialog box, from the **Categories** box, click **Orchestration Files**.</span></span> <span data-ttu-id="1bd9b-112">從**範本**方塊中，按一下**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-112">From the **Templates** box, click **BizTalk Orchestration**.</span></span>  
  
   3.  <span data-ttu-id="1bd9b-113">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-113">Type a name for the BizTalk orchestration, and then click **Add**.</span></span> <span data-ttu-id="1bd9b-114">本教學課程中，輸入 名稱`EmployeeOrch.odx`。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-114">For this tutorial, enter the name `EmployeeOrch.odx`.</span></span>  
  
2. <span data-ttu-id="1bd9b-115">開啟**協調流程檢視**的 BizTalk 專案中，如果它尚未開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-115">Open the **Orchestration View** window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="1bd9b-116">若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-116">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3. <span data-ttu-id="1bd9b-117">將訊息加入至協調流程。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-117">Add messages to the orchestration.</span></span>  
  
   1.  <span data-ttu-id="1bd9b-118">在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-118">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
   2.  <span data-ttu-id="1bd9b-119">以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-119">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
   3.  <span data-ttu-id="1bd9b-120">在 [**屬性**] 窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1bd9b-120">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
       |<span data-ttu-id="1bd9b-121">使用</span><span class="sxs-lookup"><span data-stu-id="1bd9b-121">Use this</span></span>|<span data-ttu-id="1bd9b-122">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="1bd9b-122">To do this</span></span>|  
       |--------------|----------------|  
       |<span data-ttu-id="1bd9b-123">識別碼</span><span class="sxs-lookup"><span data-stu-id="1bd9b-123">Identifier</span></span>|<span data-ttu-id="1bd9b-124">輸入 `NotifyReceive`。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-124">Type `NotifyReceive`.</span></span>|  
       |<span data-ttu-id="1bd9b-125">訊息類型</span><span class="sxs-lookup"><span data-stu-id="1bd9b-125">Message Type</span></span>|<span data-ttu-id="1bd9b-126">從下拉式清單中，依序展開**結構描述**，然後選取**Employee_PurchaseOrder.Notification**Employee_PurchaseOrder 所在的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-126">From the drop-down list, expand **Schemas**, and select **Employee_PurchaseOrder.Notification**, where Employee_PurchaseOrder is the name of your BizTalk project.</span></span> <span data-ttu-id="1bd9b-127">通知是針對產生的結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-127">Notification is the schema generated for the **Notification** operation.</span></span>|  
  
   4.  <span data-ttu-id="1bd9b-128">重複上述步驟來新增四個新的訊息，要求-回應訊息設定叫用 UPDATE_EMPLOYEE 預存程序，並執行為另一個要求-回應訊息**插入**上的作業**為 Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-128">Repeat the previous step to add four new messages—a request-response message set for invoking the UPDATE_EMPLOYEE stored procedure and another request-response message set for performing the **Insert** operation on **Purchase_Order** table.</span></span>  
  
       |<span data-ttu-id="1bd9b-129">若要設定識別項</span><span class="sxs-lookup"><span data-stu-id="1bd9b-129">Set Identifier to</span></span>|<span data-ttu-id="1bd9b-130">若要設定訊息類型</span><span class="sxs-lookup"><span data-stu-id="1bd9b-130">Set Message Type to</span></span>|  
       |-----------------------|-------------------------|  
       |<span data-ttu-id="1bd9b-131">UpdateEmployee</span><span class="sxs-lookup"><span data-stu-id="1bd9b-131">UpdateEmployee</span></span>|<span data-ttu-id="1bd9b-132">*Employee_PurchaseOrder.TypedProcedure_dbo。UPDATE_EMPLOYEE*，其中 TypedProcedure_dbo。UPDATE_EMPLOYEE 是結構描述為 UPDATE_EMPLOYEE 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-132">*Employee_PurchaseOrder.TypedProcedure_dbo.UPDATE_EMPLOYEE*, where TypedProcedure_dbo.UPDATE_EMPLOYEE is the schema for the UPDATE_EMPLOYEE stored procedure.</span></span>|  
       |<span data-ttu-id="1bd9b-133">UpdateEmployeeResponse</span><span class="sxs-lookup"><span data-stu-id="1bd9b-133">UpdateEmployeeResponse</span></span>|<span data-ttu-id="1bd9b-134">*Employee_PurchaseOrder.TypedProcedure_dbo。UPDATE_EMPLOYEEResponse*</span><span class="sxs-lookup"><span data-stu-id="1bd9b-134">*Employee_PurchaseOrder.TypedProcedure_dbo.UPDATE_EMPLOYEEResponse*</span></span>|  
       |<span data-ttu-id="1bd9b-135">InsertPO</span><span class="sxs-lookup"><span data-stu-id="1bd9b-135">InsertPO</span></span>|<span data-ttu-id="1bd9b-136">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*TableOperation_dbo_Purchase_Order.Insert 所在的結構描述為 Purchase_Order 資料表上的插入作業。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-136">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*, where TableOperation_dbo_Purchase_Order.Insert is the schema for the Insert operation on the Purchase_Order table.</span></span>|  
       |<span data-ttu-id="1bd9b-137">InsertPOResponse</span><span class="sxs-lookup"><span data-stu-id="1bd9b-137">InsertPOResponse</span></span>|<span data-ttu-id="1bd9b-138">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*</span><span class="sxs-lookup"><span data-stu-id="1bd9b-138">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*</span></span>|  
  
   5.  <span data-ttu-id="1bd9b-139">儲存協調流程檔案和 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-139">Save the orchestration file and the BizTalk project.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="1bd9b-140">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="1bd9b-140">What did I just do?</span></span>  
 <span data-ttu-id="1bd9b-141">在此步驟中，您會建立訊息來叫用執行的輸入和輸出作業上使用 SQL Server [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-141">In this step, you created messages for invoking performing inbound and outbound operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1bd9b-142">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1bd9b-142">Next Steps</span></span>  
 <span data-ttu-id="1bd9b-143">中所述，新增至插入作業的 SQL Server 和篩選器通知中收到通知的協調流程圖形[第 2 課： 接收和篩選器通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd9b-143">You add orchestration shapes to receive notification from SQL Server and filter notifications for Insert operation, as described in [Lesson 2: Receive and Filter Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd9b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bd9b-144">See Also</span></span>  
 <span data-ttu-id="1bd9b-145">[第 1 課： 產生結構描述，並建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1bd9b-145">[Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md) </span></span>  
 [<span data-ttu-id="1bd9b-146">步驟 1：產生作業的結構描述</span><span class="sxs-lookup"><span data-stu-id="1bd9b-146">Step 1: Generate Schema for Operations</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)