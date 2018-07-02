---
title: 監視 BizTalk Server 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f137fc5-0e95-4952-8465-008771a1a377
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b041822791b08890a34c39f3658de879062d9fb7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973815"
---
# <a name="monitor-the-biztalk-server-databases"></a>監視 BizTalk Server 資料庫
您可以執行監視 BizTalk Server SQL Agent 作業，以識別任何已知的問題，管理、 訊息方塊或 DTA 資料庫中。 當您在 BizTalk Server 管理主控台中設定 BizTalk 群組或從舊版本升級 BizTalk 時，就會建立此工作。  
  
## <a name="the-monitor-biztalk-server-job"></a>監視 BizTalk Server 作業  
 [監控 BizTalk Server] 作業會在管理、訊息方塊或 DTA 資料庫中掃描下列問題：  
  
> [!NOTE]  
>  [監控 BizTalk Server] 工作只會掃描問題。 並不會修正找到的問題。  
  
- 不具任何參考的訊息  
  
- 不具參考計數的訊息  
  
- 參考計數小於 0 的訊息  
  
- 不具多工緩衝處理列的訊息參考  
  
- 不具執行個體的訊息參考  
  
- 不具執行個體的執行個體狀態  
  
- 不具對應執行個體的執行個體訂閱  
  
- 被遺棄的 DTA 服務執行個體  
  
- 被遺棄的 DTA 服務執行個體例外狀況  
  
- 啟用全域追蹤選項時，任何主控件執行個體上未執行 TDDS  
  
  已設定 [監控 BizTalk Server] 工作，而且已自動化成一週執行一次。 因為工作會耗用大量運算資源，我們建議您排程的停機時間或低流量期間執行。  
  作業失敗時，如果遇到任何問題;傳回的錯誤字串會包含找到的問題數。 否則表示已順利執行。 您可以在工作記錄中查看詳細資料。 如果您是系統管理員權限執行作業，將記錄錯誤字串，作業記錄和 SQL Server 應用程式記錄檔。  
  
> [!IMPORTANT]  
>  這項作業失敗不一定是構成重要的問題，但相反地，應該調查和解決一部分的 BizTalk Server 資料庫的定期維護的問題。 萬一它會探索其中一個上述問題，這項作業會失敗所設計。 如上面所列問題的詳細資訊，以及存取公用程式常用的 Microsoft 產品支援服務疑難排解這些問題，請參閱[使用 BizTalk 結束字元來解決 BizTalk 所識別的問題MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=210367) (http://go.microsoft.com/fwlink/?LinkId=210367)。