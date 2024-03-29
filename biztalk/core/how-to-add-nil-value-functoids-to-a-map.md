---
title: 如何新增 Nil 值運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b2e193ed-fe5c-4b12-aab8-ff2d81fd45e1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8488ea03fb40e1616b98e3ac8a1fc68b18e70e9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011863"
---
# <a name="how-to-add-nil-value-functoids-to-a-map"></a>如何新增 Nil 值運算質至對應
**值，Nil**運算質設定的目的地節點值**Nil**。  

 如需概念性資訊 **「 Nil 值**運算質，請參閱[Nil 值運算質](../core/nil-value-functoid.md)。  

## <a name="add-the-nil-value-functoid-to-a-map-and-configure-it"></a>新增 「 Nil 值 」 運算質至對應並加以設定  

1. 具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。 顯示所選類別中的進階運算質清單。  

2. 拖曳**值，Nil**運算質 (![Nil 值 」 運算質](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) 從工具箱拖曳至格線頁上的適當位置。  

   > [!NOTE]
   >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
   >
   >  若您要建構使用一個以上運算質的對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  

3. **「 Nil 值**運算質可以有零個到一個輸入參數。 如果沒有為此運算質輸入的參數，在目標節點設定為**Nil**。 若要建立的輸入的參數 **「 Nil 值**運算質建立輸入的連結，方法是將輸出拖曳某個其他**邏輯**運算質或從輸入執行個體訊息中的變數布林值欄位。  

4. 若要使用的輸出參數 **「 Nil 值**運算質，建立輸出連結，藉由拖曳 **「 Nil 值**」 運算質的記錄或欄位與目的結構描述。  

   > [!NOTE]
   >  與其他運算質的輸出一樣 **「 Nil 值**運算質可用來當做另一個運算質的輸入。  

## <a name="see-also"></a>另請參閱  
- **Nil 值運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [將進階運算質新增至對應](../core/adding-advanced-functoids-to-a-map.md)
