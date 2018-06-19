---
title: 大型訊息至 MSMQ |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fb87b46-5656-42c0-be99-8ab66e51bb4d
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 008e6c2d775fc5d46977ca4672b6d3376349b3f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976108"
---
# <a name="large-message-to-msmq"></a><span data-ttu-id="6c464-102">用於 MSMQ 的大型訊息</span><span class="sxs-lookup"><span data-stu-id="6c464-102">Large Message to MSMQ</span></span>
<span data-ttu-id="6c464-103">大型的訊息至 MSMQ 範例示範如何傳送的.xml 文件大於 4 mb 從 Message Queuing (也稱為 MSMQ) BizTalk MSMQ 配接器使用**MQSendLargeMessage**藉由應用程式開發介面MQRTLarge.dll。</span><span class="sxs-lookup"><span data-stu-id="6c464-103">The Large Message to MSMQ sample demonstrates how to send an .xml document larger than 4 megabytes (MB) from Message Queuing (also known as MSMQ) to the BizTalk MSMQ adapter by using the **MQSendLargeMessage** API implemented by MQRTLarge.dll.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="6c464-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="6c464-104">What This Sample Does</span></span>  
 <span data-ttu-id="6c464-105">範例的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="6c464-105">The sample works as follows:</span></span>  
  
1.  <span data-ttu-id="6c464-106">使用者使用 SendLargeMessage.exe，將大型.xml 檔案傳送至本機電腦上的佇列。</span><span class="sxs-lookup"><span data-stu-id="6c464-106">A user uses SendLargeMessage.exe to send a large .xml file to a queue on a local computer.</span></span>  
  
2.  <span data-ttu-id="6c464-107">BizTalk Server 會從佇列接收大型.xml 檔案，並將它複製到本機目錄。</span><span class="sxs-lookup"><span data-stu-id="6c464-107">BizTalk Server receives the large .xml file from the queue and copies it to a local directory.</span></span>  
  
 <span data-ttu-id="6c464-108">訊息佇列中的許多作業都是非同步的。</span><span class="sxs-lookup"><span data-stu-id="6c464-108">Many operations in Message Queuing are asynchronous.</span></span> <span data-ttu-id="6c464-109">也就是說，許多 MSMQ API 呼叫 (例如， **MQSendLargeMessage**) 傳回給呼叫端要求的作業完全完成之前。</span><span class="sxs-lookup"><span data-stu-id="6c464-109">That is, many MSMQ API calls (for example, **MQSendLargeMessage**) return to the caller before the requested operation has fully completed.</span></span>  
  
 <span data-ttu-id="6c464-110">MSMQ 提供一項機制，會在作業全部完成之後將回應傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c464-110">MSMQ provides a mechanism to deliver feedback to the application after the operation has completed.</span></span> <span data-ttu-id="6c464-111">這個機制需要用到「管理佇列」。</span><span class="sxs-lookup"><span data-stu-id="6c464-111">This mechanism involves the use of an "Admin Queue."</span></span> <span data-ttu-id="6c464-112">MSMQ 管理佇列中訊息的形式，傳回的意見反應。</span><span class="sxs-lookup"><span data-stu-id="6c464-112">MSMQ returns feedback in the form of a message in the Admin Queue.</span></span> <span data-ttu-id="6c464-113">當進行原始 MSMQ API 呼叫時，便會指定 MSMQ 要將回應傳送所至的管理佇列。</span><span class="sxs-lookup"><span data-stu-id="6c464-113">The Admin Queue to which MSMQ will return feedback is specified when the original MSMQ API call is made.</span></span> <span data-ttu-id="6c464-114">因此，範例中，當傳送訊息，使用**MQSendLargeMessage** API，應用程式可以指定管理佇列的名稱使用**PROPID_M_ADMIN_QUEUE**訊息在訊息上的屬性傳入呼叫**MQSendLargeMessage**。</span><span class="sxs-lookup"><span data-stu-id="6c464-114">So, for example, when sending a message using the **MQSendLargeMessage** API, the application can specify the name of an Admin Queue by using the **PROPID_M_ADMIN_QUEUE** message property on the message passed in the call to **MQSendLargeMessage**.</span></span> <span data-ttu-id="6c464-115">即使應用程式可能取得成功的傳回碼**MQSendLargeMessage**呼叫時，如果後續訊息傳送作業失敗，MSMQ 訊息寫入該效果指定管理佇列。</span><span class="sxs-lookup"><span data-stu-id="6c464-115">Even though the application may get a successful return code on the **MQSendLargeMessage** call, if the message send operation subsequently fails, MSMQ writes a message to that effect to the specified Admin Queue.</span></span>  
  
 <span data-ttu-id="6c464-116">如果應用程式未指定管理佇列，傳送失敗將會導致訊息遺失而無法擷取診斷資訊，訊息將會毫無跡象地消失。</span><span class="sxs-lookup"><span data-stu-id="6c464-116">If the application does not specify an Admin Queue, a send failure results in the message being lost and no diagnostics captured — in effect, the message disappears without any evidence.</span></span> <span data-ttu-id="6c464-117">MSMQ 中的錯誤情況的數目可能會造成這種情形，例如，非交易式傳送至異動式佇列。</span><span class="sxs-lookup"><span data-stu-id="6c464-117">A number of error situations in MSMQ can cause this to happen, for example, doing a non-transactional send to a transactional queue.</span></span>  
  
 <span data-ttu-id="6c464-118">在此範例的內容，是很重要的程式碼呼叫中指定交易類型**MQSendLargeMessage**這與指定傳送訊息佇列的交易支援一致。</span><span class="sxs-lookup"><span data-stu-id="6c464-118">In the context of this sample, it is important that the code specify a transaction type in the call to **MQSendLargeMessage** that is consistent with the transaction support specified for the queue to which the message is sent.</span></span> <span data-ttu-id="6c464-119">如果未進行此設定，而且如果沒有指定管理佇列是 （在此情況下在此範例中），MSMQ 捨棄傳送的訊息，它確實會留下任何跡象 （也就是沒有錯誤碼傳回至應用程式，而不將診斷資訊寫入事件記錄檔依此類推)。</span><span class="sxs-lookup"><span data-stu-id="6c464-119">If this is not done and if no Admin Queue is specified (as is the case in this sample), then MSMQ discards the sent message with no indication that it has done so (that is, no error code returned to the application, no diagnostics written to the event log, and so on).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="6c464-120">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="6c464-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="6c464-121">\<範例路徑\>\AdaptersUsage\MSMQLarge</span><span class="sxs-lookup"><span data-stu-id="6c464-121">\<Samples Path\>\AdaptersUsage\MSMQLarge</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c464-122">如果使用 64 位元版本的 Windows 和 BizTalk Server，將範例安裝在**C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6c464-122">If using a 64-bit version of Windows and BizTalk Server, the sample will be installed in the **C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge** folder.</span></span>  <span data-ttu-id="6c464-123">請注意這項變更，在此文件中使用的其他指示**C:\Program Files**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6c464-123">Note this change for any other instructions in this document using the **C:\Program Files** folder.</span></span>  
  
 <span data-ttu-id="6c464-124">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="6c464-124">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="6c464-125">**檔案**</span><span class="sxs-lookup"><span data-stu-id="6c464-125">**File**</span></span>|<span data-ttu-id="6c464-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="6c464-126">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="6c464-127">**MQRTLarge.dll**</span><span class="sxs-lookup"><span data-stu-id="6c464-127">**MQRTLarge.dll**</span></span>|<span data-ttu-id="6c464-128">提供原生訊息佇列的附加元件。</span><span class="sxs-lookup"><span data-stu-id="6c464-128">Provides an add-on for native message queuing.</span></span> <span data-ttu-id="6c464-129">公開**MQSendLargeMessage**和**MQReceiveLargeMessage**應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="6c464-129">Exposes the **MQSendLargeMessage** and **MQReceiveLargeMessage** APIs.</span></span><br /><br /> <span data-ttu-id="6c464-130">若要存取 MQRTLarge.dll 的 64 位元版本，您必須在 64 位元版本的 Windows 上安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="6c464-130">You must install BizTalk Server on a 64-bit version of Windows in order to access the 64-bit version of MQRTLarge.dll.</span></span><br /><br /> <span data-ttu-id="6c464-131">MSMQ 未搭配 BizTalk Server 解決方案，MQRTLarge.dll 可能仍正常運作。</span><span class="sxs-lookup"><span data-stu-id="6c464-131">For an MSMQ solution without BizTalk Server, the MQRTLarge.dll may still function correctly.</span></span> <span data-ttu-id="6c464-132">不過，這不是建議的設定，Microsoft 支援，而且如果在 BizTalk Server 環境之外使用，可能會發生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="6c464-132">However, this is not a recommended configuration that Microsoft supports, and unexpected results may occur if used outside of the BizTalk Server environment.</span></span>|  
|||  
|<span data-ttu-id="6c464-133">**LargeMessages.sln**</span><span class="sxs-lookup"><span data-stu-id="6c464-133">**LargeMessages.sln**</span></span>|<span data-ttu-id="6c464-134">提供 Visual Studio 解決方案以建立範例中使用的 SendLargeMessage 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="6c464-134">Provides a Visual Studio solution to create the SendLargeMessage executable used in the sample.</span></span>|  
|<span data-ttu-id="6c464-135">**XMLCreator.sln**</span><span class="sxs-lookup"><span data-stu-id="6c464-135">**XMLCreator.sln**</span></span>|<span data-ttu-id="6c464-136">提供 Visual Studio 解決方案來建立 XMLCreator 可執行檔，以產生 SDK 範例的測試 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="6c464-136">Provides a Visual Studio solution to create the XMLCreator executable to generate a test .xml file for the SDK sample.</span></span>|  
  
## <a name="configure-biztalk-and-create-the-msmq-queue"></a><span data-ttu-id="6c464-137">將 BizTalk 設定，並建立 MSMQ 佇列</span><span class="sxs-lookup"><span data-stu-id="6c464-137">Configure BizTalk and Create the MSMQ Queue</span></span>  
 <span data-ttu-id="6c464-138">請確定 Visual Studio、 Microsoft Message Queuing 與 BizTalk Server 安裝。</span><span class="sxs-lookup"><span data-stu-id="6c464-138">Ensure that Visual Studio, Microsoft Message Queuing, and BizTalk Server installed.</span></span>  
  
#### <a name="to-configure-biztalk-server"></a><span data-ttu-id="6c464-139">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6c464-139">To configure BizTalk Server</span></span>  
  
1.  <span data-ttu-id="6c464-140">在 Visual Studio 中開啟**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln**方案檔。</span><span class="sxs-lookup"><span data-stu-id="6c464-140">In Visual Studio, open the **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln** solution file.</span></span>  <span data-ttu-id="6c464-141">建立此範例。</span><span class="sxs-lookup"><span data-stu-id="6c464-141">Build the sample.</span></span>  
  
2.  <span data-ttu-id="6c464-142">建立**C:\Demo** BizTalk Server 將放置從 MSMQ 訊息目錄。</span><span class="sxs-lookup"><span data-stu-id="6c464-142">Create a **C:\Demo** directory where BizTalk Server will place the messages from MSMQ.</span></span>  
  
3.  <span data-ttu-id="6c464-143">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6c464-143">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="6c464-144">建立傳送埠將訊息寫入範例。</span><span class="sxs-lookup"><span data-stu-id="6c464-144">Create a send port for the sample to write the message.</span></span>  
  
    -   <span data-ttu-id="6c464-145">展開**BizTalk 群組**，依序展開**應用程式**，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="6c464-145">Expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, right-click **Send Ports**, click **New**, and then click **Static One-Way Send Port**.</span></span>  
  
5.  <span data-ttu-id="6c464-146">在**靜態單向傳送埠屬性**對話方塊方塊中，設定之連接埠名稱**MySendPort**。</span><span class="sxs-lookup"><span data-stu-id="6c464-146">In the **Static One-Way Send Port Properties** dialog box, set the name of the port to **MySendPort**.</span></span>  
  
6.  <span data-ttu-id="6c464-147">將傳輸類型設定為**檔案**。</span><span class="sxs-lookup"><span data-stu-id="6c464-147">Set the transport type to **File**.</span></span>  
  
7.  <span data-ttu-id="6c464-148">按一下**設定** 按鈕以開啟**File 傳輸屬性**表單。</span><span class="sxs-lookup"><span data-stu-id="6c464-148">Click the **Configure** button to open the **File Transport Properties** form.</span></span> <span data-ttu-id="6c464-149">輸入**C:\Demo**中**目的地資料夾**。</span><span class="sxs-lookup"><span data-stu-id="6c464-149">Enter **C:\Demo** in **Destination Folder**.</span></span> <span data-ttu-id="6c464-150">請確認主控件執行個體識別具有存取權 C:\Demo 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6c464-150">Ensure that the host instance identity has access to the C:\Demo folder.</span></span>  
  
8.  <span data-ttu-id="6c464-151">請確認**檔案名稱**設 **%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="6c464-151">Ensure that **File Name** is set to **%MessageID%.xml**.</span></span> <span data-ttu-id="6c464-152">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6c464-152">Click **OK**.</span></span>  
  
9. <span data-ttu-id="6c464-153">按一下 **[篩選]**。</span><span class="sxs-lookup"><span data-stu-id="6c464-153">Click **Filters**.</span></span>  
  
    1.  <span data-ttu-id="6c464-154">設定**屬性**至**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="6c464-154">Set **Property** to **BTS.ReceivePortName**.</span></span>  
  
    2.  <span data-ttu-id="6c464-155">設定**運算子**至 **=** 。</span><span class="sxs-lookup"><span data-stu-id="6c464-155">Set **Operator** to **=**.</span></span>  
  
    3.  <span data-ttu-id="6c464-156">設定**值**至**MyReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="6c464-156">Set **Value** to **MyReceivePort**.</span></span>  
  
    4.  <span data-ttu-id="6c464-157">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6c464-157">Click **OK**.</span></span>  
  
10. <span data-ttu-id="6c464-158">建立接收埠以接受來自 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="6c464-158">Create a receive port to accept the message from MSMQ.</span></span>  
  
    1.  <span data-ttu-id="6c464-159">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="6c464-159">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Ports**.</span></span>  
  
    2.  <span data-ttu-id="6c464-160">按一下**新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="6c464-160">Click **New**, and then click **One-way Receive Port**.</span></span>  
  
11. <span data-ttu-id="6c464-161">在**接收埠屬性**對話方塊方塊中，設定之連接埠名稱**MyReceivePort**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6c464-161">In the **Receive Port Properties** dialog box, set the name of the port to **MyReceivePort**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="6c464-162">建立範例的接收埠之後，您必須建立一個接收位置。</span><span class="sxs-lookup"><span data-stu-id="6c464-162">After creating a receive port for the sample, you must create a receive location.</span></span>  
  
    1.  <span data-ttu-id="6c464-163">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="6c464-163">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Locations**.</span></span>  
  
    2.  <span data-ttu-id="6c464-164">按一下**新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="6c464-164">Click **New**, and then click **One-way Receive Location**.</span></span>  
  
    3.  <span data-ttu-id="6c464-165">設定接收位置的名稱**MSMQReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="6c464-165">Set the name of the receive location to **MSMQReceiveLocation**.</span></span>  
  
    4.  <span data-ttu-id="6c464-166">在**選取接收埠**對話方塊中，選取**MyReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="6c464-166">In the **Select a Receive Port** dialog box, select **MyReceivePort**.</span></span>  
  
    5.  <span data-ttu-id="6c464-167">在**接收位置屬性** 對話方塊中，將**傳輸類型**至**MSMQ**。</span><span class="sxs-lookup"><span data-stu-id="6c464-167">In the **Receive Location Properties** dialog box, set **Transport Type** to **MSMQ**.</span></span>  
  
    6.  <span data-ttu-id="6c464-168">在**位址 (URI)** 區段中，按一下**設定**開啟**MSMQ 傳輸屬性**表單。</span><span class="sxs-lookup"><span data-stu-id="6c464-168">In the **Address (URI)** section, click **Configure** to open the **MSMQ Transport Properties** form.</span></span> <span data-ttu-id="6c464-169">設定**佇列**至**localhost\private$ \test**。</span><span class="sxs-lookup"><span data-stu-id="6c464-169">Set **Queue** to **localhost\private$\test**.</span></span>  
  
    7.  <span data-ttu-id="6c464-170">設定**交易式**至`True`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6c464-170">Set **Transactional** to `True`, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="6c464-171">您必須讓連接埠和接收位置可供使用，透過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6c464-171">You must make the ports and receive locations available for use through the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    1.  <span data-ttu-id="6c464-172">以滑鼠右鍵按一下**MySendPort**，然後按一下 **登錄**。</span><span class="sxs-lookup"><span data-stu-id="6c464-172">Right-click **MySendPort**, and then click **Enlist**.</span></span>  
  
    2.  <span data-ttu-id="6c464-173">以滑鼠右鍵按一下**MySendPort**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="6c464-173">Right-click **MySendPort**, and then click **Start**.</span></span>  
  
    3.  <span data-ttu-id="6c464-174">以滑鼠右鍵按一下**MSMQReceiveLocation**，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="6c464-174">Right-click **MSMQReceiveLocation**, and then click **Enable**.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-server"></a><span data-ttu-id="6c464-175">若要在 Windows Server 中建立 MSMQ 佇列</span><span class="sxs-lookup"><span data-stu-id="6c464-175">To create the MSMQ queue in Windows Server</span></span>
  
1.  <span data-ttu-id="6c464-176">按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下 **管理**。</span><span class="sxs-lookup"><span data-stu-id="6c464-176">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="6c464-177">展開**功能**節點。</span><span class="sxs-lookup"><span data-stu-id="6c464-177">Expand the **Features** node.</span></span>  
  
3.  <span data-ttu-id="6c464-178">展開**訊息佇列**節點。</span><span class="sxs-lookup"><span data-stu-id="6c464-178">Expand the **Message Queuing** node.</span></span>  
  
4.  <span data-ttu-id="6c464-179">以滑鼠右鍵按一下**私用佇列**節點中，按一下 **新增**，然後按一下 **私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="6c464-179">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
5.  <span data-ttu-id="6c464-180">在下**佇列名稱**，輸入**測試**。</span><span class="sxs-lookup"><span data-stu-id="6c464-180">Under **Queue name**, enter **test**.</span></span> <span data-ttu-id="6c464-181">請確認**交易式**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6c464-181">Ensure that the **Transactional** check box is selected.</span></span>  
  
6.  <span data-ttu-id="6c464-182">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6c464-182">Click **OK**.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows"></a><span data-ttu-id="6c464-183">若要在 Windows 中建立 MSMQ 佇列</span><span class="sxs-lookup"><span data-stu-id="6c464-183">To create the MSMQ queue in Windows</span></span> 
  
1.  <span data-ttu-id="6c464-184">按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下 **管理**。</span><span class="sxs-lookup"><span data-stu-id="6c464-184">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="6c464-185">展開**服務和應用程式**，然後展開**訊息佇列**節點。</span><span class="sxs-lookup"><span data-stu-id="6c464-185">Expand **Services and Applications**, and then expand the **Message Queuing** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c464-186">如果**訊息佇列**未安裝在電腦中，移至**控制台 > 程式 > 程式和功能**，然後選取**開啟或關閉 Windows 功能**。</span><span class="sxs-lookup"><span data-stu-id="6c464-186">If **Message Queuing** is not installed in the computer, go to **Control Panel > Programs > Programs and Features**, and then select **Turn Windows features on or off**.</span></span> <span data-ttu-id="6c464-187">檢查下的所有功能**Microsoft Message Queue (MSMQ) 伺服器**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6c464-187">Check all the features under **Microsoft Message Queue (MSMQ) Server**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6c464-188">以滑鼠右鍵按一下**私用佇列**節點中，按一下 **新增**，然後按一下 **私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="6c464-188">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
4.  <span data-ttu-id="6c464-189">在下**佇列名稱**，輸入**測試**。</span><span class="sxs-lookup"><span data-stu-id="6c464-189">Under **Queue name**, enter **test**.</span></span> <span data-ttu-id="6c464-190">請確認**交易式**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6c464-190">Ensure that the **Transactional** check box is selected.</span></span>  
  
5.  <span data-ttu-id="6c464-191">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6c464-191">Click **OK**.</span></span>  
  
## <a name="creating-a-test-file-and-running-the-sample"></a><span data-ttu-id="6c464-192">建立測試檔案並執行範例</span><span class="sxs-lookup"><span data-stu-id="6c464-192">Creating a Test File and Running the Sample</span></span>  
  
#### <a name="to-create-a-large-test-file"></a><span data-ttu-id="6c464-193">若要建立大型的測試檔案</span><span class="sxs-lookup"><span data-stu-id="6c464-193">To create a large test file</span></span>  
  
1.  <span data-ttu-id="6c464-194">在 Visual Studio 中開啟方案**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**。</span><span class="sxs-lookup"><span data-stu-id="6c464-194">In Visual Studio, open the solution **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**.</span></span>  
  
2.  <span data-ttu-id="6c464-195">建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="6c464-195">Build and run the project.</span></span>  
  
3.  <span data-ttu-id="6c464-196">在下**XML 主體**，型別**這是測試訊息**。</span><span class="sxs-lookup"><span data-stu-id="6c464-196">Under **XML Body**, type **This is a test message**.</span></span>  
  
4.  <span data-ttu-id="6c464-197">在下**的次數来複製的 XML 主體 #**，型別`250000`。</span><span class="sxs-lookup"><span data-stu-id="6c464-197">Under **# of times to copy XML body**, type `250000`.</span></span>  
  
5.  <span data-ttu-id="6c464-198">在下**XML 檔案位置**，型別`C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`。</span><span class="sxs-lookup"><span data-stu-id="6c464-198">Under **XML File Location**, type `C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`.</span></span>  
  
6.  <span data-ttu-id="6c464-199">按一下**建立 XML**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6c464-199">Click **Create XML**, and then click **OK**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="6c464-200">執行範例</span><span class="sxs-lookup"><span data-stu-id="6c464-200">To run the sample</span></span>  
  
1.  <span data-ttu-id="6c464-201">開啟命令提示字元，然後將目錄切換至**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**。</span><span class="sxs-lookup"><span data-stu-id="6c464-201">Open a command prompt and change directory to **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**.</span></span>  
  
2.  <span data-ttu-id="6c464-202">在命令提示字元中，執行**SendLargeMessage.exe**。</span><span class="sxs-lookup"><span data-stu-id="6c464-202">At the command prompt, run **SendLargeMessage.exe**.</span></span> <span data-ttu-id="6c464-203">SendLargeMessage 可執行檔接受兩個變數，第一個是 MSMQ 佇列的位置，第二個是要傳送的.xml 檔案的位置：</span><span class="sxs-lookup"><span data-stu-id="6c464-203">The SendLargeMessage executable accepts two variables — the first is the location of the MSMQ queue, and the second is the location of the .xml file to send:</span></span>  
  
    ```  
    DIRECT=OS:localhost\private$\Test  "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml"  
    ```  
  
3.  <span data-ttu-id="6c464-204">確認已在 BizTalk Server 電腦上建立相同大小的檔案**C:\Demo**目錄。</span><span class="sxs-lookup"><span data-stu-id="6c464-204">Verify that a file of the same size was created on the BizTalk Server computer in the **C:\Demo** directory.</span></span> <span data-ttu-id="6c464-205">這是您在 MySendPort 傳送埠中找到的目錄。</span><span class="sxs-lookup"><span data-stu-id="6c464-205">This is the directory you identified in the MySendPort send port.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="6c464-206">註解</span><span class="sxs-lookup"><span data-stu-id="6c464-206">Comments</span></span>  
 <span data-ttu-id="6c464-207">SendLargeMessage.exe 參考**LargeMessages**又參考 BizTalk 訊息佇列大型訊息延伸模組 (MQRTLarge.dll) API 的 API。</span><span class="sxs-lookup"><span data-stu-id="6c464-207">SendLargeMessage.exe references the **LargeMessages** API, which in turn references the BizTalk Message Queuing Large Message Extension (MQRTLarge.dll) API.</span></span> <span data-ttu-id="6c464-208">訊息佇列大型訊息延伸模組 API 是原生訊息佇列的附加元件可讓處理大於 4 MB 限制的原生訊息佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="6c464-208">The Message Queuing Large Message Extension API is an add-on for native message queuing that enables the processing of messages larger than the 4 MB limit of native message queuing.</span></span>  
  
 <span data-ttu-id="6c464-209">這個範例會使用**MQSendLargeMessage** API 並公開 API 的.NET framework 使用**LargeMessages**應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="6c464-209">This sample uses the **MQSendLargeMessage** API and exposes the API to the .NET Framework by using the **LargeMessages** API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c464-210">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c464-210">See Also</span></span>  
 <span data-ttu-id="6c464-211">[BizTalk 訊息佇列大型訊息延伸模組](../core/biztalk-message-queuing-large-message-extension.md) </span><span class="sxs-lookup"><span data-stu-id="6c464-211">[BizTalk Message Queuing Large Message Extension](../core/biztalk-message-queuing-large-message-extension.md) </span></span>  
 [<span data-ttu-id="6c464-212">配接器範例 - 用法</span><span class="sxs-lookup"><span data-stu-id="6c464-212">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)