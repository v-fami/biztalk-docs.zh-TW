---
title: 可重複的欄位區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- segments, repeatable fields
- QPD
- Table Row Data (RDT)
- Query Parameter Definition (QPD)
- Segments table
- RDT
ms.assetid: 4c31cb56-21e5-4918-aaf6-67e8ceddd74f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9651b8d3414f792b81633cafbe41dd66559df04c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981975"
---
# <a name="repeatable-field-segments"></a>可重複的欄位區段
HL7 Access 資料庫中的區段資料表包含資料行的區段 （ADD、 RDT 和 QPD） 和最後一個欄位，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會定義為可重複 (**Last_field_repeatable**  =  **，則為 true**)。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 不支援新增。 不過，同時 RDT QPD 有查詢資料表並以資料表值的回應。 下列範例會示範如何[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理這些資料行。  
  
 在用戶端提交下列查詢，與指出用戶端設定需要立即回應**RCP-1-回應的優先順序**到 「**我**」:  
  
```  
MSH|^&~\|PCR|Gen Hosp|PIMS||199811201400-0800||QBP^Q42^QBP_Q13|ACK9901|P|2.4||||||||  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR| |19980531|19990531|  
RCP|I|999^RD|  
RDF|3|PatientList^ST^20~PatientName^XPN^48~MedicationDispensed^ST^40~RXD.3^TS^26  
```  
  
 伺服器會回應一分鐘之後出現下列訊息：  
  
```  
MSH|^&~\|PIMS|Gen Hosp|PCR||199811201401-0800||RTB^K42^RTB_K13|8858|P|2.3||||||||  
MSA|AA|8699|  
QAK|Q010|OK|Q42^Tabular Dispense History^HL7nnn|4  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR||19980531|19990531|  
RDF|7|PatientId^CX^20~PatientName^XPN^48~OrderControlCode^ID^2~ MedicationDispensed^CE^100~DispenseDate^TS^26~QuantityDispensed^NM^20~ OrderingProvider^XCN^120  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|525440345^Verapamil Hydrochloride 120 mg TAB^NDC |199805291115-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00182196901^VERAPAMIL HCL ER TAB 180MG ER^NDC |19980821-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00172409660^BACLOFEN 10MG TABS^NDC |199809221415-0700|10|88^Semmelweis^Samuel^^^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00054384163^THEOPHYLLINE 80MG/15ML SOLN^NDC|199810121145-0700|10|99^Lister^Lenora^^^DR^MD  
```  
  
 從範例中，您會看到 QPD 和 RDT 所定義的自訂/站台。 HL7 規格會定義 QPD 和 RDT 區段，如下所示。  
  
## <a name="qpd---query-parameter-definition"></a>QPD-查詢參數定義  
 下表顯示如何 HL7 規格定義 QPD。  
  
|SEQ|LEN|DT|選擇加入|RP / #|TBL #|項目 #|項目名稱|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|@shouldalert|250|CE|R||0471|01375|訊息查詢名稱|  
|2|32|ST|c|||00696|查詢標記|  
|3-n|256|非固定||||01435|在後續的欄位中的使用者參數|  
  
## <a name="rdt---table-row-data"></a>RDT-資料表資料列資料  
 下表顯示如何 HL7 規格定義 RDT。  
  
|SEQ|LEN|DT|選擇加入|RP / #|TBL #|項目 #|項目名稱|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1-n|變數|變數|R|||00703|資料行值|  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] QPD 和 RDT 解譯可以重複的網站定義值。 由於[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不能解決問題的資料類型和其他詳細資料， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] QPD.3 和 RDT.1 視為字串的結構描述中的資料類型。 您可能要修改這些結構描述，根據您自己的站台條件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)