---
title: "在 BizTalk 中設定 Siebel 配接器的 SOAP 動作 |Microsoft 文件"
description: "在 Visual Studio 中，輸入 SOAP 動作，或使用 Wcf-custom 或 Wcf-siebel 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f22a4691-0355-4f08-a14e-e90a3c987ac0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b851aa0b26d80a43f5a839232298ace5507f471b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-siebel"></a><span data-ttu-id="8c2c2-103">設定 Siebel 的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="8c2c2-103">Configure the SOAP action for Siebel</span></span>
<span data-ttu-id="8c2c2-104">若要執行使用 WCF 型 Siebel 系統中的任何作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，配接器使用者必須指定 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-104">To perform any operation on the Siebel system using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], adapter users must specify a SOAP action.</span></span> <span data-ttu-id="8c2c2-105">SOAP 動作與外界溝通的配接器應該執行哪些動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="8c2c2-106">您可以指定在設計階段或執行階段的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-106">You can specify the SOAP action either at design time or at run time.</span></span> <span data-ttu-id="8c2c2-107">不過，如果您指定的 SOAP 動作這兩個設計階段和執行階段，則會覆寫您在設計階段指定的動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-107">However, if you specify the SOAP action both at design time and run time, the action you specified at design time will be overridden.</span></span>  
  
 <span data-ttu-id="8c2c2-108">如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>
  
## <a name="enter-soap-action-at-design-time"></a><span data-ttu-id="8c2c2-109">輸入在設計階段的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="8c2c2-109">Enter SOAP Action at Design Time</span></span>  
 <span data-ttu-id="8c2c2-110">設計階段，您必須指定的 SOAP 動作協調流程包括 「 運算式 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-110">For design time, you must specify the SOAP action as part of orchestration by including an expression shape.</span></span>  
  
1.  <span data-ttu-id="8c2c2-111">在 BizTalk 協調流程 「 運算式 」 圖形，藉以加入將它從**BizTalk 協調流程**工具箱。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-111">In the BizTalk orchestration include an Expression shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="8c2c2-112">按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-112">Double-click the **Expression** shape to open the BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="8c2c2-113">在 BizTalk 運算式編輯器 」 中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-113">Specify the action in the BizTalk Expression Editor.</span></span> <span data-ttu-id="8c2c2-114">例如：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"  
    ```  
  
     <span data-ttu-id="8c2c2-115">如需有關**運算式**圖形和 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-115">For more information about **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>  
  
## <a name="enter-soap-action-at-run-time"></a><span data-ttu-id="8c2c2-116">在執行階段輸入 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="8c2c2-116">Enter SOAP Action at run time</span></span>  
 <span data-ttu-id="8c2c2-117">執行階段，您必須指定 Wcf-custom 或 Wcf-siebel 連接埠屬性 對話方塊的一部分的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-117">For run time, you must specify the SOAP action as part of the WCF-Custom or WCF-Siebel port properties dialog box.</span></span>  
  
#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="8c2c2-118">輸入 WCF 自訂連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="8c2c2-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="8c2c2-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8c2c2-120">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="8c2c2-121">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="8c2c2-122">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="8c2c2-123">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="8c2c2-124">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="8c2c2-125">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="8c2c2-126">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-126">**By using the single action format**.</span></span> <span data-ttu-id="8c2c2-127">如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="8c2c2-128">例如：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-128">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    -   <span data-ttu-id="8c2c2-129">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-129">**By using the action mapping format**.</span></span> <span data-ttu-id="8c2c2-130">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="8c2c2-131">例如，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要執行插入作業帳戶商務元件上的） Op1 和 Op2 （於執行帳戶商務元件上的更新作業），SOAP 動作可以指定下列方式：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to perform an Insert operation on Account business component) and Op2 (to perform an Update operation on Account business component), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="8c2c2-132">此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-132">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="8c2c2-133">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="8c2c2-134">如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-134">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).</span></span>
  
#### <a name="enter-a-soap-action-for-the-wcf-siebel-port"></a><span data-ttu-id="8c2c2-135">輸入 Wcf-siebel 連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="8c2c2-135">Enter a SOAP action for the WCF-Siebel port</span></span>  
  
1.  <span data-ttu-id="8c2c2-136">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8c2c2-137">新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-137">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8c2c2-138">如需指示，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-138">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="8c2c2-139">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="8c2c2-140">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="8c2c2-141">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取 Wcf-siebel 配接器，您將較舊版本，然後再按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-Siebel adapter you add earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="8c2c2-142">在 連接埠屬性 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-142">In the port properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="8c2c2-143">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="8c2c2-144">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="8c2c2-145">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-145">**By using the single action format**.</span></span> <span data-ttu-id="8c2c2-146">如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-146">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="8c2c2-147">例如：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-147">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    -   <span data-ttu-id="8c2c2-148">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-148">**By using the action mapping format**.</span></span> <span data-ttu-id="8c2c2-149">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-149">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="8c2c2-150">例如，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要執行插入作業帳戶商務元件上的） Op1 和 Op2 （於執行帳戶商務元件上的更新作業），SOAP 動作可以指定下列方式：</span><span class="sxs-lookup"><span data-stu-id="8c2c2-150">For example, if a single WCF-Custom port sends and receives messages for Op1 (to perform an Insert operation on Account business component) and Op2 (to perform an Update operation on Account business component), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="8c2c2-151">此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-151">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="8c2c2-152">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="8c2c2-153">如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="8c2c2-153">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8c2c2-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c2c2-154">See Also</span></span>  
[<span data-ttu-id="8c2c2-155">若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="8c2c2-155">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)