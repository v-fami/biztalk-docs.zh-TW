---
title: MQSeries 內容屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQCIH_TaskEndStatus property [MQSeries adapters]
- MQIIH_SecurityScope property [MQSeries adapters]
- MQCIH_AbendCode property [MQSeries adapters]
- filters, MQSeries adapters
- MQCIH_ReturnCode property [MQSeries adapters]
- MQCIH_TransactionId property [MQSeries adapters]
- MQCIH_ReplyToFormat property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- MQMD_PutTime property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQMD_PutApplName property [MQSeries adapters]
- configuring [MQSeries adapters], filtering
- MQCIH_UOWControl property [MQSeries adapters]
- MQCIH_ErrorOffset property [MQSeries adapters]
- MQMD_Priority property [MQSeries adapters]
- MQMD_MsgSeqNumber property [MQSeries adapters]
- MQMD_Format property [MQSeries adapters]
- MQCIH_ConversationalTask property [MQSeries adapters]
- Message Descriptor table [MQSeries adapters]
- MQMD_Feedback property [MQSeries adapters]
- MQCIH_Authenticator property [MQSeries adapters]
- MQIIH_TranState property [MQSeries adapters]
- MQCIH_AttentionId property [MQSeries adapters]
- MQMD_UserIdentifier property [MQSeries adapters]
- MQCIH_Flags property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQIIH_Format property [MQSeries adapters]
- MQMD_Offset property [MQSeries adapters]
- MQMD_BackoutCount property [MQSeries adapters]
- MQMD_Report property [MQSeries adapters]
- MQMD_MsgFlags property [MQSeries adapters]
- MQSeries adapters, filtering
- MQMD_ApplIdentityData property [MQSeries adapters]
- MQIIH_Authenticator property [MQSeries adapters]
- MQIIH_MFSMapName property [MQSeries adapters]
- MQCIH_LinkType property [MQSeries adapters]
- MQMD_Persistence property [MQSeries adapters]
- MQCIH_CursorPosition property [MQSeries adapters]
- MQCIH_Format property [MQSeries adapters]
- MQCIH_Facility property [MQSeries adapters]
- MQCIH_CancelCode property [MQSeries adapters]
- MQMD_PutDate property [MQSeries adapters]
- MQCIH_NextTransactionId property [MQSeries adapters]
- MQIIH_CommitMode property [MQSeries adapters]
- MQIIH_ReplyToFormat property [MQSeries adapters]
- MQCIH_Function property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- MQCIH_StartCode property [MQSeries adapters]
- MQMD_Expiry property [MQSeries adapters]
- MQMD_PutApplType property [MQSeries adapters]
- MQCIH_FacilityLike property [MQSeries adapters]
- MQIIH_Flags property [MQSeries adapters]
- MQCIH_CompCode property [MQSeries adapters]
- MQSeries adapters, properties
- MQCIH_FacilityKeepTime property [MQSeries adapters]
- MQMD_ApplOriginData property [MQSeries adapters]
- MQCIH_Reason property [MQSeries adapters]
- MQIIH_LTermOverride property [MQSeries adapters]
- MQMD_CodedCharSetId property [MQSeries adapters]
- MQMD_GroupID property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgType property [MQSeries adapters]
- MQMD_OriginalLength property [MQSeries adapters]
- MQMD_Encoding property [MQSeries adapters]
- MQMD_AccountingToken property [MQSeries adapters]
- MQCIH_OutputDataLength property [MQSeries adapters]
- MQIIH_TranInstanceId property [MQSeries adapters]
- MQCIH_GetWaitInterval property [MQSeries adapters]
- MQCIH_ADSDescriptor property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: 1b22b7d7-432b-4ec5-938c-c43077ce3e0f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 684fad8e1a417e9faf7127a81a4e8f7d6f10e630
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976591"
---
# <a name="mqseries-context-properties"></a>MQSeries 內容屬性
MQSeries 配接器提供一組 MQSeries 專用的內容屬性，可在應用程式中使用。 您可以在篩選運算式與協調流程中使用這些屬性。  
  
 若要指派 MQSeries 內容屬性給要傳送到繫結至 MQSeries 配接器之傳送埠的訊息，請使用訊息設定運算子，然後在 MQSeries 命名空間中指定其中一個可用的內容屬性。  
  
 以下是範例設定 MQSeries **MQMD_UserIdentifier**屬性：  
  
```  
Message_2(MQSeries.MQMD_UserIdentifier) = "MeMyselfAndI";  
```  
  
 您必須從 IBM MQSeries SDK 所含的 C 程式設計語言標頭檔中取得列舉值。 您可以在 Program Files\IBM\WebSphere MQ\Tools\c\include 資料夾中找到這些檔案。 這些檔案定義在設定或讀取 MQSeries 內容屬性值時所要使用的值。  
  
 十六進位字串值是代表二進位值的字元字串。 它們沒有諸如 0x 的前置詞。 它們包含從 0 至 9 的數字，以及從 "a" 至 "f" 或 "A" 至 "F" 的字母。 此配接器會忽略其中的空白。  
  
 如需有關這些屬性的詳細資訊，請參閱 IBM WebSphere MQ 文件。  
  
 下表顯示一組完整、可用的「訊息描述元」(MQMD 結構)」屬性及其對應的類型與值。  
  
|[屬性]|類型|長度|ReplTest1|  
|----------|----------|------------|-----------|  
|**MQMD_AccountingToken**|string|64|十六進位字串|  
|**MQMD_ApplIdentityData**|string|32|十六進位字串|  
|**MQMD_ApplOriginData**|string|4|String<br /><br /> **預設值：** 空間|  
|**MQMD_BackoutCount**|不帶正負號的整數|4|Number<br /><br /> 唯讀<br /><br /> **預設值：** 0|  
|**MQMD_CodedCharSetId**|不帶正負號的整數|4|Number<br /><br /> **預設值：** 0|  
|**MQMD_CorrelId**|string|48|十六進位字串|  
|**MQMD_Encoding**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。 **預設值：** 0|  
|**MQMD_Expiry**|不帶正負號的整數|4|Number|  
|**MQMD_Feedback**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。 **預設值：** 0|  
|**MQMD_Format**|string|8|String<br /><br /> 若設為 MQXMIT，請確定 MQXQH 屬性有值。|  
|**MQMD_GroupID**|string|48|十六進位字串|  
|**MQMD_MsgFlags**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。 **預設值：** 0|  
|**MQMD_MsgId**|string|48|十六進位字串|  
|**MQMD_MsgSeqNumber**|不帶正負號的整數|4||  
|**MQMD_MsgType**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。|  
|**MQMD_Offset**|不帶正負號的整數|4||  
|**MQMD_OriginalLength**|不帶正負號的整數|4||  
|**MQMD_Persistence**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。|  
|**MQMD_Priority**|不帶正負號的整數|4|Number|  
|**MQMD_PutApplName**|string|28|String<br /><br /> **預設值：** 空間|  
|**MQMD_PutApplType**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。 **預設值：** 0|  
|**MQMD_PutDate**|string|8|date|  
|**MQMD_PutTime**|string|8|Time|  
|**MQMD_ReplyToQ**|string|48|String<br /><br /> **預設值：** 空間|  
|**MQMD_ReplyToQMgr**|string|48|String<br /><br /> **預設值：** 空間|  
|**MQMD_Report**|不帶正負號的整數|4|Number<br /><br /> 使用標頭檔值。|  
|**MQMD_UserIdentifier**|string|12|String<br /><br /> 當您使用包含使用者識別碼**SSOAffiliateApplication**屬性。|  
  
 直接從 MQSeries 傳輸佇列接收訊息時，MQSeries 配接器會將傳輸佇列標頭屬性 (MQXQH 資料結構) 格式化，然後放在對應的內容屬性中。 標頭屬性時直接傳送訊息至 MQSeries 傳輸佇列，格式化並指派值給從對應的內容屬性只有當**MQMD_Format**屬性的值為 MQXMIT。 下表描述這些屬性。  
  
|[屬性]|類型|長度|ReplTest1|  
|----------|----------|------------|-----------|  
|**MQXQH_RemoteQMgrName**|string|48|string|  
|**MQXQH_RemoteQName**|string|48|string|  
  
 此配接器會根據相同規則將本主題稍早所列的屬性一起填入下列「訊息描述元」值中。 此配接器會在這些屬性名稱之前加上 MQXQH_ 而不是 MQMD_，否則它們會直接對應至「訊息描述元」表格中所定義的那些屬性：  
  
- **MQXQH_MsgDesc_AccountingToken**  
  
- **MQXQH_MsgDesc_ApplIdentityData**  
  
- **MQXQH_MsgDesc_ApplOriginData**  
  
- **MQXQH_MsgDesc_BackoutCount**  
  
- **MQXQH_MsgDesc_CodedCharSetId**  
  
- **MQXQH_MsgDesc_CorrelId**  
  
- **MQXQH_MsgDesc_Encoding**  
  
- **MQXQH_MsgDesc_Expiry**  
  
- **MQXQH_MsgDesc_Feedback**  
  
- **MQXQH_MsgDesc_Format**  
  
- **MQXQH_MsgDesc_MsgId**  
  
- **MQXQH_MsgDesc_MsgType**  
  
- **MQXQH_MsgDesc_Persistence**  
  
- **MQXQH_MsgDesc_Priority**  
  
- **MQXQH_MsgDesc_PutApplName**  
  
- **MQXQH_MsgDesc_PutApplType**  
  
- **MQXQH_MsgDesc_PutDate**  
  
- **MQXQH_MsgDesc_PutTime**  
  
- **MQXQH_MsgDesc_ReplyToQ**  
  
- **MQXQH_MsgDesc_ReplyToQMgr**  
  
- **MQXQH_MsgDesc_Report**  
  
- **MQXQH_MsgDesc_UserIdentifier**  
  
  在屬性結構描述中還包含其他與 MQSeries 相關的屬性，並可用於篩選運算式中。 下表列出這些屬性。  
  
|[屬性]|類型|長度|ReplTest1|  
|----------|----------|------------|-----------|  
|**MQCIH_AbendCode**|string|4||  
|**MQCIH_ADSDescriptor**|不帶正負號的整數|4||  
|**MQCIH_AttentionId**|string|4||  
|**MQCIH_Authenticator**|string|8|當您使用設定為 SSO 密碼**SSOAffiliateApplication**屬性。 **注意：** 這個值會設為空白，MQSeries 配接器，如果 SSO 密碼的長度超過 8 個字元。|  
|**MQCIH_CancelCode**|string|4||  
|**MQCIH_CompCode**|不帶正負號的整數|4||  
|**MQCIH_ConversationalTask**|不帶正負號的整數|4||  
|**MQCIH_CursorPosition**|不帶正負號的整數|4||  
|**MQCIH_ErrorOffset**|不帶正負號的整數|4||  
|**MQCIH_Facility**|string|16|十六進位字串|  
|**MQCIH_FacilityKeepTime**|不帶正負號的整數|4||  
|**MQCIH_FacilityLike**|string|4||  
|**MQCIH_Flags**|不帶正負號的整數|4||  
|**MQCIH_Format**|string|||  
|**MQCIH_Function**|string|4||  
|**MQCIH_GetWaitInterval**|不帶正負號的整數|4||  
|**MQCIH_LinkType**|不帶正負號的整數|4||  
|**MQCIH_NextTransactionId**|string|4||  
|**MQCIH_OutputDataLength**|不帶正負號的整數|4||  
|**MQCIH_Reason**|不帶正負號的整數|4||  
|**MQCIH_ReplyToFormat**|string|||  
|**MQCIH_ReturnCode**|不帶正負號的整數|4||  
|**MQCIH_StartCode**|string|4||  
|**MQCIH_TaskEndStatus**|不帶正負號的整數|4||  
|**MQCIH_TransactionId**|string|4||  
|**MQCIH_UOWControl**|不帶正負號的整數|4||  
|**MQIIH_Authenticator**|string|8|當您使用設定為 SSO 密碼**SSOAffiliateApplication**屬性。 **注意：** 這個值會設為空白，MQSeries 配接器，如果 SSO 密碼的長度超過 8 個字元。|  
|**MQIIH_CommitMode**|string|||  
|**MQIIH_Flags**|不帶正負號的整數|4||  
|**MQIIH_Format**|string|||  
|**MQIIH_LTermOverride**|string|8||  
|**MQIIH_MFSMapName**|string|8||  
|**MQIIH_ReplyToFormat**|string|||  
|**MQIIH_SecurityScope**|string|||  
|**MQIIH_TranInstanceId**|string|32|十六進位字串|  
|**MQIIH_TranState**|string|||  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)   
 [與 BizTalk Server 相關的屬性](../core/properties-related-to-biztalk-server.md)   
 [屬性的資料類型轉換](../core/data-type-conversion-of-properties.md)