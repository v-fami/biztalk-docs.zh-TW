---
title: "在 BizTalk 中設定 Oracle 資料庫的 SOAP 動作 |Microsoft 文件"
description: "在 Visual Studio 中，輸入 SOAP 動作，或使用 Wcf-custom 或 Wcf-oracledb 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d21cca-3907-4f99-af76-c1e7286e1bcf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2577a221385cdef2e210798b3e8170433ff0e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-oracle-database"></a><span data-ttu-id="33814-103">設定 Oracle 資料庫的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="33814-103">Configure the SOAP action for Oracle Database</span></span>
<span data-ttu-id="33814-104">若要完成使用 WCF 型 Oracle 資料庫中的任何作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，配接器使用者必須輸入 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="33814-104">To complete any operation on the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], adapter users must enter a SOAP action.</span></span> <span data-ttu-id="33814-105">SOAP 動作與外界溝通的配接器應該完成哪些動作。</span><span class="sxs-lookup"><span data-stu-id="33814-105">The SOAP action communicates to the adapter what action should be completed.</span></span> <span data-ttu-id="33814-106">您可以輸入在設計階段或執行階段的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="33814-106">You can enter the SOAP action either at design time or at run time.</span></span> <span data-ttu-id="33814-107">不過，如果您輸入的 SOAP 動作這兩個設計階段和執行階段時，就會覆寫您在設計階段輸入的動作。</span><span class="sxs-lookup"><span data-stu-id="33814-107">However, if you enter the SOAP action both at design time and run time, the action you enter at design time is overridden.</span></span>  
  
 <span data-ttu-id="33814-108">如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="33814-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>  
  
## <a name="enter-soap-action-from-visual-studio"></a><span data-ttu-id="33814-109">從 Visual Studio 輸入 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="33814-109">Enter SOAP Action from Visual Studio</span></span>  
 <span data-ttu-id="33814-110">從 Visual Studio 中，您必須指定的 SOAP 動作協調流程的一部分使用**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="33814-110">From Visual Studio, you must specify the SOAP action as part of the orchestration by using an **Expression** shape.</span></span>  
  
1.  <span data-ttu-id="33814-111">在 BizTalk 協調流程中，包括**運算式**圖形，方法是將它從**BizTalk 協調流程**工具箱。</span><span class="sxs-lookup"><span data-stu-id="33814-111">In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="33814-112">按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="33814-112">Double-click the **Expression** shape to open the BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="33814-113">在 BizTalk 運算式編輯器 」 中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="33814-113">Specify the action in the BizTalk Expression Editor.</span></span> <span data-ttu-id="33814-114">例如：</span><span class="sxs-lookup"><span data-stu-id="33814-114">For example:</span></span>  
  
    ```
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
    ```  
  
     <span data-ttu-id="33814-115">如需有關**運算式**圖形和 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="33814-115">For more information about **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>  
  
## <a name="enter-soap-action-from-biztalk-server-administration"></a><span data-ttu-id="33814-116">輸入 SOAP 動作，從 BizTalk Server 管理</span><span class="sxs-lookup"><span data-stu-id="33814-116">Enter SOAP Action from BizTalk Server Administration</span></span>  
 <span data-ttu-id="33814-117">從 BizTalk Server 管理主控台中，您必須指定 Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="33814-117">From the BizTalk Server Administration console, you must specify the SOAP action as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span> 

#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="33814-118">輸入 WCF 自訂連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="33814-118">Enter a SOAP action for the WCF-Custom port</span></span>  
 
  
1.  <span data-ttu-id="33814-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="33814-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="33814-120">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用的程式在其下您想要建立連接埠，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="33814-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="33814-121">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="33814-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="33814-122">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="33814-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="33814-123">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33814-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="33814-124">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="33814-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="33814-125">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="33814-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="33814-126">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="33814-126">**By using the single action format**.</span></span> <span data-ttu-id="33814-127">如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="33814-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="33814-128">例如：</span><span class="sxs-lookup"><span data-stu-id="33814-128">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
        ```  
  
    -   <span data-ttu-id="33814-129">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="33814-129">**By using the action mapping format**.</span></span> <span data-ttu-id="33814-130">如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="33814-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="33814-131">比方說，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要將記錄插入 EMP 資料表中） Op1 和 Op2 （若要更新 EMP 資料表中的記錄），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="33814-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the EMP table) and Op2 (to update records in the EMP table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="33814-132">此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="33814-132">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="33814-133">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="33814-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="33814-134">如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="33814-134">For more information about action format for each operation, see [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>  
  
#### <a name="enter-a-soap-action-for-the-wcf-oracledb-port"></a><span data-ttu-id="33814-135">輸入 Wcf-oracledb 連接埠的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="33814-135">Enter a SOAP action for the WCF-OracleDB port</span></span>  
  
1.  <span data-ttu-id="33814-136">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="33814-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="33814-137">新增 Wcf-oracledb 配接器至 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="33814-137">Add the WCF-OracleDB adapter to the BizTalk Server Administration console.</span></span> <span data-ttu-id="33814-138">如需指示，請參閱[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="33814-138">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="33814-139">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用的程式在其下您想要建立連接埠，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="33814-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="33814-140">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="33814-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="33814-141">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 Wcf-oracledb 連接埠，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="33814-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleDB port you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="33814-142">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33814-142">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="33814-143">在**動作**文字方塊中，指定作業的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="33814-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="33814-144">您可以下列方式指定的動作：</span><span class="sxs-lookup"><span data-stu-id="33814-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="33814-145">**使用單一動作格式**。</span><span class="sxs-lookup"><span data-stu-id="33814-145">**By using the single action format**.</span></span> <span data-ttu-id="33814-146">如果 Wcf-oracledb 連接埠傳送和接收訊息的單一作業，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="33814-146">Use this format if the WCF-OracleDB port sends and receive messages for a single operation.</span></span> <span data-ttu-id="33814-147">例如：</span><span class="sxs-lookup"><span data-stu-id="33814-147">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
        ```  
  
    -   <span data-ttu-id="33814-148">**使用動作對應格式**。</span><span class="sxs-lookup"><span data-stu-id="33814-148">**By using the action mapping format**.</span></span> <span data-ttu-id="33814-149">如果單一 Wcf-oracledb 連接埠傳送和接收多個作業的訊息，請使用此格式。</span><span class="sxs-lookup"><span data-stu-id="33814-149">Use this format if a single WCF-OracleDB port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="33814-150">比方說，如果單一 Wcf-oracledb 連接埠傳送與接收訊息 （若要將記錄插入 EMP 資料表中） Op1 和 Op2 （若要更新 EMP 資料表中的記錄），可以指定的 SOAP 動作以下列方式：</span><span class="sxs-lookup"><span data-stu-id="33814-150">For example, if a single WCF-OracleDB port sends and receives messages for Op1 (to insert records in the EMP table) and Op2 (to update records in the EMP table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="33814-151">此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="33814-151">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="33814-152">SOAP 動作的格式是不同的每一項作業。</span><span class="sxs-lookup"><span data-stu-id="33814-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="33814-153">如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="33814-153">For more information about action format for each operation, see [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="33814-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33814-154">See Also</span></span>  
[<span data-ttu-id="33814-155">開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊</span><span class="sxs-lookup"><span data-stu-id="33814-155">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)