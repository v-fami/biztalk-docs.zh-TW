---
title: TIBCO Enterprise Message Service 配接器功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede748ce-3f28-4942-b2bd-e38e5f1b0f54
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce63950ea9fca42969a7d8574fec76f438ed5f8f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015133"
---
# <a name="tibco-ems-adapter-features"></a><span data-ttu-id="1b895-102">TIBCO EMS 配接器功能</span><span class="sxs-lookup"><span data-stu-id="1b895-102">TIBCO EMS Adapter Features</span></span>
<span data-ttu-id="1b895-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 可讓您使用 BizTalk Server 和 TIBCO SDK 來發佈和訂閱由 TIBCO EMS 所管理的佇列和主題。</span><span class="sxs-lookup"><span data-stu-id="1b895-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) enables you to publish and subscribe to queues and topics managed by TIBCO EMS, using BizTalk Server and the TIBCO SDK.</span></span> <span data-ttu-id="1b895-104">此配接器以快速、 簡易而可靠的方式與 TIBCO EMS 訊息整合。</span><span class="sxs-lookup"><span data-stu-id="1b895-104">The adapter integrates TIBCO EMS messages in a fast, easy, and reliable way.</span></span> <span data-ttu-id="1b895-105">其在 TIBCO EMS 伺服器與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之間交換 XML 資料格式，以提供緊密整合而可靠的應用程式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="1b895-105">It exchanges XML data formats between TIBCO EMS servers and Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to provide a tightly integrated and reliable application infrastructure.</span></span> <span data-ttu-id="1b895-106">它會提供傳輸和接收配接器整合作業提供端對端商務程序管理使用 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1b895-106">It provides transmit and receive adapter integration operations providing end-to-end business-process management using XML schemas.</span></span>  
  
## <a name="data-validation"></a><span data-ttu-id="1b895-107">資料驗證</span><span class="sxs-lookup"><span data-stu-id="1b895-107">Data Validation</span></span>  
 <span data-ttu-id="1b895-108">BizTalk Adapter for TIBCO EMS 會以嚴密整合的原生內含式配接器形式，搭配 BizTalk Server 主控件執行，並且會在進行設定時驗證連接埠設定。</span><span class="sxs-lookup"><span data-stu-id="1b895-108">BizTalk Adapter for TIBCO EMS runs in-process with the BizTalk Server host as a native, tightly integrated adapter and validates port configuration at the time of configuration.</span></span> <span data-ttu-id="1b895-109">它會盡量驗證許多資料，例如有效名稱、有效數字、有效範圍。</span><span class="sxs-lookup"><span data-stu-id="1b895-109">It validates the data as much as possible--for example, valid name, valid number, valid in range.</span></span> <span data-ttu-id="1b895-110">它不會嘗試建立連線。</span><span class="sxs-lookup"><span data-stu-id="1b895-110">It does not try to make a connection.</span></span> <span data-ttu-id="1b895-111">因此，主控件、連接埠目的地、使用者和密碼在到了執行階段被呼叫之前，都未經過驗證，在此情況下就會記錄錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1b895-111">Therefore, the host, port destination, user, and password are not validated until there is a run-time call, in which case an error is logged.</span></span>  
  
## <a name="message-delivery"></a><span data-ttu-id="1b895-112">訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="1b895-112">Message Delivery</span></span>  
 <span data-ttu-id="1b895-113">BizTalk Adapter for TIBCO EMS 保證訊息只會傳遞一次。</span><span class="sxs-lookup"><span data-stu-id="1b895-113">BizTalk Adapter for TIBCO EMS guarantees one-time-only delivery of messages.</span></span> <span data-ttu-id="1b895-114">未到達 EMS 而遭到擱置的訊息會標示為可重試。</span><span class="sxs-lookup"><span data-stu-id="1b895-114">Messages that do not reach EMS are marked as retryable when suspended.</span></span> <span data-ttu-id="1b895-115">但也可能會有一些例外，例如執行時有無效的連接埠組態存在。</span><span class="sxs-lookup"><span data-stu-id="1b895-115">There can be some exceptions to this, for example, when an invalid port configuration exists at the time of execution.</span></span>  
  
 <span data-ttu-id="1b895-116">此配接器會接受文字 EMS 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1b895-116">The adapter accepts text EMS message types.</span></span>  <span data-ttu-id="1b895-117">配接器支援前往 EMS，訊息的交易和交易支援由[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1b895-117">The adapter supports transactions for messages going to EMS, and the transaction support is controlled by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b895-118">BizTalk Adapter for TIBCO EMS 與 EMS 伺服器之間使用不安全的連線。</span><span class="sxs-lookup"><span data-stu-id="1b895-118">The connection between BizTalk Adapter for TIBCO EMS and the EMS server is not secure.</span></span> <span data-ttu-id="1b895-119">所提供的 TIBCO EMS SDK 並不支援此連線。</span><span class="sxs-lookup"><span data-stu-id="1b895-119">It is not supported by the provided TIBCO EMS SDK.</span></span>  
  
 <span data-ttu-id="1b895-120">此配接器支援所有標準的 JMS 屬性和 EMS 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1b895-120">The adapter supports all standard JMS properties and EMS extensions.</span></span> <span data-ttu-id="1b895-121">這些屬性會放在 BizTalk 訊息內容中以供協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="1b895-121">These properties are put in the BizTalk message context to be available to an orchestration.</span></span>  
  
## <a name="general-adapter-features"></a><span data-ttu-id="1b895-122">一般配接器功能</span><span class="sxs-lookup"><span data-stu-id="1b895-122">General Adapter Features</span></span>  
 <span data-ttu-id="1b895-123">BizTalk Adapter for TIBCO EMS 提供一種在 TIBCO EMS 系統與 BizTalk Server 之間交換即時商務資料的方法。</span><span class="sxs-lookup"><span data-stu-id="1b895-123">BizTalk Adapter for TIBCO EMS provides a means to exchange real-time business data between TIBCO EMS systems and BizTalk Server.</span></span> <span data-ttu-id="1b895-124">此配接器讓 XML 應用程式與 TIBCO EMS 得以彼此互動。</span><span class="sxs-lookup"><span data-stu-id="1b895-124">The adapter allows for interaction between an XML application and TIBCO EMS.</span></span> <span data-ttu-id="1b895-125">其可讓 XML 應用程式處理輸入自或輸出至 TIBCO EMS 的訊息。</span><span class="sxs-lookup"><span data-stu-id="1b895-125">It enables XML applications for inbound and outbound processing with TIBCO EMS.</span></span>  
  
 <span data-ttu-id="1b895-126">此配接器會使用下列其中一項接受 XML 訊息，讓 BizTalk Server 應用程式能夠與 TIBCO EMS 進行通訊：</span><span class="sxs-lookup"><span data-stu-id="1b895-126">The adapter accepts XML messages to enable BizTalk Server applications to communicate with TIBCO EMS using one of the following:</span></span>  
  
-   <span data-ttu-id="1b895-127">傳輸配接器，使用「靜態單向傳送埠」來傳送訊息給 TIBCO EMS。</span><span class="sxs-lookup"><span data-stu-id="1b895-127">Transmit Adapter, which uses a Static One-Way Send port to send a message to TIBCO EMS.</span></span>  
  
-   <span data-ttu-id="1b895-128">接收配接器，使用「靜態單向接收埠」接收來自 TIBCO EMS 的訊息。</span><span class="sxs-lookup"><span data-stu-id="1b895-128">Receive Adapter, which uses a Static One-Way Receive port to receive messages from TIBCO EMS.</span></span>  
  
### <a name="transmit-adapter-architecture-send--static-one-way"></a><span data-ttu-id="1b895-129">傳輸配接器架構： 傳送 – 靜態單向</span><span class="sxs-lookup"><span data-stu-id="1b895-129">Transmit Adapter Architecture: Send – Static One-Way</span></span>  
 <span data-ttu-id="1b895-130">在單向傳送的實例中，傳送埠會設定為將訊息傳送至某個佇列/主題。</span><span class="sxs-lookup"><span data-stu-id="1b895-130">In the one-way send scenario, the send port is configured to send messages to a queue/topic.</span></span> <span data-ttu-id="1b895-131">BizTalk Adapter for TIBCO Enterprise Message Service 會將所指定的佇列/主題上的要求轉寄給 TIBCO EMS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b895-131">BizTalk Adapter for TIBCO Enterprise Message Service forwards the request to the TIBCO EMS server on the specified queue/topic.</span></span> <span data-ttu-id="1b895-132">此配接器會使用 TIBCO EMS 通訊協定將訊息傳送給 TIBCO EMS 系統。</span><span class="sxs-lookup"><span data-stu-id="1b895-132">The adapter sends the message to the TIBCO EMS system using TIBCO EMS communication protocol.</span></span> <span data-ttu-id="1b895-133">TIBCO EMS 系統會接收要求，然後執行商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="1b895-133">The TIBCO EMS system receives the requests and executes the business logic.</span></span> <span data-ttu-id="1b895-134">若要呼叫 TIBCO EMS，您必須提供此配接器和用於存取 TIBCO EMS 伺服器的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="1b895-134">To make calls into TIBCO EMS, you must provide the adapter with the configuration information to access the TIBCO EMS server.</span></span>  
  
 <span data-ttu-id="1b895-135">下圖顯示此配接器的單向傳送作業。</span><span class="sxs-lookup"><span data-stu-id="1b895-135">The following image shows the adapter's one-way send operation.</span></span>  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
### <a name="receive-adapter-architecture-receive--static-one-way"></a><span data-ttu-id="1b895-136">接收配接器架構： 接收 – 靜態單向</span><span class="sxs-lookup"><span data-stu-id="1b895-136">Receive Adapter Architecture: Receive – Static One-Way</span></span>  
 <span data-ttu-id="1b895-137">在單向接收的實例中，接收位置會設定為接收某個 EMS 佇列/主題上的訊息。</span><span class="sxs-lookup"><span data-stu-id="1b895-137">In the one-way receive scenario, the receive location is configured to receive messages on an EMS queue/topic.</span></span> <span data-ttu-id="1b895-138">BizTalk Adapter for TIBCO EMS 會接聽所指定佇列/主題上的訊息，然後將收到的訊息提交給 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b895-138">BizTalk Adapter for TIBCO EMS listens for messages on a specified queue/topic and submits the received messages to BizTalk Server.</span></span>  
  
 <span data-ttu-id="1b895-139">下圖顯示此配接器的單向接收作業。</span><span class="sxs-lookup"><span data-stu-id="1b895-139">The following image shows the adapter's one-way receive operation.</span></span>  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a><span data-ttu-id="1b895-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b895-140">See Also</span></span>  
 <span data-ttu-id="1b895-141">[開發應用程式](../core/developing-applications5.md) </span><span class="sxs-lookup"><span data-stu-id="1b895-141">[Developing Applications](../core/developing-applications5.md) </span></span>  
 [<span data-ttu-id="1b895-142">快速入門</span><span class="sxs-lookup"><span data-stu-id="1b895-142">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)