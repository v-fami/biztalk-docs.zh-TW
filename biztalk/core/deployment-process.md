---
title: "部署程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, deploying
- deploying, SSO
- LogonExternalUser test [SSO]
- security, SSO
- SSO, LogonExternalUser test
- SSO, security
ms.assetid: 7dd4c022-c70b-467a-bf94-dc4ac6029f81
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21be32ec58c90c1fb95134a002bee82ef5d78fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-process"></a>部署程序
下列步驟提供安全部署「企業單一登入」的高層級概觀。 如需在 SQL Server 中執行之動作的詳細程序，請參閱您的 SQL Server 手冊。  
  
1.  在 SQL Server 網域控制站，使用「新增信任精靈」建立包含以下屬性的信任：  
  
    -   **名稱：** ORCH.com  
  
    -   **方向：**雙向  
  
    -   **側邊：**僅此網域  
  
    -   **連出信任驗證等級-本機網域：**選擇性驗證  
  
    -   **密碼：**選擇的密碼  
  
    -   **確認連出信任：** [是]  
  
    -   **確認連入信任：**否  
  
2.  在 ORCH.com 網域控制站，使用「新增信任精靈」建立包含以下屬性的信任：  
  
    -   **名稱：** SQL.com  
  
    -   **方向：**雙向  
  
    -   **側邊：**僅此網域  
  
    -   **連出信任驗證等級-本機網域：**選擇性驗證  
  
    -   **密碼：**必須是 ORCH.com 的密碼相同  
  
    -   **確認連出信任：** [是]  
  
    -   **確認連入信任：**否  
  
3.  在 ORCH.com 網域控制站，設定從 SQL.COM 連入的網域整體信任。  
  
4.  在 SQL.com 網域控制站，設定從 ORCH.COM 連出的網域整體信任。  
  
5.  在 ORCH.com 網域控制站，將網域功能等級提升至 Windows Server 2008 SP2 或 Windows Server 2008 R2。  
  
6.  在 ORCH 網域，建立下列新使用者：  
  
    -   ORCH\SSOSvcUser  
  
    -   ORCH\TestAppUser  
  
    -   ORCH\AffAppUser  
  
7.  新增**做為作業系統的一部分**至 SSOSvcUser 和 TestAppUser。  
  
8.  新增**允許驗證**ORCH\TestAdmin 權限。  
  
9. 將 ORCH\SSOSvcUser 新增至 SQL 網域的 SQL2。 (此步驟需要使用 Active Directory MMC 的「進階檢視」)。  
  
10. 在 SQL2 電腦，建立下列兩個新登入：  
  
    -   ORCH\TestAdmin  
  
    -   ORCH\SSOSvcUser  
  
11. 在 SQL2 網域，建立兩個網域全域群組：  
  
    -   ORCH\SSOAdminGroup  
  
    -   ORCH\SSOAffAdminGroup  
  
12. 新增**允許驗證**新增至 ORCH\SSOAdminGroup 群組的權限。  
  
13. 在 SQL2 資料庫，建立下列新登入：  
  
    -   ORCH\SSOAdminGroup  
  
14. 按照以下步驟安裝「主要密碼伺服器」：  
  
    -   使用 ORCH\TestAdmin 登入 NTS5。  
  
    -   使用 SQL2 當成「主要密碼伺服器」來安裝 ESSO。  
  
15. 使用 ORCH\TestAdmin 登入 HIS1，然後安裝「企業單一登入」。 使用資料庫伺服器名稱 SQL2，將 ESSO 設定為 SSO 聯結 HIS2。  
  
16. 使用 ORCH\TestAdmin，在 HIS3 安裝「企業單一登入管理」公用程式。  
  
17. 將下列使用者新增至以下群組：  
  
    -   將 ORCH\TestAppUser 新增至 ORCH\SSOAdminGroup  
  
    -   將 ORCH\AffAppUser 新增至 ORCH\TestAffUserGroup  
  
18. 在 HIS3 上安裝 SQL Server Enterprise Edition，然後新增登入 ORCH\AffAppUser。  
  
19. 在 HIS1 電腦，開啟命令提示字元，然後使用下列命令來設定限制委派和通訊協定轉換：  
  
    -   **setspn-A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**  
  
    -   **setspn-A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**  
  
20. 在**ORCH\SSOSvcUser**和**ORCH\TestAppUser**屬性頁中，選取下列選項來設定兩個使用者帳戶的適當委派：  
  
    -   **信任這個使用者委派指定的服務**  
  
    -   **使用任何驗證通訊協定**  
  
21. 在 HIS1 電腦使用 ORCH\TestAdmin，執行下列工作：  
  
    -   將 ORCH\TestAppUser 新增至「遠端桌面使用者群組」  
  
    -   授與**通過驗證後模擬**權限至 ORCH\SSOSvcUser  
  
    -   授與**通過驗證後模擬**權限至 ORCH\TestAppUser  
  
22. 使用 ORCH\TestAppUser 並執行下列應用程式組態，以登入 HIS1 來驗證您的部署：  
  
     執行 LogonExternalUser 測試。  
  
    ```  
    <SSO>  
       <application name="TestApp">  
          <description>An SSO Test Affiliate Application</description>  
          <contact>AffAppUser@ESSOV2.EBiz.Com</contact>  
          <appUserAccount>ORCH\TestAffAdminGroup</appUserAccount>  
          <appAdminAccount>ORCH\TestAffUserGroup</appAdminAccount>  
          <field ordinal="0" label="User ID" masked="no" />  
          <field ordinal="1" label="Password" masked="yes" />  
          <flags   
             groupApp="no"   
             configStoreApp="no"   
             allowTickets="no"   
             validateTickets="yes"   
             allowLocalGroups="yes"   
             ticketTimeout="yes"   
             adminGroupSame="no"   
             enableApp="yes"   
             hostInitiatedSSO="yes"   
             validatePassword="yes"/>  
       </application>  
    </SSO>  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [SSO 部署概觀](../core/sso-deployment-overview.md)