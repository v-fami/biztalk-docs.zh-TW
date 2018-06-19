---
title: 欄位填補 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47017036-7d64-4222-b574-d2913bf69358
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56aa8490bd9e72677c9c8eefa73e7f6bd8438dfd
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "22246222"
---
# <a name="field-padding"></a>欄位填補

## <a name="overview"></a>概觀

當欄位中包含的資料小於欄位的保留字元數目或位元組數目時，就會在分隔和序數記錄中的欄位使用填補字元。 這些字元佔用資料不需要的欄位部分 (若有的話)。 指定欄位的欄位使用填補字元**填補字元**和**Pad Character Type**屬性對應**欄位項目**和**欄位屬性**節點。 若特定欄位沒有指定的填補字元，則該欄位會使用預設的填補字元，即空格 (" ")。  
  
## <a name="inbound-instances"></a>輸入執行個體
 若是輸入的執行個體訊息，因為要將執行個體訊息轉譯為其對等的 XML 格式，所以無論特定記錄是序數記錄或分隔記錄，一般檔案解譯器都會捨棄特定欄位的指定或預設填補字元之前置或尾端執行個體。 它是否前置或尾端會捨棄相關填補字元的執行個體取決於是否**理由**屬性對應**欄位項目**和**欄位屬性**節點設定為**右邊**或**左**分別。  

## <a name="outbound-instances"></a>輸出執行個體  
 若是輸出的執行個體訊息，一般檔案解譯器會將適當數目的指定或預設填補字元插入欄位，使欄位的長度正確。 之前或之後的資料字元根據是否會插入填補字元 **理由** 對應 **欄位項目** 和 **欄位屬性** 節點設定為 **右邊** 或 **左**, 分別。  
  
 當輸出執行個體訊息中被填補的欄位是否包含在位置記錄， **Positional Offset**和**Positional Length**屬性對應**欄位項目**或**欄位屬性**結合的欄位必須包含的資料字元數 節點，判斷是否有任何填補字元是必要的而且如果是，多少。 當輸出執行個體訊息中被填補的欄位包含在分隔記錄中時，只會填補字元插入時的值**Minimum Length with Pad Character**對應**欄位項目**或**欄位屬性**節點超過資料字元數。  

## 
這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>另請參閱  
 [欄位考量](../core/field-considerations.md)   
 [欄位左右對齊](../core/field-justification.md)   
 [位置記錄中欄位位置的規格](../core/specification-of-field-positions-within-positional-records.md)  