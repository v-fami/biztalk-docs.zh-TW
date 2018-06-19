---
title: Microsoft.BizTalk.DefaultPipelines 參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines
- PassThruTransmit pipelines
- XMLReceive pipelines
- pipelines, XMLTransmit
- Pipeline Designer
- pipelines, XMLReceive
- pipelines, about pipelines
- PassThruReceive pipelines
- XMLTransmit pipelines
- namespaces, Microsoft.BizTalk.DefaultPipelines namespace
- Microsoft.BizTalk.DefaultPipelines namespace
ms.assetid: a54f8813-9c6f-4afe-8c76-2db3fa478947
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ad7cad78e3e8606371a5fa49673297cf590ddbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263406"
---
# <a name="microsoftbiztalkdefaultpipelines-reference"></a>Microsoft.BizTalk.DefaultPipelines 參考
**Microsoft.BizTalk.DefaultPipelines**命名空間包含下列管線：  
  
-   XMLReceive  
  
-   PassThruReceive  
  
-   XMLTransmit  
  
-   PassThruTransmit  
  
 管線是一種軟體元件，可定義和連結處理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所接收或傳送之訊息的一或多個階段。 這些階段包括諸如編碼或解碼、組譯或反組譯以及加密或解密等函式。 這些功能會以特定的順序進行實作。 您可以使用「管線設計師」來建立傳送管線和接收管線。  
  
 包含在 BizTalk 專案中的預設管線參考能夠處理所有類型的文件使用**PassThruReceive**和**PassThruTransmit**管線。  
  
 下列清單列出了預設管線中的預設元件。 這些清單也會指出各管線中元件的預設順序。 如有需要，您可以新增或刪除元件。  
  
 預設 XMLReceive 管線中的預設元件為：  
  
-   解密器  
  
-   解碼器  
  
-   解譯器  
  
-   驗證器  
  
-   合作對象解析  
  
 預設 XMLTransmit 管線中的預設元件為：  
  
-   組合器  
  
-   編碼器  
  
-   加密器  
  
## <a name="see-also"></a>另請參閱  
 [建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md)   
 [關於在 BizTalk 專案中包含的 BizTalk 命名空間參考](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)