---
title: '逐步解說 (AS2): 透過 AS2 傳送非 EDI 訊息 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6120b81e-bdd5-44ad-9040-26be88c71258
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78da76298e4443acfafa1893e6e4c5bb946bfd2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002463"
---
# <a name="walkthrough-as2-sending-a-non-edi-message-over-as2"></a><span data-ttu-id="c0315-102">逐步解說 (AS2)：透過 AS2 傳送非 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="c0315-102">Walkthrough (AS2): Sending a Non-EDI Message over AS2</span></span>
<span data-ttu-id="c0315-103">本逐步解說提供一組逐步執行的程序，建立透過 AS2 傳送非 EDI 訊息的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c0315-103">This walkthrough provides a set of step-by-step procedures that creates a solution for sending non-EDI messages over AS2.</span></span> <span data-ttu-id="c0315-104">本逐步解說會透過 AS2 傳送 PIDX 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-104">In this walkthrough, a PIDX message is sent over AS2.</span></span> <span data-ttu-id="c0315-105">此方案使用含一個 AS2Send 傳送管線和一個 AS2Receive 接收管線的雙向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c0315-105">This solution uses a two-way send port with an AS2Send send pipeline and an AS2Receive receive pipeline.</span></span> <span data-ttu-id="c0315-106">您可以在單一電腦上，建立並測試此逐步解說中的整個解決方案。</span><span class="sxs-lookup"><span data-stu-id="c0315-106">You can create and test the full solution in this walkthrough on a single computer.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c0315-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="c0315-107">Prerequisites</span></span>  
 <span data-ttu-id="c0315-108">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="c0315-108">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
- <span data-ttu-id="c0315-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="c0315-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
- <span data-ttu-id="c0315-110">執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。</span><span class="sxs-lookup"><span data-stu-id="c0315-110">The computer that runs the walkthrough must have Internet Information Services (IIS) 7 installed.</span></span>  
  
- <span data-ttu-id="c0315-111">若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。</span><span class="sxs-lookup"><span data-stu-id="c0315-111">If the computer that runs the walkthrough is installed with a 64-bit version of Windows, you must ensure that the BizTalk hosts are marked as 32-bit only.</span></span> <span data-ttu-id="c0315-112">您也必須確定 IIS 已將應用程式集區的「啟用 32 位元應用程式」設定為 True。</span><span class="sxs-lookup"><span data-stu-id="c0315-112">You must also ensure IIS has the Enable 32-Bit Application Setting for the Application Pools set to True.</span></span> <span data-ttu-id="c0315-113">如需詳細資訊，請參閱 <<c0> [ 教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="c0315-113">For more information, see [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md).</span></span>  
  
## <a name="how-the-solution-sends-a-non-edias2-message-and-returns-a-synchronous-mdn"></a><span data-ttu-id="c0315-114">解決方案如何傳送非 EDI/AS2 訊息並傳回同步 MDN</span><span class="sxs-lookup"><span data-stu-id="c0315-114">How the Solution Sends a non-EDI/AS2 Message and Returns a Synchronous MDN</span></span>  
 <span data-ttu-id="c0315-115">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c0315-115">The solution will do the following:</span></span>  
  
1. <span data-ttu-id="c0315-116">單向 FILE 接收埠從 Contoso 接收 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-116">A one-way FILE receive port receives an XML message from Contoso.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-117">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="c0315-117">The events in this list may not occur in the order shown.</span></span>  
  
2. <span data-ttu-id="c0315-118">透過使用 XML 接收管線，接收埠會檢查訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-118">Using the XML receive pipeline, the receive port checks the message.</span></span> <span data-ttu-id="c0315-119">然後接收埠將測試訊息依原狀放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="c0315-119">The receive port then drops the test message as-is into the MessageBox.</span></span>  
  
3. <span data-ttu-id="c0315-120">靜態雙向傳送埠取用 XML 訊息，並訂閱接收埠收到的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-120">A static two-way send port picks up the XML message, subscribing to all messages received by the receive port.</span></span>  
  
4. <span data-ttu-id="c0315-121">Fabrikam 的雙向接收埠會使用 Fabrikam 虛擬目錄來接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-121">The two-way receive port at Fabrikam receives the AS2 message using the Fabrikam virtual directory.</span></span> <span data-ttu-id="c0315-122">接收管線解碼 AS2 訊息，然後將訊息置放在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="c0315-122">The receive pipeline decodes the message from AS2, and drops the message into the MessageBox.</span></span>  
  
5. <span data-ttu-id="c0315-123">具有通過傳送管線的靜態單向傳送埠取用該 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-123">A static one-way send port with a passthrough send pipeline picks up the XML message.</span></span>  
  
6. <span data-ttu-id="c0315-124">單向傳送埠將 XML 訊息傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-124">The one-way send port sends the XML message to a local folder.</span></span>  
  
7. <span data-ttu-id="c0315-125">與雙向接收埠相關聯的傳送埠會傳回同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="c0315-125">The send port associated with the two-way receive port returns a synchronous MDN.</span></span>  
  
8. <span data-ttu-id="c0315-126">與雙向傳送埠相關聯的接收埠接收 MDN，並將其置放在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="c0315-126">The receive port associated with the two-way send port receives the MDN, and drops it in the MessageBox.</span></span>  
  
9. <span data-ttu-id="c0315-127">具有通過傳送管線的靜態單向傳送埠會拾取該 MDN。</span><span class="sxs-lookup"><span data-stu-id="c0315-127">A static one-way send port with a passthrough send pipeline picks up the MDN.</span></span>  
  
10. <span data-ttu-id="c0315-128">單向傳送埠會將 MDN 傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-128">The one-way send port sends the MDN to a local folder.</span></span>  
  
    <span data-ttu-id="c0315-129">下圖顯示這個解決方案的架構。</span><span class="sxs-lookup"><span data-stu-id="c0315-129">The following figure shows the architecture for the solution.</span></span>  
  
    <span data-ttu-id="c0315-130">![傳送非&#45;透過 AS2 的 EDI 訊息](../core/media/57b7dc54-b8e8-462e-98d1-9cddedd14107.gif "57b7dc54-b8e8-462e-98d1-9cddedd14107")</span><span class="sxs-lookup"><span data-stu-id="c0315-130">![Sending a non&#45;EDI message over AS2](../core/media/57b7dc54-b8e8-462e-98d1-9cddedd14107.gif "57b7dc54-b8e8-462e-98d1-9cddedd14107")</span></span>  
  
## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="c0315-131">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="c0315-131">The Functionality in this Solution</span></span>  
 <span data-ttu-id="c0315-132">下列項目適用於本逐步解說的功能：</span><span class="sxs-lookup"><span data-stu-id="c0315-132">The following applies to the functionality of this walkthrough:</span></span>  
  
-   <span data-ttu-id="c0315-133">本逐步解說是處理 AS2 功能。</span><span class="sxs-lookup"><span data-stu-id="c0315-133">This walkthrough deals with AS2 functionality.</span></span> <span data-ttu-id="c0315-134">因此，與 AS2 處理有關的所有連接埠都是使用 AS2Receive 或 AS2Send 管線。</span><span class="sxs-lookup"><span data-stu-id="c0315-134">As a result, all ports involved in AS2 processing use either AS2Receive or AS2Send pipelines.</span></span> <span data-ttu-id="c0315-135">與 AS2 處理無關的連接埠，則使用 XMLReceive 或 PassThruTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="c0315-135">Ports that are not involved in AS2 processing use either the XMLReceive or PassThruTransmit pipelines.</span></span>  
  
-   <span data-ttu-id="c0315-136">本逐步解說會使用 XML 測試訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-136">This walkthrough uses an XML test message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0315-137">您必須提供 XML 測試訊息和測試訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0315-137">You must provide an XML test message and a schema for the test message.</span></span>  
  
-   <span data-ttu-id="c0315-138">沒有啟用狀態報告。</span><span class="sxs-lookup"><span data-stu-id="c0315-138">Status reporting is not enabled.</span></span>  
  
-   <span data-ttu-id="c0315-139">這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。</span><span class="sxs-lookup"><span data-stu-id="c0315-139">This solution does not configure signing, compression, encryption, or message storage in the non-repudiation database.</span></span> <span data-ttu-id="c0315-140">如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c0315-140">For procedures on configuring those properties, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).</span></span>  
  
## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="c0315-141">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="c0315-141">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="c0315-142">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c0315-142">The procedures required for this solution include the following:</span></span>  
  
- <span data-ttu-id="c0315-143">使用必要的訊息結構描述來建置並部署 BizTalk 專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-143">Build and deploy a BizTalk project with the required message schema, making the schema available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the received message.</span></span>  
  
- <span data-ttu-id="c0315-144">讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-144">Enable the BTS ISAPI filter used in receiving the AS2 message.</span></span>  
  
- <span data-ttu-id="c0315-145">建立 Fabrikam 虛擬目錄，用於接收 Contoso 的 AS2 訊息，如接收位置中所設定。</span><span class="sxs-lookup"><span data-stu-id="c0315-145">Create a Fabrikam virtual directory that receives the AS2 message from Contoso, as configured in the receive location.</span></span>  
  
- <span data-ttu-id="c0315-146">指定 Fabrikam 虛擬目錄不是由 Windows SharePoint Services 管理。</span><span class="sxs-lookup"><span data-stu-id="c0315-146">Specify that the Fabrikam virtual directory is not managed by Windows SharePoint Services.</span></span>  
  
- <span data-ttu-id="c0315-147">建立單向 FILE 接收埠，以接收要透過 AS2 傳輸來傳送的 XML 測試訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-147">Create a one-way FILE receive port to receive the XML test message that will be sent via AS2 transport.</span></span> <span data-ttu-id="c0315-148">建立本機資料夾，接收測試訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-148">Create the local folder to receive the test message.</span></span>  
  
- <span data-ttu-id="c0315-149">建立靜態請求-回應 HTTP 傳送埠、將傳送管線設定為 AS2Send 管線，以及將接收管線設定為 AS2Receive 管線。</span><span class="sxs-lookup"><span data-stu-id="c0315-149">Create a static solicit-response HTTP send port, configuring the send pipeline to be the AS2Send pipeline and the receive pipeline to be the AS2Receive pipeline.</span></span> <span data-ttu-id="c0315-150">連接埠將 AS2 訊息傳送到 Fabrikam，並接收 Fabrikam 的 MDN 回應，然後將它放到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="c0315-150">The port sends the AS2 message to Fabrikam and receives the MDN response from Fabrikam and drops it to the Message box.</span></span>  
  
- <span data-ttu-id="c0315-151">建立雙向 HTTP 接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 AS2 訊息及傳送 MDN 回應。</span><span class="sxs-lookup"><span data-stu-id="c0315-151">Create a two-way HTTP receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the AS2 message, and to send the MDN response.</span></span> <span data-ttu-id="c0315-152">設定接收管線為 AS2Receive 管線，並設定傳送管線為 AS2Send 管線。</span><span class="sxs-lookup"><span data-stu-id="c0315-152">Configure the receive pipeline to be the AS2Receive pipeline and the send pipeline to be the AS2Send pipeline.</span></span> <span data-ttu-id="c0315-153">設定接收位置，以透過 Fabrikam 虛擬目錄接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0315-153">Configure the receive location to receive the AS2 message via the Fabrikam virtual directory.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="c0315-154">測試解決方案位於單一電腦上，因此，用於傳送 AS2 訊息 (自 Contoso 寄出) 的雙向傳送埠和用於接收 AS2 訊息 (由 Fabrikam 接收) 的雙向接收埠，皆位於相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="c0315-154">The test solution is on a single computer; as a result, the two-way send port sending the AS2 message (from Contoso) and the two-way receive port receiving the AS2 message (as Fabrikam) are on the same computer.</span></span>  
  
- <span data-ttu-id="c0315-155">建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，將訊息 XML 內容路由傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-155">Create a static one-way FILE send port (with a passthrough send pipeline) to route the message XML payload to a local folder.</span></span> <span data-ttu-id="c0315-156">建立本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-156">Create the local folder.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="c0315-157">如果您沒有傳送埠可以訂閱訊息內容，那麼訊息內容就會擱置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="c0315-157">If you do not have a send port to subscribe to the message payload, it will be suspended in the MessageBox.</span></span>  
  
- <span data-ttu-id="c0315-158">建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，以將 MDN 路由傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-158">Create a static one-way FILE send port (with a passthrough send pipeline) to route the MDN to a local folder.</span></span> <span data-ttu-id="c0315-159">建立本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-159">Create the local folder.</span></span>  
  
- <span data-ttu-id="c0315-160">為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="c0315-160">Create a party (trading partner) for both Fabrikam and Contoso.</span></span>  
  
- <span data-ttu-id="c0315-161">為這兩個交易合作對象各建立一個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="c0315-161">Create a business profile each for both the trading parties.</span></span>  
  
- <span data-ttu-id="c0315-162">在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="c0315-162">Create an AS2 agreement between the business profiles for Fabrikam and Contoso.</span></span> <span data-ttu-id="c0315-163">AS2 協議應包含傳送 AS2 訊息及接收同步回傳之 MDN 的屬性。</span><span class="sxs-lookup"><span data-stu-id="c0315-163">The AS2 agreement would contain properties to send an AS2 message and receive a synchronous MDN in return.</span></span>  
  
- <span data-ttu-id="c0315-164">使用 XML 測試訊息測試逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c0315-164">Test the walkthrough using an XML test message.</span></span>  
  
### <a name="configuring-the-walkthrough"></a><span data-ttu-id="c0315-165">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="c0315-165">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="c0315-166">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="c0315-166">This section describes the procedures to configure the walkthrough.</span></span>  
  
##### <a name="to-deploy-the-test-message-schema"></a><span data-ttu-id="c0315-167">若要部署測試訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c0315-167">To deploy the test message schema</span></span>  
  
1. <span data-ttu-id="c0315-168">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="c0315-168">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-169">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="c0315-169">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="c0315-170">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="c0315-170">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
2. <span data-ttu-id="c0315-171">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="c0315-171">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="c0315-172">若要使用 XML 檔案測試您的解決方案，請移至包含 XML 測試訊息之 XSD 結構描述的本機資料夾，然後選取該 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0315-172">To use an XML file to test your solution, move to the local folder that contains the XSD schema for the XML test message, and select the XSD file.</span></span> <span data-ttu-id="c0315-173">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="c0315-173">Click **Add**.</span></span>  
  
3. <span data-ttu-id="c0315-174">設定組件金鑰檔案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="c0315-174">Set the assembly key file, and then build and deploy the assembly.</span></span>  
  
##### <a name="to-enable-the-bts-isapi-filter"></a><span data-ttu-id="c0315-175">若要啟用 BTS ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="c0315-175">To enable the BTS ISAPI Filter</span></span>  
  
1. <span data-ttu-id="c0315-176">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="c0315-176">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
   > [!TIP]
   >  <span data-ttu-id="c0315-177">視作業系統而定，[系統管理工具] 開始功能表選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="c0315-177">Depending on the operating system, the Administrative Tools start menu option may not be available.</span></span> <span data-ttu-id="c0315-178">在這種情況下，按一下**開始**，按一下**執行**，然後輸入`inetmgr`以開啟 Internet Information Services (IIS) 管理員。</span><span class="sxs-lookup"><span data-stu-id="c0315-178">In such cases, click **Start**, click **Run**, and enter `inetmgr` to open Internet Information Services (IIS) Manager.</span></span>  
  
2. <span data-ttu-id="c0315-179">選取根 Web 伺服器項目並在**功能檢視**，按兩下**處理常式對應**，然後在 動作 窗格中的，按一下 **新增指令碼對應**。</span><span class="sxs-lookup"><span data-stu-id="c0315-179">Select the root Web Server entry and in the **Features View**, double click **Handler Mappings** and then in the Actions pane click **Add Script Map**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-180">在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。</span><span class="sxs-lookup"><span data-stu-id="c0315-180">Configuring the script mapping at the Web Server level will cause this mapping to apply to all child Web Sites.</span></span> <span data-ttu-id="c0315-181">若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c0315-181">If you wish to restrict the mapping to a specific Web Site or Virtual Folder, select the target site or folder instead of the Web Server.</span></span>  
  
3. <span data-ttu-id="c0315-182">在 **新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。</span><span class="sxs-lookup"><span data-stu-id="c0315-182">In the **Add Script Map** dialog box, enter `BtsHttpReceive.dll` in the **Request path** field.</span></span>  
  
4. <span data-ttu-id="c0315-183">在 **可執行檔**欄位中，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="c0315-183">In the **Executable** field, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span></span> <span data-ttu-id="c0315-184">選取 BtsHttpReceive.dll，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-184">Select BtsHttpReceive.dll and click **OK**.</span></span>  
  
5. <span data-ttu-id="c0315-185">請輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。</span><span class="sxs-lookup"><span data-stu-id="c0315-185">Enter `BizTalk HTTP Receive` in the `Name` field, and then click **Request Restrictions**.</span></span>  
  
6. <span data-ttu-id="c0315-186">在 **要求限制**對話方塊中，選取**動詞**索引標籤，然後選取**其中一個下列的指令動詞**。</span><span class="sxs-lookup"><span data-stu-id="c0315-186">In the **Request Restrictions** dialog box, select the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="c0315-187">輸入`POST`作為動詞。</span><span class="sxs-lookup"><span data-stu-id="c0315-187">Enter `POST` as the verb.</span></span>  
  
7. <span data-ttu-id="c0315-188">在上**存取權**索引標籤上，選取**指令碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-188">On the **Access** tab, select **Script** and then click **OK**.</span></span>  
  
8. <span data-ttu-id="c0315-189">按一下  **確定**當系統提示您允許 ISAPI 延伸模組時，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="c0315-189">Click **OK** and when prompted to allow the ISAPI extension, click **Yes**.</span></span>  
  
##### <a name="to-configure-the-fabrikam-web-page"></a><span data-ttu-id="c0315-190">若要設定 Fabrikam 網頁</span><span class="sxs-lookup"><span data-stu-id="c0315-190">To configure the Fabrikam Web page</span></span>  
  
1. <span data-ttu-id="c0315-191">在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，然後選取**新增應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="c0315-191">In IIS Manager, right-click **Application Pools** and select **Add Application Pool**.</span></span>  
  
2. <span data-ttu-id="c0315-192">在**新增應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c0315-192">In **the Add Application Pool** dialog box, enter **BizTalkAppPool** in **Name**, and then select **.NET Framework V4.0.30210** in the **.NET Framework version** drop-down list.</span></span> <span data-ttu-id="c0315-193">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-193">Click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-194">版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="c0315-194">The version number may vary depending on the version of [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installed on the machine.</span></span>  
  
3. <span data-ttu-id="c0315-195">選取**應用程式集區**，請在**功能檢視**選取**BizTalkAppPool**，然後按一下**進階設定**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="c0315-195">Select **Application Pools**, in the **Features View** select **BizTalkAppPool**, and then click **Advanced Settings** in the **Actions** pane.</span></span>  
  
4. <span data-ttu-id="c0315-196">在 [**進階設定]** 對話方塊中，選取**識別**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c0315-196">In the **Advanced Settings** dialog box, select **Identity** and then click the ellipsis (…) button.</span></span>  
  
5. <span data-ttu-id="c0315-197">在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-197">In the **Application Pool Identity** dialog box, select **Custom account** and then click **Set**.</span></span>  
  
6. <span data-ttu-id="c0315-198">輸入**使用者名**並**密碼**使用者帳戶，系統管理員群組的成員，請輸入中的密碼**確認密碼**，然後按一下  **確定**三次，以返回 IIS 管理員。</span><span class="sxs-lookup"><span data-stu-id="c0315-198">Enter the **User name** and **Password** for a user account that is a member of the administrators group, enter the password in **Confirm password** and then click **OK** three times to return to the IIS Manager.</span></span>  
  
7. <span data-ttu-id="c0315-199">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-199">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="c0315-200">以滑鼠右鍵按一下**Default Web Site**節點，，然後選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="c0315-200">Right-click the **Default Web Site** node, and then select **Add Application**.</span></span>  
  
8. <span data-ttu-id="c0315-201">在 **新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="c0315-201">In the **Add Application** dialog box, enter **Fabrikam** in **Alias**, and then click **Select**.</span></span>  
  
9. <span data-ttu-id="c0315-202">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-202">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
10. <span data-ttu-id="c0315-203">按一下省略符號 （...） 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]針對 HttpReceive**實體路徑**。</span><span class="sxs-lookup"><span data-stu-id="c0315-203">Click the ellipsis (…) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
11. <span data-ttu-id="c0315-204">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0315-204">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="c0315-205">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c0315-205">Click **Close**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="c0315-206">在 [IIS 管理員] 中，選取 Fabrikam 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="c0315-206">In IIS Manager, select the Fabrikam virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  
  
13. <span data-ttu-id="c0315-207">在 **驗證**頁面上，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="c0315-207">In the **Authentication** page, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="c0315-208">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="c0315-208">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a><span data-ttu-id="c0315-209">若要指定虛擬目錄不是由 Windows SharePoint Services 管理</span><span class="sxs-lookup"><span data-stu-id="c0315-209">To specify that your virtual directory is not managed by Windows SharePoint Services</span></span>  
  
1.  <span data-ttu-id="c0315-210">如果 Windows SharePoint Services 安裝在電腦上，按一下**開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="c0315-210">If Windows SharePoint Services is installed on your computer, click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0315-211">如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="c0315-211">This procedure is required if Windows SharePoint Server is installed on the same computer that you are setting the walkthrough up on.</span></span> <span data-ttu-id="c0315-212">在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。</span><span class="sxs-lookup"><span data-stu-id="c0315-212">In that case, you must specify that your IIS virtual directory is not being managed by Windows SharePoint Server.</span></span>  
  
2.  <span data-ttu-id="c0315-213">在上**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。</span><span class="sxs-lookup"><span data-stu-id="c0315-213">On the **Central Administration** page, under **Central Administration**, click **Application Management**.</span></span>  
  
3.  <span data-ttu-id="c0315-214">在 **應用程式管理**頁面上，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="c0315-214">On the **Application Management** page, click **Define managed paths**.</span></span>  
  
4.  <span data-ttu-id="c0315-215">在 **定義管理的路徑**頁面的 **加入新路徑**，請在**路徑**文字方塊中，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="c0315-215">In the **Define Managed Paths** page, under **Add a New Path**, in the **Path** text box, enter `Fabrikam`.</span></span> <span data-ttu-id="c0315-216">底下**型別**，按一下**排除的路徑**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-216">Under **Type**, click **Excluded Path**, and then click **OK**.</span></span>  
  
##### <a name="to-create-a-receive-port-to-receive-the-test-message"></a><span data-ttu-id="c0315-217">若要建立接收埠以接收測試訊息</span><span class="sxs-lookup"><span data-stu-id="c0315-217">To create a receive port to receive the test message</span></span>  
  
1. <span data-ttu-id="c0315-218">在 Windows 檔案總管中，建立本機資料夾，以接收來自 Contoso 的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="c0315-218">In Windows Explorer, create a local folder to receive the EDI interchange from Contoso.</span></span>  
  
2. <span data-ttu-id="c0315-219">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="c0315-219">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3. <span data-ttu-id="c0315-220">在 [**接收埠屬性**] 對話方塊中，接收埠命名為**RecvXMLFromCont**。</span><span class="sxs-lookup"><span data-stu-id="c0315-220">In the **Receive Port Properties** dialog box, name the receive port as **RecvXMLFromCont**.</span></span>  
  
4. <span data-ttu-id="c0315-221">按一下 **接收位置**在主控台樹狀目錄中，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="c0315-221">Click **Receive Locations** in the console tree, and then click **New**.</span></span>  
  
5. <span data-ttu-id="c0315-222">接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-222">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
6. <span data-ttu-id="c0315-223">針對**接收資料夾**，輸入您在步驟 1 中建立資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0315-223">For **Receive folder**, enter the name of the folder that you created in step 1.</span></span>  
  
7. <span data-ttu-id="c0315-224">在 **檔案遮罩**，輸入 **\*.xml**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-224">In **File mask**, enter **\*.xml**, and then click **OK**.</span></span>  
  
8. <span data-ttu-id="c0315-225">在 接收管線中，選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="c0315-225">In Receive pipeline, select **XMLReceive**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-226">如果您使用另一個非 EDI 以外的檔案類型，XML 中，輸入**PassThruTranmit**。</span><span class="sxs-lookup"><span data-stu-id="c0315-226">If you are using another non-EDI file type, other than XML, enter **PassThruTranmit**.</span></span>  
  
9. <span data-ttu-id="c0315-227">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="c0315-227">Click **OK**, and then click **OK** again.</span></span>  
  
10. <span data-ttu-id="c0315-228">按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="c0315-228">Click the **Receive Locations** node, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-send-port-to-send-the-as2-message-to-fabrikam"></a><span data-ttu-id="c0315-229">建立傳送埠以將 AS2 訊息傳送至 Fabrikam</span><span class="sxs-lookup"><span data-stu-id="c0315-229">To create a send port to send the AS2 message to Fabrikam</span></span>  
  
1. <span data-ttu-id="c0315-230">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="c0315-230">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-231">如果使用 [BizTalk Application 1]，您必須在 [BizTalk Application 1] 中加入「BizTalk EDI 應用程式」的參考，讓應用程式使用其成品。</span><span class="sxs-lookup"><span data-stu-id="c0315-231">If you use BizTalk Application 1, you must add a reference in BizTalk Application 1 to the BizTalk EDI Application, so your application can use its artifacts.</span></span> <span data-ttu-id="c0315-232">如需詳細資訊，請參閱 <<c0> [ 如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="c0315-232">For more information, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
2. <span data-ttu-id="c0315-233">在 [**傳送埠屬性**] 對話方塊中，將傳送埠命名為**SendToFab_RecvMDN**。</span><span class="sxs-lookup"><span data-stu-id="c0315-233">In the **Send Port Properties** dialog box, name the send port as **SendToFab_RecvMDN**.</span></span>  
  
3. <span data-ttu-id="c0315-234">在 **傳輸**區段中，選取**HTTP**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-234">In the **Transport** section, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="c0315-235">在 [ **HTTP 傳輸屬性**] 對話方塊中，如**目的地 URL**，輸入**http://localhost/Fabrikam/BTSHttpReceive.dll**。</span><span class="sxs-lookup"><span data-stu-id="c0315-235">In the **HTTP Transport Properties** dialog box, for **Destination URL**, enter **http://localhost/Fabrikam/BTSHttpReceive.dll**.</span></span>  
  
5. <span data-ttu-id="c0315-236">清除**啟用區塊編碼**。</span><span class="sxs-lookup"><span data-stu-id="c0315-236">Clear **Enable chunked encoding**.</span></span> <span data-ttu-id="c0315-237">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-237">Click **OK**.</span></span>  
  
6. <span data-ttu-id="c0315-238">針對**傳送管線**，選取**AS2Send**。</span><span class="sxs-lookup"><span data-stu-id="c0315-238">For **Send pipeline**, select **AS2Send**.</span></span>  
  
7. <span data-ttu-id="c0315-239">針對**接收管線**，選取**AS2Receive**。</span><span class="sxs-lookup"><span data-stu-id="c0315-239">For **Receive pipeline**, select **AS2Receive**.</span></span>  
  
8. <span data-ttu-id="c0315-240">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="c0315-240">In the console tree, select **Filters**.</span></span> <span data-ttu-id="c0315-241">針對**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 及針對**值**輸入將接收 EDI 接收埠的名稱交換 (`RecvXMLFromCont`)。</span><span class="sxs-lookup"><span data-stu-id="c0315-241">For **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; and for **Value** enter the name of the receive port that will receive the EDI interchange (`RecvXMLFromCont`).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-242">如果您要傳送 PIDX 訊息，您可以建立篩選的篩選條件運算式的訊息類型 (**PIDX**)。</span><span class="sxs-lookup"><span data-stu-id="c0315-242">If you are sending a PIDX message, you can create a filter expression that filters on the type of the message (**PIDX**).</span></span>  
  
9. <span data-ttu-id="c0315-243">如果您想要套用對應來轉換 XML 文件，請按一下**輸出對應**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="c0315-243">If you want to apply a map to transform the XML document, click **Outbound Maps** in the console tree.</span></span> <span data-ttu-id="c0315-244">請輸入**來源文件**輸出對應中，選取**地圖**，然後輸入**目標文件**。</span><span class="sxs-lookup"><span data-stu-id="c0315-244">Enter the **Source Document** for the outbound map, select the **Map**, and then enter the **Target Document**.</span></span> <span data-ttu-id="c0315-245">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-245">Click **OK**.</span></span>  
  
10. <span data-ttu-id="c0315-246">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-246">Click **OK**.</span></span>  
  
11. <span data-ttu-id="c0315-247">按一下 **傳送埠**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下您的傳送埠，然後**啟動**。</span><span class="sxs-lookup"><span data-stu-id="c0315-247">Click the **Send Ports** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-receive-port-to-receive-the-as2-message-and-return-an-acknowledgment"></a><span data-ttu-id="c0315-248">若要建立接收埠以接收 AS2 訊息並傳回通知</span><span class="sxs-lookup"><span data-stu-id="c0315-248">To create a receive port to receive the AS2 message and return an acknowledgment</span></span>  
  
1. <span data-ttu-id="c0315-249">中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，底下**BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 [ **要求回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="c0315-249">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **BizTalk Application 1** node, right-click **Receive Ports**, point to **New**, and then click **Request Response Receive Port**.</span></span>  
  
2. <span data-ttu-id="c0315-250">接收埠命名為**RecvAS2Msg**，然後按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="c0315-250">Name the receive port as **RecvAS2Msg**, and then click **Receive Locations** in the console tree.</span></span>  
  
3. <span data-ttu-id="c0315-251">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="c0315-251">Click **New**.</span></span>  
  
4. <span data-ttu-id="c0315-252">中**接收位置屬性**對話方塊中，名稱您接收位置中，選取**HTTP**如**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-252">In the **Receive Location Properties** dialog box, name your receive location, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
5. <span data-ttu-id="c0315-253">在  **HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Fabrikam/BTSHttpReceive.dll** for**虛擬目錄加 ISAPI 延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="c0315-253">In the **HTTP Transport Properties** dialog box, enter **/Fabrikam/BTSHttpReceive.dll** for **Virtual directory plus ISAPI extension**.</span></span> <span data-ttu-id="c0315-254">清除**成功時傳回相互關聯控制代碼**，然後選取**擱置失敗的要求**。</span><span class="sxs-lookup"><span data-stu-id="c0315-254">Clear **Return correlation handle on success** and select **Suspend failed requests**.</span></span> <span data-ttu-id="c0315-255">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-255">Click **OK**.</span></span>  
  
6. <span data-ttu-id="c0315-256">選取**AS2Receive** for**接收管線**，並**AS2Send**如**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="c0315-256">Select **AS2Receive** for the **Receive Pipeline**, and **AS2Send** for the **Send Pipeline**.</span></span> <span data-ttu-id="c0315-257">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="c0315-257">Click **OK**, and then click **OK** again.</span></span>  
  
7. <span data-ttu-id="c0315-258">按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="c0315-258">Click the **Receive Locations** node, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-send-port-to-send-the-test-xml-payload-to-a-local-folder"></a><span data-ttu-id="c0315-259">若要建立傳送埠以將測試 XML 內容傳送至本機資料夾</span><span class="sxs-lookup"><span data-stu-id="c0315-259">To create a send port to send the test XML payload to a local folder</span></span>  
  
1. <span data-ttu-id="c0315-260">在 Windows 檔案總管中，建立本機資料夾，以便將 EDI 交換傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-260">In Windows Explorer, create a local folder to send the EDI interchange to.</span></span>  
  
2. <span data-ttu-id="c0315-261">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="c0315-261">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
3. <span data-ttu-id="c0315-262">在 **傳送埠屬性**對話方塊中，將傳送埠作為**SendXMLPayload**。</span><span class="sxs-lookup"><span data-stu-id="c0315-262">In the **Send Port Properties** dialog box, name your send port as **SendXMLPayload**.</span></span> <span data-ttu-id="c0315-263">選取 **檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-263">Select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="c0315-264">在 [ **FILE 傳輸屬性**] 對話方塊中，如**目的地資料夾**，輸入您建立之 EDI 內容的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-264">In the **FILE Transport Properties** dialog box, for **Destination folder**, enter the local folder that you created for the EDI payload.</span></span>  
  
5. <span data-ttu-id="c0315-265">針對**檔案名**，輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c0315-265">For **File name**, enter the file name.</span></span> <span data-ttu-id="c0315-266">如果您使用的 XML 檔案做為測試訊息，請輸入 **%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="c0315-266">If you are using an XML file as your test message, enter **%MessageID%.xml**.</span></span> <span data-ttu-id="c0315-267">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-267">Click **OK**.</span></span>  
  
6. <span data-ttu-id="c0315-268">接受預設值是**PassThruTransmit** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="c0315-268">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  
  
7. <span data-ttu-id="c0315-269">按一下 **篩選器**在主控台樹狀結構，並加入挑選 EDI 內容的篩選屬性。</span><span class="sxs-lookup"><span data-stu-id="c0315-269">Click **Filters** in the console tree, and add filter properties for picking up the EDI payload.</span></span> <span data-ttu-id="c0315-270">在第一行，如**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 對於**值**，輸入接收的 AS2 接收埠的名稱訊息 (`RecvAS2Msg`); 至於**分組**，接受**和**。</span><span class="sxs-lookup"><span data-stu-id="c0315-270">On the first line, for **Property**, enter **BTS.ReceivePortName**; for **Operator**, enter **==**; for **Value**, enter the name of the receive port that receives the AS2 message (`RecvAS2Msg`); and for **Group by**, accept **And**.</span></span> <span data-ttu-id="c0315-271">在第二行，如**屬性**，輸入**EdiIntAS.IsAS2PayloadMessage**; 對於**運算子**，輸入**==**; 以及**值**，輸入 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="c0315-271">On the second line, for **Property**, enter **EdiIntAS.IsAS2PayloadMessage**; for **Operator**, enter **==**; and for **Value**, enter **True**.</span></span>  
  
8. <span data-ttu-id="c0315-272">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-272">Click **OK**.</span></span>  
  
9. <span data-ttu-id="c0315-273">按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="c0315-273">Click the **Send Ports** node, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-send-port-to-send-the-mdn-to-a-local-folder"></a><span data-ttu-id="c0315-274">若要建立傳送埠以將 MDN 傳送至本機資料夾</span><span class="sxs-lookup"><span data-stu-id="c0315-274">To create a send port to send the MDN to a local folder</span></span>  
  
1. <span data-ttu-id="c0315-275">在 Windows 檔案總管中，建立本機資料夾，以便將 MDN 傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-275">In Windows Explorer, create a local folder to send the MDN to.</span></span>  
  
2. <span data-ttu-id="c0315-276">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="c0315-276">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
3. <span data-ttu-id="c0315-277">在 **傳送埠屬性**對話方塊中，將傳送埠作為**SendMDNToContoso**。</span><span class="sxs-lookup"><span data-stu-id="c0315-277">In the **Send Port Properties** dialog box, name your send port as **SendMDNToContoso**.</span></span> <span data-ttu-id="c0315-278">選取 **檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-278">Select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
4. <span data-ttu-id="c0315-279">在 [ **FILE 傳輸屬性**] 對話方塊中，如**目的地資料夾**，輸入您要建立為 MDN 傳送目標的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-279">In the **FILE Transport Properties** dialog box, for **Destination folder**, enter the local folder you created to send the MDN to.</span></span>  
  
5. <span data-ttu-id="c0315-280">針對**檔名**，輸入 **%MessageID%.msg**。按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-280">For **File name**, enter **%MessageID%.msg**. Click **OK**.</span></span>  
  
6. <span data-ttu-id="c0315-281">接受預設值是**PassThruTransmit** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="c0315-281">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  
  
7. <span data-ttu-id="c0315-282">按一下 **篩選器**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="c0315-282">Click **Filters** in the console tree.</span></span> <span data-ttu-id="c0315-283">針對**屬性**，輸入**BTS。SPName**; 對於**運算子**，輸入**==**; 對於**值**，輸入傳送 AS2 訊息的傳送埠的名稱 (`SendToFab_RecvMDN`);至於**分組**，接受**和**。</span><span class="sxs-lookup"><span data-stu-id="c0315-283">For **Property**, enter **BTS.SPName**; for **Operator**, enter **==**; for **Value**, enter the name of the send port that sends the AS2 message (`SendToFab_RecvMDN`); and for **Group by**, accept **And**.</span></span> <span data-ttu-id="c0315-284">在第二行中，如**屬性**，輸入**EdiIntAS.IsAS2MdnResponseMessage**。</span><span class="sxs-lookup"><span data-stu-id="c0315-284">On a second line, for **Property**, enter **EdiIntAS.IsAS2MdnResponseMessage**.</span></span> <span data-ttu-id="c0315-285">針對**運算子**，輸入**==**。</span><span class="sxs-lookup"><span data-stu-id="c0315-285">For **Operator**, enter **==**.</span></span> <span data-ttu-id="c0315-286">針對**值**，輸入 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="c0315-286">For **Value**, enter **True**.</span></span>  
  
8. <span data-ttu-id="c0315-287">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-287">Click **OK**.</span></span>  
  
9. <span data-ttu-id="c0315-288">按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="c0315-288">Click the **Send Ports** node, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a><span data-ttu-id="c0315-289">若要為 Fabrikam 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="c0315-289">To create a party and a business profile for Fabrikam</span></span>  
  
1. <span data-ttu-id="c0315-290">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="c0315-290">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2. <span data-ttu-id="c0315-291">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-291">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-292">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0315-292">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c0315-293">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="c0315-293">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="c0315-294">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="c0315-294">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3. <span data-ttu-id="c0315-295">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="c0315-295">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4. <span data-ttu-id="c0315-296">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c0315-296">In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-297">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="c0315-297">When you create a party, a profile is also created.</span></span> <span data-ttu-id="c0315-298">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="c0315-298">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="c0315-299">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c0315-299">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="c0315-300">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0315-300">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a><span data-ttu-id="c0315-301">若要為 Contoso 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="c0315-301">To create a party and a business profile for Contoso</span></span>  
  
1. <span data-ttu-id="c0315-302">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="c0315-302">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2. <span data-ttu-id="c0315-303">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c0315-303">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-304">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0315-304">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c0315-305">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="c0315-305">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="c0315-306">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="c0315-306">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3. <span data-ttu-id="c0315-307">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="c0315-307">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4. <span data-ttu-id="c0315-308">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c0315-308">In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0315-309">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="c0315-309">When you create a party, a profile is also created.</span></span> <span data-ttu-id="c0315-310">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="c0315-310">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="c0315-311">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c0315-311">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="c0315-312">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0315-312">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-an-as2-agreement-between-the-two-business-profiles"></a><span data-ttu-id="c0315-313">若要建立兩個商務設定檔之間的 AS2 協議</span><span class="sxs-lookup"><span data-stu-id="c0315-313">To create an AS2 agreement between the two business profiles</span></span>  
  
1.  <span data-ttu-id="c0315-314">以滑鼠右鍵按一下 **[contoso_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="c0315-314">Right-click **Contoso_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="c0315-315">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0315-315">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
3.  <span data-ttu-id="c0315-316">從**通訊協定**下拉式清單中，選取**AS2**。</span><span class="sxs-lookup"><span data-stu-id="c0315-316">From the **Protocol** drop-down list, select **AS2**.</span></span>  
  
4.  <span data-ttu-id="c0315-317">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Fabrikam**。</span><span class="sxs-lookup"><span data-stu-id="c0315-317">In the **Second Partner** section, from the **Name** drop-down list, select **Fabrikam**.</span></span>  
  
5.  <span data-ttu-id="c0315-318">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**fabrikam_profile**。</span><span class="sxs-lookup"><span data-stu-id="c0315-318">In the **Second Partner** section, from the **Profile** drop-down list, select **Fabrikam_Profile**.</span></span>  
  
     <span data-ttu-id="c0315-319">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="c0315-319">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way AS2 agreement.</span></span>  
  
6.  <span data-ttu-id="c0315-320">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c0315-320">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  
  
    1.  <span data-ttu-id="c0315-321">上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="c0315-321">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="c0315-322">針對**AS2-從**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="c0315-322">For **AS2-From**, enter `Contoso`.</span></span> <span data-ttu-id="c0315-323">針對**AS2-To**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="c0315-323">For **AS2- To**, enter `Fabrikam`.</span></span>  
  
    2.  <span data-ttu-id="c0315-324">在 **通知 (Mdn)** 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c0315-324">In the **Acknowledgements (MDNs)** page, do the following:</span></span>  
  
        1.  <span data-ttu-id="c0315-325">選取 **針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c0315-325">Select the **Process inbound MDN into MessageBox for routing/delivery options** check box.</span></span>  
  
            > [!NOTE]
            >  <span data-ttu-id="c0315-326">檢查**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**所需的測試此逐步解說中，因為則只會傳回的 MDN 放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="c0315-326">Checking the **Process inbound MDN into MessageBox for routing/delivery options** is required for the testing of this walkthrough, because only then will the returned MDN be dropped into the MessageBox.</span></span> <span data-ttu-id="c0315-327">而您也才可以建立傳送埠訂閱 MDN、將 MDN 傳送到本機目錄，好讓您確認 AS2 傳輸。</span><span class="sxs-lookup"><span data-stu-id="c0315-327">That enables you to create a send port to subscribe to the MDN, and to send the MDN to a local directory, so you can verify the AS2 transmission.</span></span>  
  
        2.  <span data-ttu-id="c0315-328">選取 **的 要求 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c0315-328">Select the **Request MDN** check box.</span></span>  
  
        3.  <span data-ttu-id="c0315-329">請確定**要求簽署的 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c0315-329">Make sure the **Request Signed MDN** check box is cleared.</span></span>  
  
        4.  <span data-ttu-id="c0315-330">離開**要求非同步 MDN**清除。</span><span class="sxs-lookup"><span data-stu-id="c0315-330">Leave **Request asynchronous MDN** cleared.</span></span>  
  
        5.  <span data-ttu-id="c0315-331">在 **配置通知到**，輸入任何值。</span><span class="sxs-lookup"><span data-stu-id="c0315-331">In **Disposition-Notification-To**, enter any value.</span></span> <span data-ttu-id="c0315-332">在 AS2 處理期間並不會使用這個欄位值，但還是必須在該欄位中輸入值。</span><span class="sxs-lookup"><span data-stu-id="c0315-332">The value of this field is not used during AS2 processing, but a value must be entered in the field.</span></span>  
  
    3.  <span data-ttu-id="c0315-333">在 **傳送埠**頁面上，建立將用來傳送 EDI 交換給 Fabrikam 的雙向傳送埠的關聯。</span><span class="sxs-lookup"><span data-stu-id="c0315-333">On the **Send Ports** page, associate the two-way send port that will be sending the EDI interchange to Fabrikam.</span></span> <span data-ttu-id="c0315-334">在 **傳送埠**格線底下**名稱**資料行中，按一下空白儲存格，並從下拉式清單中，選取 傳送埠**SendToFab_RecvMDN**。</span><span class="sxs-lookup"><span data-stu-id="c0315-334">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port **SendToFab_RecvMDN**.</span></span>  
  
7.  <span data-ttu-id="c0315-335">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c0315-335">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0315-336">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="c0315-336">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="c0315-337">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**AS2_From**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="c0315-337">To successfully create an agreement, both one-way agreement tabs must have values defined for **AS2_From** and **AS2-To**.</span></span>  
  
    1.  <span data-ttu-id="c0315-338">上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。</span><span class="sxs-lookup"><span data-stu-id="c0315-338">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="c0315-339">針對**AS2-從**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="c0315-339">For **AS2-From**, enter `Fabrikam`.</span></span> <span data-ttu-id="c0315-340">針對**AS2-To**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="c0315-340">For **AS2- To**, enter `Contoso`.</span></span>  
  
8.  <span data-ttu-id="c0315-341">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="c0315-341">Click **Apply**.</span></span>  
  
9. <span data-ttu-id="c0315-342">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c0315-342">Click **OK**.</span></span> <span data-ttu-id="c0315-343">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="c0315-343">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="c0315-344">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="c0315-344">The newly added agreement is enabled by default.</span></span>  
  
### <a name="testing-the-walkthrough"></a><span data-ttu-id="c0315-345">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="c0315-345">Testing the Walkthrough</span></span>  
 <span data-ttu-id="c0315-346">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="c0315-346">This section provides information on how to test the walkthrough.</span></span>  
  
##### <a name="to-test-the-solution"></a><span data-ttu-id="c0315-347">測試方案</span><span class="sxs-lookup"><span data-stu-id="c0315-347">To test the solution</span></span>  
  
1.  <span data-ttu-id="c0315-348">在 [Windows 檔案總管] 中，將 XML 測試檔案貼入到您為了接收 Contoso 測試訊息而建立的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-348">In Windows Explorer, paste your XML test file into the local folder that you created to receive the test message from Contoso.</span></span>  
  
2.  <span data-ttu-id="c0315-349">移至您建立用來傳送 XML 內容的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-349">Move to the local folder that you created to send the XML payload to.</span></span> <span data-ttu-id="c0315-350">確認該資料夾包含 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0315-350">Confirm that the folder contains an XML file.</span></span> <span data-ttu-id="c0315-351">開啟檔案和原始測試訊息，並確認其內容是相同的。</span><span class="sxs-lookup"><span data-stu-id="c0315-351">Open the file and the original test message, and verify that they have the same content.</span></span>  
  
3.  <span data-ttu-id="c0315-352">移至您建立用來做為結果 MDN 之傳送目標的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0315-352">Move to the local folder that you created to send the resulting MDN to.</span></span> <span data-ttu-id="c0315-353">確認該資料夾包含一個檔案，開啟該檔案並確認是否為 MDN 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0315-353">Confirm that the folder contains a file; open the file and confirm that it is an MDN file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0315-354">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0315-354">See Also</span></span>  
 <span data-ttu-id="c0315-355">[開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="c0315-355">[Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md) </span></span>  
 [<span data-ttu-id="c0315-356">透過 AS2 從傳送端處理外寄非 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="c0315-356">Send-Side Processing of an Outgoing Non-EDI Message over AS2</span></span>](../core/send-side-processing-of-an-outgoing-non-edi-message-over-as2.md)