---
title: 疑難排解效能 Issues3 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a348c4b-7df2-43e9-810c-1f538a97d7e1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40f7ae950a7078152d2952fb72ebe39303d41813
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998807"
---
# <a name="troubleshooting-performance-issues"></a>針對效能問題進行疑難排解
本節包含一般的指導方針來診斷及解決效能問題的相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和其相依性。 這些指導方針可能也用於事先，它們變成嚴重的問題之前找出潛在的問題。  
  
## <a name="diagnosing-performance-problems-in-the-biztalk-server-environment"></a>BizTalk Server 環境中的診斷效能問題  
 通常是效能問題可以縮小至下列元件之一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境：  
  
- 接收配接器或系統的配接器接收的文件。 例如，如果文件接收的 HTTP 配接器以低於最佳速率的問題可能在使用 HTTP 接收配接器或張貼到 HTTP 配接器的用戶端。  
  
- 協調流程服務執行個體。  
  
- 效能[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
- 傳送配接器，或是配接器將文件傳送至的系統。 比方說，如果文件傳送的 SQL 配接器以低於最佳速率則問題可能與 SQL 傳送配接器或執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，SQL 配接器正在更新。  
  
  請使用下列指導方針，以協助辨識效能不佳的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境元件：  
  
- 請擷取在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 事件檢視器中產生的警告或錯誤訊息。  
  
- 遵循 「 識別效能瓶頸 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154238 ](http://go.microsoft.com/fwlink/?LinkId=154238)以協助找出效能瓶頸。  
  
  一旦辨識出效能不佳的元件後，請遵循正確的指導方針來協助解決問題：  
  
  **解決與傳送和接收配接器相關的效能問題的指導方針**  
  
- 如需有關問題的疑難排解資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器，請參閱中的 < 疑難排解 BizTalk Server 配接器 >[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在協助[ http://go.microsoft.com/fwlink/?LinkId=154240 ](http://go.microsoft.com/fwlink/?LinkId=154240)。 本節包含一般的疑難排解資訊，包括如何設定特定記錄配接器的相關資訊和可用的資訊診斷網路問題，問題的登錄檔有問題的問題與 MSDTC、系統和 IIS 的問題。  
  
- 如需 MSDTC 問題疑難排解，憑證、 企業單一登入，並[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，參閱的適當章節的 < 疑難排解 BizTalk Server 相依性 >[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在協助[ http://go.microsoft.com/fwlink/?LinkId=154242](http://go.microsoft.com/fwlink/?LinkId=154242).  
  
  **解決與協調流程相關的效能問題的指導方針**  
  
- 如需修改 BTSNTSvc.exe.config 檔案之適當章節的資訊，請參閱 [協調流程引擎組態] 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154244 ](http://go.microsoft.com/fwlink/?LinkId=154244)。  
  
  **解決 SQL Server 相關的效能問題的指導方針**  
  
- SQL Server Profiler 可以用來擷取傳送至的 TRANSACT-SQL 陳述式[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]而[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]這些陳述式的結果集。 由於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]緊密整合[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，分析[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]追蹤設定檔可以是有用的工具，分析可能會發生的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讀取和寫入時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。 如需有關如何使用資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Profiler，請參閱中的 「 使用 SQL Server Profiler 」[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在線上叢書 》 [ http://go.microsoft.com/fwlink/?linkid=104423 ](http://go.microsoft.com/fwlink/?linkid=104423)。  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio 可用來執行 SQL 陳述式，直接針對[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。 這項功能可用來查詢[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或更新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在某些情況下的資料庫。 如需使用 SQL Server Management Studio 來執行 SQL 陳述式的詳細資訊，請參閱 < 撰寫、 分析和與 SQL Server Management Studio 的 編輯指令碼 」 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在線上叢書 》 [ http://go.microsoft.com/fwlink/?linkid=104425 ](http://go.microsoft.com/fwlink/?linkid=104425)。  
  
- 如需有關解決效能問題的相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱中的 < 疑難排解 SQL Server >[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在協助[ http://go.microsoft.com/fwlink/?LinkId=154250 ](http://go.microsoft.com/fwlink/?LinkId=154250)。  
  
## <a name="see-also"></a>另請參閱  
 [http://go.microsoft.com/fwlink/?linkid=104430](http://go.microsoft.com/fwlink/?linkid=104430)