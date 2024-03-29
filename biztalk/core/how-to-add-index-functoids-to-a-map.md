---
title: 如何新增索引運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbfccfcc-c333-422f-b40b-13ca4152e588
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68b560b1565638c7d82d6f497319387fc5f58755
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976183"
---
# <a name="how-to-add-index-functoids-to-a-map"></a>如何新增索引運算質至對應
**Index**運算質可讓您選取從一系列迴圈記錄中的特定記錄的資訊。 每個**Index**運算質會從單一欄位中選取資訊。  
  
 如需概念性資訊**Index**運算質，請參閱[索引運算質](../core/index-functoid.md)。  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a>新增索引運算質至對應並加以設定  
  
1. 具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。  
  
    顯示所選類別中的進階運算質清單。  
  
2. 拖曳**Index**運算質 (![](../core/media/bts-tls-index.gif "bts_tls_index")) 從工具箱拖曳至格線頁上的適當位置。  
  
   > [!NOTE]
   >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
   > [!NOTE]
   >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3. 若要建立的欄位輸入的參數**索引**運算質建立輸入的連結，將迴圈記錄中的欄位拖曳至來源結構描述**索引**運算質，或拖曳**索引**」 運算質，在來源結構描述中迴圈記錄內的欄位。  
  
4. 若要建立至少一個索引輸入的參數**Index**運算質，執行下列步驟：  
  
   1.  具有**Index**運算質選取，按一下省略符號 (**...**) 按鈕相關聯**輸入參數**中的屬性**屬性**視窗。  
  
   2.  在 [**設定索引運算質** 對話方塊中，按一下![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters")  按鈕。  
  
   3.  在編輯方塊中，輸入索引輸入的參數做為數值。 如果其他的索引值是必要的然後按一下 視需要重複**確定**。  
  
5. 若要使用的輸出參數**Index**運算質，拖曳以建立輸出連結**索引**」 運算質，欄位與目的結構描述中，或是將目的結構描述中的欄位拖曳到**索引**運算質。  
  
   > [!NOTE]
   >  與其他運算質的輸出一樣**Index**運算質可用來當做另一個運算質的輸入。  
  
## <a name="see-also"></a>另請參閱  
 [將進階運算質新增至對應](../core/adding-advanced-functoids-to-a-map.md)