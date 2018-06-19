---
title: 何謂 BAM 定義？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- definitions [BAM], observation models
- definitions [BAM], about BAM definitions
- definitions [BAM]
ms.assetid: 1ba1f45e-85fe-492f-8a2e-98bf3570c633
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cbc600f66be7167aabb4cf0273cb1c0bda78973
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289678"
---
# <a name="what-is-a-bam-definition"></a>何謂 BAM 定義？
BAM 定義是 BAM 觀察模型的 XML 表示法，代表所監控之商務程序的高階定義。 觀察模型的主要部分包括里程碑和蒐集的資料事件 (BAM 活動)、任何資料彙總的描述，以及向使用者呈現資訊的方式 (BAM 檢視)；因此這些同樣也是 BAM 定義的主要部分。  
  
> [!NOTE]
>  您也可以手動建立遵循 BAM 結構描述的 XML 檔案，但不建議以此方式建立 BAM 定義，因為這類定義沒有經過驗證。  
  
 BAM 定義可包含下列項目：  
  
-   商務活動 - 有效的 BAM 定義必須包含商務活動 (也稱為 BAM 活動)。 定義中其餘所有項目皆為選擇性。 新增至定義商務活動的相關資訊，請參閱[如何定義商務活動](../core/how-to-define-a-business-activity.md)。  
  
-   檢視 – 檢視定義了能夠存取商務活動所定義之資料的使用者集合。 檢視中包含篩選的資料、所篩選資料的彙總，以及呈現篩選資料的方式，例如樞紐分析圖報表。 每個 BAM 活動支援一或多個檢視的定義。  
  
     在檢視中可以定義下列商務程序：  
  
    -   別名商務資料 - 別名允許您對資料項目套用易記名稱。 例如，開發人員定義的資料項目名稱可能是 "LName"。 您可以建立別名，以便於檢視 BAM 即時資料時將 “LName” 顯示為「姓氏」。  如需別名的詳細資訊，請參閱[如何重新命名檢視項目](../core/how-to-rename-view-items.md)。  
  
    -   持續時間 - 監控活動的時間週期。  
  
    -   里程碑群組 - 一組商務里程碑。 您可以使用群組做為持續時間的開始或結束商務里程碑。  
  
    -   彙總 - 可能是即時彙總 (RTA) 或排程彙總 (也稱為線上分析處理 (OLAP))，且包含下列項目：  
  
-   量值 - 根據 Cube 事實資料表的資料行，在 Analysis Services (OLAP) Cube 中建立的數值集。  
  
-   進度維度 - 代表與仍在進行中之活動進度有關的彙總建立情況。  
  
-   資料維度 - 用以將彙總分類。 資料維度是以 BAM 活動中的字串格式資料項目的值為依據。  
  
-   時間維度 - 用以建立橫跨已定義時間區段的彙總。  
  
-   數字範圍維度 - 用以根據特定數字範圍的易記名稱將彙總分類。  
  
 BAM 定義可以包含檢視中所定義的警示定義。 BAM 定義也能包含樞紐分析表版面配置。 一旦部署 BAM 定義後，就能使用 Excel 即時資料活頁簿或透過 BAM 入口網站，檢視含有即時商務資料的樞紐分析表報表。  
  
> [!NOTE]
>  使用 Excel 的 BAM 增益集所建立的 BAM 定義無法包含警示。  
  
## <a name="see-also"></a>另請參閱  
 [在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md)   
 [BAM 入口網站](../core/bam-portal.md)   
 [BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)