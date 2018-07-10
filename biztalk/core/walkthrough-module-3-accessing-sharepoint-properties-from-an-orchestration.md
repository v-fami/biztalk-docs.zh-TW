---
title: 逐步解說： 模組 3-從協調流程存取 SharePoint 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, orchestrations
- Windows SharePoint Services adapter tutorials, accessing SharePoint properties
ms.assetid: 310c4002-3416-44c6-b409-1d5467063e28
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0d66a381403f8649174046cb249ff92a644ac15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006823"
---
# <a name="walkthrough-module-3---accessing-sharepoint-properties-from-an-orchestration"></a><span data-ttu-id="67709-102">逐步解說： 模組 3-從協調流程存取 SharePoint 屬性</span><span class="sxs-lookup"><span data-stu-id="67709-102">Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration</span></span>
<span data-ttu-id="67709-103">這個逐步解說會將延續[逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)，並說明如何存取內送訊息在 Windows SharePoint Services 內容屬性執行階段，然後決定該屬性，使用協調流程中的動態連接埠為基礎的訊息的目的地。</span><span class="sxs-lookup"><span data-stu-id="67709-103">This walkthrough is a continuation of [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) and shows you how to access the Windows SharePoint Services context properties of an incoming message at run time and then determine the destination of that message based on a property using dynamic ports in an orchestration.</span></span> <span data-ttu-id="67709-104">如需 Windows SharePoint Services 配接器的簡介，請參閱[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="67709-104">For an introduction to the Windows SharePoint Services adapter see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="67709-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="67709-105">Prerequisites</span></span>  
 <span data-ttu-id="67709-106">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="67709-106">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
- <span data-ttu-id="67709-107">您必須擁有完整安裝上執行的 BizTalk Server 的單一伺服器部署[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67709-107">You must have a single server deployment with a complete installation of BizTalk Server running on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span></span>  
  
- <span data-ttu-id="67709-108">您必須完成下列逐步解說：[逐步解說： 模組 1-傳送和接收 Windows SharePoint Services 配接器的訊息](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)和[逐步解說： 模組 2-整合 Office 與 WindowsSharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)</span><span class="sxs-lookup"><span data-stu-id="67709-108">You must complete the following walkthroughs: [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) and [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)</span></span>  
  
  <span data-ttu-id="67709-109">在多重伺服器部署中使用 Windows SharePoint Services 配接器的相關資訊，請參閱[設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="67709-109">For information about using the Windows SharePoint Services Adapter in a multi server deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="modify-the-biztalk-project"></a><span data-ttu-id="67709-110">修改 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="67709-110">Modify the BizTalk project</span></span>  
 <span data-ttu-id="67709-111">您可以在此程序修改 PurchaseOrder 結構描述，從[逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="67709-111">In this procedure you modify the PurchaseOrder schema from [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md).</span></span> <span data-ttu-id="67709-112">本程序說明如何升級結構描述屬性，以便能在 BizTalk 協調流程中輕鬆存取。</span><span class="sxs-lookup"><span data-stu-id="67709-112">This procedure illustrates how to promote a schema property for easy access in a BizTalk orchestration.</span></span>  
  
#### <a name="modify-the-purchaseorderxsd-schema"></a><span data-ttu-id="67709-113">修改 PurchaseOrder.xsd 結構描述</span><span class="sxs-lookup"><span data-stu-id="67709-113">Modify the PurchaseOrder.xsd schema</span></span>  
  
1. <span data-ttu-id="67709-114">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="67709-114">Start **Microsoft Visual Studio**.</span></span>  
  
2. <span data-ttu-id="67709-115">按一下 **檔案**，按一下**開放**，然後按一下**專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="67709-115">Click **File**, click **Open**, and then click **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="67709-116">瀏覽至`OrderProcess.sln`檔案，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="67709-116">Browse to the `OrderProcess.sln` file, and then click **Open**.</span></span>  
  
4. <span data-ttu-id="67709-117">在 **方案總管**，以滑鼠右鍵按一下`OrderProcessSchema.xsd`檔案，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="67709-117">In **Solution Explorer**, right-click the `OrderProcessSchema.xsd` file, and then click **Open**.</span></span>  
  
5. <span data-ttu-id="67709-118">在  **BizTalk 編輯器**，展開  `PurchaseOrder`。</span><span class="sxs-lookup"><span data-stu-id="67709-118">In **BizTalk Editor**, expand `PurchaseOrder`.</span></span>  
  
6. <span data-ttu-id="67709-119">以滑鼠右鍵按一下`Amount`，按一下**升階**，然後按一下**快速升級**。</span><span class="sxs-lookup"><span data-stu-id="67709-119">Right-click `Amount`, click **Promote**, and then click **Quick Promotion**.</span></span>  
  
7. <span data-ttu-id="67709-120">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67709-120">Click **OK**.</span></span>  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="67709-121"> 會在目前的專案中為此建立屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="67709-121"> creates a property schema for this in the current project.</span></span>  
  
8. <span data-ttu-id="67709-122">儲存 `PurchaseOrder.xsd`。</span><span class="sxs-lookup"><span data-stu-id="67709-122">Save `PurchaseOrder.xsd`.</span></span>  
  
## <a name="create-an-orchestration"></a><span data-ttu-id="67709-123">建立協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-123">Create an orchestration</span></span>  
 <span data-ttu-id="67709-124">在此程序中，您要建立新的 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="67709-124">In this procedure you create a new BizTalk orchestration.</span></span> <span data-ttu-id="67709-125">此程序會建立用來處理由 Windows Sharepoint Services 配接器接收之訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="67709-125">This procedure creates the orchestration that is used to process a message received by the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="add-a-biztalk-orchestration"></a><span data-ttu-id="67709-126">新增 BizTalk 協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-126">Add a BizTalk orchestration</span></span>  
  
1.  <span data-ttu-id="67709-127">中**方案總管**，以滑鼠右鍵按一下`OrderProcess`專案中，按一下 **新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="67709-127">In **Solution Explorer**, right-click the `OrderProcess` project, click **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="67709-128">底下**分類**，選取**協調流程檔案**。</span><span class="sxs-lookup"><span data-stu-id="67709-128">Under **Categories**, select **Orchestration Files**.</span></span>  
  
3.  <span data-ttu-id="67709-129">底下**範本**，選取**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="67709-129">Under **Templates**, select **BizTalk Orchestration**.</span></span>  
  
4.  <span data-ttu-id="67709-130">型別`MyCompanyOrderProcessing`中**名稱**欄位，，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="67709-130">Type `MyCompanyOrderProcessing` in the **Name** field, and then click **Add**.</span></span>  
  
## <a name="create-receive-information"></a><span data-ttu-id="67709-131">建立接收資訊</span><span class="sxs-lookup"><span data-stu-id="67709-131">Create receive information</span></span>  
 <span data-ttu-id="67709-132">在此程序中，您要為協調流程建立新訊息、接收埠以及接收圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-132">In this procedure you create a new message, receive port, and receive shape for the orchestration.</span></span> <span data-ttu-id="67709-133">此程序說明如何設定協調流程接收的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67709-133">This procedure illustrates how to configure an orchestration to receive a message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="create-a-new-message"></a><span data-ttu-id="67709-134">新立新訊息</span><span class="sxs-lookup"><span data-stu-id="67709-134">Create a new message</span></span>  
  
1.  <span data-ttu-id="67709-135">在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="67709-135">In **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="67709-136">這樣將會產生名稱為 `Message_1` 的新訊息。</span><span class="sxs-lookup"><span data-stu-id="67709-136">This will generate a new message with the name `Message_1`.</span></span>  
  
2.  <span data-ttu-id="67709-137">以滑鼠右鍵按一下`Message_1`，按一下**重新命名**，然後輸入`Message_PO`。</span><span class="sxs-lookup"><span data-stu-id="67709-137">Right-click `Message_1`, click **Rename**, and then type `Message_PO`.</span></span>  
  
3.  <span data-ttu-id="67709-138">以滑鼠右鍵按一下`Message_PO`，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="67709-138">Right-click `Message_PO`, and then click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="67709-139">在 **訊息類型**屬性，展開**結構描述**，然後選取 `OrderProcess.OrderProcessSchema`結構描述。</span><span class="sxs-lookup"><span data-stu-id="67709-139">In the **Message Type** property, expand **Schemas**, and then select `OrderProcess.OrderProcessSchema` schema.</span></span>  
  
#### <a name="add-a-receive-port-to-the-orchestration"></a><span data-ttu-id="67709-140">新增接收埠至協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-140">Add a receive port to the orchestration</span></span>  
  
1.  <span data-ttu-id="67709-141">底下**BizTalk 協調流程**在 工具箱 拖曳**連接埠**至連接埠介面 圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-141">Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface.</span></span> <span data-ttu-id="67709-142">將會啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="67709-142">The Port Configuration Wizard will start.</span></span>  
  
2.  <span data-ttu-id="67709-143">在 [歡迎使用畫面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="67709-143">On the Welcome screen, click **Next**.</span></span>  
  
3.  <span data-ttu-id="67709-144">型別`ReceivePurchaseOrder`中**名稱**欄位，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-144">Type `ReceivePurchaseOrder` in the **Name** field, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="67709-145">選取 **建立新的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="67709-145">Select **Create a new Port Type**.</span></span>  
  
5.  <span data-ttu-id="67709-146">型別`PurchaseOrderPT`中**連接埠類型名稱**欄位，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-146">Type `PurchaseOrderPT` in the **Port Type Name** field, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="67709-147">在 **連接埠繫結螢幕**，保留預設值，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-147">On the **Port Binding screen**, leave the default values, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="67709-148">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="67709-148">Click **Finish**.</span></span>  
  
8.  <span data-ttu-id="67709-149">在 **協調流程檢視**下方**連接埠類型**，展開 `PurchaseOrderPT`連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="67709-149">In **Orchestration View**, under **Port Types**, expand the `PurchaseOrderPT` port type.</span></span>  
  
9. <span data-ttu-id="67709-150">以滑鼠右鍵按一下`Operation_1`，按一下**重新命名**，然後輸入`PurchaseOrderOperation`。</span><span class="sxs-lookup"><span data-stu-id="67709-150">Right-click `Operation_1`, click **Rename**, and then type `PurchaseOrderOperation`.</span></span>  
  
#### <a name="add-a-receive-shape-to-the-orchestration"></a><span data-ttu-id="67709-151">新增 [接收] 圖形至協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-151">Add a Receive shape to the orchestration</span></span>  
  
1.  <span data-ttu-id="67709-152">底下**BizTalk 協調流程**在 [工具箱] 拖曳**接收**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="67709-152">Under **BizTalk Orchestrations** in the Toolbox, drag a **Receive** shape to the Orchestration.</span></span>  
  
2.  <span data-ttu-id="67709-153">接收 圖形中，以滑鼠右鍵按一下，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="67709-153">Right-click the Receive shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="67709-154">設定**Activate**屬性設`True`。</span><span class="sxs-lookup"><span data-stu-id="67709-154">Set the **Activate** property to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67709-155">如果 [啟動] 屬性設定為 false，您就會收到下列錯誤：「錯誤 X2214: 您必須為位於非自我相互關聯連接埠上的非啟動接收，至少指定一個已經初始化的相互關聯集合」。</span><span class="sxs-lookup"><span data-stu-id="67709-155">If the activate property is set to false, you will get the following error: "error X2214: you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port"</span></span>  
  
4.  <span data-ttu-id="67709-156">型別`Receive_PO`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-156">Type `Receive_PO` in the **Name** field.</span></span>  
  
5.  <span data-ttu-id="67709-157">在 [**屬性] 視窗**，選取`Message_PO`訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-157">In the **Properties Window**, select `Message_PO` for the Message property.</span></span>  
  
6.  <span data-ttu-id="67709-158">選取  `ReceivePurchaseOrder.PurchaseOrderOperation.Request` for**作業**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-158">Select `ReceivePurchaseOrder.PurchaseOrderOperation.Request` for the **Operation** property.</span></span> <span data-ttu-id="67709-159">這會將繫結協調流程設計師中的 「 接收 」 圖形的連接埠。</span><span class="sxs-lookup"><span data-stu-id="67709-159">This will tie the port to the Receive shape in the Orchestration Designer.</span></span>  
  
## <a name="create-send-information"></a><span data-ttu-id="67709-160">建立傳送資訊</span><span class="sxs-lookup"><span data-stu-id="67709-160">Create send information</span></span>  
 <span data-ttu-id="67709-161">在此程序中，您要為協調流程建立新訊息、傳送埠以及決策結構。</span><span class="sxs-lookup"><span data-stu-id="67709-161">In this procedure you create a new message, send ports, and decision structure to the orchestration.</span></span> <span data-ttu-id="67709-162">此程序說明如何以決策邏輯來設定協調流程，以及如何設定協調流程將訊息傳送到傳送埠。</span><span class="sxs-lookup"><span data-stu-id="67709-162">This procedure illustrates how to configure an orchestration with decision logic and how to configure an orchestration to send a message to a send port.</span></span>  
  
#### <a name="create-a-new-message"></a><span data-ttu-id="67709-163">新立新訊息</span><span class="sxs-lookup"><span data-stu-id="67709-163">Create a new message</span></span>  
  
1.  <span data-ttu-id="67709-164">在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="67709-164">In **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="67709-165">這樣將會產生名稱為 `Message_1` 的新訊息。</span><span class="sxs-lookup"><span data-stu-id="67709-165">This will generate a new message with the name `Message_1`.</span></span>  
  
2.  <span data-ttu-id="67709-166">以滑鼠右鍵按一下`Message_1`，按一下**重新命名**，然後輸入`Message_Task`。</span><span class="sxs-lookup"><span data-stu-id="67709-166">Right-click `Message_1`, click **Rename**, and then type `Message_Task`.</span></span>  
  
3.  <span data-ttu-id="67709-167">以滑鼠右鍵按一下`Message_Task`，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="67709-167">Right-click `Message_Task`, and then click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="67709-168">在 **訊息類型**屬性，展開**結構描述**，然後選取 `OrderProcess.OrderProcessSchema`結構描述。</span><span class="sxs-lookup"><span data-stu-id="67709-168">In the **Message Type** property, expand **Schemas**, and then select `OrderProcess.OrderProcessSchema` schema.</span></span>  
  
#### <a name="add-a-send-port-to-the-orchestration"></a><span data-ttu-id="67709-169">新增傳送埠至協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-169">Add a send port to the orchestration</span></span>  
  
1.  <span data-ttu-id="67709-170">底下**BizTalk 協調流程**在 工具箱 拖曳**連接埠**至連接埠介面 圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-170">Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface.</span></span> <span data-ttu-id="67709-171">將會啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="67709-171">The Port Configuration Wizard will start.</span></span>  
  
2.  <span data-ttu-id="67709-172">在 [歡迎使用畫面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="67709-172">On the Welcome screen, click **Next**.</span></span>  
  
3.  <span data-ttu-id="67709-173">型別`SendPurchaseOrder`中**名稱**欄位，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-173">Type `SendPurchaseOrder` in the **Name** field, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="67709-174">選取 **使用現有的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="67709-174">Select **Use an existing Port Type**.</span></span>  
  
5.  <span data-ttu-id="67709-175">底下**可用的連接埠類型**，選取`OrderProcess.PurchaseOrderPT`，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-175">Under **Available Port Types**, select `OrderProcess.PurchaseOrderPT`, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="67709-176">上**連接埠繫結螢幕**下方**連接埠通訊方向**，選取`I'll always be sending messages on this port`，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-176">On the **Port Binding screen**, under **Port direction of communication**, select `I'll always be sending messages on this port`, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="67709-177">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="67709-177">Click **Finish**.</span></span>  
  
#### <a name="add-a-send-shape-to-the-orchestration"></a><span data-ttu-id="67709-178">新增 [傳送] 圖形至協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-178">Add a Send shape to the orchestration</span></span>  
  
1.  <span data-ttu-id="67709-179">底下**BizTalk 協調流程**在 [工具箱] 拖曳**傳送**圖形至協調流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="67709-179">Under **BizTalk Orchestrations** in the Toolbox, drag a **Send** shape to the Orchestration Designer.</span></span> <span data-ttu-id="67709-180">將它放在 `Receive_PO` 接收圖形下方。</span><span class="sxs-lookup"><span data-stu-id="67709-180">Place it below the `Receive_PO` Receive shape.</span></span>  
  
2.  <span data-ttu-id="67709-181">以滑鼠右鍵按一下 傳送 圖形，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="67709-181">Right-click the Send shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="67709-182">型別`Send_PO`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-182">Type `Send_PO` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="67709-183">選取  `Message_PO` for**訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-183">Select `Message_PO` for the **Message** property.</span></span>  
  
5.  <span data-ttu-id="67709-184">選取  `SendPurchaseOrder.PurchaseOrderOperation.Request` for**作業**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-184">Select `SendPurchaseOrder.PurchaseOrderOperation.Request` for the **Operation** property.</span></span> <span data-ttu-id="67709-185">這會結合連接埠至 [協調流程設計師] 中的 [傳送] 圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-185">This will tie the port to the Send shape in the Orchestration Designer.</span></span>  
  
#### <a name="add-a-decide-shape-to-the-orchestration"></a><span data-ttu-id="67709-186">新增 [決定] 圖形至協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-186">Add a Decide shape to the orchestration</span></span>  
  
1.  <span data-ttu-id="67709-187">底下**BizTalk 協調流程**在 [工具箱] 拖曳**決定**圖形至協調流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="67709-187">Under **BizTalk Orchestrations** in the Toolbox, drag a **Decide** shape to the Orchestration Designer.</span></span> <span data-ttu-id="67709-188">將它放在 `Send_PO` 傳送圖形下方。</span><span class="sxs-lookup"><span data-stu-id="67709-188">Place it below the `Send_PO` Send shape.</span></span>  
  
2.  <span data-ttu-id="67709-189">[決定] 圖形中，以滑鼠右鍵按一下，然後按一下 [**屬性] 視窗。**</span><span class="sxs-lookup"><span data-stu-id="67709-189">Right-click the Decide shape, and then click **Properties Window.**</span></span>  
  
3.  <span data-ttu-id="67709-190">型別`NeedsApproval`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-190">Type `NeedsApproval` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="67709-191">在 [協調流程設計師 」 中按一下**Rule_1**決定] 圖形上。</span><span class="sxs-lookup"><span data-stu-id="67709-191">In Orchestration Designer, click **Rule_1** on the Decide shape.</span></span>  
  
5.  <span data-ttu-id="67709-192">在 屬性 Windows 中，鍵入`ApprovalRequired`for**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-192">In the Properties Windows, type `ApprovalRequired` for the **Name** property.</span></span>  
  
6.  <span data-ttu-id="67709-193">按一下 **運算式**屬性欄位，，然後按一下 省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67709-193">Click the **Expression** property field, and then click the ellipsis (**…**) button.</span></span>  
  
7.  <span data-ttu-id="67709-194">在 [BizTalk 運算式編輯器] 中，輸入或複製下列運算式：</span><span class="sxs-lookup"><span data-stu-id="67709-194">In the BizTalk Expression Editor, type or copy the following:</span></span>  
  
    ```  
    Message_PO(OrderProcess.PropertySchema.Amount) > 1000  
    ```  
  
8.  <span data-ttu-id="67709-195">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67709-195">Click **OK**.</span></span>  
  
#### <a name="add-another-send-port-to-the-orchestration"></a><span data-ttu-id="67709-196">新增另一個傳送埠至協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-196">Add another send port to the orchestration</span></span>  
  
1.  <span data-ttu-id="67709-197">底下**BizTalk 協調流程**在 工具箱 拖曳**連接埠**至連接埠介面 圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-197">Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface.</span></span> <span data-ttu-id="67709-198">將會啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="67709-198">The Port Configuration Wizard will start.</span></span>  
  
2.  <span data-ttu-id="67709-199">在 [歡迎使用畫面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="67709-199">On the Welcome screen, click **Next**.</span></span>  
  
3.  <span data-ttu-id="67709-200">型別`SendToTasksList`中**名稱**欄位，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-200">Type `SendToTasksList` in the **Name** field, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="67709-201">選取 **使用現有的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="67709-201">Select **Use an existing Port Type**.</span></span>  
  
5.  <span data-ttu-id="67709-202">底下**可用的連接埠類型**，選取`OrderProcess.PurchaseOrderPT`，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-202">Under **Available Port Types**, select `OrderProcess.PurchaseOrderPT`, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="67709-203">在上**連接埠繫結螢幕**下方**連接埠通訊方向**，選取`I'll always be sending messages on this port`。</span><span class="sxs-lookup"><span data-stu-id="67709-203">On the **Port Binding screen**, under **Port direction of communication**, select `I'll always be sending messages on this port`.</span></span>  
  
7.  <span data-ttu-id="67709-204">底下**連接埠繫結**，選取`Dynamic`，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="67709-204">Under **Port binding**, select `Dynamic`, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="67709-205">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="67709-205">Click **Finish**.</span></span>  
  
#### <a name="add-a-send-shape-to-the-decide-shape"></a><span data-ttu-id="67709-206">新增 [傳送] 圖形至 [決定] 圖形</span><span class="sxs-lookup"><span data-stu-id="67709-206">Add a Send shape to the Decide shape</span></span>  
  
1.  <span data-ttu-id="67709-207">底下**BizTalk 協調流程**在 [工具箱] 拖曳**傳送**圖形至協調流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="67709-207">Under **BizTalk Orchestrations** in the Toolbox, drag a **Send** shape to the Orchestration Designer.</span></span> <span data-ttu-id="67709-208">將圖形放置在 `ApprovalRequired` 圖形的下方。</span><span class="sxs-lookup"><span data-stu-id="67709-208">Place it below the `ApprovalRequired` shape.</span></span>  
  
2.  <span data-ttu-id="67709-209">以滑鼠右鍵按一下 傳送 圖形，然後按一下**屬性 視窗**</span><span class="sxs-lookup"><span data-stu-id="67709-209">Right-click the Send shape, and then click **Properties Window**</span></span>  
  
3.  <span data-ttu-id="67709-210">型別`CreateApprovalTask`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-210">Type `CreateApprovalTask` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="67709-211">選取  `Message_Task` for**訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-211">Select `Message_Task` for the **Message** property.</span></span>  
  
5.  <span data-ttu-id="67709-212">選取  `SendToTasksList.PurchaseOrderOperation.Request` for**作業**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-212">Select `SendToTasksList.PurchaseOrderOperation.Request` for the **Operation** property.</span></span> <span data-ttu-id="67709-213">這會結合連接埠至 [協調流程設計師] 中的 [傳送] 圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-213">This will tie the port to the Send shape in the Orchestration Designer.</span></span>  
  
## <a name="create-an-expression"></a><span data-ttu-id="67709-214">建立運算式</span><span class="sxs-lookup"><span data-stu-id="67709-214">Create an expression</span></span>  
 <span data-ttu-id="67709-215">在此程序中，您要新增 [運算式] 圖形至指派工作路徑值給變數的解決方案中。</span><span class="sxs-lookup"><span data-stu-id="67709-215">In this procedure you add an Expression shape to your solution which assigns the Tasks path value to a variable.</span></span> <span data-ttu-id="67709-216">此程序說明如何將邏輯新增到協調流程，以修改動態傳送埠的屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-216">This procedure illustrates how to add logic to an orchestration to modify the properties of a dynamic send port.</span></span>  
  
#### <a name="create-a-new-expression"></a><span data-ttu-id="67709-217">新立新的運算式</span><span class="sxs-lookup"><span data-stu-id="67709-217">Create a new expression</span></span>  
  
1.  <span data-ttu-id="67709-218">底下**BizTalk 協調流程**在 [工具箱] 拖曳**運算式**圖形之前`CreateApprovalTask`傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-218">Under **BizTalk Orchestrations** in the Toolbox, drag an **Expression** shape before the `CreateApprovalTask` Send shape.</span></span>  
  
2.  <span data-ttu-id="67709-219">以滑鼠右鍵按一下 運算式 圖形，然後按一下**屬性 視窗。**</span><span class="sxs-lookup"><span data-stu-id="67709-219">Right-click the Expression shape, and then click **Properties Window.**</span></span>  
  
3.  <span data-ttu-id="67709-220">型別`SetPortDestination`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-220">Type `SetPortDestination` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="67709-221">按一下 **運算式**屬性欄位，，然後按一下 省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67709-221">Click the **Expression** property field, and then click the ellipsis (**…**) button.</span></span>  
  
5.  <span data-ttu-id="67709-222">在  **BizTalk 運算式編輯器**，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="67709-222">In the **BizTalk Expression Editor**, type the following:</span></span>  
  
    ```  
    SendToTasksList(Microsoft.XLANGs.BaseTypes.Address) = "wss://localhost/sites/WSSAdapterWalkthrough/Lists/Tasks/";  
    ```  
  
6.  <span data-ttu-id="67709-223">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67709-223">Click **OK**.</span></span>  
  
## <a name="construct-a-new-message"></a><span data-ttu-id="67709-224">建構新訊息</span><span class="sxs-lookup"><span data-stu-id="67709-224">Construct a new message</span></span>  
 <span data-ttu-id="67709-225">在此程序中，您要新增 [建構] 圖形至將在協調流程中建構新的訊息類型執行個體的解決方案中。</span><span class="sxs-lookup"><span data-stu-id="67709-225">In this procedure you add a Construct shape to the solution which will construct a new instance of a message type within the orchestration.</span></span> <span data-ttu-id="67709-226">此程序說明如何建立同時也是輸入訊息複本的新訊息，然後修改此新訊息的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-226">This procedure illustrates how to create a new message that is a copy of the inbound message and then modify the context properties of the new message.</span></span> <span data-ttu-id="67709-227">由於訊息在 BizTalk 中是不變的，因此需要執行此步驟；也就是說，一旦您建構了訊息，便無法修改原始訊息。</span><span class="sxs-lookup"><span data-stu-id="67709-227">This step is required because messages are immutable in BizTalk; that is, once you have constructed it, you cannot modify the original.</span></span>  
  
#### <a name="add-a-construct-shape"></a><span data-ttu-id="67709-228">新增 [建構] 圖形</span><span class="sxs-lookup"><span data-stu-id="67709-228">Add a Construct Shape</span></span>  
  
1.  <span data-ttu-id="67709-229">底下**BizTalk 協調流程**在 [工具箱] 拖曳**建構訊息**圖形之前`SetPortDestination`運算式 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-229">Under **BizTalk Orchestrations** in the Toolbox, drag a **Construct Message** shape before the `SetPortDestination` Expression shape.</span></span>  
  
2.  <span data-ttu-id="67709-230">[建構訊息] 圖形中，以滑鼠右鍵按一下，然後按一下 [**屬性] 視窗。**</span><span class="sxs-lookup"><span data-stu-id="67709-230">Right-click the Construct Message shape, and then click **Properties Window.**</span></span>  
  
3.  <span data-ttu-id="67709-231">型別`ConstructTaskMessage`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-231">Type `ConstructTaskMessage`in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="67709-232">選取  `Message_Task` for**建構的訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-232">Select `Message_Task` for the **Messages Constructed** property.</span></span>  
  
5.  <span data-ttu-id="67709-233">底下**BizTalk 協調流程**在 [工具箱] 拖曳**訊息指派**塑造成`ConstructTaskMessage`**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="67709-233">Under **BizTalk Orchestrations** in the Toolbox, drag a **Message Assignment** shape into the `ConstructTaskMessage`**Construct Message** shape.</span></span>  
  
6.  <span data-ttu-id="67709-234">在 [**屬性] 視窗**，型別`InitTaskMessage`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-234">In the **Properties Window**, type `InitTaskMessage` in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="67709-235">按一下 **運算式**屬性欄位，，然後按一下 省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67709-235">Click the **Expression** property field, and then click the ellipsis (**…**) button.</span></span>  
  
8.  <span data-ttu-id="67709-236">在  **BizTalk 運算式編輯器**中，輸入或複製下列：</span><span class="sxs-lookup"><span data-stu-id="67709-236">In the **BizTalk Expression Editor**, type or copy the following:</span></span>  
  
    ```  
    Message_Task = Message_PO;  
    Message_Task(WSS.ConfigOverwrite) = "no";  
    Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";  
    Message_Task(WSS.ConfigPropertiesXml) = "<ConfigPropertiesXml><PropertyName1>Title</PropertyName1><PropertySource1>Approve %XPATH=//orchns:PurchaseOrder/orchns:PurchaseOrderID%</PropertySource1><PropertyName3>Status</PropertyName3><PropertySource3>Not Started</PropertySource3><PropertyName4>Priority</PropertyName4><PropertySource4>(1) High</PropertySource4></ConfigPropertiesXml>";  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="67709-237">提供給內容屬性的這些值有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="67709-237">These values supplied for these context properties are case sensitive.</span></span> <span data-ttu-id="67709-238">在設定具有內容屬性的動態連接埠之組態值時，您必須確定使用適當的大小寫，否則，當 BizTalk 嘗試路由文件至指定的傳送埠時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="67709-238">When setting configuration values for a dynamic port with context properties you must ensure that you use the proper case or an error will occur when BizTalk attempts to route the document to the designated send port.</span></span>  
  
9. <span data-ttu-id="67709-239">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67709-239">Click **OK**.</span></span>  
  
10. <span data-ttu-id="67709-240">按一下 **檔案**，然後按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="67709-240">Click **File**, and then click **Save All**.</span></span>  
  
## <a name="build-the-biztalk-project"></a><span data-ttu-id="67709-241">建置 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="67709-241">Build the BizTalk project</span></span>  
 <span data-ttu-id="67709-242">在此程序中，您要建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="67709-242">In this procedure you build and deploy the BizTalk project.</span></span> <span data-ttu-id="67709-243">此步驟，才能建立和部署組件，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在執行階段使用。</span><span class="sxs-lookup"><span data-stu-id="67709-243">This step is required to create and deploy the assembly that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses at runtime.</span></span>  
  
#### <a name="build-and-deploy-the-solution"></a><span data-ttu-id="67709-244">建置和部署解決方案</span><span class="sxs-lookup"><span data-stu-id="67709-244">Build and deploy the solution</span></span>  
  
1. <span data-ttu-id="67709-245">按一下 **建置**，然後按一下**建置 OrderProcess**。</span><span class="sxs-lookup"><span data-stu-id="67709-245">Click **Build**, and then click **Build OrderProcess**.</span></span>  
  
2. <span data-ttu-id="67709-246">按一下 **建置**，然後按一下**部署 OrderProcess**。</span><span class="sxs-lookup"><span data-stu-id="67709-246">Click **Build**, and then click **Deploy OrderProcess**.</span></span>  
  
3. <span data-ttu-id="67709-247">關閉 [Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]]。</span><span class="sxs-lookup"><span data-stu-id="67709-247">Close Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="modify-the-receive-location-and-send-port"></a><span data-ttu-id="67709-248">修改接收位置與傳送埠</span><span class="sxs-lookup"><span data-stu-id="67709-248">Modify the receive location and send port</span></span>  
 <span data-ttu-id="67709-249">在此程序中，您要修改現有的接收位置和傳送埠，以便在管線中使用 XML 處理。</span><span class="sxs-lookup"><span data-stu-id="67709-249">In this procedure you modify the existing receive location and send port to use XML processing for the pipelines.</span></span> <span data-ttu-id="67709-250">接收 XML 管線會保存協調流程處理期間使用的訊息屬性，而傳送 XML 管線會保存套用到協調流程中的訊息屬性，且此屬性後續會用於訊息路由。</span><span class="sxs-lookup"><span data-stu-id="67709-250">The receive XML pipeline persists message properties used during orchestration processing and the send XML pipeline persists the message properties that were applied in the orchestration which are subsequently used for message routing.</span></span>  
  
#### <a name="modify-the-receive-location"></a><span data-ttu-id="67709-251">修改接收位置</span><span class="sxs-lookup"><span data-stu-id="67709-251">Modify the receive location</span></span>  
  
1. <span data-ttu-id="67709-252">按一下 **開始**，指向**所有程式**，指向**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理]。**</span><span class="sxs-lookup"><span data-stu-id="67709-252">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2. <span data-ttu-id="67709-253">依序展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **管理嵌入式管理單元**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開  **BizTalk Application 1**，然後按一下**接收位置**節點。</span><span class="sxs-lookup"><span data-stu-id="67709-253">Expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration SnapIn**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and then click the **Receive Locations** node.</span></span>  
  
3. <span data-ttu-id="67709-254">以滑鼠右鍵按一下`SourceLocation`，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="67709-254">Right-click `SourceLocation`, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="67709-255">在 **接收位置屬性**對話方塊的 **一般**，選取`XMLReceive`如**接收管線**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-255">In the **Receive Location Properties** dialog box, under **General**, select `XMLReceive` for the **Receive pipeline** property.</span></span>  
  
5. <span data-ttu-id="67709-256">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67709-256">Click **OK**.</span></span>  
  
#### <a name="modify-the-send-port"></a><span data-ttu-id="67709-257">修改傳送埠</span><span class="sxs-lookup"><span data-stu-id="67709-257">Modify the send port</span></span>  
  
1.  <span data-ttu-id="67709-258">按一下 **傳送埠**節點。</span><span class="sxs-lookup"><span data-stu-id="67709-258">Click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="67709-259">以滑鼠右鍵按一下`SendToDestination`，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="67709-259">Right-click `SendToDestination`, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="67709-260">在 **傳送埠屬性**對話方塊的 **一般**，選取`XMLTransmit`如**傳送管線**屬性。</span><span class="sxs-lookup"><span data-stu-id="67709-260">In the **Send Port Properties** dialog box, under **General**, select `XMLTransmit` for the **Send pipeline** property.</span></span>  
  
4.  <span data-ttu-id="67709-261">選取 [**篩選器**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="67709-261">Select the **Filters** tab.</span></span>  
  
5.  <span data-ttu-id="67709-262">選取現有的條件，按下 DELETE，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="67709-262">Select the existing condition, press DELETE, and then click **OK**.</span></span>  
  
#### <a name="start-a-new-send-port"></a><span data-ttu-id="67709-263">啟動新的傳送埠</span><span class="sxs-lookup"><span data-stu-id="67709-263">Start a new send port</span></span>  
  
1.  <span data-ttu-id="67709-264">按一下 **傳送埠**節點。</span><span class="sxs-lookup"><span data-stu-id="67709-264">Click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="67709-265">以滑鼠右鍵按一下`OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="67709-265">Right-click `OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`, and then click **Start**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67709-266">若看不見此項目，您可能需要重新整理主控台。</span><span class="sxs-lookup"><span data-stu-id="67709-266">You may have to refresh the console if this is not visible.</span></span>  
  
## <a name="bind-the-orchestration"></a><span data-ttu-id="67709-267">繫結協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-267">Bind the orchestration</span></span>  
 <span data-ttu-id="67709-268">在此程序中，您要繫結協調流程至指定的連接埠。</span><span class="sxs-lookup"><span data-stu-id="67709-268">In this procedure you bind the orchestration to the specified ports.</span></span> <span data-ttu-id="67709-269">此程序必須將實體連接埠結合至您建立和部署的協調流程。</span><span class="sxs-lookup"><span data-stu-id="67709-269">This procedure is required to tie physical ports to the orchestration that you built and deployed.</span></span>  
  
#### <a name="bind-the-orchestration"></a><span data-ttu-id="67709-270">繫結協調流程</span><span class="sxs-lookup"><span data-stu-id="67709-270">Bind the orchestration</span></span>  
  
1. <span data-ttu-id="67709-271">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**協調流程**節點。</span><span class="sxs-lookup"><span data-stu-id="67709-271">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Orchestrations** node.</span></span>  
  
2. <span data-ttu-id="67709-272">以滑鼠右鍵按一下`OrderProcess.MyCompanyOrderProcessing`協調流程，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="67709-272">Right-click the `OrderProcess.MyCompanyOrderProcessing` orchestration, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="67709-273">選取 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="67709-273">Select the **Bindings** tab.</span></span>  
  
4. <span data-ttu-id="67709-274">底下**主機**，選取`BizTalkServerApplication`中**主機**欄位。</span><span class="sxs-lookup"><span data-stu-id="67709-274">Under **Host**, select `BizTalkServerApplication` in the **Host** field.</span></span>  
  
5. <span data-ttu-id="67709-275">底下**繫結**，選取`FromSource`如`ReceivePurchaseOrder`輸入邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="67709-275">Under **Bindings**, select `FromSource` for the `ReceivePurchaseOrder` Inbound Logical Port.</span></span>  
  
6. <span data-ttu-id="67709-276">底下**繫結**，選取`SendToDestination`如`SendPurchaseOrder`輸出邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="67709-276">Under **Bindings**, select `SendToDestination` for the `SendPurchaseOrder` Outbound Logical Port.</span></span>  
  
7. <span data-ttu-id="67709-277">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67709-277">Click **OK**.</span></span>  
  
8. <span data-ttu-id="67709-278">以滑鼠右鍵按一下`OrderProcess.MyCompanyOrderProcessing`協調流程，然後再按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="67709-278">Right click `OrderProcess.MyCompanyOrderProcessing` orchestration, and then click **Start**.</span></span>  
  
## <a name="send-a-message-through-the-system"></a><span data-ttu-id="67709-279">透過系統傳送訊息</span><span class="sxs-lookup"><span data-stu-id="67709-279">Send a message through the system</span></span>  
 <span data-ttu-id="67709-280">在此程序中，您要建立 InfoPath 表單，並將它上載至 Windows SharePoint Services 網站。</span><span class="sxs-lookup"><span data-stu-id="67709-280">In this procedure you create an InfoPath form and upload it to the Windows SharePoint Services Web site.</span></span> <span data-ttu-id="67709-281">Windows SharePoint Services 配接器會取得該訊息、封存至「封存」文件庫，然後傳送至「目的地」文件庫。</span><span class="sxs-lookup"><span data-stu-id="67709-281">The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library.</span></span> <span data-ttu-id="67709-282">在處理此訊息期間，將存取 Windows SharePoint Services 內容屬性，以協助決定目的地。</span><span class="sxs-lookup"><span data-stu-id="67709-282">During the processing of this message, Windows SharePoint Services context properties will be accessed that help determine the destination.</span></span>  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a><span data-ttu-id="67709-283">建立 InfoPath 表單以透過系統傳送</span><span class="sxs-lookup"><span data-stu-id="67709-283">Create an InfoPath form to send through the system</span></span>  
  
1.  <span data-ttu-id="67709-284">開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。</span><span class="sxs-lookup"><span data-stu-id="67709-284">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="67709-285">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="67709-285">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="67709-286">在 [快速啟動] 功能表中，按一下 `InfoPathSolutions`。</span><span class="sxs-lookup"><span data-stu-id="67709-286">In the Quick Launch menu, click `InfoPathSolutions`.</span></span>  
  
3.  <span data-ttu-id="67709-287">按一下 `PurchaseOrder`檔案，以顯示**檔案下載**對話方塊，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="67709-287">Click the `PurchaseOrder` file to display the **File Download** dialog box, and then click **Open**.</span></span> <span data-ttu-id="67709-288">InfoPath 將載入此表單。</span><span class="sxs-lookup"><span data-stu-id="67709-288">InfoPath will load the form.</span></span>  
  
4.  <span data-ttu-id="67709-289">在 **採購單識別碼**欄位中，輸入`1003`。</span><span class="sxs-lookup"><span data-stu-id="67709-289">In the **Purchase Order ID** field, type `1003`.</span></span>  
  
5.  <span data-ttu-id="67709-290">在 **付款人**欄位中，輸入`John Doe`。</span><span class="sxs-lookup"><span data-stu-id="67709-290">In the **Bill To** field, type `John Doe`.</span></span>  
  
6.  <span data-ttu-id="67709-291">在 **金額**欄位中，輸入`1750`。</span><span class="sxs-lookup"><span data-stu-id="67709-291">In the **Amount** field, type `1750`.</span></span>  
  
7.  <span data-ttu-id="67709-292">在 **採購單日期**欄位中，輸入`1/3/2005`。</span><span class="sxs-lookup"><span data-stu-id="67709-292">In the **Purchase Order Date** field, type `1/3/2005`.</span></span>  
  
8.  <span data-ttu-id="67709-293">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="67709-293">Click **Save**.</span></span>  
  
9. <span data-ttu-id="67709-294">在 [**另存新檔**] 對話方塊中，輸入`http://<server_name>/sites/WSSAdapterWalkthrough/Source`中**檔案名稱**欄位，然後再按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="67709-294">In the **Save As** dialog box, type `http://<server_name>/sites/WSSAdapterWalkthrough/Source`in the **file name** field, and then press ENTER.</span></span>  
  
10. <span data-ttu-id="67709-295">型別`PurchaseOrder3.xml`中**檔案名稱**欄位，，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="67709-295">Type `PurchaseOrder3.xml` in the **file name** field, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="67709-296">關閉 InfoPath。</span><span class="sxs-lookup"><span data-stu-id="67709-296">Close InfoPath.</span></span>  
  
12. <span data-ttu-id="67709-297">在網頁瀏覽器中，按一下**文件，並列出**。</span><span class="sxs-lookup"><span data-stu-id="67709-297">In the Web browser, click **Documents and Lists**.</span></span>  
  
13. <span data-ttu-id="67709-298">底下**文件庫**，按一下**目的地**。</span><span class="sxs-lookup"><span data-stu-id="67709-298">Under **Document Libraries**, click **Destination**.</span></span>  
  
14. <span data-ttu-id="67709-299">在 [目的地] 文件庫中，您現在會看見已列出您的訊息。</span><span class="sxs-lookup"><span data-stu-id="67709-299">In the Destination document library, you will now see your message listed in this library.</span></span> <span data-ttu-id="67709-300">您也可以在 [封存] 文件庫中找到封存的複本。</span><span class="sxs-lookup"><span data-stu-id="67709-300">You will also find a copy archived in the Archive document library.</span></span>  
  
15. <span data-ttu-id="67709-301">按一下 [首頁]。</span><span class="sxs-lookup"><span data-stu-id="67709-301">Click **Home**.</span></span>  
  
16. <span data-ttu-id="67709-302">底下**列出**，按一下**工作**。</span><span class="sxs-lookup"><span data-stu-id="67709-302">Under **Lists**, click **Tasks**.</span></span>  
  
17. <span data-ttu-id="67709-303">在 [工作] 清單中，您會看見新建立的核准工作。</span><span class="sxs-lookup"><span data-stu-id="67709-303">In the Tasks list you will see the newly created approval task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67709-304">由於訂單金額超過 $1,000.00，所以建立此工作。</span><span class="sxs-lookup"><span data-stu-id="67709-304">Since the amount of the purchase order was over $1,000.00, the task was created.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="67709-305">摘要</span><span class="sxs-lookup"><span data-stu-id="67709-305">Summary</span></span>  
 <span data-ttu-id="67709-306">在此逐步解說中，您已經瞭解如何存取 Windows SharePoint Services 內容屬性，以及如何決定通過動態連接埠之訊息的目的地。</span><span class="sxs-lookup"><span data-stu-id="67709-306">In this walkthrough you have seen how to access the Windows SharePoint Services context properties and how to determine the destination of messages going through dynamic ports.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="67709-307">後續步驟</span><span class="sxs-lookup"><span data-stu-id="67709-307">Next Steps</span></span>  
 <span data-ttu-id="67709-308">繼續檢視 Windows SharePoint Services 配接器章節的其他部分。</span><span class="sxs-lookup"><span data-stu-id="67709-308">Continue to review the rest of the Windows SharePoint Services adapter section.</span></span> <span data-ttu-id="67709-309">如需詳細資訊，請參閱＜另請參閱＞中的主題。</span><span class="sxs-lookup"><span data-stu-id="67709-309">For more information, see the topics in See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67709-310">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67709-310">See Also</span></span>  
 <span data-ttu-id="67709-311">[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="67709-311">[What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="67709-312">Windows SharePoint Services 配接器逐步解說</span><span class="sxs-lookup"><span data-stu-id="67709-312">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)