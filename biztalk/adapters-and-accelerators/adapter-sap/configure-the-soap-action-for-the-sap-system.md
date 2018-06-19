---
title: 在 BizTalk 中設定 SAP 系統的 SOAP 動作 |Microsoft 文件
description: 在運算式圖形中，輸入 SOAP 動作，或使用 Wcf-custom 或 WCF SAP 配接器在 BizTalk 配接器組件 (BAP)
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
ms.openlocfilehash: 36a474d53d3fcaf61668800094a1d98d0e061aa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217534"
---
# <a name="configure-the-soap-action-for-the-sap-system"></a><span data-ttu-id="0a044-103">設定 SAP 系統的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="0a044-103">Configure the SOAP action for the SAP system</span></span>
<span data-ttu-id="0a044-104">若要執行使用 WCF 為基礎之 SAP 系統上的任何作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，配接器使用者必須指定 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-104">To perform any operation on the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], adapter users must specify a SOAP action.</span></span> <span data-ttu-id="0a044-105">SOAP 動作與外界溝通的配接器應該執行哪些動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="0a044-106">您可以指定在設計階段或執行階段的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-106">You can specify the SOAP action either at design time or at run time.</span></span> <span data-ttu-id="0a044-107">不過，如果您指定的 SOAP 動作這兩個設計階段和執行階段，則會覆寫您在設計階段指定的動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-107">However, if you specify the SOAP action both at design time and run time, the action you specified at design time will be overridden.</span></span>  
  
 <span data-ttu-id="0a044-108">如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="0a044-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>
  
## <a name="enter-soap-action-at-design-time"></a><span data-ttu-id="0a044-109">輸入在設計階段的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="0a044-109">Enter SOAP Action at Design Time</span></span>  
 <span data-ttu-id="0a044-110">設計階段，您必須指定的 SOAP 動作協調流程包括 「 運算式 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="0a044-110">For design time, you must specify the SOAP action as part of orchestration by including an expression shape.</span></span>  
  
 
1.  <span data-ttu-id="0a044-111">在 BizTalk 協調流程中，包括將它從 「 運算式 」 圖形**BizTalk 協調流程**工具箱。</span><span class="sxs-lookup"><span data-stu-id="0a044-111">In the BizTalk orchestration, include an Expression shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="0a044-112">按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="0a044-112">Double-click the **Expression** shape to open the BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="0a044-113">在 BizTalk 運算式編輯器 」 中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-113">Specify the action in the BizTalk Expression Editor.</span></span> <span data-ttu-id="0a044-114">例如：</span><span class="sxs-lookup"><span data-stu-id="0a044-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET"  
    ```  
  
     <span data-ttu-id="0a044-115">如需有關**運算式**圖形和 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0a044-115">For more information about the **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>
  
## <a name="enter-soap-action-at-run-time"></a><span data-ttu-id="0a044-116">輸入在執行階段的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="0a044-116">Enter SOAP Action at Run Time</span></span>  
 <span data-ttu-id="0a044-117">執行階段，您可以指定的 SOAP 動作 Wcf-custom 或 WCF SAP 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="0a044-117">For run time, you can specify the SOAP action as part of the WCF-Custom or WCF-SAP port configuration.</span></span>  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="0a044-118">輸入 WCF 自訂連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="0a044-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="0a044-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a044-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="0a044-120">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0a044-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="0a044-121">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0a044-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="0a044-122">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0a044-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="0a044-123">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a044-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="0a044-124">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="0a044-125">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="0a044-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="0a044-126">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="0a044-126">**By using the single action format**.</span></span> <span data-ttu-id="0a044-127">如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="0a044-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="0a044-128">例如：</span><span class="sxs-lookup"><span data-stu-id="0a044-128">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    -   <span data-ttu-id="0a044-129">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="0a044-129">**By using the action mapping format**.</span></span> <span data-ttu-id="0a044-130">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="0a044-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="0a044-131">比方說，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要叫用 RFC_CUSTOMER_GET RFC） Op1 和 Op2 （要叫用 BAPI_SALESORDER_CREATEFROMDAT2 BAPI），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="0a044-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="0a044-132">此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="0a044-132">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="0a044-133">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="0a044-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="0a044-134">如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="0a044-134">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>
  
### <a name="enter-a-soap-action-for-the-wcf-sap-port"></a><span data-ttu-id="0a044-135">輸入 WCF SAP 連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="0a044-135">Enter a SOAP action for the WCF-SAP port</span></span>  
  
1.  <span data-ttu-id="0a044-136">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a044-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="0a044-137">加入 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a044-137">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0a044-138">如需指示，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="0a044-138">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="0a044-139">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0a044-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="0a044-140">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0a044-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="0a044-141">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您之前，加入 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0a044-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="0a044-142">在 傳輸屬性對話方塊中，按一下 **一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a044-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="0a044-143">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="0a044-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="0a044-144">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="0a044-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="0a044-145">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="0a044-145">**By using the single action format**.</span></span> <span data-ttu-id="0a044-146">如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="0a044-146">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="0a044-147">例如：</span><span class="sxs-lookup"><span data-stu-id="0a044-147">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    -   <span data-ttu-id="0a044-148">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="0a044-148">**By using the action mapping format**.</span></span> <span data-ttu-id="0a044-149">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="0a044-149">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="0a044-150">比方說，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要叫用 RFC_CUSTOMER_GET RFC） Op1 和 Op2 （要叫用 BAPI_SALESORDER_CREATEFROMDAT2 BAPI），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="0a044-150">For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="0a044-151">此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="0a044-151">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="0a044-152">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="0a044-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="0a044-153">如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="0a044-153">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a044-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a044-154">See Also</span></span>  
[<span data-ttu-id="0a044-155">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="0a044-155">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)