---
title: 如何新增反覆項目運算質至對應 |Microsoft 文件
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
ms.openlocfilehash: c2df7cda082a9a85e54e1dce427d73ea15d8f920
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247030"
---
# <a name="how-to-add-iteration-functoids-to-a-map"></a>如何新增重複項目運算質至對應
**反覆項目**運算質的輸出中迴圈的目前記錄的索引結構，在第一筆記錄，而第二個資料錄，2 的 1 開始等等。  
  
 如需概念資訊**反覆項目**運算質，請參閱[反覆項目運算質](../core/iteration-functoid.md)。  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a>新增索引運算質至對應並加以設定  
  
1.  與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。  
  
     顯示所選類別中的進階運算質清單。  
  
2.  拖曳**索引**運算質 (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) 從工具箱拖曳至格線頁上的適當位置。  
  
    > [!NOTE]
    >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
    > [!NOTE]
    >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3.  若要建立的迴圈記錄輸入的參數**反覆項目**運算質，迴圈記錄拖曳至來源結構描述建立輸入的連結**反覆項目**運算質，或藉由拖曳**反覆項目**運算質到來源結構描述中迴圈記錄。  
  
4.  若要使用的輸出參數**反覆項目**運算質，拖曳以建立輸出連結**反覆項目**欄位與目的結構描述中，或是將目的結構描述中的欄位拖曳到運算質**反覆項目**運算質。  
  
    > [!NOTE]
    >  在目的結構描述的對應欄位的資料類型必須是數值或可轉換為數值，使其符合的輸出資料型別**反覆項目**運算質。  
  
## <a name="see-also"></a>另請參閱  
 [新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)