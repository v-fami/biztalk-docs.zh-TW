---
title: "最小安全性使用者權限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, user accounts
- permissions, user accounts
- permissions, roles
- administrator accounts, permissions
- roles, permissions
- permissions, administrator accounts
- user accounts, permissions
- user accounts, access control
- security, permissions
ms.assetid: 44b6e7da-8e6c-40c0-a250-52ab422c0adf
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ad405afd1f69b4499b8c4650586411957a2ca3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="minimum-security-user-rights"></a>最小安全性使用者權限
BizTalk Server 使用的群組和帳戶擁有執行大部分工作所需的最低使用者權限。 因此，有些工作需要的權限可能超過 BizTalk Server 自動授與您所屬群組的使用者權限。 本主題內容：  
  
 [群組和角色成員資格](../core/minimum-security-user-rights.md#BKMK_GroupRole)  
  
 [執行系統管理工作的使用者權限](../core/minimum-security-user-rights.md#BKMK_UserRights)  
  
 [社群補充-工作清單](../core/minimum-security-user-rights.md#BKMK_Community)  
  
##  <a name="BKMK_GroupRole"></a>群組和角色成員資格  
 下表描述您需要在 BizTalk Server 中執行工作最小安全性使用者權限：  
  
|工作|群組或角色|  
|----------|---------------------|  
|**安裝程式**||  
|安裝|本機系統管理員|  
|組態|BizTalk Server 系統管理員<br />本機系統管理員<br />-sysadmin SQL Server 角色<br />為 SSO 系統管理員<br />OLAP 系統管理員|  
|加入 BizTalk Server 群組|本機系統管理員<br />BizTalk Server 系統管理員|  
|**BizTalk 管理**||  
|建立 MessageBox 資料庫|BizTalk Server 系統管理員<br />-sysadmin SQL Server 角色|  
|建立或刪除 BizTalk 主控件|BizTalk Server 系統管理員<br />-在 BizTalk MessageBox 資料庫上的 db_ddladmin SQL Server 資料庫角色|  
|變更主控件的 [主控件追蹤] 屬性|BizTalk Server 系統管理員<br />-在 BAM 主要匯入資料庫、 BizTalk MessageBox 資料庫和 BizTalk 追蹤資料庫上的 db_securityadmin SQL Server 資料庫角色|  
|建立 (安裝)、刪除或變更主控件執行個體的認證|<ul><li>BizTalk Server 系統管理員</li><li>本機系統管理員</li><li>下列資料庫所在伺服器上的 securityadmin SQL Server 角色：<br /><br /> <ul><li>BizTalk MessageBox 資料庫、BizTalk 管理資料庫、規則引擎資料庫、BizTalk 追蹤資料庫、BAM 主要匯入資料庫</li></ul></li><li>在下列資料庫上的 db_securityadmin SQL Server 資料庫角色：<br /><br /> <ul><li>BizTalk MessageBox 資料庫、BizTalk 管理資料庫、規則引擎資料庫、BizTalk 追蹤資料庫、BAM 主要匯入資料庫</li></ul></li></ul>|  
|啟動或停止主控件執行個體|BizTalk Server 系統管理員|  
|新增或移除伺服器|BizTalk Server 系統管理員<br />的您要加入或移除的電腦上本機系統管理員。|  
|新增或移除接收處理常式|BizTalk Server 系統管理員<br />為 SSO 分支機構系統管理員|  
|啟動或停止應用程式、協調流程、傳送埠和傳送埠群組|BizTalk Server 操作員|  
|啟用和停用接收位置|BizTalk Server 操作員|  
|搜尋成品|BizTalk Server 操作員|  
|新增配接器|BizTalk Server 系統管理員<br />為 SSO 分支機構系統管理員|  
|備份資料庫|的資料庫 BTS_BACKUP_USERS 角色<br />-裝載 BizTalk 管理資料庫的 SQL Server 上的 sysadmin SQL Server 角色。 **注意：**您必須設定每個 SQL Server 執行個體上執行的網域帳戶或本機帳戶下對應的使用者與 SQL Server Agent 服務。|  
|以憑證設定 BizTalk 群組|BizTalk Server 系統管理員|  
|所有其他的工作 (包括 WMI)|BizTalk Server 系統管理員|  
|**作業和訊息追蹤的服務執行個體**||  
|檢視 [群組中樞] 頁面、執行查詢、儲存及載入查詢|BizTalk Server 操作員|  
|檢視查詢結果|BizTalk Server 操作員|  
|一般組態和追蹤組態|BizTalk Server 系統管理員 （讀取和寫入）<br />BizTalk Server 操作員 （讀取）|  
|瀏覽狀況監控 Cube|BizTalk Server 系統管理員|  
|檢視訊息屬性|BizTalk Server 系統管理員|  
|儲存訊息內文|BizTalk Server 系統管理員|  
|使用**尋找訊息**查詢|BizTalk Server 系統管理員|  
|使用**查詢組建**|BizTalk Server 系統管理員|  
|使用協調流程偵錯工具|BizTalk Server 系統管理員|  
|檢視訊息流程中，使用 BizTalk Server 管理主控台的 群組中樞 頁面中的訊息事件。|BizTalk Server 操作員|  
|擱置、終止或繼續執行個體|BizTalk Server 操作員|  
|封存或清除「追蹤」資料庫中的訊息|-在 BizTalk 追蹤資料庫的 db_owner 角色|  
|所有其他的工作|BizTalk Server 系統管理員|  
|**追蹤設定檔編輯器**||  
|讀取或寫入 BizTalk 管理資料庫|BizTalk Server 系統管理員|  
|**事件匯流排監控 MMC**||  
|所有工作|BizTalk Server 系統管理員|  
|**BizTalk WCF 服務發佈精靈**||  
|所有工作|本機系統管理員|  
|**BizTalk Web 服務發佈精靈**||  
|所有工作|本機系統管理員|  
|**商務活動監控**||  
|執行 BM.exe|-在 BAM 主要匯入、 BAM 星狀結構描述和 BAM 封存資料庫的 db_owner SQL Server 資料庫角色|  
|如果有 Analysis Services 資料庫，則執行 BM.exe|-在 BAM 主要匯入、 BAM 星狀結構描述和 BAM 封存資料庫的 db_owner SQL Server 資料庫角色<br />在 BAM Analysis Services 資料庫中的 OLAP 系統管理員|  
|建立 BAM 檢視帳戶|-在 BAM 主要匯入資料庫的 db_owner SQL Server 資料庫角色<br />在 BAM Analysis Services 資料庫中的 OLAP 系統管理員|  
|**規則引擎 （發佈規則）**||  
|部署/解除部署原則；操作有關安全性的成品|的 「 規則引擎 」 資料庫中 RE_ADMIN_USERS SQL Server 資料庫角色|  
  
##  <a name="BKMK_UserRights"></a>執行系統管理工作的使用者權限  
 若要執行管理工作，請使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI)；執行管理工作的帳戶視執行的工作而定，需要不同的使用者權限層級。  
  
 下表說明帳戶執行工作所需的使用者權限，從最低的使用者權限 (層級 1) 到最高的使用者權限 (層級 4)。  
  
|使用者權限的層級|授與的使用者權限|工作|  
|--------------------------|-------------------------|-----------|  
|0|BizTalk Server 操作員|-基本管理和監視工作。 沒有變更組態設定的能力。 沒有訊息屬性或內容的存取權。|  
|1|BizTalk Server 系統管理員|-所有管理工作的詳細資訊，除了需要層級 2-4 使用者權限|  
|2|授與層級 1 的使用者權限<br />-所有 SQL Server 上的 securityadmin SQL Server 角色<br />-在 BizTalk 追蹤、 規則引擎、 BizTalk 管理、 BAM 主要匯入和 BizTalk MessageBox 資料庫中的 db_securityadmin 和 db_accessadmin SQL Server 資料庫角色<br />-所有 BizTalk MessageBox 資料庫上的 db_ddladmin SQL Server 資料庫角色<br />為 SSO 分支機構系統管理員|-建立和刪除 BizTalk 主控件<br />變更主控件追蹤屬性<br />新增和刪除伺服器<br />新增和刪除接收處理常式<br />新增配接器|  
|3|授與層級 2 的使用者權限<br />的所有的 BizTalk Server 執行階段電腦上本機系統管理員|-建立和刪除主控件執行個體|  
|4|授與層級 3 的使用者權限<br />-在所有具有 BizTalk MessageBox 資料庫的 SQL 伺服器上的 sysadmin SQL Server 角色|建立 MessageBox 資料庫|  
  
##  <a name="BKMK_Community"></a>社群補充-工作清單  
 [BizTalk Server 2013 R2 的最低安全性權限](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2013-r2.aspx)(http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2013-r2.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [存取控制和資料安全性](../core/access-control-and-data-security.md)   
 [設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [在 BizTalk Server 資料庫](../core/databases-in-biztalk-server.md)   
 [BizTalk Server 中的 Windows 群組和使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)