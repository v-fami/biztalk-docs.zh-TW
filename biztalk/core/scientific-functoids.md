---
title: 科學運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0311b7dc-1955-45af-b858-681faccc939b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf7a181f200948335aab0ffa2a06d43d38408afb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977414"
---
# <a name="scientific-functoids"></a>科學運算質

## <a name="overview"></a>概觀
**科學**運算質用來執行各種標準三角、 對數以及指數計算。  

 除了**指定基底對數**並**X ^ Y**運算質接受兩個輸入的參數，**科學**所有的運算質接受單一參數。  

 四種三角**科學**運算質 (**反正切值**，**餘弦函數**，**正弦**，和**正切函數**) 所有使用弧度為單位，而不是度為單位的相關輸入或輸出參數。 弧度是一種角度測量單位，例如一個圓為 2π 弧度。 說明如下：  

- 2π 弧度等於 360 度  

- 1 弧度 = 180/π 度  

- 1 度 = π/180 弧度  

  如果您輸入或輸出的執行個體訊息會使用度數作為其測量單位的角度，您必須使用**數學**運算質與三角倂**科學**」 運算質達到正確的結果。  

## <a name="available-functoids"></a>可用的運算質  
 **科學**運算質為： 

* 10^n
* 反正切值
* 指定基底對數
* 常用對數
* 餘弦函數
* 自然指數函式
* 自然對數
* 正弦函數
* 正切函數
* X^Y

## <a name="see-also"></a>另請參閱  
- [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
- **科學運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
