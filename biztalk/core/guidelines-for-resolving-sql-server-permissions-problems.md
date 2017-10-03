---
title: "解決 SQL Server 權限問題的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c24512-5f65-4363-b806-8dd52b22f179
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db02fd2a981d3f1dc34924e680caf5926f67871a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-resolving-sql-server-permissions-problems"></a>解決 SQL Server 權限問題的指導方針
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會密集使用 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫進行執行階段作業，因此正確設定 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 權限非常重要。 本主題包含一些一般指導方針，可用來排除大多數的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的權限問題，另外也包含疑難排解步驟，您可以遵循這些步驟，解決對 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 造成影響的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 權限問題。  
  
## <a name="general-guidelines"></a>一般指導方針  
  
-   **使用 BizTalk Server 的多重電腦安裝的網域使用者和群組**  
  
     在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以執行於多電腦實例時 (例如，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同電腦上)，您必須使用網域使用者群組和帳戶。 請勿嘗試設定或執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中*傳遞*藉此避免使用網域群組和帳戶的每一部電腦建立成對的使用者名稱和密碼的驗證案例。 在有些實例中這種通過實例可能會正常運作，但在其他實例中這會造成 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 失敗，因此是不受支援的組態。  
  
     如需有關安裝和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在多重電腦組態中，下載安裝指南 》，網址[安裝指南相關的 BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582)。  
  
-   **請確定適當的 Windows 使用者和群組已在適當的 SQL Server 角色定義**  
  
     請確認正確[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]主題中的資料表所列出的角色成員資格[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
-   **使用 SQL Server Profiler 診斷權限問題**  
  
     設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Profiler 追蹤來監視**稽核登入失敗事件**來收集有關權限失敗的詳細的資訊。 如需有關如何使用資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]程式碼剖析工具，請參閱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="the-sql-server-jobs-that-are-installed-with-biztalk-server-fail-to-execute"></a>與 BizTalk Server 一起安裝的 SQL Server 作業無法執行  
  
##### <a name="problem"></a>問題  
 隨 SQL Server 工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]失敗，而且類似下列的錯誤會產生[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應用程式記錄檔：  
  
 事件類型: 警告  
  
 事件來源: SQLSERVERAGENT  
  
 事件類別目錄: 工作引擎  
  
 事件識別碼: 208  
  
 日期: 6/29/2008  
  
 時間: 4:45:01 PM  
  
 使用者: N/A  
  
 電腦： *SQLServer*  
  
 描述：  
  
 SQL Server 排程作業 '備份 BizTalk Server'  
  
 (0x4AC7C44A48541443927A56C5C6699ECF)-狀態： 失敗-在上叫用： 2008年-6-29 13:45:01-訊息： 工作失敗。  工作由排程 305 (MarkAndBackupLogSched) 叫用。 要執行的最後一個步驟是步驟 1 (BackupFull)。  
  
 **-和-**  
  
 事件類型： 資訊  
  
 事件來源: MSSQLSERVER  
  
 事件類別目錄: (4)  
  
 事件識別碼： 17055  
  
 日期: 6/29/2008  
  
 時間: 4:45:01 PM  
  
 使用者: N/A  
  
 電腦： *SQLServer*  
  
 描述：  
  
 18456: 使用者 'NT AUTHORITY\SYSTEM' 登入失敗。  
  
##### <a name="cause"></a>原因  
 如果已從 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 刪除 BUILTIN\Administrators 登入，便會發生這個錯誤。 如果已刪除 BUILTIN\Administrators 登入，sqlmaint.exe 就無法登入 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，而導致 SQL 工作無法執行。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個錯誤，請重建 BUILTIN\Administrators 登入，並將其加入至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫和 Master 資料庫的 db_owner 角色中。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 SQL Server](../core/troubleshooting-sql-server.md)   
 [疑難排解 BizTalk Server 權限](../core/troubleshooting-biztalk-server-permissions.md)