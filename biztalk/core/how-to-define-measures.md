---
title: 如何定義量值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating measures
- aggregations [BAM], measures
- BAM views, measures
ms.assetid: fd3dfe6b-cc63-4306-8aad-a9d2a9af01e8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56fea736baaec3f259fc8831a7256e28eaabc9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249142"
---
# <a name="how-to-define-measures"></a>如何定義量值
量值可以定義計算活動的方式。 建立 BAM 檢視時，您可以定義檢視中的活動量值。 例如，對於「訂單」活動，您可以計算訂單總金額、訂單件數、訂單平均金額等。  
  
 BAM 支援的量值包括：  
  
-   Sum  
  
-   Count  
  
-   平均值  
  
-   最小值  
  
-   最大值  
  
> [!NOTE]
>  「BAM 即時彙總」(RTA) 功能目前不支援「最小值」和「最大值」量值。 您可以使用這些量值，但是將 Excel 樞紐分析表標示為 RTA 時，「最小值」和「最大值」會被忽略。  
  
### <a name="to-add-new-measures"></a>新增量值  
  
1.  在 BAM 檢視精靈中，按一下 **下一步**直到您看到**新 BAM 檢視： 彙總維度與量值**頁面。 按一下**新的量值**。  
  
2.  輸入量值的名稱。  
  
3.  從下拉式清單選取**基底資料項**。  
  
4.  按一下**彙總類型**您想要使用。 選項包括：  
  
    -   Sum  
  
    -   Count  
  
    -   平均值  
  
    -   最小值 （Rta 不支援）。  
  
    -   最大值 (RTA 不支援)  
  
5.  按一下 **[確定]**。 當您完成新增維度和量值時，按一下**下一步**。  
  
6.  在**新 BAM 檢視： 摘要**頁面上，檢閱您的新檢視的相關資訊，然後按一下**下一步**。  
  
7.  按一下**完成**完成**BAM 檢視精靈**。  
  
 如果您已將量值和維度新增至 BAM 檢視，就可以將這些項目新增到 Excel 活頁簿中的樞紐分析表。 如需有關建立樞紐分析表的詳細資訊，請參閱[如何使用樞紐分析表](../core/how-to-use-the-pivottable.md)。  
  
## <a name="see-also"></a>另請參閱  
 [定義維度](../core/defining-dimensions.md)