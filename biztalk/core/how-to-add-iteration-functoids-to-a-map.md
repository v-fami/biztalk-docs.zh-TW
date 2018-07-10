---
title: 如何新增反覆項目運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1eaea929-e352-447d-b119-bd69b6b24e6c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ed2dfe33feb7d5e0e6f43be61742bfbbddfc98c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997191"
---
# <a name="how-to-add-iteration-functoids-to-a-map"></a>如何新增重複項目運算質至對應
**反覆項目**運算質會輸出迴圈的目前資料錄的索引結構，開始第一筆記錄，而第二個資料錄，2 的 1 等等。  
  
 如需概念性資訊**反覆項目**運算質，請參閱[反覆項目運算質](../core/iteration-functoid.md)。  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a>新增索引運算質至對應並加以設定  
  
1. 具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。  
  
    顯示所選類別中的進階運算質清單。  
  
2. 拖曳**Index**運算質 (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) 從工具箱拖曳至格線頁上的適當位置。  
  
   > [!NOTE]
   >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
   > [!NOTE]
   >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3. 若要建立的迴圈記錄輸入的參數**反覆項目**運算質，將迴圈記錄拖曳至來源結構描述，以建立輸入的連結**反覆項目**運算質，或藉由拖曳**反覆項目**運算質將來源結構描述中迴圈記錄。  
  
4. 若要使用的輸出參數**反覆項目**運算質，建立輸出連結，藉由拖曳**反覆項目**欄位與目的結構描述中，或是將目的結構描述中的欄位拖曳到運算質**反覆項目**運算質。  
  
   > [!NOTE]
   >  目的結構描述中相關欄位的資料類型必須是數值或可轉換為數值，使其符合的輸出資料型別**反覆項目**運算質。  
  
## <a name="see-also"></a>另請參閱  
 [將進階運算質新增至對應](../core/adding-advanced-functoids-to-a-map.md)