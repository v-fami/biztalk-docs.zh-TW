---
title: "IBaseMessage 介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10bfb95c-aef5-46ba-ba0e-9961833f27a3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7de478b27105ee6c01d582aa9b728bd0496d0487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ibasemessage-interface"></a>IBaseMessage 介面
當接收配接器接受連入的資料封包，透過其通訊協定時，它會使用**IBaseMessage**介面來建立要傳遞給傳訊引擎的訊息。 所有訊息都是使用此介面來代表。  
  
 訊息會有一或多個訊息部分由**IBaseMessagePart**介面。 每個訊息部分已透過其資料的參考**IStream**介面指標。 訊息的內容由其**IBaseMessageContext**介面。 下圖說明 BizTalk 訊息物件模型。  
  
 ![](../core/media/ibasemessagestructure.gif "IBaseMessageStructure")  
  
 訊息內容是以屬性名稱與屬性命名空間的組合為索引鍵的字典。 這樣可以避免不同來源中名稱相似的屬性之間發生衝突，例如，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統屬性和自訂配接器屬性。 這些屬性的值為.NET 型別的**物件**，但這些屬性實際上是變化。  
  
 每個部分都有同時也是字典的部分內容，但是沒有命名空間的概念。 部分內容的值是用來參考該部分之資料的中繼資料。 舉例來說，這是**Charset**屬性，指定用來編碼訊息的字元集。  
  
 您可以在訊息內容中寫入或讀取屬性， 也可以將這些屬性升級到可用於訊息路由。 屬性得到升級，即表示可以將它們當做與訊息一起流動之中繼資料的一部分來寫入。 如果是升級屬性，您就可以在傳送埠和協調流程上使用其值來建立篩選條件運算式。 協調流程中的下游元件和使用者程式碼可以讀取升級屬性，也可以將新值寫入其中。  
  
 在升級屬性符合現有訂閱，並用於路由傳送訊息之後，便會降級該屬性以避免發生循環的訂閱相符情況。 降級屬性將做為中繼資料保留在訊息內容裡，但會失去其升級狀態。  
  
 **實作秘訣：**訊息內容屬性會在執行階段時載入記憶體。 您不應將非常大量的資料寫入訊息內容，因為這樣可能會中斷 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 大型訊息支援。 物件可能會序列化至訊息內容提供這些物件實作**IPersistStream**介面。 此外，升級屬性還有 255 個字元的限制。  
  
 您應該永遠使用訊息 Factory 來建立新訊息。  下列程式碼片斷說明如何從接收自配接器的資料流中建立新的 BizTalk 訊息。  
  
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