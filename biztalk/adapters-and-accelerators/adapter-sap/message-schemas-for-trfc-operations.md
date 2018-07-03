---
title: TRFC 作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tRFC operations, message structure for
- tRFC operations, message schemas for
- tRFC operations, message actions for
ms.assetid: 0e269555-f0a1-40ae-a1b5-d8c4981e730f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a25413854b35a7bd27b3621a9c8ddfff31f083a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999775"
---
# <a name="message-schemas-for-trfc-operations"></a>TRFC 作業的訊息結構描述
遠端函式呼叫 Transactiostructnal (Trfc) 用來執行 RFC 呼叫中的工作 (LUW) 邏輯單元。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援多個 Trfc LUW 每輸入的 tRFC 呼叫。 輸出 （用戶端） tRFC 呼叫，配接器可以支援單一一個 tRFC LUW;它因此 for LUW 上建立 SAP 針對每個用戶端 tRFC 呼叫。 如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 tRFC 作業，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。 本章節描述的訊息結構描述和 tRFC 作業的動作。  

## <a name="message-structure-for-trfc-operations"></a>TRFC 作業的訊息結構  
 每個 tRFC 作業是由要求訊息和回覆 （回應） 訊息所組成。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]關聯的 SAP 系統的交易識別碼 (TID) 可識別 LUW 上 SAP 系統的 GUID。 此 GUID 可以在兩個 tRFC 要求和回應訊息中存在\<TransactionalRfcOperationIdentifier\>項目。  

-   輸出的 tRFC 呼叫，可傳遞至 tRFC 要求訊息中的配接器的 GUID。 如果您未提供 GUID，配接器會產生一個。 配接器永遠會傳回 tRFC 回應訊息中的 GUID。 您會將此 GUID 傳入 RfcConfirmTransID 作業，以確認 TID SAP 系統上。  

-   輸入的 tRFC 呼叫，配接器會產生並對應至 SAP TID tRFC 要求訊息中的 GUID。 您可以選擇性地傳回回應訊息中的此 GUID。  

> [!IMPORTANT]
>  在某些情況下，例如若要疑難排解問題的 SAP 系統上，您可能需要 SAP TID 可識別 tRFC SAP 系統上的實際值。 您可以取得 SAP TID，藉由呼叫相關聯的 GUID 值**ConvertGuidToTid**方法。 如需詳細資訊**ConvertGuidToTid**，請參閱[特殊作業](../../adapters-and-accelerators/adapter-sap/special-operations.md)。  

 下表顯示使用 tRFC 作業的和 RfcConfirmTransID 作業的訊息結構描述。 RfcConfirmTransID 作業會顯示配接器，以便確認用戶端的 tRFC 呼叫中的 SAP TID。  


|                             作業                             |                                                                                                                                                                                                                                                                         XML 結構                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                                             描述                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   tRFC<br /><br /> ([RFC_NAME])                   | `<[RFC_NAME] xmlns="[VERSION]/Trfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Trfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   …   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </[RFC_NAME]>` | 叫用 tRFC SAP 系統上。<br /><br /> -匯入，變更，並支援資料表參數。<br /><br /> -匯入並變更參數可以是 SAP 結構類型，SAP 資料表類型或 SAP 簡單資料型別。<br /><br /> -tRFC 用戶端呼叫沒有傳回輸出端中的值。 SAP 以非同步方式執行它們只輸入端值。<br /><br /> \<TransactionalRfcOperationIdentifier\>項目：<br /><br /> -若為輸出的 tRFC 呼叫中，您可以選擇性地指定應該對應至 SAP TID，這個項目中的配接器的 GUID。 如果未指定的 GUID，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生一個，並將它對應至 tRFC 的 SAP TID。<br /><br /> -若為輸入的 tRFC 呼叫，配接器會對應到 SAP TID，此項目中的 GUID。 |
|          tRFC 回應<br /><br /> （[RFC_NAME] 回應）           |                                                                                                                                                                                                   `<[RFC_NAME]Response xmlns="[VERSION]/Trfc/">   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </[RFC_NAME]Response>`                                                                                                                                                                                                   |                                                                                                                                                                   指出 RFC，已傳送到 SAP 系統。<br /><br /> -tRFC 用戶端呼叫沒有傳回輸出端中的值。 SAP 以非同步方式執行它們只輸入端值。<br /><br /> \<TransactionalRfcOperationIdentifier\>項目：<br /><br /> -若為輸出的 tRFC 呼叫配接器會傳送此項目中 tRFC 的 SAP TID 與相關聯的 GUID。<br /><br /> -若為輸入的 tRFC 呼叫中，您可以選擇性地傳回要求訊息中的配接器所傳送的 GUID。                                                                                                                                                                    |
|         RfcConfirmTransID<br /><br /> (RfcConfirmTransID)         |                                                                                                                                                                                                    `<RfcConfirmTransID xmlns="[VERSION]/Trfc/">   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </RfcConfirmTransID>`                                                                                                                                                                                                    |                                                                                                                                                             RfcConfirmTransID 作業確認用於 SAP 系統上的輸出 tRFC 作業的 TID。<br /><br /> \<TransactionalRfcOperationIdentifier\>項目包含對應至 TID 與輸出的 tRFC 呼叫相關聯的 GUID。 您應該將它設定為 tRFC 回應訊息中的配接器所傳回的 guid 值。<br /><br /> 如需有關 RfcConfirmTransID 作業的詳細資訊，請參閱[特殊作業](../../adapters-and-accelerators/adapter-sap/special-operations.md)。                                                                                                                                                              |
| RfcConfirmTransIDResponse<br /><br /> (RfcConfirmTransIDResponse) |                                                                                                                                                                                                                                      `<RfcConfirmTransIDResponse xmlns="[VERSION]/Trfc/"> </RfcConfirmTransIDResponse>`                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                   表示[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]確認 TID SAP 系統上的。                                                                                                                                                                                                                                                                                                                                                                    |

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [RFC_NAME] = RFC; 的名稱比方說，RFC_CUSTOMER_GET。  

 [IN_PARAM_NAME] = RFC 匯入參數的名稱。  

 [INOUT_PARAM_NAME] = RFC 變更參數的名稱。  

 [TABLE_PARAM_NAME] = RFC 資料表參數名稱。  

 [STRUCT_PARAM_NAME] = RFC 結構參數的名稱。  

 GUID = 識別 SAP TID tRFC 相關聯的 GUID。  

## <a name="message-actions-for-trfc-operations"></a>TRFC 作業的訊息動作  
 下表顯示用於 tRFC 作業的訊息動作。  


|         作業          |              訊息的動作              |                                 範例                                  |
|----------------------------|------------------------------------------|--------------------------------------------------------------------------|
|         [RFC_NAME]         |        [VERSION] /Trfc/ [RFC_NAME]         |      http://Microsoft.LobServices.Sap/2007/03/Trfc/RFC_CUSTOMER_GET      |
|    [RFC_NAME]回應     |    [VERSION] /Trfc/ [RFC_NAME] / 回應    | http://Microsoft.LobServices.Sap/2007/03/Trfc/RFC_CUSTOMER_GET/response  |
|     RfcConfirmTransID      |     [VERSION] / Trfc/RfcConfirmTransID     |     http://Microsoft.LobServices.Sap/2007/03/Trfc/RfcConfirmTransID      |
| RfcConfirmTransID 回應 | [版本/Trfc/RfcConfirmTransID/回應 | http://Microsoft.LobServices.Sap/2007/03/Trfc/RfcConfirmTransID/response |

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [RFC_NAME] = 要叫用; RFC 的名稱比方說，RFC_CUSTOMER_GET。  

## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)