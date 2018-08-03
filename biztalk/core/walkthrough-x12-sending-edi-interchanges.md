---
title: 逐步解說 (X12)： 傳送 EDI 交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05533821-b9eb-44bc-af65-b6fb0b545137
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 032fffbe22d397597288d11590995ec5c74708d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007559"
---
# <a name="walkthrough-x12-sending-edi-interchanges"></a><span data-ttu-id="3606a-102">逐步解說 (X12)：傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3606a-102">Walkthrough (X12): Sending EDI Interchanges</span></span>
<span data-ttu-id="3606a-103">本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可傳送 EDI 交換的解決方案。</span><span class="sxs-lookup"><span data-stu-id="3606a-103">This walkthrough provides a set of step-by-step procedures that creates a solution for sending EDI interchanges using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="3606a-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="3606a-104">Prerequisites</span></span>  
 <span data-ttu-id="3606a-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="3606a-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  

## <a name="how-the-solution-sends-edi-interchanges"></a><span data-ttu-id="3606a-106">解決方案如何傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3606a-106">How the Solution Sends EDI Interchanges</span></span>  
 <span data-ttu-id="3606a-107">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3606a-107">The solution will do the following:</span></span>  

1.  <span data-ttu-id="3606a-108">單向 FILE 接收埠會從 Fabrikam 接收 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-108">A one-way FILE receive port receives an EDI message from Fabrikam.</span></span>  

2.  <span data-ttu-id="3606a-109">這個接收埠會使用 EdiReceive 管線來檢查訊息並將其轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="3606a-109">Using the EdiReceive pipeline, the receive port checks the message and converts it into XML.</span></span> <span data-ttu-id="3606a-110">然後接收埠會將測試訊息拖曳到 MeassageBox。</span><span class="sxs-lookup"><span data-stu-id="3606a-110">The receive port then drops the test message into the MeassageBox.</span></span>  

3.  <span data-ttu-id="3606a-111">靜態的單向傳送埠會從 MessageBox 拾取 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-111">A static one-way send port picks up the XML message from the MessageBox.</span></span>  

4.  <span data-ttu-id="3606a-112">靜態的單向傳送埠會依據訊息結構描述驗證 EDI 訊息、序列化 EDI 訊息成 EDI 交換，然後再將 EDI 訊息傳送到交易夥伴 Contoso 的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="3606a-112">The static one-way send port validates the EDI message against the message schema, serializes the EDI message into an EDI interchange, and then sends the EDI message to the trading partner Contoso's local folder.</span></span>  

## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="3606a-113">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="3606a-113">The Functionality in this Solution</span></span>  
 <span data-ttu-id="3606a-114">本逐步解說使用下列功能：</span><span class="sxs-lookup"><span data-stu-id="3606a-114">This walkthrough uses the following functionality:</span></span>  

- <span data-ttu-id="3606a-115">本逐步解說中不會測試通知的接收。</span><span class="sxs-lookup"><span data-stu-id="3606a-115">Receiving an acknowledgment is not tested in this walkthrough.</span></span> <span data-ttu-id="3606a-116">若要了解如何接收通知，請參閱示範[逐步解說 (X12)： 接收 EDI 交換，並將傳送回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)</span><span class="sxs-lookup"><span data-stu-id="3606a-116">To understand how to receive an acknowledgment, see demonstrated [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)</span></span>  

- <span data-ttu-id="3606a-117">這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。</span><span class="sxs-lookup"><span data-stu-id="3606a-117">The solution is designed for interchanges using X12 encoding, not EDIFACT encoding.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="3606a-118">用於 HIPAA 與 EDIFACT 編碼的組態，與用於 X12 編碼的組態近乎相同。</span><span class="sxs-lookup"><span data-stu-id="3606a-118">The configuration used for HIPAA and for EDIFACT encoding is closely parallel to that used for X12 encoding.</span></span>  

- <span data-ttu-id="3606a-119">將針對外寄交換執行 EDI 類型和擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="3606a-119">EDI type and extended validation will be performed on the outgoing interchange.</span></span>  

- <span data-ttu-id="3606a-120">這個解決方案使用靜態單向傳送埠與 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="3606a-120">The solution uses a static one-way send port with a FILE transport type.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="3606a-121">您可以使用靜態雙向傳送埠以傳送交換並接收通知，來取代靜態單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3606a-121">Instead of a static one-way send port, you could use a static two-way send port to send the interchange and receive the acknowledgment.</span></span> <span data-ttu-id="3606a-122">也可以使用動態單向傳送埠以傳送交換。</span><span class="sxs-lookup"><span data-stu-id="3606a-122">You could also use a dynamic one-way send port to send the interchange.</span></span> <span data-ttu-id="3606a-123">如需有關如何使用動態傳送埠的詳細資訊，請參閱 <<c0> [ 設定動態傳送埠以傳送 EDI 交換和通知](../core/configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments.md)。</span><span class="sxs-lookup"><span data-stu-id="3606a-123">For more information on using a dynamic send port, see [Configuring a Dynamic Send Port to Send EDI Interchanges and Acknowledgments](../core/configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments.md).</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="3606a-124">您可以使用 HTTP 配接器和 AS2 傳輸。</span><span class="sxs-lookup"><span data-stu-id="3606a-124">You can use an HTTP adapter and AS2 transport.</span></span> <span data-ttu-id="3606a-125">如需有關這種方式的詳細資訊，請參閱[逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)或是[逐步解說 (AS2): 使用非同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="3606a-125">For more information on doing so, see [Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md) or [Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).</span></span>  

- <span data-ttu-id="3606a-126">EDI 報告將會啟用，並會儲存交易集，以從交換狀態報告進行檢視。</span><span class="sxs-lookup"><span data-stu-id="3606a-126">EDI reporting will be enabled, and transaction sets will be saved for viewing from the interchange status report.</span></span>  

- <span data-ttu-id="3606a-127">基於測試的目的，解決方案使用接收位置以接收測試訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-127">For testing purposes, the solution uses a receive location to receive a test message.</span></span>  

  <span data-ttu-id="3606a-128">下圖顯示這個解決方案的架構，其中使用靜態單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3606a-128">The following figure shows the architecture for this solution, which uses a static one-way send port.</span></span>  

  <span data-ttu-id="3606a-129">![傳送 EDI 交換](../core/media/6915024c-687c-4076-a730-3f7b9d2db7fb.gif "6915024c-687c-4076-a730-3f7b9d2db7fb")</span><span class="sxs-lookup"><span data-stu-id="3606a-129">![Sending EDI interchanges](../core/media/6915024c-687c-4076-a730-3f7b9d2db7fb.gif "6915024c-687c-4076-a730-3f7b9d2db7fb")</span></span>  

## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="3606a-130">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="3606a-130">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="3606a-131">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3606a-131">The procedures required for this solution include the following:</span></span>  

- <span data-ttu-id="3606a-132">將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用該結構描述來處理輸出交換。</span><span class="sxs-lookup"><span data-stu-id="3606a-132">Add the required message schema(s) to a BizTalk project, and then build and deploy the project, making the schemas available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the outbound interchange.</span></span>  

- <span data-ttu-id="3606a-133">建立接收埠和位置以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="3606a-133">Create a receive port and location for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the EDI interchange.</span></span> <span data-ttu-id="3606a-134">此接收位置繫結至檔案資料夾，而 Fabrikam 會在此資料夾放置要傳送給 Contoso 的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="3606a-134">This receive location is tied to the file folder where Fabrikam drops the EDI interchange to be sent to Contoso.</span></span> <span data-ttu-id="3606a-135">接收位置將使用 EdiReceive 接收管線。</span><span class="sxs-lookup"><span data-stu-id="3606a-135">The receive location will use an EdiReceive receive pipeline.</span></span>  

- <span data-ttu-id="3606a-136">建立傳送埠以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 EDI 交換至 Contoso。</span><span class="sxs-lookup"><span data-stu-id="3606a-136">Create a send port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send the EDI interchange to Contoso.</span></span> <span data-ttu-id="3606a-137">在此逐步解說中，您將建立靜態單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3606a-137">In this walkthrough, you will create a static one-way send port.</span></span>  

- <span data-ttu-id="3606a-138">為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="3606a-138">Create a party (trading partner) for both Fabrikam and Contoso.</span></span>  

- <span data-ttu-id="3606a-139">分別為兩個交易夥伴建立商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="3606a-139">Create a business profile each for both the trading partners.</span></span>  

- <span data-ttu-id="3606a-140">設定讓訊息收得到的 EDI 屬性，以建立這兩個設定檔之間的協議。</span><span class="sxs-lookup"><span data-stu-id="3606a-140">Create an agreement between the two profiles by configuring the EDI properties for the message to be received.</span></span>  

- <span data-ttu-id="3606a-141">使用測試 EDI 交換以測試逐步解說。</span><span class="sxs-lookup"><span data-stu-id="3606a-141">Test the walkthrough using a test EDI interchange.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="3606a-142">對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="3606a-142">For a test message, you can use the SamplePO.txt file that is used in the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="3606a-143">該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3606a-143">That file is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ folder.</span></span> <span data-ttu-id="3606a-144">這是 X12 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-144">This is an X12 850 message.</span></span>  

### <a name="configuring-the-walkthrough"></a><span data-ttu-id="3606a-145">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="3606a-145">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="3606a-146">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="3606a-146">This section describes the procedures to configure the walkthrough.</span></span>  

##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="3606a-147">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="3606a-147">To deploy the message schema</span></span>  

1. <span data-ttu-id="3606a-148">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3606a-148">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-149">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="3606a-149">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="3606a-150">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="3606a-150">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  

2. <span data-ttu-id="3606a-151">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="3606a-151">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="3606a-152">移至結構描述所在的資料夾 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI，然後按兩下該結構描述。</span><span class="sxs-lookup"><span data-stu-id="3606a-152">Move to the folder that your schema is in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI, and then double-click your schema.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-153">如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾結構描述解壓縮至預設資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="3606a-153">If the EDI schemas have not been unzipped into the \XSD_Schema\EDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the \XSD_Schema\EDI folder to unzip the schemas into the default folder.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="3606a-154">如果您使用 EDI 介面開發人員教學課程中所用的 SamplePO.txt 檔案，則必須使用隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾中的 X12_00401_850.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="3606a-154">If you use the SamplePO.txt file that is used in the EDI Interface Developer tutorial, you must use the X12_00401_850.xsd schema that is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI folder.</span></span> <span data-ttu-id="3606a-155">您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。</span><span class="sxs-lookup"><span data-stu-id="3606a-155">You must not use the X12 850 schema in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema folder.</span></span>  

3. <span data-ttu-id="3606a-156">將組件金鑰檔案加入專案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="3606a-156">Add the assembly key file to the project, and then build and deploy the assembly.</span></span>  

##### <a name="to-create-a-one-way-receive-port-for-fabrikam-to-receive-the-edi-interchange"></a><span data-ttu-id="3606a-157">建立單向接收埠 (供 Fabrikam 使用) 以接收 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3606a-157">To create a one-way receive port (for Fabrikam) to receive the EDI interchange</span></span>  

1. <span data-ttu-id="3606a-158">在 Windows 檔案總管中，建立本機資料夾，以接收交換。</span><span class="sxs-lookup"><span data-stu-id="3606a-158">In Windows Explorer, create a local folder to receive the interchange in.</span></span>  

2. <span data-ttu-id="3606a-159">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="3606a-159">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.</span></span>  

3. <span data-ttu-id="3606a-160">將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="3606a-160">Name the receive port, and then click **Receive Locations** in the console tree.</span></span>  

4. <span data-ttu-id="3606a-161">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="3606a-161">Click **New**.</span></span>  

5. <span data-ttu-id="3606a-162">接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="3606a-162">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  

6. <span data-ttu-id="3606a-163">輸入所需的資料夾**接收資料夾**，然後輸入 **\*.txt**對於檔案遮罩。</span><span class="sxs-lookup"><span data-stu-id="3606a-163">Enter a folder for **Receive folder**, and enter **\*.txt** for the file mask.</span></span>  

7. <span data-ttu-id="3606a-164">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="3606a-164">Click **OK**.</span></span>  

8. <span data-ttu-id="3606a-165">針對**接收管線**，選取**EdiReceive**。</span><span class="sxs-lookup"><span data-stu-id="3606a-165">For **Receive pipeline**, select **EdiReceive**.</span></span>  

9. <span data-ttu-id="3606a-166">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="3606a-166">Click **OK**, and then click **OK** again.</span></span>  

10. <span data-ttu-id="3606a-167">在主控台樹狀目錄中，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="3606a-167">In the console tree, click **Receive Locations**.</span></span> <span data-ttu-id="3606a-168">在 **接收位置**窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="3606a-168">In the **Receive Locations** pane, right-click your receive location, and then click **Enable**.</span></span>  

##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a><span data-ttu-id="3606a-169">建立靜態單向傳送埠 (供 Contoso 使用) 以傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3606a-169">To create a static one-way send port (for Contoso) to send the EDI interchange</span></span>  

1. <span data-ttu-id="3606a-170">在 Windows 檔案總管中，建立本機資料夾，以便將 EDI 交換傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="3606a-170">In Windows Explorer, create a local folder to send the EDI interchange to.</span></span>  

2. <span data-ttu-id="3606a-171">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="3606a-171">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  

3. <span data-ttu-id="3606a-172">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="3606a-172">In the **Send Port Properties** dialog box, name the send port.</span></span>  

4. <span data-ttu-id="3606a-173">在 **傳輸**區段中，選取**型別**，例如**檔案**。</span><span class="sxs-lookup"><span data-stu-id="3606a-173">In the **Transport** section, select the **Type**, for example, **FILE**.</span></span>  

5. <span data-ttu-id="3606a-174">如果使用的檔案類型，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="3606a-174">If using a FILE type, click **Configure**.</span></span> <span data-ttu-id="3606a-175">在 **目的地資料夾**，瀏覽至要傳送交換的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3606a-175">In **Destination folder**, browse to a folder to send the interchange to.</span></span> <span data-ttu-id="3606a-176">針對**檔名**，輸入 **%MessageID%.edi**。</span><span class="sxs-lookup"><span data-stu-id="3606a-176">For **File name**, enter **%MessageID%.edi**.</span></span> <span data-ttu-id="3606a-177">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="3606a-177">Click **OK**.</span></span>  

6. <span data-ttu-id="3606a-178">在 **傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="3606a-178">In **Send pipeline**, select **EdiSend**.</span></span>  

7. <span data-ttu-id="3606a-179">在主控台樹狀目錄中，選取**篩選**，然後輸入要用來訂閱訊息的傳送埠的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="3606a-179">In the console tree, select **Filters**, and enter a filter expression for the send port to use to subscribe to the message.</span></span> <span data-ttu-id="3606a-180">例如，您可以使用將要接收原始測試訊息的接收位置做為篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="3606a-180">For example, you could use the receive location that will receive the original test message as a filter expression.</span></span> <span data-ttu-id="3606a-181">若要這樣做，**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 及針對**值**輸入您要建立的接收埠名稱接收來自 Fabrikam 的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-181">To do so, for **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; and for **Value** enter the name of the receive port that you created to receive the XML message from Fabrikam.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-182">您可以依您的選擇篩選其他屬性，例如 BTS.MessageType。</span><span class="sxs-lookup"><span data-stu-id="3606a-182">You could filter on another property of your choice, for example, on BTS.MessageType.</span></span>  

8. <span data-ttu-id="3606a-183">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="3606a-183">Click **OK**.</span></span>  

9. <span data-ttu-id="3606a-184">按一下 **傳送埠**節點在管理主控台中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="3606a-184">Click the **Send Ports** node in the Administration Console, right-click your send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a><span data-ttu-id="3606a-185">若要為 Fabrikam 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="3606a-185">To create a party and a business profile for Fabrikam</span></span>  

1. <span data-ttu-id="3606a-186">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="3606a-186">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="3606a-187">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3606a-187">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-188">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3606a-188">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3606a-189">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="3606a-189">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="3606a-190">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="3606a-190">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="3606a-191">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="3606a-191">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="3606a-192">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="3606a-192">In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-193">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="3606a-193">When you create a party, a profile is also created.</span></span> <span data-ttu-id="3606a-194">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="3606a-194">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="3606a-195">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3606a-195">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="3606a-196">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="3606a-196">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a><span data-ttu-id="3606a-197">若要為 Contoso 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="3606a-197">To create a party and a business profile for Contoso</span></span>  

1. <span data-ttu-id="3606a-198">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="3606a-198">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="3606a-199">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3606a-199">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-200">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3606a-200">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3606a-201">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="3606a-201">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="3606a-202">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="3606a-202">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="3606a-203">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="3606a-203">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="3606a-204">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="3606a-204">In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-205">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="3606a-205">When you create a party, a profile is also created.</span></span> <span data-ttu-id="3606a-206">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="3606a-206">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="3606a-207">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3606a-207">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="3606a-208">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="3606a-208">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a><span data-ttu-id="3606a-209">在兩個商務設定檔之間建立協議</span><span class="sxs-lookup"><span data-stu-id="3606a-209">To create an agreement between the two business profiles</span></span>  

1. <span data-ttu-id="3606a-210">以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="3606a-210">Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="3606a-211">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="3606a-211">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  

3. <span data-ttu-id="3606a-212">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="3606a-212">From the **Protocol** drop-down list, select **X12**.</span></span>  

4. <span data-ttu-id="3606a-213">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="3606a-213">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  

5. <span data-ttu-id="3606a-214">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="3606a-214">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  

    <span data-ttu-id="3606a-215">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。</span><span class="sxs-lookup"><span data-stu-id="3606a-215">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).</span></span>  

6. <span data-ttu-id="3606a-216">在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。</span><span class="sxs-lookup"><span data-stu-id="3606a-216">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  

7. <span data-ttu-id="3606a-217">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3606a-217">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  

   1. <span data-ttu-id="3606a-218">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3606a-218">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="3606a-219">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="3606a-219">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="3606a-220">它會比對的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="3606a-220">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3606a-221"> 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。</span><span class="sxs-lookup"><span data-stu-id="3606a-221"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="3606a-222">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="3606a-222">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
      > 
      > [!NOTE]
      >  <span data-ttu-id="3606a-223">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**要**ZZ**， **ISA6**至**THEM**， **ISA7**要**ZZ**，和**ISA8**至**美國**。</span><span class="sxs-lookup"><span data-stu-id="3606a-223">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **THEM**, **ISA7** to **ZZ**, and **ISA8** to **US**.</span></span>  

   2. <span data-ttu-id="3606a-224">上**驗證**下方的頁面上**交換設定**區段中，確定**檢查 ISA13 是否重複**選項未核取。</span><span class="sxs-lookup"><span data-stu-id="3606a-224">On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="3606a-225">清除**檢查 ISA13 是否重複**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3606a-225">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  

   3. <span data-ttu-id="3606a-226">在上**字元集和分隔符號**下方的頁面上**交換設定**區段中，選取**CR LF**選項。</span><span class="sxs-lookup"><span data-stu-id="3606a-226">On the **Charset and Separators** page under the **Interchange Settings** section, select the **CR LF** option.</span></span>  

   4. <span data-ttu-id="3606a-227">上**傳送埠**下方的頁面上**交換設定**區段中，將會從 Fabrikam 接收 EDI 交換的傳送埠產生關聯。</span><span class="sxs-lookup"><span data-stu-id="3606a-227">On the **Send Ports** page under the **Interchange Settings** section, associate the send port that will be receiving the EDI interchange from Fabrikam.</span></span> <span data-ttu-id="3606a-228">在 **傳送埠**格線下方**名稱** 欄中，按一下空白儲存格，並從下拉式清單中，選取 建立從 Fabrikam 接收 EDI 交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3606a-228">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port created for receiving the EDI interchange from Fabrikam.</span></span>  

   5. <span data-ttu-id="3606a-229">上**驗證**下方的頁面上**交易集設定**區段中，保留**EDI 類型驗證**核取，並檢查**擴充驗證**.</span><span class="sxs-lookup"><span data-stu-id="3606a-229">On the **Validation** page under the **Transaction Set Settings** section, leave **EDI Type Validation** checked and check **Extended validation**.</span></span>  

   6. <span data-ttu-id="3606a-230">如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。</span><span class="sxs-lookup"><span data-stu-id="3606a-230">If you are using one of the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], on the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange.</span></span>  


      |       <span data-ttu-id="3606a-231">使用</span><span class="sxs-lookup"><span data-stu-id="3606a-231">Use this</span></span>       |                           <span data-ttu-id="3606a-232">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="3606a-232">To do this</span></span>                            |
      |----------------------|-----------------------------------------------------------------|
      |     <span data-ttu-id="3606a-233">**預設值**</span><span class="sxs-lookup"><span data-stu-id="3606a-233">**Default**</span></span>      |                <span data-ttu-id="3606a-234">選取欄中的核取方塊</span><span class="sxs-lookup"><span data-stu-id="3606a-234">Select the checkbox in the column</span></span>                |
      |     <span data-ttu-id="3606a-235">**針對 ST1**</span><span class="sxs-lookup"><span data-stu-id="3606a-235">**For ST1**</span></span>      |                <span data-ttu-id="3606a-236">選取  **850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="3606a-236">Select **850 - Purchase Order**.</span></span>                 |
      |       <span data-ttu-id="3606a-237">**GS2**</span><span class="sxs-lookup"><span data-stu-id="3606a-237">**GS2**</span></span>        |                         <span data-ttu-id="3606a-238">請輸入**THEM**。</span><span class="sxs-lookup"><span data-stu-id="3606a-238">Enter **THEM**.</span></span>                         |
      | <span data-ttu-id="3606a-239">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="3606a-239">**Target Namespace**</span></span> | <span data-ttu-id="3606a-240">選取  **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**。</span><span class="sxs-lookup"><span data-stu-id="3606a-240">Select **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**.</span></span> |

      > [!NOTE]
      >  <span data-ttu-id="3606a-241">設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3606a-241">Setting the properties enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to determine the schema to be used in processing the incoming 850 interchange.</span></span> <span data-ttu-id="3606a-242">如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3606a-242">If an interchange has the values of GS02 and ST01 that are entered on a line of the grid, then the target namespace for the same line will be used to determine the schema to be used.</span></span>  

   7. <span data-ttu-id="3606a-243">在上**信封**下方的頁面上**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。</span><span class="sxs-lookup"><span data-stu-id="3606a-243">On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.</span></span>  


      |       <span data-ttu-id="3606a-244">使用</span><span class="sxs-lookup"><span data-stu-id="3606a-244">Use this</span></span>       |                                                                                                                                               <span data-ttu-id="3606a-245">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="3606a-245">To do this</span></span>                                                                                                                                               |
      |----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     <span data-ttu-id="3606a-246">**預設值**</span><span class="sxs-lookup"><span data-stu-id="3606a-246">**Default**</span></span>      | <span data-ttu-id="3606a-247">選取核取方塊**預設**資料行。</span><span class="sxs-lookup"><span data-stu-id="3606a-247">Select the checkbox in the **Default** column.</span></span> <span data-ttu-id="3606a-248">**注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **[gs7]**，以及**GS8**習慣即使的值**交易型別**，**版本/版次**，和**目標命名空間**不相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-248">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.</span></span> |
      | <span data-ttu-id="3606a-249">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="3606a-249">**Transaction Type**</span></span> |                                                                                                                <span data-ttu-id="3606a-250">選取測試訊息，訊息類型**850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="3606a-250">Select the message type of your test message, **850 - Purchase Order**.</span></span>                                                                                                                 |
      | <span data-ttu-id="3606a-251">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="3606a-251">**Version/Release**</span></span>  |                                                                                                                                   <span data-ttu-id="3606a-252">輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="3606a-252">Enter the EDI version, **00401**.</span></span>                                                                                                                                    |
      | <span data-ttu-id="3606a-253">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="3606a-253">**Target namespace**</span></span> |                                                                                                                    <span data-ttu-id="3606a-254">選取  **<http://schemas.microsoft.com/BizTalk/Edi/X12/2006>**。</span><span class="sxs-lookup"><span data-stu-id="3606a-254">Select **<http://schemas.microsoft.com/BizTalk/Edi/X12/2006>**.</span></span>                                                                                                                     |
      |       <span data-ttu-id="3606a-255">**GS1**</span><span class="sxs-lookup"><span data-stu-id="3606a-255">**GS1**</span></span>        |                                                                                                      <span data-ttu-id="3606a-256">確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。</span><span class="sxs-lookup"><span data-stu-id="3606a-256">Verify that the message type of the test message is selected, **PO - Purchase Order (850)**.</span></span>                                                                                                      |
      |       <span data-ttu-id="3606a-257">**GS2**</span><span class="sxs-lookup"><span data-stu-id="3606a-257">**GS2**</span></span>        |                                                                                                                               <span data-ttu-id="3606a-258">輸入應用程式傳送者的值。</span><span class="sxs-lookup"><span data-stu-id="3606a-258">Enter a value for the Application sender.</span></span>                                                                                                                                |
      |       <span data-ttu-id="3606a-259">**GS3**</span><span class="sxs-lookup"><span data-stu-id="3606a-259">**GS3**</span></span>        |                                                                                                                              <span data-ttu-id="3606a-260">輸入應用程式接收者的值。</span><span class="sxs-lookup"><span data-stu-id="3606a-260">Enter a value for the Application receiver.</span></span>                                                                                                                               |
      |       <span data-ttu-id="3606a-261">**GS4**</span><span class="sxs-lookup"><span data-stu-id="3606a-261">**GS4**</span></span>        |            <span data-ttu-id="3606a-262">選取您想要的日期格式。</span><span class="sxs-lookup"><span data-stu-id="3606a-262">Select the date format that you want.</span></span> <span data-ttu-id="3606a-263">**注意：** 您必須在下拉式清單中選取值，不只是按一下要顯示預設值的欄位。</span><span class="sxs-lookup"><span data-stu-id="3606a-263">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="3606a-264">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="3606a-264">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span>            |
      |       <span data-ttu-id="3606a-265">**GS5**</span><span class="sxs-lookup"><span data-stu-id="3606a-265">**GS5**</span></span>        |                                                                                                                                 <span data-ttu-id="3606a-266">選擇您要的時間格式。</span><span class="sxs-lookup"><span data-stu-id="3606a-266">Select the time format that you want.</span></span>                                                                                                                                  |
      |       <span data-ttu-id="3606a-267">**[GS7]**</span><span class="sxs-lookup"><span data-stu-id="3606a-267">**GS7**</span></span>        |                                                                                                                           <span data-ttu-id="3606a-268">選取  **X-Accredited 的 Standards Committee X12**。</span><span class="sxs-lookup"><span data-stu-id="3606a-268">Select **X - Accredited Standards Committee X12**.</span></span>                                                                                                                           |
      |       <span data-ttu-id="3606a-269">**GS8**</span><span class="sxs-lookup"><span data-stu-id="3606a-269">**GS8**</span></span>        |                                                                                                                        <span data-ttu-id="3606a-270">確認已輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="3606a-270">Verify that the EDI version has been entered, **00401**.</span></span>                                                                                                                        |

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3606a-271"> 將設定值，如 GS01，GS02，GS03、 GS04、 GS05、 GS07 和輸出的輸入值為基礎的通知的 GS08**交易類型**，**版本/版次**，和**目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="3606a-271"> will set the values for GS01, GS02, GS03, GS04, GS05, GS07, and GS08 of the outbound acknowledgments based on the values entered for **Transaction Type**, **Version/Release**, and **Target namespace**.</span></span> <span data-ttu-id="3606a-272">傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。</span><span class="sxs-lookup"><span data-stu-id="3606a-272">The send pipeline attempts to match the transaction set type, the X12 version, and the target namespace with the corresponding values in the header of the message.</span></span> <span data-ttu-id="3606a-273">如果成功，則會使用相關聯的 GS 值**交易類型**，**版本/版次**，並**目標命名空間**值。</span><span class="sxs-lookup"><span data-stu-id="3606a-273">If successful, it uses the GS values associated with the **Transaction Type**, **Version/Release**, and **Target namespace** values.</span></span>  

8. <span data-ttu-id="3606a-274">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3606a-274">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-275">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="3606a-275">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="3606a-276">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**。</span><span class="sxs-lookup"><span data-stu-id="3606a-276">To successfully create an agreement, both one-way agreement tabs must have values defined for **ISA5**, **ISA6**, **ISA7**, and **ISA8**.</span></span>  

   1.  <span data-ttu-id="3606a-277">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3606a-277">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  

       > [!NOTE]
       >  <span data-ttu-id="3606a-278">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**要**ZZ**， **ISA6**至**美國**， **ISA7**要**ZZ**，和**ISA8**至**THEM**。</span><span class="sxs-lookup"><span data-stu-id="3606a-278">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **US**, **ISA7** to **ZZ**, and **ISA8** to **THEM**.</span></span>  

9. <span data-ttu-id="3606a-279">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="3606a-279">Click **Apply**.</span></span>  

10. <span data-ttu-id="3606a-280">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="3606a-280">Click **OK**.</span></span> <span data-ttu-id="3606a-281">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="3606a-281">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="3606a-282">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="3606a-282">The newly added agreement is enabled by default.</span></span>  

### <a name="testing-the-walkthrough"></a><span data-ttu-id="3606a-283">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="3606a-283">Testing the Walkthrough</span></span>  
 <span data-ttu-id="3606a-284">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="3606a-284">This section provides information on how to test the walkthrough.</span></span>  

##### <a name="to-test-the-walkthrough"></a><span data-ttu-id="3606a-285">若要測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="3606a-285">To test the walkthrough</span></span>  

1. <span data-ttu-id="3606a-286">在 Windows 檔案總管中，將測試 EDI 交換置放到本機接收資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3606a-286">In Windows Explorer, drop the test EDI interchange into your local receive folder.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="3606a-287">對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="3606a-287">For a test message, you can use the SamplePO.txt file that is used in the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="3606a-288">該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3606a-288">That file is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial folder.</span></span> <span data-ttu-id="3606a-289">這是 X12 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="3606a-289">This is an X12 850 message.</span></span> <span data-ttu-id="3606a-290">如果您使用這個訊息，則必須完成 X12_00401_850.xsd 結構描述的部署 (該結構描述隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾)。</span><span class="sxs-lookup"><span data-stu-id="3606a-290">If you use this message, you must have deployed the X12_00401_850.xsd schema that is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI folder.</span></span> <span data-ttu-id="3606a-291">您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。</span><span class="sxs-lookup"><span data-stu-id="3606a-291">You must not use the X12 850 schema in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema folder.</span></span>  

2. <span data-ttu-id="3606a-292">在 Windows 檔案總管中，開啟為傳送埠指定的目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3606a-292">In Windows Explorer, open the destination folder specified for the send port.</span></span> <span data-ttu-id="3606a-293">確認資料夾包含輸出 EDI 交換，其 ISA、GS 和 ST 標頭符合您在協議屬性中輸入的值。</span><span class="sxs-lookup"><span data-stu-id="3606a-293">Verify that the folder contains an output EDI interchange that has ISA, GS, and ST headers that match the values that you entered in the agreement properties.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3606a-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3606a-294">See Also</span></span>  
 [<span data-ttu-id="3606a-295">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="3606a-295">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)