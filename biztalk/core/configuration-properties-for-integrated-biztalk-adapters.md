---
title: 整合式的 BizTalk 配接器的組態屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, security
- adapters, passwords
- IReceiveLocation.CustomData property
- security, passwords
- ISendPort.CustomData property
- binding files, passwords
- adapters, properties
- binding files, security
ms.assetid: 4780a558-4322-428a-aa4a-0c32913faded
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45779131906460040db969bd4ef412b8f9220ab6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005983"
---
# <a name="configuration-properties-for-integrated-biztalk-adapters"></a>整合式 BizTalk 配接器的組態屬性
「 BizTalk 總管物件模型會公開**IReceiveLocation.CustomData**並**ISendPort.CustomData**包含配接器組態屬性包中的名稱/值形式的屬性組 XML 字串。 此名稱/值組 XML 字串會儲存在\<CustomProps\>內的項目\<TransportTypeData\>繫結檔案中的項目。 中的資訊，大部分\<CustomProps\>元素都會對應到配接器可以設定 BizTalk Server 使用者介面 （例如 BizTalk 管理主控台或 BizTalk 總管 中） 中的資訊。 如果這些值存在於繫結檔案中，當匯入繫結檔案時，它們便會套用至指定之接收位置和傳送埠的配接器組態。 所有配接器的組態資訊都會儲存在「單一登入」資料庫中。  
  
 本節描述可為每個整合式 BizTalk 配接器設定的組態屬性。  
  
> [!NOTE]
>  密碼資訊儲存在\<TransportTypeData\>項目繫結檔案遮罩，如此敏感性資料不會儲存在純文字。 取決於傳輸方式，密碼資訊若非以 NULL 取代，就會以星號取代。 將繫結檔案匯入到目標 BizTalk Server 組態之前，您必須以手動方式將此資訊輸入繫結檔案以更新配接器組態。  
  
 使用配接器架構建置的配接器的組態資料儲存在\<AdapterConfig\>項目。 由於\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料類型**\< \>** 必須逸出此項目中包含的字元，或會發生錯誤時您嘗試匯入繫結檔案。 這樣會使組態資料的文字，比沒有逸出字元時更加難以閱讀。 下列範例說明從繫結至 POP3 配接器之傳送埠的範例組態資料，逸出這些字元的效果。  
  
 **不逸出所使用的 <> 字元的 TransportTypeData 組態資料\<AdapterConfig\>項目**  
  
 這項組態資料無效因為\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料型別並\<\>中所包含的字元\<AdapterConfig\>項目不會逸出：  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<mailServer>test.microsoft.com</mailServer>  
<serverPort>0</serverPort>  
<userName>testuser</userName>  
<password>******</password>  
<authenticationScheme>Basic</authenticationScheme>  
<sslRequired>false</sslRequired>  
<applyMIME>true</applyMIME>  
<bodyPartContentType>text/xml</bodyPartContentType>  
<bodyPartIndex>1</bodyPartIndex>  
<errorThreshold>10</errorThreshold>  
<pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure>   
<uri>POP3://test.microsoft.com#testuser</uri>  
</Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 **未逸出 <> 字元中使用的 TransportTypeData 組態資料\<AdapterConfig\>項目**  
  
 由於\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料類型\<\>必須逸出字元，從\<AdapterConfig\>項目，如下所示：  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test  
microsoft.com</mailServer><serverPort>0</serverPort>&  
lt;userName>testuser</userName><password>******</pass  
word><authenticationScheme>Basic</authenticationScheme>&  
lt;sslRequired>false</sslRequired><applyMIME>true</ap  
plyMIME><bodyPartContentType>text/xml</bodyPartContentType&  
gt;<bodyPartIndex>1</bodyPartIndex><errorThreshold>10  
</errorThreshold><pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri  
>POP3://test.microsoft.com#testuser</uri></Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 以「配接器架構」建立的整合式配接器包括下列各項：  
  
- FTP 配接器  
  
- MQSeries 配接器  
  
- MSMQ 配接器  
  
- POP3 配接器  
  
- Windows Sharepoint Services 配接器  
  
  若要檢視對每個整合式配接器用來做為 TransportTypeData 組態資料的範例字串，請參閱與此節中的配接器關聯的組態屬性主題。  
  
## <a name="in-this-section"></a>本節內容  
 [設定屬性變數類型](../core/configuration-property-variable-types.md)  
  
 [File 配接器設定屬性](../core/file-adapter-configuration-properties.md)  
  
 [FTP 配接器設定屬性](../core/ftp-adapter-configuration-properties.md)  
  
 [HTTP 配接器設定屬性](../core/http-adapter-configuration-properties.md)  
  
 [MQSeries 配接器設定屬性](../core/mqseries-adapter-configuration-properties.md)  
  
 [MSMQ 配接器設定屬性](../core/msmq-adapter-configuration-properties.md)  
  
 [POP3 配接器設定屬性](../core/pop3-adapter-configuration-properties.md)  
  
 [SMTP 配接器設定屬性](../core/smtp-adapter-configuration-properties.md)  
  
 [SOAP 配接器設定屬性](../core/soap-adapter-configuration-properties.md)  
  
 [Windows Sharepoint Services 配接器設定屬性](../core/windows-sharepoint-services-adapter-configuration-properties.md)