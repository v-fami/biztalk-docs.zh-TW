---
title: '教學課程 3: AS2 教學課程 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 018829a9-e670-4b87-bac5-7f7b1332d90e
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03de45aa09b2704f205b81db4c513a0da5770ee3
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22287550"
---
# <a name="tutorial-3-as2-tutorial"></a><span data-ttu-id="48b80-102">教學課程 3: AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="48b80-102">Tutorial 3: AS2 Tutorial</span></span>
<span data-ttu-id="48b80-103">在本教學課程中，您將設定透過 HTTP 傳輸接收和傳送 EDIINT/AS2 編碼訊息的解決方案。</span><span class="sxs-lookup"><span data-stu-id="48b80-103">In this tutorial, you set up a solution that receives and sends EDIINT/AS2-encoded messages over an HTTP transport.</span></span>  
  
 <span data-ttu-id="48b80-104">**教學課程解決方案的運作方式**</span><span class="sxs-lookup"><span data-stu-id="48b80-104">**How the Tutorial Solution Works**</span></span>  
  
 <span data-ttu-id="48b80-105">解決方案會執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="48b80-105">The solution will do the following:</span></span>  
  
-   <span data-ttu-id="48b80-106">從夥伴 (Fabrikam) 接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="48b80-106">Receive an AS2 message from a partner (Fabrikam)</span></span>  
  
-   <span data-ttu-id="48b80-107">以非同步方式將 MDN 回應傳回給夥伴</span><span class="sxs-lookup"><span data-stu-id="48b80-107">Return an MDN response asynchronously to the partner</span></span>  
  
-   <span data-ttu-id="48b80-108">處理 AS2 訊息的 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="48b80-108">Process the EDI payload of the AS2 message</span></span>  
  
-   <span data-ttu-id="48b80-109">透過 AS2 將 997 通知傳回給夥伴 (Fabrikam)</span><span class="sxs-lookup"><span data-stu-id="48b80-109">Return a 997 acknowledgment to the partner (Fabrikam) over AS2</span></span>  
  
-   <span data-ttu-id="48b80-110">將含有 EDI 訊息內容的 XML 檔案路由傳送至主要組織 (Contoso) 的後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="48b80-110">Route an XML file containing the payload of the EDI message to a backend application of the home organization (Contoso).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48b80-111">這個解決方案不會使用簽章或加密來協助確保 AS2 訊息的安全性。</span><span class="sxs-lookup"><span data-stu-id="48b80-111">This solution does not use signing or encryption to help ensure the security of AS2 messages.</span></span>  
  
 <span data-ttu-id="48b80-112">**教學課程元件**</span><span class="sxs-lookup"><span data-stu-id="48b80-112">**Tutorial Components**</span></span>  
  
 <span data-ttu-id="48b80-113">這個解決方案將使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="48b80-113">This solution will use the following:</span></span>  
  
-   <span data-ttu-id="48b80-114">BTS Http 接收 ISAPI 篩選器來接收 AS2/EDI 訊息寄件者 **(/Contoso/BTSHTTPReceive.dll**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-114">A BTS Http Receive ISAPI Filter to receive the AS2/EDI message from the sender **(/Contoso/BTSHTTPReceive.dll**).</span></span>  
  
-   <span data-ttu-id="48b80-115">若要透過傳回 997 通知和 MDN 模擬夥伴的 ASPX 網頁 (**http://localhost/Fabrikam/Default.aspx**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-115">An ASPX Web page to simulate the partner by returning a 997 acknowledgment and an MDN (**http://localhost/Fabrikam/Default.aspx**).</span></span>  
  
-   <span data-ttu-id="48b80-116">您用來部署 864 結構描述和其他結構描述的專案檔 (**Schemas.btproj**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-116">A project file that you will use to deploy an 864 schema and other schemas (**Schemas.btproj**).</span></span>  
  
-   <span data-ttu-id="48b80-117">單向 HTTP 接收位置來接收 EDI 檔案 (**Receive_AS2**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-117">A one-way HTTP receive location to receive the EDI file (**Receive_AS2**).</span></span> <span data-ttu-id="48b80-118">這個接收位置會使用含有 AS2 解碼器和 EDI 解譯器的預設 AS2EdiReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="48b80-118">This receive location uses the default AS2EdiReceive pipeline that contains the AS2 Decoder and EDI Disassembler.</span></span>  
  
-   <span data-ttu-id="48b80-119">動態 HTTP 傳送埠以傳回非同步 MDN (**Send_Async_MDN**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-119">A dynamic HTTP send port to return an asynchronous MDN (**Send_Async_MDN**).</span></span> <span data-ttu-id="48b80-120">這個傳送埠會使用含有 AS2 編碼器的 AS2Send 管線。</span><span class="sxs-lookup"><span data-stu-id="48b80-120">This send port uses the AS2Send pipeline that contains the AS2 Encoder.</span></span>  
  
-   <span data-ttu-id="48b80-121">靜態單向 FILE 傳送埠以將 EDI 內容路由傳送到後端資料夾的 XML 檔案中 (**Send_Payload_EdiXml**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-121">A static one-way FILE send port to route the EDI payload in an XML file to a back-end folder (**Send_Payload_EdiXml**).</span></span> <span data-ttu-id="48b80-122">這個傳送埠會使用 PassThruTransmit 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="48b80-122">This send port uses the PassThruTransmit send pipeline.</span></span>  
  
-   <span data-ttu-id="48b80-123">靜態單向 HTTP 傳送埠以透過 AS2 將 997 通知傳回給夥伴 (**Send_Async_997**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-123">A static one-way HTTP send port to return a 997 acknowledgment to the partner over AS2 (**Send_Async_997**).</span></span> <span data-ttu-id="48b80-124">這個傳送埠會使用包含 AS2 編碼器 (但不需要 EDI 組合器) 的 AS2Send 管線。</span><span class="sxs-lookup"><span data-stu-id="48b80-124">This send port uses the AS2Send pipeline that includes the AS2 Encoder, but has no need for the EDI Assembler.</span></span>  
  
-   <span data-ttu-id="48b80-125">您將用來建置應用程式以將 EDI 檔案從 Fabrikam 夥伴傳送至 BizTalk 專案檔 (**Sender.csproj**)。</span><span class="sxs-lookup"><span data-stu-id="48b80-125">A project file that you will use to build an application to send the EDI file from the Fabrikam partner to BizTalk (**Sender.csproj**).</span></span>  
  
 <span data-ttu-id="48b80-126">**訊息流程**</span><span class="sxs-lookup"><span data-stu-id="48b80-126">**Message Flow**</span></span>  
  
 <span data-ttu-id="48b80-127">已完成解決方案的訊息流程將顯示在下圖中：</span><span class="sxs-lookup"><span data-stu-id="48b80-127">The message flow in the completed solution will be as shown in the following figure:</span></span>  
  
 <span data-ttu-id="48b80-128">![AS2 教學課程訊息流程](../core/media/31710c1d-4070-433e-953d-dcbfd0bb07a0.gif "31710c1d-4070-433e-953d-dcbfd0bb07a0")</span><span class="sxs-lookup"><span data-stu-id="48b80-128">![AS2 tutorial message flow](../core/media/31710c1d-4070-433e-953d-dcbfd0bb07a0.gif "31710c1d-4070-433e-953d-dcbfd0bb07a0")</span></span>  
  
 <span data-ttu-id="48b80-129">教學課程元件會依照下列方式處理訊息：</span><span class="sxs-lookup"><span data-stu-id="48b80-129">The tutorial components process the message as follows:</span></span>  
  
1.  <span data-ttu-id="48b80-130">您使用 **sender.exe 應用程式** 從夥伴 Fabrikam 的原始 EDI/AS2 訊息傳送到 BizTalk Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="48b80-130">You use the **sender.exe application** to send the original EDI/AS2 message from the partner Fabrikam to the BizTalk Server computer.</span></span> <span data-ttu-id="48b80-131">Sender.exe 會將 EDI/AS2 訊息傳送至 Contoso 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="48b80-131">Sender.exe sends the EDI/AS2 message to the Contoso virtual directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48b80-132">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="48b80-132">The events in this list may not occur in the order shown.</span></span>  
    >   
    >  <span data-ttu-id="48b80-133">測試訊息是 files\microsoft BizTalk Server 20xx\SDK\AS2 教學課程中的 X12_00401_864.edi。</span><span class="sxs-lookup"><span data-stu-id="48b80-133">The test message is X12_00401_864.edi in \Program Files\Microsoft BizTalk Server 20xx\SDK\AS2 Tutorial.</span></span>  
  
2.  <span data-ttu-id="48b80-134">**Receive_AS2** 單向接收位置接收 EDI 訊息從 Fabrikam 挑選檔案從 Contoso 虛擬目錄使用 BTSHTTPReceive.dll ISAPI 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="48b80-134">The **Receive_AS2** one-way receive location receives the EDI message from Fabrikam, using the BTSHTTPReceive.dll ISAPI extension to pick the file up from the Contoso virtual directory.</span></span> <span data-ttu-id="48b80-135">此接收管線會解碼 AS2 訊息、解譯 EDI 交換，然後將訊息 XML 放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="48b80-135">The receive pipeline decodes the AS2 message, disassembles the EDI interchange, and then drops the message XML into the MessageBox.</span></span>  
  
3.  <span data-ttu-id="48b80-136">此接收管線會產生 AS2 訊息的 MDN，而且因為 MDN 設定為非同步，所以此接收管線會將 MDN 放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="48b80-136">The receive pipeline generates an MDN for the AS2 message, and since the MDN is set up to be asynchronous, the receive pipeline drops the MDN into the MessageBox.</span></span>  
  
4.  <span data-ttu-id="48b80-137">此接收管線會產生 997 通知，以便回應 EDI 交換，然後將 997 放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="48b80-137">The receive pipeline generates a 997 acknowledgment in response to the EDI interchange, and drops the 997 into the MessageBox.</span></span>  
  
5.  <span data-ttu-id="48b80-138">**Send_Payload_EdiXml** 靜態單向傳送埠會拾取 EDI 內容 MessageBox 的 BTS 進行篩選。訊息類型的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="48b80-138">The **Send_Payload_EdiXml** static one-way send port picks up the EDI payload from the MessageBox, filtering on the BTS.MessageType context property.</span></span>  
  
6.  <span data-ttu-id="48b80-139">裝載傳送埠將包含 EDI 內容後端 Contoso 應用程式所代表的 XML 檔案 \\_EDIXMLToContoso 資料夾。</span><span class="sxs-lookup"><span data-stu-id="48b80-139">The payload send port sends the XML file containing the EDI payload to the back-end Contoso application, represented by the \\_EDIXMLToContoso folder.</span></span> <span data-ttu-id="48b80-140">這個傳送埠會使用 PassThruTransmit 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="48b80-140">This send port uses a PassThruTransmit send pipeline.</span></span>  
  
7.  <span data-ttu-id="48b80-141">**Send_Async_MDN** 動態傳送埠取用非同步 MDN 從 MessageBox 針對 EdiIntAS.IsAS2AsynchronousMdn 內容屬性進行篩選。</span><span class="sxs-lookup"><span data-stu-id="48b80-141">The **Send_Async_MDN** dynamic send port picks up the asynchronous MDN from the MessageBox, filtering on the EdiIntAS.IsAS2AsynchronousMdn context property.</span></span>  
  
8.  <span data-ttu-id="48b80-142">MDN 將傳送埠傳回 MDN \\_MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="48b80-142">The MDN send port returns the MDN to the \\_MDNToFabrikam folder.</span></span> <span data-ttu-id="48b80-143">由於這是動態傳送埠時，它會使用位址的訊息標頭中的回條傳遞選項一行 (**http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam**) 若要將訊息路由至\\_MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="48b80-143">Since this is a dynamic send port, it will use the address in the Receipt-Delivery-Option line in the header of the message (**http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam**) to route the message to the \\_MDNToFabrikam folder.</span></span>  
  
9. <span data-ttu-id="48b80-144">**Send_Async_997** 傳送埠收取 997 從 MessageBox BTS 的篩選。訊息類型的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="48b80-144">The **Send_Async_997** send port picks up the 997 from the MessageBox, filtering on the BTS.MessageType context property.</span></span>  
  
10. <span data-ttu-id="48b80-145">997 傳送埠會使用 HTTP 傳輸，將 EdiReceive 所產生的 997 訊息接收管線 \\_997ToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="48b80-145">The 997 send port uses HTTP transport to send the 997 message generated by the EdiReceive receive pipeline to the \\_997ToFabrikam folder.</span></span> <span data-ttu-id="48b80-146">傳送埠將訊息傳送至 Fabrikam default.aspx 頁面中，使用 URI **http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam**。</span><span class="sxs-lookup"><span data-stu-id="48b80-146">The send port sends the message to the Fabrikam default.aspx page, using the URI **http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam**.</span></span> <span data-ttu-id="48b80-147">Default.aspx 網頁接著會傳送到 997 \\_997ToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="48b80-147">The default.aspx page then sends the 997 to the \\_997ToFabrikam folder.</span></span>  
  
 <span data-ttu-id="48b80-148">若要進行這個教學課程，您應該具備下列項目的相關知識：</span><span class="sxs-lookup"><span data-stu-id="48b80-148">To do this tutorial, you should be knowledgeable about the following:</span></span>  
  
-   <span data-ttu-id="48b80-149">BizTalk Server 管線和管線元件</span><span class="sxs-lookup"><span data-stu-id="48b80-149">BizTalk Server pipelines and pipeline components</span></span>  
  
-   <span data-ttu-id="48b80-150">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="48b80-150">HTTP Adapter</span></span>  
  
-   <span data-ttu-id="48b80-151">接收埠與位置</span><span class="sxs-lookup"><span data-stu-id="48b80-151">Receive ports and locations</span></span>  
  
-   <span data-ttu-id="48b80-152">傳送埠</span><span class="sxs-lookup"><span data-stu-id="48b80-152">Send ports</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48b80-153">本節內容</span><span class="sxs-lookup"><span data-stu-id="48b80-153">In This Section</span></span>  
  
-   [<span data-ttu-id="48b80-154">步驟 1：準備 AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="48b80-154">Step 1: Prepare for the AS2 Tutorial</span></span>](../core/step-1-prepare-for-the-as2-tutorial.md)  
  
-   [<span data-ttu-id="48b80-155">步驟 2：建立和部署範例 X12 結構描述</span><span class="sxs-lookup"><span data-stu-id="48b80-155">Step 2: Create and Deploy the Sample X12 Schema</span></span>](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
-   [<span data-ttu-id="48b80-156">步驟 3：為組織設定合作對象和商務設定檔</span><span class="sxs-lookup"><span data-stu-id="48b80-156">Step 3: Configure a Party and Business Profile for Your Organization</span></span>](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md)  
  
-   [<span data-ttu-id="48b80-157">步驟 4：為交易夥伴設定合作對象和商務設定檔</span><span class="sxs-lookup"><span data-stu-id="48b80-157">Step 4: Configure a Party and Business Profile for Your Trading Partner</span></span>](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md)  
  
-   [<span data-ttu-id="48b80-158">步驟 5：設定交易夥伴網頁</span><span class="sxs-lookup"><span data-stu-id="48b80-158">Step 5: Configure the Trading Partner Web Pages</span></span>](../core/step-5-configure-the-trading-partner-web-pages.md)  
  
-   [<span data-ttu-id="48b80-159">步驟 6：設定 EDI-AS2 接收位置</span><span class="sxs-lookup"><span data-stu-id="48b80-159">Step 6: Configure the EDI-AS2 Receive Location</span></span>](../core/step-6-configure-the-edi-as2-receive-location.md)  
  
-   [<span data-ttu-id="48b80-160">步驟 7：設定 MDN 傳送埠</span><span class="sxs-lookup"><span data-stu-id="48b80-160">Step 7: Configure the MDN Send Port</span></span>](../core/step-7-configure-the-mdn-send-port.md)  
  
-   [<span data-ttu-id="48b80-161">步驟 8：設定 997 傳送埠</span><span class="sxs-lookup"><span data-stu-id="48b80-161">Step 8: Configure the 997 Send Port</span></span>](../core/step-8-configure-the-997-send-port.md)  
  
-   [<span data-ttu-id="48b80-162">步驟 9：設定 EDI 內容傳送埠</span><span class="sxs-lookup"><span data-stu-id="48b80-162">Step 9: Configure the EDI Payload Send Port</span></span>](../core/step-9-configure-the-edi-payload-send-port.md)  
  
-   [<span data-ttu-id="48b80-163">步驟 10：設定 X12 和 AS2 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="48b80-163">Step 10: Configure the X12 and AS2 Trading Partner Agreement</span></span>](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
-   [<span data-ttu-id="48b80-164">步驟 11：測試 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="48b80-164">Step 11: Test the AS2 Solution</span></span>](../core/step-11-test-the-as2-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="48b80-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48b80-165">See Also</span></span>  
 [<span data-ttu-id="48b80-166">BizTalk Server 教學課程</span><span class="sxs-lookup"><span data-stu-id="48b80-166">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)