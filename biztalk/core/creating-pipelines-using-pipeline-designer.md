---
title: 使用管線設計師建立管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, processing messages
- pipelines, Pipeline Designer
- Pipeline Designer, about Pipeline Designer
ms.assetid: 858302d8-a912-4199-95e5-4322db789b4e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62e182440522e82f7ae6eaeaf52234161bee7483
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998607"
---
# <a name="creating-pipelines-using-pipeline-designer"></a>使用管線設計師建立管線
Microsoft BizTalk Server 主要處理 XML 文件格式。 為能充分利用 BizTalk Server 處理優點，必須經常將訊息由其原生格式轉換為 XML 表示法。 BizTalk Server 管線會針對內送與外寄訊息執行此轉換，以及其他資料特定動作 (例如，資料加密或解密、屬性升級等)。 本節提供關於管線和「管線設計師」的概念性和工作特定資訊。  
  
 管線的目的是在配接器收到訊息之後準備訊息以供伺服器處理，或是在伺服器處理之後準備訊息以供傳送。  
  
 管線通常執行的作業：  
  
- 將各種格式資料正規化為 XML。  
  
- 將 XML 資料轉換為各種格式。  
  
- 屬性升級和降級。  
  
- 文件解譯和組合。  
  
- 文件解碼和編碼。  
  
- 文件解密和加密。  
  
- 文件簽章和數位簽章驗證。  
  
  下圖顯示使用管線處理訊息所需的工作流程。  
  
  ![處理訊息的工作流程的圖表。] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")  
  描述訊息處理工作流程。  
  
  如圖所示，訊息從配接器傳送到接收管線，在此轉換為 XML。 然後訊息可供協調流程使用，或傳遞到傳送管線，然後到達傳送配接器。  
  
  如需使用管線設計師鍵盤快速鍵的詳細資訊，請參閱[管線設計師鍵盤快速鍵](../core/pipeline-designer-keyboard-shortcuts.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [關於管線、階段和元件](../core/about-pipelines-stages-and-components.md)  
  
-   [使用管線設計師](../core/using-pipeline-designer.md)  
  
-   [使用管線設計師建立管線](../core/creating-pipelines-with-pipeline-designer.md)  
  
-   [設定原生管線元件](../core/configuring-native-pipeline-components.md)  
  
-   [如何部署管線](../core/how-to-deploy-pipelines.md)  
  
-   [如何保護管線](../core/how-to-secure-pipelines.md)