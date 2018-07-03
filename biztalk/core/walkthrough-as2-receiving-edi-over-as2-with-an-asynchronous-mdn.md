---
title: '逐步解說 (AS2): 使用非同步 MDN 透過 AS2 接收 EDI |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3962e4-0525-4194-8cf1-b90664f1a139
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59fdb22b08a1855f1ba4d9cc433acb288132283a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003863"
---
# <a name="walkthrough-as2-receiving-edi-over-as2-with-an-asynchronous-mdn"></a><span data-ttu-id="8f862-102">逐步解說 (AS2)：使用非同步 MDN 透過 AS2 接收 EDI</span><span class="sxs-lookup"><span data-stu-id="8f862-102">Walkthrough (AS2): Receiving EDI over AS2 with an Asynchronous MDN</span></span>
<span data-ttu-id="8f862-103">本逐步解說提供一組逐步執行的程序，可建立透過 AS2 傳輸接收 EDI 訊息並傳回同步 MDN 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="8f862-103">This walkthrough provides a set of step-by-step procedures that creates a solution for receiving EDI messages over AS2 transport, returning synchronous MDNs.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="8f862-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="8f862-104">Prerequisites</span></span>  
 <span data-ttu-id="8f862-105">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="8f862-105">The following are prerequisites for performing the procedure in this topic:</span></span>  

- <span data-ttu-id="8f862-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="8f862-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  

- <span data-ttu-id="8f862-107">執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。</span><span class="sxs-lookup"><span data-stu-id="8f862-107">The computer that runs the walkthrough must have Internet Information Services (IIS) 7 installed.</span></span>  

- <span data-ttu-id="8f862-108">若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。</span><span class="sxs-lookup"><span data-stu-id="8f862-108">If the computer that runs the walkthrough is installed with a 64-bit version of Windows, you must ensure that the BizTalk hosts are marked as 32-bit only.</span></span> <span data-ttu-id="8f862-109">您也必須確定 IIS 已將應用程式集區的「啟用 32 位元應用程式」設定為 True。</span><span class="sxs-lookup"><span data-stu-id="8f862-109">You must also ensure IIS has the Enable 32-Bit Application Setting for the Application Pools set to True.</span></span> <span data-ttu-id="8f862-110">如需詳細資訊，請參閱 <<c0> [ 教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="8f862-110">For more information, see [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md).</span></span>  

## <a name="how-the-solution-receives-an-edi-interchange-and-returns-an-asynchronous-mdn"></a><span data-ttu-id="8f862-111">解決方案接收 EDI 交換並傳回非同步 MDN 的方式</span><span class="sxs-lookup"><span data-stu-id="8f862-111">How the Solution Receives an EDI Interchange and Returns an Asynchronous MDN</span></span>  
 <span data-ttu-id="8f862-112">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8f862-112">The solution will do the following:</span></span>  

1. <span data-ttu-id="8f862-113">透過 HTTP 從交易夥伴接收包含 EDI 交換的 AS2 訊息，並從 EDIINT/AS2 解碼此交換。</span><span class="sxs-lookup"><span data-stu-id="8f862-113">Receive an AS2 message containing an EDI interchange over HTTP from the trading partner, and decode the interchange from EDIINT/AS2.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-114">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="8f862-114">The events in this list may not occur in the order shown.</span></span>  

2. <span data-ttu-id="8f862-115">產生 MDN 回應，然後將它放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="8f862-115">Generate an MDN response, and drop it in the MessageBox.</span></span>  

3. <span data-ttu-id="8f862-116">動態傳送埠取用訊息 MDN。</span><span class="sxs-lookup"><span data-stu-id="8f862-116">Pick up the message MDN by a dynamic send port.</span></span>  

4. <span data-ttu-id="8f862-117">將非同步訊息 MDN 傳回給交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="8f862-117">Return the asynchronous message MDN to the trading partner.</span></span>  

5. <span data-ttu-id="8f862-118">將交換的 EDI 格式轉換為內部 XML 格式，然後將它放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="8f862-118">Convert the EDI format of the interchange to internal XML format, and drop it in the MessageBox.</span></span>  

6. <span data-ttu-id="8f862-119">具有 PassThruTransmit 管線的傳送埠從 MessageBox 接收訊息 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8f862-119">A send port with a PassThruTransmit pipeline picks up the message XML file from the MessageBox.</span></span>  

7. <span data-ttu-id="8f862-120">傳送埠將 EDI 交換 XML 檔案傳送至 Contoso 合作對象的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-120">The send port sends EDI interchange XML file to a folder at the Contoso party.</span></span>  

   <span data-ttu-id="8f862-121">下圖顯示這個解決方案的架構。</span><span class="sxs-lookup"><span data-stu-id="8f862-121">The following figure shows the architecture for this solution.</span></span>  

   <span data-ttu-id="8f862-122">![使用非同步 MDN 的 AS2 接收](../core/media/bts-configuring-the-receiving-of-edi-over-as2-with-an-asynchronous-mdnc.gif "bts_Configuring_the_Receiving_of_EDI_Over_AS2_with_an_Asynchronous_MDNc")</span><span class="sxs-lookup"><span data-stu-id="8f862-122">![AS2 receiving with an asynchronous MDN](../core/media/bts-configuring-the-receiving-of-edi-over-as2-with-an-asynchronous-mdnc.gif "bts_Configuring_the_Receiving_of_EDI_Over_AS2_with_an_Asynchronous_MDNc")</span></span>  

## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="8f862-123">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="8f862-123">The Functionality in this Solution</span></span>  
 <span data-ttu-id="8f862-124">下列項目適用於本逐步解說的功能：</span><span class="sxs-lookup"><span data-stu-id="8f862-124">The following applies to the functionality of this walkthrough:</span></span>  

-   <span data-ttu-id="8f862-125">不會產生 EDI 通知。</span><span class="sxs-lookup"><span data-stu-id="8f862-125">An EDI acknowledgment is not generated.</span></span> <span data-ttu-id="8f862-126">產生 EDI 通知所示[逐步解說 (X12)： 接收 EDI 交換和傳送，將通知傳回](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。</span><span class="sxs-lookup"><span data-stu-id="8f862-126">Generating an EDI acknowledgment is demonstrated in [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).</span></span> <span data-ttu-id="8f862-127">傳送 EDI 通知，透過 AS2 傳輸所述[逐步解說 (AS2): 使用非同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="8f862-127">Sending an EDI acknowledgment over AS2 transport is described in [Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).</span></span>  

-   <span data-ttu-id="8f862-128">這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。</span><span class="sxs-lookup"><span data-stu-id="8f862-128">The solution is designed for interchanges using X12 encoding, not EDIFACT encoding.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8f862-129">EDIFACT 編碼使用的組態與 X12 編碼使用的組態近乎平行。</span><span class="sxs-lookup"><span data-stu-id="8f862-129">The configuration used for EDIFACT encoding is closely parallel to that used for X12 encoding.</span></span>  

-   <span data-ttu-id="8f862-130">將針對內送交換執行 EDI 類型和擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="8f862-130">EDI type and extended validation will be performed on the incoming interchange.</span></span>  

-   <span data-ttu-id="8f862-131">將會啟用 AS2 和 EDI 報告，而且將會儲存交易集，然後從交換狀態報告中檢視交易集。</span><span class="sxs-lookup"><span data-stu-id="8f862-131">AS2 and EDI reporting will be enabled, and transaction sets will be saved for viewing from the interchange status report.</span></span>  

-   <span data-ttu-id="8f862-132">這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。</span><span class="sxs-lookup"><span data-stu-id="8f862-132">This solution does not configure signing, compression, encryption, or message storage in the non-repudiation database.</span></span> <span data-ttu-id="8f862-133">如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8f862-133">For procedures on configuring those properties, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).</span></span>  

## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="8f862-134">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="8f862-134">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="8f862-135">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8f862-135">The procedures required for this solution include the following:</span></span>  

- <span data-ttu-id="8f862-136">使用必要的訊息結構描述來建置並部署 BizTalk 專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的交換。</span><span class="sxs-lookup"><span data-stu-id="8f862-136">Build and deploy a BizTalk project with the required message schema, making the schema available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the received interchange.</span></span>  

- <span data-ttu-id="8f862-137">讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="8f862-137">Enable the BTS ISAPI filter used in receiving the AS2 message.</span></span>  

- <span data-ttu-id="8f862-138">建立會從 Fabrikam 接收 AS2 訊息的 Contoso 虛擬目錄 (如接收位置中所設定)。</span><span class="sxs-lookup"><span data-stu-id="8f862-138">Create a Contoso virtual directory that receives the AS2 message from Fabrikam, as configured in the receive location.</span></span>  

- <span data-ttu-id="8f862-139">建立會從 Contoso 接收 MDN 的 Fabrikam 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="8f862-139">Create a Fabrikam virtual directory that receives the MDN from Contoso.</span></span>  

- <span data-ttu-id="8f862-140">指定 Contoso 和 Fabrikam 虛擬目錄不是由 Windows SharePoint Services 管理。</span><span class="sxs-lookup"><span data-stu-id="8f862-140">Specify that the Contoso and Fabrikam virtual directories are not managed by Windows SharePoint Services.</span></span>  

- <span data-ttu-id="8f862-141">建立靜態單向 HTTP 接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收包含 EDI 商業文件的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="8f862-141">Create a static one-way HTTP receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the AS2 message containing the EDI business document from the trading partner.</span></span> <span data-ttu-id="8f862-142">將接收管線設定為 AS2EDIReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="8f862-142">Configure the receive pipeline to be the AS2EDIReceive pipeline.</span></span>  

- <span data-ttu-id="8f862-143">建立動態單向 HTTP 傳送埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 MDN 來回應收到的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="8f862-143">Create a dynamic one-way HTTP send port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send the MDN responding to the received AS2 message.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="8f862-144">這個傳送埠會訂閱以 EdiIntAS.IsAS2AsynchronousMDN 屬性 (由 AS2EdiReceive 管線設定為 True) 和相互關聯之 Token 為基礎的 MDN。</span><span class="sxs-lookup"><span data-stu-id="8f862-144">This send port subscribes to the MDN based on the EdiIntAS.IsAS2AsynchronousMDN property (which was set to True by the AS2EdiReceive pipeline) and correlation tokens.</span></span> <span data-ttu-id="8f862-145">傳送埠必須是動態，才能將 MDN 傳送至訊息標頭內 Receipt-Delivery-Notification 一行中的地址。</span><span class="sxs-lookup"><span data-stu-id="8f862-145">The send port must be dynamic, so it will send the MDN to the address in the Receipt-Delivery-Notification line in the header of the message.</span></span>  

- <span data-ttu-id="8f862-146">建立靜態單向 FILE 傳送埠，以將 EDI 內容 (XML 格式) 路由傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-146">Create a static one-way FILE send port to route the EDI payload (in XML format) to a local folder.</span></span> <span data-ttu-id="8f862-147">建立本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-147">Create the local folder.</span></span>  

- <span data-ttu-id="8f862-148">為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="8f862-148">Create a party (trading partner) for both Fabrikam and Contoso.</span></span>  

- <span data-ttu-id="8f862-149">為這兩個交易合作對象各建立一個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="8f862-149">Create a business profile each for both the trading parties.</span></span>  

- <span data-ttu-id="8f862-150">在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-150">Create an AS2 agreement between the business profiles for Fabrikam and Contoso.</span></span> <span data-ttu-id="8f862-151">這個 AS2 協議包含的屬性將可用來傳送 AS2 訊息並接收回傳的同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="8f862-151">The AS2 agreement would contain properties to send an AS2 message and receive an asynchronous MDN in return.</span></span>  

- <span data-ttu-id="8f862-152">在 Fabrikam 與 Contoso 的商務設定檔之間建立 X12 協議，以便接收 X12 訊息。</span><span class="sxs-lookup"><span data-stu-id="8f862-152">Create an X12 agreement between the business profiles for Fabrikam and Contoso to receive X12 messages.</span></span>  

- <span data-ttu-id="8f862-153">使用 AS2 教學課程檔案中隨附的 HTTP 傳送者公用程式，測試此解決方案。</span><span class="sxs-lookup"><span data-stu-id="8f862-153">Test the solution by using the HTTP Sender utility that is shipped as part of the AS2 tutorial files.</span></span> <span data-ttu-id="8f862-154">這個公用程式會傳送測試 AS2 訊息，其中包含透過 AS2 傳輸的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="8f862-154">This utility sends a test AS2 message containing an EDI interchange over AS2 transport.</span></span> <span data-ttu-id="8f862-155">這個公用程式會傳送測試 AS2 訊息，其中包含透過 AS2 傳輸的 EDI 交換 (AS2 教學課程中隨附的 X12_00401_864.edi)。</span><span class="sxs-lookup"><span data-stu-id="8f862-155">This utility sends a test AS2 message containing an EDI interchange over AS2 transport (X12_00401_864.edi, also shipped with the AS2 tutorial).</span></span> <span data-ttu-id="8f862-156">針對這個逐步解說使用的「HTTP 傳送者」和測試訊息與教學課程隨附的版本相同。</span><span class="sxs-lookup"><span data-stu-id="8f862-156">The HTTP Sender and the test message that you use for this walkthrough are the same as the versions that shipped for the tutorial.</span></span>  

### <a name="configuring-the-walkthrough"></a><span data-ttu-id="8f862-157">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="8f862-157">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="8f862-158">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="8f862-158">This section describes the procedures to configure the walkthrough.</span></span>  

##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="8f862-159">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="8f862-159">To deploy the message schema</span></span>  

1. <span data-ttu-id="8f862-160">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟專案 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.btproj。</span><span class="sxs-lookup"><span data-stu-id="8f862-160">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the project [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.btproj.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-161">這個專案 (隨附於 AS2 教學課程) 包含了搭配測試訊息使用的 864 結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f862-161">This project, which is shipped for the AS2 tutorial, includes an 864 schema for use with the test message.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-162">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="8f862-162">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="8f862-163">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="8f862-163">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  

2. <span data-ttu-id="8f862-164">以滑鼠右鍵按一下**結構描述**在 [方案總管] 中專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8f862-164">Right-click the **Schemas** project in the Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="8f862-165">按一下 **簽署**索引標籤，在 專案設計工具中，核取**簽署組件**核取方塊，然後從下拉式清單中，選取**新增**，並提供必要的值，以建立強式名稱金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="8f862-165">Click the **Signing** tab in the project designer, check the **Sign the Assembly** checkbox, and from the drop-down, select **New** and provide the necessary values to create a strong name key file.</span></span> <span data-ttu-id="8f862-166">儲存變更，然後關閉專案屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="8f862-166">Save the changes and close the project properties window.</span></span>  

3. <span data-ttu-id="8f862-167">建置並部署 Schemas.btproj。</span><span class="sxs-lookup"><span data-stu-id="8f862-167">Build and deploy Schemas.btproj.</span></span>  

##### <a name="to-enable-the-bts-isapi-filter"></a><span data-ttu-id="8f862-168">若要啟用 BTS ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="8f862-168">To enable the BTS ISAPI Filter</span></span>  

1. <span data-ttu-id="8f862-169">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="8f862-169">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  

   > [!TIP]
   >  <span data-ttu-id="8f862-170">視作業系統而定，[系統管理工具] 開始功能表選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="8f862-170">Depending on the operating system, the Administrative Tools start menu option may not be available.</span></span> <span data-ttu-id="8f862-171">在這種情況下，按一下**開始**，按一下**執行**，然後輸入`inetmgr`以開啟 Internet Information Services (IIS) 管理員。</span><span class="sxs-lookup"><span data-stu-id="8f862-171">In such cases, click **Start**, click **Run**, and enter `inetmgr` to open Internet Information Services (IIS) Manager.</span></span>  

2. <span data-ttu-id="8f862-172">選取根 Web 伺服器項目並在**功能檢視**，按兩下**處理常式對應**，然後在 動作 窗格中的，按一下 **新增指令碼對應**。</span><span class="sxs-lookup"><span data-stu-id="8f862-172">Select the root Web Server entry and in the **Features View**, double click **Handler Mappings** and then in the Actions pane click **Add Script Map**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-173">在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。</span><span class="sxs-lookup"><span data-stu-id="8f862-173">Configuring the script mapping at the Web Server level will cause this mapping to apply to all child Web Sites.</span></span> <span data-ttu-id="8f862-174">若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8f862-174">If you wish to restrict the mapping to a specific Web Site or Virtual Folder, select the target site or folder instead of the Web Server.</span></span>  

3. <span data-ttu-id="8f862-175">在 **新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。</span><span class="sxs-lookup"><span data-stu-id="8f862-175">In the **Add Script Map** dialog box, enter `BtsHttpReceive.dll` in the **Request path** field.</span></span>  

4. <span data-ttu-id="8f862-176">在 **可執行檔**欄位中，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="8f862-176">In the **Executable** field, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span></span> <span data-ttu-id="8f862-177">選取 BtsHttpReceive.dll，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-177">Select BtsHttpReceive.dll and click **OK**.</span></span>  

5. <span data-ttu-id="8f862-178">請輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。</span><span class="sxs-lookup"><span data-stu-id="8f862-178">Enter `BizTalk HTTP Receive` in the `Name` field, and then click **Request Restrictions**.</span></span>  

6. <span data-ttu-id="8f862-179">在 [要求限制] 對話方塊中，選取**動詞**索引標籤，然後選取**其中一個下列的指令動詞**。</span><span class="sxs-lookup"><span data-stu-id="8f862-179">In the Request Restrictions dialog box, select the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="8f862-180">輸入`POST`作為動詞。</span><span class="sxs-lookup"><span data-stu-id="8f862-180">Enter `POST` as the verb .</span></span>  

7. <span data-ttu-id="8f862-181">在上**存取權**索引標籤上，選取**指令碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-181">On the **Access** tab, select **Script** and then click **OK**.</span></span>  

8. <span data-ttu-id="8f862-182">按一下  **確定**當系統提示您允許 ISAPI 延伸模組時，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="8f862-182">Click **OK** and when prompted to allow the ISAPI extension, click **Yes**.</span></span>  

##### <a name="to-configure-the-contoso-web-page"></a><span data-ttu-id="8f862-183">若要設定 Contoso 網頁</span><span class="sxs-lookup"><span data-stu-id="8f862-183">To configure the Contoso Web page</span></span>  

1. <span data-ttu-id="8f862-184">在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，然後選取**新增應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="8f862-184">In IIS Manager, right-click **Application Pools** and select **Add Application Pool**.</span></span>  

2. <span data-ttu-id="8f862-185">在**新增的應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f862-185">In the **Add Application Pool** dialog box, enter **BizTalkAppPool** in **Name**, and then select **.NET Framework V4.0.30210** in the **.NET Framework version** drop-down list.</span></span> <span data-ttu-id="8f862-186">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f862-186">Click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-187">版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8f862-187">The version number may vary depending on the version of [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installed on the machine.</span></span>  

3. <span data-ttu-id="8f862-188">選取 **應用程式集區**，在 功能檢視 中選取**BizTalkAppPool**，然後按一下**進階設定**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="8f862-188">Select **Application Pools**, in the Features View select **BizTalkAppPool**, and then click **Advanced Settings** in the **Actions** pane.</span></span>  

4. <span data-ttu-id="8f862-189">在 [**進階設定]** 對話方塊中，選取**身分識別**，然後按一下 [**省略符號 （...）** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f862-189">In the **Advanced Settings** dialog box, select **Identity** and then click the **ellipsis (…)** button.</span></span>  

5. <span data-ttu-id="8f862-190">在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-190">In the **Application Pool Identity** dialog box, select **Custom account** and then click **Set**.</span></span>  

6. <span data-ttu-id="8f862-191">輸入**使用者名**並**密碼**使用者帳戶，系統管理員群組的成員，請輸入中的密碼**確認密碼**，然後按一下  **確定**三次，以返回 IIS 管理員。</span><span class="sxs-lookup"><span data-stu-id="8f862-191">Enter the **User name** and **Password** for a user account that is a member of the administrators group, enter the password in **Confirm password** and then click **OK** three times to return to the IIS Manager.</span></span>  

7. <span data-ttu-id="8f862-192">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-192">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="8f862-193">以滑鼠右鍵按一下**Default Web Site**節點，，然後選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8f862-193">Right-click the **Default Web Site** node, and then select **Add Application**.</span></span>  

8. <span data-ttu-id="8f862-194">在 **新增應用程式**對話方塊方塊中，輸入**Contoso**中**別名**文字方塊中，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="8f862-194">In the **Add Application** dialog box, enter **Contoso** in the **Alias** text box, and then click **Select**.</span></span>  

9. <span data-ttu-id="8f862-195">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-195">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  

10. <span data-ttu-id="8f862-196">針對**實體路徑**，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="8f862-196">For the **Physical Path**, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span></span>  

11. <span data-ttu-id="8f862-197">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-197">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="8f862-198">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8f862-198">Click **Close**, and then click **OK**.</span></span>  

12. <span data-ttu-id="8f862-199">在 [IIS 管理員] 中，選取 Contoso 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8f862-199">In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  

13. <span data-ttu-id="8f862-200">在 **驗證**頁面上，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="8f862-200">In the **Authentication** page, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="8f862-201">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="8f862-201">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  

##### <a name="to-configure-the-fabrikam-web-page"></a><span data-ttu-id="8f862-202">若要設定 Fabrikam 網頁</span><span class="sxs-lookup"><span data-stu-id="8f862-202">To configure the Fabrikam Web page</span></span>  

1. <span data-ttu-id="8f862-203">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-203">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="8f862-204">以滑鼠右鍵按一下**Default Web Site**節點，，然後選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8f862-204">Right-click the **Default Web Site** node, and then select **Add Application**.</span></span>  

2. <span data-ttu-id="8f862-205">在 **新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="8f862-205">In the **Add Application** dialog box, enter **Fabrikam** in **Alias**, and then click **Select**.</span></span>  

3. <span data-ttu-id="8f862-206">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-206">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  

4. <span data-ttu-id="8f862-207">針對**實體路徑**，按一下 [**省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 tutorial\fabrikam]。</span><span class="sxs-lookup"><span data-stu-id="8f862-207">For the **Physical Path**, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Fabrikam.</span></span>  

5. <span data-ttu-id="8f862-208">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-208">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="8f862-209">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8f862-209">Click **Close**, and then click **OK**.</span></span>  

6. <span data-ttu-id="8f862-210">在 [IIS 管理員] 中，選取 Contoso 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8f862-210">In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  

7. <span data-ttu-id="8f862-211">在 **驗證**頁面上，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="8f862-211">In the **Authentication** page, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="8f862-212">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="8f862-212">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  

##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a><span data-ttu-id="8f862-213">若要指定虛擬目錄不是由 Windows SharePoint Services 管理</span><span class="sxs-lookup"><span data-stu-id="8f862-213">To specify that your virtual directory is not managed by Windows SharePoint Services</span></span>  

1.  <span data-ttu-id="8f862-214">如果 Windows SharePoint Services 安裝在電腦上，按一下**開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="8f862-214">If Windows SharePoint Services is installed on your computer, click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint 3.0 Central Administration**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8f862-215">如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="8f862-215">This procedure is required if Windows SharePoint Server is installed on the same computer that you are setting the walkthrough up on.</span></span> <span data-ttu-id="8f862-216">在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。</span><span class="sxs-lookup"><span data-stu-id="8f862-216">In that case, you must specify that your IIS virtual directory is not being managed by Windows SharePoint Server.</span></span>  

2.  <span data-ttu-id="8f862-217">在上**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。</span><span class="sxs-lookup"><span data-stu-id="8f862-217">On the **Central Administration** page, under **Central Administration**, click **Application Management**.</span></span>  

3.  <span data-ttu-id="8f862-218">在 **應用程式管理**頁面上，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="8f862-218">On the **Application Management** page, click **Define managed paths**.</span></span>  

4.  <span data-ttu-id="8f862-219">在 **定義管理的路徑**頁面的 **加入新路徑**，請在**路徑**文字方塊中，輸入**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="8f862-219">In the **Define Managed Paths** page, under **Add a New Path**, in the **Path** text box, enter **Contoso**.</span></span> <span data-ttu-id="8f862-220">底下**型別**，按一下**排除的路徑**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-220">Under **Type**, click **Excluded Path**, and then click **OK**.</span></span>  

5.  <span data-ttu-id="8f862-221">針對 Fabrikam 虛擬目錄重複步驟 4。</span><span class="sxs-lookup"><span data-stu-id="8f862-221">Repeat step 4 for the Fabrikam virtual directory.</span></span>  

##### <a name="to-create-a-receive-port-to-receive-the-edi-interchange-over-as2-from-fabrikam"></a><span data-ttu-id="8f862-222">若要建立接收埠以透過 AS2 接收來自 Fabrikam 的 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="8f862-222">To create a receive port to receive the EDI interchange Over AS2 from Fabrikam</span></span>  

1. <span data-ttu-id="8f862-223">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="8f862-223">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.</span></span>  

2. <span data-ttu-id="8f862-224">將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="8f862-224">Name the receive port, and then click **Receive Locations** in the console tree.</span></span>  

3. <span data-ttu-id="8f862-225">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8f862-225">Click **New**.</span></span>  

4. <span data-ttu-id="8f862-226">接收位置命名，選取**HTTP** for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-226">Name the receive location, select **HTTP** for **Type**, and then click **Configure**.</span></span>  

5. <span data-ttu-id="8f862-227">針對**虛擬目錄加 ISAPI 延伸模組**，輸入`/Contoso/BTSHTTPReceive.dll`。</span><span class="sxs-lookup"><span data-stu-id="8f862-227">For **Virtual directory plus ISAPI extension**, enter `/Contoso/BTSHTTPReceive.dll`.</span></span>  

6. <span data-ttu-id="8f862-228">選取 **擱置失敗的要求**核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-228">Select the **Suspend failed requests** check box, and click **OK**.</span></span>  

7. <span data-ttu-id="8f862-229">針對**接收管線**，選取**AS2EDIReceive**。</span><span class="sxs-lookup"><span data-stu-id="8f862-229">For **Receive pipeline**, select **AS2EDIReceive**.</span></span>  

8. <span data-ttu-id="8f862-230">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="8f862-230">Click **OK**, and then click **OK** again.</span></span>  

9. <span data-ttu-id="8f862-231">在 **接收位置**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下接收位置，然後**啟用**。</span><span class="sxs-lookup"><span data-stu-id="8f862-231">In the **Receive Locations** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location, and then click **Enable**.</span></span>  

##### <a name="to-create-a-dynamic-send-port-to-send-the-mdn-to-fabrikam"></a><span data-ttu-id="8f862-232">若要建立動態傳送埠以將 MDN 傳送至 Fabrikam</span><span class="sxs-lookup"><span data-stu-id="8f862-232">To create a dynamic send port to send the MDN to Fabrikam</span></span>  

1. <span data-ttu-id="8f862-233">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **動態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8f862-233">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Dynamic One-way Send Port**.</span></span>  

2. <span data-ttu-id="8f862-234">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f862-234">In the **Send Port Properties** dialog box, name the send port.</span></span>  

3. <span data-ttu-id="8f862-235">針對**傳送管線**，選取**AS2Send**。</span><span class="sxs-lookup"><span data-stu-id="8f862-235">For **Send Pipeline**, select **AS2Send**.</span></span>  

4. <span data-ttu-id="8f862-236">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="8f862-236">In the console tree, select **Filters**.</span></span> <span data-ttu-id="8f862-237">針對**屬性**，輸入**EdiIntAS.IsAS2AsynchronousMDN**; 對於**運算子**，輸入**==**; 及針對**值**，輸入 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="8f862-237">For **Property**, enter **EdiIntAS.IsAS2AsynchronousMDN**; for **Operator**, enter **==**; and for **Value** , enter **True**.</span></span>  

5. <span data-ttu-id="8f862-238">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f862-238">Click **OK**.</span></span>  

##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a><span data-ttu-id="8f862-239">若要建立傳送埠以將 EDI 內容傳送至本機資料夾</span><span class="sxs-lookup"><span data-stu-id="8f862-239">To create a send port to send the EDI payload to a local folder</span></span>  

1. <span data-ttu-id="8f862-240">在 Windows 檔案總管中，會建立名為的 Contoso 本機資料夾**EDI_to_Contoso**傳送 EDI 內容。</span><span class="sxs-lookup"><span data-stu-id="8f862-240">In Windows Explorer, create a Contoso local folder named **EDI_to_Contoso** to send the EDI payload to.</span></span>  

2. <span data-ttu-id="8f862-241">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8f862-241">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  

3. <span data-ttu-id="8f862-242">在 **傳送埠屬性**對話方塊中，將傳送埠，例如**Send_Payload**。</span><span class="sxs-lookup"><span data-stu-id="8f862-242">In the **Send Port Properties** dialog box, name your send port, for example, **Send_Payload**.</span></span> <span data-ttu-id="8f862-243">選取 **檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-243">Select **FILE** for **Type**, and then click **Configure**.</span></span>  

4. <span data-ttu-id="8f862-244">在**FILE 傳輸屬性** 對話方塊中，如**目的地資料夾**中，瀏覽並選取**EDI_to_Contoso**您在步驟 1 中建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-244">In the **FILE Transport Properties** dialog box, for **Destination folder**, browse to and select the **EDI_to_Contoso** folder that you created in step 1.</span></span> <span data-ttu-id="8f862-245">離開**檔名**作為 **%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="8f862-245">Leave **File name** as **%MessageID%.xml**.</span></span> <span data-ttu-id="8f862-246">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f862-246">Click **OK**.</span></span>  

5. <span data-ttu-id="8f862-247">接受預設值是**PassThruTransmit** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="8f862-247">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  

6. <span data-ttu-id="8f862-248">按一下 **篩選器**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="8f862-248">Click **Filters** in the console tree.</span></span> <span data-ttu-id="8f862-249">針對**屬性**，輸入**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="8f862-249">For **Property**, enter **BTS.MessageType**.</span></span> <span data-ttu-id="8f862-250">針對**運算子**，輸入**==**。</span><span class="sxs-lookup"><span data-stu-id="8f862-250">For **Operator**, enter **==**.</span></span> <span data-ttu-id="8f862-251">針對**值**，輸入您的訊息，訊息類型`http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`。</span><span class="sxs-lookup"><span data-stu-id="8f862-251">For **Value**, enter the message type for your message, `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.</span></span>  

7. <span data-ttu-id="8f862-252">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f862-252">Click **OK**.</span></span>  

8. <span data-ttu-id="8f862-253">在 **傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下傳送埠，然後**啟動**。</span><span class="sxs-lookup"><span data-stu-id="8f862-253">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a><span data-ttu-id="8f862-254">若要為 Fabrikam 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="8f862-254">To create a party and a business profile for Fabrikam</span></span>  

1. <span data-ttu-id="8f862-255">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="8f862-255">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="8f862-256">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-256">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-257">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f862-257">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="8f862-258">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="8f862-258">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="8f862-259">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="8f862-259">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="8f862-260">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="8f862-260">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="8f862-261">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-261">In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-262">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="8f862-262">When you create a party, a profile is also created.</span></span> <span data-ttu-id="8f862-263">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="8f862-263">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="8f862-264">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8f862-264">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="8f862-265">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f862-265">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a><span data-ttu-id="8f862-266">若要為 Contoso 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="8f862-266">To create a party and a business profile for Contoso</span></span>  

1. <span data-ttu-id="8f862-267">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="8f862-267">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="8f862-268">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8f862-268">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-269">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f862-269">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="8f862-270">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="8f862-270">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="8f862-271">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="8f862-271">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="8f862-272">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="8f862-272">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="8f862-273">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-273">In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-274">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="8f862-274">When you create a party, a profile is also created.</span></span> <span data-ttu-id="8f862-275">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="8f862-275">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="8f862-276">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8f862-276">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="8f862-277">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f862-277">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-an-as2-agreement-between-the-two-business-profiles"></a><span data-ttu-id="8f862-278">若要建立兩個商務設定檔之間的 AS2 協議</span><span class="sxs-lookup"><span data-stu-id="8f862-278">To create an AS2 agreement between the two business profiles</span></span>  

1.  <span data-ttu-id="8f862-279">以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="8f862-279">Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  

2.  <span data-ttu-id="8f862-280">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f862-280">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  

3.  <span data-ttu-id="8f862-281">從**通訊協定**下拉式清單中，選取**AS2**。</span><span class="sxs-lookup"><span data-stu-id="8f862-281">From the **Protocol** drop-down list, select **AS2**.</span></span>  

4.  <span data-ttu-id="8f862-282">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="8f862-282">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  

5.  <span data-ttu-id="8f862-283">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="8f862-283">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  

     <span data-ttu-id="8f862-284">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-284">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way AS2 agreement.</span></span>  

6.  <span data-ttu-id="8f862-285">在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**。</span><span class="sxs-lookup"><span data-stu-id="8f862-285">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**.</span></span>  

7.  <span data-ttu-id="8f862-286">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8f862-286">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  

    1.  <span data-ttu-id="8f862-287">上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="8f862-287">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="8f862-288">針對**AS2-從**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="8f862-288">For **AS2-From**, enter `Fabrikam`.</span></span> <span data-ttu-id="8f862-289">針對**AS2-To**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="8f862-289">For **AS2- To**, enter `Contoso`.</span></span>  

    2.  <span data-ttu-id="8f862-290">在 **驗證**頁面上，選取**使用協議設定進行驗證與 MDN 取代訊息標頭**核取方塊</span><span class="sxs-lookup"><span data-stu-id="8f862-290">On the **Validation** page, select the **Use agreement settings for validation and MDN instead of message header** check box</span></span>  

    3.  <span data-ttu-id="8f862-291">在 **通知 (Mdn)** 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8f862-291">In the **Acknowledgements (MDNs)** page, do the following:</span></span>  

        1.  <span data-ttu-id="8f862-292">選取 **的 要求 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-292">Select the **Request MDN** check box.</span></span>  

        2.  <span data-ttu-id="8f862-293">請確定**要求簽署的 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-293">Make sure the **Request Signed MDN** check box is cleared.</span></span>  

        3.  <span data-ttu-id="8f862-294">選取 **要求非同步 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8f862-294">Select the **Request asynchronous MDN** check box.</span></span>  

        4.  <span data-ttu-id="8f862-295">在 **回條傳遞選項 (URL)** 文字方塊中，輸入`http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`。</span><span class="sxs-lookup"><span data-stu-id="8f862-295">In the **Receipt-Delivery-Option (URL)** text box, enter `http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`.</span></span>  

8.  <span data-ttu-id="8f862-296">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8f862-296">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8f862-297">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-297">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="8f862-298">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="8f862-298">To successfully create an agreement, both one-way agreement tabs must have values defined for **AS2-From** and **AS2-To**.</span></span>  

    1.  <span data-ttu-id="8f862-299">上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="8f862-299">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="8f862-300">針對**AS2-從**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="8f862-300">For **AS2-From**, enter `Contoso`.</span></span> <span data-ttu-id="8f862-301">針對**AS2-To**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="8f862-301">For **AS2- To**, enter `Fabrikam`.</span></span>  

9. <span data-ttu-id="8f862-302">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="8f862-302">Click **Apply**.</span></span>  

10. <span data-ttu-id="8f862-303">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f862-303">Click **OK**.</span></span> <span data-ttu-id="8f862-304">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="8f862-304">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="8f862-305">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-305">The newly added agreement is enabled by default.</span></span>  

##### <a name="to-create-an-x12-agreement-between-the-two-business-profiles"></a><span data-ttu-id="8f862-306">若要建立兩個商務設定檔之間的 X12 協議</span><span class="sxs-lookup"><span data-stu-id="8f862-306">To create an X12 agreement between the two business profiles</span></span>  

1. <span data-ttu-id="8f862-307">以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="8f862-307">Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="8f862-308">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f862-308">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  

3. <span data-ttu-id="8f862-309">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="8f862-309">From the **Protocol** drop-down list, select **X12**.</span></span>  

4. <span data-ttu-id="8f862-310">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="8f862-310">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  

5. <span data-ttu-id="8f862-311">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="8f862-311">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  

    <span data-ttu-id="8f862-312">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 X12 協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-312">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way X12 agreement.</span></span>  

6. <span data-ttu-id="8f862-313">在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。</span><span class="sxs-lookup"><span data-stu-id="8f862-313">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  

7. <span data-ttu-id="8f862-314">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8f862-314">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  

   1. <span data-ttu-id="8f862-315">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="8f862-315">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="8f862-316">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="8f862-316">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="8f862-317">它會比對的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="8f862-317">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8f862-318"> 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-318"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="8f862-319">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="8f862-319">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
      > 
      > [!NOTE]
      >  <span data-ttu-id="8f862-320">針對此逐步解說中，設定**ISA5**要**ZZ**， **ISA6**至**7654321**， **ISA7**到**ZZ**，並**ISA8**要**1234567**。</span><span class="sxs-lookup"><span data-stu-id="8f862-320">For this walkthrough, set **ISA5** to **ZZ**, **ISA6** to **7654321**, **ISA7** to **ZZ**, and **ISA8** to **1234567**.</span></span>  

   2. <span data-ttu-id="8f862-321">上**驗證**下方的頁面上**交換設定**區段中，確定**檢查 ISA13 是否重複**選項未核取。</span><span class="sxs-lookup"><span data-stu-id="8f862-321">On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="8f862-322">清除**檢查 ISA13 是否重複**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f862-322">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  

   3. <span data-ttu-id="8f862-323">如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。</span><span class="sxs-lookup"><span data-stu-id="8f862-323">If you are using one of the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], on the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange.</span></span>  

      |<span data-ttu-id="8f862-324">使用</span><span class="sxs-lookup"><span data-stu-id="8f862-324">Use this</span></span>|<span data-ttu-id="8f862-325">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f862-325">To do this</span></span>|  
      |--------------|----------------|  
      |<span data-ttu-id="8f862-326">**預設值**</span><span class="sxs-lookup"><span data-stu-id="8f862-326">**Default**</span></span>|<span data-ttu-id="8f862-327">選取欄中的核取方塊</span><span class="sxs-lookup"><span data-stu-id="8f862-327">Select the checkbox in the column</span></span>|  
      |<span data-ttu-id="8f862-328">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="8f862-328">**Target Namespace**</span></span>|<span data-ttu-id="8f862-329">選取 [ `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`]。</span><span class="sxs-lookup"><span data-stu-id="8f862-329">Select `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`.</span></span>|  

      > [!NOTE]
      >  <span data-ttu-id="8f862-330">設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f862-330">Setting the properties enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to determine the schema to be used in processing the incoming 850 interchange.</span></span> <span data-ttu-id="8f862-331">如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f862-331">If an interchange has the values of GS02 and ST01 that are entered on a line of the grid, then the target namespace for the same line will be used to determine the schema to be used.</span></span>  

   4. <span data-ttu-id="8f862-332">上**信封**下方的頁面上**交易集設定**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8f862-332">On the **Envelopes** page under the **Transaction Set Settings** section, do the following:</span></span>  


      |       <span data-ttu-id="8f862-333">使用</span><span class="sxs-lookup"><span data-stu-id="8f862-333">Use this</span></span>       |                                                                                                                                              <span data-ttu-id="8f862-334">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="8f862-334">To do this</span></span>                                                                                                                                               |
      |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     <span data-ttu-id="8f862-335">**預設值**</span><span class="sxs-lookup"><span data-stu-id="8f862-335">**Default**</span></span>      |              <span data-ttu-id="8f862-336">選取 **預設**。</span><span class="sxs-lookup"><span data-stu-id="8f862-336">Select **Default**.</span></span> <span data-ttu-id="8f862-337">**注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **[gs7]**，以及**GS8**習慣即使的值**交易型別**，**版本/版次**，和**目標命名空間**不相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="8f862-337">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.</span></span>              |
      | <span data-ttu-id="8f862-338">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="8f862-338">**Transaction Type**</span></span> |                                                                                                          <span data-ttu-id="8f862-339">例如，選取您的測試訊息的訊息類型**864-簡訊**。</span><span class="sxs-lookup"><span data-stu-id="8f862-339">Select the message type of your test message, for example, **864 – Text Message**.</span></span>                                                                                                           |
      | <span data-ttu-id="8f862-340">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="8f862-340">**Version/Release**</span></span>  |                                                                                                                                           <span data-ttu-id="8f862-341">請輸入**00401**。</span><span class="sxs-lookup"><span data-stu-id="8f862-341">Enter **00401**.</span></span>                                                                                                                                            |
      | <span data-ttu-id="8f862-342">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="8f862-342">**Target namespace**</span></span> |                                                                                                                    <span data-ttu-id="8f862-343">選取  **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**。</span><span class="sxs-lookup"><span data-stu-id="8f862-343">Select **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**.</span></span>                                                                                                                    |
      |       <span data-ttu-id="8f862-344">**GS1**</span><span class="sxs-lookup"><span data-stu-id="8f862-344">**GS1**</span></span>        |                                                                                                <span data-ttu-id="8f862-345">確認已選取測試訊息的訊息類型，例如**TX-簡訊 (864)**。</span><span class="sxs-lookup"><span data-stu-id="8f862-345">Verify that the message type of the test message is selected, for example, **TX - Text Message (864)**.</span></span>                                                                                                |
      |       <span data-ttu-id="8f862-346">**GS2**</span><span class="sxs-lookup"><span data-stu-id="8f862-346">**GS2**</span></span>        |                                                                                                                                             <span data-ttu-id="8f862-347">請輸入**01**。</span><span class="sxs-lookup"><span data-stu-id="8f862-347">Enter **01**.</span></span>                                                                                                                                             |
      |       <span data-ttu-id="8f862-348">**GS3**</span><span class="sxs-lookup"><span data-stu-id="8f862-348">**GS3**</span></span>        |                                                                                                                                          <span data-ttu-id="8f862-349">請輸入**7654321**。</span><span class="sxs-lookup"><span data-stu-id="8f862-349">Enter **7654321**.</span></span>                                                                                                                                           |
      |       <span data-ttu-id="8f862-350">**GS4**</span><span class="sxs-lookup"><span data-stu-id="8f862-350">**GS4**</span></span>        | <span data-ttu-id="8f862-351">選取您想要的日期格式。</span><span class="sxs-lookup"><span data-stu-id="8f862-351">Select the date format that you want.</span></span> <span data-ttu-id="8f862-352">選取  **CCYYMMDD**。</span><span class="sxs-lookup"><span data-stu-id="8f862-352">Select **CCYYMMDD**.</span></span> <span data-ttu-id="8f862-353">**注意：** 您必須在下拉式清單中選取值，不只是按一下要顯示預設值的欄位。</span><span class="sxs-lookup"><span data-stu-id="8f862-353">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="8f862-354">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="8f862-354">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span> |
      |       <span data-ttu-id="8f862-355">**GS5**</span><span class="sxs-lookup"><span data-stu-id="8f862-355">**GS5**</span></span>        |                                                                                                                      <span data-ttu-id="8f862-356">選擇您要的時間格式。</span><span class="sxs-lookup"><span data-stu-id="8f862-356">Select the time format that you want.</span></span> <span data-ttu-id="8f862-357">選取  **HHMMSSdd**。</span><span class="sxs-lookup"><span data-stu-id="8f862-357">Select **HHMMSSdd**.</span></span>                                                                                                                       |
      |       <span data-ttu-id="8f862-358">**[GS7]**</span><span class="sxs-lookup"><span data-stu-id="8f862-358">**GS7**</span></span>        |                                                                                                                   <span data-ttu-id="8f862-359">選取  **T-Transportation Data Coordinating Committee (TDCC)**。</span><span class="sxs-lookup"><span data-stu-id="8f862-359">Select **T - Transportation Data Coordinating Committee (TDCC)**.</span></span>                                                                                                                   |
      |       <span data-ttu-id="8f862-360">**GS8**</span><span class="sxs-lookup"><span data-stu-id="8f862-360">**GS8**</span></span>        |                                                                                                                      <span data-ttu-id="8f862-361">確認已輸入 EDI 版本做**00401**。</span><span class="sxs-lookup"><span data-stu-id="8f862-361">Verify that the EDI version has been entered as **00401**.</span></span>                                                                                                                       |


8. <span data-ttu-id="8f862-362">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8f862-362">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-363">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-363">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="8f862-364">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**。</span><span class="sxs-lookup"><span data-stu-id="8f862-364">To successfully create an agreement, both one-way agreement tabs must have values defined for **ISA5**, **ISA6**, **ISA7**, and **ISA8**.</span></span>  

   1.  <span data-ttu-id="8f862-365">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="8f862-365">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  

       > [!NOTE]
       >  <span data-ttu-id="8f862-366">針對此逐步解說中，設定**ISA5**要**ZZ**， **ISA6**至**1234567**， **ISA7**到**ZZ**，並**ISA8**要**7654321**。</span><span class="sxs-lookup"><span data-stu-id="8f862-366">For this walkthrough, set **ISA5** to **ZZ**, **ISA6** to **1234567**, **ISA7** to **ZZ**, and **ISA8** to **7654321**.</span></span>  

9. <span data-ttu-id="8f862-367">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="8f862-367">Click **Apply**.</span></span>  

10. <span data-ttu-id="8f862-368">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8f862-368">Click **OK**.</span></span> <span data-ttu-id="8f862-369">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="8f862-369">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="8f862-370">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="8f862-370">The newly added agreement is enabled by default.</span></span>  

### <a name="testing-the-walkthrough"></a><span data-ttu-id="8f862-371">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="8f862-371">Testing the Walkthrough</span></span>  
 <span data-ttu-id="8f862-372">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="8f862-372">This section provides information on how to test the walkthrough.</span></span>  

##### <a name="to-test-the-solution"></a><span data-ttu-id="8f862-373">測試方案</span><span class="sxs-lookup"><span data-stu-id="8f862-373">To test the solution</span></span>  

1. <span data-ttu-id="8f862-374">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。</span><span class="sxs-lookup"><span data-stu-id="8f862-374">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the Sender.csproj project in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender folder.</span></span>  

2. <span data-ttu-id="8f862-375">在 HttpSender.cs 中，確定下列程式碼行未標記為註解 (緊接在 //Request Asynchronous MDN 註解行底下)：</span><span class="sxs-lookup"><span data-stu-id="8f862-375">In HttpSender.cs, make sure that the following line is not commented out (immediately below the //Request Asynchronous MDN comment line):</span></span>  

   ```  
   Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
   ```  

3. <span data-ttu-id="8f862-376">確定下列程式碼行已標記為註解 (緊接在 //Request Synchronous MDN 註解行底下)：</span><span class="sxs-lookup"><span data-stu-id="8f862-376">Make sure that the following line is commented out (immediately below the //Request Synchronous MDN comment line):</span></span>  

   ```  
   Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
   ```  

4. <span data-ttu-id="8f862-377">建置這個專案。</span><span class="sxs-lookup"><span data-stu-id="8f862-377">Build this project.</span></span>  

5. <span data-ttu-id="8f862-378">在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial。</span><span class="sxs-lookup"><span data-stu-id="8f862-378">In Windows Explorer, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial.</span></span> <span data-ttu-id="8f862-379">在 [記事本] 中開啟 X12_00401_864.edi。</span><span class="sxs-lookup"><span data-stu-id="8f862-379">Open X12_00401_864.edi in Notepad.</span></span> <span data-ttu-id="8f862-380">刪除定義 Disposition-Notification-Options 標頭的一行，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="8f862-380">Delete the line defining the Disposition-Notification-Options header, and then save the file.</span></span>  

6. <span data-ttu-id="8f862-381">在 Windows 檔案總管中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug，然後執行**Sender.exe**。</span><span class="sxs-lookup"><span data-stu-id="8f862-381">In Windows Explorer, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug and execute **Sender.exe**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="8f862-382">這時執行 Sender.exe 會將訊息 X12_00401_864.edi 傳送至 Contoso 虛擬目錄 (BTS http 接收位置)。</span><span class="sxs-lookup"><span data-stu-id="8f862-382">Running Sender.exe in this instance posts the message X12_00401_864.edi to the Contoso virtual directory (the BTS http receive location).</span></span>  

7. <span data-ttu-id="8f862-383">開啟為傳送 EDI 內容所建立的 Contoso 本機資料夾 (\EDI_to_Contoso)。</span><span class="sxs-lookup"><span data-stu-id="8f862-383">Open the Contoso local folder that you created to send the EDI payload to (\EDI_to_Contoso).</span></span> <span data-ttu-id="8f862-384">確認資料夾中有 .XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8f862-384">Verify that there is a .XML file in the folder.</span></span> <span data-ttu-id="8f862-385">開啟這個 XML 檔案，並確認它包含 864 交易集。</span><span class="sxs-lookup"><span data-stu-id="8f862-385">Open the XML file and verify that it contains an 864 transaction set.</span></span>  

8. <span data-ttu-id="8f862-386">開啟要將 MDN 傳回到的 Fabrikam 本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f862-386">Open the Fabrikam local folder to which the MDN is returned.</span></span> <span data-ttu-id="8f862-387">在 Windows 檔案總管中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam。</span><span class="sxs-lookup"><span data-stu-id="8f862-387">In Windows Explorer, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam.</span></span> <span data-ttu-id="8f862-388">在記事本中開啟訊息檔案並確認 MDN。</span><span class="sxs-lookup"><span data-stu-id="8f862-388">Open the message file in a notepad and verify the MDN.</span></span> <span data-ttu-id="8f862-389">確認 MDN 的 AS2-From 是 Contoso，而 AS2-To 則是 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="8f862-389">Verify that in the MDN AS2-From is Contoso and AS2-To is Fabrikam.</span></span>  

9. <span data-ttu-id="8f862-390">在 [記事本] 中開啟測試訊息 X12_00401_864.edi，並確認 \EDI_to_Contoso 本機資料夾中輸出訊息的交易集對應至 X12_00401_864.edi 輸入訊息的交易集。</span><span class="sxs-lookup"><span data-stu-id="8f862-390">Open the test message X12_00401_864.edi in Notepad, and verify that the transaction set in the output message in the \EDI_to_Contoso local folder corresponds to the transaction set in the X12_00401_864.edi input message.</span></span>  

## <a name="see-also"></a><span data-ttu-id="8f862-391">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f862-391">See Also</span></span>  
 [<span data-ttu-id="8f862-392">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="8f862-392">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)