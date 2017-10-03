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
# <a name="how-to-use-messagebox-direct-bound-ports"></a>如何使用 MessageBox 直接繫結連接埠
MessageBox 直接繫結連接埠可讓您直接將訊息放入 MessageBox 資料庫，而不指定明確的收件者；以及訂閱符合特定準則的訊息，而非來自特定傳送者的訊息。  
  
 在 MessageBox 直接繫結連接埠上傳送訊息，就等於將訊息發佈至訊息匯流排 (在本案例中，即 MessageBox 資料庫)。 任何發佈的訊息都可以有任意數目的訂閱者，如果發佈訊息當時沒有任何訂閱者對此訊息有興趣，將會擲回「找不到訂閱」例外狀況。 如果您透過 MessageBox 直接繫結連接埠將訊息傳送使用特定的收件者，請注意，您可能想要設定屬性，為特定值**訊息指派**您要尋找的預定訂閱者的圖形。 您可以根據 BizTalk Server 預先定義的屬性定義或自訂屬性定義來設定屬性。 例如：  
  
```  
myMessage(PropertyNamespace.PropertyName) = "My Property")  
```  
  
 透過 MessageBox 直接繫結連接埠接收訊息，相當於使用篩選準則來訂閱訊息匯流排。 訊息的收件者可以是任何能訂閱訊息的服務類型，這包括協調流程和傳送埠。 對於啟動**接收**圖形，訂閱是訊息類型和篩選運算式，以及非啟動**接收**圖形，訂閱是訊息類型和相互關聯集。 每個**接收**圖形永遠會包含訊息類型做為其訂用帳戶的一部分。  
  
> [!NOTE]
>  您必須使用篩選條件運算式，如果您有一個啟動**接收**圖形接收訊息的型別**System.Xml.XmlDocument**或**Microsoft.XLANGs.BaseTypes.Any**直接繫結連接埠上與訂閱定義路由。  
  
 如果您未指定任何篩選準則中啟用**接收**圖形連接至 MessageBox 直接繫結連接埠，則訂閱看起來如下所示：  
  
```  
http://schemas.microsoft.com/BizTalk/2003/system-properties.ReceivePortID == {2F6A80E1-2518-4A69-9C28-401C2DB1CBF6} And  
http://schemas.microsoft.com/BizTalk/2003/system-properties.MessageType == http://MyMessageType  
```  
  
 在前述範例中，MessageBox 直接繫結接收埠將會接收符合為連接埠作業所設定之訊息類型的所有訊息。  
  
> [!NOTE]
>  使用 MessageBox 直接繫結接收埠時，您應該盡可能具體明確地設定篩選條件。 如果篩選條件設定得不夠明確，您的協調流程可能會收到不需要的訊息。  
  
 若要設定 MessageBox 直接繫結連接埠，請選取**將由 Messagebox 資料庫中的內送訊息的篩選條件運算式定義連接埠之間路由**中連接埠組態精靈。  
  
 如需如何使用 MessageBox 直接繫結連接埠的範例，請參閱 SDK 範例 「 直接繫結至 MessageBox 資料庫中協調流程 」 在[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用自我相互關聯直接繫結連接埠](../core/how-to-use-self-correlating-direct-bound-ports.md)   
 [如何使用夥伴協調流程直接繫結連接埠](../core/how-to-use-partner-orchestration-direct-bound-ports.md)