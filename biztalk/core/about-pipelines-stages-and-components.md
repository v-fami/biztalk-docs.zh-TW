---
title: "關於管線、 階段和元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Microsoft.BizTalk.Component.Interop namespace
- pipelines, about pipelines
ms.assetid: a98e1c93-f264-4577-bd12-4430a5859e3c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 070c785924021f8e398a547c01afe969fa6430cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-pipelines-stages-and-components"></a>關於管線、階段和元件
管線是軟體基礎結構的一部分，其中包含的 .NET 或 COM 元件組可根據預先定義的順序來處理訊息。 管線會將處理程序分割成數個工作類別，稱之為階段，然後決定這些階段的執行順序。 各個階段都會定義邏輯工作群組、決定將於階段中使用的元件，然後指定管線元件在階段中的執行方式。  
  
 在各個階段中，管線元件都會執行特定的工作。 例如，接收管線階段中的元件可以解碼、解譯，然後將文件從其他的格式轉換為 XML。 傳送管線的工作剛好相反：這個工作會將文件從 XML 轉換為其他格式，並進行組合和加密；每個管線元件都負責執行整個程序中的部分工作。 雖然階段是數個元件的容器，但是各階段本身都是一個附有中繼資料的元件。 階段沒有執行碼；相反地，管線元件則有執行碼。  
  
 下圖顯示管線設計介面的管線說明。 此管線有兩個階段：「組合」階段和「編碼」階段。 XML 組合器管線元件已加入至 「 組合 」 階段，但 「 編碼 」 階段仍為空白，因為它仍顯示**放置到此處 ！** 表示管線元件，可以新增至階段。  
  
 ![階段與 BizTalk 管線中的元件](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")  
說明 BizTalk 管線中的階段和元件。  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含一組管線範本、管線元件和預設管線。 您可以建立並使用管線設計師使用者介面; 設定管線使用中的 API 實作管線**Microsoft.BizTalk.Component.Interop**命名空間。 您無法修改管線範本。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [類型的管線](../core/types-of-pipelines.md)  
  
-   [類型的管線元件](../core/types-of-pipeline-components.md)  
  
-   [管線階段](../core/pipeline-stages.md)  
  
-   [預設管線](../core/default-pipelines.md)  
  
-   [管線範本](../core/pipeline-templates.md)  
  
-   [管線元件](../core/pipeline-components.md)  
  
-   [管線元件中的結構描述解析](../core/schema-resolution-in-pipeline-components.md)  
  
-   [XML 組合器和解譯器管線元件中使用的信封](../core/envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components.md)  
  
-   [組合器管線元件中的屬性降級](../core/property-demotion-in-assembler-pipeline-components.md)  
  
-   [解譯器管線元件中的屬性升級](../core/property-promotion-in-disassembler-pipeline-components.md)  
  
-   [辨別的欄位在解譯器管線元件](../core/distinguished-fields-in-disassembler-pipeline-components.md)