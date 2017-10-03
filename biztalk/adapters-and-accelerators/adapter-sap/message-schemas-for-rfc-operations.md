---
title: "RFC 作業的訊息結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RFC operations, message structure for
- RFC operations, message actions for
ms.assetid: 50cd9b28-2e66-4c76-9d19-f0da6e7b8e10
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9d1dfe3ff3cef27269facfe89d3aea8f43cb10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-rfc-operations"></a>RFC 作業的訊息結構描述
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]呈現 SAP 遠端函式呼叫 (RFC) 做為作業。 本主題包含的訊息結構描述 」 和 「 用於 RFC 作業的訊息動作的相關資訊。 訊息結構是相同的輸入和輸出 RFC 作業。 如需配接器支援的 RFC 作業的概觀，請參閱[作業中 SAP Rfc](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。  
  
 您也可以使用做為介面卡上的 RFC 作業叫用的 Bapi。 本主題會包含這類引動過程訊息結構的範例。  
  
## <a name="message-structure-for-rfc-operations"></a>RFC 作業的訊息結構  
 下表顯示 RFC 訊息結構描述。 每個 RFC 作業包含要求訊息和回覆 （回應） 的訊息。  
  
|訊息|XML 訊息結構|Description|  
|-------------|---------------------------|-----------------|  
|RFC<br /><br /> ([RFC_NAME])|`<[RFC_NAME] xmlns="[VERSION]/Rfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]>`|叫用的 RFC，SAP 系統上。<br /><br /> -匯入，變更，以及支援資料表參數。<br /><br /> -匯入，變更參數可以是 SAP 結構類型、 SAP 資料表類型或 SAP 簡單資料類型。|  
|RFC 回應 （[RFC_NAME] 回應）|`<[RFC_NAME]Response xmlns="[VERSION]/Rfc/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME>     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]Response>`|傳回的 RFC。<br /><br /> -Export，變更，並支援資料表參數。<br /><br /> **注意：**根據預設，資料表參數不會顯示在回應訊息中。 如果您需要在回應訊息中的資料表參數時，您必須在要求訊息中傳遞空資料表參數。<br /><br /> -匯入，變更參數可以是 SAP 結構類型、 SAP 資料表類型或 SAP 簡單資料類型。|  
|RfcGetAttributes<br /><br /> (RfcGetAttributes)|`<RfcGetAttributes> </RfcGetAttributes>`|RfcGetAttributes 是呈現由 RFC SDK API 作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 RfcGetAttributes 作業可讓用戶端程式擷取語言、 系統識別碼，以及與 RFC 連線相關聯的夥伴字碼頁。|  
|RfcGetAttributes 回應<br /><br /> (RfcGetAttributesResponse)|`<RfcGetAttributesResponse>   <Language>lang</Language>   <SysId>id</SysId>   <PartnerCodePage>pnrcp</PartnerCodePage> </RfcGetAttributesResponse>`|RfcGetAttributes 作業的回應傳回語言、 系統識別碼，以及與 RFC 連線相關聯的夥伴字碼頁。|  
  
 [版本] = 訊息版本字串。例如，http://Microsoft.LobServices.SAP/2007/03。  
  
 [RFC_NAME] = RFC; 的名稱例如，RFC_CUSTOMER_GET。  
  
 [IN_PARAM_NAME] = RFC 匯入參數名稱。  
  
 [OUT_PARAM_NAME] = 匯出 RFC 參數的名稱。  
  
 [INOUT_PARAM_NAME] = RFC 變更參數的名稱。  
  
 [TABLE_PARAM_NAME] = RFC 資料表參數的名稱。  
  
 [STRUCT_PARAM_NAME] = RFC 結構參數的名稱。  
  
## <a name="message-actions-for-rfc-operations"></a>RFC 作業的訊息動作  
 下表顯示 RFC 作業的訊息動作。  
  
|作業|訊息的動作|範例|  
|---------------|--------------------|-------------|  
|[RFC_NAME]|[版本] /Rfc/ [RFC_NAME]|http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET|  
|[RFC_NAME]回應|[版本] /Rfc/ [RFC_NAME] / 回應|http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET/response|  
|RfcGetAttributes|[版本] / RfcGetAttributes|http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes|  
|RfcGetAttributes 回應|[版本/RfcGetAttributes/回應|http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes/response|  
  
 [版本] = 訊息版本字串。例如，http://Microsoft.LobServices.Sap/2007/03。  
  
 [RFC_NAME] = 要叫用; RFC 的名稱例如，RFC_CUSTOMER_GET。  
  
## <a name="invoking-a-bapi-as-an-rfc-operation"></a>以 RFC 作業叫用 BAPI  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現 Bapi 同時 RFC 作業和商務物件的方法。 做為 RFC 作業便會依名稱顯示 Bapi。 如需使用商務物件介面叫用的 Bapi 的詳細資訊，請參閱[SAP 中的 Bapi 作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。  
  
 下列 XML 顯示 BAPI (BAPI_CUSTOMER_GETDETAIL2) 以 RFC 叫用的訊息結構。 這項作業的訊息動作是： http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2。  
  
```  
<BAPI_CUSTOMER_GETDETAIL2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <COMPANYCODE>1001</COMPANYCODE>  
  <CUSTOMERNO>0000001001</CUSTOMERNO>  
  <CUSTOMERBANKDETAIL>  
    <BAPICUSTOMER_02 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <CUSTOMER />  
      <BANK_CTRY />  
      <BANK_KEY />  
      <BANK_ACCT />  
      <CTRL_KEY />  
      <PARTNER_BK />  
      <COLL_AUTH />  
      <BANK_REF />  
    </BAPICUSTOMER_02>  
  </CUSTOMERBANKDETAIL>  
</BAPI_CUSTOMER_GETDETAIL2>  
```  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)