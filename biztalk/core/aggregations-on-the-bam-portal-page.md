---
title: "BAM 入口網站上的彙總頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], alerts
- aggregations [BAM], viewing results
- alerts, aggregations
- Aggregations page [BAM portal]
- BAM portal, aggregations
ms.assetid: 6bc1a6f2-9e9a-4db6-aaa1-188ed2f2641f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a61df22bf5d07bd1b4d955f2baf884459de52998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="aggregations-on-the-bam-portal-page"></a>BAM 入口網站頁面上的彙總
商務使用者、開發人員和商務分析師使用 BAM 入口網站頁面呈現所需的彙總資料，這是預先計算的資料集摘要，可顯示該資料集具代表性的特性。 BAM 入口網站的 [彙總] 頁面能讓您以圖形化圖表和樞紐分析表的形式顯示彙總資料。  
  
## <a name="the-aggregations-page"></a>彙總頁面  
 [彙總] 頁面會顯示活動的結果，以共同傳達程序或整體商務的狀況。 例如，使用者可能只需要簡單的圓形圖，顯示所收到的 1,000 張發票明細，以查看每張發票的處理階段 (400 張還在評估，400 張已拒絕，100 張已付款，100 張還在分配款項)。  
  
### <a name="creating-alerts-for-aggregations"></a>建立彙總的警示  
 您可以使用彙總做為建立警示的基礎 (如果超過 500 張發票在評估階段時通知我)。 若要這樣做，以滑鼠右鍵按一下任何樞紐分析表資料格，然後選取**設定警示**，或按一下資料格，並按一下 **設定警示**按鈕右邊的樞紐分析表報表。 如需有關如何建立警示的詳細資訊，請參閱[如何設定警示](../core/how-to-set-an-alert.md)。  
  
### <a name="viewing-individual-results-of-aggregations"></a>檢視彙總的個別結果  
 您也可以選取任何彙總數量 (例如，400 張發票仍在評估中)，並檢視彙總的個別結果。 您可以存取個別結果的任何樞紐分析表儲存格上按一下滑鼠右鍵，然後選取**顯示結果**。 執行此動作後，將會帶領您前往 [活動搜尋] 頁面，搜尋會自動建構然後顯示結果 (以 400 張發票來說，每張發票都有一筆記錄)。  
  
> [!NOTE]
>  某些 BAM 檢視沒有關聯的彙總，所以根據檢視建立的方式不同，或許未能存取到相關資訊。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 入口網站](../core/bam-portal.md)   
 [BAM 入口網站上的活動搜尋頁面](../core/activity-search-on-the-bam-portal-page.md)   
 [BAM 入口網站上的警示管理員頁面](../core/alert-manager-on-the-bam-portal-page.md)