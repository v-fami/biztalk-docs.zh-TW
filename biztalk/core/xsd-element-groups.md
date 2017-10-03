---
title: "XSD 項目群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT, XSLT variations
- BizTalk Mapper, XSLT variations
- maps, groups
- Choice Group node
- XSD element groups
- XSLT, warnings
ms.assetid: a6ea22cb-6066-480e-8a2a-75fade3e5970
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b850841819ce844a10e407827d02993ce3559bad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xsd-element-groups"></a>XSD 項目群組
在結構描述中使用某些特定的結構，可能會在 BizTalk 對應工具所產生的「可延伸樣式語言轉換」(Extensible Stylesheet Language Transformations，XSLT) 中製造一些變化。  
  
 在定義 Sequence、Choice 或所有項目群組的對應包括結構描述時，就會發生這個變化。 例如，如果您使用的結構描述包括**Choice 群組** 節點，便可讓您建立的地圖，需要兩個以上的子系**Choice 群組**才會出現在輸出執行個體的節點訊息。 在此例中，BizTalk 對應工具會在您編譯對應時顯示警告。 此項警告會告知您，在您已對應的必要欄位中，只有一個可以在執行階段中填入父迴圈的相同重複項目中。 BizTalk 對應工具不會提供錯誤訊息，來告知您的對應邏輯不正確。  
  
 若符合下列條件，您將能夠在 XSLT 中產生變化：  
  
-   **記錄 A**其子系**欄位項目 B**。  
  
-   **記錄 A**和子系**欄位項目 B**出現一次。  
  
-   **記錄 A**屬於**Choice 群組**重複。  
  
 在此狀況中，BizTalk 對應工具所產生的 XSLT 會包含重複項目邏輯，以處理來源記錄產生許多變化的可能性。  
  
> [!NOTE]
>  您必須明確了解所涉及之群組的對應。 例如，如果目的結構描述包含**Choice 群組**節點有子節點 A 和 B，不能擁有 A 和 B，同時在其父群組中的相同重複項目上。 BizTalk 對應工具並不會阻止您建立無效的對應。 所以，您必須使用邏輯運算質來設定對應，讓 A 和 B 永遠不同時出現。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)