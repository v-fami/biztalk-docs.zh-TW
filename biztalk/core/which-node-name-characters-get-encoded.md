---
title: 這會編碼節點名稱字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48a581d2-48fa-4c36-b5c2-fe87c328a7f4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b72c7bb1eb05e8bb8ce8c0596cbacc88cb3d2f0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022068"
---
# <a name="which-node-name-characters-get-encoded"></a>哪些節點名稱字元會進行編碼
XML 對於可用於 XML 名稱 (如項目名稱) 的字元有所限制，包括對 XML 名稱中第一個字元的部分特殊限制。 在決定合法的 XML 名稱允許使用哪些字元，以及排除使用哪些字元方面的概念性目標如下：  
  
- 只要適用時，均以包含取代排除，讓新的寫入系統可符合 Unicode 編碼。  
  
- 將可能是或做為分隔符號使用的字元排除，讓 XML 名稱可以比較容易以非 XML、分隔的內容顯示。  
  
  下表顯示哪些字元可以用於 XML 名稱，可位於名稱的任何位置，或除了首字之外的任何位置。 某些允許的字元會被排除使用於名稱的第一個字元。 常值字元放在引號中，範圍則顯示在方括弧內。  
  
|名稱中的位置|允許的字元|  
|----------------------|------------------------|  
|任何位置|["A"-"Z"]、["a"-"z"]、"_"、[0x00C0-0x02FF]、[0x0370-0x037D]、[0x037F-0x1FFF]、[0x200C-0x200D]、[0x2070-0x218F]、[0x2C00-0x2FEF]、[0x3001-0xD7FF]、[0xF900-0xEFFF]|  
|首字之外的任何位置|"-"、"."、["0"-"9"]、0x00B7、[0x0300-0x036F]、[0x203F-0x2040]|  
  
 以英文表示的項目或屬性名稱 (結構描述樹狀結構檢視中的節點名稱) 之最佳作法摘要如下：  
  
-   使用英數字元，但不要以數字開頭。  
  
-   使用底線 (_)、連字號 (-)、句號 (.) 和中間點 (• )。  
  
-   不要使用空白字元。  
  
-   使用以自然語言表示的有意義字詞或字詞組合。  
  
## <a name="see-also"></a>另請參閱  
 [節點名稱屬性](../core/node-name-property.md)   
 [如何編碼節點名稱字元](../core/how-node-name-characters-get-encoded.md)