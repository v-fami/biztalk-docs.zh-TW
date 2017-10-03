---
title: "關係節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], relationships
- definition files [BAM], Tracking Profile Editor
- Relationship nodes [Tracking Profile Editor]
- activities [BAM], relationships
- activities [BAM], Tracking Profile Editor
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 74090133-24d1-4aba-a4fc-f12d19c881fb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f670c62b4e883b124d849ab61396f6f5216e7182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="relationship-nodes"></a>關係節點
當活動定義檔案包含一個以上的活動時，就會用到關係資料夾。 資料夾的名稱會與關聯活動的名稱相符。 將關係資料夾的名稱與相關活動的活動識別碼配對，並配上資料項目的值，即可形成連結。 請使用不同的節點定義每個關係。  
  
## <a name="working-with-relationship-nodes"></a>使用關係節點  
 指示可連結活動資料項目的唯一執行個體識別項：  
  
-   將資料項目對應到主協調流程的 ActivityId 節點。  
  
-   將具有與上述資料項目相同名稱的資料項目拖放到相關活動的關係節點中。 此關係節點的名稱與主活動的活動節點名稱相同。  
  
 舉例來說，在範例實例中，可能有個用名稱為 RefinanceOrchestration 的協調流程來表示相關但不同的商務程序。 該協調流程可能含有 LoanRefinance 活動節點、Refinance ActivityID，以及如「接收評估要求」的協調流程圖形。 不過，關係節點和關係識別碼可能是 LoanID，表示與原始 LoanProcess 活動的連結。  
  
## <a name="see-also"></a>另請參閱  
 [TPE 活動檢視節點](../core/tpe-activity-view-nodes.md)