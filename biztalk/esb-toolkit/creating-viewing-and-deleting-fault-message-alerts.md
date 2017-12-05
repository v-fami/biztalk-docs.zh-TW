---
title: "建立、 檢視和刪除錯誤訊息通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59df2b40-b42c-4167-873c-0819839919da
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55894eca1baa8ca6616c67f623a87e8015a2f32f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="creating-viewing-and-deleting-fault-message-alerts"></a>建立、 檢視和刪除錯誤訊息的警示
ESB 管理入口網站可以產生警示，當錯誤訊息抵達入口網站中，指定警示的準則為基礎的訊息中的值的比較。 在入口網站也可以維護一份通知連結到個別警示的使用者，並主動便會產生警示時，它會通知這些使用者。  
  
### <a name="to-create-and-configure-a-new-alert"></a>若要建立及設定新的警示  
  
1.  開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)查看現有警示的清單，這些警示您目前訂閱。  
  
2.  按一下**建立警示**連結可開啟[新增警示 頁面](../esb-toolkit/add-alert-page.md)。  
  
3.  在**輸入警示名稱** 文字方塊中，輸入新警示的名稱。  
  
4.  在**條件**區段的 新增警示 頁面上，選取一個欄位 (例如**應用程式**，**錯誤類型**，或**錯誤嚴重性**) 中**準則**下拉式清單; 請選取 比較類型 (例如 +、 =、 ！ =、 > =、 < =、 或**像**) 中**運算子**下拉式清單，並輸入或選取從清單或文字的第三個方塊的值 (名為**值**)。 當您選取**準則**值相符的值的下拉式清單或文字方塊中顯示的頁面上變更。 所有的條件會組合使用**AND**運算子。  
  
5.  按一下**新增**連結新增至清單中，這種狀況，然後重複上述步驟，視需要新增更多條件。  
  
6.  按一下**儲存**按鈕以建立新的警示，具有指定的名稱和條件。  
  
### <a name="to-view-details-of-an-existing-alert-or-delete-an-existing-alert"></a>若要檢視現有警示的詳細資料，或刪除現有的警示  
  
1.  開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)。  
  
2.  若要刪除警示，請按一下**刪除警示**現有警示的 [動作] 欄中的圖示。  
  
    > [!NOTE]
    >  非系統管理使用者可以刪除只有警示他們是擁有者，以及其目前沒有任何訂閱者。 您必須刪除其他警示系統管理員身分來登入入口網站。  
  
3.  若要檢視警示的詳細資訊，請按一下**檢視**現有警示的 [動作] 欄中的圖示。 這會開啟 [警示檢視器] 頁面。  
  
4.  按一下**匯出至 Excel**下載的格式，您可以在 Microsoft Excel 中檢視警示的完整清單。