---
title: 結構描述的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues, schemas
- schemas, known issues
ms.assetid: 17651462-baa9-448a-954c-c09e70640f17
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ced040dab48f455e5af5a7731a319173fa27ca5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983063"
---
# <a name="schema-known-issues"></a>結構描述的已知問題
本節包含可協助您避免結構描述錯誤的有用資訊。  
  
## <a name="mcf21glodefxsd-schema"></a>MCF_21_GLO_DEF.xsd 結構描述  
 在 [templates\schemas\2.1] 資料夾中，結構描述 MCF_21_GLO_DEF.xsd 不 Common231 專案的一部分。  
  
## <a name="miscellaneous-errors-can-result-from-undeployed-schemas"></a>發生其他錯誤可能是因為已解除部署的結構描述  
 如果您無法識別中剖析或序列化的錯誤，請確認您已部署屬性結構描述和通用的結構描述 (MSH/ACK)。 解除部署的屬性結構描述和通用結構描述，可能會導致其他錯誤。  
  
## <a name="if-the-starter-project-is-installed-but-the-hl7-2x-schemas-are-not-installed-running-the-schema-wizard-generates-an-error"></a>如果已安裝的入門專案，但 HL7 2.X 結構描述不會安裝、 執行結構描述精靈會產生錯誤  
 如果您執行自訂安裝的 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 在您安裝這[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]入門專案，但執行未安裝 HL7 2.X 結構描述，然後再嘗試執行結構描述精靈 中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生發生錯誤。 對此解決方案是再次執行自訂安裝程序，才能安裝 HL7 2.X 結構描述。  
  
## <a name="msh91-enumeration-list-needs-to-be-updated"></a>MSH9.1 列舉清單需要更新  
 安裝 MSH_25_GLO_DEF 結構描述[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]在安裝時不包含完整的列舉清單 MSH9.1 (MessageType) 和 MSH9.2 (EventTrigger)，人事 HL72。標準的 X。 下表列出訊息類型和觸發程序事件的值，您必須新增至其相關聯的資料表，如果您想要使用其訊息類型包含值的結構描述。 比方說，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將不會處理 QBP ^ Z99 訊息，直到您將 「 QBP"新增至 Table76 MSH_25_GLO_DEF 中的列舉並不會處理 QBP ^ Z99 訊息，直到您將 「 Z99"新增至 Table3 MSH_25_GLO_DEF 中的列舉。  
  
 若要加入的 MSH9.1 」 或 「 MSH9.2 列舉值，請參閱中的 「 若要加入訊息標頭結構描述中的列舉值 」 程序[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。  
  
|欄位/資料表|要加入至列舉值|  
|------------------|--------------------------------------|  
|MessageType/Table76|ARD、 RDO、 RRO|  
|TriggerEvent/Table3|K11、 K13、 K15、 MFA、 O22、 Q11、 Q13、 Q15、 Q26、 Q27、 Q28、 Q29、 R0R、 Z73、 Z74、 Z75、 Z76、 Z77、 Z78、 Z79、 Z80、 Z81、 Z82、 Z83、 Z84、 Z85、 Z86、 Z87、 Z88、 Z89、 Z90、 Z91、 Z92、 Z93、 Z94、 Z95、 Z96、 Z97、 Z98、 Z99|  
|MessageStructure/Table354|ARD_A19 ORL_O22|  
  
## <a name="btahl7-does-not-support-schemas-with-an-ambiguous-structure"></a>BTAHL7 不支援具有模稜兩可的結構的結構描述  
 BTAHL7 引擎無法處理 HL7 結構描述具有模稜兩可的結構相符的訊息執行個體。 模稜兩可的結構描述結構是不完全由 HL7 標準定義。 這類結構描述包括 CSU、 OMD、 ORD 和 SUR.的訊息類型  
  
## <a name="btahl7-will-return-a-segment-sequence-error-for-some-messages"></a>BTAHL7 會傳回部分訊息的區段順序錯誤  
 BTAHL7 不能處理符合下面所列的結構描述的訊息。 這些訊息的內文剖析將會失敗，導致下列錯誤: 「 區段順序錯誤 （無效的區段找到在此區段之後） 」。 以下列出受影響的區段識別碼，訊息中。 所有這些錯誤的受影響的順序號碼為"2"。  
  
|版本|訊息類型|觸發程序事件|區段識別碼|  
|-------------|------------------|-------------------|----------------|  
|V2.3|CSU|C09|ORC_CommonOrderSegment|  
|V2.3|CSU|C10|ORC_CommonOrderSegment|  
|V2.3|CSU|C11|ORC_CommonOrderSegment|  
|V2.3|CSU|C12|ORC_CommonOrderSegment|  
|V2.3|SUR|P09|PSH_ProductSummaryHeader|  
|V2.3.1|CSU|C09|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C10|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C11|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C12|ORC_CommonOrderSegment|  
|V2.3.1|SUR|P09|PSH_ProductSummaryHeader<br />區段|  
|V2.4|CSU|C09|ORC_CommonOrder|  
|V2.4|CSU|C10|ORC_CommonOrder|  
|V2.4|CSU|C11|ORC_CommonOrder|  
|V2.4|CSU|C12|ORC_CommonOrder|  
|V2.4|OMD|O03|ORC_CommonOrder|  
|V2.4|ORD|O04|ORC_CommonOrder|  
|V2.4|SUR|P09|PSH_ProductSummaryHeader|  
|V2.5|CSU|C09|ORC_CommonOrder|  
|V2.5|CSU|C10|ORC_CommonOrder|  
|V2.5|CSU|C11|ORC_CommonOrder|  
|V2.5|CSU|C12|ORC_CommonOrder|  
|V2.5|OMD|O03|ORC_CommonOrder|  
|V2.5|ORD|O04|ORC_CommonOrder|  
|V2.5|SUR|P09|PSH_ProductSummaryHeader"|  
|V2.5|RDE|025|PSH_ProductSummaryHeader"|  
|V2.5|新增了對|R24|PSH_ProductSummaryHeader"|  
|V2.5|OML|035|PSH_ProductSummaryHeader"|  
|V2.5|ORL|034|PSH_ProductSummaryHeader"|  
  
> [!NOTE]
>  2.5 版的上述清單未全部列出，而且可能包含其他訊息類型，會導致 「 區段順序錯誤 」。  
  
## <a name="btahl7-does-not-support-some-v231-schemas"></a>BTAHL7 不支援某些 v2.3.1 結構描述  
 BTAHL7 安裝程式不會安裝下列 v2.3.1 結構描述：  
  
-   OMD_O01_231_GLO_DEF  
  
-   OMN_O01_231_GLO_DEF  
  
-   OMS_O01_231_GLO_DEF  
  
-   ORD_O02_231_GLO_DEF  
  
-   ORN_O02_231_GLO_DEF  
  
-   ORS_O02_231_GLO_DEF  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)