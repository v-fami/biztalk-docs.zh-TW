---
title: '檢查清單: 作業的安全環境中規劃 |Microsoft 文件'
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d6464df-6736-46e2-a0c7-cc2a256c5144
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c99c14f16df3f6b98555a4006706eb7804f24a34
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976828"
---
# <a name="checklist-planning-for-operations-in-a-secure-environment"></a>作業的安全環境中規劃檢查清單：
執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安全的環境中需要額外的步驟部署和組態。 預設作業系統安裝不需要採取這些帳戶，但案例嚴格的安全性原則已套用的位置，而應該納入本章節中的帳戶資訊。 層級的限制套用到伺服器上可能有所差異，但是下列資訊應涵蓋大部分的情況下，會是很好的起點。  
  
-   [執行 BizTalk Server 之電腦的安全性考量](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_BTSSec)  
  
-   [執行 SQL Server 之電腦的安全性考量](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_SQLServSec)  
  
-   [其他安全性考量](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_AddSec)  
  
<a name="BKMK_BTSSec"></a>   
## <a name="security-considerations-for-computers-running-biztalk-server"></a>執行 BizTalk Server 之電腦的安全性考量  
 下表所示的安全性相關設定執行的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
### <a name="user-rights-assignment"></a>使用者權限指派  
 若要啟動 使用者權利指派 MMC 嵌入式管理單元，請按一下**啟動**，按一下 **系統管理工具**，然後按一下 **本機安全性原則**。 在**本機安全性原則**MMC 嵌入式管理單元中，展開**安全性設定**，依序展開**本機原則**，然後按一下 **使用者權限指派**.  
  
|原則設定|值|參考和詳細資料|  
|--------------------|------------|---------------------------|  
|登入為服務|BizTalk 應用程式使用者|執行 BizTalk 主控件執行個體所需。 如需不同的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](http://go.microsoft.com/fwlink/?LinkID=155755)(http://go.microsoft.com/fwlink/?LinkID=155755)。|  
|登入為服務|規則引擎更新服務帳戶|需要執行規則引擎更新服務。 如需不同的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](http://go.microsoft.com/fwlink/?LinkID=155755)(http://go.microsoft.com/fwlink/?LinkID=155755)。|  
|登入為服務|SSO 服務帳戶|需要執行 「 企業單一登入服務。 如需不同的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](http://go.microsoft.com/fwlink/?LinkID=155755)(http://go.microsoft.com/fwlink/?LinkID=155755)。|  
  
### <a name="system-services"></a>系統服務  
 若要啟動服務 MMC 嵌入式管理單元，請按一下**啟動**，按一下 [**執行**，然後在**執行**] 對話方塊中，輸入`services.msc`按下 ENTER。  
  
|服務名稱|啟動類型<sup>1</sup>|詳細資料|使用者<sup>2</sup>|Permissions|詳細資料|  
|------------------|------------------------------|-------------|----------------------|-----------------|-------------|  
|COM+ 系統應用程式|自動|BizTalk 才能正確執行|(預設值)|||  
|DHCP 用戶端|自動|即使是靜態的 IP 位址所需|(預設值)|||  
|分散式交易協調器|自動|BizTalk 才能正確執行|SSO 服務帳戶|完整控制|啟動 SSO 服務所需|  
||||BizTalk 主控件服務帳戶|完整控制|啟動 BizTalk 主控件所需|  
||||網路服務|完整控制|所需的 IIS|  
|HTTP SSL<sup>3</sup>|自動|所需的 IIS|(預設值)|||  
|IPSEC 服務<sup>3</sup>|自動|如果使用 IPSEC 會增加網路安全性|(預設值)|||  
|Netlogon|(預設值)||本機服務|完整控制||  
|NT LM 安全性支援提供者<sup>3</sup>|自動|所需的 Kerberos 驗證[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL 中|(預設值)|||  
|Remote Access Connection Manager|(預設值)||SSO 服務帳戶|完整控制|啟動 SSO 服務所需|  
||||BizTalk 主控件服務帳戶|完整控制|啟動 BizTalk 主控件所需|  
||||網路服務|完整控制|所需的 IIS|  
|遠端程序呼叫 (RPC) 定位器|自動|所需的 BizTalk|(預設值)|||  
|WinHTTP Web Proxy 自動探索服務|(預設值)||SSO 服務帳戶|完整控制|啟動 SSO 服務所需|  
||||BizTalk 主控件服務帳戶|完整控制|啟動 BizTalk 主控件所需|  
  
 <sup>1</sup> （預設值） 的值表示，不會變更安全性原則所套用的預設設定  
  
 <sup>2</sup> （預設值） 的值表示尚未變更服務的預設使用者權限  
  
### <a name="registry-settings"></a>登錄設定  
 若要啟動登錄編輯程式，請按一下**啟動**，按一下 [**執行**，然後在**執行**] 對話方塊中，輸入`regedit`按下 ENTER。  
  
|索引鍵|使用者|Permissions|詳細資料|  
|---------|----------|-----------------|-------------|  
|HKLM\ SYSTEM\CurrentControlSet\Services\DHCP|網路服務|完整控制|DHCP 用戶端服務所需|  
|HKLM\ SYSTEM\CurrentControlSet\Services\TCPIP|網路服務|完整控制|DHCP 用戶端服務所需|  
  
<a name="BKMK_SQLServSec"></a>   
## <a name="security-considerations-for-computers-running-sql-server"></a>執行 SQL Server 之電腦的安全性考量  
 下表所示的安全性相關設定執行的電腦上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
### <a name="user-rights-assignment"></a>使用者權限指派  
 若要啟動 使用者權利指派 MMC 嵌入式管理單元，請按一下**啟動**，按一下 **系統管理工具**，然後按一下 **本機安全性原則**。 在**本機安全性原則**MMC 嵌入式管理單元中，展開**安全性設定**，依序展開**本機原則**，然後按一下 **使用者權限指派**.  
  
|原則設定|值|參考和詳細資料|  
|--------------------|------------|---------------------------|  
|作為作業系統的一部分|SQL Server Agent 服務帳戶，SQL Server 服務帳戶|執行所需[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
|調整處理序的記憶體配額|SQL Server Agent 服務帳戶，SQL Server 服務帳戶|執行所需[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
|略過周遊檢查|SQL Server Agent 服務帳戶，SQL Server 服務帳戶|執行所需[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
|建立通用物件|SQL Server 服務帳戶|所需的 SSIS 服務。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
|讓電腦和使用者帳戶，以受信任可以委派|SQL Server 服務帳戶，SQL Server 的伺服器，BizTalk Server 的伺服器，SQL Server 叢集名稱|BizTalk Server 所需。 伺服器名稱的格式為\<servername\>$。 如需詳細資訊，請參閱[How to： 在 SQL Server 容錯移轉叢集上啟用 Kerberos 驗證](http://go.microsoft.com/fwlink/?LinkId=157417)(http://go.microsoft.com/fwlink/?LinkId=157417)。|  
|登入為服務|SQL Server Agent 服務帳戶，SQL Server 服務帳戶|執行所需[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
|登入為服務|SSO 服務帳戶|需要執行 「 企業單一登入服務。 如需不同的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](http://go.microsoft.com/fwlink/?LinkID=155755)(http://go.microsoft.com/fwlink/?LinkID=155755)。|  
|以批次工作登入|SQL Server Agent 服務帳戶，SQL Server 服務帳戶|執行所需[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
|取代處理序層級的 Token|SQL Server Agent 服務帳戶，SQL Server 服務帳戶|執行所需[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需詳細資訊，請參閱[設定 Windows 服務帳戶](http://go.microsoft.com/fwlink/?LinkId=157415)(http://go.microsoft.com/fwlink/?LinkId=157415)。|  
  
### <a name="system-services"></a>系統服務  
 若要啟動服務 MMC 嵌入式管理單元，請按一下**啟動**，按一下 [**執行**，然後在**執行**] 對話方塊中，輸入`services.msc`按下 ENTER。  
  
|服務名稱|啟動類型<sup>1</sup>|詳細資料|使用者<sup>2</sup>|Permissions|詳細資料|  
|------------------|------------------------------|-------------|----------------------|-----------------|-------------|  
|DHCP 用戶端|自動|即使是靜態的 IP 位址所需|(預設值)|||  
|分散式交易協調器|手動|叢集服務所管理的服務啟動|SSO 服務帳戶|完整控制|啟動 SSO 服務所需|  
||||網路服務|完整控制|所需的 IIS|  
|HTTP SSL<sup>3</sup>|自動|所需的 IIS|(預設值)|||  
|IPSEC 服務<sup>3</sup>|自動|如果使用 IPSEC 會增加網路安全性|(預設值)|||  
|Netlogon|(預設值)||本機服務|完整控制||  
|NT LM 安全性支援提供者<sup>3</sup>|自動|所需的 Kerberos 驗證[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL 中|(預設值)|||  
|Remote Access Connection Manager|(預設值)||SSO 服務帳戶|完整控制|啟動 SSO 服務所需|  
||||網路服務|完整控制|所需的 IIS|  
|Server|自動|用於叢集檔案共用資源|網路服務|完整控制||  
|WinHTTP Web Proxy 自動探索服務|(預設值)||SSO 服務帳戶|完整控制|啟動 SSO 服務所需|  
||World Wide Web Publishing Service|自動|所需的 SQL Server Reporting Services|(預設值)||  
  
 <sup>1</sup> （預設值） 的值表示，不會變更安全性原則所套用的預設設定  
  
 <sup>2</sup> （預設值） 的值表示尚未變更服務的預設使用者權限  
  
### <a name="registry-settings"></a>登錄設定  
 若要啟動登錄編輯程式，請按一下**啟動**，按一下 [**執行**，然後在**執行**] 對話方塊中，輸入`regedit`按下 ENTER。  
  
|索引鍵|使用者|Permissions|詳細資料|  
|---------|----------|-----------------|-------------|  
|HKLM\ SYSTEM\CurrentControlSet\Services\DHCP|網路服務|完整控制|DHCP 用戶端服務所需|  
|HKLM\ SYSTEM\CurrentControlSet\Services\TCPIP|網路服務|完整控制|DHCP 用戶端服務所需|  
  
<a name="BKMK_AddSec"></a>   
## <a name="additional-security-considerations"></a>其他安全性考量  
 下表所示的其他重要的安全性相關設定您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
|受影響的成品|變更|參考和詳細資料|  
|-----------------------|------------|---------------------------|  
|SSO 服務帳戶|授與完全控制叢集在叢集管理員 上的權限|這項變更是為了使用 SSO，才能正常運作|  
|SQL Server 服務帳戶，SQL Server 的伺服器，BizTalk Server 的伺服器，SQL Server 叢集名稱|在 Active Directory 中的委派信任|所需的適當的 Kerberos 驗證。 如需詳細資訊，請參閱[How to： 在 SQL Server 容錯移轉叢集上啟用 Kerberos 驗證](http://go.microsoft.com/fwlink/?LinkId=157417)(http://go.microsoft.com/fwlink/?LinkId=157417)。|  
|SQL Server 服務帳戶|授與權限來建立 SPN 項目|所需的適當的 Kerberos 驗證。 如需詳細資訊，請參閱[如何在 SQL Server 中使用 Kerberos 驗證](http://go.microsoft.com/fwlink/?LinkId=157420)(http://go.microsoft.com/fwlink/?LinkId=157420)。|  
|SQL Server 節點，SQL 叢集名稱|建立使用者 SQL Server 服務帳戶的 SPN 項目|所需的適當的 Kerberos 驗證。 如需詳細資訊，請參閱[如何在 SQL Server 中使用 Kerberos 驗證](http://go.microsoft.com/fwlink/?LinkId=157420)(http://go.microsoft.com/fwlink/?LinkId=157420)。|  
|SQL 網路名稱叢集資源|DNS 註冊必須成功，啟用 Kerberos 驗證|所需的適當的 Kerberos 驗證|  
|SQL Server 介面組態|啟用遠端直接管理員連接|SQL Browser 服務正常運作所需的 SQL 用戶端 (BizTalk/ASP.NET) 才能正確地找出 SQL Server 具名執行個體所需|  
|BizTalk 應用程式使用者群組|授與 Execute 權限**sp_help_jobhistory**中**msdb**資料庫|所需[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
  
## <a name="see-also"></a>請參閱  
 [其他重要工作的檢查清單](~/technical-guides/checklists-for-other-important-tasks.md)