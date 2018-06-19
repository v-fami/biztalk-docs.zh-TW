---
title: 定義維度 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], dimensions
- BAM, dimensions
- BAM views, dimensions
- Excel add-in [BAM], creating dimensions
- dimensions [BAM]
ms.assetid: c00e0c45-eef2-42d9-832c-4be08d79203f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 916e8f29d7f1e48a7bab5f9ad78e65cb78e51802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238486"
---
# <a name="defining-dimensions"></a>定義維度
Microsoft Excel 將維度定義成類別，可用來將表格資料組織到用於分析的層級中。 例如，位置資料維度可能包含城市、州/省和國家/地區等層級。 在「BAM 檢視精靈」中建立 BAM 檢視時，您可以新增一或多個下列維度類型：  
  
-   [進度維度](../core/progress-dimension.md)  
  
-   [資料維度](../core/data-dimension.md)  
  
-   [時間維度](../core/time-dimension.md)  
  
-   [數字範圍維度](../core/numeric-range-dimension.md)  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
預先計算的彙總資料  
  
 您可以在「BAM 檢視精靈」中新增維度。 但是在新增維度之前，您必須先使用此精靈來建立商務活動檢視。 如需有關如何使用精靈的詳細資訊，請參閱[定義商務活動和在 Excel 中的檢視](../core/defining-business-activities-and-views-in-excel.md)。  
  
### <a name="to-add-new-dimensions"></a>新增維度  
  
1.  在 BAM 檢視精靈中，按一下 **下一步**直到您看到**新 BAM 檢視： 彙總維度與量值**頁面。 按一下**新維度**。  
  
2.  輸入維度的名稱。  
  
3.  從下拉式清單中選取維度類型。  
  
4.  根據您所選取維度類型，填入適當的資料，並再按**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [進度維度](../core/progress-dimension.md)