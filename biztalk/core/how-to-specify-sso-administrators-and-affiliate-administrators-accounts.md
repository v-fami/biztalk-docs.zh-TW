---
title: 如何指定 SSO 系統管理員和分支機構系統管理員帳戶 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- enabling, SSO
- SSO, enabling
- disabling, SSO
- SSO, disabling
- managing [SSO], configuring administrator accounts
- managing [SSO], enabling
- managing [SSO], disabling
- SSO, administrator accounts
ms.assetid: 6c300e09-b781-45de-b2da-b1083164a1c0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c96e2d99bd6071098a65b3635bb466de44a455d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-specify-sso-administrators-and-affiliate-administrators-accounts"></a>如何指定 SSO 系統管理員和分支機構系統管理員帳戶
「企業單一登入」(SSO) 和「分支機構管理員」帳戶可以是主控件群組或個別帳戶。 設定 SSO 系統之前，必須先建立這些帳戶。  
  
 使用網域帳戶時，必須建立「SSO 系統管理員」和「SSO 分支機構系統管理員」帳戶，以做為網域控制站中的網域全域安全性群組。 網域管理員必須建立這些帳戶。  
  
 您必須在 SSO 資料庫中指定「單一登入管理員」和「分支機構管理員」帳戶。 更新 SSO 資料庫的「SSO 系統管理員」群組前，必須先停用「單一登入」系統。  
  
 下列 XML 程式碼顯示用來更新 SSO 資料庫的 XML 範例  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  「組態精靈」會在 SSO 資料庫中自動指定 SSO 系統管理員和 SSO 分支機構系統管理員群組。  
  
> [!NOTE]
>  如果未設定 SSO，使用者應該檢查混合模式網域中是否正在使用的網域本機帳戶。  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元停用企業單一登入系統  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下 **系統**, ，然後按一下  **停用**。  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-command-line"></a>使用命令列停用企業單一登入系統  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 **ssomanage** –**disablesso**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元更新 SSO 資料庫  
  
1.  在 **啟動** ] 功能表上，按一下 [ **所有程式**, ，**Microsoft 企業單一登入**, ，然後 **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下 **系統**, ，然後按一下  **更新**。  
  
### <a name="to-update-the-sso-database-using-the-command-line"></a>使用命令列更新 SSO 資料庫  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 * * ssomanage – updatedb *\<更新檔案\>* * *，其中*\<更新檔案\>*是 XML 檔案的名稱與路徑。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元啟用企業單一登入系統  
  
1.  在 **啟動** ] 功能表上，按一下 [ **所有程式**, ，**Microsoft 企業單一登入**, ，然後 **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下 **系統**, ，然後按一下  **啟用**。  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-command-line"></a>使用命令列啟用企業單一登入系統  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 **ssomanage – enablesso**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 使用者群組](../core/sso-user-groups.md)