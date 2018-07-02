---
title: '逐步解說 (AS2): 使用非同步 MDN 透過 AS2 傳送 EDI |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83644ac9-7023-4b09-966c-7c41d36f6b11
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56bdad99f9929c298aa6a047f7c20667f6f7d924
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974503"
---
# <a name="walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn"></a><span data-ttu-id="d4aca-102">逐步解說 (AS2)：使用非同步 MDN 透過 AS2 傳送 EDI</span><span class="sxs-lookup"><span data-stu-id="d4aca-102">Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN</span></span>
<span data-ttu-id="d4aca-103">本逐步解說提供一組逐步執行的程序，建立使用非同步 MDN 透過 AS2 傳送 EDI 訊息的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-103">This walkthrough provides a set of step-by-step procedures that creates a solution for sending EDI messages over AS2, with an asynchronous MDN.</span></span>  <span data-ttu-id="d4aca-104">您可以建立並測試完整的解決方案，在單一電腦上的這個逐步解說</span><span class="sxs-lookup"><span data-stu-id="d4aca-104">You can create and test the full solution in this walkthrough on a single computer</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4aca-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="d4aca-105">Prerequisites</span></span>  
 <span data-ttu-id="d4aca-106">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="d4aca-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
- <span data-ttu-id="d4aca-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="d4aca-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
- <span data-ttu-id="d4aca-108">執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。</span><span class="sxs-lookup"><span data-stu-id="d4aca-108">The computer that runs the walkthrough must have Internet Information Services (IIS) 7 installed.</span></span>  
  
- <span data-ttu-id="d4aca-109">若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。</span><span class="sxs-lookup"><span data-stu-id="d4aca-109">If the computer that runs the walkthrough is installed with a 64-bit version of Windows, you must ensure that the BizTalk hosts are marked as 32-bit only.</span></span> <span data-ttu-id="d4aca-110">您也必須確定 IIS 已將應用程式集區的「啟用 32 位元應用程式」設定為 True。</span><span class="sxs-lookup"><span data-stu-id="d4aca-110">You must also ensure IIS has the Enable 32-Bit Application Setting for the Application Pools set to True.</span></span> <span data-ttu-id="d4aca-111">如需詳細資訊，請參閱 <<c0> [ 教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aca-111">For more information, see [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md).</span></span>  
  
## <a name="how-the-solution-sends-an-edias2-message-and-returns-an-asynchronous-mdn"></a><span data-ttu-id="d4aca-112">解決方案傳送 EDI/AS2 訊息並傳回非同步 MDN 的方式</span><span class="sxs-lookup"><span data-stu-id="d4aca-112">How the Solution Sends an EDI/AS2 Message and Returns an Asynchronous MDN</span></span>  
 <span data-ttu-id="d4aca-113">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d4aca-113">The solution will do the following:</span></span>  
  
1. <span data-ttu-id="d4aca-114">單向 FILE 接收埠從 Contoso 接收 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="d4aca-114">A one-way FILE receive port receives an EDI interchange from Contoso.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-115">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="d4aca-115">The events in this list may not occur in the order shown.</span></span>  
  
2. <span data-ttu-id="d4aca-116">藉由使用通過接收管線，接收埠將測試訊息保留原狀置放在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-116">Using a passthrough receive pipeline, the receive port drops the test message into the MeassageBox unchanged.</span></span>  
  
3. <span data-ttu-id="d4aca-117">靜態單向傳送埠取用 EDI 交換，並將其編碼為 AS2 格式。</span><span class="sxs-lookup"><span data-stu-id="d4aca-117">A static one-way send port picks up the EDI interchange and encodes it into AS2 format.</span></span>  
  
4. <span data-ttu-id="d4aca-118">傳送埠透過 AS2 傳輸，將 EDI 交換傳送到 Fabrikam 合作對象。</span><span class="sxs-lookup"><span data-stu-id="d4aca-118">The send port sends the EDI interchange over AS2 transport to the Fabrikam party.</span></span>  
  
5. <span data-ttu-id="d4aca-119">Fabrikam 的單向接收埠使用 Fabrikam 虛擬目錄接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-119">The one-way receive port at Fabrikam receives the AS2 message using the Fabrikam virtual directory.</span></span> <span data-ttu-id="d4aca-120">接收管線會解碼來自 AS2 的 EDI 交換，然後將 EDI 交換置放在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-120">The receive pipeline decodes the EDI interchange from AS2, and drops the EDI interchange into the MessageBox.</span></span>  
  
6. <span data-ttu-id="d4aca-121">同一個單向接收埠還會產生 MDN，然後將 MDN 置放在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-121">The same one-way receive port also generates an MDN and drops the MDN into the MessageBox.</span></span>  
  
7. <span data-ttu-id="d4aca-122">靜態單向傳送埠取用 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-122">A static one-way send port pick up the EDI message.</span></span>  
  
8. <span data-ttu-id="d4aca-123">靜態單向傳送埠將 EDI 訊息傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-123">The static one-way send port sends the EDI message to a local folder.</span></span>  
  
9. <span data-ttu-id="d4aca-124">單向動態傳送埠取用非同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="d4aca-124">A one-way dynamic send port picks up the asynchronous MDN.</span></span>  
  
10. <span data-ttu-id="d4aca-125">單向動態傳送埠將 MDN 傳送至 Contoso。</span><span class="sxs-lookup"><span data-stu-id="d4aca-125">The one-way dynamic send port sends the MDN to Contoso.</span></span>  
  
11. <span data-ttu-id="d4aca-126">單向接收埠接收 MDN，然後將 MDN 置放在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-126">A one-way receive port receives the MDN, and drops it into the MessageBox.</span></span>  
  
12. <span data-ttu-id="d4aca-127">具有通過傳送管線的靜態單向傳送埠會拾取該 MDN。</span><span class="sxs-lookup"><span data-stu-id="d4aca-127">A static one-way send port with a passthrough send pipeline picks up the MDN.</span></span>  
  
13. <span data-ttu-id="d4aca-128">單向傳送埠會將 MDN 傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-128">The one-way send port sends the MDN to a local folder.</span></span>  
  
    <span data-ttu-id="d4aca-129">下圖顯示這個解決方案的架構。</span><span class="sxs-lookup"><span data-stu-id="d4aca-129">The following figure shows the architecture for this solution.</span></span>  
  
    <span data-ttu-id="d4aca-130">![使用非同步 MDN 的 AS2 傳送](../core/media/343bbfcc-5387-426c-8700-db9738816218.gif "343bbfcc-5387-426c-8700-db9738816218")</span><span class="sxs-lookup"><span data-stu-id="d4aca-130">![AS2 sending with an asynchronous MDN](../core/media/343bbfcc-5387-426c-8700-db9738816218.gif "343bbfcc-5387-426c-8700-db9738816218")</span></span>  
  
## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="d4aca-131">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="d4aca-131">The Functionality in this Solution</span></span>  
 <span data-ttu-id="d4aca-132">下列項目適用於本逐步解說的功能：</span><span class="sxs-lookup"><span data-stu-id="d4aca-132">The following applies to the functionality of this walkthrough:</span></span>  
  
-   <span data-ttu-id="d4aca-133">這個逐步解說是處理 AS2 功能，而非 EDI 功能。</span><span class="sxs-lookup"><span data-stu-id="d4aca-133">This walkthrough deals with AS2 functionality, not EDI functionality.</span></span> <span data-ttu-id="d4aca-134">因此，與 AS2 處理有關的所有連接埠都是使用 AS2Receive 或 AS2Send 管線，而非 AS2EdiReceive 或 AS2EdiSend。</span><span class="sxs-lookup"><span data-stu-id="d4aca-134">As a result, all ports involved in AS2 processing use either AS2Receive or AS2Send pipelines, not AS2EdiReceive or AS2EdiSend.</span></span> <span data-ttu-id="d4aca-135">與 AS2 處理無關的連接埠，則使用 PassThruReceive 或 PassThruTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="d4aca-135">Ports that are not involved in AS2 processing use PassThruReceive or PassThruTransmit pipelines.</span></span>  
  
-   <span data-ttu-id="d4aca-136">沒有啟用狀態報告。</span><span class="sxs-lookup"><span data-stu-id="d4aca-136">Status reporting is not enabled.</span></span>  
  
-   <span data-ttu-id="d4aca-137">這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。</span><span class="sxs-lookup"><span data-stu-id="d4aca-137">This solution does not configure signing, compression, encryption, or message storage in the non-repudiation database.</span></span> <span data-ttu-id="d4aca-138">如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aca-138">For procedures on configuring those properties, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).</span></span>  
  
## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="d4aca-139">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="d4aca-139">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="d4aca-140">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d4aca-140">The procedures required for this solution include the following:</span></span>  
  
- <span data-ttu-id="d4aca-141">使用必要的訊息結構描述來建置並部署 BizTalk 專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的交換。</span><span class="sxs-lookup"><span data-stu-id="d4aca-141">Build and deploy a BizTalk project with the required message schema, making the schema available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the received interchange.</span></span>  
  
- <span data-ttu-id="d4aca-142">讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-142">Enable the BTS ISAPI filter used in receiving the AS2 message.</span></span>  
  
- <span data-ttu-id="d4aca-143">建立 Fabrikam 虛擬目錄，用於接收 Contoso 的 AS2 訊息，如接收位置中所設定。</span><span class="sxs-lookup"><span data-stu-id="d4aca-143">Create a Fabrikam virtual directory that receives the AS2 message from Contoso, as configured in the receive location.</span></span>  
  
- <span data-ttu-id="d4aca-144">建立會從 Fabrikam 接收 AS2 訊息的 Contoso 虛擬目錄 (如接收位置中所設定)。</span><span class="sxs-lookup"><span data-stu-id="d4aca-144">Create a Contoso virtual directory that receives the AS2 message from Fabrikam, as configured in the receive location.</span></span>  
  
- <span data-ttu-id="d4aca-145">指定 Fabrikam 和 Contoso 虛擬目錄不是由 Windows SharePoint Services 管理。</span><span class="sxs-lookup"><span data-stu-id="d4aca-145">Specify that the Fabrikam and Contoso virtual directories are not managed by Windows SharePoint Services.</span></span>  
  
- <span data-ttu-id="d4aca-146">建立單向 FILE 接收埠，接收要透過 AS2 傳輸來傳送的 EDI 測試訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-146">Create a one-way FILE receive port to receive the EDI test message that will be sent via AS2 transport.</span></span> <span data-ttu-id="d4aca-147">建立本機資料夾，接收測試訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-147">Create the local folder to receive the test message.</span></span>  
  
- <span data-ttu-id="d4aca-148">建立靜態單向 HTTP 傳送埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送包含 EDI 商業文件的 AS2 訊息給 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="d4aca-148">Create a static one-way HTTP send port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send the AS2 message containing the EDI business document to Fabrikam.</span></span> <span data-ttu-id="d4aca-149">將傳送管線設定為 AS2Send 管線。</span><span class="sxs-lookup"><span data-stu-id="d4aca-149">Configure the send pipeline to be the AS2Send pipeline.</span></span>  
  
- <span data-ttu-id="d4aca-150">建立單向 HTTP 接收埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-150">Create a one-way HTTP receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the AS2 message.</span></span> <span data-ttu-id="d4aca-151">請將接收管線設定為 AS2Receive 管線。</span><span class="sxs-lookup"><span data-stu-id="d4aca-151">Configure the receive pipeline to be the AS2Receive pipeline.</span></span> <span data-ttu-id="d4aca-152">設定接收位置，以透過 Fabrikam 虛擬目錄接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-152">Configure the receive location to receive the AS2 message via the Fabrikam virtual directory.</span></span>  
  
- <span data-ttu-id="d4aca-153">建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，以將訊息內容路由傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-153">Create a static one-way FILE send port (with a passthrough send pipeline) to route the message payload to a local folder.</span></span> <span data-ttu-id="d4aca-154">建立本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-154">Create the local folder.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="d4aca-155">如果您沒有傳送埠可以訂閱訊息內容，那麼訊息內容就會擱置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-155">If you do not have a send port to subscribe to the message payload, it will be suspended in the MessageBox.</span></span>  
  
- <span data-ttu-id="d4aca-156">建立動態單向 HTTP 傳送埠，將 MDN 傳回 Contoso。</span><span class="sxs-lookup"><span data-stu-id="d4aca-156">Create a dynamic one-way HTTP send port to return the MDN to Contoso.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="d4aca-157">測試解決方案位於單一電腦上，因此，用於傳送 AS2 訊息 (來自 Contoso) 的單向傳送埠和用於傳送 MDN 訊息 (來自 Fabrikam) 的單向傳送埠皆位於相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="d4aca-157">The test solution is on a single computer; as a result, the one-way send port sending the AS2 message (from Contoso) and the one-way send port sending the MDN response (from Fabrikam) are on the same computer.</span></span>  
  
- <span data-ttu-id="d4aca-158">建立單向接收埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收來自 Fabrikam 的 MDN 回應。</span><span class="sxs-lookup"><span data-stu-id="d4aca-158">Create a one-way receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the MDN response from Fabrikam.</span></span>  
  
- <span data-ttu-id="d4aca-159">建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，以將 MDN 路由傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-159">Create a static one-way FILE send port (with a passthrough send pipeline) to route the MDN to a local folder.</span></span> <span data-ttu-id="d4aca-160">建立本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-160">Create the local folder.</span></span>  
  
- <span data-ttu-id="d4aca-161">為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="d4aca-161">Create a party (trading partner) for both Fabrikam and Contoso.</span></span>  
  
- <span data-ttu-id="d4aca-162">為這兩個交易合作對象各建立一個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4aca-162">Create a business profile each for both the trading parties.</span></span>  
  
- <span data-ttu-id="d4aca-163">在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="d4aca-163">Create an AS2 agreement between the business profiles for Fabrikam and Contoso.</span></span> <span data-ttu-id="d4aca-164">這個 AS2 協議包含的屬性將可用來傳送 AS2 訊息並接收回傳的同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="d4aca-164">The AS2 agreement would contain properties to send an AS2 message and receive an asynchronous MDN in return.</span></span>  
  
- <span data-ttu-id="d4aca-165">使用測試 EDI 交換以測試逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d4aca-165">Test the walkthrough using a test EDI interchange.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="d4aca-166">對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-166">For a test message, you can use the SamplePO.txt file that is used in the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="d4aca-167">該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\SDK\EDI Interface Developer Tutorial\ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-167">That file is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\SDK\EDI Interface Developer Tutorial\ folder.</span></span> <span data-ttu-id="d4aca-168">這是 X12 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4aca-168">This is an X12 850 message.</span></span>  
  
### <a name="configuring-the-walkthrough"></a><span data-ttu-id="d4aca-169">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="d4aca-169">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="d4aca-170">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="d4aca-170">This section describes the procedures to configure the walkthrough.</span></span>  
  
##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="d4aca-171">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="d4aca-171">To deploy the message schema</span></span>  
  
1. <span data-ttu-id="d4aca-172">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-172">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-173">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="d4aca-173">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="d4aca-174">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="d4aca-174">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
2. <span data-ttu-id="d4aca-175">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-175">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="d4aca-176">若要使用 SamplePO.txt 檔案來測試您的解決方案，請移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-176">To use the SamplePO.txt file to test your solution, move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI folder.</span></span> <span data-ttu-id="d4aca-177">選取 X12_00401_850.xsd 結構描述，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-177">Select the X12_00401_850.xsd schema, and then click **Add**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-178">若要使用不同的 EDI 結構描述，請移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_SchemaEDI 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-178">To use a different EDI schema, go to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_SchemaEDI folder.</span></span> <span data-ttu-id="d4aca-179">如果 EDI 結構描述尚未解壓縮至 XSD_SchemaEDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** XSD_SchemaEDI 資料夾結構描述解壓縮至預設資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-179">If the EDI schemas have not been unzipped into the XSD_SchemaEDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the XSD_SchemaEDI folder to unzip the schemas into the default folder.</span></span>  
  
3. <span data-ttu-id="d4aca-180">設定組件金鑰檔案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="d4aca-180">Set the assembly key file, and then build and deploy the assembly.</span></span>  
  
##### <a name="to-enable-the-bts-isapi-filter"></a><span data-ttu-id="d4aca-181">若要啟用 BTS ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="d4aca-181">To enable the BTS ISAPI Filter</span></span>  
  
1. <span data-ttu-id="d4aca-182">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="d4aca-182">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
   > [!TIP]
   >  <span data-ttu-id="d4aca-183">視作業系統而定，[系統管理工具] 開始功能表選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="d4aca-183">Depending on the operating system, the Administrative Tools start menu option may not be available.</span></span> <span data-ttu-id="d4aca-184">在這種情況下，按一下**開始**，按一下**執行**，然後輸入`inetmgr`以開啟 Internet Information Services (IIS) 管理員。</span><span class="sxs-lookup"><span data-stu-id="d4aca-184">In such cases, click **Start**, click **Run**, and enter `inetmgr` to open Internet Information Services (IIS) Manager.</span></span>  
  
2. <span data-ttu-id="d4aca-185">選取根 Web 伺服器項目並在**功能檢視**，按兩下**處理常式對應**，然後在 動作 窗格中的，按一下 **新增指令碼對應**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-185">Select the root Web Server entry and in the **Features View**, double click **Handler Mappings** and then in the Actions pane click **Add Script Map**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-186">在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。</span><span class="sxs-lookup"><span data-stu-id="d4aca-186">Configuring the script mapping at the Web Server level will cause this mapping to apply to all child Web Sites.</span></span> <span data-ttu-id="d4aca-187">若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d4aca-187">If you wish to restrict the mapping to a specific Web Site or Virtual Folder, select the target site or folder instead of the Web Server.</span></span>  
  
3. <span data-ttu-id="d4aca-188">在 **新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。</span><span class="sxs-lookup"><span data-stu-id="d4aca-188">In the **Add Script Map** dialog box, enter `BtsHttpReceive.dll` in the **Request path** field.</span></span>  
  
4. <span data-ttu-id="d4aca-189">在 **可執行檔**欄位中，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="d4aca-189">In the **Executable** field, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span></span> <span data-ttu-id="d4aca-190">選取 BtsHttpReceive.dll，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-190">Select BtsHttpReceive.dll and click **OK**.</span></span>  
  
5. <span data-ttu-id="d4aca-191">請輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-191">Enter `BizTalk HTTP Receive` in the `Name` field, and then click **Request Restrictions**.</span></span>  
  
6. <span data-ttu-id="d4aca-192">在 **要求限制**對話方塊中，選取**動詞**索引標籤，然後選取**其中一個下列的指令動詞**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-192">In the **Request Restrictions** dialog box, select the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="d4aca-193">輸入`POST`作為動詞。</span><span class="sxs-lookup"><span data-stu-id="d4aca-193">Enter `POST` as the verb.</span></span>  
  
7. <span data-ttu-id="d4aca-194">在上**存取權**索引標籤上，選取**指令碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-194">On the **Access** tab, select **Script** and then click **OK**.</span></span>  
  
8. <span data-ttu-id="d4aca-195">按一下  **確定**當系統提示您允許 ISAPI 延伸模組時，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-195">Click **OK** and when prompted to allow the ISAPI extension, click **Yes**.</span></span>  
  
##### <a name="to-configure-the-fabrikam-web-page"></a><span data-ttu-id="d4aca-196">若要設定 Fabrikam 網頁</span><span class="sxs-lookup"><span data-stu-id="d4aca-196">To configure the Fabrikam Web page</span></span>  
  
1. <span data-ttu-id="d4aca-197">在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，然後選取**新增應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-197">In IIS Manager, right-click **Application Pools** and select **Add Application Pool**.</span></span>  
  
2. <span data-ttu-id="d4aca-198">在**新增的應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-198">In the **Add Application Pool** dialog box, enter **BizTalkAppPool** in **Name**, and then select **.NET Framework V4.0.30210** in the **.NET Framework version** dropdown list.</span></span> <span data-ttu-id="d4aca-199">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-199">Click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-200">版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="d4aca-200">The version number may vary depending on the version of [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installed on the machine.</span></span>  
  
3. <span data-ttu-id="d4aca-201">選取**應用程式集區**，請在**功能檢視**選取**BizTalkAppPool**，然後按一下**進階設定**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="d4aca-201">Select **Application Pools**, in the **Features View** select **BizTalkAppPool**, and then click **Advanced Settings** in the **Actions** pane.</span></span>  
  
4. <span data-ttu-id="d4aca-202">在 [**進階設定]** 對話方塊中，選取**識別**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d4aca-202">In the **Advanced Settings** dialog box, select **Identity** and then click the ellipsis (…) button.</span></span>  
  
5. <span data-ttu-id="d4aca-203">在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-203">In the **Application Pool Identity** dialog box, select **Custom account** and then click **Set**.</span></span>  
  
6. <span data-ttu-id="d4aca-204">輸入**使用者名**並**密碼**使用者帳戶，系統管理員群組的成員，請輸入中的密碼**確認密碼**，然後按一下  **確定**三次，以返回 IIS 管理員。</span><span class="sxs-lookup"><span data-stu-id="d4aca-204">Enter the **User name** and **Password** for a user account that is a member of the administrators group, enter the password in **Confirm password** and then click **OK** three times to return to the IIS Manager.</span></span>  
  
7. <span data-ttu-id="d4aca-205">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-205">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="d4aca-206">使用滑鼠右鍵按一下 [預設的網站]，然後選取 [新增應用程式]。</span><span class="sxs-lookup"><span data-stu-id="d4aca-206">Right-click the Default Web Site and then select Add Application.</span></span>  
  
8. <span data-ttu-id="d4aca-207">在 **新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-207">In the **Add Application** dialog box, enter **Fabrikam** in **Alias**, and then click **Select**.</span></span>  
  
9. <span data-ttu-id="d4aca-208">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-208">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
10. <span data-ttu-id="d4aca-209">按一下省略符號 （...） 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]針對 HttpReceive**實體路徑**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-209">Click the ellipsis (…) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
11. <span data-ttu-id="d4aca-210">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-210">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="d4aca-211">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d4aca-211">Click **Close**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="d4aca-212">在 [IIS 管理員] 中，選取 Contoso 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-212">In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  
  
13. <span data-ttu-id="d4aca-213">在 **驗證**，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-213">In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="d4aca-214">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="d4aca-214">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
##### <a name="to-configure-the-contoso-web-page"></a><span data-ttu-id="d4aca-215">若要設定 Contoso 網頁</span><span class="sxs-lookup"><span data-stu-id="d4aca-215">To configure the Contoso Web page</span></span>  
  
1. <span data-ttu-id="d4aca-216">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-216">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="d4aca-217">使用滑鼠右鍵按一下 [預設的網站]，然後選取 [新增應用程式]。</span><span class="sxs-lookup"><span data-stu-id="d4aca-217">Right-click the Default Web Site and then select Add Application.</span></span>  
  
2. <span data-ttu-id="d4aca-218">在 **新增應用程式**對話方塊方塊中，輸入**Contoso**中**別名**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-218">In the **Add Application** dialog box, enter **Contoso** in **Alias**, and then click **Select**.</span></span>  
  
3. <span data-ttu-id="d4aca-219">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-219">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
4. <span data-ttu-id="d4aca-220">按一下省略符號 （...） 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]針對 HttpReceive**實體路徑**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-220">Click the ellipsis (…) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
5. <span data-ttu-id="d4aca-221">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-221">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="d4aca-222">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d4aca-222">Click **Close**, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-223">在 [IIS 管理員] 中，選取 Contoso 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-223">In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  
  
7. <span data-ttu-id="d4aca-224">在 **驗證**，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-224">In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="d4aca-225">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="d4aca-225">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
##### <a name="to-specify-that-the-fabrikam-and-contoso-virtual-directories-are-not-managed-by-windows-sharepoint-services"></a><span data-ttu-id="d4aca-226">若要指定 Fabrikam 和 Contoso 虛擬目錄不是由 Windows SharePoint Services 管理</span><span class="sxs-lookup"><span data-stu-id="d4aca-226">To specify that the Fabrikam and Contoso virtual directories are not managed by Windows SharePoint Services</span></span>  
  
1.  <span data-ttu-id="d4aca-227">如果 Windows SharePoint Services 安裝在電腦上，按一下**開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-227">If Windows SharePoint Services is installed on your computer, click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4aca-228">如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="d4aca-228">This procedure is required if Windows SharePoint Server is installed on the same computer that you are setting the walkthrough up on.</span></span> <span data-ttu-id="d4aca-229">在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。</span><span class="sxs-lookup"><span data-stu-id="d4aca-229">In that case, you must specify that your IIS virtual directory is not being managed by Windows SharePoint Server.</span></span>  
  
2.  <span data-ttu-id="d4aca-230">在上**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-230">On the **Central Administration** page, under **Central Administration**, click **Application Management**.</span></span>  
  
3.  <span data-ttu-id="d4aca-231">在 **應用程式管理**頁面上，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-231">On the **Application Management** page, click **Define managed paths**.</span></span>  
  
4.  <span data-ttu-id="d4aca-232">在 **定義管理的路徑**頁面的 **加入新路徑**，請在**路徑**文字方塊中，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="d4aca-232">In the **Define Managed Paths** page, under **Add a New Path**, in the **Path** text box, enter `Fabrikam`.</span></span> <span data-ttu-id="d4aca-233">底下**型別**，按一下**排除的路徑**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-233">Under **Type**, click **Excluded Path**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="d4aca-234">針對 Contoso 虛擬目錄重複步驟 4。</span><span class="sxs-lookup"><span data-stu-id="d4aca-234">Repeat step 4 for the Contoso virtual directory.</span></span>  
  
6.  <span data-ttu-id="d4aca-235">關閉**定義管理的路徑**頁面。</span><span class="sxs-lookup"><span data-stu-id="d4aca-235">Close the **Define Managed Paths** page.</span></span>  
  
##### <a name="to-create-a-receive-port-to-receive-the-edi-test-message"></a><span data-ttu-id="d4aca-236">若要建立接收埠以接收 EDI 測試訊息</span><span class="sxs-lookup"><span data-stu-id="d4aca-236">To create a receive port to receive the EDI test message</span></span>  
  
1. <span data-ttu-id="d4aca-237">在 Windows 檔案總管中，建立本機資料夾，以接收來自 Contoso 的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="d4aca-237">In Windows Explorer, create a local folder to receive the EDI interchange from Contoso.</span></span>  
  
2. <span data-ttu-id="d4aca-238">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-238">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3. <span data-ttu-id="d4aca-239">接收埠命名為**RecvISAFromCont**，然後按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-239">Name the receive port as **RecvISAFromCont**, and then click **Receive Locations** in the console tree.</span></span>  
  
4. <span data-ttu-id="d4aca-240">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-240">Click **New**.</span></span>  
  
5. <span data-ttu-id="d4aca-241">接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-241">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
6. <span data-ttu-id="d4aca-242">針對**接收資料夾**，輸入您在步驟 1 中建立資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4aca-242">For **Receive folder**, enter the name of the folder that you created in step 1.</span></span>  
  
7. <span data-ttu-id="d4aca-243">在 [檔案遮罩] 中，輸入檔案副檔名。</span><span class="sxs-lookup"><span data-stu-id="d4aca-243">For File mask, enter the extension of your file.</span></span> <span data-ttu-id="d4aca-244">如果您使用 SamplePO.txt 檔案做為測試訊息，請輸入 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-244">If you are using the SamplePO.txt file as your test message, enter **\*.txt**.</span></span> <span data-ttu-id="d4aca-245">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-245">Click **OK**.</span></span>  
  
8. <span data-ttu-id="d4aca-246">針對**接收管線**，接受預設值是**PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-246">For **Receive pipeline**, accept the default of **PassThruReceive**.</span></span>  
  
9. <span data-ttu-id="d4aca-247">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="d4aca-247">Click **OK**, and then click **OK** again.</span></span>  
  
10. <span data-ttu-id="d4aca-248">按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-248">Click the **Receive Locations** node, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-send-port-to-send-the-edi-interchange-over-as2-to-fabrikam"></a><span data-ttu-id="d4aca-249">若要建立傳送埠以透過 AS2 將 EDI 交換傳送至 Fabrikam</span><span class="sxs-lookup"><span data-stu-id="d4aca-249">To create a send port to send the EDI interchange over AS2 to Fabrikam</span></span>  
  
1. <span data-ttu-id="d4aca-250">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-250">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2. <span data-ttu-id="d4aca-251">在 [**傳送埠屬性**] 對話方塊中，將傳送埠命名為**SendISAToFab**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-251">In the **Send Port Properties** dialog box, name the send port as **SendISAToFab**.</span></span>  
  
3. <span data-ttu-id="d4aca-252">在 **傳輸**區段中，選取**HTTP**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-252">In the **Transport** section, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="d4aca-253">在 [ **HTTP 傳輸屬性**] 對話方塊中，如**目的地 URL**，輸入**http://localhost/Fabrikam/BTSHttpReceive.dll**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-253">In the **HTTP Transport Properties** dialog box, for **Destination URL**, enter **http://localhost/Fabrikam/BTSHttpReceive.dll**.</span></span>  
  
5. <span data-ttu-id="d4aca-254">清除**啟用區塊編碼**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-254">Clear **Enable Chunked Encoding**, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-255">在 **傳送管線**，選取**AS2Send**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-255">In **Send pipeline**, select **AS2Send**.</span></span>  
  
7. <span data-ttu-id="d4aca-256">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-256">In the console tree, select **Filters**.</span></span> <span data-ttu-id="d4aca-257">針對**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 及針對**值**輸入將接收 EDI 接收埠的名稱交換 (`RecvISAFromCont`)。</span><span class="sxs-lookup"><span data-stu-id="d4aca-257">For **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; and for **Value** enter the name of the receive port that will receive the EDI interchange (`RecvISAFromCont`).</span></span>  
  
8. <span data-ttu-id="d4aca-258">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-258">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d4aca-259">按一下 **傳送埠**節點在管理主控台中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-259">Click the **Send Ports** node in the Administration Console, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-receive-port-for-fabrikam-to-receive-the-as2-message"></a><span data-ttu-id="d4aca-260">若要為 Fabrikam 建立接收埠以接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="d4aca-260">To create a receive port for Fabrikam to receive the AS2 message</span></span>  
  
1. <span data-ttu-id="d4aca-261">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **單向接收埠**.</span><span class="sxs-lookup"><span data-stu-id="d4aca-261">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, under the BizTalk Application 1 node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2. <span data-ttu-id="d4aca-262">接收埠命名為**RecvAS2ForFabrikam**，然後按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-262">Name the receive port as **RecvAS2ForFabrikam**, and then click **Receive Locations** in the console tree.</span></span>  
  
3. <span data-ttu-id="d4aca-263">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-263">Click **New**.</span></span>  
  
4. <span data-ttu-id="d4aca-264">中**接收位置屬性**對話方塊中，名稱您接收位置中，選取**HTTP**如**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-264">In the **Receive Location Properties** dialog box, name your receive location, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
5. <span data-ttu-id="d4aca-265">在  **HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Fabrikam/BTSHttpReceive.dll** for**虛擬目錄加 ISAPI 延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-265">In the **HTTP Transport Properties** dialog box, enter **/Fabrikam/BTSHttpReceive.dll** for **Virtual directory plus ISAPI extension**.</span></span> <span data-ttu-id="d4aca-266">清除**成功時傳回相互關聯控制代碼**，然後選取**擱置失敗的要求**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-266">Clear **Return correlation handle on success** and select **Suspend failed requests**.</span></span> <span data-ttu-id="d4aca-267">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-267">Click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-268">選取  **AS2Receive** for**接收管線**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-268">Select **AS2Receive** for the **Receive Pipeline**.</span></span> <span data-ttu-id="d4aca-269">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="d4aca-269">Click **OK**, and then click **OK** again.</span></span>  
  
7. <span data-ttu-id="d4aca-270">按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-270">Click the **Receive Locations** node, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a><span data-ttu-id="d4aca-271">若要建立傳送埠以將 EDI 內容傳送至本機資料夾</span><span class="sxs-lookup"><span data-stu-id="d4aca-271">To create a send port to send the EDI payload to a local folder</span></span>  
  
1. <span data-ttu-id="d4aca-272">在 Windows 檔案總管中，建立本機資料夾，以便將 EDI 交換傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-272">In Windows Explorer, create a local folder to send the EDI interchange to.</span></span>  
  
2. <span data-ttu-id="d4aca-273">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-273">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
3. <span data-ttu-id="d4aca-274">在 **傳送埠屬性**對話方塊中，將傳送埠作為**SendEDIToFab**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-274">In the **Send Port Properties** dialog box, name your send port as **SendEDIToFab**.</span></span> <span data-ttu-id="d4aca-275">選取 **檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-275">Select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="d4aca-276">在 [ **FILE 傳輸屬性**] 對話方塊中，如**目的地資料夾**，輸入您建立之 EDI 內容的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-276">In the **FILE Transport Properties** dialog box, for **Destination folder**, enter the local folder that you created for the EDI payload.</span></span>  
  
5. <span data-ttu-id="d4aca-277">針對**檔案名**，輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d4aca-277">For **File name**, enter the file name.</span></span> <span data-ttu-id="d4aca-278">如果您使用 SamplePO.txt 檔案做為測試訊息，請輸入 **%MessageID%.txt**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-278">If you are using the SamplePO.txt file as your test message, enter **%MessageID%.txt**.</span></span> <span data-ttu-id="d4aca-279">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-279">Click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-280">接受預設值是**PassThruTransmit** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-280">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  
  
7. <span data-ttu-id="d4aca-281">按一下 **篩選器**在主控台樹狀結構，並加入挑選 EDI 內容的篩選屬性。</span><span class="sxs-lookup"><span data-stu-id="d4aca-281">Click **Filters** in the console tree, and add filter properties for picking up the EDI payload.</span></span> <span data-ttu-id="d4aca-282">在第一行，如**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 對於**值**，輸入接收的 AS2 接收埠的名稱訊息 (`RecvAS2ForFabrikam`); 至於**分組**，接受**和**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-282">On the first line, for **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; for **Value**, enter the name of the receive port that receives the AS2 message (`RecvAS2ForFabrikam`); and for **Group by**, accept **And**.</span></span> <span data-ttu-id="d4aca-283">在第二行，如**屬性**，輸入**EdiIntAS.IsAS2PayloadMessage**; 對於**運算子**，輸入**==**; 以及**值**，輸入 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-283">On the second line, for **Property**, enter **EdiIntAS.IsAS2PayloadMessage**; for **Operator**, enter **==**; and for **Value**, enter **True**.</span></span>  
  
8. <span data-ttu-id="d4aca-284">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-284">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d4aca-285">按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-285">Click the **Send Ports** node, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-dynamic-one-way-send-port-to-return-the-mdn"></a><span data-ttu-id="d4aca-286">若要建立動態單向傳送埠以傳回 MDN</span><span class="sxs-lookup"><span data-stu-id="d4aca-286">To create a dynamic one-way send port to return the MDN</span></span>  
  
1. <span data-ttu-id="d4aca-287">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **動態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-287">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Send Ports**, point to **New**, and then click **Dynamic One-Way Send Port**.</span></span>  
  
2. <span data-ttu-id="d4aca-288">在 **傳送埠屬性**對話方塊中，將傳送埠作為**Send_MDN**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-288">In the **Send Port Properties** dialog box, name your send port as **Send_MDN**.</span></span>  
  
3. <span data-ttu-id="d4aca-289">針對**傳送管線**，請輸入 AS2Send。</span><span class="sxs-lookup"><span data-stu-id="d4aca-289">For **Send Pipeline**, enter AS2Send.</span></span>  
  
4. <span data-ttu-id="d4aca-290">按一下 **篩選器**在主控台樹狀結構，並加入挑選 EDI 內容的篩選屬性。</span><span class="sxs-lookup"><span data-stu-id="d4aca-290">Click **Filters** in the console tree, and add filter properties for picking up the EDI payload.</span></span> <span data-ttu-id="d4aca-291">在第一行，如**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 對於**值**，輸入接收的 AS2 接收埠的名稱訊息 (`RecvAS2ForFabrikam`); 至於**分組**，接受**和**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-291">On the first line, for **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; for **Value**, enter the name of the receive port that receives the AS2 message (`RecvAS2ForFabrikam`); and for **Group by**, accept **And**.</span></span> <span data-ttu-id="d4aca-292">在第二行，如**屬性**，輸入**EdiIntAS.IsAS2AsynchronousMDN**; 對於**運算子**，輸入**==**; 以及**值**，輸入 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-292">On the second line, for **Property**, enter **EdiIntAS.IsAS2AsynchronousMDN**; for **Operator**, enter **==**; and for **Value**, enter **True**.</span></span>  
  
5. <span data-ttu-id="d4aca-293">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-293">Click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-294">按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-294">Click the **Send Ports** node, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-receive-port-to-receive-the-mdn-from-fabrikam"></a><span data-ttu-id="d4aca-295">若要建立接收埠以接收來自 Fabrikam 的 MDN</span><span class="sxs-lookup"><span data-stu-id="d4aca-295">To create a receive port to receive the MDN from Fabrikam</span></span>  
  
1. <span data-ttu-id="d4aca-296">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **單向接收埠**.</span><span class="sxs-lookup"><span data-stu-id="d4aca-296">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, under the BizTalk Application 1 node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2. <span data-ttu-id="d4aca-297">接收埠命名為**RecvMDNFromFab**，然後按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-297">Name the receive port as **RecvMDNFromFab**, and then click **Receive Locations** in the console tree.</span></span>  
  
3. <span data-ttu-id="d4aca-298">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-298">Click **New**.</span></span>  
  
4. <span data-ttu-id="d4aca-299">中**接收位置屬性**對話方塊中，名稱您接收位置中，選取**HTTP**如**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-299">In the **Receive Location Properties** dialog box, name your receive location, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
5. <span data-ttu-id="d4aca-300">在  **HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Contoso/BTSHTTPReceive.dll** for**虛擬目錄加 ISAPI 延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-300">In the **HTTP Transport Properties** dialog box, enter **/Contoso/BTSHTTPReceive.dll** for **Virtual directory plus ISAPI extension**.</span></span> <span data-ttu-id="d4aca-301">清除**成功時傳回相互關聯控制代碼**，然後選取**擱置失敗的要求**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-301">Clear **Return correlation handle on success** and select **Suspend failed requests**.</span></span> <span data-ttu-id="d4aca-302">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-302">Click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-303">選取  **AS2Receive** for**接收管線**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-303">Select **AS2Receive** for the **Receive Pipeline**.</span></span> <span data-ttu-id="d4aca-304">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="d4aca-304">Click **OK**, and then click **OK** again.</span></span>  
  
7. <span data-ttu-id="d4aca-305">按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-305">Click the **Receive Locations** node, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-send-port-to-send-the-mdn-to-a-local-folder"></a><span data-ttu-id="d4aca-306">若要建立傳送埠以將 MDN 傳送至本機資料夾</span><span class="sxs-lookup"><span data-stu-id="d4aca-306">To create a send port to send the MDN to a local folder</span></span>  
  
1. <span data-ttu-id="d4aca-307">在 Windows 檔案總管中，建立本機資料夾，以便將 MDN 傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-307">In Windows Explorer, create a local folder to send the MDN to.</span></span>  
  
2. <span data-ttu-id="d4aca-308">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-308">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
3. <span data-ttu-id="d4aca-309">在 **傳送埠屬性**對話方塊方塊中，將傳送埠命名。</span><span class="sxs-lookup"><span data-stu-id="d4aca-309">In the **Send Port Properties** dialog box, name your send port.</span></span> <span data-ttu-id="d4aca-310">選取 **檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-310">Select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="d4aca-311">在 [ **FILE 傳輸屬性**] 對話方塊中，如**目的地資料夾**，輸入您要建立為 MDN 傳送目標的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-311">In the **FILE Transport Properties** dialog box, for **Destination folder**, enter the local folder you created to send the MDN to.</span></span>  
  
5. <span data-ttu-id="d4aca-312">針對**檔名**，輸入 **%MessageID%.msg**。按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-312">For **File name**, enter **%MessageID%.msg**. Click **OK**.</span></span>  
  
6. <span data-ttu-id="d4aca-313">接受預設值是**PassThruTransmit** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-313">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  
  
7. <span data-ttu-id="d4aca-314">按一下 **篩選器**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="d4aca-314">Click **Filters** in the console tree.</span></span> <span data-ttu-id="d4aca-315">針對**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 對於**值**，輸入接收埠接收 MDN (名稱`RecvMDNFromFab`);至於**分組**，接受**和**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-315">For **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; for **Value**, enter the name of the receive port that receives the MDN (`RecvMDNFromFab`); and for **Group by**, accept **And**.</span></span> <span data-ttu-id="d4aca-316">在第二行中，如**屬性**，輸入**EdiIntAS.IsAS2MdnResponseMessage**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-316">On a second line, for **Property**, enter **EdiIntAS.IsAS2MdnResponseMessage**.</span></span> <span data-ttu-id="d4aca-317">針對**運算子**，輸入**==**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-317">For **Operator**, enter **==**.</span></span> <span data-ttu-id="d4aca-318">針對**值**，輸入 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-318">For **Value**, enter **True**.</span></span>  
  
8. <span data-ttu-id="d4aca-319">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-319">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d4aca-320">按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-320">Click the **Send Ports** node, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a><span data-ttu-id="d4aca-321">若要為 Fabrikam 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="d4aca-321">To create a party and a business profile for Fabrikam</span></span>  
  
1. <span data-ttu-id="d4aca-322">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-322">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2. <span data-ttu-id="d4aca-323">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-323">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-324">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4aca-324">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d4aca-325">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="d4aca-325">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="d4aca-326">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="d4aca-326">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3. <span data-ttu-id="d4aca-327">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-327">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4. <span data-ttu-id="d4aca-328">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-328">In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-329">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4aca-329">When you create a party, a profile is also created.</span></span> <span data-ttu-id="d4aca-330">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4aca-330">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="d4aca-331">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-331">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="d4aca-332">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4aca-332">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a><span data-ttu-id="d4aca-333">若要為 Contoso 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="d4aca-333">To create a party and a business profile for Contoso</span></span>  
  
1. <span data-ttu-id="d4aca-334">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-334">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2. <span data-ttu-id="d4aca-335">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-335">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-336">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4aca-336">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d4aca-337">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="d4aca-337">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="d4aca-338">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="d4aca-338">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3. <span data-ttu-id="d4aca-339">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-339">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4. <span data-ttu-id="d4aca-340">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-340">In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d4aca-341">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4aca-341">When you create a party, a profile is also created.</span></span> <span data-ttu-id="d4aca-342">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4aca-342">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="d4aca-343">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-343">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="d4aca-344">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4aca-344">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-an-as2-agreement-between-the-two-business-profiles"></a><span data-ttu-id="d4aca-345">若要建立兩個商務設定檔之間的 AS2 協議</span><span class="sxs-lookup"><span data-stu-id="d4aca-345">To create an AS2 agreement between the two business profiles</span></span>  
  
1.  <span data-ttu-id="d4aca-346">以滑鼠右鍵按一下 **[contoso_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-346">Right-click **Contoso_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="d4aca-347">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4aca-347">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
3.  <span data-ttu-id="d4aca-348">從**通訊協定**下拉式清單中，選取**AS2**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-348">From the **Protocol** drop-down list, select **AS2**.</span></span>  
  
4.  <span data-ttu-id="d4aca-349">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Fabrikam**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-349">In the **Second Partner** section, from the **Name** drop-down list, select **Fabrikam**.</span></span>  
  
5.  <span data-ttu-id="d4aca-350">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**fabrikam_profile**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-350">In the **Second Partner** section, from the **Profile** drop-down list, select **Fabrikam_Profile**.</span></span>  
  
     <span data-ttu-id="d4aca-351">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="d4aca-351">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way AS2 agreement.</span></span>  
  
6.  <span data-ttu-id="d4aca-352">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aca-352">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  
  
    1.  <span data-ttu-id="d4aca-353">上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-353">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="d4aca-354">針對**AS2-從**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="d4aca-354">For **AS2-From**, enter `Contoso`.</span></span> <span data-ttu-id="d4aca-355">針對**AS2-To**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="d4aca-355">For **AS2- To**, enter `Fabrikam`.</span></span>  
  
    2.  <span data-ttu-id="d4aca-356">在 **通知 (Mdn)** 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d4aca-356">In the **Acknowledgements (MDNs)** page, do the following:</span></span>  
  
        1.  <span data-ttu-id="d4aca-357">選取 **針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-357">Select the **Process inbound MDN into MessageBox for routing/delivery options** check box.</span></span>  
  
            > [!NOTE]
            >  <span data-ttu-id="d4aca-358">檢查**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**所需的測試此逐步解說中，因為則只會傳回的 MDN 放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="d4aca-358">Checking the **Process inbound MDN into MessageBox for routing/delivery options** is required for the testing of this walkthrough, because only then will the returned MDN be dropped into the MessageBox.</span></span> <span data-ttu-id="d4aca-359">而您也才可以建立傳送埠訂閱 MDN、將 MDN 傳送到本機目錄，好讓您確認 AS2 傳輸。</span><span class="sxs-lookup"><span data-stu-id="d4aca-359">That enables you to create a send port to subscribe to the MDN, and to send the MDN to a local directory, so you can verify the AS2 transmission.</span></span>  
  
        2.  <span data-ttu-id="d4aca-360">選取 **的 要求 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-360">Select the **Request MDN** check box.</span></span>  
  
        3.  <span data-ttu-id="d4aca-361">請確定**要求簽署的 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-361">Make sure the **Request Signed MDN** check box is cleared.</span></span>  
  
        4.  <span data-ttu-id="d4aca-362">選取 **要求非同步 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-362">Select the **Request asynchronous MDN** check box.</span></span>  
  
        5.  <span data-ttu-id="d4aca-363">在 **回條傳遞選項 (URL)**，輸入**http://localhost/Contoso/BTSHttpReceive.dll**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-363">In **Receipt-Delivery-Option (URL)**, enter **http://localhost/Contoso/BTSHttpReceive.dll**.</span></span>  
  
        6.  <span data-ttu-id="d4aca-364">**配置通知來**預設會設定為您指定**回條傳遞選項 (URL)** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4aca-364">The **Disposition-Notification-To** is by default set to the value you specified for **Receipt-Delivery-Option (URL)** property.</span></span> <span data-ttu-id="d4aca-365">在處理 AS2 的過程中並不會使用這個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="d4aca-365">The value of this field is not used during AS2 processing.</span></span>  
  
    3.  <span data-ttu-id="d4aca-366">在 **傳送埠**頁面上，建立將用來傳送 EDI 交換給 Fabrikam 的雙向傳送埠的關聯。</span><span class="sxs-lookup"><span data-stu-id="d4aca-366">On the **Send Ports** page, associate the two-way send port that will be sending the EDI interchange to Fabrikam.</span></span> <span data-ttu-id="d4aca-367">在 **傳送埠**格線底下**名稱**資料行中，按一下空白儲存格，並從下拉式清單中，選取 傳送埠**SendISAToFab**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-367">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port **SendISAToFab**.</span></span>  
  
7.  <span data-ttu-id="d4aca-368">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aca-368">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4aca-369">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="d4aca-369">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="d4aca-370">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**AS2_From**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-370">To successfully create an agreement, both one-way agreement tabs must have values defined for **AS2_From** and **AS2-To**.</span></span>  
  
    1.  <span data-ttu-id="d4aca-371">上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-371">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="d4aca-372">針對**AS2-從**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="d4aca-372">For **AS2-From**, enter `Fabrikam`.</span></span> <span data-ttu-id="d4aca-373">針對**AS2-To**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="d4aca-373">For **AS2- To**, enter `Contoso`.</span></span>  
  
8.  <span data-ttu-id="d4aca-374">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="d4aca-374">Click **Apply**.</span></span>  
  
9. <span data-ttu-id="d4aca-375">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4aca-375">Click **OK**.</span></span> <span data-ttu-id="d4aca-376">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="d4aca-376">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="d4aca-377">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="d4aca-377">The newly added agreement is enabled by default.</span></span>  
  
### <a name="testing-the-walkthrough"></a><span data-ttu-id="d4aca-378">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="d4aca-378">Testing the Walkthrough</span></span>  
 <span data-ttu-id="d4aca-379">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aca-379">This section provides information on how to test the walkthrough.</span></span>  
  
##### <a name="to-test-the-solution"></a><span data-ttu-id="d4aca-380">測試方案</span><span class="sxs-lookup"><span data-stu-id="d4aca-380">To test the solution</span></span>  
  
1. <span data-ttu-id="d4aca-381">在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial。</span><span class="sxs-lookup"><span data-stu-id="d4aca-381">In Windows Explorer, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial.</span></span> <span data-ttu-id="d4aca-382">複製**SamplePO.txt**檔案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-382">Copy the **SamplePO.txt** file.</span></span>  
  
2. <span data-ttu-id="d4aca-383">貼上**SamplePO.txt**檔案放置於您要建立從 Contoso 接收測試訊息的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-383">Paste the **SamplePO.txt** file into the local folder that you created to receive the test message from Contoso.</span></span>  
  
3. <span data-ttu-id="d4aca-384">移至您建立用來傳送 EDI 內容的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-384">Move to the local folder that you created to send the EDI payload to.</span></span> <span data-ttu-id="d4aca-385">確認該資料夾包含 EDI 檔案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-385">Confirm that the folder contains an EDI file.</span></span> <span data-ttu-id="d4aca-386">開啟檔案和原始測試訊息，並確認其內容是相同的。</span><span class="sxs-lookup"><span data-stu-id="d4aca-386">Open the file and the original test message, and verify that they have the same content.</span></span>  
  
4. <span data-ttu-id="d4aca-387">移至您建立用來做為結果 MDN 之傳送目標的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4aca-387">Move to the local folder that you created to send the resulting MDN to.</span></span> <span data-ttu-id="d4aca-388">確認該資料夾包含測試檔案、開啟該檔案並確認是否為 MDN 檔案。</span><span class="sxs-lookup"><span data-stu-id="d4aca-388">Confirm that the folder contains a test file; open the file, and confirm that it is an MDN file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4aca-389">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4aca-389">See Also</span></span>  
 [<span data-ttu-id="d4aca-390">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="d4aca-390">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)