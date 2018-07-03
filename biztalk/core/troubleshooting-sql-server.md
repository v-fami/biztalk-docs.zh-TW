---
title: 疑難排解 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f6707c5-7c6e-4375-bfa6-9b1a86ec5e81
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6418194021678080da3166c359e2b9e14072f221
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004463"
---
# <a name="troubleshooting-sql-server"></a>疑難排解 SQL Server
大多數會影響 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 問題分為下列類別：  
  
- 連線相關問題  
  
- 權限相關問題  
  
- 資料庫大小問題  
  
  本主題說明各個類別，以及您可以用於解決相關問題的步驟。  
  
## <a name="connectivity-related-problems"></a>連線相關問題  
 下列問題最常與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦和裝載 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦之間的連線問題相關聯。  
  
#### <a name="errors-related-to-failed-transactions-or-communication-with-the-underlying-transaction-manager-errors-are-written-to-the-biztalk-server-application-log"></a>與失敗交易相關的錯誤或與基礎交易管理員通訊錯誤會記錄在 BizTalk Server 應用程式記錄檔中  
  
##### <a name="problem"></a>問題  
 表示 MSDTC 交易失敗的錯誤或無法與基礎交易管理員通訊的失敗會記錄在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式記錄檔中。  
  
##### <a name="cause"></a>原因  
 之間的 MSDTC 連線能力[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]失敗。  
  
##### <a name="resolution"></a>解決方案  
 如需有關之間 MSDTC 連線疑難排解資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦並[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。  
  
#### <a name="error-a-connection-was-successfully-established-with-the-server-but-then-an-error-occurred-during-the-pre-login-handshake-occurs-when-connecting-to-remote-sql-server-databases-on-sql-server-2008"></a>在連接到 SQL Server 2008 上的遠端 SQL Server 資料庫時發生錯誤，指出成功建立與伺服器的連線，但在登入前交握期間發生錯誤  
  
##### <a name="problem"></a>問題  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 失去與裝載 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫之遠端 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的連線，並且產生錯誤訊息：  
  
##### <a name="cause"></a>原因  
 如果下列一或多個狀況成立，可能就會發生這個問題：  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 未設定為接受遠端連線。  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦或執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 用戶端電腦上未啟用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的必要通訊協定。  
  
##### <a name="resolution"></a>解決方案  
 請依照下列步驟解決這個問題：  
  
- **SQL Server 介面區組態**工具並不適用於 SQL Server 2008。 若要啟用 SQL Server 2008 電腦上的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 遠端連線，請依照 SQL Server 2008 線上說明中的指示進行。  
  
- 使用**SQL Server 組態管理員**工具，可讓**TCP/IP**和/或**具名管道**通訊協定上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
  1.  按一下 **開始**，指向**所有程式**，然後按一下**SQL Server 組態管理員**。  
  
  2.  按一下以展開**SQL Server 網路組態**，然後按一下**MSSQLSERVER 的通訊協定**。  
  
  3.  以滑鼠右鍵按一下**TCP/IP**通訊協定，然後按一下**啟用**。  
  
  4.  以滑鼠右鍵按一下**具名管道**通訊協定，然後按一下**啟用**。  
  
  5.  關閉**SQL Server 組態管理員**工具。  
  
- 使用**SQL Server 組態管理員**工具，可讓**TCP/IP**和/或**具名管道**通訊協定上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行的用戶端電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
  1.  按一下 **開始**，指向**所有程式**，然後按一下**SQL Server 組態管理員**。  
  
  2.  按一下以展開**SQL Server 網路組態**，然後按一下**ClientProtocols**。  
  
  3.  以滑鼠右鍵按一下**TCP/IP**通訊協定，然後按一下**啟用**。  
  
  4.  以滑鼠右鍵按一下**具名管道**通訊協定，然後按一下**啟用**。  
  
  5.  關閉**SQL Server 組態管理員**工具。  
  
  > [!NOTE]
  >  確定執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用戶端電腦至少有一個通訊協定符合 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上啟用的通訊協定。  
  
#### <a name="a-biztalk-host-instance-fails-and-a-general-network-error-is-written-to-the-application-log-when-the-biztalk-server-based-server-processes-a-high-volume-of-documents"></a>BizTalk 主控件執行個體失敗，而且 BizTalk Server 為基礎的伺服器處理大量文件時，將會寫入應用程式記錄檔的 「 一般網路 」 錯誤  
  
##### <a name="problem"></a>問題  
 在處理大量文件時，BizTalk 主控件執行個體就會失敗，並將 「 一般網路 」 錯誤寫入應用程式記錄檔。  
  
##### <a name="cause"></a>原因  
 會發生此問題是因為 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 實作的安全性功能會減少伺服器的並行 TCP/IP 連線之佇列大小。 此功能可防止阻絕服務的攻擊。  
  
##### <a name="resolution"></a>解決方案  
 如需有關如何解決此問題的詳細資訊，請參閱 <<c0> [ 避免 DBNETLIB 例外狀況](../core/avoiding-dbnetlib-exceptions.md)。  
  
## <a name="permissions-related-problems"></a>權限相關問題  
  
#### <a name="biztalk-server-run-time-or-design-time-operations-fail-and-a-cannot-open-database-requested-in-login-database-error-is-written-to-the-application-log-of-the-biztalk-server-or-sql-server-computer"></a>BizTalk Server 執行階段或設計階段作業失敗，「 無法開啟登入所要求的資料庫\<資料庫\>」 錯誤寫入 BizTalk Server 或 SQL Server 電腦的應用程式記錄檔  
  
##### <a name="problem"></a>問題  
 執行階段或設計階段作業失敗，而且類似如下的錯誤會寫入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦的應用程式記錄檔：  
  
 無法開啟登入所要求的資料庫\<*資料庫*\>。 登入失敗。   
使用者登入失敗\<*使用者名稱*\>。  
  
##### <a name="cause"></a>原因  
 如果指定的帳戶不屬於適當的 Windows 群組或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 角色，就會發生這個錯誤。  
  
##### <a name="resolution"></a>解決方案  
 確定指定的帳戶是適當 Windows 群組的成員或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 角色。 如需有關適當的成員資格的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
## <a name="database-sizing-problems"></a>資料庫大小問題  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫不受抑制地成長，這會嚴重影響 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的效能。 請依照下列步驟來管理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的成長。  
  
#### <a name="the-biztalk-server-messagebox-database-is-growing-unchecked-and-impacting-overall-performance"></a>BizTalk Server MessageBox 資料庫不受抑制地成長，因此影響整體效能  
  
##### <a name="problem"></a>問題  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox 資料庫的成長會嚴重影響 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的效能。  
  
##### <a name="cause"></a>原因  
 如果維護 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的「SQL 代理程式」工作未執行，就會發生這個問題。  
  
##### <a name="resolution"></a>解決方案  
 確定維護 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的「SQL 代理程式」工作執行中。 請參閱[資料庫結構與工作](../core/database-structure-and-jobs.md)如需完整清單，會與一起安裝的 SQL Agent 作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
#### <a name="the-biztalk-server-tracking-database-is-growing-unchecked-and-impacting-overall-performance"></a>BizTalk Server 追蹤資料庫不受抑制地成長，因此影響整體效能  
  
##### <a name="problem"></a>問題  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫不受抑制地成長，而且嚴重影響 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的整體效能。  
  
##### <a name="cause"></a>原因  
 如果未執行步驟來清除和封存 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫，就會發生這個問題。  
  
##### <a name="resolution"></a>解決方案  
 應該執行步驟來清除和封存 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫。 請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [解決 SQL Server 權限問題的指導方針](../core/guidelines-for-resolving-sql-server-permissions-problems.md)