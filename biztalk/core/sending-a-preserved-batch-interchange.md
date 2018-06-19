---
title: 傳送保留批次交換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9bc2207-e34d-4d06-a224-bd7f8e498c27
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5813bb4881535290422e2ba01d20d4370f4e604
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974844"
---
# <a name="sending-a-preserved-batch-interchange"></a>傳送保留的批次交換
當 EDI 傳送管線處理保留的輸出批次交換時，它會將該批次交換一起處理。 它通常會建立 EDI 交換，而不是套用信封根據協議中的現有信封 （控制項） 區段重複使用。 發生這種情況時**輸入批次處理選項**屬性設定為**保留交換-發生錯誤時暫停交換**或**保留交換-發生時暫停交易集錯誤**。  
  
## <a name="schema-validation"></a>結構描述驗證  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用批次結構描述和服務結構描述來驗證保留批次的信封。 批次結構描述可用來驗證保留訊息的根節點，而服務結構描述則用於驗證交換、群組，以及交易集標頭和結尾。 如需批次結構描述的詳細資訊，請參閱[EDI 批次結構描述](../core/edi-batch-schemas.md)。 如需有關服務結構描述的詳細資訊，請參閱[EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用專案中的文件結構描述來驗證批次交換中的文件。  
  
## <a name="send-side-processing"></a>傳送端處理  
 當 EDI 組合器處理保留交換時，它通常會使用收到批次交換時該批次中現有的相同交換、群組和交易集標頭。  
  
-   對於 X12 交換，在單向協議索引標籤中的不同頁面上的屬性設定**協議屬性**對話方塊 (用來決定如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會建立傳出的 ISA、 GS 和 ST 標頭交換） 通常不會套用。  
  
-   若是 EDIFACT 交換，通常會使用協議屬性中的 UNA 設定。 UNA 區段在 EDIFACT 編碼訊息中是選用項目，但在序列化保留的批次交換時是必要項目。 如果 XML 執行個體中的 UNA 區段沒有指定值，則會使用傳送管線元件的預設屬性值。 如果未指定傳送管線元件屬性的值，保留批次中繼 XML 訊息將會遭到擱置。  
  
-   如果您將要保留之交換上的 `EDI.PopulateInterchangeValues` 內容屬性升級為 "True" (使用自訂元件)，傳送埠中的 EdiAssembler 就會將設定在協議屬性中的值填入所有的交換、群組和交易集標頭。  
  
-   如果您在傳送管線處理 `EDIOverride.OverrideEdiHeader` 內容屬性之前，在交換上將它升級為 "True"，則可以透過設定適當的 `EDIOverride` 內容屬性值來覆寫輸出文件的信封值。 如需詳細資訊，請參閱[覆寫 EDI 標頭](../core/overriding-edi-headers.md)。  
  
 對於沒有錯誤的保留交換，組合器會保留交換群組中的交易集順序和交換中的群組順序。  
  
> [!NOTE]
>  您可以透過 XML 傳送管線來傳送保留批次。 不過，這時您必須修改該批次結構描述的命名空間。 如需詳細資訊，請參閱[透過 XML 傳送管線傳送保留批次](../core/sending-a-preserved-batch-with-an-xml-send-pipeline.md)。  
  
## <a name="error-processing"></a>錯誤處理  
 EDI 傳送管線會因為 XML 中的保留標記，而將批次 EDI 交換辨識為保留批次。 此標記，可能是\<X12InterchangeXml\>或\<EdifactInterchangeXml\>，套用至 XML 由 EDI 接收管線。  
  
 下列特殊案例適用於發生錯誤時擱置交易集的情況：  
  
-   如果群組中的所有交易集全都無效，EDI 傳送管線就會將群組控制區段包含到產生的 EDI 中，但該群組不會包含任何交易集 (因為已經捨棄)。 群組尾總計會更新為零。 交換控制區段則保持不變。  
  
-   如果交換中的所有交易集全都無效，交換控制區段仍然會包含在產生的 EDI 交換中，但該交換不會包含任何交易集 (因為已經捨棄)。 這會構成空白交換。  
  
-   如果群組控制區段或交換控制區段無效，就不會產生 EDI 編碼交換。 事件檢視器中將會建立記錄檔，表示該次交換已遭拒絕。  
  
## <a name="see-also"></a>請參閱  
 [批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)