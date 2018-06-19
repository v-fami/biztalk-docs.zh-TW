---
title: TIBCO Rendezvous 中的資料類型的傳送處理常式對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa1a9233-8781-45a8-9c55-a18ecaa0f456
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bda336d149d373477b26efeb2e4b05de4aac7554
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015237"
---
# <a name="data-type-mapping-for-send-handlers-in-tibco-rendezvous"></a>TIBCO Rendezvous 中的傳送處理常式資料型別對應
只有當 TIBCO Rendezvous 提供了型別資訊 (xsi:type=) 時，才能從 XML 結構描述型別對應至 TIBCO Rendezvous 型別。 任何 不支援的型別都會對應至字串 (如果可以的話)。 若無法進行對應，或傳送埠組態中已停用對應選項，即會產生錯誤。  
  
## <a name="xml-schema-to-tibco-rendezvous-data-type-mapping"></a>XML 結構描述至 TIBCO Rendezvous 資料型別的對應  
 下表顯示從 XML 結構描述型別至 TIBCO Rendezvous 型別的可能對應。  
  
|XML 型別|TIBCO RV 型別|  
|--------------|-------------------|  
||TIBRVMSG_MSG|  
||TIBRVMSG_XML|  
|xsd:dateTime|TIBRVMSG_DATETIME|  
|xsd:boolean|TIBRVMSG_BOOL|  
|xsd:byte|TIBRVMSG_I8|  
|xsd:short|TIBRVMSG_I16|  
|xsd:int|TIBRVMSG_I32|  
|xsd:long|TIBRVMSG_I64|  
|xsd:unsignedByte|TIBRVMSG_U8|  
|xsd:unsignedShort|TIBRVMSG_U16|  
|xsd:unsignedInt|TIBRVMSG_U32|  
|xsd:unsignedLong|TIBRVMSG_U64|  
|xsd:float|TIBRVMSG_F32|  
|xsd:double|TIBRVMSG_F64|  
|tibrv:IPaddress|TIBRVMSG_IPADDR32|  
|tibrv:IPport|TIBRVMSG_IPPORT16|  
|tibrv:arrayOfByte|TIBRVMSG_I8ARRAY|  
|tibrv:arrayOfShort|TIBRVMSG_I16ARRAY|  
|tibrv:arrayOfInt|TIBRVMSG_I32ARRAY|  
|tibrv:arrayOfLong|TIBRVMSG_I64ARRAY|  
|tibrv:arrayOfUnsignedByte|TIBRVMSG_U8ARRAY|  
|tibrv:arrayOfUnsignedShort|TIBRVMSG_U16ARRAY|  
|tibrv:arrayOfUnsignedInt|TIBRVMSG_U32ARRAY|  
|tibrv:arrayOfUnsignedLong|TIBRVMSG_U64ARRAY|  
|tibrv:arrayOfFloat|TIBRVMSG_F32ARRAY|  
|tibrv:arrayOfDouble|TIBRVMSG_F64ARRAY|  
|任何其他型別 - 會有偵錯訊息|TIBRVMSG_STRING 記錄檔。|  
  
 因為 BizTalk Adapter for TIBCO Rendezvous 無權存取結構描述，所以當您從 BizTalk Server 傳輸至 TIBCO Rendezvous 時，必須為任何非字串欄位提供 XML `xsi:type` 屬性。 此配接器會使用該資訊在 TIBCO Rendezvous 訊息中產生適當的訊息欄位型別。  
  
## <a name="message-mapping-example"></a>訊息對應 範例  
 下列範例會示範將訊息從 BizTalk Server 對應到 TIBCO Rendezvous。 如需瞭解型別對應的方式，請參閱資料型別對應表中的資訊。  
  
```  
<ns:QuoteUpdate xmlns:xsi http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd http://www.w3.org/2001/XMLSchema"  
xmlns:tibrv="http://schemas.microsoft.com/TibcoRendezvous/Types"  
xmlns:ns="some namespace for this message [value not important, unless the schema is also used for receive ports]">  
  
<ns:SymbolName id=1 xsi:type="xsd:string">MSFT</ns:SymbolName>  
  
<ns:LastTrade id=2 xsi:type="xsd:double">28.40</ns:LastTrade>   
<ns:DayLow id=3 xsi:type="xsd:double">28.25</ns:DayLow>  
  
```  
  
|||  
|-|-|  
|`<ns:DayHigh`|`id=4 xsi:type="xsd:double">28.40</ns:DayHigh>`|  
|`<ns:MarketCap`|`id=10>262575234981</ns:MarketCap>`|  
|`<ns:Bids`|`id=100 xsi:type="tibrv:message">`|  
  
```  
<ns:TopBids id=1 xsi:type="tibrv:arrayOfDouble">  
<item>28.40</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.38</item>  
  
</ns:TopBids>  
  
<ns:BidsSize id=2 xsi:type="tibrv:arrayOfLong">  
<item>500</item>  
<item>1000</item>  
<item>100</item>  
<item>100</item>  
<item>2000</item>  
  
</ns:BidsSize>  
</ns:Bids>  
</ns:QuoteUpdate>  
  
```  
  
 先前的訊息在產生為結構化的 TIBCO Rendezvous 訊息之後，即會成為含有六個欄位的最上層 TibcoMsg 執行個體。 最後一個欄位是子訊息，由兩個陣列型別的欄位所組成 ('item' 項目不會對應至 TIBCO Rendezvous 訊息欄位，而是對應至 `array` 型別之訊息欄位中的項目)。 MarketCap 欄位沒有型別規格，會當成字串訊息欄位來傳送。  
  
## <a name="see-also"></a>另請參閱  
 [建立 TIBCO Rendezvous 傳送處理常式](../core/creating-tibco-rendezvous-send-handlers.md)