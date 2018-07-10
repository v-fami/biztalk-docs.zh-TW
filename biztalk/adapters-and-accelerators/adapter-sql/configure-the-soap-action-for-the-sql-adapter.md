---
title: 在 BizTalk 設定 SQL 配接器的 SOAP 動作 |Microsoft Docs
description: 在 Visual Studio 中，輸入 SOAP 動作，或使用 BizTalk 配接器組件 (BAP) 中的 WCF 自訂] 或 [WCF-SQL 配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acd7f60b-c27f-4988-a67c-e56ef8d38f66
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a927740ba04a0fd1b080e73ef60892ffdc9bf385
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980519"
---
# <a name="configure-the-soap-action-for-the-sql-adapter"></a><span data-ttu-id="ac212-103">設定 SQL 配接器的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="ac212-103">Configure the SOAP action for the SQL adapter</span></span>
<span data-ttu-id="ac212-104">若要使用以 WCF 為基礎的 SQL Server 上執行任何作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須指定 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="ac212-104">To perform any operation on SQL Server using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must specify a SOAP action.</span></span> <span data-ttu-id="ac212-105">SOAP 動作與配接器應該執行什麼動作。</span><span class="sxs-lookup"><span data-stu-id="ac212-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="ac212-106">您可以從指定的 SOAP 動作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac212-106">You can specify the SOAP action either from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ac212-107">不過，如果您指定來自兩個位置的 SOAP 動作，您指定動作從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]將會覆寫。</span><span class="sxs-lookup"><span data-stu-id="ac212-107">However, if you specify the SOAP action from both locations, the action you specified from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] will be overridden.</span></span>  
  
 <span data-ttu-id="ac212-108">如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="ac212-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>
  
## <a name="enter-the-soap-action-in-visual-studio"></a><span data-ttu-id="ac212-109">在 Visual Studio 中，輸入 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="ac212-109">Enter the SOAP action in Visual Studio</span></span>  
 <span data-ttu-id="ac212-110">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您也必須使用協調流程指定的 SOAP 動作**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="ac212-110">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the SOAP action as part of the orchestration by using an **Expression** shape.</span></span>  
  
1.  <span data-ttu-id="ac212-111">在 BizTalk 協調流程，包括**運算式**圖形，方法是將它從**BizTalk 協調流程**工具箱。</span><span class="sxs-lookup"><span data-stu-id="ac212-111">In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="ac212-112">按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="ac212-112">Double-click the **Expression** shape to open BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="ac212-113">在 [BizTalk 運算式編輯器] 中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="ac212-113">Specify the action in BizTalk Expression Editor.</span></span> <span data-ttu-id="ac212-114">例如：</span><span class="sxs-lookup"><span data-stu-id="ac212-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="TableOp/Insert/dbo/Employee"  
    ```  
  
     <span data-ttu-id="ac212-115">如需詳細資訊**運算式**形狀 」 和 「 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ac212-115">For more information about the **Expression** shape and BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>
  
## <a name="enter-the-soap-action-from-the-biztalk-server-administration-console"></a><span data-ttu-id="ac212-116">從 BizTalk Server 管理主控台中輸入的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="ac212-116">Enter the SOAP action from the BizTalk Server Administration console</span></span>  
 <span data-ttu-id="ac212-117">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定的 SOAP 動作為 [Wcf-custom] 或 [WCF SQL 連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="ac212-117">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can specify the SOAP action as part of the WCF-Custom or WCF-SQL port configuration.</span></span>  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="ac212-118">輸入 WCF 自訂連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="ac212-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1. <span data-ttu-id="ac212-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac212-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="ac212-120">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="ac212-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="ac212-121">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ac212-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3. <span data-ttu-id="ac212-122">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ac212-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="ac212-123">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac212-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5. <span data-ttu-id="ac212-124">在 **動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="ac212-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="ac212-125">您可以透過下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="ac212-125">You can specify the action in the following ways:</span></span>  
  
   -   <span data-ttu-id="ac212-126">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="ac212-126">**By using the single action format**.</span></span> <span data-ttu-id="ac212-127">如果 「 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="ac212-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="ac212-128">例如：</span><span class="sxs-lookup"><span data-stu-id="ac212-128">For example:</span></span>  
  
       ```  
       TableOp/Insert/dbo/Employee  
       ```  
  
   -   <span data-ttu-id="ac212-129">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="ac212-129">**By using the action mapping format**.</span></span> <span data-ttu-id="ac212-130">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="ac212-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="ac212-131">比方說，如果單一 WCF 自訂連接埠傳送或接收訊息 （若要 Employee 資料表中插入記錄） Op1 和 Op2 （若要更新 Employee 資料表中的記錄），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="ac212-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the Employee table) and Op2 (to update records in the Employee table), the SOAP action can be specified in the following manner:</span></span>  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
         <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
       </BtsActionMapping>  
       ```  
  
        <span data-ttu-id="ac212-132">動作對應方法，提供更大的彈性以指定的一組動作，並因此啟用屬於不同的動作類型的流量通過相同的連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac212-132">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
        <span data-ttu-id="ac212-133">SOAP 動作的格式是針對每個作業不同。</span><span class="sxs-lookup"><span data-stu-id="ac212-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="ac212-134">如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ac212-134">For more information about the action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>
  
### <a name="enter-a-soap-action-for-the-wcf-sql-port"></a><span data-ttu-id="ac212-135">輸入 WCF SQL 連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="ac212-135">Enter a SOAP action for the WCF-SQL port</span></span>  
  
1. <span data-ttu-id="ac212-136">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac212-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="ac212-137">新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac212-137">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ac212-138">如需相關指示，請參閱 <<c0> [ 將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="ac212-138">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="ac212-139">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="ac212-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="ac212-140">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ac212-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4. <span data-ttu-id="ac212-141">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 WCF-SQL 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ac212-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
5. <span data-ttu-id="ac212-142">在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac212-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6. <span data-ttu-id="ac212-143">在 **動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="ac212-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="ac212-144">您可以透過下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="ac212-144">You can specify the action in the following ways:</span></span>  
  
   -   <span data-ttu-id="ac212-145">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="ac212-145">**By using the single action format**.</span></span> <span data-ttu-id="ac212-146">如果 WCF SQL 連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="ac212-146">Use this format if the WCF-SQL port sends and receive messages for a single operation.</span></span> <span data-ttu-id="ac212-147">例如：</span><span class="sxs-lookup"><span data-stu-id="ac212-147">For example:</span></span>  
  
       ```  
       TableOp/Insert/dbo/Employee  
       ```  
  
   -   <span data-ttu-id="ac212-148">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="ac212-148">**By using the action mapping format**.</span></span> <span data-ttu-id="ac212-149">如果單一 WCF SQL 連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="ac212-149">Use this format if a single WCF-SQL port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="ac212-150">比方說，如果單一 WCF SQL 連接埠傳送或接收訊息 （若要 Employee 資料表中插入記錄） Op1 和 Op2 （若要更新 Employee 資料表中的記錄），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="ac212-150">For example, if a single WCF-SQL port sends and receives messages for Op1 (to insert records in the Employee table) and Op2 (to update records in the Employee table), the SOAP action can be specified in the following manner:</span></span>  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
         <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
       </BtsActionMapping>  
       ```  
  
        <span data-ttu-id="ac212-151">動作對應方法，提供更大的彈性以指定的一組動作，並因此啟用屬於不同的動作類型的流量通過相同的連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac212-151">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
        <span data-ttu-id="ac212-152">SOAP 動作的格式是針對每個作業不同。</span><span class="sxs-lookup"><span data-stu-id="ac212-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="ac212-153">如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ac212-153">For more information about the action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ac212-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac212-154">See Also</span></span>  
[<span data-ttu-id="ac212-155">若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="ac212-155">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)