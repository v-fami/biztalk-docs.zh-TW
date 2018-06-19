---
title: 如何更新 SSO 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tickets [SSO], modifying
- managing [SSO], modifying Credential cache timeout
- tickets [SSO], timeouts
- modifying, SSO database
- managing [SSO], modifying ticket timeouts
- SSO database, modifying
ms.assetid: 45eb6a77-d91a-44a8-b26d-05508c288c36
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbb7ea650a2845d8ebdcdcc2204f8346c5737c43
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971316"
---
# <a name="how-to-update-the-sso-database"></a>如何更新 SSO 資料庫
使用 MMC 嵌入式管理單元或命令列，可以變更 SSO 資料庫中的全域資訊，像是主要密碼伺服器識別碼、帳戶名稱、資料庫中的稽核、票證逾時以及認證快取逾時。  
  
## <a name="changing-timeouts-for-the-sso-system"></a>變更 SSO 系統的逾時  
 您可以修改「企業單一登入」(SSO) 系統層級上的兩個逾時：  
  
 **票證逾時。** 。此屬性指定 SSO 核發之票證的有效時間長度。 為了滿足使用 SSO 的企業中大部分實例，預設的票證逾時為 2 分鐘。 SSO 系統管理員可以根據應用程式需求變更此值。  
  
 **認證快取逾時。** 。此屬性指定所有 SSO 伺服器的認證快取逾時。 SSO 伺服器在第一次尋查之後會快取認證。 依照預設，認證快取逾時為 60 分鐘。 SSO 系統管理員可以根據安全性需求，將此變更為適當的值。  
  
 更新 SSO 資料庫即可變更這兩種逾時。  
  
 更新 SSO 資料庫的範例 XML 檔案為：  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
<secretServer>ComputerA</secretServer>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
<ticketTimeout>2</ticketTimeout>  
<credCacheTimeout>60</credCacheTimeout>  
</globalInfo>  
</sso>  
  
```  
  
#### <a name="to-change-timeouts-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元變更逾時  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  在 [SSO 系統屬性]  對話方塊中，按一下 [一般]  索引標籤。  
  
5.  輸入適當的設定，然後按一下 **[確定]**。  
  
#### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元更新 SSO 資料庫  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  在 [系統] 上按一下滑鼠右鍵，然後按一下 [升級資料庫] 。  
  
#### <a name="to-update-the-sso-database-using-the-command-line"></a>使用命令列更新 SSO 資料庫  
  
1.  依序按一下 **[開始]** 及 **[執行]**，然後輸入 **cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – updatedb\<更新檔案\>**，其中**\<更新檔案\>** 路徑和檔案名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)   
 [使用 SSO](../core/using-sso.md)