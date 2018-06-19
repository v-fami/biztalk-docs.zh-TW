---
title: 編譯對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, compiling
- XSLT, generating
- maps, validating
- BizTalk Mapper, compiling
- BizTalk Mapper, validating
ms.assetid: 967181d6-22a9-4a76-ae45-3317c0c6321b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346769519343afe9456a7b1e7cf9a3bd5bb159ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231862"
---
# <a name="compiling-maps"></a>編譯對應
當您驗證對應時，BizTalk 對應工具編譯器元件會產生「可延伸樣式表語言轉換」(XSLT) 樣式表。 這會建立經過編譯的對應，可將來源結構描述定義的執行個體訊息轉換為目的結構描述定義的執行個體訊息。 編譯對應可強制使用格線頁中指定的結構化規則與轉換。  
  
 轉換 (例如連結) 會以記錄與欄位顯示在目的結構描述的相同順序處理。 例如，當 BizTalk 對應工具到達目的地**記錄**或**欄位**節點的連結，BizTalk 對應工具會編譯連結的屬性。 進行的動作可能只是從來源結構描述的記錄或欄位複製值，或可能包含使用運算質和多個記錄與欄位的多個運算式。  
  
 BizTalk 對應工具會產生警告中的**輸出**視窗和**工作清單**當編譯器遇到的情況，可能會產生不正確的輸出 視窗。 例如，如果運算質需要一個輸入的參數，而且沒有輸入參數，BizTalk 對應工具會產生一個警告**輸出**視窗。 一般而言，若產生警告，就不應在生產環境中使用對應。  
  
 產生的 XSLT 樣式表的連結也會出現在**輸出**會正確編譯對應時，視窗。  
  
 BizTalk Server 會使用已編譯的對應，將輸入執行個體訊息轉譯成輸出執行個體訊息。  
  
## <a name="see-also"></a>另請參閱  
 [測試對應](../core/testing-maps.md)   
 [資料轉換組態](../core/data-transformation-configuration.md)   
 [節點階層層級比對](../core/node-hierarchy-level-matching.md)