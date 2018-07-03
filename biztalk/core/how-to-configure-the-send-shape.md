---
title: 如何設定 「 傳送 」 圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Send shape [Orchestration Designer], delivery notification
- send ports, delivery notifications
- configuring [Orchestration Designer], Send shapes
- Send shape [Orchestration Designer], configuring
- delivery notification
- messages, delivery notification
ms.assetid: 2cf4755b-1cfc-484e-bd9c-c9f3855af556
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbfedd5067be1de443c20ce522cbe30f27395db1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989959"
---
# <a name="how-to-configure-the-send-shape"></a><span data-ttu-id="770e2-102">如何設定傳送圖形</span><span class="sxs-lookup"><span data-stu-id="770e2-102">How to Configure the Send Shape</span></span>
<span data-ttu-id="770e2-103">![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")</span><span class="sxs-lookup"><span data-stu-id="770e2-103">![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")</span></span>  
<span data-ttu-id="770e2-104">傳送圖形</span><span class="sxs-lookup"><span data-stu-id="770e2-104">Send shape</span></span>  
  
 <span data-ttu-id="770e2-105">若您預期收到您已送出訊息的間接或非同步回應 (不使用要求-回應連接埠)，則需要將訊息與目前正在執行的協調流程執行個體建立相互關聯，讓回應者能將回應送給正確的執行個體。</span><span class="sxs-lookup"><span data-stu-id="770e2-105">If you expect to receive an indirect or asynchronous response (not using a request-response port) to the message that you have sent, you need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance.</span></span> <span data-ttu-id="770e2-106">您可以套用下列的相互關聯集合來**傳送**圖形以先前初始化的相互關聯，或您可以套用初始相互關聯集。</span><span class="sxs-lookup"><span data-stu-id="770e2-106">You can apply a following correlation set to the **Send** shape for a previously initialized correlation, or you can apply an initializing correlation set.</span></span> <span data-ttu-id="770e2-107">如需詳細資訊，請參閱 <<c0> [ 協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="770e2-107">For more information, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).</span></span>  
  
### <a name="to-configure-a-send-shape"></a><span data-ttu-id="770e2-108">設定傳送圖形</span><span class="sxs-lookup"><span data-stu-id="770e2-108">To configure a Send shape</span></span>  
  
1.  <span data-ttu-id="770e2-109">設定訊息和連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="770e2-109">Set a message and a port operation.</span></span>  
  
    1.  <span data-ttu-id="770e2-110">在 [協調流程檢視] 視窗中，確認您的協調流程有為傳送的多部分訊息類型，定義訊息和連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="770e2-110">In the Orchestration View window, verify that your orchestration has both a message and a port operation defined for the multi-part message type being sent.</span></span>  
  
    2.  <span data-ttu-id="770e2-111">在 屬性 視窗中，選取 從傳送訊息**訊息**屬性下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="770e2-111">In the Properties window, select the message to send from the **Message** property drop-down list.</span></span>  
  
    3.  <span data-ttu-id="770e2-112">在 屬性 視窗中，選取 將訊息從傳送連接埠作業**連接埠作業**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="770e2-112">In the Properties window, select the port operation that sends the message from the **Port Operation** drop-down list.</span></span>  
  
         <span data-ttu-id="770e2-113">-或-</span><span class="sxs-lookup"><span data-stu-id="770e2-113">—Or—</span></span>  
  
         <span data-ttu-id="770e2-114">從傳送連接器拖曳到**傳送**圖形以將訊息傳送的連接埠通訊端。</span><span class="sxs-lookup"><span data-stu-id="770e2-114">Drag the send connector from the **Send** shape to the port socket that sends the message.</span></span>  
  
2.  <span data-ttu-id="770e2-115">指定相互關聯集來限制的訊息**傳送**」 圖形將傳送或初始化的相互關聯集合中的值。</span><span class="sxs-lookup"><span data-stu-id="770e2-115">Specify correlation sets to restrict the messages the **Send** shape will send or to initialize the values in a correlation set.</span></span>  
  
    1.  <span data-ttu-id="770e2-116">針對您想要使用的每個相互關聯集，檢查相互關聯集從下拉式清單上**沿用相互關聯集**屬性。</span><span class="sxs-lookup"><span data-stu-id="770e2-116">For each correlation set you want to use, check a correlation set from the drop-down on the **Following Correlation Sets** property.</span></span>  
  
    2.  <span data-ttu-id="770e2-117">用於每個相互關聯集您想要初始化，請檢查相互關聯集從下拉式清單上**初始相互關聯集**屬性。</span><span class="sxs-lookup"><span data-stu-id="770e2-117">For each correlation set that you want to initialize, check a correlation set from the drop-down on the **Initializing Correlation Sets** property.</span></span>  
  
## <a name="delivery-notification"></a><span data-ttu-id="770e2-118">傳遞通知</span><span class="sxs-lookup"><span data-stu-id="770e2-118">Delivery Notification</span></span>  
 <span data-ttu-id="770e2-119">若要測試是否已經透過傳送埠成功傳送訊息，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="770e2-119">To test whether you have successfully sent a message over a send port, complete the following steps:</span></span>  
  
1. <span data-ttu-id="770e2-120">將您的「傳送」圖形放在非交易式、長時間執行或不可部分完成的範圍中。</span><span class="sxs-lookup"><span data-stu-id="770e2-120">Put your Send shape in a non-transactional, long-running or atomic scope.</span></span>  
  
2. <span data-ttu-id="770e2-121">在您的傳送埠，將 DeliveryNotification 屬性設定為**傳輸**。</span><span class="sxs-lookup"><span data-stu-id="770e2-121">On your send port, set the DeliveryNotification property to **Transmitted**.</span></span>  
  
3. <span data-ttu-id="770e2-122">將 Catch 處理常式新增到您的範圍，以處理 DeliveryFailureException。</span><span class="sxs-lookup"><span data-stu-id="770e2-122">Add a catch handler to your scope to handle a DeliveryFailureException.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="770e2-123">如果 「 傳送 」 圖形包含不可部分完成的範圍內，DeliveryFailureException 依然可以攔截，但會需要使用交易類型設定為新增外部範圍圖形**長時間執行**或是**無**.</span><span class="sxs-lookup"><span data-stu-id="770e2-123">If the Send shape is contained within an atomic scope, the DeliveryFailureException can still be caught, but will require an outer scope shape be added with a Transaction Type set to **Long Running** or **None**.</span></span> <span data-ttu-id="770e2-124">不可部分完成的範圍不能直接攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="770e2-124">Atomic scopes are not able to catch exceptions directly.</span></span>  
  
   <span data-ttu-id="770e2-125">協調流程會在封閉式非不可部分完成之範圍的結尾，或是協調流程的結尾等待通知，以便接收通知。</span><span class="sxs-lookup"><span data-stu-id="770e2-125">The orchestration waits for acknowledgment at the end of the enclosing non-atomic scope, or the end of the orchestration, to receive the acknowledgment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="770e2-126">這點僅適用於單向作業；如果在雙向 (要求 – 回應) 作業中失敗，即使沒有設定連接埠屬性，也會造成 SoapException (負值通知)。</span><span class="sxs-lookup"><span data-stu-id="770e2-126">This applies only to one-way operations; failure in two-way (request-response) operations results in a SoapException (negative acknowledgement) even without the port attribute being set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="770e2-127">直接繫結不支援傳遞通知。</span><span class="sxs-lookup"><span data-stu-id="770e2-127">Delivery notification is not supported for direct binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770e2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="770e2-128">See Also</span></span>  
 [<span data-ttu-id="770e2-129">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="770e2-129">Error Handling</span></span>](../core/error-handling.md)