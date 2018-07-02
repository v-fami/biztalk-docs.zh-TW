---
title: RFC 作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RFC operations, message structure for
- RFC operations, message actions for
ms.assetid: 50cd9b28-2e66-4c76-9d19-f0da6e7b8e10
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 156b8e8c218c4ad23d49959323ed324b0c7cdfd0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972847"
---
# <a name="message-schemas-for-rfc-operations"></a>RFC 作業的訊息結構描述
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]呈現 SAP 遠端函式呼叫 (RFC) 做為作業。 本主題包含的訊息結構描述 」 和 「 用於 RFC 作業的訊息動作的相關資訊。 訊息結構是輸入和輸出的 RFC 作業的相同。 如需配接器支援 RFC 作業的概觀，請參閱 <<c0> [ 對 sap Rfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。  

 您也可以做為介面卡上的 RFC 作業叫用 Bapi。 本主題會包含這類引動過程的訊息結構的範例。  

## <a name="message-structure-for-rfc-operations"></a>RFC 作業的訊息結構  
 下表顯示 RFC 訊息結構描述。 每個 RFC 作業是由要求訊息和回覆 （回應） 訊息所組成。  


|                             訊息                              |                                                                                                                                                                                                                         XML 訊息結構                                                                                                                                                                                                                          |                                                                                                                                                                                                     描述                                                                                                                                                                                                      |
|------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   RFC<br /><br /> ([RFC_NAME])                   | `<[RFC_NAME] xmlns="[VERSION]/Rfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]>` |                                                                                              叫用 RFC，SAP 系統上。<br /><br /> -匯入，變更，並支援資料表參數。<br /><br /> -匯入並變更參數可以是 SAP 結構類型，SAP 資料表類型或 SAP 簡單資料型別。                                                                                              |
|                RFC 回應 （[RFC_NAME] 回應）                 |     `<[RFC_NAME]Response xmlns="[VERSION]/Rfc/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME>     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]Response>`      | 傳回的 RFC。<br /><br /> -Export，變更，並支援資料表參數。<br /><br /> **注意：** 根據預設，資料表參數不會顯示在回應訊息中。 如果您需要在回應訊息中的資料表參數時，您必須傳遞空的資料表參數在要求訊息中。<br /><br /> -匯入並變更參數可以是 SAP 結構類型，SAP 資料表類型或 SAP 簡單資料型別。 |
|         RfcGetAttributes<br /><br /> (RfcGetAttributes)          |                                                                                                                                                                                                                `<RfcGetAttributes> </RfcGetAttributes>`                                                                                                                                                                                                                |                                                  RfcGetAttributes 是 RFC SDK API 作業呈現的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 RfcGetAttributes 作業可讓用戶端程式擷取語言、 系統識別碼，以及 RFC 連線相關聯的夥伴字碼頁。                                                   |
| RfcGetAttributes 回應<br /><br /> (RfcGetAttributesResponse) |                                                                                                                                                          `<RfcGetAttributesResponse>   <Language>lang</Language>   <SysId>id</SysId>   <PartnerCodePage>pnrcp</PartnerCodePage> </RfcGetAttributesResponse>`                                                                                                                                                           |                                                                                                                              語言、 系統識別碼，以及 RFC 連線相關聯的夥伴字碼頁，則會傳回 RfcGetAttributes 作業的回應。                                                                                                                              |

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.SAP/2007/03。  

 [RFC_NAME] = RFC; 的名稱比方說，RFC_CUSTOMER_GET。  

 [IN_PARAM_NAME] = RFC 匯入參數的名稱。  

 [OUT_PARAM_NAME] = RFC 匯出參數的名稱。  

 [INOUT_PARAM_NAME] = RFC 變更參數的名稱。  

 [TABLE_PARAM_NAME] = RFC 資料表參數名稱。  

 [STRUCT_PARAM_NAME] = RFC 結構參數的名稱。  

## <a name="message-actions-for-rfc-operations"></a>RFC 作業的訊息動作  
 下表顯示 RFC 作業的訊息動作。  


|         作業         |           訊息的動作           |                                範例                                 |
|---------------------------|------------------------------------|------------------------------------------------------------------------|
|        [RFC_NAME]         |      [VERSION]/Rfc/[RFC_NAME]      |     http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET      |
|    [RFC_NAME]回應    | [VERSION] /Rfc/ [RFC_NAME] / 回應  | http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET/response |
|     RfcGetAttributes      |     [VERSION] / RfcGetAttributes     |       http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes        |
| RfcGetAttributes 回應 | [版本/RfcGetAttributes/回應 |   http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes/response   |

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [RFC_NAME] = 要叫用; RFC 的名稱比方說，RFC_CUSTOMER_GET。  

## <a name="invoking-a-bapi-as-an-rfc-operation"></a>叫用 RFC 作業的 BAPI  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]作為 RFC 作業和商務物件的方法，請瀏覽 Bapi。 RFC 作業為 Bapi 會依名稱顯示。 如需有關如何使用商務物件介面叫用 Bapi 的詳細資訊，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。  

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