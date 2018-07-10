---
title: 如何新增迴圈運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b24051b7-3e79-4a49-8249-a057c048ddae
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 659b9b39beea4bf5efed4c6d1553fca173191cc5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988759"
---
# <a name="how-to-add-looping-functoids-to-a-map"></a>如何新增迴圈運算質至對應

## <a name="overview"></a>概觀
**迴圈**運算質結合多個記錄或欄位在來源結構描述中的目的地結構描述中的單一記錄。  

 如需概念性資訊**迴圈**運算質，請參閱[迴圈 」 運算質](../core/looping-functoid.md)。  

 某些狀況下，某些運算質可能無法如預期般 map 中索引使用時**迴圈**運算質。 如果這樣的運算質符合下列條件，則不會產生預期的結果：  

-   此運算質擁有一個以上的輸入連結。  

-   兩個或多個運算質輸入連結連結至子欄位來輸入資料錄**迴圈**運算質，其中的子欄位並非同層級項目。  

-   運算質有輸出連結連結到的輸出記錄的子欄位**迴圈**運算質。  

## <a name="add-the-looping-functoid-to-a-map-and-configure-it"></a>新增迴圈運算質至對應並加以設定  

1. 具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。  

    顯示所選類別中的進階運算質清單。  

2. 拖曳**迴圈**」 運算質從工具箱拖曳至格線頁上的適當位置。  

    ![](../core/media/bts-tls-looping.gif "bts_tls_looping")  
   迴圈運算質  

   > [!NOTE]
   >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
   > 
   >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  

3. 若要建立的輸入的參數**迴圈**運算質建立輸入的連結，藉由拖曳記錄或欄位從 來源結構描述**迴圈**運算質，或拖曳**迴圈**的記錄或欄位在來源結構描述中的運算質。 依規定必須納入所有相關的輸入的記錄或欄位，以重複**迴圈**運算質。  

4. 若要使用的輸出參數**迴圈**運算質，建立輸出連結，藉由拖曳**迴圈**記錄或欄位與目的結構描述，或藉由拖曳記錄或欄位到運算質至目的結構描述**迴圈**運算質。  

   > [!NOTE]
   >  不同於許多其他運算質的輸出**迴圈**運算質只可以連結至目的結構描述的項目。  

## <a name="see-also"></a>另請參閱  
- [將進階運算質新增至對應](../core/adding-advanced-functoids-to-a-map.md)   
- **迴圈運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
