---
title: 類型的管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, components
ms.assetid: 9b493758-6b0f-4223-94bb-8f077ee735a9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9ba18aed137380f6b3d491ad52cfcee94bf111a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-pipeline-components"></a>類型的管線元件
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含三種管線元件類型：一般、組合和解譯。 這三種類型也能實作探查功能。 此主題描述每種元件類型以及通常會使用各個元件的階段。  
  
## <a name="general"></a>一般  
 一般元件會取得一個訊息、處理該訊息，然後產生零或一個訊息。  
  
 一般元件包含 MIME/SMIME 解碼器、MIME/SMIME 編碼器、合作對象解析以及驗證器元件。 您可能必須在傳送之前建立自訂的一般元件以壓縮訊息大小，或是在等待其他資訊以處理訊息時使用該訊息。  
  
 一般元件應置於解碼、編碼、預先組合、合作對象解析與驗證階段。  
  
 如需開發一般管線元件的詳細資訊，請參閱[開發一般管線元件](../core/developing-a-general-pipeline-component.md)。  
  
## <a name="assembling"></a>組合  
 組合元件負責多項責任以準備要傳送的訊息。 首先，元件會根據結構描述中設定的組合器與屬性，將 XML 訊息轉換成適當的 XML 或非 XML 原生格式訊息。 此外，組合元件還會組合和包裝信封中的訊息，或將標頭或結尾 (或兩者) 新增至訊息。 在組合期間，部分屬性會從訊息內容移至文件內文或信封。  
  
 BizTalk Framework 組合器、一般檔案組合器以及 XML 組合器元件都是預設的組合元件。  
  
 組合元件應置於傳送管線的組合階段。  
  
 如需開發組合管線元件的詳細資訊，請參閱[開發組合管線元件](../core/developing-an-assembling-pipeline-component.md)。  
  
## <a name="disassembling"></a>解譯  
 解譯元件會根據要在 BizTalk Server 內使用的信封與文件結構描述，完成許多工作以準備將訊息分割成個別的文件。 首先，解譯元件可將非 XML 訊息轉換成 XML 表示法，這是供 BizTalk Server 處理的必要條件。 接下來，會將訊息解譯為可傳送給不同協調流程的單一訊息。 解譯訊息是藉由移除信封、根據信封及訊息結構描述將訊息分割成個別文件，然後將屬性從信封移至個別訊息內容。 此外，部分屬性可能會從訊息內文升級成標頭。 升級的屬性是由結構描述所決定。  
  
 解譯元件還必須設定訊息類型屬性，以便用於適當地路由訊息。 訊息類型屬性是訊息內文的 Namespace#RootElement。 其他屬性如內容類型與字元集等都會設為內容屬性的一部分。  
  
 BizTalk Framework 解譯器 」、 「 一般檔案解譯器 」 和 「 XML 解譯器元件會解譯元件隨附於 BizTalk Server 的預設值。  
  
 解譯元件應該用於接收管線的解譯階段。  
  
 如需開發解譯管線元件的詳細資訊，請參閱[開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)。  
  
## <a name="probing"></a>探查  
 探查元件會檢查訊息的第一個部分，查看它是否使用元件可辨識的格式。 若為已知的格式，則會將整個訊息傳送給此元件進行處理。  
  
 如需有關開發探查管線元件，請參閱[開發探查管線元件](../core/developing-a-probing-pipeline-component.md)。  
  
## <a name="see-also"></a>另請參閱  
 [類型的管線](../core/types-of-pipelines.md)   
 [預設管線](../core/default-pipelines.md)   
 [管線範本](../core/pipeline-templates.md)   
 [管線元件](../core/pipeline-components.md)   
 [關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md)