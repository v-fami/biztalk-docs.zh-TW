---
title: 結構描述的已知問題 |Microsoft 文件
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
ms.openlocfilehash: 0568a892559ea119b9a198368b4521cbe49ddf45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207958"
---
# <a name="schema-known-issues"></a>結構描述的已知問題
本節包含可協助您避免結構描述錯誤的有用資訊。  
  
## <a name="mcf21glodefxsd-schema"></a>MCF_21_GLO_DEF.xsd 結構描述  
 在 templates\schemas\2.1 資料夾中，結構描述 MCF_21_GLO_DEF.xsd 不 Common231 專案的一部分。  
  
## <a name="miscellaneous-errors-can-result-from-undeployed-schemas"></a>發生其他錯誤可能是因為在解除部署結構描述  
 如果您是無法識別中剖析或序列化的錯誤，請確認您已部署的屬性結構描述和常見的結構描述 （MSH/通知）。 解除部署的屬性結構描述和通用的結構描述可能會導致發生其他錯誤。  
  
## <a name="if-the-starter-project-is-installed-but-the-hl7-2x-schemas-are-not-installed-running-the-schema-wizard-generates-an-error"></a>如果已安裝的入門專案，但 HL7 2.X 結構描述不會安裝，執行結構描述精靈會產生錯誤  
 如果您執行自訂安裝的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 中哪些安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]入門專案，但不是安裝 HL7 2.X 結構描述，並嘗試執行結構描述 精靈中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生發生錯誤。 這是重新執行自訂安裝程序，以安裝 HL7 2.X 結構描述。  
  
## <a name="msh91-enumeration-list-needs-to-be-updated"></a>MSH9.1 列舉清單需要更新  
 所安裝的 MSH_25_GLO_DEF 結構描述[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]在安裝時不包含完整列舉清單 MSH9.1 (MessageType) 和 MSH9.2 (EventTrigger)，如 HL72 中所包含。X 標準。 下表列出訊息類型和觸發程序事件的值，您必須新增至其相關聯的資料表，如果您想要使用結構描述的訊息型別包含的值。 比方說，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會處理 QBP ^ Z99 訊息直到 Table76 MSH_25_GLO_DEF 中的列舉型別中加入"QBP"並不會處理 QBP ^ Z99 訊息，直到您將 「 Z99"新增至 Table3 MSH_25_GLO_DEF 中的列舉。  
  
 若要將值加入到 MSH9.1 或 MSH9.2 列舉型別，請參閱中的 < 若要將列舉值新增到訊息標頭結構描述 > 程序[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。  
  
|欄位/資料表|要加入至列舉值|  
|------------------|--------------------------------------|  
|MessageType/Table76|ARD，RDO，RRO|  
|TriggerEvent/Table3|K11、 K13、 K15、 MFA、 O22、 Q11、 Q13、 Q15、 Q26、 Q27、 Q28、 Q29、 R0R、 Z73、 Z74、 Z75、 Z76、 Z77、 Z78、 Z79、 Z80、 Z81、 Z82、 Z83、 Z84、 Z85、 Z86、 Z87、 Z88、 Z89、 Z90、 Z91、 Z92、 Z93、 Z94、 Z95、 Z96、 Z97、 Z98、 Z99|  
|MessageStructure/Table354|ARD_A19 ORL_O22|  
  
## <a name="btahl7-does-not-support-schemas-with-an-ambiguous-structure"></a>BTAHL7 不支援結構描述具有模稜兩可的結構  
 BTAHL7 引擎無法處理訊息執行個體符合 HL7 結構描述模稜兩可的結構。 模稜兩可的結構描述結構是不完全由 HL7 標準定義。 這類結構描述包括 CSU、 OMD、 ORD 和 SUR.的訊息類型  
  
## <a name="btahl7-will-return-a-segment-sequence-error-for-some-messages"></a>BTAHL7 會傳回某些訊息區段順序錯誤  
 BTAHL7 無法處理符合下面所列的結構描述的訊息。 這些訊息本文的剖析將會失敗，導致下列錯誤: 「 區段順序錯誤 （無效的區段找到此區段之後） 」。 以下列出受影響的區段識別碼的訊息中。 所有這些錯誤的受影響的順序號碼為"2"。  
  
|Version|訊息類型|觸發程序事件|區段識別碼|  
|-------------|------------------|-------------------|----------------|  
|V2.3|CSU|C09|ORC_CommonOrderSegment|  
|V2.3|CSU|C10|ORC_CommonOrderSegment|  
|V2.3|CSU|C11|ORC_CommonOrderSegment|  
|V2.3|CSU|C12|ORC_CommonOrderSegment|  
|V2.3|南下|P09|PSH_ProductSummaryHeader|  
|V2.3.1|CSU|C09|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C10|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C11|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C12|ORC_CommonOrderSegment|  
|V2.3.1|南下|P09|PSH_ProductSummaryHeader<br />區段|  
|V2.4|CSU|C09|ORC_CommonOrder|  
|V2.4|CSU|C10|ORC_CommonOrder|  
|V2.4|CSU|C11|ORC_CommonOrder|  
|V2.4|CSU|C12|ORC_CommonOrder|  
|V2.4|OMD|O03|ORC_CommonOrder|  
|V2.4|ORD|O04|ORC_CommonOrder|  
|V2.4|南下|P09|PSH_ProductSummaryHeader|  
|2.5 版|CSU|C09|ORC_CommonOrder|  
|2.5 版|CSU|C10|ORC_CommonOrder|  
|2.5 版|CSU|C11|ORC_CommonOrder|  
|2.5 版|CSU|C12|ORC_CommonOrder|  
|2.5 版|OMD|O03|ORC_CommonOrder|  
|2.5 版|ORD|O04|ORC_CommonOrder|  
|2.5 版|南下|P09|PSH_ProductSummaryHeader"|  
|2.5 版|RDE|025|PSH_ProductSummaryHeader"|  
|2.5 版|OUL|R24|PSH_ProductSummaryHeader"|  
|2.5 版|OML|035|PSH_ProductSummaryHeader"|  
|2.5 版|ORL|034|PSH_ProductSummaryHeader"|  
  
> [!NOTE]
>  2.5 版的上述清單並非完整清單，而且可能包括額外的訊息類型導致 「 區段順序錯誤 」。  
  
## <a name="btahl7-does-not-support-some-v231-schemas"></a>BTAHL7 不支援部分 v2.3.1 結構描述  
 BTAHL7 安裝程式不會安裝下列 v2.3.1 結構描述：  
  
-   OMD_O01_231_GLO_DEF  
  
-   OMN_O01_231_GLO_DEF  
  
-   OMS_O01_231_GLO_DEF  
  
-   ORD_O02_231_GLO_DEF  
  
-   ORN_O02_231_GLO_DEF  
  
-   ORS_O02_231_GLO_DEF  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)