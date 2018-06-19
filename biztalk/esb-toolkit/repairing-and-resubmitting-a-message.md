---
title: 修復和重新提交訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccd720b4-44a2-4c44-bf6e-8cf5e9ded1aa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e524ffca1b79032dce55f74e195032d14ec1bf9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295054"
---
# <a name="repairing-and-resubmitting-a-message"></a>修復和重新提交訊息
若要修復並重新提交失敗的訊息，使用 ESB 管理入口網站的 [錯誤] 頁面。  
  
### <a name="to-repair-and-resubmit-a-message-for-processing"></a>修復並重新提交訊息，以進行處理  
  
1.  找出所需的錯誤訊息上[入口網站錯誤網頁](../esb-toolkit/portal-faults-page.md)ESB 管理入口網站頁面。 使用 [錯誤] 頁面上的篩選功能來搜尋特定訊息。 空白的任何控制項來擷取所有的訊息。 請注意，篩選非常大的錯誤資料庫上可能需要花費幾秒鐘的時間才會顯示適當的結果。 圖 1 所示的錯誤頁面。  
  
     ![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")  
  
     **圖 1**  
  
     **ESB 管理入口網站的 [錯誤] 頁面**  
  
2.  按一下以開啟所需的錯誤訊息的資料列中的任何位置[入口網站錯誤訊息檢視器](../esb-toolkit/portal-fault-message-viewer.md)頁面[錯誤詳細資料檢視](../esb-toolkit/fault-details-view.md)。  
  
3.  捲動到 錯誤詳細資料檢視的錯誤訊息中包含的訊息清單的底部。 圖 2 說明**訊息**錯誤檢視器 頁面的區段。  
  
     ![訊息區段](../esb-toolkit/media/ch8-messagessection.gif "Ch8 MessagesSection")  
  
     **圖 2**  
  
     **ESB 管理入口網站的 [錯誤檢視器] 頁面的 [訊息] 區段**  
  
4.  按一下您想要重新提交訊息的訊息識別項。 這會開啟中的訊息[訊息詳細資料檢視](../esb-toolkit/message-details-view.md)，其中顯示個別的訊息和訊息內容的詳細資料，如圖 3 所示。  
  
     ![訊息檢視器](../esb-toolkit/media/ch8-messageviewer.gif "Ch8 MessageViewer")  
  
     **圖 3**  
  
     **ESB 管理入口網站的 [訊息檢視器] 頁面**  
  
5.  按一下**編輯**包含訊息內容切換至編輯模式，，然後編輯 訊息內容所需的文字方塊底下的連結。 例如，您可能需要變更服務方法引動過程訊息中所包含的參數。 請注意，您必須遵循 （例如 XML 或一般檔案格式） 的原生文件樣式以防止拒絕重新提交的訊息。 圖 4 說明**訊息詳細資料**訊息編輯器頁面區段。  
  
     ![訊息詳細資料](../esb-toolkit/media/ch8-messagedetails.gif "Ch8 MessageDetails")  
  
     **圖 4**  
  
     **ESB 管理入口網站的 訊息檢視器 頁面的 訊息詳細資料區段**  
  
6.  編輯之後的訊息，請選取 [重新送出的位置之下訊息文字] 方塊的下拉式清單中。 此清單會顯示動態擷取可用的端點的清單。 您必須選取設定為重新送出端點的端點。 重新提交適用的下列端點：  
  
    -   **WCF 上手**。 此端點是 ESB 行程服務 WCF 上手，僅適用於 XML 檔案。 入口網站的 Web.config 檔案中定義此上手的 URL。  
  
    -   **SOAP 上手**。 此端點是 ESB 行程服務 ASMX 上手，僅適用於 XML 檔案。 入口網站的 Web.config 檔案中定義此上手的 URL。  
  
    -   **任何接收位置使用 BizTalk HTTP 配接器**。 此選項適用於 XML 檔案和一般檔案。  
  
7.  按一下**重新提交**送出郵件的連結。 訊息，指出**重新送出狀態**在訊息內容文字方塊下方會出現。  
  
8.  如有需要，開啟[稽核記錄檔 頁面](../esb-toolkit/audit-log-page.md)從**Admin**索引標籤，確認訊息重新提交，如圖 5 所示。  
  
     ![AuditLog 頁面小型檢視](../esb-toolkit/media/ch8-auditlogpagesmallview.gif "Ch8 AuditLogPageSmallView")  
  
     **圖 5**  
  
     **ESB 管理入口網站的 [稽核記錄] 頁面**