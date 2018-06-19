---
title: 如何新增大量複製運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cff63fc-8f34-4bd0-8501-a8401bde6349
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cee6f2c53bbd3b3dbabe55f0160309532d0ebf3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247566"
---
# <a name="how-to-add-mass-copy-functoids-to-a-map"></a>如何將大量複製運算質新增至對應
**大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。 這些項目實際上是在 XML 結構描述定義語言中提供的萬用字元，以符合未知的結構或屬性集。  
  
 如需概念資訊**大量複製**運算質，請參閱[大量複製運算質](../core/mass-copy-functoid.md)。  
  
### <a name="to-add-the-mass-copy-functoid-to-a-map-and-configure-it"></a>將大量複製運算質新增至對應並加以設定  
  
1.  與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。  
  
     顯示所選類別中的進階運算質清單。  
  
2.  拖曳**大量複製**運算質 (![](../core/media/advmasscopy.gif "advmasscopy")) 從工具箱拖曳至格線頁上的適當位置。  
  
    > [!NOTE]
    >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
    > [!NOTE]
    >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3.  若要建立的輸入的參數**大量複製**運算質建立輸入的連結，從來源結構描述拖曳記錄**大量複製**運算質，或拖曳**大量複製**運算質至來源結構描述中的記錄。  
  
4.  若要使用的輸出參數**大量複製**運算質，拖曳以建立輸出連結**大量複製**運算質至目的結構描述，或將記錄拖曳至目的結構描述中的記錄**大量複製**運算質。  
  
    > [!NOTE]
    >  不同於其他運算質，您無法使用的輸出**大量複製**運算質，做為另一個運算質的輸入。  
  
> [!NOTE]
>  您可以插入並設定**大量複製**連結兩個運算質會直接記錄。 如需詳細資訊，請參閱 < 使用大量複製運算質的連結 」 一節中[如何自動連結記錄](../core/how-to-link-records-automatically.md)。  
  
## <a name="see-also"></a>另請參閱  
 [新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)