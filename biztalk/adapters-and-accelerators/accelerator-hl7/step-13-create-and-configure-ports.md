---
title: 步驟 13： 建立和設定連接埠 |Microsoft 文件
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
ms.openlocfilehash: 7c1b18e5b7addf1bae390dd541b84d17bd94023d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006383"
---
# <a name="step-13-create-and-configure-ports"></a><span data-ttu-id="ed2f3-102">步驟 13： 建立和設定連接埠</span><span class="sxs-lookup"><span data-stu-id="ed2f3-102">Step 13: Create and Configure Ports</span></span>
<span data-ttu-id="ed2f3-103">在此步驟中，您可以使用連接埠組態精靈來建立及設定協調流程設計師中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-103">In this step, you use the Port Configuration Wizard to create and configure ports in Orchestration Designer.</span></span> <span data-ttu-id="ed2f3-104">連接埠指定您的協調流程傳送和接收訊息，並從商務程序的方式。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-104">Ports specify how your orchestration sends and receives messages to and from business processes.</span></span> <span data-ttu-id="ed2f3-105">每個連接埠都有類型、 方向和繫結。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-105">Each port has a type, a direction, and a binding.</span></span> <span data-ttu-id="ed2f3-106">屬性可同時決定通訊的通訊模式、 位置或從中方向[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]傳送或接收訊息，以及如何的通訊會發生。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-106">The properties together determine the direction of communication, the pattern of communication, the location to or from which [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] sends or receives the message, and how the communication takes place.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="ed2f3-107">使用最小值較低層通訊協定 (MLLP) 配接器做為傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-107"> uses the Minimum Lower Layer Protocol (MLLP) adapter as a send port.</span></span> <span data-ttu-id="ed2f3-108">MLLP 配接器介面與其他應用程式，例如實驗室儀器應用程式、 保險的應用程式和繼承的特定業務應用程式使用 TCP 通訊端通訊。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-108">The MLLP adapter uses TCP sockets communication to interface with other applications, such as laboratory applications, insurance applications, and legacy line-of-business applications.</span></span> <span data-ttu-id="ed2f3-109">代表 MLLP 傳送配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器：</span><span class="sxs-lookup"><span data-stu-id="ed2f3-109">The MLLP Send Adapter represents a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter that is:</span></span>  
  
-   <span data-ttu-id="ed2f3-110">自訂。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-110">Customized.</span></span> <span data-ttu-id="ed2f3-111">配接器只隨附[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]，與 BizTalk server 傳送。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-111">The adapter only ships with [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], as opposed to shipping with BizTalk Server.</span></span>  
  
-   <span data-ttu-id="ed2f3-112">通訊協定/傳輸。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-112">Protocol/Transport.</span></span> <span data-ttu-id="ed2f3-113">配接器不是應用程式或資料配接器。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-113">The adapter is not an application or data adapter.</span></span>  
  
-   <span data-ttu-id="ed2f3-114">靜態。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-114">Static.</span></span> <span data-ttu-id="ed2f3-115">配接器組態不包括自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-115">The adapter configuration does not involve a custom user interface.</span></span>  
  
-   <span data-ttu-id="ed2f3-116">非同步的。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-116">Asynchronous.</span></span> <span data-ttu-id="ed2f3-117">配接器不會封鎖傳訊引擎執行緒，可讓所有介面卡的提升的效能，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-117">The adapter does not block the Messaging Engine thread, which enables increased performance of all adapters that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hosts.</span></span>  
  
-   <span data-ttu-id="ed2f3-118">非交易。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-118">Nontransacted.</span></span> <span data-ttu-id="ed2f3-119">配接器不是交易性的接收或傳送[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-119">The adapter is not a transacted receive or send [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter.</span></span>  
  
-   <span data-ttu-id="ed2f3-120">規則。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-120">Regular.</span></span> <span data-ttu-id="ed2f3-121">配接器不會在個別的應用程式處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-121">The adapter does not run in a separate application process.</span></span>  
  
-   <span data-ttu-id="ed2f3-122">單向和雙向。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-122">Both One-Way and Two-Way.</span></span> <span data-ttu-id="ed2f3-123">配接器支援單向和要求-回應/請求-回應模式的互動。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-123">The adapter supports both One-way and Request-Response/Solicit-Response modes of interaction.</span></span>  
  
 <span data-ttu-id="ed2f3-124">MLLP 配接器可以將個別訊息提交或提交批次中的訊息。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-124">The MLLP adapter can submit individual messages or submit messages in a batch.</span></span> <span data-ttu-id="ed2f3-125">MLLP 訊息的開頭是以包裝函式的字元、 十六進位 0x0b （也就是啟動區塊或 SB 字元），而且訊息結尾是十六進位 0x1c 字元 （也稱為 End 區塊或 EB 字元） 的組合緊接著 0x0d 字元 （歸位字元）。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-125">The beginning of an MLLP message is marked with a wrapper character, hexadecimal 0x0b (also known as the Start Block or SB character), and the end of the message is marked by the combination of a hexadecimal 0x1c character (also known as the End Block or EB character) immediately followed by the 0x0d character (Carriage Return).</span></span> <span data-ttu-id="ed2f3-126">BTAHL7 效能計數器只會計算傳送訊息的這些包裝函式的字元。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-126">BTAHL7 performance counters only count these wrapper characters for sent messages.</span></span> <span data-ttu-id="ed2f3-127">接收訊息時，BTAHL7 效能計數器不計算這些包裝函式的字元。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-127">BTAHL7 performance counters do not count these wrapper characters when receiving messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed2f3-128">MLLP 通訊協定標準不訊息內容中允許 0x20 下的字元，因為它會干擾偵測 SB 和 EB 字元的功能。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-128">The MLLP protocol standard does not allow characters under 0x20 in the message payload because it interferes with the ability to detect the SB and EB characters.</span></span> <span data-ttu-id="ed2f3-129">您可以設定 SB 和 EB 字元值，所以要小心此問題進行變更時。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-129">You can configure the SB and EB character values, so be wary of this issue when making changes.</span></span>  
  
 <span data-ttu-id="ed2f3-130">在此步驟中，您可以設定 MLLP 配接器與 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-130">In this step, you configure the MLLP adapter and SOAP adapter.</span></span>  
  
### <a name="to-create-and-configure-the-ports"></a><span data-ttu-id="ed2f3-131">建立和設定連接埠</span><span class="sxs-lookup"><span data-stu-id="ed2f3-131">To create and configure the ports</span></span>  
  
1.  <span data-ttu-id="ed2f3-132">在協調流程設計師 」 中，拖曳**連接埠**圖形從工具箱拖曳至設計檢視介面中，左側連接埠介面，然後將圖形放，讓它與水平對齊**DoorbellReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-132">In Orchestration Designer, drag the **Port** shape from the Toolbox to the Port Surface on the left side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellReceive** shape.</span></span>  
  
2.  <span data-ttu-id="ed2f3-133">在**連接埠組態精靈**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-133">In the **Port Configuration Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="ed2f3-134">在**連接埠內容**頁面上，於**名稱**欄位中，輸入**SOAPReceivePort**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-134">On the **Port Properties** page, in the **Name** field, type **SOAPReceivePort**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ed2f3-135">在**選取連接埠類型**頁面上，輸入下列資訊，然後按**下一步**才能繼續。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-135">On the **Select a Port Type** page, enter the following information, and then click **Next** to continue.</span></span>  
  
    |<span data-ttu-id="ed2f3-136">使用</span><span class="sxs-lookup"><span data-stu-id="ed2f3-136">Use this</span></span>|<span data-ttu-id="ed2f3-137">動作</span><span class="sxs-lookup"><span data-stu-id="ed2f3-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ed2f3-138">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-138">**Port Type Name**</span></span>|<span data-ttu-id="ed2f3-139">型別**SOAPReceivePortType**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-139">Type **SOAPReceivePortType**.</span></span>|  
    |<span data-ttu-id="ed2f3-140">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-140">**Communication Pattern**</span></span>|<span data-ttu-id="ed2f3-141">選取**單向**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-141">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="ed2f3-142">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-142">**Access Restrictions**</span></span>|<span data-ttu-id="ed2f3-143">選取**公用-沒有限制**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-143">Select **Public - no limit**.</span></span>|  
  
5.  <span data-ttu-id="ed2f3-144">在**連接埠繫結**頁面上，按一下**下一步**接受預設值。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-144">On the **Port Binding** page, click **Next** to accept the default values.</span></span>  
  
6.  <span data-ttu-id="ed2f3-145">在**完成連接埠精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-145">On the **Completing the Port Wizard** page, click **Finish**.</span></span>  
  
7.  <span data-ttu-id="ed2f3-146">拖曳**連接埠**圖形從工具箱拖曳至 [設計] 檢視介面，右邊的連接埠介面，然後將圖形放，讓它與水平對齊**DoorbellSend**圖形。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-146">Drag the **Port** shape from the Toolbox to the Port Surface on the right side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellSend** shape.</span></span>  
  
8.  <span data-ttu-id="ed2f3-147">使用**連接埠組態精靈**如同在步驟 2 到 7，建立額外的傳送埠，使用下列參數：</span><span class="sxs-lookup"><span data-stu-id="ed2f3-147">Using the **Port Configuration Wizard** as you did in steps 2 through 7, create an additional send port using the following parameters:</span></span>  
  
    |<span data-ttu-id="ed2f3-148">屬性</span><span class="sxs-lookup"><span data-stu-id="ed2f3-148">Property</span></span>|<span data-ttu-id="ed2f3-149">參數</span><span class="sxs-lookup"><span data-stu-id="ed2f3-149">Parameter</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="ed2f3-150">**連接埠的屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-150">**Port Properties Name**</span></span>|<span data-ttu-id="ed2f3-151">MLLPSendPort</span><span class="sxs-lookup"><span data-stu-id="ed2f3-151">MLLPSendPort</span></span>|  
    |<span data-ttu-id="ed2f3-152">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-152">**Port Type Name**</span></span>|<span data-ttu-id="ed2f3-153">MLLPSendPortType</span><span class="sxs-lookup"><span data-stu-id="ed2f3-153">MLLPSendPortType</span></span>|  
    |<span data-ttu-id="ed2f3-154">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-154">**Communication Pattern**</span></span>|<span data-ttu-id="ed2f3-155">單向</span><span class="sxs-lookup"><span data-stu-id="ed2f3-155">One-Way</span></span>|  
    |<span data-ttu-id="ed2f3-156">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-156">**Access Restrictions**</span></span>|<span data-ttu-id="ed2f3-157">公用 - 沒有限制</span><span class="sxs-lookup"><span data-stu-id="ed2f3-157">Public - no limit</span></span>|  
    |<span data-ttu-id="ed2f3-158">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-158">**Port Binding**</span></span>|<span data-ttu-id="ed2f3-159">稍後指定</span><span class="sxs-lookup"><span data-stu-id="ed2f3-159">Specify Later</span></span>|  
    |<span data-ttu-id="ed2f3-160">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="ed2f3-160">**Port direction of communication**</span></span>|<span data-ttu-id="ed2f3-161">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-161">I'll always be sending messages on this port.</span></span>|  
  
9. <span data-ttu-id="ed2f3-162">在**協調流程檢視**視窗中，與**類型**，**連接埠類型**，和**SOAPReceivePortType**節點展開，展開  **Operation_1**，然後按一下 **要求**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-162">In the **Orchestration View** window, with the **Types**, **Ports Types**, and **SOAPReceivePortType** nodes expanded, expand **Operation_1**, and then click **Request**.</span></span>  
  
10. <span data-ttu-id="ed2f3-163">在**屬性**視窗中的，在下拉式清單中**訊息類型**，依序展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-163">In the **Properties** window, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.</span></span>  
  
11. <span data-ttu-id="ed2f3-164">在**協調流程檢視**視窗中，展開  **MLLPSendPortType**，依序展開**Operation_1**，然後按一下**要求**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-164">In the **Orchestration View** window, expand **MLLPSendPortType**, expand **Operation_1**, and then click **Request**.</span></span>  
  
12. <span data-ttu-id="ed2f3-165">在**屬性**視窗中的，在下拉式清單中**訊息類型**，依序展開**多部分訊息類型**，然後按一下  **BTAHL7_Project.DoorbellFinalMessageType**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-165">In the **Properties** window, in the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.</span></span>  
  
13. <span data-ttu-id="ed2f3-166">在**名稱**欄位中，輸入**回應**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-166">In the **Name** field, type **Response**, then press **Enter**.</span></span>  
  
14. <span data-ttu-id="ed2f3-167">協調流程設計檢視介面上，按一下  **DoorbellReceive**動作圖形。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-167">On the orchestration Design view surface, click the **DoorbellReceive** action shape.</span></span>  
  
15. <span data-ttu-id="ed2f3-168">在**屬性**視窗中的，在下拉式清單中**訊息**，選取**DoorbellInputMessage**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-168">In the **Properties** window, in the drop-down list for **Message**, select **DoorbellInputMessage**.</span></span>  
  
16. <span data-ttu-id="ed2f3-169">協調流程設計檢視介面上，按一下  **DoorbellSend**圖形。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-169">On the orchestration Design view surface, click the **DoorbellSend** shape.</span></span>  
  
17. <span data-ttu-id="ed2f3-170">在**屬性**視窗中的，在下拉式清單中**訊息**，選取**DoorbellFinalMessage**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-170">In the **Properties** window, in the drop-down list for **Message**, select **DoorbellFinalMessage**.</span></span>  
  
18. <span data-ttu-id="ed2f3-171">按一下中的綠色控點**SOAPReceivePort**並將它拖曳至的綠色控點**DoorbellReceive**接收圖形連接**SOAPReceivePort** 至**DoorbellReceive**接收圖形。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-171">Click the green handle in the **SOAPReceivePort** and drag it to the green handle on the **DoorbellReceive** receive shape to connect the **SOAPReceivePort** to the **DoorbellReceive** receive shape.</span></span>  
  
19. <span data-ttu-id="ed2f3-172">按一下中的綠色控點**DoorbellSend**圖形，並將它拖曳至的綠色控點**MLLPSendPort**連接的連接埠**DoorbellSend** 到傳送圖形**MLLPSendPort**連接埠。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-172">Click the green handle in the **DoorbellSend** shape and drag it to the green handle on the **MLLPSendPort** port to connect the **DoorbellSend** send shape to the **MLLPSendPort** port.</span></span>  
  
20. <span data-ttu-id="ed2f3-173">按一下**方案總管 中**在協調流程檢視 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-173">Click the **Solution Explorer** tab under the Orchestration View.</span></span>  
  
21. <span data-ttu-id="ed2f3-174">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-174">In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Build**.</span></span> <span data-ttu-id="ed2f3-175">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-175">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed2f3-176">如果不成功的訊息出現，請對方案進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-176">If no success message appears, troubleshoot the solution.</span></span>  
  
22. <span data-ttu-id="ed2f3-177">以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**部署**部署 BTAHL7 專案。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-177">Right-click **BTAHL7 Project**, and click **Deploy** to deploy the BTAHL7 project.</span></span>  
  
 <span data-ttu-id="ed2f3-178">若要繼續[步驟 14： 發佈為 Web 服務協調流程](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ed2f3-178">Proceed to [Step 14: Publish the Orchestration as a Web Service](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2f3-179">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed2f3-179">See Also</span></span>  
 [<span data-ttu-id="ed2f3-180">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="ed2f3-180">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)