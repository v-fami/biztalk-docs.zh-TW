---
title: BAPI 作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI operations, message schemas for
- BAPI operations, message structure for
- BAPI operations, message actions for
ms.assetid: ef4d88e8-f31a-4b68-a303-6885b6f8c083
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796e7beb428e6f9a4f0df63eff9cf45e9d5410bb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995215"
---
# <a name="message-schemas-for-bapi-operations"></a>BAPI 作業的訊息結構描述
下列各節描述的訊息結構描述和使用上叫用 Bapi 的訊息動作[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]當做商務物件的方法。 您也可以做為介面卡上的 RFC 作業叫用 Bapi。 如需有關用來叫用 Rfc 之訊息的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。 不論您如何叫用 BAPI 的介面卡上，配接器永遠會叫用 BAPI 為 SAP 系統的 RFC。 如需如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 Bapi，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。  

## <a name="message-structure-for-business-object-operations"></a>適用於商務物件作業的訊息結構  
 下表顯示用來叫用 BAPI 的商務物件方法為訊息結構描述。  

|作業|XML 結構|描述|  
|---------------|-------------------|-----------------|  
|[BUSOBJ_METHOD]|`<[BUSOBJ_METHOD] xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]>`|在 SAP 系統的商務物件方法來叫用。<br /><br /> 支援匯入、 變更和資料表參數。|  
|[BUSOBJ_METHOD]回應|`<[BUSOBJ_METHOD]Response xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]Response>`|商務物件方法的回應。<br /><br /> 匯出，請變更，並支援資料表參數。<br /><br /> **請注意**根據預設，資料表參數不會顯示在回應訊息中。 如果您需要在回應訊息中的資料表參數時，您必須傳遞空的資料表參數在要求訊息中。|  

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [BUSOBJ_METHOD] = 商務物件方法; 的名稱比方說，CREATEFROMDAT2。  

 [IN_PARAM_NAME] = BAPI 匯入參數的名稱。  

 [OUT_PARAM_NAME] = BAPI 匯出參數的名稱。  

 [INOUT_PARAM_NAME] = BAPI 變更參數的名稱。  

 [TABLE_PARAM_NAME] = BAPI 資料表參數名稱。  

 [STRUCT_PARAM_NAME] = BAPI 結構參數的名稱。  

## <a name="message-actions-for-business-object-operations"></a>適用於商務物件作業的訊息動作  
 下表顯示用來叫用 Bapi 當做商務物件方法的訊息動作。  


|        作業         |                            訊息的動作                             |                                                   範例                                                    |
|--------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     [BUSOBJ_METHOD]      |     [VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]      |     http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2      |
| [BUSOBJ_METHOD]回應 | [VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]/response | http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/response |

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [BUSOBJ_NAME] = 商務物件的名稱比方說，BUS2032。  

 [BUSOBJ_METHOD] = 商務物件方法比方說，CREATEFROMDAT2。  

 [BAPI_RFC_NAME] = [RFC 名稱 BAPI;比方說，BAPI_SALESORDER_CREATEFROMDAT2。  

## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)