---
title: 如何稽核 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO], auditing
- SSO, auditing
- auditing [SSO]
- SSO database, auditing
ms.assetid: dc6d0726-fc31-4af2-9a23-8df9e3fc5836
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27528cf6da53c69db4b2bc6c9e1d296472b24186
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-audit-sso"></a>如何稽核 SSO
您可以使用 MMC 嵌入式管理單元或命令列，以設定正負兩種稽核層次。 稽核的結果會儲存在資料庫的事件日誌和稽核日誌。  
  
 SSO 系統管理員可設定符合公司政策的正面和負面稽核層級。 您可以在下列層級的其中一個設定正面和負面稽核︰  
  
 0 = 無  
  
 1 = 低  
  
 2 = 中  
  
 3 = 高。 此層級會儘可能發出最多的稽核訊息。  
  
 正面稽核的預設值是 0 (無)，負面稽核的預設值是 1 (低)。  
  
 若要變更資料庫稽核層次，必須使用 XML 檔案更新 SSO 資料庫。 更新 SSO 資料庫的範例 XML 檔案為：  
  
```  
<sso>  
<globalnfo>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
</globalInfo>  
</sso>  
  
```  
  
### <a name="to-audit-single-sign-on-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元稽核單一登入  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  在  **系統內容** 對話方塊中，按一下 [ **稽核** ] 索引標籤。  
  
5.  輸入適當的設定，然後按一下 **[確定]**。  
  
### <a name="to-audit-single-sign-on-using-the-command-line"></a>若要稽核單一登入使用命令列  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoconfig – auditlevel\<正數\>\<負數\>**，其中**\<正數\>**的層級當動作成功，稽核和**\<負數\>**是動作失敗時的稽核層級。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-audit-the-sso-database"></a>稽核 SSO 資料庫  
  
1.  依序按一下 **[開始]**及 **[執行]**，然後輸入 **cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – updatedb\<更新檔案\>**，其中**\<更新檔案\>**路徑和檔案名稱。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md)   
 [使用 SSO](../core/using-sso.md)