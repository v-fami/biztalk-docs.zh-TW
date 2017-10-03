---
title: "資料維度 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data dimension [BAM]
- aggregations [BAM], data dimensions
ms.assetid: 07b5e56a-4fd5-4c88-a98a-758e514d0621
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7138cf31a9cb86a9ba949142129ac5c906754b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-dimension"></a>資料維度
定義資料維度以允許將 BAM 活動中部分文字項目的值使用在資料列或資料行上。 例如，名為「產品」的資料維度可以用來建立下列資料表：  
  
|產品|Count|  
|-------------|-----------|  
|網球拍|100|  
|足球|200|  
  
 此外，您也可以在 BAM 檢視精靈中定義一個以上的資料維度。 例如，定義名為的資料維度**位置**的層級**狀態**和**縣 （市)**可用來建立下列資料表：  
  
|||||  
|-|-|-|-|  
||California||Washington|  
||Los Angeles|San Francisco|Seattle|  
|網球拍|50|20|30|  
|足球|130|50|20|  
  
 這個資料表使用「產品」維度做為資料列，並使用「位置」維度做為資料行。  
  
## <a name="see-also"></a>另請參閱  
 [時間維度](../core/time-dimension.md)   
 [進度維度](../core/progress-dimension.md)   
 [數字範圍維度](../core/numeric-range-dimension.md)   
 [定義維度](../core/defining-dimensions.md)