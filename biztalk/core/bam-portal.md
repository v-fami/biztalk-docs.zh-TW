---
title: BAM 入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM portal, alerts
- activities [BAM], searching
- BAM portal
- BAM portal, features
- aggregations [BAM], BAM portal
- BAM portal, activity searches
- alerts, Alert Manager
- BAM portal, about BAM portal
- BAM, portals
- BAM portal, aggregations
ms.assetid: 593c9637-6b97-4ad8-8af7-2b49325acf10
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f86aad2a183653f00f1f7fc2533ac6956b2a85f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232078"
---
# <a name="bam-portal"></a>BAM 入口網站
商務使用者使用 BAM 入口網站來監控「關鍵效能指標」(KPI)，此 KPI 會測量達到商務目標的進度，以及有關商務程序的其他資訊。 商務分析師使用 BAM 入口網站來監督觀察模型的建立，觀察模型是商務程序中可見性需求的高階定義。 系統管理員會在各種不同的監控活動中使用觀察模型，其中包括監控商務程序管理系統的狀況。  
  
## <a name="what-is-the-bam-portal"></a>何謂 BAM 入口網站？  
 BAM 入口網站提供商務程序即時、端對端的可見性， 它是 Web 架構的功能，其中包含 ASP.NET 網頁的集合。 您可以自訂 BAM 來增強效能及使用者經驗。  
  
## <a name="why-use-the-bam-portal"></a>為什麼要使用 BAM 入口網站？  
 BAM 入口網站可讓您執行搜尋、彙總資料並在 BAM 檢視 (屬於商務資料的觀點) 上設定警示。 此可見性能夠為您的商務提供必要的 KPI 資訊，或是在您實作其他解決方案 (例如擴充 Microsoft Office Excel 試算表、使用 SQL Reporting 或建置自訂使用者介面 (UI)) 時，做為概念的證明。  
  
## <a name="bam-portal-components"></a>BAM 入口網站元件  
 下列概要說明 BAM 入口網站元件。 如需詳細資訊，請參閱＜另請參閱＞中的主題。  
  
### <a name="activity-searches"></a>活動搜尋  
 您可以使用 BAM 入口網站對 BAM 資料執行搜尋，以尋找特定 BAM 活動。 您可以新增和移除搜尋子句，藉此建立查詢，以顯示符合您想要加以警示之準則的活動。  
  
 查詢可以儲存並重複使用， 也可以做為警示的基礎，例如收到特定客戶的訂單時的通知。  
  
### <a name="aggregations"></a>Aggregations  
 入口網站可讓您擷取資料的快照集，並以圖形化圖表和樞紐分析表的形式顯示。 此資料提供您對該程序或整體商務狀況的可見性。 例如，使用者可能只需要簡單的圓形圖，顯示今天所收到的 1,000 張發票明細，以查看每張發票的處理階段 (400 張還在評估，400 張已拒絕，100 張已付款，100 張還在分配款項)。  
  
 所呈現的資料可以做為建立警示的基礎，例如：如果超過 500 張發票都在「評估」階段時通知我。  
  
### <a name="alert-manager"></a>警示管理員  
 入口網站提供了使用者介面，可以用來建立警示和編輯現有警示。 警示採用來自 [活動搜尋] 或 [彙總] 頁面所要監控的條件。 您可以在「警示管理員」中填入警示的相關部分，例如通知對象、通知方式 (例如電子郵件)、其他人是否能看見以及訂閱警示等等。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BAM 入口網站的元件](../core/components-of-the-bam-portal.md)  
  
-   [規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)  
  
-   [BAM 入口網站中的活動搜尋](../core/activity-searches-in-the-bam-portal.md)  
  
-   [BAM 入口網站中的彙總](../core/aggregations-in-the-bam-portal.md)  
  
-   [BAM 入口網站中的警示](../core/alerts-in-the-bam-portal.md)  
  
-   [BAM 入口網站的協助工具](../core/accessibility-for-the-bam-portal.md)  
  
-   [BAM 入口網站的安全性考量](../core/security-considerations-for-the-bam-portal.md)  
  
-   [BAM 入口網站中的已知的問題](../core/known-issues-in-the-bam-portal.md)  
  
## <a name="see-also"></a>另請參閱  
 [BAM 入口網站上的活動搜尋頁面](../core/activity-search-on-the-bam-portal-page.md)   
 [BAM 入口網站上的彙總頁面](../core/aggregations-on-the-bam-portal-page.md)   
 [BAM 入口網站上的警示管理員頁面](../core/alert-manager-on-the-bam-portal-page.md)