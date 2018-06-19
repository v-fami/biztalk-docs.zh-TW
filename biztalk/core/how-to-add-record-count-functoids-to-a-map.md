---
title: 如何新增記錄計數運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fbfd2a0-fac5-49f1-bcbb-873c287cd278
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd315a637b3efd069361dfa2d780cff179559da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247662"
---
# <a name="how-to-add-record-count-functoids-to-a-map"></a>如何將記錄計數運算質新增至對應
**記錄計數**運算質可讓您產生執行個體訊息中的一筆記錄發生次數的計數。  
  
 如需概念資訊**記錄計數**運算質，請參閱[記錄計數運算質](../core/record-count-functoid.md)。  
  
### <a name="to-add-the-record-count-functoid-to-a-map-and-configure-it"></a>新增記錄計數運算質至對應並設定  
  
1.  與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。  
  
     顯示所選類別中的進階運算質清單。  
  
2.  拖曳**記錄計數**運算質 (![](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) 從工具箱拖曳至格線頁上的適當位置。  
  
    > [!NOTE]
    >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
    > [!NOTE]
    >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
3.  若要建立的輸入的參數**記錄計數**運算質，迴圈記錄拖曳至來源結構描述建立輸入的連結**記錄計數**運算質，或拖曳**記錄計數**運算質到來源結構描述中迴圈記錄。  
  
4.  若要使用的輸出參數**記錄計數**運算質，拖曳以建立輸出連結**記錄計數**運算質至目的結構描述，或將欄位拖曳目的地中的欄位結構描述以**記錄計數**運算質。  
  
    > [!NOTE]
    >  與其他運算質的輸出**記錄計數**運算質可用做為另一個運算質的輸入。  
  
## <a name="see-also"></a>另請參閱  
 [新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)