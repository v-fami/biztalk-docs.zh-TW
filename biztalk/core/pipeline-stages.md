---
title: "管線階段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- CATID_AssemblingSerializer component category
- CATID_Encoder component category
- pipelines, stages
- CATID_DisassemblingParser component category
- CATID_Validate component category
- ComponentCategory class attribute
- CATID_Decoder component category
- CATID_Any component category
- CATID_PartyResolver component category
- Execution Mode property
ms.assetid: ac50c48c-6ed5-4322-95cc-af55df6bcd1c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aeb675f39cb39ade4230e6e39f798e95115aaf78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pipeline-stages"></a>管線階段
本主題討論**執行模式**屬性和階段相似性。  
  
## <a name="execution-mode-property"></a>Execution Mode 屬性  
 在管線的執行期間，管線階段只能執行第一個辨識出訊息格式的元件，不然就是執行所有的元件。 決定執行模式的屬性是**執行模式**。  
  
> [!NOTE]
>  這個屬性在管線範本的階段中為唯讀，但是對它的運作方式進行瞭解是相當重要的。  
  
 當**執行模式**屬性設定為**所有**，執行階段內的所有元件中設定的順序。 此模式會執行數個元件來完成邏輯工作。 在此例中，若任何元件在管線階段中處理訊息時發生錯誤，就會產生執行階段錯誤。  
  
 當管線用來接收訊息數種格式，然後在**執行模式**屬性設定為**FirstMatch**。 在此模式中，只會執行第一個辨識出訊息的元件。 若階段中沒有任何元件辨識出此訊息，則會發生執行階段錯誤。  
  
 請注意，每個階段可以有它自己**執行模式**管線內的設定，因此不同階段可以有不同的執行模式。  
  
> [!NOTE]
>  在這一版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 在傳送中的所有階段都管線和接收都管線中的除了 「 解譯 」 階段中具有的值**執行模式**屬性設定為**所有**。 值**執行模式**「 解譯 」 階段的屬性設定為**FirstMatch**。 您無法變更**執行模式**階段的屬性。  
  
#### <a name="to-read-pipeline-stage-properties"></a>讀取管線階段屬性  
  
1.  在「管線設計師」中按一下階段圖形。  
  
2.  在 [屬性] 視窗中**一般**區段中，讀取下列屬性：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|表示階段的名稱。|  
    |**執行模式**|表示階段的執行模式。<br /><br /> 有效值：**所有**或**FirstMatch**|  
    |**元件的最小數目**|表示能夠新增至階段之管線元件的最小數目。|  
    |**元件的最大數目**|表示能夠新增至階段之管線元件的最大數目。|  
    |**StageID**|表示階段的唯一識別項。|  
  
## <a name="stage-affinity"></a>階段相似性  
 管線元件擁有階段相似性，這表示建立它們的目的是為了在管線的某個或某些特定階段中使用。  
  
 以 COM 為基礎的管線元件來註冊自己以階段 ID 作為實作類別，表示對於階段相似性時。以網路為基礎的管線元件會使用指定階段相似性**ComponentCategory**類別屬性。 請注意，它可能元件將本身與多個階段產生關聯 — 元件可以有一個以上的實作類別或**ComponentCategory**屬性。  
  
 下表顯示可用的元件類別和其關聯階段。  
  
|元件類別|可放置元件的階段|Description|  
|------------------------|-----------------------------------------|-----------------|  
|CATID_Decoder {9d0e4103-4cce-4536-83fa-4a5040674ad6}|解碼|所有的解碼元件都必須實作此類別。|  
|CATID_DisassemblingParser {9d0e4105-4cce-4536-83fa-4a5040674ad6}|Disassemble|所有的解譯和剖析元件都必須實作此類別。|  
|CATID_Validate {9d0e410d-4cce-4536-83fa-4a5040674ad6}|Validate|驗證元件都必須實作此類別。|  
|CATID_PartyResolver {9d0e410e-4cce-4536-83fa-4a5040674ad6}|ResolveParty|「合作對象解析」元件使用的階段。|  
|CATID_Encoder {9d0e4108-4cce-4536-83fa-4a5040674ad6}|編碼|所有的編碼元件都必須實作此類別。|  
|CATID_AssemblingSerializer {9d0e4107-4cce-4536-83fa-4a5040674ad6}|序列化|所有的序列化和組合元件都必須實作此類別。|  
|CATID_Any {9d0e4101-4cce-4536-83fa-4a5040674ad6}|任一階段|若某個管線元件實作此類別，則表示該元件可以放入管線的任一階段中。|  
  
## <a name="see-also"></a>另請參閱  
 [建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md)   
 [關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md)