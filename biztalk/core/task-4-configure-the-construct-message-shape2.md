---
title: 工作 4： 設定建構訊息 Shape2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43a7b912-0293-41be-b992-309eca550801
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67c9e667248150a705841d0947bfb0cb3799a516
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012695"
---
# <a name="task-4-configure-the-construct-message-shape"></a><span data-ttu-id="5baa9-102">工作 4： 設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="5baa9-102">Task 4: Configure the Construct Message Shape</span></span>
<span data-ttu-id="5baa9-103">「建構訊息」會保存訊息指派，包含 Begin、Edit 和 End Doc 程式碼的指示。</span><span class="sxs-lookup"><span data-stu-id="5baa9-103">The Construct Messages hold messages assignments with the instructions for the Begin, Edit, and End Doc code.</span></span>  
  
 <span data-ttu-id="5baa9-104">請使用下列程序設定「建構訊息」圖形。</span><span class="sxs-lookup"><span data-stu-id="5baa9-104">Use the following procedure to configure the Construct Message shape.</span></span>  
  
### <a name="to-configure-the-construct-message-shape"></a><span data-ttu-id="5baa9-105">若要設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="5baa9-105">To configure the Construct Message shape</span></span>  
  
1. <span data-ttu-id="5baa9-106">在 ReceiveBeginDoc 和 SendBeginDoc 之間拖放「建構訊息」圖形。</span><span class="sxs-lookup"><span data-stu-id="5baa9-106">Drag a Construct Message shape inbetween ReceiveBeginDoc and SendBeginDoc.</span></span>  
  
   -   <span data-ttu-id="5baa9-107">**建構的訊息：** BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="5baa9-107">**Messages Constructed:** BeginDocSessionMsg</span></span>  
  
   -   <span data-ttu-id="5baa9-108">**名稱：** ConstructBeginDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="5baa9-108">**Name:** ConstructBeginDocMessageWithSession</span></span>  
  
   1.  <span data-ttu-id="5baa9-109">將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5baa9-109">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
   2.  <span data-ttu-id="5baa9-110">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="5baa9-110">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
        <span data-ttu-id="5baa9-111">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="5baa9-111">The BizTalk Expression Editor appears.</span></span>  
  
   3.  <span data-ttu-id="5baa9-112">輸入您的程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="5baa9-112">Type in your code, for example:</span></span>  
  
   ```  
   BeginDocSessionMsg = BeginDocMsg;  
   BeginDocSessionMsg(JDE.ReserveSession) = true;  
   BeginDocSessionMsg(JDE.SessionID) = 0;  
   ```  
  
    <span data-ttu-id="5baa9-113">這會通知配接器您想要啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="5baa9-113">This tells the adapter you want to start a session.</span></span> <span data-ttu-id="5baa9-114">SessionID 初始化為 0，但回應傳回時，J.D.</span><span class="sxs-lookup"><span data-stu-id="5baa9-114">The SessionID is initialized as 0 but when the response comes back the ID will be assigned by the J.D.</span></span> <span data-ttu-id="5baa9-115">Edwards OneWorld 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5baa9-115">Edwards OneWorld Server.</span></span>  
  
    <span data-ttu-id="5baa9-116">![](../core/media/jde-message-expression-editor.gif "JDE_message_expression_editor")</span><span class="sxs-lookup"><span data-stu-id="5baa9-116">![](../core/media/jde-message-expression-editor.gif "JDE_message_expression_editor")</span></span>  
  
2. <span data-ttu-id="5baa9-117">在 SendEditLine 之前拖曳「建構訊息」。</span><span class="sxs-lookup"><span data-stu-id="5baa9-117">Drag a Construct Message before SendEditLine.</span></span>  
  
   - <span data-ttu-id="5baa9-118">**建構的訊息：** EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="5baa9-118">**Messages Constructed:** EditLineSessionMsg</span></span>  
  
   - <span data-ttu-id="5baa9-119">**名稱：** ConstructEditLineMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="5baa9-119">**Name:** ConstructEditLineMessageWithSession</span></span>  
  
     <span data-ttu-id="5baa9-120">![](../core/media/jde-constructoreditlinemessagewithsession.gif "JDE_constructoreditlinemessagewithsession")</span><span class="sxs-lookup"><span data-stu-id="5baa9-120">![](../core/media/jde-constructoreditlinemessagewithsession.gif "JDE_constructoreditlinemessagewithsession")</span></span>  
  
   1.  <span data-ttu-id="5baa9-121">將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5baa9-121">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
   2.  <span data-ttu-id="5baa9-122">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="5baa9-122">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
        <span data-ttu-id="5baa9-123">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="5baa9-123">The BizTalk Expression Editor appears.</span></span>  
  
   3.  <span data-ttu-id="5baa9-124">輸入您的程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="5baa9-124">Type in your code, for example:</span></span>  
  
   ```  
   EditLineSessionMsg = EditLineMsg;  
   EditLineSessionMsg(JDE.ReserveSession) = true;  
   EditLineSessionMsg(JDE.SessionID) =  
      BeginDocResponseMsg(JDE.SessionID);  
   ```  
  
    <span data-ttu-id="5baa9-125">![](../core/media/jde-editline-editor.gif "JDE_editline_editor")</span><span class="sxs-lookup"><span data-stu-id="5baa9-125">![](../core/media/jde-editline-editor.gif "JDE_editline_editor")</span></span>  
  
3. <span data-ttu-id="5baa9-126">在 SendEndDoc 之前拖曳「建構訊息」。</span><span class="sxs-lookup"><span data-stu-id="5baa9-126">Drag a Construct Message before SendEndDoc.</span></span>  
  
   -   <span data-ttu-id="5baa9-127">**建構的訊息：** EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="5baa9-127">**Messages Constructed:** EndDocSessionMsg</span></span>  
  
   -   <span data-ttu-id="5baa9-128">**名稱：** ConstructEndDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="5baa9-128">**Name:** ConstructEndDocMessageWithSession</span></span>  
  
   1.  <span data-ttu-id="5baa9-129">將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5baa9-129">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
   2.  <span data-ttu-id="5baa9-130">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="5baa9-130">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
        <span data-ttu-id="5baa9-131">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="5baa9-131">The BizTalk Expression Editor appears.</span></span>  
  
   3.  <span data-ttu-id="5baa9-132">輸入您的程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="5baa9-132">Type in your code, for example:</span></span>  
  
   ```  
   EndDocSessionMsg = EndDocMsg;  
   EndDocSessionMsg(JDE.ReserveSession) = false;  
   EndDocSessionMsg(JDE.SessionID) =  
      BeginDocResponseMsg(JDE.SessionID);  
   ```  
  
## <a name="see-also"></a><span data-ttu-id="5baa9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5baa9-133">See Also</span></span>  
 <span data-ttu-id="5baa9-134">[工作 1： 建立連接埠](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="5baa9-134">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="5baa9-135">[工作 2： 建立訊息](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="5baa9-135">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="5baa9-136">[工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="5baa9-136">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 [<span data-ttu-id="5baa9-137">工作 5：設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="5baa9-137">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)