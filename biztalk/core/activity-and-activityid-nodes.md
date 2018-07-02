---
title: Activity 和 ActivityID 節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ActivityID nodes [Tracking Profile Editor]
- Activity nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- activities [BAM], definitions
ms.assetid: 94d4130a-53c5-4cd5-916a-4a6bd9acbf23
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbe92c28a3ca84cdd94236c1069c9d340cc4630f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983559"
---
# <a name="activity-and-activityid-nodes"></a>Activity 和 ActivityID 節點
Activity 和 ActivityID 節點是用以包含和識別活動定義。 Activity 節點是活動定義中之項目的父資料夾。 所有的資料項目和商務事件節點都附屬和包含在關聯的活動節點中。 Activity 節點的命稱應該反映活動本身的名稱。  
  
 ActivityID 節點是在活動定義中自動產生的項目，應包含活動的唯一識別碼。 ActivityID 節點可用以追蹤使用者提供的識別碼或系統產生的識別碼。 例如，在將訂單編號做為系統中所有訂單之唯一識別碼的案例中，您可使用此編號做為 ActivityID，在此情況下，您將從一些事件來源 (例如訂單結構描述中的 PO 編號欄位) 對應 ActivityID 的值。 另一方面，如果訂單值不是唯一的，則您可以不要對應節點，BAM 會在執行階段自動產生唯一的識別碼。  
  
 活動可能和其他活動相關。 在某些案例中，這些關係明確屬於觀察模型的一部分。  特別是，當任何使用者檢視包含兩個以上的活動時，這些活動之間就自動具有關係。  當這樣的關係存在時，在活動樹狀目錄的 Activity 節點下就會為每個已知的對等活動自動建立關係節點。 在有資料關係但沒有擴展的檢視時，您可以手動將關係節點新增到活動樹狀目錄中。  
  
 在任一情況下，關係節點的目的都是為相關的活動提供識別碼。 例如，訂單和出貨可能有多對多的關係 (一張 PO 可能包含多次出貨；一次出貨所裝載的產品可能滿足許多 PO)。  每張訂單的活動記錄可能有多個相關之出貨的指標，每次出貨活動記錄可能指向一或多張訂單。  以資料庫的方式來說，關係節點的值就是資料表中另一個活動的外部索引鍵。  
  
## <a name="working-with-activity-id-nodes"></a>使用 Activity ID 節點  
 例如，假設有以下狀況： EquityLoan 協調流程包含 LoanProcess 活動資料夾。 它參考下列商務事件：  
  
- LoanApplicationReceived  
  
- CHRequest  
  
- CHResponse  
  
- AppraisalRequest  
  
- AppraisalResponse  
  
- 已核准  
  
- 拒絕  
  
  ActivityID 節點可讓方案開發人員擷取唯一識別活動的資料，例如訂單編號或是訊息的 SSN 欄位 (在範本案例的情況中)。 如果您未將任何資料拖曳到 ActivityID 節點，自動產生的 GUID 就會識別商務活動。  
  
  若要定義不同協調流程中之商務事件或里程碑之間的關係，目標協調流程就必須參考 ActivityID。 如需如何使用 TPE 實作關係的詳細資訊，請參閱[關係節點](../core/relationship-nodes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [TPE 活動檢視節點](../core/tpe-activity-view-nodes.md)