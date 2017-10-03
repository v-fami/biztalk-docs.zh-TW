---
title: "如何執行連接埠組態精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Port Configuration Wizard [Orchestration Designer], starting
- Port Configuration Wizard [Orchestration Designer], how to
- Port Configuration Wizard [Orchestration Designer], about Port Configuration Wizard
- ports, Port Configuration Wizard [Orchestration Designer]
- Port Configuration Wizard [Orchestration Designer]
ms.assetid: 8035ce32-5ed4-49cb-b6f0-998b0460751e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbdb5843eb8011478f13c0de6443bb1ded177378
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-port-configuration-wizard"></a><span data-ttu-id="8090b-102">如何執行連接埠組態精靈</span><span class="sxs-lookup"><span data-stu-id="8090b-102">How to Run the Port Configuration Wizard</span></span>
<span data-ttu-id="8090b-103">您可以使用 [連接埠組態精靈] 來建立和設定「協調流程設計師」中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8090b-103">You use the Port Configuration Wizard to create and configure a port in Orchestration Designer.</span></span> <span data-ttu-id="8090b-104">連接埠必須具有與其相關聯的連接埠類型，您可以使用精靈選取現有的連接埠類型或建立新的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="8090b-104">A port must have a port type associated with it, and you use the wizard to select an existing port type or to create a new port type.</span></span> <span data-ttu-id="8090b-105">如需連接埠和連接埠類型的詳細資訊，請參閱[協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="8090b-105">For more information about ports and port types, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
### <a name="to-start-the-wizard"></a><span data-ttu-id="8090b-106">啟動精靈</span><span class="sxs-lookup"><span data-stu-id="8090b-106">To Start the wizard</span></span>  
  
1.  <span data-ttu-id="8090b-107">以滑鼠右鍵按一下 連接埠 （在設計介面上或在 協調流程檢視 視窗中），然後按一下**設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="8090b-107">Right-clicking a port (on the design surface or in the Orchestration View window) and clicking **Configure Port**.</span></span>  
  
2.  <span data-ttu-id="8090b-108">執行 [智慧標籤] 項目，其相關的動作可建立連接埠。</span><span class="sxs-lookup"><span data-stu-id="8090b-108">Running Smart Tag items whose associated actions cause a port to be created.</span></span>  
  
3.  <span data-ttu-id="8090b-109">選取**新設定連接埠參數**命令，從 [協調流程檢視] 視窗中的 [協調流程參數] 資料夾的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="8090b-109">Selecting the **New Configured Port Parameter** command from the shortcut menu of the Orchestration Parameters folder in the Orchestration View window.</span></span>  
  
### <a name="to-run-the-wizard"></a><span data-ttu-id="8090b-110">執行精靈</span><span class="sxs-lookup"><span data-stu-id="8090b-110">To Run the Wizard</span></span>  
  
1.  <span data-ttu-id="8090b-111">開啟 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="8090b-111">Open the Port Configuration Wizard.</span></span>  
  
2.  <span data-ttu-id="8090b-112">指定連接埠資訊。</span><span class="sxs-lookup"><span data-stu-id="8090b-112">Specify port information.</span></span> <span data-ttu-id="8090b-113">精靈會顯示數個頁面以協助您。</span><span class="sxs-lookup"><span data-stu-id="8090b-113">To help you, the wizard displays several pages.</span></span> <span data-ttu-id="8090b-114">完成每個頁面之後，將移至下列其中一個，依序按一下**下一步**，或移至前一個按一下**回**。</span><span class="sxs-lookup"><span data-stu-id="8090b-114">After completing each page, move to the following one by clicking **Next**, or move to the preceding one by clicking **Back**.</span></span>  
  
    -   <span data-ttu-id="8090b-115">**連接埠內容**。</span><span class="sxs-lookup"><span data-stu-id="8090b-115">**Port Properties**.</span></span> <span data-ttu-id="8090b-116">輸入連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="8090b-116">Type in a name for the port.</span></span>  
  
    -   <span data-ttu-id="8090b-117">**選取連接埠類型。**</span><span class="sxs-lookup"><span data-stu-id="8090b-117">**Select a Port Type.**</span></span> <span data-ttu-id="8090b-118">這個頁面上，您先選取您要讓**新連接埠類型**或**現有連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="8090b-118">On this page, you first select whether you want a **New Port Type** or an **Existing Port Type**.</span></span> <span data-ttu-id="8090b-119">如果您選取**現有連接埠類型**，然後使用樹狀目錄控制項來選擇要指派的現有連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="8090b-119">If you select **Existing Port Type**, you then use a tree control to choose which existing port type to assign.</span></span>  
  
         <span data-ttu-id="8090b-120">如果您選取**新連接埠類型**，則需要輸入中的連接埠類型名稱**名稱**文字，或是接受建議的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="8090b-120">If you select **New Port Type**, you then need to type the name of the port type in the **Name** text box, or accept the suggested default name.</span></span> <span data-ttu-id="8090b-121">您也要選取連接埠類型的通訊模式 (單向或要求-回應) 以及對新連接埠類型的所有存取限制。</span><span class="sxs-lookup"><span data-stu-id="8090b-121">You also select the port type's communication pattern (one-way or request-response) and any access restrictions to impose on the new port type.</span></span>  
  
    -   <span data-ttu-id="8090b-122">**連接埠繫結**。</span><span class="sxs-lookup"><span data-stu-id="8090b-122">**Port Binding**.</span></span> <span data-ttu-id="8090b-123">在此頁面上您指定的方向的通訊，也稱為*極性*，以及連接埠的繫結類型。</span><span class="sxs-lookup"><span data-stu-id="8090b-123">On this page you specify the direction of communication, also known as the *polarity*, and the binding type of the port.</span></span>  
  
         <span data-ttu-id="8090b-124">極性您選擇部分取決於您在精靈的上一頁選取的連接埠類型的通訊模式**選取連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="8090b-124">The polarity choice you make depends in part on the communication pattern of the port type that you selected on the preceding page of the wizard, **Select a Port Type**.</span></span> <span data-ttu-id="8090b-125">您選擇的項目摘要如下表：</span><span class="sxs-lookup"><span data-stu-id="8090b-125">Your choices are summarized in the following table:</span></span>  
  
        |<span data-ttu-id="8090b-126">連接埠方向</span><span class="sxs-lookup"><span data-stu-id="8090b-126">Port direction</span></span>|<span data-ttu-id="8090b-127">通訊模式</span><span class="sxs-lookup"><span data-stu-id="8090b-127">Communication pattern</span></span>|<span data-ttu-id="8090b-128">若要連接埠繫結 頁面上選擇的通訊方向</span><span class="sxs-lookup"><span data-stu-id="8090b-128">Direction of communication to choose on Port Binding page</span></span>|  
        |--------------------|---------------------------|---------------------------------------------------------------|  
        |<span data-ttu-id="8090b-129">Send</span><span class="sxs-lookup"><span data-stu-id="8090b-129">Send</span></span>|<span data-ttu-id="8090b-130">單向</span><span class="sxs-lookup"><span data-stu-id="8090b-130">One-way</span></span>|<span data-ttu-id="8090b-131">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="8090b-131">I will always be sending messages on this port.</span></span>|  
        |<span data-ttu-id="8090b-132">Receive</span><span class="sxs-lookup"><span data-stu-id="8090b-132">Receive</span></span>|<span data-ttu-id="8090b-133">單向</span><span class="sxs-lookup"><span data-stu-id="8090b-133">One-way</span></span>|<span data-ttu-id="8090b-134">我將總是在此連接埠接收訊息。</span><span class="sxs-lookup"><span data-stu-id="8090b-134">I will always be receiving messages on this port.</span></span>|  
        |<span data-ttu-id="8090b-135">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="8090b-135">Send-Receive</span></span>|<span data-ttu-id="8090b-136">請求-回應</span><span class="sxs-lookup"><span data-stu-id="8090b-136">Solicit-response</span></span>|<span data-ttu-id="8090b-137">我將會傳送要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="8090b-137">I will be sending a request and receiving a response.</span></span>|  
        |<span data-ttu-id="8090b-138">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="8090b-138">Receive-Send</span></span>|<span data-ttu-id="8090b-139">要求-回應</span><span class="sxs-lookup"><span data-stu-id="8090b-139">Request-response</span></span>|<span data-ttu-id="8090b-140">我將會接收要求並傳送回應。</span><span class="sxs-lookup"><span data-stu-id="8090b-140">I will be receiving a request and sending a response.</span></span>|  
  
         <span data-ttu-id="8090b-141">您可以從四個不同的繫結類型選擇：[稍後指定]、[立即指定]、[動態] 以及 [直接]。</span><span class="sxs-lookup"><span data-stu-id="8090b-141">You have a choice of four different binding types: Specify later, Specify now, Dynamic, and Direct.</span></span> <span data-ttu-id="8090b-142">每個選擇會顯示不同的組態選項組，摘要如下：</span><span class="sxs-lookup"><span data-stu-id="8090b-142">Each choice displays a different set of configuration options, as summarized here:</span></span>  
  
         <span data-ttu-id="8090b-143">**稍後指定。**</span><span class="sxs-lookup"><span data-stu-id="8090b-143">**Specify later.**</span></span> <span data-ttu-id="8090b-144">在選取此選項之後，您不會在精靈中進行進一步的組態選擇，因為不會在設計階段決定繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="8090b-144">After selecting this option, you make no further configuration choices in the wizard because binding information is not determined at design time.</span></span> <span data-ttu-id="8090b-145">通常是由系統管理員在部署階段新增。</span><span class="sxs-lookup"><span data-stu-id="8090b-145">Typically it is added by an Administrator at deployment time.</span></span>  
  
         <span data-ttu-id="8090b-146">**立即指定。**</span><span class="sxs-lookup"><span data-stu-id="8090b-146">**Specify now.**</span></span> <span data-ttu-id="8090b-147">您可以在設計階段指定用來定義與連接埠繫結的實體 URI。</span><span class="sxs-lookup"><span data-stu-id="8090b-147">You can specify at design time a URI that defines the entity to which the port is to be bound.</span></span> <span data-ttu-id="8090b-148">您也需要在包含「BizTalk 訊息佇列」的傳輸類型清單中選取 FILE、SMTP、HTTP 和 SOAP。</span><span class="sxs-lookup"><span data-stu-id="8090b-148">You also need to select from a list of transport types that includes BizTalk Message Queuing, FILE, SMTP, HTTP, and SOAP.</span></span> <span data-ttu-id="8090b-149">這是為了協調流程設計師中的早期繫結而建立的硬式編碼清單；因此，其他傳輸將無法在此清單中取得。</span><span class="sxs-lookup"><span data-stu-id="8090b-149">This is a hard-coded list for the purpose of early binding in Orchestration Designer; therefore, other transports are not available in this list.</span></span> <span data-ttu-id="8090b-150">最後，您要從可用管線清單選取接收管線和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="8090b-150">Finally, you select a receive pipeline and a send pipeline from a list of available pipelines.</span></span> <span data-ttu-id="8090b-151">每個清單中目前的專案，再加上從參考的組件，會顯示選取管線的選項包含所有的管線**選取成品類型** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8090b-151">The list for each includes all pipelines in the current project plus the option of selecting a pipeline from a referenced assembly, which displays the **Select Artifact Type** dialog box.</span></span>  
  
         <span data-ttu-id="8090b-152">**動態的。**</span><span class="sxs-lookup"><span data-stu-id="8090b-152">**Dynamic.**</span></span> <span data-ttu-id="8090b-153">這個選項擁有類似的選擇，可以**現在指定**，但只供傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8090b-153">This option has similar choices to **Specify now**, but it is available only for a send port.</span></span> <span data-ttu-id="8090b-154">您可以指定要使用的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="8090b-154">You can specify a send pipeline to use.</span></span> <span data-ttu-id="8090b-155">您可以指定分別在連接埠**運算式**圖形，將它指派執行階段。</span><span class="sxs-lookup"><span data-stu-id="8090b-155">You can specify the port separately in an **Expression** shape so that it is assigned at run time.</span></span>  
  
         <span data-ttu-id="8090b-156">**直接。**</span><span class="sxs-lookup"><span data-stu-id="8090b-156">**Direct.**</span></span> <span data-ttu-id="8090b-157">對於直接繫結，您可以選取連接埠以供連接、執行以 MessageBox 資料庫中內送訊息的篩選條件運算式為基礎的路由，或將它設為自我相互關聯的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8090b-157">For direct binding, you can either select a port to connect to, to do routing based on filter expressions on incoming messages in the MessageBox database, or to make it a self-correlating port.</span></span> <span data-ttu-id="8090b-158">您可以從下拉式清單方塊中選取。</span><span class="sxs-lookup"><span data-stu-id="8090b-158">You can select a port from a drop-down list box.</span></span>  
  
         <span data-ttu-id="8090b-159">如需詳細資訊，請參閱[連接埠繫結](../core/port-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="8090b-159">For more information, see [Port Bindings](../core/port-bindings.md).</span></span>  
  
3.  <span data-ttu-id="8090b-160">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="8090b-160">Complete the wizard.</span></span> <span data-ttu-id="8090b-161">標題為連接埠組態精靈的最後一頁**完成連接埠精靈**，會顯示您在先前的頁面，方便在執行變更之前驗證做的選擇。</span><span class="sxs-lookup"><span data-stu-id="8090b-161">The final page of the Port Configuration Wizard, entitled **Completing the Port Wizard**, displays the choices you made on the preceding pages so that you can verify them before committing the changes.</span></span> <span data-ttu-id="8090b-162">如果變更正確無誤，請按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="8090b-162">If the changes are correct, click **Finish**.</span></span> <span data-ttu-id="8090b-163">否則，請按一下**回**重新輸入您想要變更任何資訊。</span><span class="sxs-lookup"><span data-stu-id="8090b-163">Otherwise, click **Back** to re-enter any information you want to change.</span></span> <span data-ttu-id="8090b-164">然後再繼續執行精靈並按一下**完成**最後一頁上顯示的資訊符合您想要的變更時。</span><span class="sxs-lookup"><span data-stu-id="8090b-164">Then move through the wizard again and click **Finish** when the information displayed on the final page matches the changes you want to make.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8090b-165">如果您要建立新的連接埠，而且您按一下**取消**在隨時之前完成連接埠組態精靈中，無法建立連接埠。</span><span class="sxs-lookup"><span data-stu-id="8090b-165">If you are creating a new port and you click **Cancel** in the wizard at any time before finishing port configuration, the port is not created.</span></span> <span data-ttu-id="8090b-166">若您使用精靈修改現有的連接埠，取消精靈則會回復任何您已進行的變更。</span><span class="sxs-lookup"><span data-stu-id="8090b-166">If you were using the wizard to modify an existing port, canceling the wizard undoes any changes you have made.</span></span> <span data-ttu-id="8090b-167">否則，如果您按一下**取消**在精靈中，仍會建立配接器，但未設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="8090b-167">Otherwise, if you click **Cancel** in the wizard, the adapter is still created, but its properties are not set.</span></span> <span data-ttu-id="8090b-168">您可以在 [屬性] 視窗中為連接埠手動設定連接埠屬性，或者再次執行精靈。</span><span class="sxs-lookup"><span data-stu-id="8090b-168">You can set port properties manually in the Properties window for the port, or you can run the wizard again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8090b-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8090b-169">See Also</span></span>  
 [<span data-ttu-id="8090b-170">協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="8090b-170">Using Ports in Orchestrations</span></span>](../core/using-ports-in-orchestrations.md)