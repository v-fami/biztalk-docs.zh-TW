---
title: 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- adapters
- send adapters
- adapters, about adapters
- send adapters, about send adapters
- receive adapters, about receive adapters
- adapters, adapter framework
- receive adapters
- adapters, send adapters
ms.assetid: 7803a806-3396-4662-877f-eae11cb5e3e4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c16fc3dd95145d35bd09aeb049d7d38df979e6a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022932"
---
# <a name="adapters"></a><span data-ttu-id="72b5c-102">配接器</span><span class="sxs-lookup"><span data-stu-id="72b5c-102">Adapters</span></span>
<span data-ttu-id="72b5c-103">Microsoft BizTalk Server 使用配接器的概念與外部系統、應用程式和實體交換訊息。</span><span class="sxs-lookup"><span data-stu-id="72b5c-103">To exchange messages with external systems, applications, and entities Microsoft BizTalk Server uses the concept of an adapter.</span></span> <span data-ttu-id="72b5c-104">*配接器*都是 COM 或。以.NET 為基礎的元件傳送商務端點 （例如檔案系統、 資料庫和自訂商務應用程式） 的訊息，使用各種通訊協定。</span><span class="sxs-lookup"><span data-stu-id="72b5c-104">*Adapters* are COM or .NET-based components that transfer messages to and from business endpoints (such as file systems, databases, and custom business applications) using various communication protocols.</span></span>  
  
 <span data-ttu-id="72b5c-105">BizTalk Server 使用配接器以傳送和接收作業與外部實體交換訊息。</span><span class="sxs-lookup"><span data-stu-id="72b5c-105">Adapters are used by BizTalk Server to exchange messages with external entities in send and receive operations</span></span>  
  
-   <span data-ttu-id="72b5c-106">BizTalk Server 使用配接器支援的通訊協定，將資訊傳送至外部實體時，即為發生傳送 (或傳送端) 作業。</span><span class="sxs-lookup"><span data-stu-id="72b5c-106">Send (or send-side) operations occur when information is being sent by BizTalk Server to an external entity using the protocols supported by the adapter.</span></span>  
  
-   <span data-ttu-id="72b5c-107">當配接器收到來自外部實體的資訊，並將它傳送至「BizTalk Server 傳訊引擎」時，即為發生接收 (或接收端) 作業。</span><span class="sxs-lookup"><span data-stu-id="72b5c-107">Receive (or receive-side) operations occur when the adapter receives information from an external entity and passes it into the BizTalk Server Messaging Engine.</span></span>  
  
## <a name="the-adapter-framework"></a><span data-ttu-id="72b5c-108">配接器架構</span><span class="sxs-lookup"><span data-stu-id="72b5c-108">The Adapter Framework</span></span>  
 <span data-ttu-id="72b5c-109">下圖顯示配接器和「配接器架構」如何共同運作，將應用程式連線至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="72b5c-109">The following figure shows how an adapter and the Adapter Framework work together to connect your application to BizTalk Server.</span></span>  
  
1. <span data-ttu-id="72b5c-110">資料是透過接收位置接收，該位置在指定的位址聆聽特定通訊協定的訊息。</span><span class="sxs-lookup"><span data-stu-id="72b5c-110">Data is received through a receive location that is listening for messages of a certain protocol at a specified address.</span></span> <span data-ttu-id="72b5c-111">接收位置與配接器和接收管線相關聯。</span><span class="sxs-lookup"><span data-stu-id="72b5c-111">The receive location is associated with an adapter and a receive pipeline.</span></span> <span data-ttu-id="72b5c-112">您可以設定配接器和管線元件，對已預先決定通訊協定的訊息執行特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="72b5c-112">You can configure both the adapter and the pipeline components to perform certain logic on messages having a predetermined protocol.</span></span>  
  
2. <span data-ttu-id="72b5c-113">接收位置收到訊息後，便會將訊息傳送至配接器，而建立新的 BizTalk Server 訊息，將資料流附加到訊息 (通常在訊息的內文部分)，新增與接收資料的結束點相關的任何中繼資料，然後將該訊息提交至「傳訊引擎」。</span><span class="sxs-lookup"><span data-stu-id="72b5c-113">After the message is received by the receive location, the message is sent to the adapter, which creates a new BizTalk Server message, attaches the data stream to the message (typically in the body part of the message), adds any metadata pertaining to the endpoint over which the data was received, and then submits that message into the Messaging Engine.</span></span>  
  
3. <span data-ttu-id="72b5c-114">傳訊引擎將訊息傳送到接收管線，讓資料在此轉換成 XML，並在此驗證訊息傳送者、解密訊息及驗證 XML。</span><span class="sxs-lookup"><span data-stu-id="72b5c-114">The Messaging Engine sends the message to the receive pipeline where the data is transformed into XML, the message sender is authenticated, the message is decrypted, and the XML is validated.</span></span>  
  
4. <span data-ttu-id="72b5c-115">「傳訊引擎」將訊息發佈至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="72b5c-115">The Messaging Engine publishes the message to the MessageBox.</span></span> <span data-ttu-id="72b5c-116">MessageBox 是一個 Microsoft SQL Server 資料表，其中包含要處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="72b5c-116">The MessageBox is a Microsoft SQL Server table containing messages to be processed.</span></span> <span data-ttu-id="72b5c-117">協調流程和傳送埠兩者都可以訂閱 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="72b5c-117">Both orchestrations and send ports can subscribe to the MessageBox.</span></span>  
  
5. <span data-ttu-id="72b5c-118">傳訊引擎根據符合訂閱者在篩選條件中設定之規格的訊息內容屬性，將訊息傳送到協調流程或傳送埠訂閱者。</span><span class="sxs-lookup"><span data-stu-id="72b5c-118">The Messaging Engine sends the message to either an orchestration or a send port subscriber based upon the message context properties matching the specifications set in the filter on the subscriber.</span></span>  
  
6. <span data-ttu-id="72b5c-119">若協調流程為訂閱者，協調流程會處理訊息並使用傳送埠將訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="72b5c-119">If an orchestration is the subscriber, it processes the message and sends it out using a send port.</span></span> <span data-ttu-id="72b5c-120">當訊息抵達傳送埠或當傳送埠是唯一的訂閱者時，會先透過傳送管線將訊息傳送到傳送配接器，之後才會在網路上傳輸。</span><span class="sxs-lookup"><span data-stu-id="72b5c-120">After the send port has it, or is the only subscriber, the message passes through the send pipeline into a send adapter before being transmitted over the wire.</span></span>  
  
   <span data-ttu-id="72b5c-121">配接器架構</span><span class="sxs-lookup"><span data-stu-id="72b5c-121">The Adapter Framework</span></span>  
  
   <span data-ttu-id="72b5c-122">![配接器架構](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span><span class="sxs-lookup"><span data-stu-id="72b5c-122">![The adapter framework](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span></span>  
  
## <a name="receive-adapters"></a><span data-ttu-id="72b5c-123">接收配接器</span><span class="sxs-lookup"><span data-stu-id="72b5c-123">Receive Adapters</span></span>  
 <span data-ttu-id="72b5c-124">接收配接器負責將網路/資料來源資料流附加到訊息內文，以建立新的 BizTalk Server 訊息。</span><span class="sxs-lookup"><span data-stu-id="72b5c-124">Receive adapters are responsible for creating a new BizTalk Server message by attaching the network/data source stream to the message body.</span></span> <span data-ttu-id="72b5c-125">它也會新增與接收資料的結束點有關的任何中繼資料，然後將該訊息提交至傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="72b5c-125">It also adds any metadata pertinent to the endpoint over which the data was received, then submits that message to the Messaging Engine.</span></span>  
  
 <span data-ttu-id="72b5c-126">配接器將接收結束點的資料刪除，或是將適當的通知訊息傳送到用戶端，以表示 BizTalk Server 已接受資料。</span><span class="sxs-lookup"><span data-stu-id="72b5c-126">The adapter deletes the data from the receive endpoint or sends the appropriate acknowledgement message to the client indicating that the data has been accepted into BizTalk Server.</span></span>  
  
## <a name="send-adapters"></a><span data-ttu-id="72b5c-127">傳送配接器</span><span class="sxs-lookup"><span data-stu-id="72b5c-127">Send Adapters</span></span>  
 <span data-ttu-id="72b5c-128">傳送配接器負責使用其特定的傳輸通訊協定，將 BizTalk 訊息傳送到指定的結束點。</span><span class="sxs-lookup"><span data-stu-id="72b5c-128">Send adapters are responsible for sending a BizTalk message to the specified endpoint using its specific transport protocol.</span></span>  
  
 <span data-ttu-id="72b5c-129">如需有關配接器的詳細資訊，請的結構，配接器，以及撰寫自訂配接器，請參閱[開發自訂配接器](../core/developing-custom-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="72b5c-129">For more information about adapters, the structure of an adapter, and writing custom adapters, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b5c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72b5c-130">See Also</span></span>  
 [<span data-ttu-id="72b5c-131">成品</span><span class="sxs-lookup"><span data-stu-id="72b5c-131">Artifacts</span></span>](../core/artifacts.md)