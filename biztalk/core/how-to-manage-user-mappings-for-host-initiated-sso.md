---
title: "如何管理使用者對應的主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, host initiated SSO
- host initiated SSO, user maps
ms.assetid: 6b05249e-da35-475b-9c23-5eb556013d57
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0bf65bdb3de30d5b701946215b5c7ae7d40d828
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-user-mappings-for-host-initiated-sso"></a>如何管理使用者對應的主控件初始化的 SSO
使用下列程序，以建立對應、設定認證以及啟用或停用對應。  
  
### <a name="to-manage-user-mappings-for-host-initiated-sso-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元為主控件初始化的 SSO 管理使用者對應  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  在 [領域] 窗格中，按一下**分支機構應用程式**。  
  
4.  在詳細資訊窗格中，使用滑鼠右鍵按一下分支機構應用程式，然後為您的動作選擇適當的功能表項目。  
  
### <a name="to-create-mappings-in-host-initiated-sso-using-the-command-line"></a>使用命令列在主控件初始化的 SSO 中建立對應  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage – createmappings\<對應檔\>**，其中**對應檔 >**是 xml 檔案的名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
     以下顯示對應檔案範例。  
  
    ```  
    <SSO>  
      <mapping>  
        <windowsDomain>DomainName</windowsDomain>  
        <windowsUserId>UserA</windowsUserId>  
        <externalApplication>SSOApplication</externalApplication>  
    <externalUserId>ExternalUserID that corresponds to UserA</externalUserId>  
      </mapping>  
    </SSO>  
  
    ```  
  
 為分支機構應用程式啟用「驗證密碼」功能時，需要設定認證，如下所示：  
  
#### <a name="to-set-credentials-for-individual-type-affiliate-applications-using-the-command-line"></a>使用命令列為個別類型的分支機構應用程式設定認證  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-setcredentials \<Windows 帳戶名稱\>\<應用程式名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
#### <a name="to-set-credentials-for-host-group-type-affiliate-applications-using-the-command-line"></a>使用命令列設定主控件群組類型分支機構應用程式的認證  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-setcredentials\<外部帳戶名稱\>\<應用程式名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
#### <a name="to-enable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a>使用命令列為個別類型的分支機構應用程式啟用對應  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-enablemapping \<Windows 帳戶名稱\>\<應用程式名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a>使用命令列為個別類型的分支機構應用程式停用對應  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-disablemapping \<Windows 帳戶名稱\>\<應用程式名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
#### <a name="to-enable-mappings-for-host-group-type-affiliate-applications-using-the-command-line"></a>使用命令列為主控件群組類型的分支機構應用程式啟用對應  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-enablemapping\<外部帳戶名稱\>\<應用程式名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a>使用命令列為個別類型的分支機構應用程式停用對應  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-disablemapping\<外部帳戶名稱\>\<應用程式名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [主控件初始化的 SSO](../core/host-initiated-sso.md)