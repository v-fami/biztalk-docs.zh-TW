---
title: "檢查清單： 執行每日維護檢查 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1abae6fb-abce-4f23-a07d-b32ba58cd070
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 281f33f0d880fdd217f3cac303526d7cfc0802f7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="checklist-performing-daily-maintenance-checks"></a>檢查清單： 執行每日維護檢查
本主題描述一些您應該每日，協助監視的狀態檢查的項目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 您必須以一致的方式執行大部分的這些檢查，並封存結果經過一段時間來取得最大的好處。 我們建議您將自動化例行的維護工作檢查盡可能。  
  
|步驟|參考|  
|-----------|---------------|  
|檢查有硬體 RAID （可靠性核取） 中失敗的磁碟。|[管理磁碟](http://go.microsoft.com/fwlink/?LinkId=158666)(http://go.microsoft.com/fwlink/?LinkId=158666)。|  
|檢查需要手動介入，例如擱置訊息 （可靠性檢查） 的訊息。|如需手動檢查擱置的訊息資訊，請參閱[調查協調流程、 連接埠和訊息失敗](http://go.microsoft.com/fwlink/?LinkId=154512)(http://go.microsoft.com/fwlink/?LinkId=154512)。|  
|檢查有任何錯誤或問題與各種 BizTalk Server 中，特別是 MessageBox 資料庫與相關聯的資料庫。|執行 BizTalk MsgBoxViewer 工具可從[BizTalk MsgBoxViewer-從這裡下載最新版本的工具](http://go.microsoft.com/fwlink/?LinkId=151930)(http://go.microsoft.com/fwlink/?LinkId=151930)。 這項工具會分析 BizTalk MessageBox 資料庫與其他資料庫，並產生 HTML 報表包含警告，如果有任何與資料庫相關的其他資訊。 **提示：**您也可以儲存供稍後使用的報表。 與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會有用。 **注意：**使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。|  
|請解決問題，如果任何項目，BizTalk MsgBoxViewer 工具所識別。|執行位於結束字元工具[結束字元](http://go.microsoft.com/fwlink/?LinkId=151931)(http://go.microsoft.com/fwlink/?LinkId=151931)。 此工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。 如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。 **注意：**使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。|  
|請檢查事件記錄檔中錯誤和警告 （管理檢查）。|BizTalk Server 錯誤和警告事件會儲存在應用程式記錄檔中。 事件來源是 「 BizTalk Server >。|  
  
## <a name="see-also"></a>請參閱  
 [維護可靠性](../technical-guides/maintaining-reliability.md)   
 [監控 BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md)