---
title: "使用剖析和序列化引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing engine
- pipeline components [custom], engines
- serialization engine
- pipeline components [custom], assembling
- pipeline components [custom], parsing
ms.assetid: a9d19703-b074-402a-971a-b2a6cd5d0724
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e820b2dce1257ec948aa214c9fdf1d43a6a7152
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-parsing-and-serializing-engines"></a>使用剖析和序列化引擎
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含剖析和序列化引擎，以簡化剖析和序列化一般檔案文件的程序。  
  
 剖析引擎是一個以結構描述驅動的架構，它可以將許多不同的文件格式剖析為 XML。 此外，此引擎也具有一個定義完善的擴充性模型，讓自訂格式的剖析更為輕鬆。  
  
 如果是複雜的剖析，則會使用解譯器。 除了將原生格式轉換為 XML，解譯器也可以將單一文件分成多個文件。  
  
 序列化引擎類似於剖析引擎，例外的一點是它會反向運作。 剖析引擎會將原生格式轉換為 XML，而序列化引擎則是將 XML 轉換為原生格式。 序列化引擎會使用組合器，就如同剖析引擎使用解譯器一樣。  
  
 本章節將討論如何執行字元編碼、根據 XML 結構描述定義語言 (XSD) 結構描述來剖析及序列化，以及使用剖析引擎和序列化引擎 API 執行其他一般工作。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [實作管線元件中的字元編碼方式](../core/implementing-character-encoding-in-a-pipeline-component.md)  
  
-   [使用結構描述](../core/using-schemas.md)  
  
-   [使用一般檔案剖析引擎](../core/using-the-flat-file-parsing-engine.md)  
  
-   [使用一般檔案序列化引擎](../core/using-the-flat-file-serializing-engine.md)