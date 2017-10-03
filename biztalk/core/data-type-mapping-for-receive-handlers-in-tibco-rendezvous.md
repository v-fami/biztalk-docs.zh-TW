---
title: "資料類型對應在 TIBCO Rendezvous 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data type mapping
- array types
- receive handlers, data type mapping
ms.assetid: 36908a94-3c0d-466e-aa49-f674ba4a26af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8729a94fdcfc43ca17e498b10784cc163307badc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-mapping-for-receive-handlers-in-tibco-rendezvous"></a>TIBCO Rendezvous 中的接收處理常式資料型別對應
Microsoft BizTalk Adapter for TIBCO Rendezvous 會將 TIBCO RV 類型對應至如下表所指定的 XML 結構描述類型中。  
  
## <a name="tibco-rv-to-xml-data-type-mapping"></a>TIBCO RV 與 XML 資料類型的對應  
  
|TIBCO RV 型別|XML 結構描述類型|註解|  
|-------------------|---------------------|--------------|  
|TIBRVMSG_MSG|tibrv:message|從整個訊息所建構的完整 XML 文件。|  
|TIBRVMSG_XML|tibrv:rawxml|從位元組陣列建構的 XML 文件 (未經過配接器解譯)。|  
|TIBRVMSG_DATETIME|xsd:dateTime|配接器會使用 System.Xml.XmlConvert 類別，以在 XML 結構描述 `dateTime` 與 `System.DateTime` 執行個體之間轉換。|  
|TIBRVMSG_OPAQUE|xsd:base64Binary||  
|TIBRVMSG_STRING|xsd:string||  
|TIBRVMSG_BOOL|xsd:boolean||  
|TIBRVMSG_I8|xsd:byte||  
|TIBRVMSG_I16|xsd:short||  
|TIBRVMSG_I32|xsd:int||  
|TIBRVMSG_I64|xsd:long||  
|TIBRVMSG_U8|xsd:unsignedByte||  
|TIBRVMSG_U16|xsd:unsignedShort||  
|TIBRVMSG_U32|xsd:unsignedInt||  
|TIBRVMSG_U64|xsd:unsignedLong||  
|TIBRVMSG_F32|xsd:float||  
|TIBRVMSG_F64|xsd:double||  
|TIBRVMSG_IPADDR32|tibrv:IPaddress|`System.Net.IPAddress.ToString( )` 用於產生輸出。 內容以網路位元組順序排序。 由 ToString() 負責處理。|  
|TIBRVMSG_IPPORT16|tibrv:IPport|內容以網路位元組順序排序|  
|TIBRVMSG_I8ARRAY|tibrv:arrayOfByte|'tibrv' 結構描述命名空間會隨配接器一起提供。|  
|TIBRVMSG_I16ARRAY|tibrv:arrayOfShort||  
|TIBRVMSG_I32ARRAY|tibrv:arrayOfInt||  
|TIBRVMSG_I64ARRAY|tibrv:arrayOfLong||  
|TIBRVMSG_U8ARRAY|tibrv:arrayOfUnsignedByte||  
|TIBRVMSG_U16ARRAY|tibrv:arrayOfUnsignedShort||  
|TIBRVMSG_U32ARRAY|tibrv:arrayOfUnsignedInt||  
|TIBRVMSG_U64ARRAY|tibrv:arrayOfUnsignedLong||  
|TIBRVMSG_F32ARRAY|tibrv:arrayOfFloat||  
|TIBRVMSG_F64ARRAY|tibrv:arrayOfDouble||  
  
 TIBCO Rendezvous 陣列與名稱相同的一系列欄位不同。 例如，在 TIBCO Rendezvous 訊息中，含有 70,000 個元素的陣列有效，但含有 70,000 個欄位的陣列則無效。  
  
 以上表格中的陣列類型結構描述看起來與下列內容類似：  
  
```  
…  
<xsd:complexType name='arrayOfShort'>  
<xsd:sequence>  
<xsd:element name="item" type="xsd:short"/>  
</xsd:sequence>  
</xsd:complexType>  
  
```  
  
 訊息中的陣列元素看起來與下列內容類似：  
  
```  
<someElement xsi:type='tibrv:arrayOfShort'>  
<item>100</item>  
<item>200</item>  
<item>300</item>  
<item>400</item>  
<item>500</item>  
</someElement>  
  
```  
  
 IPaddress 的結構描述看起來與下列內容類似：  
  
```  
<xsd:simpleType name='IPaddress'>  
  
 <xsd:restriction base="xs:string">  
   <xsd:minLength value="7" />  
   <xsd:maxLength value="15" />  
  
 </xsd:restriction>  
       </xsd:simpleType>   
</xsd:simpleType>  
  
```  
  
 IPport 的結構描述看起來與下列內容類似：  
  
```  
<xsd:simpleType name='IPport'>  
  
<xsd:restriction base='xsd:ushort'>  
</xsd:simpleType>  
```  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 中的訊息對應](../core/message-mapping-in-tibco-rendezvous.md)   
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)