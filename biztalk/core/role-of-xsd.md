---
title: "XSD 的角色 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe08f6b-563f-4bae-a5be-551e487b2a6d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad2f99b60de5ebb2a3cd7e102a2f3f7b787d1ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="role-of-xsd"></a>XSD 的角色
XML 結構描述定義 (XSD) 語言提供在 BizTalk 中定義之訊息結構描述的基礎語法。 雖然 BizTalk 編輯器和 BizTalk 對應工具中的樹狀檢視會使用記錄和欄位節點 (在其他類型節點之間) 之 BizTalk 特定的圖形階層，但其各自的屬性集 (如階層) 均是以 XSD 建構與保存。 BizTalk 編輯器會提供唯讀 XSD 檢視，您可以在其中看到建構為各種節點的 XSD 新增至樹狀檢視中之結構描述的圖形表示法中，或是從中移除，以及與那些節點相關之屬性值的變更。 雖然通常不需要了解 XSD 的細節即能以 BizTalk 編輯器成功建構簡單結構描述，但若您要在樹狀檢視中對結構描述階層進行變更時研究 XSD 變更，那麼您將要學習使用 XSD。  
  
 XSD 中的結構描述註解功能 (BizTalk Server 所定義的大量註解集) 可有效地擴充 XSD，以支援表示非 XML 訊息 (如一般檔案) 的必要語法。  
  
## <a name="see-also"></a>另請參閱  
 [在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)   
 [關於結構描述](../core/about-schemas.md)