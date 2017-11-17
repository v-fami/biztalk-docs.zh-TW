---
title: "在 BizTalk Server 中設定 Oracle E-business Suite 的 SOAP 動作 |Microsoft 文件"
description: "在 Visual Studio 中，輸入 SOAP 動作，或使用 Wcf-custom 或 Wcf-oracleebs 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca799d96-66e4-4d4e-a632-cb5505e999b4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29cb5ce17f0a80e42ceae908639bed48e99e3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-oracle-e-business-suite"></a><span data-ttu-id="31c4d-103">設定 for Oracle E-business Suite 的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="31c4d-103">Configure the SOAP action for Oracle E-Business Suite</span></span>
<span data-ttu-id="31c4d-104">若要執行使用 WCF 型 Oracle E-business Suite 中的任何作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須指定 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="31c4d-104">To perform any operation on Oracle E-Business Suite using the WCF-based [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must specify a SOAP action.</span></span> <span data-ttu-id="31c4d-105">SOAP 動作與外界溝通的配接器應該執行哪些動作。</span><span class="sxs-lookup"><span data-stu-id="31c4d-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="31c4d-106">您可以從指定的 SOAP 動作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="31c4d-106">You can specify the SOAP action either from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="31c4d-107">不過，如果您指定的 SOAP 動作，從兩個位置，您指定動作從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]會覆寫。</span><span class="sxs-lookup"><span data-stu-id="31c4d-107">However, if you specify the SOAP action from both locations, the action you specified from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] is overridden.</span></span>  
  
 <span data-ttu-id="31c4d-108">如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="31c4d-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>  
  
## <a name="enter-soap-action-from-visual-studio"></a><span data-ttu-id="31c4d-109">從 Visual Studio 輸入 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="31c4d-109">Enter SOAP Action from Visual Studio</span></span>  
 <span data-ttu-id="31c4d-110">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定的 SOAP 動作協調流程的一部分使用**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="31c4d-110">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the SOAP action as part of the orchestration by using an **Expression** shape.</span></span>  
  
1.  <span data-ttu-id="31c4d-111">在 BizTalk 協調流程中，包括**運算式**圖形，方法是將它從**BizTalk 協調流程**工具箱。</span><span class="sxs-lookup"><span data-stu-id="31c4d-111">In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="31c4d-112">按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="31c4d-112">Double-click the **Expression** shape to open BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="31c4d-113">在 [BizTalk 運算式編輯器] 中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="31c4d-113">Specify the action in BizTalk Expression Editor.</span></span> <span data-ttu-id="31c4d-114">例如：</span><span class="sxs-lookup"><span data-stu-id="31c4d-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY"  
    ```  
  
     <span data-ttu-id="31c4d-115">如需有關**運算式**形狀 」 和 「 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="31c4d-115">For more information about the **Expression** shape and BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>  
  
## <a name="enter-soap-action-from-biztalk-server-administration"></a><span data-ttu-id="31c4d-116">輸入 SOAP 動作，從 BizTalk Server 管理</span><span class="sxs-lookup"><span data-stu-id="31c4d-116">Enter SOAP Action from BizTalk Server Administration</span></span>  
 <span data-ttu-id="31c4d-117">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定的 SOAP 動作 Wcf-custom 或 Wcf-oracleebs 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="31c4d-117">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the SOAP action as part of the WCF-Custom or WCF-OracleEBS port configuration.</span></span>  
  
#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="31c4d-118">輸入 WCF 自訂連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="31c4d-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="31c4d-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="31c4d-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="31c4d-120">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="31c4d-121">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="31c4d-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="31c4d-122">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="31c4d-123">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="31c4d-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="31c4d-124">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="31c4d-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="31c4d-125">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="31c4d-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="31c4d-126">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-126">**By using the single action format**.</span></span> <span data-ttu-id="31c4d-127">如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="31c4d-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="31c4d-128">例如：</span><span class="sxs-lookup"><span data-stu-id="31c4d-128">For example:</span></span>  
  
        ```  
        InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY  
        ```  
  
    -   <span data-ttu-id="31c4d-129">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-129">**By using the action mapping format**.</span></span> <span data-ttu-id="31c4d-130">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="31c4d-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="31c4d-131">比方說，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要將記錄插入 GL_ALLOC_HISTORY 資料表中） Op1 和 Op2 （若要更新 GL_ALLOC_HISTORY 資料表中的記錄），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="31c4d-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the GL_ALLOC_HISTORY table) and Op2 (to update records in the GL_ALLOC_HISTORY table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY" />  
          <Operation Name="Op2" Action="InterfaceTables/Update/SQLGL/GL/GL_ALLOC_HISTORY " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="31c4d-132">動作對應方法，提供更大彈性，以指定的一組動作，並因此啟用屬於流經的相同連接埠的不同動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="31c4d-132">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="31c4d-133">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="31c4d-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="31c4d-134">如需每個作業的動作格式的詳細資訊，請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="31c4d-134">For more information about the action format for each operation, see [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>
  
#### <a name="enter-a-soap-action-for-the-wcf-oracleebs-port"></a><span data-ttu-id="31c4d-135">輸入 Wcf-oracleebs 連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="31c4d-135">Enter a SOAP action for the WCF-OracleEBS port</span></span>  
  
1.  <span data-ttu-id="31c4d-136">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="31c4d-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="31c4d-137">新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="31c4d-137">Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="31c4d-138">如需指示，請參閱[Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="31c4d-138">For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="31c4d-139">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="31c4d-140">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="31c4d-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="31c4d-141">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取 Wcf-oracleebs 配接器，您將較舊版本，然後再按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleEBS adapter you add earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="31c4d-142">在 傳輸屬性對話方塊中，按一下 **一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="31c4d-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="31c4d-143">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="31c4d-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="31c4d-144">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="31c4d-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="31c4d-145">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-145">**By using the single action format**.</span></span> <span data-ttu-id="31c4d-146">如果 Wcf-oracleebs 連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="31c4d-146">Use this format if the WCF-OracleEBS port sends and receive messages for a single operation.</span></span> <span data-ttu-id="31c4d-147">例如：</span><span class="sxs-lookup"><span data-stu-id="31c4d-147">For example:</span></span>  
  
        ```  
        InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY  
        ```  
  
    -   <span data-ttu-id="31c4d-148">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="31c4d-148">**By using the action mapping format**.</span></span> <span data-ttu-id="31c4d-149">如果單一 Wcf-oracleebs 連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="31c4d-149">Use this format if a single WCF-OracleEBS port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="31c4d-150">比方說，如果單一 Wcf-oracleebs 連接埠傳送與接收訊息 （若要將記錄插入 GL_ALLOC_HISTORY 資料表中） Op1 和 Op2 （若要更新 GL_ALLOC_HISTORY 資料表中的記錄），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="31c4d-150">For example, if a single WCF-OracleEBS port sends and receives messages for Op1 (to insert records in the GL_ALLOC_HISTORY table) and Op2 (to update records in the GL_ALLOC_HISTORY table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY" />  
          <Operation Name="Op2" Action="InterfaceTables/Update/SQLGL/GL/GL_ALLOC_HISTORY " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="31c4d-151">動作對應方法，提供更大彈性，以指定的一組動作，並因此啟用屬於流經的相同連接埠的不同動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="31c4d-151">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="31c4d-152">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="31c4d-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="31c4d-153">如需每個作業的動作格式的詳細資訊，請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="31c4d-153">For more information about the action format for each operation, see [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="31c4d-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31c4d-154">See Also</span></span>  
 [<span data-ttu-id="31c4d-155">若要建立 Oracle E-business Suite 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="31c4d-155">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)