---
title: 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, headers
- messages, acknowledgements
- messages, persisting
- messages
- examples, message headers
- properties
- message headers
- EMS messages
ms.assetid: 65bb3431-7186-4d4c-b004-932cdf070e73
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f7313e93029ca75d345aa4e9603699c50399230
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266686"
---
# <a name="messages"></a>訊息
類似 JMS 訊息的 Enterprise Message Service (EMS) 訊息，其中包含了三個不同部分：標頭、屬性和內文。 標頭是 EMS 訊息唯一要求指定的部分。 本主題會描述訊息中的處理方式 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service。  
  
> [!NOTE]
>  若要設定或擷取標頭欄位 （例如，設定訊息優先順序 」 或是 「 相互關聯識別碼） 或從協調流程的訊息屬性，您必須加入參考**Microsoft.BizTalk.Adapters.TIBCOEMSProperties.dll**中您使用方案總管 中的專案。  
  
## <a name="message-header"></a>訊息標頭  
 訊息標頭包含一連串含值的預先定義欄位。 BizTalk Adapter for TIBCO Enterprise Message Service 知道標題中可設定和不可設定的項目。 若您嘗試設定唯讀值，配接器就會將您的設定值重新導向或設定到 Properties{} 區段中。  
  
### <a name="header-example"></a>標頭範例  
 在下列範例中，注意**屬性 = {目的地 = {String: Queue [Q2]}}**。 `Properties`是包含字串屬性，字串內容是**Q2**。 這個屬性與 Destination 區段完全無關，因為它包含的是哪兒也不去的字串值 (您所設定的值)，所以配接器會將這些字串保存在這個區段內。  
  
 `ReplyTo` 屬性可以設定於協調流程，以便告知最終取用者要將回應送往何處。 當訊息接收自 TIBCOEMS 時，EMS 會設定 `Destination` 屬性。 在訊息為接收自 TIBCOEMS 的協調流程中，這個第二個屬性具有唯讀性質，因此無法在協調流程中加以編輯。  
  
 例如，協調流程無法動態地分派協調流程內的訊息和設定訊息目的地。 Destination 的值會依據將傳送該訊息的連接埠而設定。  
  
 若您要將訊息分派到不同的佇列，您就必須針對個別佇列建立傳送埠。 這樣一來，協調流程就可以決定將哪個連接埠指派給該訊息。  
  
 在下面這個訊息範例中，Destination= `{Queue[Q1]}` 具唯讀性質。 這個值是 TIBCOEMS 在伺服器接收訊息時設定的。 Destination 和 Q1 的值來自「傳輸屬性」。  
  
#### <a name="example"></a>範例  
  
```  
TextMessage={   
    Header={ MessageID={ID:EMS-SERVER.824437A58B11C75F4:1}   
    Destination={Queue[Q1]}   
  
        ' This is READONLY. It gets set by the server when the  
        ' message is received by the server (EMS). It is set in the  
        ' Transport Properties when you specify that you want to  
        ' listen for messages on Q1.  
    ReplyTo={}   
    DeliveryMode={Persistent}   
    Redelivered={False}   
    CorrelationID={}   
    MsgType={}   
    Timestamp={12/1/2005 11:59:01 PM}   
    Expiration={0}   
    Priority={1} }   
    Properties={ Destination={String:Queue[Q2]} }   
  
        ' This is a property that contains a string, and the   
        ' contents of the string is Q2. This has nothing to do with  
        ' the Destination section above – it is just another   
        ' property that is set.   
        ' This is in the schema. The adapter knows what it can and   
        ' cannot set in an EMS header. The values that the adapter   
        ' cannot set are put in the Properties section.   
    text={<?xml version="1.0" encoding="utf-16"?>  
    <ns0:Employees xmlns:ns0="http://BizTalk_Server_Project1.Employee">  
        <Emp Id="Id_0">  
            Name>Name_0</Name>  
        </Emp>  
    </ns0:Employees>  
    }  
```  
  
 標頭內含的一連串預先定義欄位，包含了配接器會升級到 BizTalk Server 訊息以便用於協調流程的值。 所升級屬性在標準標頭屬性中的定義，與 JMS 規格和 TIBCO Enterprise Message Service 延伸所下的定義，完全相同。 訊息是接收自 EMS 的協調流程可以使用所有屬性，但是 `Destination` 和 `ReplyTo` 除外，這兩個屬性描述的是無法正確對應以作為協調流程中單一屬性使用的目的地。  
  
 BizTalk Adapter for TIBCO EMS 會將 TIBCOEMS 屬性對應成字串型別，並且使用 Destination 字串表示法。 這個字串看起來像是 `StaticQueue[queuename]` 或 `StatisTopic[topicname]`。 協調流程可以設定 `ReplyTo` 的值，而配接器會用標頭中的有效目的地物件來取代該值。  
  
 配接器會提供結構描述和參考組件，這兩者會描述可供協調流程使用的任何 TIBCO EMS 標頭屬性。 這些屬性可用於篩選內送訊息，或是加入到外寄訊息。 掌控協調流程篩選條件的規則，不同於 EMS 伺服器訊息選取器所使用的規則。 例如，協調流程可以就 `TibcoEMS.ReplyTo` 或 `TibcoEMS.Destination` 屬性進行篩選，但是 JMS 規格並未提供任何讓訊息選取器就此相同屬性進行篩選的支援。  
  
 當協調流程有設定這些屬性時，JMS 訊息的標頭屬性中就會包含這些屬性。 否則，當 EMS 訊息獲得接收時，這些標頭屬性就會複製到 BizTalk Server 訊息內容中。  
  
 當某個屬性與連接埠組態相符時，在訊息上之該屬性值的優先順序便會高於該連接埠組態。 例如，如果連接埠內所設定的優先順序為 4，而您在協調流程邏輯中是將訊息的優先順序設成 9，則此訊息會依據優先順序 9 來由 TIBCO EMS 接收。  
  
### <a name="property-descriptions"></a>屬性描述  
 下表描述 BizTalk Adapter for TIBCO Enterprise Message Service 如何使用各個屬性。  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|TibcoEMS.MessageID|string|傳送呼叫，可為各個訊息指派唯一識別碼，並將此識別碼記錄在標頭中。<br /><br /> 任何訊息識別碼值的開頭都是 3 個字元組成的前置識別碼 (已就這個用途而保留)。<br /><br /> 唯讀。 變更這個值並不會影響訊息。|  
|TibcoEMS.Timestamp|long|傳送呼叫，可在標頭中記錄 UTC 時間戳記。 這個時間戳記會指出伺服器接受訊息的大致估計時間。<br /><br /> 這個值是自 1970 年 1 月 1 日以來所經過的毫秒數。<br /><br /> 唯讀。 變更這個值並不會影響訊息。|  
|TibcoEMS.Redelivered|boolean|伺服器會將標頭設定成指出某個訊息是否與先前所傳送的訊息重複：<br /><br /> -false-伺服器尚未先前嘗試將這個訊息傳送給取用者。<br />-為 true，它是可能的但不是保證，伺服器先前已嘗試將此訊息傳送給取用者，但取用者未傳回具時效性的應答。<br /><br /> 唯讀。 變更這個值並不會影響訊息。|  
|TibcoEMS.Destination|string|傳送呼叫，可在這個標頭中記錄此訊息的目的地 (佇列或主題)。 格式會從目的地改成字串表示法。 格式已於先前內容中介紹過。<br /><br /> 唯讀。 變更這個值並不會影響訊息。|  
|TibcoEMS.DeliveryMode|string|有兩個可能的值： 持續性和非持續性。 預設值為 PERSISTENT 模式。<br /><br /> 配接器會先等候來自 EMS 伺服器的通知，接著才發出訊息已傳送到 BizTalk Server 的通知。 這個標頭屬性和連接埠組態項目會決定 EMS 將這個通知傳送給配接器時所花費的時間，並決定訊息傳輸的穩定性。<br /><br /> 使用 PERSISTENT 傳遞模式 -- EMS 伺服器會一直等候到訊息成功保存於 EMS 伺服器中。 這個動作可保證該訊息有送達佇列。 使用 PERSISTENT 模式傳遞時，請注意下列幾點：<br /><br /> 訊息越大，BizTalk Server 就會花更多時間來判定該訊息為已傳送。<br /><br /> 使用 NON-PERSISTENT 模式 -- EMS 伺服器會先傳回通知，再保存該訊息。 如果 EMS 伺服器發生失敗，在系統判定 BizTalk Server 已成功傳送該訊息之際，訊息可能已經遺失了。|  
|TibcoEMS.Expiration|long|訊息在過期前維持有效的時間長度。 如果設成 0，表示訊息永遠不會過期。<br /><br /> 此段有效時間的指定單位是毫秒。|  
|TibcoEMS.Priority|int|使用從 0 到 9 的數字排名，定義訊息的優先順序為一般或是加速。 數字越大表示優先順序越前面。|  
|TibcoEMS.CorrolationID|string|可以用來連結訊息，例如將回應訊息連結到要求訊息。<br /><br /> 這個屬性值通常就是 `EMS.JMSMessageID`。 這個屬性通常與 `EMS.JMSReplyTo` 屬性搭配使用。|  
|TibcoEMS.ReplyTo|string|訊息回覆時應該送至其中的目的地。 格式和連接埠組態與 `EMS.JMSDestination` 的設定相同。|  
|TibcoEMS.Type|string|不描述訊息類型 (文字、位元組、字串…)。<br /><br /> 有些 JMS 提供者會使用訊息儲存機制來存放訊息類型定義。 用戶端程式可在這個欄位中，存放可參考至該儲存機制內定義的值。 EMS 支援這個標頭，但是並不會使用它。<br /><br /> JMS 規格不會定義標準的訊息定義儲存機制，也不會定義訊息類型定義的命名原則。<br /><br /> 有些提供者需要使用各個應用程式訊息的訊息類型定義。 為了保證與這類提供者維持相容性，用戶端程式可以設定這個標頭，即使該用戶端應用程式並不會使用該標頭。<br /><br /> 為了保證可攜性，用戶端可以用符號值 (而不要用常值) 來設定這個標頭，並將標頭設定成與提供者的儲存機制相符。|  
  
## <a name="properties"></a>屬性  
 整合者可以定義要升級到 BizTalk Server 訊息內容的一組屬性，等到升級過後，這些屬性就會加入到 JMS 訊息的屬性部分。 整合者會在建立結構描述的同時，注意何時要定義該屬性的類型。 如果這個屬性值將用於訊息選取器，這個屬性的型別將會決定特定作業是否可有效執行。 例如，如果訊息選取器**myMessageProperty > 5**是使用，必須將屬性定義為整數值，而且配接器會將該值放成為整數值的訊息中。 對於要升級的屬性，屬性名稱的開頭必須是 EMSX， 而且屬性名稱不能和預先定義的屬性相同。  
  
 BizTalk Adapter for TIBCO Enterprise Message Service 會提供結構描述和組件，這兩者會宣告可能出現在這個區段中的 EMS 專屬和 JMS 專屬屬性。 這些屬性可予以增加以包含任何遺漏。 在此訊息內容中加以參考的任何 EMSX 屬性，都會放入該 EMS 訊息的訊息屬性區段。 如需詳細資訊，請參閱《TIBCO EMS 使用者指南》。  
  
## <a name="body"></a>本文  
 EMS 支援列舉於 JMS 規格中的所有訊息： 文字、 位元組、 資料流、 對應和物件。 BizTalk Adapter for TIBCO EMS 支援文字訊息類型。  
  
 JMS 不要求文字訊息類型一定要包含 XML 格式的內文。 配接器不會處理訊息; 本文提供給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收。  因此，配接器提交至 BizTalk 訊息可能並不一定剖析為 XML 資料。  
  
## <a name="persistent-messages"></a>保存的訊息  
 訊息可以保存在 EMS 伺服器上來保證完整一次傳遞給訂閱者，但是，這種作法可能會嚴重影響到配接器的效能。 當您傳送訊息時，EMS 會先將訊息存放在本機儲存區，再向配接器發出已接收訊息的通知。 您可以在協調流程中針對各個訊息來設定這個屬性，或是針對連接埠所處理的任何訊息設定這個屬性。  
  
 就接收的角度來說，配接器可能會在主題沒有訂閱訊息情況下遺漏掉某些訊息。 當 EMS 沒有保存任何訂閱時，訊息就會張貼到主題上。 配接器需要某種機制，接收訊息張貼即使目前未訂閱;不過，像使用的持續性的訊息，這會對 EMS 效能，具有顯著的影響，它不一定需要。  
  
> [!NOTE]
>  還有一種從 EMS 檢視位置進行接收的機制，不過這種機制尚未實作，也沒有實際的需要。 這個問題只和主題有關，而不會影響到佇列。 主題通常是用於時間特定資料，例如，股票報價。 當股票價格漏掉時，您知道稍後它就會補貼出來。  
  
 基於這些因素，您可以選擇為連接埠組態啟用或停用將訊息保存在 EMS 伺服器上。  
  
## <a name="message-acknowledgement"></a>訊息應答  
 BizTalk Adapter for TIBCO Enterprise Message Service 一定會在訊息已正確分派給 BizTalk Server 時應答已接收訊息。 這樣表示，沒有應答的訊息會從 EMS 重新傳送給配接器。 配接器無法決定 EMS 重新傳送訊息的次數，因為這是目的地本身的組態設定；但是，配接器可以決定該訊息是否要傳送到 MessageBox。 EMS 伺服器會決定失敗訊息傳送到佇列的最多次數。  
  
 對於重新傳遞的訊息，EMS 伺服器會將 `JMSRedelivered` 屬性設為 True，而且會遞增 `JMSXDeliveryCount`。 這兩種屬性值都可用於協調流程。 您不能在訊息還未傳遞之前就將它移到 EMS 未傳遞佇列。 這樣做會改變訊息的屬性。  
  
 當訊息到達其已設定的最大重新傳遞計數時，EMS 伺服器就會判斷該訊息應該要加以刪除，或是放入 $sys.undelivered 佇列。 EMS 伺服器會根據 `JMS_TIBCO_PRESERVE_UNDELIVERED` 屬性來做出決定；如果是 True，訊息就會前往未傳遞佇列，否則就會加以刪除。 這個屬性可以先設定於協調流程中，接著才傳送該訊息。 傳遞之後，訊息屬性就不能變更。 系統會在傳送到 EMS 的訊息成功抵達時應答 BizTalk Server。 如果對 EMS 的傳送發生失敗，這些訊息會擱置，並標記為可再嘗試。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)