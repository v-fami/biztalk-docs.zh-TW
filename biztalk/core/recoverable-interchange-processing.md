---
title: "可復原交換處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b341b3673cd7118d459197fecea1eca25efe4e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="recoverable-interchange-processing"></a><span data-ttu-id="98870-102">可復原交換處理</span><span class="sxs-lookup"><span data-stu-id="98870-102">Recoverable Interchange Processing</span></span>
<span data-ttu-id="98870-103">本章節將討論**可復原交換處理**功能，讓即使在下列階段/階段失敗的交換中的一個或多個訊息完全處理交換：</span><span class="sxs-lookup"><span data-stu-id="98870-103">This section discusses **recoverable interchange processing** feature, which allows an interchange to be processed completely even if one or more messages in the interchange fail at the following stages/phases:</span></span>  
  
-   <span data-ttu-id="98870-104">接收管線的反組譯階段</span><span class="sxs-lookup"><span data-stu-id="98870-104">Disassembly stage of a receive pipeline</span></span>  
  
-   <span data-ttu-id="98870-105">接收管線的 XML 驗證階段</span><span class="sxs-lookup"><span data-stu-id="98870-105">XML validation stage of a receive pipeline</span></span>  
  
-   <span data-ttu-id="98870-106">接收埠的對應執行階段</span><span class="sxs-lookup"><span data-stu-id="98870-106">Map execution phase of a receive port</span></span>  
  
 <span data-ttu-id="98870-107">可復原交換處理是為支援成功處理包含多個可識別訊息的單一交換之需求所設計，因此有效的訊息可透過傳訊路徑傳播，而無效的訊息會被擱置。</span><span class="sxs-lookup"><span data-stu-id="98870-107">Recoverable interchange processing is motivated by the need to support successful processing of a single interchange that contains multiple identifiable messages so that valid messages are propagated through the messaging pathway and invalid messages are suspended.</span></span> <span data-ttu-id="98870-108">使用標準交換處理時，若在指定交換中有任何無效的訊息，會導致整個交換被擱置，即使它包含一或多個有效訊息也一樣。</span><span class="sxs-lookup"><span data-stu-id="98870-108">With standard interchange processing, the existence of any invalid message in a given interchange causes the entire interchange to be suspended even if it contains one or more valid messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98870-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="98870-109">In This Section</span></span>  
  
-   [<span data-ttu-id="98870-110">反組譯階段 （可復原交換處理）</span><span class="sxs-lookup"><span data-stu-id="98870-110">Disassembly Stage (Recoverable Interchange Processing)</span></span>](../core/disassembly-stage-recoverable-interchange-processing.md)  
  
-   [<span data-ttu-id="98870-111">XML 驗證階段 （可復原交換處理）</span><span class="sxs-lookup"><span data-stu-id="98870-111">XML Validation Stage (Recoverable Interchange Processing)</span></span>](../core/xml-validation-stage-recoverable-interchange-processing.md)  
  
-   [<span data-ttu-id="98870-112">對應階段 （可復原交換處理）</span><span class="sxs-lookup"><span data-stu-id="98870-112">Mapping Phase (Recoverable Interchange Processing)</span></span>](../core/mapping-phase-recoverable-interchange-processing.md)