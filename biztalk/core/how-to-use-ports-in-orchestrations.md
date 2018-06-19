---
title: 如何在協調流程中使用連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, adding ports
- Port Configuration Wizard [Orchestration Designer], configuring ports
- ports, operations
- operations, adding to ports
- configuring, ports
- ports, deleting
- deleting, ports
- ports, Port Configuration Wizard [Orchestration Designer]
- ports, adding to orchestrations
- ports, configuring
ms.assetid: da8665cd-ccde-4949-b5f5-01f9f8be5ce8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3edef29376d8724d93192040ee88951ced245ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257910"
---
# <a name="how-to-use-ports-in-orchestrations"></a><span data-ttu-id="1e705-102">如何在協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-102">How to Use Ports in Orchestrations</span></span>
<span data-ttu-id="1e705-103">新增連接埠到協調流程的方式，和新增控制項到 Web Form 或 Windows Form 的方式類似。</span><span class="sxs-lookup"><span data-stu-id="1e705-103">You add ports to an orchestration in much the same way that you add controls to a Web Form or Windows Form.</span></span> <span data-ttu-id="1e705-104">您也可以使用 [協調流程檢視] 視窗來新增連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e705-104">You can also add ports by using the Orchestration View window.</span></span>  
  
### <a name="to-add-a-new-port"></a><span data-ttu-id="1e705-105">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-105">To add a new port</span></span>  
  
-   <span data-ttu-id="1e705-106">以滑鼠右鍵按一下**連接埠介面**或**角色連結**，然後按一下 **新連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e705-106">Right-click a **Port Surface** or a **Role Link**, and then click **New Port**.</span></span>  
  
     <span data-ttu-id="1e705-107">-或者-</span><span class="sxs-lookup"><span data-stu-id="1e705-107">—Or—</span></span>  
  
     <span data-ttu-id="1e705-108">在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠**，然後按一下 [**新連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e705-108">In the Orchestration View window, right-click **Ports** and then click **New Port**.</span></span>  
  
     <span data-ttu-id="1e705-109">DesignTip 會出現在尚未完全設定的連接埠上。</span><span class="sxs-lookup"><span data-stu-id="1e705-109">A DesignTip appears on ports that are not yet fully configured.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1e705-110">您也可以拖曳到連接埠**角色連結**。</span><span class="sxs-lookup"><span data-stu-id="1e705-110">You can also drag ports into a **Role Link**.</span></span>  
  
### <a name="to-add-and-configure-a-new-port"></a><span data-ttu-id="1e705-111">新增及設定新連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-111">To add and configure a new port</span></span>  
  
1.  <span data-ttu-id="1e705-112">從**BizTalk 協調流程** 索引標籤的 工具箱 拖曳**連接埠**圖形拖曳到**連接埠介面**或**角色連結**。</span><span class="sxs-lookup"><span data-stu-id="1e705-112">From the **BizTalk Orchestrations** tab of the Toolbox, drag the **Port** shape onto a **Port Surface** or a **Role Link**.</span></span>  
  
     <span data-ttu-id="1e705-113">-或者-</span><span class="sxs-lookup"><span data-stu-id="1e705-113">—Or—</span></span>  
  
     <span data-ttu-id="1e705-114">以滑鼠右鍵按一下**連接埠介面**或**角色連結**，然後按一下 **新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e705-114">Right-click a **Port Surface** or a **Role Link**, and then click **New Configured Port**.</span></span>  
  
     <span data-ttu-id="1e705-115">-或者-</span><span class="sxs-lookup"><span data-stu-id="1e705-115">—Or—</span></span>  
  
     <span data-ttu-id="1e705-116">在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠**，然後按一下 [**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e705-116">In the Orchestration View window, right-click **Ports** and then click **New Configured Port**.</span></span>  
  
     <span data-ttu-id="1e705-117">「連接埠組態精靈」隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1e705-117">The Port Configuration Wizard appears.</span></span>  
  
2.  <span data-ttu-id="1e705-118">請遵照精靈中的步驟設定連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e705-118">Follow the steps in the wizard to configure the port.</span></span> <span data-ttu-id="1e705-119">如需詳細資訊，請參閱[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="1e705-119">For more information, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).</span></span>  
  
### <a name="to-remove-a-port"></a><span data-ttu-id="1e705-120">移除連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-120">To remove a port</span></span>  
  
-   <span data-ttu-id="1e705-121">以滑鼠右鍵按一下要移除，然後按一下 連接埠**刪除**。</span><span class="sxs-lookup"><span data-stu-id="1e705-121">Right-click the port to remove, and then click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e705-122">如果您刪除連接埠連接到後**傳送**或**接收**圖形的協調流程中編譯之後，在圖形上的連接埠作業將不會被刪除，而且您會收到錯誤時您嘗試編譯。</span><span class="sxs-lookup"><span data-stu-id="1e705-122">If you delete a port after it has been connected to a **Send** or **Receive** shape in an orchestration that has been compiled, the port operations on the shape will not be deleted, and you will receive errors when you try to compile.</span></span> <span data-ttu-id="1e705-123">將圖形連接到其他連接埠，並重新設定連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="1e705-123">Connect the shape to another port and reconfigure the port operations.</span></span>  
  
### <a name="to-configure-a-port-by-using-the-port-configuration-wizard"></a><span data-ttu-id="1e705-124">使用連接埠組態精靈來設定連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-124">To configure a port by using the Port Configuration Wizard</span></span>  
  
1.  <span data-ttu-id="1e705-125">以滑鼠右鍵按一下要設定，然後再按一下的通訊埠**設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e705-125">Right-click the port to configure, and then click **Configure Port**.</span></span>  
  
2.  <span data-ttu-id="1e705-126">遵循設定連接埠的連接埠組態精靈中的步驟。</span><span class="sxs-lookup"><span data-stu-id="1e705-126">Follow the steps in the Port Configuration Wizard to configure the port.</span></span> <span data-ttu-id="1e705-127">如需詳細資訊，請參閱[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="1e705-127">For more information, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).</span></span>  
  
### <a name="to-configure-a-port-manually-by-using-the-properties-window"></a><span data-ttu-id="1e705-128">使用屬性視窗來手動設定連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-128">To configure a port manually by using the Properties window</span></span>  
  
1.  <span data-ttu-id="1e705-129">選取要設定的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e705-129">Select the port to configure.</span></span>  
  
2.  <span data-ttu-id="1e705-130">在 [屬性] 視窗中，指定以下屬性：</span><span class="sxs-lookup"><span data-stu-id="1e705-130">In the Properties window, specify the following properties:</span></span>  
  
    |<span data-ttu-id="1e705-131">屬性</span><span class="sxs-lookup"><span data-stu-id="1e705-131">Property</span></span>|<span data-ttu-id="1e705-132">Description</span><span class="sxs-lookup"><span data-stu-id="1e705-132">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="1e705-133">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="1e705-133">Port Type</span></span>|<span data-ttu-id="1e705-134">決定與連接埠相關的通訊模式、作業及多部分訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1e705-134">Determines the communication pattern, operations, and multi-part message types associated with a port.</span></span>|  
    |<span data-ttu-id="1e705-135">通訊方向</span><span class="sxs-lookup"><span data-stu-id="1e705-135">Communication Direction</span></span>|<span data-ttu-id="1e705-136">決定此協調流程是此通訊的傳送者或接收者。</span><span class="sxs-lookup"><span data-stu-id="1e705-136">Determines whether this orchestration is the sender or the receiver for this communication.</span></span>|  
    |<span data-ttu-id="1e705-137">通訊模式</span><span class="sxs-lookup"><span data-stu-id="1e705-137">Communication Pattern</span></span>|<span data-ttu-id="1e705-138">決定連接埠是用於「要求-回應」通訊或「單向」通訊</span><span class="sxs-lookup"><span data-stu-id="1e705-138">Determines if this port is used for request-response or one-way communication.</span></span> <span data-ttu-id="1e705-139">(這個屬性由**連接埠類型**屬性和是唯讀的。)</span><span class="sxs-lookup"><span data-stu-id="1e705-139">(This property is determined by the **Port Type** property and is read-only.)</span></span>|  
    |<span data-ttu-id="1e705-140">繫結</span><span class="sxs-lookup"><span data-stu-id="1e705-140">Binding</span></span>|<span data-ttu-id="1e705-141">決定訊息如何抵達其目的地：</span><span class="sxs-lookup"><span data-stu-id="1e705-141">Determines how a message gets to its destination:</span></span><br /><br /> <span data-ttu-id="1e705-142">直接—與其他協調流程通訊。</span><span class="sxs-lookup"><span data-stu-id="1e705-142">Direct—Communication is with another orchestration.</span></span><br /><br /> <span data-ttu-id="1e705-143">動態—與執行階段所決定的端點通訊。</span><span class="sxs-lookup"><span data-stu-id="1e705-143">Dynamic—Communication is with an endpoint that is determined at run time.</span></span><br /><br /> <span data-ttu-id="1e705-144">稍後指定—與系統管理員在設定階段所決定的端點通訊。</span><span class="sxs-lookup"><span data-stu-id="1e705-144">Specify later—Communication is with an endpoint that is determined by an administrator at configuration time.</span></span><br /><br /> <span data-ttu-id="1e705-145">立即指定—與設計階段已知的端點通訊。</span><span class="sxs-lookup"><span data-stu-id="1e705-145">Specify now—Communication is with an endpoint that is known at design time.</span></span>|  
    |<span data-ttu-id="1e705-146">識別碼</span><span class="sxs-lookup"><span data-stu-id="1e705-146">Identifier</span></span>|<span data-ttu-id="1e705-147">在協調流程中針對此連接埠所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="1e705-147">The name used for this port in the orchestration.</span></span>|  
    |<span data-ttu-id="1e705-148">排序的傳遞</span><span class="sxs-lookup"><span data-stu-id="1e705-148">Ordered Delivery</span></span>|<span data-ttu-id="1e705-149">針對接收埠，確保以指定順序發佈至 MessageBox 資料庫的訊息是以與發佈至 MessageBox 的相同順序傳遞給每一個相符的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1e705-149">For receive ports, ensures that messages that are published to the MessageBox database in a given order are delivered to each matching subscriber in the same order in which they were published to the message box.</span></span> <span data-ttu-id="1e705-150">如需詳細資訊，請參閱[排序訊息傳遞](../core/ordered-delivery-of-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="1e705-150">For more information, see [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md).</span></span>|  
    |<span data-ttu-id="1e705-151">傳遞通知</span><span class="sxs-lookup"><span data-stu-id="1e705-151">Delivery Notification</span></span>|<span data-ttu-id="1e705-152">針對傳送埠，決定是否要在訊息成功傳送時收到通知。</span><span class="sxs-lookup"><span data-stu-id="1e705-152">For send ports, determines whether want to receive an acknowledgment when a message is sent successfully.</span></span> <span data-ttu-id="1e705-153">如需詳細資訊，請參閱 < 傳遞通知 > 中[如何設定 「 傳送 」 圖形](../core/how-to-configure-the-send-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="1e705-153">For more information, see "Delivery Notification" in [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md).</span></span>|  
  
3.  <span data-ttu-id="1e705-154">指定的剩餘屬性由**繫結**屬性：</span><span class="sxs-lookup"><span data-stu-id="1e705-154">The remaining properties to specify are determined by the **Binding** property:</span></span>  
  
    -   <span data-ttu-id="1e705-155">直接繫結—用於直接與其他協調流程通訊時。</span><span class="sxs-lookup"><span data-stu-id="1e705-155">Direct binding—Used when communicating directly with another orchestration.</span></span>  
  
        |<span data-ttu-id="1e705-156">屬性</span><span class="sxs-lookup"><span data-stu-id="1e705-156">Property</span></span>|<span data-ttu-id="1e705-157">Description</span><span class="sxs-lookup"><span data-stu-id="1e705-157">Description</span></span>|  
        |--------------|-----------------|  
        |<span data-ttu-id="1e705-158">夥伴協調流程連接埠</span><span class="sxs-lookup"><span data-stu-id="1e705-158">Partner Orchestration Port</span></span>|<span data-ttu-id="1e705-159">決定會直接與夥伴協調流程繫結的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e705-159">Determines to which port the partner orchestrations will be directly bound.</span></span>|  
  
    -   <span data-ttu-id="1e705-160">動態繫結—用於與執行階段所決定的端點通訊時。</span><span class="sxs-lookup"><span data-stu-id="1e705-160">Dynamic binding—Used when communicating with an endpoint that is determined at run time.</span></span>  
  
        |<span data-ttu-id="1e705-161">屬性</span><span class="sxs-lookup"><span data-stu-id="1e705-161">Property</span></span>|<span data-ttu-id="1e705-162">Description</span><span class="sxs-lookup"><span data-stu-id="1e705-162">Description</span></span>|  
        |--------------|-----------------|  
        |<span data-ttu-id="1e705-163">接收管線</span><span class="sxs-lookup"><span data-stu-id="1e705-163">Receive Pipeline</span></span>|<span data-ttu-id="1e705-164">決定要用於內送訊息的管線。</span><span class="sxs-lookup"><span data-stu-id="1e705-164">Determines which pipeline to use for incoming messages.</span></span>|  
        |<span data-ttu-id="1e705-165">傳送管線</span><span class="sxs-lookup"><span data-stu-id="1e705-165">Send Pipeline</span></span>|<span data-ttu-id="1e705-166">決定要用於外寄訊息的管線。</span><span class="sxs-lookup"><span data-stu-id="1e705-166">Determines which pipeline to use for outgoing messages.</span></span>|  
  
    -   <span data-ttu-id="1e705-167">稍後指定—用於與系統管理員所設定的端點通訊時。</span><span class="sxs-lookup"><span data-stu-id="1e705-167">Specify later—Used when communicating with an endpoint that is configured by an administrator.</span></span>  
  
    -   <span data-ttu-id="1e705-168">立即指定—用於與設計階段已知的端點通訊時。</span><span class="sxs-lookup"><span data-stu-id="1e705-168">Specify now—Used when communicating with an endpoint that is known at design time.</span></span>  
  
        |<span data-ttu-id="1e705-169">屬性</span><span class="sxs-lookup"><span data-stu-id="1e705-169">Property</span></span>|<span data-ttu-id="1e705-170">Description</span><span class="sxs-lookup"><span data-stu-id="1e705-170">Description</span></span>|  
        |--------------|-----------------|  
        |<span data-ttu-id="1e705-171">接收管線</span><span class="sxs-lookup"><span data-stu-id="1e705-171">Receive Pipeline</span></span>|<span data-ttu-id="1e705-172">決定要用於內送訊息的管線。</span><span class="sxs-lookup"><span data-stu-id="1e705-172">Determines which pipeline to use for incoming messages.</span></span>|  
        |<span data-ttu-id="1e705-173">傳送管線</span><span class="sxs-lookup"><span data-stu-id="1e705-173">Send Pipeline</span></span>|<span data-ttu-id="1e705-174">決定要用於外寄訊息的管線。</span><span class="sxs-lookup"><span data-stu-id="1e705-174">Determines which pipeline to use for outgoing messages.</span></span>|  
        |<span data-ttu-id="1e705-175">傳輸</span><span class="sxs-lookup"><span data-stu-id="1e705-175">Transport</span></span>|<span data-ttu-id="1e705-176">決定要用於傳送訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="1e705-176">Determines which transport to use for sending messages.</span></span>|  
        |<span data-ttu-id="1e705-177">URI</span><span class="sxs-lookup"><span data-stu-id="1e705-177">URI</span></span>|<span data-ttu-id="1e705-178">決定傳送訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="1e705-178">Determines where to send messages.</span></span>|  
  
### <a name="to-add-a-port-operation"></a><span data-ttu-id="1e705-179">新增連接埠作業</span><span class="sxs-lookup"><span data-stu-id="1e705-179">To add a port operation</span></span>  
  
-   <span data-ttu-id="1e705-180">以滑鼠右鍵按一下您想要新增作業，然後按一下的通訊埠**新作業**。</span><span class="sxs-lookup"><span data-stu-id="1e705-180">Right-click the port to which you want to add an operation, and then click **New Operation**.</span></span>  
  
### <a name="to-remove-a-port-operation"></a><span data-ttu-id="1e705-181">移除連接埠作業</span><span class="sxs-lookup"><span data-stu-id="1e705-181">To remove a port operation</span></span>  
  
-   <span data-ttu-id="1e705-182">以滑鼠右鍵按一下要移除，然後按一下 連接埠作業**刪除**。</span><span class="sxs-lookup"><span data-stu-id="1e705-182">Right-click the port operation to remove, and then click **Delete**.</span></span>