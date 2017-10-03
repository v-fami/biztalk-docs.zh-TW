---
title: "處理訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing
- messages, pipelines
- routing, about routing
- adapters, about adapters
- routing, message types
- processing, messages
- messages, processing
- routing
- messages, routing
- pipelines, about pipelines
- message types
- messages, message types
- messages, adapters
ms.assetid: e6d1f969-20c9-41f6-85cb-46cf92656348
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 829fffc773bfc19100ad03448baf68b5846996f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-the-message"></a>處理訊息
到目前為止所描述的所有元件，都會負責在訊息流過 BizTalk Server 時處理訊息。 本節提供這些元件從接收訊息開始，在功能上如何互動的詳細資料。 下圖說明接收埠的組成方式，以及透過接收程序的訊息流程。  
  
 *接收埠* 包含一或多個接收位置，以及零或多個對應。 對應是「可延伸樣式表語言轉換」(XSLT) 樣式表，用來將 XML 訊息從一個結構或格式轉換成另一個，並且經常用於接收程序中，以便將訊息正規化為內部格式。 接收位置會控制接收訊息的結束點。 接收位置包含接收配接器和接收管線之結束點的組態。  
  
 ![接收埠結構和處理](../core/media/arch-message-processing.gif "arch_message_processing")  
  
## <a name="the-role-of-the-adapter"></a>配接器的角色  
 接收配接器藉由讀取資料流和建立訊息，來初始化接收訊息的程序。 例如，檔案配接器會查看已放置於其設定位置中的檔案，並於資料流中讀取該檔案。 配接器會建立一個訊息 (Microsoft.BizTalk.Message.Interop.IBaseMessage 介面的實作)、新增一部分到其中 (Microsoft.BizTalk.Message.Interop.IBasePart 介面的實作)，並提供資料流做為部分內容。  
  
 此外，配接器會寫入並升級到與位置、配接器類型及與配接器相關之其他資訊相關的訊息內容屬性。 在訊息與其內容建立之後，配接器會將訊息傳遞到「結束點管理員」。 接著會透過已針對接收位置設定的接收管線來處理訊息。 管線處理訊息之後，可以在「結束點管理員」使用「訊息代理程式」發佈訊息之前，先使用對應將訊息轉換成所需的格式。  
  
## <a name="the-role-of-the-pipeline"></a>管線的角色  
 雖然這是建立初始訊息的配接器，但在已接收之訊息上進行的大部分處理，都是發生在接收管線中。 管線會處理訊息內文及訊息內容。 訊息內文 (Message Content) 一般會在解碼、解譯和驗證階段中處理，而訊息內容 (Message Context) 則可以在所有階段中處理。 不過，管線不一定會在內文或內容中發揮作用。 例如，預設的通過管線沒有設定任何元件，且不會在訊息內文或內容上執行任何處理。 為了簡化起見，本文件會著重於解譯元件，因為它們通常對於訊息路由會有最大的影響。  
  
 *解譯器* 的工作是處理來自配接器的內送訊息，並將訊息解譯成許多訊息，並剖析訊息資料。 當內送訊息擁有很多較小的訊息時，這就是所謂的 *交換*。 一般檔案解譯器和 XML 解譯器處理交換，讓開發人員設定 （也就是標頭和結尾一般檔案解譯器結構描述和信封結構描述之 XML 的換行內容的相關資訊解譯器） 和 （可能會重複） 的本文內容。 此外，這些解譯器都會將原始訊息剖析為 XML 內容。 若不需要在 BizTalk Server 中進一步處理 XML，自訂解譯器不一定要將內容剖析為 XML。 範例實例可能包括一個簡單路由狀況，也就是在特定接收位置進入系統的訊息，會傳送到沒有對應或其他以 XML 為基礎之處理的特定傳送埠。  
  
## <a name="routing-with-the-message-type"></a>具有訊息類型的路由  
 路由中所用的最常見訊息屬性之一是訊息類型。 當開發人員建立結構描述來定義訊息結構時，這個結構描述會定義該訊息的訊息類型。 類型是由根節點和命名空間在結構描述定義中所決定。 例如，如下所示的 XML 文件將擁有 http://tempuri.org/samples/MessageType#Message 的訊息類型  
  
```  
<Message xmlns=http://tempuri.org/samples/MessageType>  
<SomeOtherElement type="sample"/>  
</Message>  
```  
  
 若要在路由中使用訊息類型，它必須升級到內容中。 解譯器是用來將這個值升級到訊息內容，以及具有訊息結構最適用資訊的管線元件。 XML 和一般檔案解譯器在處理訊息時會升級訊息類型，而所有的自訂解譯器也應該升級這個屬性，以確保正確的路由。  
  
 請務必注意，訊息不一定要有一個類型。 如先前所提及，訊息的部分可以是任何的二進位資料，而且不需要有定義其結構的結構描述。 這類型的訊息部分一般會通過 BizTalk Server 而不會讓 BizTalk Server 本身進行太多 (如果有的話) 處理，雖然自訂管線元件、配接器或從協調流程呼叫的程式碼可能會與這些部分互動。  
  
 配接器這類的管線元件也會寫入並升級屬性為訊息內容。 事實上，管線元件是大部分開發人員最常用來將屬性放入訊息內容的機制。 開發人員會建立結構描述，並可在結構描述中升級屬性。 這個資訊會儲存在結構描述中做為註解，屆時可供管線元件使用。 所有內建解譯器和組合器元件 (FlatFile、XML 和 BizTalk Framework)，都會使用文件結構描述，來擷取即將升級之屬性的相關資訊。 使用註解中的 XML 路徑語言 (XPath) 陳述式，解譯器即可知道要升級之項目文件的位置。 在處理透過文件的資料流期間，解譯器會尋找符合其中一個 XPath 陳述式的這些項目，然後在適當的時候將這個值升級或寫入內容。  
  
 自訂管線元件，則也可以寫入處理已接收或傳送的訊息中的任意資料的內容取得的屬性。 為了將屬性升級到內容，並讓它用於路由 (這可能是要將值升級的原因)，應該建立具有屬性定義的屬性結構描述，並部署到 BizTalk Server。 在您定義屬性結構描述以用於自訂元件之前，應該先瞭解不同類型的升級屬性。 在屬性結構描述中定義的升級屬性可以有下列其中一種基底類型：  
  
-   [Microsoft.XLANGs.BaseTypes.MessageContextPropertyBase](http://msdn.microsoft.com/library/microsoft.xlangs.basetypes.messagecontextpropertybase.aspx) 或  
  
-   [Microsoft.XLANGs.BaseTypes.MessageDataPropertyBase](http://msdn.microsoft.com/library/microsoft.xlangs.basetypes.messagedatapropertybase.messagedatapropertybase.aspx)  
  
 具有基底類型 MessageDataPropertyBase 的屬性表示這個屬性的值來自訊息內容。 這是在屬性結構描述中定義的屬性預設值，並且是最常見的用法。 MessageContextPropertyBase 表示屬性是用來做為訊息內容的一部分，但不一定是直接來自訊息資料。 具有 MessageContextPropertyBase 做為其基底類型的屬性經常是由配接器和解譯器所升級，並包含訊息類型和配接器類型這類的通用屬性。  
  
 瞭解不同類型，並在定義屬性時適當地加以使用，是非常重要的。 一個最為明顯的暗示會發生於在協調流程中存取訊息的內容屬性時。 若屬性識別為 MessageDataPropertyBase，「協調流程設計師」會檢查正在接收之訊息的結構描述，並確保它會定義符合的升級屬性。 若結構描述中找不到繫結至要存取之升級屬性的屬性，那麼「設計師」將不允許您進行存取。 另一方面，若屬性是定義為 MessageContextPropertyBase，訊息類型就不重要，而屬性便可存取。  
  
 在自訂管線中，將屬性升級或寫入到內容的機制是非常相似的。 對於寫入屬性，您可以使用 IBaseMessageContext Write 方法的呼叫，將值放入內容中。 對於升級屬性，您只需改用 IBaseMessageContext Promote 方法即可。 這些方法的每一個都會採用一個屬性名稱、命名空間及值。 對於升級屬性，名稱與命名空間是在屬性結構描述中定義的那些屬性，藉由參考屬性結構描述組件，並使用針對該屬性所建立之類別上的屬性，就能夠以最輕鬆的方式來存取。 辨別欄位會使用通用的命名空間 http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields，而用來擷取值的 XPath 運算式通常會當做名稱來使用。  
  
 下列程式碼顯示升級屬性並將其寫入內容的範例。 請注意，在這個範例中，識別欄位正在寫入內容中。 這只對訊息結構描述識別辨別欄位的協調流程有用，如此一來「協調流程設計師」就會知道這個欄位。 將屬性寫入內容，以供其他管線元件在接收與傳送端使用，可能會很有用。  
  
```  
//create an instance of the property to be promoted  
SOAP.MethodName methodName = new SOAP.MethodName();  
  
//call the promote method on the context using the property class for name   
//and namespace  
pInMsg.Context.Promote(methodName.Name.Name, methodName.Name.Namespace,   
"theSOAPMethodName");  
  
//write a distinguished field to the context  
pInMsg.Context.Write("theDistinguishedProperty",   
"http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields",   
"theDistinguishedValue");  
```  
  
 在寫入或升級值到內容時，請務必記住下列事項：  
  
-   將值寫入具有先前用來升級屬性之相同名稱與命名空間的內容，會導致該屬性不再被升級。 寫入基本上會覆寫升級。  
  
-   將空值寫入內容會刪除值，因為空值屬性是不被允許的。  
  
-   升級屬性的長度有 256 個字元的限制，但是寫入屬性並無長度限制。  
  
 升級屬性是用於訊息路由中，且基於比較與儲存效率的原因，所以在大小上會有所限制。 雖然寫入屬性在大小上並無嚴格限制，在內容中使用過大的值會影響效能，因為這些值仍會被處理並與訊息一起傳遞。  
  
 當訊息已經可以從 BizTalk Server 傳送時，它會在傳送埠中進行互補程序。 在執行傳送管線之前，對應已先套用至訊息，讓訊息在管線處理並透過配接器傳送以前，可以先轉換為客戶或應用程式專用的格式。 在傳送管線中，屬性會從內容降級為訊息，以取代將屬性升級為訊息內容。  
  
 ![傳送埠和傳送管線處理程序](../core/media/arch-message-processing-2.gif "arch_message_processing 2")  
  
## <a name="see-also"></a>另請參閱  
 [執行階段架構](../core/runtime-architecture.md)   
 [BizTalk Server 如何處理大型訊息](../core/how-biztalk-server-processes-large-messages.md)