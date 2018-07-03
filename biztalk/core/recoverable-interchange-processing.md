---
title: 可復原交換處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interchange processing [Messaging Engine], modes
- parties, party resolution
- Messaging Engine, examples
- messages, interchange modes
- interchange processing [Messaging Engine], examples
- Messaging Engine, Recoverable Interchange Processing property
- Messaging Engine, failures
- interchange processing [Messaging Engine], party resolution
- Messaging Engine, interchange processing
- disassembly stage, pipelines
- Recoverable Interchange Processing property
- Messaging Engine, interchange modes
- receive pipelines, disassembly stage
- interchange processing [Messaging Engine], failures
- interchange processing [Messaging Engine], restrictions
- System.Xml.XmlReader
- interchange modes [Messaging Engine]
ms.assetid: d9e366fe-b2a0-4f1a-b6b9-1264717e4731
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdcd48efee84c1bd36df161180a5fe393f570a60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000879"
---
# <a name="recoverable-interchange-processing"></a>可復原交換處理
本章節將討論**可復原交換處理**功能，讓即使在下列階段失敗的交換中的一或多個訊息完全處理交換：  
  
- 接收管線的反組譯階段  
  
- 接收管線的 XML 驗證階段  
  
- 接收埠的對應執行階段  
  
  可復原交換處理是為支援成功處理包含多個可識別訊息的單一交換之需求所設計，因此有效的訊息可透過傳訊路徑傳播，而無效的訊息會被擱置。 使用標準交換處理時，若在指定交換中有任何無效的訊息，會導致整個交換被擱置，即使它包含一或多個有效訊息也一樣。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [解譯階段 (可復原交換處理)](../core/disassembly-stage-recoverable-interchange-processing.md)  
  
-   [XML 驗證階段 (可復原交換處理)](../core/xml-validation-stage-recoverable-interchange-processing.md)  
  
-   [對應階段 (可復原交換處理)](../core/mapping-phase-recoverable-interchange-processing.md)