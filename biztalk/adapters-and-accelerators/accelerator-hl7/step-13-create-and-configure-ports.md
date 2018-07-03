---
title: 步驟 13： 建立和設定連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, creating
- message enrichment tutorial, ports
- creating, ports
- configuring, ports
- ports, configuring
ms.assetid: cc0540d7-46fc-4d9f-bcf3-0b0e0179fd51
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4414795b1c214e8dbe15eb3117527c3cb5227cde
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991935"
---
# <a name="step-13-create-and-configure-ports"></a><span data-ttu-id="c213d-102">步驟 13： 建立和設定連接埠</span><span class="sxs-lookup"><span data-stu-id="c213d-102">Step 13: Create and Configure Ports</span></span>
<span data-ttu-id="c213d-103">在此步驟中，您可以使用連接埠組態精靈來建立及設定連接埠在協調流程設計師。</span><span class="sxs-lookup"><span data-stu-id="c213d-103">In this step, you use the Port Configuration Wizard to create and configure ports in Orchestration Designer.</span></span> <span data-ttu-id="c213d-104">連接埠指定您的協調流程如何傳送和接收訊息，並從商務程序。</span><span class="sxs-lookup"><span data-stu-id="c213d-104">Ports specify how your orchestration sends and receives messages to and from business processes.</span></span> <span data-ttu-id="c213d-105">每個連接埠具有類型、 方向和繫結。</span><span class="sxs-lookup"><span data-stu-id="c213d-105">Each port has a type, a direction, and a binding.</span></span> <span data-ttu-id="c213d-106">屬性一起決定通訊的通訊模式、 位置或從中方向[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]傳送或接收訊息，以及通訊進行的方式。</span><span class="sxs-lookup"><span data-stu-id="c213d-106">The properties together determine the direction of communication, the pattern of communication, the location to or from which [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] sends or receives the message, and how the communication takes place.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="c213d-107"> 使用最小值較低層通訊協定 (MLLP) 配接器做為傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c213d-107"> uses the Minimum Lower Layer Protocol (MLLP) adapter as a send port.</span></span> <span data-ttu-id="c213d-108">MLLP 配接器會使用 TCP 通訊端通訊來與其他應用程式，例如實驗室應用程式、 保險的應用程式和舊版的特定業務應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="c213d-108">The MLLP adapter uses TCP sockets communication to interface with other applications, such as laboratory applications, insurance applications, and legacy line-of-business applications.</span></span> <span data-ttu-id="c213d-109">MLLP 傳送配接器表示[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器：</span><span class="sxs-lookup"><span data-stu-id="c213d-109">The MLLP Send Adapter represents a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter that is:</span></span>  

- <span data-ttu-id="c213d-110">自訂。</span><span class="sxs-lookup"><span data-stu-id="c213d-110">Customized.</span></span> <span data-ttu-id="c213d-111">配接器只隨附[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]，而不是隨附於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="c213d-111">The adapter only ships with [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], as opposed to shipping with BizTalk Server.</span></span>  

- <span data-ttu-id="c213d-112">通訊協定/傳輸。</span><span class="sxs-lookup"><span data-stu-id="c213d-112">Protocol/Transport.</span></span> <span data-ttu-id="c213d-113">配接器不是應用程式或資料配接器。</span><span class="sxs-lookup"><span data-stu-id="c213d-113">The adapter is not an application or data adapter.</span></span>  

- <span data-ttu-id="c213d-114">靜態。</span><span class="sxs-lookup"><span data-stu-id="c213d-114">Static.</span></span> <span data-ttu-id="c213d-115">配接器組態不包括自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="c213d-115">The adapter configuration does not involve a custom user interface.</span></span>  

- <span data-ttu-id="c213d-116">非同步的。</span><span class="sxs-lookup"><span data-stu-id="c213d-116">Asynchronous.</span></span> <span data-ttu-id="c213d-117">配接器不會封鎖傳訊引擎執行緒，可讓所有介面卡的效能提升，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機。</span><span class="sxs-lookup"><span data-stu-id="c213d-117">The adapter does not block the Messaging Engine thread, which enables increased performance of all adapters that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hosts.</span></span>  

- <span data-ttu-id="c213d-118">非交易。</span><span class="sxs-lookup"><span data-stu-id="c213d-118">Nontransacted.</span></span> <span data-ttu-id="c213d-119">配接器不是交易性的接收或傳送[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="c213d-119">The adapter is not a transacted receive or send [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter.</span></span>  

- <span data-ttu-id="c213d-120">規則。</span><span class="sxs-lookup"><span data-stu-id="c213d-120">Regular.</span></span> <span data-ttu-id="c213d-121">配接器不會在個別的應用程式處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="c213d-121">The adapter does not run in a separate application process.</span></span>  

- <span data-ttu-id="c213d-122">單向和雙向。</span><span class="sxs-lookup"><span data-stu-id="c213d-122">Both One-Way and Two-Way.</span></span> <span data-ttu-id="c213d-123">配接器支援單向和要求-回應/請求-回應模式的互動。</span><span class="sxs-lookup"><span data-stu-id="c213d-123">The adapter supports both One-way and Request-Response/Solicit-Response modes of interaction.</span></span>  

  <span data-ttu-id="c213d-124">MLLP 配接器可以將個別訊息提交，或提交批次中的訊息。</span><span class="sxs-lookup"><span data-stu-id="c213d-124">The MLLP adapter can submit individual messages or submit messages in a batch.</span></span> <span data-ttu-id="c213d-125">MLLP 訊息的開頭標記以包裝函式字元十六進位 0x0b （也就是啟動區塊或 SB 字元），和十六進位的 0x1c 字元 （也稱為 End 區塊或 EB 字元） 的組合來標記訊息結尾緊接著 0x0d 字元 （歸位字元）。</span><span class="sxs-lookup"><span data-stu-id="c213d-125">The beginning of an MLLP message is marked with a wrapper character, hexadecimal 0x0b (also known as the Start Block or SB character), and the end of the message is marked by the combination of a hexadecimal 0x1c character (also known as the End Block or EB character) immediately followed by the 0x0d character (Carriage Return).</span></span> <span data-ttu-id="c213d-126">BTAHL7 效能計數器只會計算傳送訊息的這些包裝函式的字元。</span><span class="sxs-lookup"><span data-stu-id="c213d-126">BTAHL7 performance counters only count these wrapper characters for sent messages.</span></span> <span data-ttu-id="c213d-127">接收訊息時，BTAHL7 效能計數器不計算這些包裝函式的字元。</span><span class="sxs-lookup"><span data-stu-id="c213d-127">BTAHL7 performance counters do not count these wrapper characters when receiving messages.</span></span>  

> [!NOTE]
>  <span data-ttu-id="c213d-128">MLLP 通訊協定標準不訊息承載中允許下 0x20 的字元，因為它會干擾偵測的 SB 和 EB 字元的能力。</span><span class="sxs-lookup"><span data-stu-id="c213d-128">The MLLP protocol standard does not allow characters under 0x20 in the message payload because it interferes with the ability to detect the SB and EB characters.</span></span> <span data-ttu-id="c213d-129">您可以設定 「 SB 」 和 「 EB 的字元值，因此請小心此問題的變更時。</span><span class="sxs-lookup"><span data-stu-id="c213d-129">You can configure the SB and EB character values, so be wary of this issue when making changes.</span></span>  

 <span data-ttu-id="c213d-130">在此步驟中，您可以設定的 MLLP 配接器和 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="c213d-130">In this step, you configure the MLLP adapter and SOAP adapter.</span></span>  

### <a name="to-create-and-configure-the-ports"></a><span data-ttu-id="c213d-131">建立和設定連接埠</span><span class="sxs-lookup"><span data-stu-id="c213d-131">To create and configure the ports</span></span>  

1. <span data-ttu-id="c213d-132">在協調流程設計師中，拖曳**連接埠**圖形從工具箱拖曳至連接埠介面左邊的 [設計] 檢視介面，然後將圖形，讓它與水平對齊**DoorbellReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="c213d-132">In Orchestration Designer, drag the **Port** shape from the Toolbox to the Port Surface on the left side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellReceive** shape.</span></span>  

2. <span data-ttu-id="c213d-133">在 [**連接埠組態精靈**，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c213d-133">In the **Port Configuration Wizard**, click **Next**.</span></span>  

3. <span data-ttu-id="c213d-134">在上**連接埠屬性**頁面上，於**名稱**欄位中，輸入**SOAPReceivePort**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="c213d-134">On the **Port Properties** page, in the **Name** field, type **SOAPReceivePort**, and then click **Next**.</span></span>  

4. <span data-ttu-id="c213d-135">在上**選取 連接埠類型**頁面上，輸入下列資訊，然後按一下 **下一步**以繼續。</span><span class="sxs-lookup"><span data-stu-id="c213d-135">On the **Select a Port Type** page, enter the following information, and then click **Next** to continue.</span></span>  


   |         <span data-ttu-id="c213d-136">使用</span><span class="sxs-lookup"><span data-stu-id="c213d-136">Use this</span></span>          |          <span data-ttu-id="c213d-137">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="c213d-137">To do this</span></span>           |
   |---------------------------|-------------------------------|
   |    <span data-ttu-id="c213d-138">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="c213d-138">**Port Type Name**</span></span>     | <span data-ttu-id="c213d-139">型別**SOAPReceivePortType**。</span><span class="sxs-lookup"><span data-stu-id="c213d-139">Type **SOAPReceivePortType**.</span></span> |
   | <span data-ttu-id="c213d-140">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="c213d-140">**Communication Pattern**</span></span> |      <span data-ttu-id="c213d-141">選取 **單向**。</span><span class="sxs-lookup"><span data-stu-id="c213d-141">Select **One-Way**.</span></span>      |
   |  <span data-ttu-id="c213d-142">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="c213d-142">**Access Restrictions**</span></span>  | <span data-ttu-id="c213d-143">選取 **公用-沒有限制**。</span><span class="sxs-lookup"><span data-stu-id="c213d-143">Select **Public - no limit**.</span></span> |


5. <span data-ttu-id="c213d-144">在 [**連接埠繫結**頁面上，按一下**下一步]** 以接受預設值。</span><span class="sxs-lookup"><span data-stu-id="c213d-144">On the **Port Binding** page, click **Next** to accept the default values.</span></span>  

6. <span data-ttu-id="c213d-145">在 **完成連接埠精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="c213d-145">On the **Completing the Port Wizard** page, click **Finish**.</span></span>  

7. <span data-ttu-id="c213d-146">拖曳**連接埠**圖形從工具箱拖曳至設計檢視介面時，右側連接埠介面，並將圖形放置，讓它與水平對齊**DoorbellSend**圖形。</span><span class="sxs-lookup"><span data-stu-id="c213d-146">Drag the **Port** shape from the Toolbox to the Port Surface on the right side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellSend** shape.</span></span>  

8. <span data-ttu-id="c213d-147">使用**連接埠組態精靈**如同在步驟 2 到 7，建立額外的傳送埠，使用下列參數：</span><span class="sxs-lookup"><span data-stu-id="c213d-147">Using the **Port Configuration Wizard** as you did in steps 2 through 7, create an additional send port using the following parameters:</span></span>  


   |              <span data-ttu-id="c213d-148">屬性</span><span class="sxs-lookup"><span data-stu-id="c213d-148">Property</span></span>               |                   <span data-ttu-id="c213d-149">參數</span><span class="sxs-lookup"><span data-stu-id="c213d-149">Parameter</span></span>                   |
   |-------------------------------------|-----------------------------------------------|
   |      <span data-ttu-id="c213d-150">**連接埠的屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="c213d-150">**Port Properties Name**</span></span>       |                 <span data-ttu-id="c213d-151">MLLPSendPort</span><span class="sxs-lookup"><span data-stu-id="c213d-151">MLLPSendPort</span></span>                  |
   |         <span data-ttu-id="c213d-152">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="c213d-152">**Port Type Name**</span></span>          |               <span data-ttu-id="c213d-153">MLLPSendPortType</span><span class="sxs-lookup"><span data-stu-id="c213d-153">MLLPSendPortType</span></span>                |
   |      <span data-ttu-id="c213d-154">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="c213d-154">**Communication Pattern**</span></span>      |                    <span data-ttu-id="c213d-155">單向</span><span class="sxs-lookup"><span data-stu-id="c213d-155">One-Way</span></span>                    |
   |       <span data-ttu-id="c213d-156">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="c213d-156">**Access Restrictions**</span></span>       |               <span data-ttu-id="c213d-157">公用 - 沒有限制</span><span class="sxs-lookup"><span data-stu-id="c213d-157">Public - no limit</span></span>               |
   |          <span data-ttu-id="c213d-158">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="c213d-158">**Port Binding**</span></span>           |                 <span data-ttu-id="c213d-159">稍後指定</span><span class="sxs-lookup"><span data-stu-id="c213d-159">Specify Later</span></span>                 |
   | <span data-ttu-id="c213d-160">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="c213d-160">**Port direction of communication**</span></span> | <span data-ttu-id="c213d-161">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c213d-161">I'll always be sending messages on this port.</span></span> |


9. <span data-ttu-id="c213d-162">在**協調流程檢視** 視窗中，使用**型別**，**連接埠類型**，和**SOAPReceivePortType**節點展開，展開**Operation_1**，然後按一下**要求**。</span><span class="sxs-lookup"><span data-stu-id="c213d-162">In the **Orchestration View** window, with the **Types**, **Ports Types**, and **SOAPReceivePortType** nodes expanded, expand **Operation_1**, and then click **Request**.</span></span>  

10. <span data-ttu-id="c213d-163">在 **屬性**視窗中的，下拉式清單中**訊息類型**，展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**.</span><span class="sxs-lookup"><span data-stu-id="c213d-163">In the **Properties** window, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.</span></span>  

11. <span data-ttu-id="c213d-164">在 **協調流程檢視** 視窗中，展開**MLLPSendPortType**，展開**Operation_1**，然後按一下 **要求**。</span><span class="sxs-lookup"><span data-stu-id="c213d-164">In the **Orchestration View** window, expand **MLLPSendPortType**, expand **Operation_1**, and then click **Request**.</span></span>  

12. <span data-ttu-id="c213d-165">在 **屬性**視窗中的，下拉式清單中**訊息類型**，展開**多部分訊息類型**，然後按一下  **BTAHL7_Project.DoorbellFinalMessageType**。</span><span class="sxs-lookup"><span data-stu-id="c213d-165">In the **Properties** window, in the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.</span></span>  

13. <span data-ttu-id="c213d-166">在 **名稱**欄位中，輸入**回應**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c213d-166">In the **Name** field, type **Response**, then press **Enter**.</span></span>  

14. <span data-ttu-id="c213d-167">協調流程設計檢視介面上，按一下**DoorbellReceive**動作圖形。</span><span class="sxs-lookup"><span data-stu-id="c213d-167">On the orchestration Design view surface, click the **DoorbellReceive** action shape.</span></span>  

15. <span data-ttu-id="c213d-168">在 **屬性**視窗中的，下拉式清單中**訊息**，選取**DoorbellInputMessage**。</span><span class="sxs-lookup"><span data-stu-id="c213d-168">In the **Properties** window, in the drop-down list for **Message**, select **DoorbellInputMessage**.</span></span>  

16. <span data-ttu-id="c213d-169">協調流程設計檢視介面上，按一下**DoorbellSend**圖形。</span><span class="sxs-lookup"><span data-stu-id="c213d-169">On the orchestration Design view surface, click the **DoorbellSend** shape.</span></span>  

17. <span data-ttu-id="c213d-170">在 **屬性**視窗中的，下拉式清單中**訊息**，選取**DoorbellFinalMessage**。</span><span class="sxs-lookup"><span data-stu-id="c213d-170">In the **Properties** window, in the drop-down list for **Message**, select **DoorbellFinalMessage**.</span></span>  

18. <span data-ttu-id="c213d-171">按一下中的綠色控**SOAPReceivePort**並將它拖曳至的綠色控點**DoorbellReceive**接收 」 圖形連接**SOAPReceivePort** 至**DoorbellReceive**接收圖形。</span><span class="sxs-lookup"><span data-stu-id="c213d-171">Click the green handle in the **SOAPReceivePort** and drag it to the green handle on the **DoorbellReceive** receive shape to connect the **SOAPReceivePort** to the **DoorbellReceive** receive shape.</span></span>  

19. <span data-ttu-id="c213d-172">按一下中的綠色控**DoorbellSend**圖形，並將它拖曳至的綠色控點**MLLPSendPort**連接埠**DoorbellSend** 到傳送圖形**MLLPSendPort**連接埠。</span><span class="sxs-lookup"><span data-stu-id="c213d-172">Click the green handle in the **DoorbellSend** shape and drag it to the green handle on the **MLLPSendPort** port to connect the **DoorbellSend** send shape to the **MLLPSendPort** port.</span></span>  

20. <span data-ttu-id="c213d-173">按一下 **方案總管 中**下方協調流程檢視 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c213d-173">Click the **Solution Explorer** tab under the Orchestration View.</span></span>  

21. <span data-ttu-id="c213d-174">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="c213d-174">In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Build**.</span></span> <span data-ttu-id="c213d-175">請確定在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="c213d-175">Ensure that a success message appears in the output window.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="c213d-176">如果沒有成功的訊息出現時，進行疑難排解的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c213d-176">If no success message appears, troubleshoot the solution.</span></span>  

22. <span data-ttu-id="c213d-177">以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**部署**部署 BTAHL7 專案。</span><span class="sxs-lookup"><span data-stu-id="c213d-177">Right-click **BTAHL7 Project**, and click **Deploy** to deploy the BTAHL7 project.</span></span>  

    <span data-ttu-id="c213d-178">請繼續進行[步驟 14： 發佈為 Web 服務協調流程](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="c213d-178">Proceed to [Step 14: Publish the Orchestration as a Web Service](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="c213d-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c213d-179">See Also</span></span>  
 [<span data-ttu-id="c213d-180">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="c213d-180">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)