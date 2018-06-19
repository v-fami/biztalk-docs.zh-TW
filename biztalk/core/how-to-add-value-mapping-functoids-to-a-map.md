---
title: 如何新增值對應運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc70067a-67a1-4a0e-95e5-b0cb327d2cee
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e463489332c3a1d2887dab5f7bd734fdd20af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247838"
---
# <a name="how-to-add-value-mapping-functoids-to-a-map"></a>如何新增值對應運算質至對應
**值對應**運算質會傳回其第二個參數的值，如果第一個參數為 true。 運算質的一般用途是將欄位的屬性變更為記錄的屬性。  
  
 如需概念資訊**值對應**運算質，請參閱[值對應運算質](../core/value-mapping-functoid.md)。  
  
### <a name="to-add-the-value-mapping-functoid-to-a-map-and-configure-it"></a>新增值對應運算質至對應並進行設定  
  
1.  與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。  
  
     顯示所選類別中的進階運算質清單。  
  
2.  拖曳**值對應**運算質 (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) 從工具箱拖曳至格線頁上的適當位置。  
  
    > [!NOTE]
    >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
    > [!NOTE]
    >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3.  若要建立的第一個輸入的參數**值對應**運算質，拖曳以建立輸入的連結**值對應**來源結構描述中的記錄或欄位節點或另一個運算質到運算質其左邊，具有布林資料類型，而且，將會產生"true"或"false"的輸入的值。  
  
    > [!NOTE]
    >  您也可以拖曳以相反的方向，將布林值的來源拖曳**值對應**運算質。  
  
4.  若要建立的第二個輸入的參數**值對應**運算質，拖曳以建立輸入的連結**值對應**記錄或欄位節點來源結構描述，或將記錄拖曳運算質來源結構描述中的 [欄位] 節點或**值對應**運算質。  
  
    > [!NOTE]
    >  第二個輸入參數來**值對應**運算質也可以從另一個運算質的輸出的左側。 藉由將其中一個相關運算質拖曳到其他相關運算質，建立代表這類輸入來源的連結。  
  
5.  若要使用的輸出參數**值對應**運算質，拖曳以建立輸出連結**值對應**的記錄或欄位與目的結構描述，或是拖曳記錄欄位的運算質目的地結構描述為**值對應**運算質。  
  
    > [!NOTE]
    >  與其他運算質的輸出**值對應**運算質可做為另一個運算質的輸入。  
  
## <a name="see-also"></a>另請參閱  
 [新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)