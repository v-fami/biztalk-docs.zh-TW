---
title: 步驟 3： 建立拒絕要求結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1ce166c-1be1-4ef4-9d00-3da7038d4ada
caps.latest.revision: 39
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ff343c58e836bc0738f0200016308eb7a4d90b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278550"
---
# <a name="step-3-create-the-request-decline-schema"></a><span data-ttu-id="2a2ae-102">步驟 3：建立拒絕要求結構描述</span><span class="sxs-lookup"><span data-stu-id="2a2ae-102">Step 3: Create the Request Decline Schema</span></span>
<span data-ttu-id="2a2ae-103">![步驟 5 的 3](../core/media/step-3of5.gif "Step_3of5")</span><span class="sxs-lookup"><span data-stu-id="2a2ae-103">![Step 3 of 5](../core/media/step-3of5.gif "Step_3of5")</span></span>  
  
 <span data-ttu-id="2a2ae-104">**若要完成的時間：** 7 分鐘</span><span class="sxs-lookup"><span data-stu-id="2a2ae-104">**Time to complete:** 7 minutes</span></span>  
  
 <span data-ttu-id="2a2ae-105">**目標：** 在此步驟中，您會建立訊息的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送傳回倉儲的商務程序拒絕庫存補充要求的情況。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-105">**Objective:** In this step, you create the schema for the message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends back to the warehouse if the business process rejects the inventory replenishment request.</span></span>  
  
 <span data-ttu-id="2a2ae-106">**用途：** 結構描述會定義資料的要求拒絕訊息結構。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-106">**Purpose:** The schema defines the data and the structure of the request decline message.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2a2ae-107">使用結構描述來識別及訊息中的資料互動。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-107"> uses the schema to identify and interact with the data in the message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2a2ae-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="2a2ae-108">Prerequisites</span></span>  
 <span data-ttu-id="2a2ae-109">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="2a2ae-109">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="2a2ae-110">在開始此步驟之前必須先完成[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-110">Before you begin this step you must complete [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2a2ae-111">程序</span><span class="sxs-lookup"><span data-stu-id="2a2ae-111">Procedures</span></span>  
  
#### <a name="to-create-the-request-decline-schema"></a><span data-ttu-id="2a2ae-112">建立拒絕要求結構描述</span><span class="sxs-lookup"><span data-stu-id="2a2ae-112">To create the Request Decline schema</span></span>  
  
1.  <span data-ttu-id="2a2ae-113">在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-113">In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="2a2ae-114">在**加入新項目-EAISchemas**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2a2ae-114">In the **Add New Item - EAISchemas** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2a2ae-115">使用</span><span class="sxs-lookup"><span data-stu-id="2a2ae-115">Use this</span></span>|<span data-ttu-id="2a2ae-116">動作</span><span class="sxs-lookup"><span data-stu-id="2a2ae-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2a2ae-117">**已安裝的範本**</span><span class="sxs-lookup"><span data-stu-id="2a2ae-117">**Installed Templates**</span></span>|<span data-ttu-id="2a2ae-118">按一下**結構描述檔案**，然後按一下 **結構描述**。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-118">Click **Schema Files**, and then click **Schema**.</span></span>|  
    |<span data-ttu-id="2a2ae-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="2a2ae-119">**Name**</span></span>|<span data-ttu-id="2a2ae-120">輸入 `RequestDecline.xsd`。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-120">Type `RequestDecline.xsd`.</span></span>|  
  
3.  <span data-ttu-id="2a2ae-121">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-121">Click **Add**.</span></span>  
  
4.  <span data-ttu-id="2a2ae-122">在 [BizTalk 編輯器] 中，從結構描述樹狀目錄中，按一下**根**節點以選取它。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-122">In BizTalk Editor, from schema tree, click the **Root** node to select it.</span></span>  
  
5.  <span data-ttu-id="2a2ae-123">在 [屬性] 窗格中，將值變更**節點名稱**屬性`DeclineReq`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-123">In the Properties pane, change the value of the **Node Name** property to `DeclineReq`, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="2a2ae-124">在結構描述樹狀目錄中，以滑鼠右鍵按一下**declinereq**節點，指向**插入結構描述節點**，然後按一下 **子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-124">In schema tree, right-click the **DeclineReq** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span>  
  
7.  <span data-ttu-id="2a2ae-125">型別`ReqID`做為項目，並再按 ENTER 鍵的新名稱。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-125">Type `ReqID` as the new name for the element, and then press ENTER.</span></span>  
  
8.  <span data-ttu-id="2a2ae-126">加入名為第二個子欄位項目`GrandTotal`。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-126">Add a second child field element named `GrandTotal`.</span></span>  
  
9. <span data-ttu-id="2a2ae-127">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-127">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="2a2ae-128">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="2a2ae-128">What did I just do?</span></span>  
 <span data-ttu-id="2a2ae-129">在此步驟中，您已經針對商務程序拒絕庫存要求的情況，為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳回倉儲的訊息建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-129">In this step, you created the schema for the message that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends back to the warehouse if the business process rejects the inventory request.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2a2ae-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2a2ae-130">Next Steps</span></span>  
 <span data-ttu-id="2a2ae-131">藉由重新格式化要求訊息的方式，建立協調流程所需的對應來建立要求拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="2a2ae-131">You create the map needed by the orchestration to create request decline message by reformatting request message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2ae-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a2ae-132">See Also</span></span>  
 [<span data-ttu-id="2a2ae-133">步驟 1： 建立 EAISchemas 專案</span><span class="sxs-lookup"><span data-stu-id="2a2ae-133">Step 1: Create EAISchemas Project</span></span>](../core/step-1-create-eaischemas-project.md)  
 <span data-ttu-id="2a2ae-134">[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="2a2ae-134">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="2a2ae-135">[步驟 4： 建立地圖](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="2a2ae-135">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="2a2ae-136">[步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="2a2ae-136">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 [<span data-ttu-id="2a2ae-137">使用 BizTalk 編輯器建立結構描述</span><span class="sxs-lookup"><span data-stu-id="2a2ae-137">Creating Schemas Using BizTalk Editor</span></span>](../core/creating-schemas-using-biztalk-editor.md)