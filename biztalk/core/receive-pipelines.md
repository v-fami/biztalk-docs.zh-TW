---
title: 接收管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive pipelines, about receive pipelines
- receive pipelines, message flow
- receive pipelines
- messages, receive pipelines
- messages, message flow
- pipelines, receive pipelines
- receive pipelines, stages
ms.assetid: ee75c1d4-00b7-4177-bca3-1447a39d2238
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a248c69cb96603e9c4883e5d21caa39165da13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268862"
---
# <a name="receive-pipelines"></a>接收管線
下圖顯示訊息處理工作流程，並以反白顯示接收管線。  
  
 ![訊息處理工作流程的圖表。] (../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")  
描述訊息處理工作流程。  
  
 在接收配接器收到訊息之後，接收管線會在訊息上作業。 接收管線取得初始訊息，執行部分轉換，然後將原始資料解譯成零個、一個或多個訊息。 然後，BizTalk Server 可以處理這些個別訊息。  
  
> [!NOTE]
>  若將耗用元件加入管線中，則接收管線可產生零個訊息。 此時，管線元件將取用訊息，而不會產生任何輸出訊息。 若耗用元件放在解譯元件之後，則管線會在取用第一個訊息之後停止執行，且不會從解譯元件擷取後續的訊息。  
  
 在建立商務程序時，您可以建立新接收管線，或使用 BizTalk Server 所包含的兩個預設接收管線之一：通過接收管線或 XML 接收管線。 如需有關這些預設管線的詳細資訊，請參閱[預設管線](../core/default-pipelines.md)。  
  
 接收管線包含四個階段：解碼、解譯、驗證以及解析合作對象。 此主題包含填入這些階段的設計考量。  
  
> [!NOTE]
>  在此版本中，不支援在管線中變更這些階段的順序或顯示。  
  
## <a name="decode-stage"></a>解碼階段  
  
-   此階段供解碼或解密訊息的元件使用。  
  
    -   若內送訊息需要從某一格式解碼成另一格式，則 [MIME/SMIME 解碼器] 管線元件或自訂解碼元件應放在此階段。  
  
-   此階段取得一個訊息，然後產生一個訊息。  
  
-   此階段可包含 0 至 255 個元件。  
  
-   此階段中的所有元件都可執行。  
  
## <a name="disassemble-stage"></a>解譯階段  
  
-   此階段供剖析或解譯訊息的元件使用。  
  
    -   此階段中的元件會探查訊息，以確認是否可辨識此訊息的格式。 根據格式的辨識結果，其中一個元件將解譯訊息。  
  
    -   若此階段包含一個以上的元件，則只會執行辨識出訊息的第一個元件。 若階段中沒有元件可辨識訊息格式，則訊息處理失敗。  
  
    -   此階段應包含實作特殊行為以解譯訊息內容的任一自訂元件。  
  
    -   此階段可包含 0 至 255 個元件。 若此階段中沒有元件，則訊息會直接通過。  
  
## <a name="validate-stage"></a>驗證階段  
  
-   此階段供驗證訊息格式的元件使用。  
  
    -   管線元件只處理符合該元件中指定的結構描述的訊息。 若管線接收到其結構描述與管線中任何元件都無關聯的訊息，則不會處理該訊息。 根據提交訊息的配接器的不同，訊息將被擱置或發出錯誤給寄件者。  
  
    -   此階段中的元件可用來驗證解譯階段所產生的 XML 訊息。 此階段中的元件會指定執行 XML 驗證的結構描述。  
  
-   此階段可包含 0 至 255 個元件。  
  
-   此階段中的所有元件都可執行。  
  
    -   此階段可執行一次以上。 它會為解譯階段所建立的每個訊息執行一次。  
  
## <a name="resolveparty-stage"></a>解析合作對象階段  
  
-   這個階段是預留位置[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。  
  
-   此階段可執行一次以上。 它會為解譯階段所建立的每個訊息執行一次。  
  
-   此階段可包含 0 至 255 個元件。  
  
-   此階段中的所有元件都可執行。  
  
## <a name="see-also"></a>另請參閱  
 [傳送管線](../core/send-pipelines.md)   
 [關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md)   
 [類型的管線元件](../core/types-of-pipeline-components.md)   
 [預設管線](../core/default-pipelines.md)   
 [管線範本](../core/pipeline-templates.md)   
 [管線元件](../core/pipeline-components.md)   
 [類型的管線](../core/types-of-pipelines.md)