---
title: "對應中的連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Looping
- Looping functoids
- maps, links
- BizTalk Mapper, links
ms.assetid: 3db77b8d-7b86-4c00-99a0-0513aff9b56b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32d2a9ef07cf2d79037d7983e49b26c6cfe5e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="links-in-maps"></a>對應中的連結
連結指定將輸入執行個體訊息中項目或屬性的資料複製到輸出執行個體中項目或屬性的基本功能。 在設計階設建立來源與目的結構描述中的記錄與欄位之間的連結。 如此一來會在執行階段從符合來源結構描述的輸入執行個體訊息，建立符合目的結構描述的輸出執行個體訊息。  
  
 BizTalk 對應工具支援一對一連結與一對多連結。 例如，連結可以連接來源結構描述的單一記錄或欄位與目的結構描述的單一記錄或欄位。 連結也可以連接來源結構描述的單一記錄或欄位與目的結構描述的多個記錄或欄位。  
  
 連結也可以將來源結構描述的多個記錄或欄位連結到運算質，然後再連接到目的結構描述的單一 (或多個) 記錄和 (或) 欄位。 一般而言，多個來源記錄或欄位與單一目的記錄或欄位的直接連結不是有效的，而且會產生警告。 一個例外狀況是**迴圈**運算質。 如需有關**迴圈**運算質，請參閱[迴圈 」 運算質](../core/looping-functoid.md)。  
  
 本節中的主題描述 BizTalk 對應工具中建立和使用連結的相關概念。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [連結類型](../core/types-of-links.md)  
  
-   [建立連結](../core/creating-links.md)  
  
-   [設定連結](../core/configuring-links.md)  
  
-   [記錄對記錄連結](../core/record-to-record-linking.md)  
  
-   [連結和從 Any 項目與 anyAttribute 節點](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)  
  
-   [編譯器指示詞和連結](../core/compiler-directives-and-links.md)