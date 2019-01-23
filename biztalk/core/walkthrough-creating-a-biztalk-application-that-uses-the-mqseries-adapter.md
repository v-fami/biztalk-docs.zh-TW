---
title: 逐步解說：建立 BizTalk 應用程式使用 MQSeries 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IBM WebSphere MQ queues
- MQSeries adapters, tutorial
- MQSeries adapters, testing
- tutorials, MQSeries adapters
- MQSeries adapters, IBM WebSphere MQ queues
- testing, MQSeries adapters
- MQSeries adapters, queues
- configuring [MQSeries adapters], tutorial
ms.assetid: e9e169e4-d41c-4e5d-b165-7bd36b481f24
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d882ee7134861496266b0d18bb288e39e05bad29
ms.sourcegitcommit: 2d39bcd10a22c5945d97a03988ccdc62f6fb3c93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2019
ms.locfileid: "54443387"
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-mqseries-adapter"></a><span data-ttu-id="1146d-102">逐步解說：建立 BizTalk 應用程式使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="1146d-102">Walkthrough: Creating a BizTalk Application That Uses the MQSeries Adapter</span></span>
<span data-ttu-id="1146d-103">本節將帶領您建立使用 MQSeries 配接器的簡單 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1146d-103">This section takes you through creating a simple Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application that uses the MQSeries adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1146d-104">此應用程式假設您已經在與 BizTalk Server 相同的電腦上安裝 IBM WebSphere MQ (適用於 Windows 平台的伺服器元件)。</span><span class="sxs-lookup"><span data-stu-id="1146d-104">The application assumes that you have installed the IBM WebSphere MQ, server component for Windows platforms on the same computer as BizTalk Server.</span></span> <span data-ttu-id="1146d-105">它也假設您尚未建立任何傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="1146d-105">It also assumes that you have not yet created any send ports or receive locations.</span></span> <span data-ttu-id="1146d-106">若您有現有的傳送埠或接收位置，當逐步進行這些步驟時請以適當的名稱來替代。</span><span class="sxs-lookup"><span data-stu-id="1146d-106">If you have existing send ports or receive locations, substitute appropriate names when you work through the steps.</span></span>  
  
 <span data-ttu-id="1146d-107">此應用程式是一個簡單以內容為基礎的路由應用程式，只使用一個接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="1146d-107">The application is a simple content-based routing application using only a receive location and a send port.</span></span> <span data-ttu-id="1146d-108">接收位置會從 IBM WebSphere MQ 佇列讀取。</span><span class="sxs-lookup"><span data-stu-id="1146d-108">The receive location reads from an IBM WebSphere MQ queue.</span></span> <span data-ttu-id="1146d-109">傳送埠會從接收位置取得訊息，並將它傳送到不同的 IBM WebSphere MQ 佇列。</span><span class="sxs-lookup"><span data-stu-id="1146d-109">The send port takes the message from the receive location and sends it to a different IBM WebSphere MQ queue.</span></span>  
  
 <span data-ttu-id="1146d-110">若要建立此應用程式，您必須建立 IBM WebSphere MQ 佇列、設定 BizTalk Server 接收位置與傳送埠、啟動傳送埠和啟用接收位置，並將測試訊息放在佇列中。</span><span class="sxs-lookup"><span data-stu-id="1146d-110">To create the application, you have to create the IBM WebSphere MQ queues, set up the BizTalk Server receive location and send port, start the send port and enable the receive location, and put a test message in the queue.</span></span>  
  
 <span data-ttu-id="1146d-111">若您擁有 IBM WebSphere MQ 安裝所需的權限，您可以透過配接器對話方塊建立 IBM WebSphere MQ 佇列，並可略過下一個程序。</span><span class="sxs-lookup"><span data-stu-id="1146d-111">If you have the required permissions to the IBM WebSphere MQ installation, you can create the IBM WebSphere MQ queues through the adapter dialog boxes, and can skip the next procedure.</span></span> <span data-ttu-id="1146d-112">若您沒有這類存取權限，您可以使用 IBM WebSphere MQ (適用於 Windows 平台總管的用戶端元件) 來建立佇列。</span><span class="sxs-lookup"><span data-stu-id="1146d-112">If you do not have such access, you can create the queues using the IBM WebSphere MQ, client components for Windows platforms Explorer.</span></span> <span data-ttu-id="1146d-113">若要透過 IBM WebSphere MQ Explorer 嵌入式管理單元來建立佇列，請執行下列程序。</span><span class="sxs-lookup"><span data-stu-id="1146d-113">To create the queues through the IBM WebSphere MQ Explorer snap-in, perform the following procedure.</span></span>  
  
## <a name="to-create-the-ibm-websphere-mq-queues-through-the-ibm-websphere-mq-explorer"></a><span data-ttu-id="1146d-114">透過 IBM WebSphere MQ Explorer 建立 IBM WebSphere MQ 佇列</span><span class="sxs-lookup"><span data-stu-id="1146d-114">To create the IBM WebSphere MQ queues through the IBM WebSphere MQ Explorer</span></span>  
 <span data-ttu-id="1146d-115">請依照以下步驟執行，透過 IBM WebSphere MQ Explorer 建立 IBM WebSphere MQ 佇列：</span><span class="sxs-lookup"><span data-stu-id="1146d-115">Follow these steps to create the IBM WebSphere MQ queues through the IBM WebSphere MQ Explorer:</span></span>  
  
1. <span data-ttu-id="1146d-116">按一下 **開始**，指向**程式**，指向**IBM WebSphere MQ**，然後按一下**WebSphere MQ Explorer**。</span><span class="sxs-lookup"><span data-stu-id="1146d-116">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2. <span data-ttu-id="1146d-117">按兩下**佇列管理員**，然後按兩下預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="1146d-117">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="1146d-118">預設佇列管理員通常會命名為**Qm_&lt**_< 電腦名稱 >_ 位置*machine_name*是您電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="1146d-118">The default queue manager is typically named **QM_**_<machine_name>_ where *machine_name* is the name of your computer.</span></span>  
  
3. <span data-ttu-id="1146d-119">以滑鼠右鍵按一下**佇列**，指向**新增**，然後按一下**本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="1146d-119">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4. <span data-ttu-id="1146d-120">中**建立本機佇列**對話方塊中，於**佇列名稱**，型別**BTStoMQS**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1146d-120">In **Create Local Queue** dialog box, in **Queue Name**, type **BTStoMQS**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="1146d-121">以滑鼠右鍵按一下**佇列**，指向**新增**，然後按一下**本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="1146d-121">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
6. <span data-ttu-id="1146d-122">中**建立本機佇列**對話方塊中，於**佇列名稱**，型別**MQStoBTS**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1146d-122">In **Create Local Queue** dialog box, in **Queue Name**, type **MQStoBTS**, and then click **OK**.</span></span>  
  
   <span data-ttu-id="1146d-123">接下來的步驟會建立接收位置和傳送埠，並啟動傳送埠及啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="1146d-123">The next steps create the receive location and the send port, and start the send port and enable the receive location.</span></span> <span data-ttu-id="1146d-124">並且也會建立 IBM WebSphere MQ 佇列。</span><span class="sxs-lookup"><span data-stu-id="1146d-124">They also create the IBM WebSphere MQ queues.</span></span>  
  
## <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="1146d-125">建立接收位置與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="1146d-125">To create the receive location and the MQSeries queue</span></span>  
 <span data-ttu-id="1146d-126">請依照以下步驟執行，建立接收位置與 MQSeries 佇列：</span><span class="sxs-lookup"><span data-stu-id="1146d-126">Follow these steps to create the receive location and the MQSeries queue:</span></span>  
  
1.  <span data-ttu-id="1146d-127">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，然後展開 [預設值應用程式 (**BizTalk Application 1**預設情況下)。</span><span class="sxs-lookup"><span data-stu-id="1146d-127">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the default application (**BizTalk Application 1** by default).</span></span>  
  
2.  <span data-ttu-id="1146d-128">以滑鼠右鍵按一下**接收埠**節點中，按一下**新增**，然後選取**單向連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1146d-128">Right-click the **Receive Ports** node, click **New**, and select **One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="1146d-129">在 **接收埠屬性**對話方塊中，於**名稱**方塊中，輸入**MQStoBTS**。</span><span class="sxs-lookup"><span data-stu-id="1146d-129">In the **Receive Port Properties** dialog box, in the **Name** box, type **MQStoBTS**.</span></span>  
  
4.  <span data-ttu-id="1146d-130">在左窗格中，按一下**接收位置**，然後在右窗格中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1146d-130">In the left pane, click **Receive Locations**, and in the right pane, click **New**.</span></span>  
  
5.  <span data-ttu-id="1146d-131">在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**MQStoBTS**。</span><span class="sxs-lookup"><span data-stu-id="1146d-131">In the **Receive Location Properties** dialog box, in the **Name** box, type **MQStoBTS**.</span></span>  
  
6.  <span data-ttu-id="1146d-132">選取  **MQSeries**下拉式清單中下一步**型別**選項。</span><span class="sxs-lookup"><span data-stu-id="1146d-132">Select **MQSeries** from the drop-down list next to the **Type** option.</span></span>  
  
7.  <span data-ttu-id="1146d-133">在 **傳輸**區段中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1146d-133">In the **Transport** section, click **Configure**.</span></span>  
  
8.  <span data-ttu-id="1146d-134">在  **MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入**1**。</span><span class="sxs-lookup"><span data-stu-id="1146d-134">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type **1**.</span></span>  
  
9. <span data-ttu-id="1146d-135">在 [**佇列定義**方塊中，按一下省略符號 (**...**)] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1146d-135">In the **Queue Definition** box, click the ellipsis (**…**) button.</span></span>  
  
10. <span data-ttu-id="1146d-136">在 **佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="1146d-136">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
11. <span data-ttu-id="1146d-137">在 **佇列管理員**方塊中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="1146d-137">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
12. <span data-ttu-id="1146d-138">在 **佇列**方塊中，輸入**MQStoBTS**，然後按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="1146d-138">In the **Queue** box, type **MQStoBTS**, and then click **Export**.</span></span>  
  
13. <span data-ttu-id="1146d-139">在**匯出** 對話方塊中，按一下**Create Queue**，然後按一下**確定**並**確定** ，以返回**接收位置屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1146d-139">In the **Export** dialog box, click **Create Queue**,and then click **OK** and **OK** again to return to the **Receive Location Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="1146d-140">在 **接收處理常式**方塊中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="1146d-140">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
15. <span data-ttu-id="1146d-141">在 **接收管線**方塊中，選取**PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="1146d-141">In the **Receive Pipeline** box, select **PassThruReceive**.</span></span>  
  
16. <span data-ttu-id="1146d-142">按一下 **確定**以套用變更。</span><span class="sxs-lookup"><span data-stu-id="1146d-142">Click **OK** to apply changes.</span></span>  
  
## <a name="to-create-the-send-port-and-the-mqseries-queue"></a><span data-ttu-id="1146d-143">建立傳送埠與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="1146d-143">To create the send port and the MQSeries queue</span></span>  
 <span data-ttu-id="1146d-144">請依照以下步驟執行，建立傳送埠與 MQSeries 佇列：</span><span class="sxs-lookup"><span data-stu-id="1146d-144">Follow these steps to create the send port and the MQSeries queue:</span></span>  
  
1.  <span data-ttu-id="1146d-145">以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="1146d-145">Right-click **Send Ports**, click **New**, and select **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="1146d-146">在 **傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入**BTStoMQS。**</span><span class="sxs-lookup"><span data-stu-id="1146d-146">In the **Send Port Properties** dialog box, in the **Name** box, type **BTStoMQS.**</span></span>  
  
3.  <span data-ttu-id="1146d-147">選取  **MQSeries**下拉式清單中下一步**型別**選項。</span><span class="sxs-lookup"><span data-stu-id="1146d-147">Select **MQSeries** from the drop-down list next to the **Type** option.</span></span>  
  
4.  <span data-ttu-id="1146d-148">在 **傳輸**區段中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1146d-148">In the **Transport** section, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="1146d-149">在 [ **MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下省略符號 (**...**)] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1146d-149">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (**…**) button.</span></span>  
  
6.  <span data-ttu-id="1146d-150">在 **佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="1146d-150">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
7.  <span data-ttu-id="1146d-151">在 **佇列管理員**方塊中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="1146d-151">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
8.  <span data-ttu-id="1146d-152">在 **佇列**方塊中，輸入**BTStoMQS**，然後按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="1146d-152">In the **Queue** box, type **BTStoMQS**, and then click **Export**.</span></span>  
  
9. <span data-ttu-id="1146d-153">在**匯出** 對話方塊中，按一下**Create Queue**，然後按一下  **確定**並**確定** ，以返回**傳送埠屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1146d-153">In the **Export** dialog box, click **Create Queue**, and then click **OK** and **OK** again to return to the **Send Port Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="1146d-154">在 **傳送管線**方塊中，選取**PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="1146d-154">In the **Send Pipeline** box, select **PassThruTransmit**.</span></span>  
  
11. <span data-ttu-id="1146d-155">按一下以選取**篩選器**在左窗格中，然後在右窗格中設定篩選選項。</span><span class="sxs-lookup"><span data-stu-id="1146d-155">Click to select **Filters** in the left pane, and then configure filter options in the right pane.</span></span>  
  
12. <span data-ttu-id="1146d-156">在 **屬性**下拉式清單中，選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="1146d-156">In the **Property** drop-down list, select **BTS.ReceivePortName**.</span></span>  
  
13. <span data-ttu-id="1146d-157">在 **值**方塊中，輸入**MQStoBTS**。</span><span class="sxs-lookup"><span data-stu-id="1146d-157">In the **Value** box, type **MQStoBTS**.</span></span>  
  
14. <span data-ttu-id="1146d-158">按一下 **確定**以套用變更。</span><span class="sxs-lookup"><span data-stu-id="1146d-158">Click **OK** to apply changes.</span></span>  
  
## <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="1146d-159">啟用接收位置和啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="1146d-159">To enable the receive location and start the send port</span></span>  
 <span data-ttu-id="1146d-160">請依照以下步驟執行，啟用接收位置和啟動傳送埠：</span><span class="sxs-lookup"><span data-stu-id="1146d-160">Follow these steps to enable the receive location and start the send port:</span></span>  
  
1. <span data-ttu-id="1146d-161">以滑鼠右鍵按一下**MQStoBTS**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="1146d-161">Right-click the **MQStoBTS** receive location, and then click **Enable**.</span></span>  
  
2. <span data-ttu-id="1146d-162">以滑鼠右鍵按一下**BTStoMQS**傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="1146d-162">Right-click the **BTStoMQS** send port, and then click **Start**.</span></span>  
  
   <span data-ttu-id="1146d-163">下一步是藉由傳送測試訊息到接收佇列，以測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="1146d-163">The next step is to test the application by sending a test message to the receive queue.</span></span>  
  
## <a name="to-test-the-application"></a><span data-ttu-id="1146d-164">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="1146d-164">To test the application</span></span>  
 <span data-ttu-id="1146d-165">請依照以下步驟執行來測試應用程式：</span><span class="sxs-lookup"><span data-stu-id="1146d-165">Follow these steps to test the application:</span></span>  
  
1. <span data-ttu-id="1146d-166">按一下 **開始**，指向**程式**，指向**IBM WebSphere MQ**，然後按一下**WebSphere MQ Explorer**。</span><span class="sxs-lookup"><span data-stu-id="1146d-166">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2. <span data-ttu-id="1146d-167">以滑鼠右鍵按一下**MQStoBTS**，然後按一下**放入測試訊息**。</span><span class="sxs-lookup"><span data-stu-id="1146d-167">Right-click **MQStoBTS**, and then click **Put Test Message**.</span></span>  
  
3. <span data-ttu-id="1146d-168">在 **訊息資料**方塊中，輸入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="1146d-168">In the **Message Data** box, type a test message.</span></span> <span data-ttu-id="1146d-169">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1146d-169">Click **OK**.</span></span>  
  
   <span data-ttu-id="1146d-170">輸入資料之後,**目前的深度**for **MQStoBTS**佇列是一 (1)。</span><span class="sxs-lookup"><span data-stu-id="1146d-170">After you enter the data, the **Current Depth** for the **MQStoBTS** queue is one (1).</span></span> <span data-ttu-id="1146d-171">當應用程式處理訊息時，計數會傳回零 (0) 和**目前深度**for **BTStoMQS**會變成一 （1)。</span><span class="sxs-lookup"><span data-stu-id="1146d-171">When the application processes the message, the count returns to zero (0) and the **Current Depth** for **BTStoMQS** becomes one (1).</span></span> <span data-ttu-id="1146d-172">您也可以檢視訊息內容。</span><span class="sxs-lookup"><span data-stu-id="1146d-172">You can also view the content of the message.</span></span>  
  
## <a name="to-view-the-message"></a><span data-ttu-id="1146d-173">檢視訊息</span><span class="sxs-lookup"><span data-stu-id="1146d-173">To view the message</span></span>  
 <span data-ttu-id="1146d-174">請依照以下步驟執行來檢視訊息：</span><span class="sxs-lookup"><span data-stu-id="1146d-174">Follow these steps to view the message:</span></span>  
  
1.  <span data-ttu-id="1146d-175">按兩下**BTStoMQS**佇列。</span><span class="sxs-lookup"><span data-stu-id="1146d-175">Double-click the **BTStoMQS** queue.</span></span>  
  
2.  <span data-ttu-id="1146d-176">按兩下訊息，然後按**資料**工作表。</span><span class="sxs-lookup"><span data-stu-id="1146d-176">Double-click the message, and then select the **Data** sheet.</span></span> <span data-ttu-id="1146d-177">您可以檢視中的訊息的文字**訊息資料** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="1146d-177">You can view the text of the message in the **Message Data** box.</span></span>  
  
3.  <span data-ttu-id="1146d-178">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1146d-178">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1146d-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1146d-179">See Also</span></span>  
 <span data-ttu-id="1146d-180">[何謂 MQSeries 配接器？](../core/what-is-the-mqseries-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="1146d-180">[What Is the MQSeries Adapter?](../core/what-is-the-mqseries-adapter.md) </span></span>  
 [<span data-ttu-id="1146d-181">MQSeries 配接器架構</span><span class="sxs-lookup"><span data-stu-id="1146d-181">MQSeries Adapter Architecture</span></span>](../core/mqseries-adapter-architecture.md)
