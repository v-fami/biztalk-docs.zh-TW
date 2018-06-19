---
title: IBaseMessage 介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10bfb95c-aef5-46ba-ba0e-9961833f27a3
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7de478b27105ee6c01d582aa9b728bd0496d0487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257086"
---
# <a name="ibasemessage-interface"></a><span data-ttu-id="6fc61-102">IBaseMessage 介面</span><span class="sxs-lookup"><span data-stu-id="6fc61-102">IBaseMessage Interface</span></span>
<span data-ttu-id="6fc61-103">當接收配接器接受連入的資料封包，透過其通訊協定時，它會使用**IBaseMessage**介面來建立要傳遞給傳訊引擎的訊息。</span><span class="sxs-lookup"><span data-stu-id="6fc61-103">When a receive adapter accepts an incoming data packet through its protocol, it uses the **IBaseMessage** interface to create a message to pass to the Messaging Engine.</span></span> <span data-ttu-id="6fc61-104">所有訊息都是使用此介面來代表。</span><span class="sxs-lookup"><span data-stu-id="6fc61-104">All messages are represented by using this interface.</span></span>  
  
 <span data-ttu-id="6fc61-105">訊息會有一或多個訊息部分由**IBaseMessagePart**介面。</span><span class="sxs-lookup"><span data-stu-id="6fc61-105">A message has one or more message parts represented by the **IBaseMessagePart** interface.</span></span> <span data-ttu-id="6fc61-106">每個訊息部分已透過其資料的參考**IStream**介面指標。</span><span class="sxs-lookup"><span data-stu-id="6fc61-106">Each message part has a reference to its data through an **IStream** interface pointer.</span></span> <span data-ttu-id="6fc61-107">訊息的內容由其**IBaseMessageContext**介面。</span><span class="sxs-lookup"><span data-stu-id="6fc61-107">The context of a message is represented by its **IBaseMessageContext** interface.</span></span> <span data-ttu-id="6fc61-108">下圖說明 BizTalk 訊息物件模型。</span><span class="sxs-lookup"><span data-stu-id="6fc61-108">The following figure illustrates the BizTalk message object model.</span></span>  
  
 ![](../core/media/ibasemessagestructure.gif "IBaseMessageStructure")  
  
 <span data-ttu-id="6fc61-109">訊息內容是以屬性名稱與屬性命名空間的組合為索引鍵的字典。</span><span class="sxs-lookup"><span data-stu-id="6fc61-109">The message context is a dictionary that is keyed on a combination of the property name and the property namespace.</span></span> <span data-ttu-id="6fc61-110">這樣可以避免不同來源中名稱相似的屬性之間發生衝突，例如，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統屬性和自訂配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="6fc61-110">This prevents collisions between similarly named properties from different sources, for example, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system properties and custom adapter properties.</span></span> <span data-ttu-id="6fc61-111">這些屬性的值為.NET 型別的**物件**，但這些屬性實際上是變化。</span><span class="sxs-lookup"><span data-stu-id="6fc61-111">The values for these properties are of the .NET type **object**, but in fact these properties are VARIANTs.</span></span>  
  
 <span data-ttu-id="6fc61-112">每個部分都有同時也是字典的部分內容，但是沒有命名空間的概念。</span><span class="sxs-lookup"><span data-stu-id="6fc61-112">Each part has a part context that is also a dictionary but without the notion of a namespace.</span></span> <span data-ttu-id="6fc61-113">部分內容的值是用來參考該部分之資料的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6fc61-113">The value of a part context is metadata referring to the data for that part.</span></span> <span data-ttu-id="6fc61-114">舉例來說，這是**Charset**屬性，指定用來編碼訊息的字元集。</span><span class="sxs-lookup"><span data-stu-id="6fc61-114">An example of this is the **Charset** property that specifies the character set used for encoding the message.</span></span>  
  
 <span data-ttu-id="6fc61-115">您可以在訊息內容中寫入或讀取屬性，</span><span class="sxs-lookup"><span data-stu-id="6fc61-115">Properties may be written to and read from the message context.</span></span> <span data-ttu-id="6fc61-116">也可以將這些屬性升級到可用於訊息路由。</span><span class="sxs-lookup"><span data-stu-id="6fc61-116">They may also be promoted to be used for message routing.</span></span> <span data-ttu-id="6fc61-117">屬性得到升級，即表示可以將它們當做與訊息一起流動之中繼資料的一部分來寫入。</span><span class="sxs-lookup"><span data-stu-id="6fc61-117">Being promoted means they are written as a part of metadata that flows with the message.</span></span> <span data-ttu-id="6fc61-118">如果是升級屬性，您就可以在傳送埠和協調流程上使用其值來建立篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="6fc61-118">A promoted property allows its value to be used in the creation of filter expressions on send ports and orchestrations.</span></span> <span data-ttu-id="6fc61-119">協調流程中的下游元件和使用者程式碼可以讀取升級屬性，也可以將新值寫入其中。</span><span class="sxs-lookup"><span data-stu-id="6fc61-119">Downstream components and user code in orchestrations may read promoted properties and also write new values to them.</span></span>  
  
 <span data-ttu-id="6fc61-120">在升級屬性符合現有訂閱，並用於路由傳送訊息之後，便會降級該屬性以避免發生循環的訂閱相符情況。</span><span class="sxs-lookup"><span data-stu-id="6fc61-120">After a promoted property has been matched to an existing subscription and used to route a message, the property is demoted to prevent cyclic subscription matches.</span></span> <span data-ttu-id="6fc61-121">降級屬性將做為中繼資料保留在訊息內容裡，但會失去其升級狀態。</span><span class="sxs-lookup"><span data-stu-id="6fc61-121">A demoted property remains on the message context as metadata but loses its promoted status.</span></span>  
  
 <span data-ttu-id="6fc61-122">**實作秘訣：** 訊息內容屬性會在執行階段時載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="6fc61-122">**Implementation Tip:** Message context properties are loaded into memory at run time.</span></span> <span data-ttu-id="6fc61-123">您不應將非常大量的資料寫入訊息內容，因為這樣可能會中斷 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 大型訊息支援。</span><span class="sxs-lookup"><span data-stu-id="6fc61-123">Very large pieces of data should not be written to the message context because this could potentially break the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] large message support.</span></span> <span data-ttu-id="6fc61-124">物件可能會序列化至訊息內容提供這些物件實作**IPersistStream**介面。</span><span class="sxs-lookup"><span data-stu-id="6fc61-124">Objects may be serialized into the message context providing they implement the **IPersistStream** interface.</span></span> <span data-ttu-id="6fc61-125">此外，升級屬性還有 255 個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="6fc61-125">Also, promoted properties are limited to 255 characters.</span></span>  
  
 <span data-ttu-id="6fc61-126">您應該永遠使用訊息 Factory 來建立新訊息。</span><span class="sxs-lookup"><span data-stu-id="6fc61-126">The message factory should always be used to create new messages.</span></span>  <span data-ttu-id="6fc61-127">下列程式碼片斷說明如何從接收自配接器的資料流中建立新的 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="6fc61-127">The following code fragment illustrates how to create a new BizTalk message from the data stream received by the adapter.</span></span>  
  
```  
using Microsoft.BizTalk.Message.Interop;  
  
IBaseMessage CreateMessage( Stream s, IBaseMessageFactory msgFactory )  
{  
IBaseMessage msg = null;  
IBaseMessagePart part = msgFactory.CreateMessagePart();  
part.Data = s;  
msg = msgFactory.CreateMessage();  
msg.AddPart("body", part, true);  
return msg;  
}  
```