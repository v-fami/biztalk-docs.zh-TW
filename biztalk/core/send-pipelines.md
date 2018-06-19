---
title: 傳送管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send pipelines, message flow
- send pipelines, about send pipelines
- messages, message flow
- send pipelines, stages
- pipelines, send pipelines
- messages, send pipelines
ms.assetid: c963b2d8-3b2b-4575-8105-c750deae8189
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef08909dbc47e11f5c9fecae6f65e01dbe79441b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270174"
---
# <a name="send-pipelines"></a>傳送管線
下圖顯示訊息處理工作流程，其中會反白傳送管線。  
  
 ![為處理訊息的工作流程的圖表。] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")  
描述訊息處理工作流程。  
  
 傳送管線的責任是必須在傳送文件到最終目的地前先處理文件。 傳送管線會先取得訊息，然後產生要傳送的訊息。  
  
 您可以建立新的傳送管線，或者使用 BizTalk Server 中的兩個預設傳送管線的其中一個—通過傳送管線和 XML 傳送管線。  
  
 依照預設，傳送管線包含三個空白階段：預先組合、組合和編碼。 此主題包含填入這些階段的設計考量。  
  
> [!NOTE]
>  當耗用元件新增到某傳送管線時，該傳送管線不會產生訊息。  
  
## <a name="pre-assemble-stage"></a>預先組合階段  
  
-   在訊息經序列化之前，有一些自訂元件必須對訊息執行某些動作，而這個階段就是那些自訂元件的預留位置。  
  
-   每個訊息都會執行一次這個階段。  
  
-   此階段可包含 0 至 255 個元件。  
  
-   此階段中的所有元件都可執行。  
  
## <a name="assemble-stage"></a>組合階段  
  
-   此階段之元件的責任是對訊息進行組合或序列化，然後將其轉換為 XML 或從 XML 格式轉換回來。  
  
-   此階段不接受任何元件或只接受一個元件。  
  
-   此階段中的所有元件都可執行。  
  
## <a name="encode-stage"></a>編碼階段  
  
-   此階段用於對訊息進行編碼或加密的元件。  
  
    -   若需要訊息簽章，請將 MIME/SMIME 編碼器元件或自訂編碼元件放入此階段。  
  
-   每個訊息都會執行一次這個階段。  
  
-   此階段可包含 0 至 255 個元件。  
  
-   此階段中的所有元件都可執行。  
  
## <a name="see-also"></a>另請參閱  
 [接收管線](../core/receive-pipelines.md)   
 [關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md)   
 [類型的管線](../core/types-of-pipelines.md)   
 [預設管線](../core/default-pipelines.md)   
 [管線範本](../core/pipeline-templates.md)   
 [管線元件](../core/pipeline-components.md)   
 [類型的管線元件](../core/types-of-pipeline-components.md)