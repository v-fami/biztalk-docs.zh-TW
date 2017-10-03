---
title: "發行階段建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5ac72aa-decd-4b3e-be34-e585e54568b3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a38a8a06fac8dc35fed4d965ea9b7952c5fdfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="release-phase-recommendations"></a>發行階段建議
發行階段包括將目前已驗證完成的系統傳播到生產硬體。  
  
## <a name="propagate-test-bed-optimizations-to-production-systems"></a>將測試台最佳化傳播至生產系統  
 將系統成品和組態傳播到生產硬體並啟動其處理程序是相當簡單的程序。 不過，在實際應用時，可能很容易忽略此階段必須考量的下列效能相關事項：  
  
-   **請確認已傳播平台最佳化**。 在實作及驗證期間，通常會實作任何數目的平台層級效能最佳化。  
  
     比方說，當使用例如 HTTP 外掛式配接器在 Internet Information Server (IIS) 中，有數個可用的配接器將在其中執行的 IIS 中的處理序數目增加，例如的一般效能最佳化。 這一類在發行之前找到的效能最佳化，全都必須加以追蹤並傳播到生產環境。  
  
-   **設定並自動化資料備份、 記錄傳送、 資料保留組態和清除作業**。 在進行生產憑證的過程中，資料庫 (例如 BizTalk 追蹤資料庫和 BAM 資料庫) 備份及清除的頻率是持續性的關鍵，因此必須將這些設定移轉到尚無這種設定的生產環境。  
  
## <a name="see-also"></a>另請參閱  
 [依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md)   
 [需求階段建議](../core/requirements-phase-recommendations.md)   
 [設計階段建議](../core/design-phase-recommendations.md)   
 [實作階段建議](../core/implementation-phase-recommendations.md)   
 [驗證階段建議](../core/verification-phase-recommendations.md)