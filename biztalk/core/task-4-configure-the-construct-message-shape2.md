---
title: "工作 4： 設定建構訊息 Shape2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43a7b912-0293-41be-b992-309eca550801
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6616fec48eb0915527a95f94992e4bda838e9d37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="task-4-configure-the-construct-message-shape"></a><span data-ttu-id="c9024-102">工作 4： 設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="c9024-102">Task 4: Configure the Construct Message Shape</span></span>
<span data-ttu-id="c9024-103">「建構訊息」會保存訊息指派，包含 Begin、Edit 和 End Doc 程式碼的指示。</span><span class="sxs-lookup"><span data-stu-id="c9024-103">The Construct Messages hold messages assignments with the instructions for the Begin, Edit, and End Doc code.</span></span>  
  
 <span data-ttu-id="c9024-104">請使用下列程序設定「建構訊息」圖形。</span><span class="sxs-lookup"><span data-stu-id="c9024-104">Use the following procedure to configure the Construct Message shape.</span></span>  
  
### <a name="to-configure-the-construct-message-shape"></a><span data-ttu-id="c9024-105">若要設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="c9024-105">To configure the Construct Message shape</span></span>  
  
1.  <span data-ttu-id="c9024-106">在 ReceiveBeginDoc 和 SendBeginDoc 之間拖放「建構訊息」圖形。</span><span class="sxs-lookup"><span data-stu-id="c9024-106">Drag a Construct Message shape inbetween ReceiveBeginDoc and SendBeginDoc.</span></span>  
  
    -   <span data-ttu-id="c9024-107">**建構的訊息：** BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="c9024-107">**Messages Constructed:** BeginDocSessionMsg</span></span>  
  
    -   <span data-ttu-id="c9024-108">**名稱：** ConstructBeginDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="c9024-108">**Name:** ConstructBeginDocMessageWithSession</span></span>  
  
    1.  <span data-ttu-id="c9024-109">將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="c9024-109">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="c9024-110">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="c9024-110">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="c9024-111">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="c9024-111">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="c9024-112">輸入您的程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="c9024-112">Type in your code, for example:</span></span>  
  
    ```  
    BeginDocSessionMsg = BeginDocMsg;  
    BeginDocSessionMsg(JDE.ReserveSession) = true;  
    BeginDocSessionMsg(JDE.SessionID) = 0;  
    ```  
  
     <span data-ttu-id="c9024-113">這會通知配接器您想要啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="c9024-113">This tells the adapter you want to start a session.</span></span> <span data-ttu-id="c9024-114">SessionID 初始化為 0，但回應傳回時，J.D.</span><span class="sxs-lookup"><span data-stu-id="c9024-114">The SessionID is initialized as 0 but when the response comes back the ID will be assigned by the J.D.</span></span> <span data-ttu-id="c9024-115">Edwards OneWorld 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9024-115">Edwards OneWorld Server.</span></span>  
  
     ![](../core/media/jde-message-expression-editor.gif "JDE_message_expression_editor")  
  
2.  <span data-ttu-id="c9024-116">在 SendEditLine 之前拖曳「建構訊息」。</span><span class="sxs-lookup"><span data-stu-id="c9024-116">Drag a Construct Message before SendEditLine.</span></span>  
  
    -   <span data-ttu-id="c9024-117">**建構的訊息：** EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="c9024-117">**Messages Constructed:** EditLineSessionMsg</span></span>  
  
    -   <span data-ttu-id="c9024-118">**名稱：** ConstructEditLineMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="c9024-118">**Name:** ConstructEditLineMessageWithSession</span></span>  
  
     ![](../core/media/jde-constructoreditlinemessagewithsession.gif "JDE_constructoreditlinemessagewithsession")  
  
    1.  <span data-ttu-id="c9024-119">將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="c9024-119">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="c9024-120">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="c9024-120">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="c9024-121">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="c9024-121">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="c9024-122">輸入您的程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="c9024-122">Type in your code, for example:</span></span>  
  
    ```  
    EditLineSessionMsg = EditLineMsg;  
    EditLineSessionMsg(JDE.ReserveSession) = true;  
    EditLineSessionMsg(JDE.SessionID) =  
       BeginDocResponseMsg(JDE.SessionID);  
    ```  
  
     ![](../core/media/jde-editline-editor.gif "JDE_editline_editor")  
  
3.  <span data-ttu-id="c9024-123">在 SendEndDoc 之前拖曳「建構訊息」。</span><span class="sxs-lookup"><span data-stu-id="c9024-123">Drag a Construct Message before SendEndDoc.</span></span>  
  
    -   <span data-ttu-id="c9024-124">**建構的訊息：** EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="c9024-124">**Messages Constructed:** EndDocSessionMsg</span></span>  
  
    -   <span data-ttu-id="c9024-125">**名稱：** ConstructEndDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="c9024-125">**Name:** ConstructEndDocMessageWithSession</span></span>  
  
    1.  <span data-ttu-id="c9024-126">將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="c9024-126">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="c9024-127">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="c9024-127">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="c9024-128">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="c9024-128">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="c9024-129">輸入您的程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="c9024-129">Type in your code, for example:</span></span>  
  
    ```  
    EndDocSessionMsg = EndDocMsg;  
    EndDocSessionMsg(JDE.ReserveSession) = false;  
    EndDocSessionMsg(JDE.SessionID) =  
       BeginDocResponseMsg(JDE.SessionID);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c9024-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9024-130">See Also</span></span>  
 <span data-ttu-id="c9024-131">[工作 1： 建立連接埠](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="c9024-131">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="c9024-132">[工作 2： 建立訊息](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="c9024-132">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="c9024-133">[工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="c9024-133">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 [<span data-ttu-id="c9024-134">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="c9024-134">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)