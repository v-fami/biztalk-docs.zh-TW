---
title: "如何使用 MessageBox 直接繫結連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1839184b-408e-4ac6-94a4-a0eb708183f6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fbe52d46847bdaa7caffbb4402ce8d380a73f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-messagebox-direct-bound-ports"></a><span data-ttu-id="e9055-102">如何使用 MessageBox 直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="e9055-102">How to Use MessageBox Direct Bound Ports</span></span>
<span data-ttu-id="e9055-103">MessageBox 直接繫結連接埠可讓您直接將訊息放入 MessageBox 資料庫，而不指定明確的收件者；以及訂閱符合特定準則的訊息，而非來自特定傳送者的訊息。</span><span class="sxs-lookup"><span data-stu-id="e9055-103">MessageBox direct bound ports enable you to drop messages directly into the MessageBox database without an explicit recipient, and to subscribe to messages that meet certain criteria rather than messages that come from a particular sender.</span></span>  
  
 <span data-ttu-id="e9055-104">在 MessageBox 直接繫結連接埠上傳送訊息，就等於將訊息發佈至訊息匯流排 (在本案例中，即 MessageBox 資料庫)。</span><span class="sxs-lookup"><span data-stu-id="e9055-104">Sending a message on a MessageBox direct bound port is equivalent to publishing the message to a message bus—in this case, to the MessageBox database.</span></span> <span data-ttu-id="e9055-105">任何發佈的訊息都可以有任意數目的訂閱者，如果發佈訊息當時沒有任何訂閱者對此訊息有興趣，將會擲回「找不到訂閱」例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9055-105">There can be any number of subscribers for any published message, and if there are no subscribers interested in the message at the time you publish it, a "subscription not found" exception will be thrown.</span></span> <span data-ttu-id="e9055-106">如果您透過 MessageBox 直接繫結連接埠將訊息傳送使用特定的收件者，請注意，您可能想要設定屬性，為特定值**訊息指派**您要尋找的預定訂閱者的圖形。</span><span class="sxs-lookup"><span data-stu-id="e9055-106">If you send a message through a MessageBox direct bound port with a particular recipient in mind, you may want to set properties to particular values in the **Message Assignment** shape for your intended subscriber to look for.</span></span> <span data-ttu-id="e9055-107">您可以根據 BizTalk Server 預先定義的屬性定義或自訂屬性定義來設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e9055-107">You can set the properties based on BizTalk Server predefined property definitions or on your own property definitions.</span></span> <span data-ttu-id="e9055-108">例如：</span><span class="sxs-lookup"><span data-stu-id="e9055-108">For example:</span></span>  
  
```  
myMessage(PropertyNamespace.PropertyName) = "My Property")  
```  
  
 <span data-ttu-id="e9055-109">透過 MessageBox 直接繫結連接埠接收訊息，相當於使用篩選準則來訂閱訊息匯流排。</span><span class="sxs-lookup"><span data-stu-id="e9055-109">Receiving a message through a MessageBox direct bound port is equivalent to subscribing to a message bus with filter criteria.</span></span> <span data-ttu-id="e9055-110">訊息的收件者可以是任何能訂閱訊息的服務類型，這包括協調流程和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e9055-110">Recipients of the message can be any type of service that can subscribe to messages, which includes orchestrations and send ports.</span></span> <span data-ttu-id="e9055-111">對於啟動**接收**圖形，訂閱是訊息類型和篩選運算式，以及非啟動**接收**圖形，訂閱是訊息類型和相互關聯集。</span><span class="sxs-lookup"><span data-stu-id="e9055-111">For an activating **Receive** shape the subscription is the message type and the filter expression, and for a non-activating **Receive** shape the subscription is the message type and the correlation set.</span></span> <span data-ttu-id="e9055-112">每個**接收**圖形永遠會包含訊息類型做為其訂用帳戶的一部分。</span><span class="sxs-lookup"><span data-stu-id="e9055-112">Every **Receive** shape always includes the message type as part of its subscription.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9055-113">您必須使用篩選條件運算式，如果您有一個啟動**接收**圖形接收訊息的型別**System.Xml.XmlDocument**或**Microsoft.XLANGs.BaseTypes.Any**直接繫結連接埠上與訂閱定義路由。</span><span class="sxs-lookup"><span data-stu-id="e9055-113">You must use a filter expression if you have an activating **Receive** shape receiving a message of type **System.Xml.XmlDocument** or **Microsoft.XLANGs.BaseTypes.Any** on a direct bound port with subscription-defined routing.</span></span>  
  
 <span data-ttu-id="e9055-114">如果您未指定任何篩選準則中啟用**接收**圖形連接至 MessageBox 直接繫結連接埠，則訂閱看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9055-114">If you did not specify any filter criteria in the activating **Receive** shape connected to a MessageBox direct bound port, then the subscription will look similar to the following:</span></span>  
  
```  
http://schemas.microsoft.com/BizTalk/2003/system-properties.ReceivePortID == {2F6A80E1-2518-4A69-9C28-401C2DB1CBF6} And  
http://schemas.microsoft.com/BizTalk/2003/system-properties.MessageType == http://MyMessageType  
```  
  
 <span data-ttu-id="e9055-115">在前述範例中，MessageBox 直接繫結接收埠將會接收符合為連接埠作業所設定之訊息類型的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="e9055-115">In the preceding example, the MessageBox direct bound receive port will receive every message that matches the message type that the port’s operation is configured for.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9055-116">使用 MessageBox 直接繫結接收埠時，您應該盡可能具體明確地設定篩選條件。</span><span class="sxs-lookup"><span data-stu-id="e9055-116">When using MessageBox direct bound receive ports, you should make the filter as specific as possible.</span></span> <span data-ttu-id="e9055-117">如果篩選條件設定得不夠明確，您的協調流程可能會收到不需要的訊息。</span><span class="sxs-lookup"><span data-stu-id="e9055-117">If you do not make the filter specific enough, your orchestration may receive unwanted messages.</span></span>  
  
 <span data-ttu-id="e9055-118">若要設定 MessageBox 直接繫結連接埠，請選取**將由 Messagebox 資料庫中的內送訊息的篩選條件運算式定義連接埠之間路由**中連接埠組態精靈。</span><span class="sxs-lookup"><span data-stu-id="e9055-118">To configure a MessageBox direct bound port, select **Routing between ports will be defined by filter expressions on incoming messages in the Message Box database** in the Port Configuration Wizard.</span></span>  
  
 <span data-ttu-id="e9055-119">如需如何使用 MessageBox 直接繫結連接埠的範例，請參閱 SDK 範例 「 直接繫結至 MessageBox 資料庫中協調流程 」 在[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="e9055-119">For an example of how to use MessageBox direct bound ports, see the SDK sample "Direct Binding to the MessageBox Database in Orchestrations" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9055-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9055-120">See Also</span></span>  
 <span data-ttu-id="e9055-121">[如何使用自我相互關聯直接繫結連接埠](../core/how-to-use-self-correlating-direct-bound-ports.md) </span><span class="sxs-lookup"><span data-stu-id="e9055-121">[How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md) </span></span>  
 [<span data-ttu-id="e9055-122">如何使用夥伴協調流程直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="e9055-122">How to Use Partner Orchestration Direct Bound Ports</span></span>](../core/how-to-use-partner-orchestration-direct-bound-ports.md)