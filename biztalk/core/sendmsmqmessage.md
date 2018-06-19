---
title: SendMSMQMessage |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, examples
- examples, MSMQ adapters
ms.assetid: 398bc396-0c66-4d55-886a-0d9bdab6476f
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a48cbb333a724d2f60141f0f67ef3feccb1d3954
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975508"
---
# <a name="sendmsmqmessage"></a><span data-ttu-id="f8080-102">SendMSMQMessage</span><span class="sxs-lookup"><span data-stu-id="f8080-102">SendMSMQMessage</span></span>
<span data-ttu-id="f8080-103">SendMSMQMessage 範例將示範如何從 .NET 架構的應用程式將訊息傳送至 MSMQ 連接埠。</span><span class="sxs-lookup"><span data-stu-id="f8080-103">The SendMSMQMessage sample demonstrates how to send a message to an MSMQ port from a .NET-based application.</span></span> <span data-ttu-id="f8080-104">此外還提供如何設定 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用 MSMQ 接收位置的指示。</span><span class="sxs-lookup"><span data-stu-id="f8080-104">It also provides instructions about how to configure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use an MSMQ receive location.</span></span>  
  
 <span data-ttu-id="f8080-105">您應該注意在訊息佇列中的許多作業都是非同步。</span><span class="sxs-lookup"><span data-stu-id="f8080-105">You should be aware that many operations in Message Queuing are asynchronous.</span></span> <span data-ttu-id="f8080-106">也就是說，許多 MSMQ API 呼叫 (例如， **System.Messaging.MessageQueue.Send**) 傳回給呼叫端要求的作業完全完成之前。</span><span class="sxs-lookup"><span data-stu-id="f8080-106">That is, many MSMQ API calls (for example, **System.Messaging.MessageQueue.Send**) return to the caller before the requested operation has fully completed.</span></span> <span data-ttu-id="f8080-107">MSMQ 提供一項機制，會在作業全部完成之後將回應傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8080-107">MSMQ provides a mechanism to deliver feedback to the application after the operation has completed.</span></span> <span data-ttu-id="f8080-108">這個機制需要用到「管理佇列」。</span><span class="sxs-lookup"><span data-stu-id="f8080-108">This mechanism involves the use of an "Admin Queue."</span></span> <span data-ttu-id="f8080-109">MSMQ 管理佇列中訊息的形式，傳回的意見反應。</span><span class="sxs-lookup"><span data-stu-id="f8080-109">MSMQ returns feedback in the form of a message in the Admin Queue.</span></span> <span data-ttu-id="f8080-110">當進行原始 MSMQ API 呼叫時，便會指定 MSMQ 要將回應傳送所至的管理佇列。</span><span class="sxs-lookup"><span data-stu-id="f8080-110">The Admin Queue to which MSMQ will return feedback is specified when the original MSMQ API call is made.</span></span> <span data-ttu-id="f8080-111">因此，範例中，當傳送訊息，使用**System.Messaging.MessageQueue.Send** API，應用程式可以指定管理佇列的名稱使用**PROPID_M_ADMIN_QUEUE**訊息屬性訊息傳遞的呼叫中**System.Messaging.MessageQueue.Send**。</span><span class="sxs-lookup"><span data-stu-id="f8080-111">So, for example, when sending a message using the **System.Messaging.MessageQueue.Send** API, the application can specify the name of an Admin Queue by using the **PROPID_M_ADMIN_QUEUE** message property on the message passed in the call to **System.Messaging.MessageQueue.Send**.</span></span> <span data-ttu-id="f8080-112">即使應用程式可能取得成功的傳回碼**System.Messaging.MessageQueue.Send**呼叫時，如果後續訊息傳送作業失敗，MSMQ 訊息寫入該效果指定管理佇列。</span><span class="sxs-lookup"><span data-stu-id="f8080-112">Even though the application may get a successful return code on the **System.Messaging.MessageQueue.Send** call, if the message send operation subsequently fails, MSMQ writes a message to that effect to the specified Admin Queue.</span></span> <span data-ttu-id="f8080-113">如果應用程式未指定管理佇列，傳送失敗會導致訊息遺失，無法擷取診斷資訊： 訊息作用中，會毫無跡象消失。</span><span class="sxs-lookup"><span data-stu-id="f8080-113">If the application does not specify an Admin Queue, the send failure results in the message being lost and no diagnostics captured — in effect, the message disappears without any evidence.</span></span> <span data-ttu-id="f8080-114">有一些情況下，可能會造成這種情形，例如，執行非交易式 MSMQ 中的傳送至異動式佇列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8080-114">There are a number of error situations in MSMQ that can cause this to happen, for example, doing a non-transactional send to a transactional queue.</span></span>  
  
 <span data-ttu-id="f8080-115">在此範例的內容，是很重要的程式碼呼叫中指定交易類型**System.Messaging.MessageQueue.Send**這與指定訊息是佇列的交易支援一致傳送。</span><span class="sxs-lookup"><span data-stu-id="f8080-115">In the context of this sample, it is important that the code specify a transaction type in the call to **System.Messaging.MessageQueue.Send** that is consistent with the transaction support specified for the queue to which the message is sent.</span></span> <span data-ttu-id="f8080-116">如果未進行此設定，而且如果沒有指定管理佇列是 （在此情況下在此範例中），MSMQ 捨棄傳送的訊息，它確實會留下任何跡象 （也就是沒有錯誤碼傳回至應用程式，而不將診斷資訊寫入事件記錄檔依此類推)。</span><span class="sxs-lookup"><span data-stu-id="f8080-116">If this is not done and if no Admin Queue is specified (as is the case in this sample), then MSMQ discards the sent message with no indication that it has done so (that is, no error code returned to the application, no diagnostics written to the event log, and so on).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="f8080-117">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f8080-117">Where to Find This Sample</span></span>  
 <span data-ttu-id="f8080-118">\<範例路徑\>\AdaptersUsage\SendMSMQMessage\\</span><span class="sxs-lookup"><span data-stu-id="f8080-118">\<Samples Path\>\AdaptersUsage\SendMSMQMessage\\</span></span>  
  
 <span data-ttu-id="f8080-119">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f8080-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="f8080-120">檔案</span><span class="sxs-lookup"><span data-stu-id="f8080-120">Files</span></span>|<span data-ttu-id="f8080-121">Description</span><span class="sxs-lookup"><span data-stu-id="f8080-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8080-122">App.ico、AssemblyInfo.cs、SendMSMQMessage.csproj、SendMSMQMessage.sln</span><span class="sxs-lookup"><span data-stu-id="f8080-122">App.ico, AssemblyInfo.cs, SendMSMQMessage.csproj, SendMSMQMessage.sln</span></span>|<span data-ttu-id="f8080-123">提供專案、 解決方案和相關的檔案，此範例的簡易圖形應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8080-123">Provide project, solution, and related files for the simple graphical application for this sample.</span></span>|  
|<span data-ttu-id="f8080-124">Form1.cs、Form1.resx</span><span class="sxs-lookup"><span data-stu-id="f8080-124">Form1.cs, Form1.resx</span></span>|<span data-ttu-id="f8080-125">提供 Microsoft[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]此範例的簡易圖形應用程式的.NET 來源和格式檔案。</span><span class="sxs-lookup"><span data-stu-id="f8080-125">Provide Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].NET source and form files for the simple graphical application for this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="f8080-126">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="f8080-126">How to Use This Sample</span></span>  
 <span data-ttu-id="f8080-127">您可以在此範例包含做為範例如何將訊息傳送至 MSMQ 接收位置內的簡易圖形應用程式中使用程式碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從。網路功能的應用程式 Microsoft Office，例如從 ASP.NET 網頁，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f8080-127">You can use the code in the simple graphical application included with this sample as an example of how to send messages to MSMQ receive locations within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from .NET-enabled applications such as Microsoft Office, from ASP.NET pages, and so on.</span></span>  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="f8080-128">建置和初始化範例</span><span class="sxs-lookup"><span data-stu-id="f8080-128">Building and Initializing the Sample</span></span>  
  
#### <a name="to-build-the-sample-executable"></a><span data-ttu-id="f8080-129">建置範例可執行檔</span><span class="sxs-lookup"><span data-stu-id="f8080-129">To build the sample executable</span></span>  
  
1.  <span data-ttu-id="f8080-130">使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 SendMSMQMessage.sln。</span><span class="sxs-lookup"><span data-stu-id="f8080-130">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendMSMQMessage.sln.</span></span>  
  
2.  <span data-ttu-id="f8080-131">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="f8080-131">On the **Build** menu, click **Build Solution**.</span></span>  
  
## <a name="configuring-biztalk-server-and-creating-the-msmq-queue"></a><span data-ttu-id="f8080-132">設定 BizTalk Server 及建立 MSMQ 佇列</span><span class="sxs-lookup"><span data-stu-id="f8080-132">Configuring BizTalk Server and Creating the MSMQ Queue</span></span>  
 <span data-ttu-id="f8080-133">使用下列程序設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並建立執行範例的 MSMQ 佇列。</span><span class="sxs-lookup"><span data-stu-id="f8080-133">Use the following procedures to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and create the MSMQ queue for running the sample.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-server-2008-r2-or-windows-server-2008-sp2"></a><span data-ttu-id="f8080-134">在 Windows Server 2008 R2 或 Windows Server 2008 SP2 中建立 MSMQ 佇列</span><span class="sxs-lookup"><span data-stu-id="f8080-134">To create the MSMQ queue in Windows Server 2008 R2 or Windows Server 2008 SP2</span></span>  
  
1.  <span data-ttu-id="f8080-135">按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下 **管理**。</span><span class="sxs-lookup"><span data-stu-id="f8080-135">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="f8080-136">展開**功能**節點。</span><span class="sxs-lookup"><span data-stu-id="f8080-136">Expand the **Features** node.</span></span>  <span data-ttu-id="f8080-137">如果**訊息佇列**是未安裝，以滑鼠右鍵按一下**功能**選取**新增功能**。</span><span class="sxs-lookup"><span data-stu-id="f8080-137">If **Message Queuing** is not installed, right-click **Features** and select **Add Features**.</span></span>  <span data-ttu-id="f8080-138">檢查**訊息佇列**，按一下 **下一步**，然後按一下 **安裝**該系統上安裝 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="f8080-138">Check **Message Queuing**, click **Next**, and then click **Install** to install MSMQ on that system.</span></span>  
  
3.  <span data-ttu-id="f8080-139">展開**訊息佇列**節點。</span><span class="sxs-lookup"><span data-stu-id="f8080-139">Expand the **Message Queuing** node.</span></span>  
  
4.  <span data-ttu-id="f8080-140">以滑鼠右鍵按一下**私用佇列**節點中，按一下 **新增**，然後按一下 **私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="f8080-140">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
5.  <span data-ttu-id="f8080-141">在下**佇列名稱**，輸入`test`。</span><span class="sxs-lookup"><span data-stu-id="f8080-141">Under **Queue name**, enter `test`.</span></span> <span data-ttu-id="f8080-142">請確認**交易式**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-142">Ensure that the **Transactional** check box is selected.</span></span>  
  
6.  <span data-ttu-id="f8080-143">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f8080-143">Click **OK**.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-7-or-windows-vista-sp2"></a><span data-ttu-id="f8080-144">在 Windows 7 或 Windows Vista SP2 中建立 MSMQ 佇列</span><span class="sxs-lookup"><span data-stu-id="f8080-144">To create the MSMQ queue in Windows 7 or Windows Vista SP2</span></span>  
  
1.  <span data-ttu-id="f8080-145">按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下 **管理**。</span><span class="sxs-lookup"><span data-stu-id="f8080-145">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="f8080-146">展開**服務和應用程式**，然後展開**訊息佇列**節點。</span><span class="sxs-lookup"><span data-stu-id="f8080-146">Expand **Services and Applications**, and then expand the **Message Queuing** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8080-147">如果**訊息佇列**未安裝在電腦中，移至**控制台 > 程式 > 程式和功能**，然後選取**開啟或關閉 Windows 功能**。</span><span class="sxs-lookup"><span data-stu-id="f8080-147">If **Message Queuing** is not installed in the computer, go to **Control Panel > Programs > Programs and Features**, and then select **Turn Windows features on or off**.</span></span> <span data-ttu-id="f8080-148">檢查下的所有功能**Microsoft Message Queue (MSMQ) 伺服器**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f8080-148">Check all the features under **Microsoft Message Queue (MSMQ) Server**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f8080-149">以滑鼠右鍵按一下**私用佇列**節點中，按一下 **新增**，然後按一下 **私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="f8080-149">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
4.  <span data-ttu-id="f8080-150">在下**佇列名稱**，輸入**測試**。</span><span class="sxs-lookup"><span data-stu-id="f8080-150">Under **Queue name**, enter **test**.</span></span> <span data-ttu-id="f8080-151">請確認**交易式**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-151">Ensure that the **Transactional** check box is selected.</span></span>  
  
5.  <span data-ttu-id="f8080-152">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f8080-152">Click **OK**.</span></span>  
  
#### <a name="to-configure-biztalk-server"></a><span data-ttu-id="f8080-153">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f8080-153">To configure BizTalk Server</span></span>  
  
1.  <span data-ttu-id="f8080-154">選取要接收訊息的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8080-154">Select a folder in which to receive messages.</span></span> <span data-ttu-id="f8080-155">下列步驟假設您已選取 C:\Demo\Report，不過您可以視需要調整步驟以使用其他資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8080-155">The following steps assume that you have selected C:\Demo\Report, but you can adjust the steps as necessary for another folder.</span></span>  
  
2.  <span data-ttu-id="f8080-156">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f8080-156">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
3.  <span data-ttu-id="f8080-157">建立新的應用程式，名為**MSMQSample**。</span><span class="sxs-lookup"><span data-stu-id="f8080-157">Create a new application named **MSMQSample**.</span></span>  
  
4.  <span data-ttu-id="f8080-158">以滑鼠右鍵按一下**接收埠**，按一下 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f8080-158">Right-click **Receive Ports**, click **New**, and then click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="f8080-159">中**接收埠屬性**對話方塊中，於**名稱**] 方塊中輸入**MyReceivePort**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="f8080-159">In the **Receive Port Properties** dialog box, in the **Name** box enter **MyReceivePort**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="f8080-160">以滑鼠右鍵按一下**接收位置**，按一下 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="f8080-160">Right-click **Receive Locations**, click **New**, and then click **One-way Receive Location**.</span></span> <span data-ttu-id="f8080-161">在**選取接收埠**對話方塊中，選取您剛才的接收埠建立，並按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f8080-161">In the **Select a Receive Port** dialog box, select the receive port you just created and click **OK**.</span></span>  
  
7.  <span data-ttu-id="f8080-162">在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入接收埠名稱，例如**MSMQReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="f8080-162">In the **Receive Location Properties** dialog box, in the **Name** box, type a name for the receive port, such as **MSMQReceiveLocation**.</span></span>  
  
8.  <span data-ttu-id="f8080-163">在**接收位置屬性**對話方塊的 傳輸類型，選取**MSMQ** 。</span><span class="sxs-lookup"><span data-stu-id="f8080-163">In the **Receive Location Properties** dialog box, for the transport type, select **MSMQ** .</span></span>  
  
9. <span data-ttu-id="f8080-164">按一下**設定**開啟**MSMQ 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-164">Click **Configure** to open the **MSMQ Transport Properties** dialog box.</span></span> <span data-ttu-id="f8080-165">設定**佇列**至`localhost\private$\test`，將**交易式**至`True`，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="f8080-165">Set **Queue** to `localhost\private$\test`, set **Transactional** to `True`, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="f8080-166">展開 應用程式中，選取**傳送埠**，選取**新增**，選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f8080-166">Expand the application, select **Send Ports**, select **New**, select **Static One-way Send Port**.</span></span>  
  
11. <span data-ttu-id="f8080-167">在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入傳送埠名稱，例如**MySendPort**。</span><span class="sxs-lookup"><span data-stu-id="f8080-167">In the **Send Port Properties** dialog box, in the **Name** box, type a name for the send port, such as **MySendPort**.</span></span>  
  
12. <span data-ttu-id="f8080-168">設定**傳輸類型**屬性**檔案**。</span><span class="sxs-lookup"><span data-stu-id="f8080-168">Set the **Transport Type** property to **FILE**.</span></span>  
  
13. <span data-ttu-id="f8080-169">按一下**設定**開啟**File 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-169">Click **Configure** to open the **File Transport Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="f8080-170">在**FILE 傳輸屬性** 對話方塊中，將**目的地資料夾**屬性**C:\Demo\Report**，保留其他屬性，預設值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f8080-170">In the **FILE Transport Properties** dialog box, set the **Destination Folder** property to **C:\Demo\Report**, keep the default settings for the other properties, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="f8080-171">選取**篩選**，然後加入新的資料列，藉由設定**屬性**至**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="f8080-171">Select **Filters**, and then add a new row by setting **Property** to **BTS.ReceivePortName**.</span></span> <span data-ttu-id="f8080-172">保留**運算子**資料行設為 **==** ，將**值**欄**MyReceivePort**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="f8080-172">Leave the **Operator** column set to **==**, set the **Value** column to **MyReceivePort**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="f8080-173">以滑鼠右鍵按一下您的新傳送埠，然後按一下 **登錄**。</span><span class="sxs-lookup"><span data-stu-id="f8080-173">Right-click your new send port, and then click **Enlist**.</span></span>  
  
17. <span data-ttu-id="f8080-174">以滑鼠右鍵按一下您的新傳送埠，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="f8080-174">Right-click your new send port again, and then click **Start**.</span></span>  
  
18. <span data-ttu-id="f8080-175">以滑鼠右鍵按一下您的新接收位置，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="f8080-175">Right-click your new receive location, and then click **Enable**.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f8080-176">現在已可使用這個範例。</span><span class="sxs-lookup"><span data-stu-id="f8080-176"> is now ready to work with this sample.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="f8080-177">執行範例</span><span class="sxs-lookup"><span data-stu-id="f8080-177">Running the Sample</span></span>  
 <span data-ttu-id="f8080-178">使用下列程序執行 SendMSMQMessage 範例。</span><span class="sxs-lookup"><span data-stu-id="f8080-178">Use the following procedure to run the SendMSMQMessage sample.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="f8080-179">執行範例</span><span class="sxs-lookup"><span data-stu-id="f8080-179">To run the sample</span></span>  
  
1.  <span data-ttu-id="f8080-180">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f8080-180">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="f8080-181">\<範例路徑\>\AdaptersUsage\SendMSMQMessage\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="f8080-181">\<Samples Path\>\AdaptersUsage\SendMSMQMessage\bin\Debug</span></span>  
  
2.  <span data-ttu-id="f8080-182">執行 SendMSMQMessage.exe，它會啟動此範例中提供的使用者介面的圖形應用程式的檔案。</span><span class="sxs-lookup"><span data-stu-id="f8080-182">Run the file SendMSMQMessage.exe, which starts the graphical application that provides the user interface for this sample.</span></span>  
  
3.  <span data-ttu-id="f8080-183">在圖形應用程式中**BizTalk 電腦名稱**方塊中，輸入本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8080-183">In the graphical application, in the **BizTalk machine name** box, type the name of the local computer.</span></span>  
  
4.  <span data-ttu-id="f8080-184">再試一次**傳送包裝項目**選項：</span><span class="sxs-lookup"><span data-stu-id="f8080-184">Try the **Send Wrapped** option:</span></span>  
  
    1.  <span data-ttu-id="f8080-185">選擇性地變更中的文字**訊息主體**方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-185">Optionally change the text in the **Message body** box.</span></span>  
  
    2.  <span data-ttu-id="f8080-186">按一下**傳送包裝**。</span><span class="sxs-lookup"><span data-stu-id="f8080-186">Click **Send wrapped**.</span></span>  
  
     <span data-ttu-id="f8080-187">如果作業成功，您會看到下列項目：</span><span class="sxs-lookup"><span data-stu-id="f8080-187">If the operation succeeds, you will see the following:</span></span>  
  
    -   <span data-ttu-id="f8080-188">Word**成功**會出現在按鈕正上方的方塊中的紅色字型。</span><span class="sxs-lookup"><span data-stu-id="f8080-188">The word **Success** appears in red font in the box immediately above the buttons.</span></span>  
  
    -   <span data-ttu-id="f8080-189">您目的資料夾 C:\Demo\Reports 中會出現一個檔案。</span><span class="sxs-lookup"><span data-stu-id="f8080-189">A file appears in your destination folder, C:\Demo\Reports.</span></span> <span data-ttu-id="f8080-190">此檔案包含從文字**訊息主體**包裝在簡單的 XML 標記，由.NET 訊息佇列的程式庫中的方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-190">This file contains the text from the **Message body** box wrapped in simple XML tags by the .NET message queuing library.</span></span>  
  
     <span data-ttu-id="f8080-191">如果作業失敗，您將在按鈕正上方的方塊中看見錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8080-191">If the operation fails, you will see an error message in the box immediately above the buttons.</span></span>  
  
5.  <span data-ttu-id="f8080-192">再試一次**傳送精確**選項：</span><span class="sxs-lookup"><span data-stu-id="f8080-192">Try the **Send Exact** option:</span></span>  
  
    1.  <span data-ttu-id="f8080-193">選擇性地變更中的文字**訊息主體**方塊。</span><span class="sxs-lookup"><span data-stu-id="f8080-193">Optionally change the text in the **Message body** box.</span></span>  
  
    2.  <span data-ttu-id="f8080-194">按一下**傳送精確**。</span><span class="sxs-lookup"><span data-stu-id="f8080-194">Click **Send exact**.</span></span>  
  
     <span data-ttu-id="f8080-195">如果作業成功，您會看到下列項目：</span><span class="sxs-lookup"><span data-stu-id="f8080-195">If the operation succeeds, you will see the following:</span></span>  
  
    -   <span data-ttu-id="f8080-196">Word**成功**會出現在按鈕正上方的方塊中的紅色字型。</span><span class="sxs-lookup"><span data-stu-id="f8080-196">The word **Success** appears in red font in the box immediately above the buttons.</span></span>  
  
    -   <span data-ttu-id="f8080-197">您目的資料夾 C:\Demo\Reports 中會出現一個檔案。</span><span class="sxs-lookup"><span data-stu-id="f8080-197">A file appears in your destination folder, C:\Demo\Reports.</span></span> <span data-ttu-id="f8080-198">此檔案包含從文字**訊息主體**方塊出現在文字方塊中的相同。</span><span class="sxs-lookup"><span data-stu-id="f8080-198">This file contains the text from the **Message body** box exactly as it appears in the text box.</span></span>  
  
     <span data-ttu-id="f8080-199">如果作業失敗，您將在按鈕正上方的方塊中看見錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8080-199">If the operation fails, you will see an error message in the box immediately above the buttons.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8080-200">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8080-200">See Also</span></span>  
 [<span data-ttu-id="f8080-201">配接器範例 - 用法</span><span class="sxs-lookup"><span data-stu-id="f8080-201">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)