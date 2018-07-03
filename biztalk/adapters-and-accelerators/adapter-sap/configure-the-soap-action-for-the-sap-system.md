---
title: 在 BizTalk 設定 SAP 系統的 SOAP 動作 |Microsoft Docs
description: 在運算式圖形中，輸入 SOAP 動作，或使用 BizTalk 配接器組件 (BAP) 中的 WCF 自訂 」 或 「 WCF SAP 配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76084bc5-7a10-4c4c-be22-bee83779a011
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 963c4b3c8d8287b430774813487e924837880a01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004871"
---
# <a name="configure-the-soap-action-for-the-sap-system"></a><span data-ttu-id="37946-103">設定 SAP 系統的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="37946-103">Configure the SOAP action for the SAP system</span></span>
<span data-ttu-id="37946-104">若要使用以 WCF 為基礎的 SAP 系統上執行任何作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，配接器使用者必須指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="37946-104">To perform any operation on the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], adapter users must specify a SOAP action.</span></span> <span data-ttu-id="37946-105">SOAP 動作與配接器應該執行什麼動作。</span><span class="sxs-lookup"><span data-stu-id="37946-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="37946-106">您可以指定在設計階段或在執行階段的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="37946-106">You can specify the SOAP action either at design time or at run time.</span></span> <span data-ttu-id="37946-107">不過，如果您指定的 SOAP 動作這兩個設計階段，並執行階段，則會覆寫您在設計階段指定的動作。</span><span class="sxs-lookup"><span data-stu-id="37946-107">However, if you specify the SOAP action both at design time and run time, the action you specified at design time will be overridden.</span></span>  
  
 <span data-ttu-id="37946-108">如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="37946-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>
  
## <a name="enter-soap-action-at-design-time"></a><span data-ttu-id="37946-109">輸入在設計階段的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="37946-109">Enter SOAP Action at Design Time</span></span>  
 <span data-ttu-id="37946-110">設計階段，您必須指定的 SOAP 動作協調流程包括 「 運算式 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="37946-110">For design time, you must specify the SOAP action as part of orchestration by including an expression shape.</span></span>  
  
 
1.  <span data-ttu-id="37946-111">在 BizTalk 協調流程，請藉由將它從包含 「 運算式 」 圖形**BizTalk 協調流程**工具箱。</span><span class="sxs-lookup"><span data-stu-id="37946-111">In the BizTalk orchestration, include an Expression shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="37946-112">按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="37946-112">Double-click the **Expression** shape to open the BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="37946-113">在 BizTalk 運算式編輯器 」 中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="37946-113">Specify the action in the BizTalk Expression Editor.</span></span> <span data-ttu-id="37946-114">例如：</span><span class="sxs-lookup"><span data-stu-id="37946-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET"  
    ```  
  
     <span data-ttu-id="37946-115">如需詳細資訊**運算式**圖形和 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="37946-115">For more information about the **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>
  
## <a name="enter-soap-action-at-run-time"></a><span data-ttu-id="37946-116">輸入 SOAP 動作，在執行階段</span><span class="sxs-lookup"><span data-stu-id="37946-116">Enter SOAP Action at Run Time</span></span>  
 <span data-ttu-id="37946-117">執行階段，您可以指定的 SOAP 動作做為 WCF 自訂 」 或 「 WCF SAP 連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="37946-117">For run time, you can specify the SOAP action as part of the WCF-Custom or WCF-SAP port configuration.</span></span>  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="37946-118">輸入 WCF 自訂連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="37946-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1. <span data-ttu-id="37946-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="37946-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="37946-120">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="37946-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="37946-121">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="37946-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3. <span data-ttu-id="37946-122">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="37946-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="37946-123">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="37946-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5. <span data-ttu-id="37946-124">在 **動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="37946-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="37946-125">您可以透過下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="37946-125">You can specify the action in the following ways:</span></span>  
  
   -   <span data-ttu-id="37946-126">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="37946-126">**By using the single action format**.</span></span> <span data-ttu-id="37946-127">如果 「 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="37946-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="37946-128">例如：</span><span class="sxs-lookup"><span data-stu-id="37946-128">For example:</span></span>  
  
       ```  
       http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
       ```  
  
   -   <span data-ttu-id="37946-129">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="37946-129">**By using the action mapping format**.</span></span> <span data-ttu-id="37946-130">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="37946-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="37946-131">比方說，如果單一 WCF 自訂連接埠傳送或接收訊息 （若要叫用 RFC_CUSTOMER_GET RFC） Op1 和 Op2 （若要叫用 BAPI_SALESORDER_CREATEFROMDAT2 BAPI），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="37946-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:</span></span>  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
       </BtsActionMapping>  
       ```  
  
        <span data-ttu-id="37946-132">此方法提供更大的彈性以指定的一組動作，並因此啟用訊息屬於不同的動作類型的流量通過相同的連接埠。</span><span class="sxs-lookup"><span data-stu-id="37946-132">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
        <span data-ttu-id="37946-133">SOAP 動作的格式是針對每個作業不同。</span><span class="sxs-lookup"><span data-stu-id="37946-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="37946-134">如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="37946-134">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>
  
### <a name="enter-a-soap-action-for-the-wcf-sap-port"></a><span data-ttu-id="37946-135">輸入 WCF SAP 連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="37946-135">Enter a SOAP action for the WCF-SAP port</span></span>  
  
1. <span data-ttu-id="37946-136">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="37946-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="37946-137">新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="37946-137">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="37946-138">如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="37946-138">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="37946-139">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="37946-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="37946-140">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="37946-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4. <span data-ttu-id="37946-141">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="37946-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
5. <span data-ttu-id="37946-142">在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="37946-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6. <span data-ttu-id="37946-143">在 **動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="37946-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="37946-144">您可以透過下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="37946-144">You can specify the action in the following ways:</span></span>  
  
   -   <span data-ttu-id="37946-145">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="37946-145">**By using the single action format**.</span></span> <span data-ttu-id="37946-146">如果 「 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="37946-146">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="37946-147">例如：</span><span class="sxs-lookup"><span data-stu-id="37946-147">For example:</span></span>  
  
       ```  
       http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
       ```  
  
   -   <span data-ttu-id="37946-148">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="37946-148">**By using the action mapping format**.</span></span> <span data-ttu-id="37946-149">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="37946-149">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="37946-150">比方說，如果單一 WCF 自訂連接埠傳送或接收訊息 （若要叫用 RFC_CUSTOMER_GET RFC） Op1 和 Op2 （若要叫用 BAPI_SALESORDER_CREATEFROMDAT2 BAPI），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="37946-150">For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:</span></span>  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
       </BtsActionMapping>  
       ```  
  
        <span data-ttu-id="37946-151">此方法提供更大的彈性以指定的一組動作，並因此啟用訊息屬於不同的動作類型的流量通過相同的連接埠。</span><span class="sxs-lookup"><span data-stu-id="37946-151">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
        <span data-ttu-id="37946-152">SOAP 動作的格式是針對每個作業不同。</span><span class="sxs-lookup"><span data-stu-id="37946-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="37946-153">如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="37946-153">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="37946-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37946-154">See Also</span></span>  
[<span data-ttu-id="37946-155">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="37946-155">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)