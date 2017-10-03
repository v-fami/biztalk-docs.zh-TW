---
title: "管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines
- deploying, pipelines
- receive pipelines, about receive pipelines
- pipelines, deploying
- send pipelines, about send pipelines
- receive pipelines
- pipelines, about pipelines
- send pipelines, stages
- send pipelines
- pipelines, receive pipelines
- pipelines, send pipelines
- receive pipelines, stages
ms.assetid: 76947dd8-728a-4fa3-bd33-7a708ae82cac
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5fec49dcc9ba21c5d117188f280f7e9b65fe2b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pipelines"></a>管線
管線是 Microsoft BizTalk Server 的一個元件，可實作「管線」和「篩選條件」整合模式。 基於商務因素，在接收和傳送訊息期間，會對訊息執行轉換以準備進入或離開 BizTalk Server。  
  
 常見範例是您需要將逗號分隔的一般檔案轉換成 XML 檔，才能利用 BizTalk Server 的特定功能，像是對應；一般檔案解譯器元件就是以此方式執行。 在接收或傳送訊息之前，需要對訊息執行數種轉換的情況，在整合實例中很常見；而管線可用以滿足此項需求。 開發人員可以使用管線定義一系列轉換，以在接收或傳送訊息時執行。  
  
 管線有傳送和接收兩種類型，而且與它們執行所在的連接埠相符。 *傳送管線*執行在傳送埠和要求/回應的回應部分中接收埠，而*接收管線*執行在接收位置和請求/回應的回應部分中傳送埠。 基本上，接收管線是用於轉換要發佈到 MessageBox 資料庫的訊息，而傳送管線是用於已訂閱和要送出 BizTalk Server 的訊息。  
  
 每個管線執行時，都會依序執行數個階段。 每一個階段可以包含零或多個元件。 元件數目的上限依據各個階段而定。  
  
## <a name="receive-pipeline-stages"></a>接收管線階段  
 ![接收管線階段](../core/media/arch-pipe-receive.gif "arch_pipe_receive")  
  
|階段|目的|  
|-----------|-------------|  
|**解碼**|將訊息資料解密或解碼|  
|**反組譯**|將交換解譯為較小的訊息並剖析訊息內容|  
|**Validate**|通常會針對結構描述驗證訊息資料|  
|**解析合作對象**|識別與訊息或訊息內容中某個安全性 Token 相關聯的 BizTalk Server 合作對象|  
  
## <a name="send-pipeline-stages"></a>傳送管線階段  
 ![傳送管線階段](../core/media/arch-pipe-send.gif "arch_pipe_send")  
  
|階段|目的|  
|-----------|-------------|  
|**預先組合**|在組合訊息之前執行任何必要的訊息處理|  
|**組合**|組合訊息並採取步驟以準備傳送訊息，例如加上信封、將 XML 轉換成一般檔案，或可與接收管線的解譯階段互補的其他工作。|  
|**編碼**|在傳遞之前將訊息編碼或加密|  
  
 在管線階段會有*執行模式*「 全部或第一個相符項目，以控制如果多個元件新增至階段執行的元件。 對於「全部」模式的階段，會呼叫每個元件以階段中設定的順序來處理訊息。 當模式為「第一個符合」時，會輪詢每個元件以指示其是否為正確的元件，直到找到相符的為止，而當下也會執行該相符元件，而不會執行其餘元件。  
  
 例如此執行模式範例，接收管線的「解譯」階段為「第一個符合」階段，因此會呼叫階段中的每個元件，以查看是否能辨識該訊息並加以處理。 若某個元件正面回應，便不會再查詢該階段內的其他元件是否也能處理該訊息。 但接收管線的「解碼」階段為「全部」執行模式時，表示會以設定的順序呼叫此階段中的每個元件來處理訊息。 第一個解碼器可能用來加密訊息，而第二個可能將訊息從壓縮的格式解壓縮。  
  
 開發人員想要在單一接收管線中使用多個解譯器時，一般會在管線處理中使用執行模式。 解譯元件通常只有些許不同，例如，兩個類似但結構描述設定不同的一般檔案解譯器。 在這種情況下，雖然訊息實際上可能會與第二個解譯器中定義的結構描述相符，但第一個解譯器則要透過探查來判定是否能夠處理該訊息。 只有在處理訊息之後，才能找出錯誤和擱置訊息。 在這些情況下，您可能會建立探查邏輯更為明確的新解譯器，或是建立兩個不同的管線，並在不同的接收位置接收不同的訊息。  
  
## <a name="pipeline-deployment"></a>管線部署  
 部署包含管線的組件時，管理資料庫會儲存管線。 管線與特定組件版本產生關聯的結果如下：  
  
-   若部署使用相同管線的多個組件，管理資料庫會為每個組件的管線各建立一個項目。  
  
-   移除包含管線的組件時，管理資料庫會同時移除與該組件相關聯的管線。 因為管理資料庫中有每個相關聯組件的管線複本，所以移除一個組件不會影響其他組件。  
  
## <a name="see-also"></a>另請參閱  
 [成品](../core/artifacts.md)