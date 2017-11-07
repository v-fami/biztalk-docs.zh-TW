---
title: "字元編碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a0c21c8-3318-4533-9734-89302527cb67
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 319ddd649e47e053fe2896d577f28b72602593e3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="character-encoding"></a><span data-ttu-id="5c756-102">字元編碼</span><span class="sxs-lookup"><span data-stu-id="5c756-102">Character Encoding</span></span>
<span data-ttu-id="5c756-103">對於從 BizTalk Adapter for TIBCO EMS 傳輸到 EMS 的訊息，TIBCO Enterprise Message Service (EMS) 支援許多字元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="5c756-103">TIBCO Enterprise Message Service (EMS) supports different character encoding in the messages transmitted to EMS by BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="5c756-104">訊息是使用預設的 UTF-8 編碼方式所編碼的。</span><span class="sxs-lookup"><span data-stu-id="5c756-104">Messages are encoded using the default UTF-8 encoding.</span></span> <span data-ttu-id="5c756-105">接收訊息時，配接器會先判斷訊息的編碼方式並轉換適當的字串為 UTF-8 後，才將訊息提供給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5c756-105">When receiving messages, the adapter determines the encoding of the message and converts the appropriate strings to UTF-8 before providing the message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="5c756-106">所有的字元轉換是使用 Microsoft .NET Framework 類別，因此配接器支援這個相同架構所提供的字元轉換。</span><span class="sxs-lookup"><span data-stu-id="5c756-106">All character conversions use the Microsoft .NET Framework classes; therefore the adapter supports the character conversions provided by this same framework.</span></span>  
  
## <a name="running-in-a-clustered-environment"></a><span data-ttu-id="5c756-107">在叢集環境中執行</span><span class="sxs-lookup"><span data-stu-id="5c756-107">Running in a Clustered Environment</span></span>  
 <span data-ttu-id="5c756-108">發佈到佇列中的訊息，會以 EMS 伺服器預先決定的順序，讓取用者使用，所以在叢集 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中，只會有一個配接器收到該訊息。</span><span class="sxs-lookup"><span data-stu-id="5c756-108">Messages published to queues are consumed by the consumers in an order pre-determined by the EMS server—only one adapter in the clustered [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment receives the message.</span></span> <span data-ttu-id="5c756-109">佇列可以設定為*獨佔*。</span><span class="sxs-lookup"><span data-stu-id="5c756-109">The queue can be configured as *exclusive*.</span></span> <span data-ttu-id="5c756-110">這代表只有對佇列自行註冊為訊息取用者的第一個配接器，會接收到訊息。</span><span class="sxs-lookup"><span data-stu-id="5c756-110">This means that only the first adapter that registers itself for message consumption on the queue receives the messages.</span></span> <span data-ttu-id="5c756-111">只有在獨佔取用者不認可訊息接收時，EMS 伺服器才會傳送訊息給其他取用者。</span><span class="sxs-lookup"><span data-stu-id="5c756-111">The EMS server only sends messages to the other consumers if the exclusive consumer does not acknowledge message reception.</span></span> <span data-ttu-id="5c756-112">獨佔佇列組態是由 EMS 組態執行的，用戶端無法進行這項設定。</span><span class="sxs-lookup"><span data-stu-id="5c756-112">Exclusive queue configuration is performed in the EMS configuration and is not client configurable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c756-113">關於主題訂閱： 因為中的所有介面卡[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組的設定都相同，它們都會一起訂閱訊息，每個主題訂閱接收訊息。</span><span class="sxs-lookup"><span data-stu-id="5c756-113">Regarding subscriptions to topics: because all adapters in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group are configured identically, they are all subscribed for the message, and each topic subscription receives the message.</span></span>  
  
## <a name="transaction-support"></a><span data-ttu-id="5c756-114">交易支援</span><span class="sxs-lookup"><span data-stu-id="5c756-114">Transaction Support</span></span>  
 <span data-ttu-id="5c756-115">在協調流程傳送埠需要時，配接器提供交易支援。</span><span class="sxs-lookup"><span data-stu-id="5c756-115">The adapter provides support for transactions when required by the orchestration send ports.</span></span> <span data-ttu-id="5c756-116">配接器聆聽訊息時不提供 EMS 伺服器的交易支援，然而，當在訊息成功提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 後，配接器就會認可所有訊息的接收。</span><span class="sxs-lookup"><span data-stu-id="5c756-116">There is no transaction support with the EMS server when the adapter is listening for messages; however, the adapter acknowledges reception of all messages from EMS after successful message submission to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="5c756-117">EMS 會重寄未認可的訊息給配接器。</span><span class="sxs-lookup"><span data-stu-id="5c756-117">EMS resends unacknowledged messages to the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c756-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c756-118">See Also</span></span>  
 <span data-ttu-id="5c756-119">[BizTalk Adapter for TIBCO EMS 中的安全性](../core/security-in-biztalk-adapter-for-tibco-ems.md) </span><span class="sxs-lookup"><span data-stu-id="5c756-119">[Security in BizTalk Adapter for TIBCO EMS](../core/security-in-biztalk-adapter-for-tibco-ems.md) </span></span>  
 [<span data-ttu-id="5c756-120">快速入門</span><span class="sxs-lookup"><span data-stu-id="5c756-120">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)