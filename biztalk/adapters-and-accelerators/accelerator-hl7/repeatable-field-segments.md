---
title: "可重複的欄位區段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- segments, repeatable fields
- QPD
- Table Row Data (RDT)
- Query Parameter Definition (QPD)
- Segments table
- RDT
ms.assetid: 4c31cb56-21e5-4918-aaf6-67e8ceddd74f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a801e39fac0e0bdf0cfb9ee88811703fd1c4373d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="repeatable-field-segments"></a>可重複的欄位區段
HL7 Access 資料庫中的區段資料表包含資料行區段 （ADD、 RDT 和 QPD） 的最後一個欄位， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 定義為可重複 (**Last_field_repeatable**  = **True**)。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不支援新增。 不過，RDT 和 QPD 出現查詢資料表，並以資料表值的回應。 下列範例將示範如何[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理這些資料行。  
  
 用戶端送出下列查詢，並指出用戶端想立即回應，藉由設定**RCP-1-回應優先順序**至 「**我**":  
  
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
  
 此範例中，從您看到 QPD 和 RDT 所定義的自訂/站台。 HL7 規格會定義 QPD 和 RDT 區段，如下所示。  
  
## <a name="qpd---query-parameter-definition"></a>QPD-查詢參數定義  
 下表顯示如何 HL7 規格定義 QPD。  
  
|SEQ|LEN|DT|選擇加入|RP / #|TBL #|項目 #|項目名稱|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1|250|CE|R||0471|01375|訊息查詢名稱|  
|2|32|ST|C|||00696|查詢標記|  
|3-n|256|非固定||||01435|使用者在後續的欄位中的參數|  
  
## <a name="rdt---table-row-data"></a>RDT-資料表的資料列資料  
 下表顯示如何 HL7 規格定義 RDT。  
  
|SEQ|LEN|DT|選擇加入|RP / #|TBL #|項目 #|項目名稱|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1-n|變數|變數|R|||00703|資料行值|  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]解譯 QPD 和 RDT 做為可重複的站台定義值。 因為[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不能解決問題的資料類型和其他詳細資料， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] QPD.3 和 RDT.1 視為字串的結構描述中的資料類型。 您可能必須修改這些結構描述，依據您的站台的條件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)