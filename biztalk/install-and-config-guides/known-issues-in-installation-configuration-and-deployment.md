---
title: 安裝、 設定及部署中的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed1c08eb-d647-4a4a-b9a3-c4d84e8d4b82
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda1bd5c8167bbf9f6049b3620c0c949950b1e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299830"
---
# <a name="known-issues-in-installation-configuration-and-deployment"></a>安裝、組態和部署中的已知問題
## <a name="some-biztalk-edias2-artifacts-are-still-active-after-unconfiguring"></a>有些 BizTalk EDI/AS2 成品在取消設定後依然在作用中  
  
##### <a name="problem"></a>問題  
 在您取消設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BizTalk EDI/AS2 功能之後，有些與 EDI 和 AS2 處理有關的 BizTalk Server 成品，仍然可以在 BizTalk 群組組態的內容中運作。 這些成品將會包括 EDI 和 AS2 管線，以及批次協調流程。 因此，即使取消設定 BizTalk EDI/AS2 功能，您仍然可以執行基本的 EDI 和 AS2 處理。  
  
##### <a name="cause"></a>原因  
 這時有存在與 EDI 和 AS2 處理相關聯的使用中連接埠。 有些成品會在這些連接埠保持使用狀態時繼續運作。  
  
##### <a name="resolution"></a>解決方案  
 若要停用所有的 EDI/AS2 成品，您應該停用、停止或刪除與 EDI 和 AS2 處理相關聯的連接埠。  
  
## <a name="if-the-biztalk-server-computer-or-sql-server-computer-is-renamed-after-biztalk-server-configuration-the-configuration-wizard-will-fail"></a>如果 BizTalk Server 電腦或 SQL Server 電腦在 BizTalk Server 組態之後重新命名，組態精靈將會失敗  
  
##### <a name="problem"></a>問題  
 這個問題可能會以數種方式出現：  
  
-   BizTalk Server 組態將會正確載入 [概觀] 頁面，不過當嘗試設定某項功能時，功能選項並未出現在畫面上。  
  
-   組態精靈無法連接到 SQL Server。  
  
-   嘗試取消設定所有功能會取消設定部分功能，而非全部功能。  
  
##### <a name="cause"></a>原因  
 BizTalk Server 組態會儲存電腦網路名稱。 當電腦重新命名後，BizTalk Server 組態與組態精靈找不到 BizTalk Server。 如果在設定 BizTalk Server 後重新命名 SQL Server 電腦，也會發生相似的問題。  
  
##### <a name="resolution"></a>解決方案  
 請勿重新命名 BizTalk Server 電腦或 SQL Server 電腦。 如果必須重新命名伺服器，請在重新命名電腦之前取消設定所有 BizTalk 功能。 接著，在重新命名電腦後，重新設定 BizTalk Server 功能。  
  
## <a name="the-biztalk-server-business-rules-configuration-wizard-fails"></a>BizTalk Server 商務規則組態精靈失敗  
  
### <a name="problem"></a>問題  
  
-   BizTalk Server 商務規則組態精靈失敗，並出現「一些元件的組態已經失敗，而且沒有套用任何設定到那些元件」錯誤。  
  
-   在已順利設定商務規則引擎的 BizTalk Server 電腦上，無法啟動並且無法手動啟動規則引擎更新服務。  
  
 發生這個問題時，BizTalk Server 電腦應用程式記錄檔中可能會產生與下例類似的錯誤：  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
### <a name="cause"></a>原因  
 Microsoft 惡意程式碼防護中心已發行更新過的簽章檔案，以解決來自 SettingsModifier:Win32/PossibleHostsFileHijack 的潛在威脅。 這個更新過的簽章檔案可能會讓 Microsoft 惡意程式碼偵測軟體 (例如 Windows Defender) 更新本機 HOSTS 檔案，以減輕來自 SettingsModifier:Win32/PossibleHostsFileHijack 的威脅。 基於這些變更，可能無法啟動 BizTalk Server 規則引擎更新服務。  
  
### <a name="resolution"></a>解決方案  
 更新本機 HOSTS 檔案，以加入下行︰  
  
```  
127.0.0.1         localhost  
```  
  
 HOSTS 檔案位於 %systemroot%\drivers\etc\ 目錄中。  
  
> [!NOTE]
>  如需解決 SettingsModifier:Win32/PossibleHostsFileHijack 潛在威脅的 Microsoft 惡意程式碼防護中心簽章更新的詳細資訊，請瀏覽 [http://go.microsoft.com/fwlink/?LinkId=146221](http://go.microsoft.com/fwlink/?LinkId=146221)。  
  
## <a name="enlistment-of-an-orchestration-fails-if-referenced-assemblies-are-missing-from-the-gacmgmt-db"></a>如果 GAC/管理資料庫中的參考組件遺失，則登錄協調流程會失敗  
  
##### <a name="problem"></a>問題  
 如果 GAC/管理資料庫中的參考 (參考為協調流程的 C# 組件) 遺失，則登錄協調流程會失敗。 重新部署的過程中，可能需要根據現有狀態登錄協調流程。 如果參考遺失，則部署也會失敗。  
  
##### <a name="cause"></a>原因  
 GAC/管理資料庫中參考的組件遺失。  
  
##### <a name="resolution"></a>解決方案  
 將參考的組件加入 GAC 中或加入做為資源，如此就能儲存在管理資料庫中，並且可在登錄協調流程時存取。  

## <a name="community-blog-biztalk-2013-r2-bugs-issues--quirks"></a>社群部落格︰BizTalk 2013 R2 Bug、問題和缺點

[BizTalk Server 2013 R2 已知 Bug、問題和缺點](https://cdijkgraaf.wordpress.com/2016/08/12/biztalk-2013-r2-known-bugs-issues-quirks/)
  
## <a name="additional-configuration-topics"></a>其他組態主題  
  
 [設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)  
  
 [在 Azure VM 上設定 BizTalk Server](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
  [設定叢集中的 BizTalk Server](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)
  
 [保護 BizTalk Server 部署安全](../install-and-config-guides/securing-your-biztalk-server-deployment.md)  
  