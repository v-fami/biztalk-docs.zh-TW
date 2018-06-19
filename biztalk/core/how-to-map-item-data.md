---
title: 如何對應項目資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data extraction
- orchestrations, data extraction
- orchestrations, tracking profiles
- tracking profiles, orchestrations
- tracking profiles, data extraction
ms.assetid: ae8b395e-152a-4e08-af31-3c9276f52711
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efdfd722e1610be02c06dd6e2a9597e13c0f1e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253950"
---
# <a name="how-to-map-item-data"></a>如何對應項目資料
對應項目資料，可以定義協調流程中的資料擷取。  
  
> [!NOTE]
>  在建立追蹤設定檔時，請務必對應與活動項目相容的資料類型值。 如果資料類型不相容，您將會收到 BAM 執行階段錯誤。  
  
> [!NOTE]
>  在對應如日期/時間戳記等里程碑時，要對應的資料必須符合 SQL 字串的日期時間戳記表示法。 YYYY-MM-DDTHH:MM:SS.mmm-HH:MM 這種 XML DateTime 格式的 DateTime 資料則不受支援。  
>   
>  例如，這個日期字串 1999-05-31T13:20:00.000-05:00 便不受支援。  
  
## <a name="prerequisites"></a>必要條件  
 已部署您將連接的 BAM 活動定義和協調流程。  
  
### <a name="how-to-map-item-data"></a>如何對應項目資料  
  
1.  開啟現有的追蹤設定檔或建立新的追蹤設定檔。 如需有關如何建立追蹤設定檔的詳細資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。  
  
2.  在此實例中，會匯入名為 LoanProcessBamDef 的活動定義， 它包含**LoanProcess**活動節點，並且以客戶的**SSN**做為 ActivityID。 如需詳細資訊，請參閱[Activity 和 ActivityID 節點](../core/activity-and-activityid-nodes.md)。  
  
3.  請確認每個活動都有可以追蹤的 ActivityID 或 ContinuationID 資料項目，例如客戶的 SSN。  
  
4.  將協調流程動作對應到適當的商務事件資料夾，以指示要追蹤的事件。例如，在貸款處理實例中下列項目，和其他項目，拖曳到下**LoanProcess**活動資料夾：  
  
    -   **LoanApplicationReceived**  
  
    -   **CreditHistoryRequest**  
  
    -   **CreditHistoryResponse**  
  
## <a name="see-also"></a>另請參閱  
 [資料項目節點](../core/data-item-nodes.md)   
 [建立追蹤設定檔](../core/creating-tracking-profiles.md)