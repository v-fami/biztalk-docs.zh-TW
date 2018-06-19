---
title: 如何變更主要密碼伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, promoting
- managing [Master Secret server], promoting servers
- managing [SSO], promoting servers
- SSO, Master Secret server
- modifying, Master Secret server
- Master Secret server, changing
ms.assetid: 44a786ca-4645-44a8-b33e-d0019f0aeca9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a1e30f1703f554792ce5243414a95965da93670
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969356"
---
# <a name="how-to-change-the-master-secret-server"></a>如何變更主要密碼伺服器
在您安裝主要密碼伺服器並設定 SSO 資料庫之後，若原始主要密碼伺服器故障且無法復原，則可以變更主要密碼伺服器。 若要變更主要密碼伺服器，您必須將 SSO 伺服器升級為主要密碼伺服器。  
  
### <a name="to-change-the-master-secret-server-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元變更主要密碼伺服器  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 領域 窗格中，以滑鼠右鍵按一下**系統**，然後按一下 **屬性**。 主要密碼伺服器會顯示在**一般** 索引標籤**系統屬性** 對話方塊。  
  
3.  按一下**變更**選取新的主要密碼伺服器。  
  
    > [!IMPORTANT]
    >  當使用 MMC 嵌入式管理單元變更主要密碼伺服器時，必須在主要密碼伺服器上執行作業。 不可能使用非主要密碼伺服器之電腦中的 MMC 嵌入式管理單元來變更主要密碼伺服器。  
  
4.  登入新的主要密碼伺服器，以還原新主要密碼伺服器之登錄的主要密碼。  
  
5.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
6.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
7.  重新啟動新的主要密碼伺服器。  
  
8.  型別**ssoconfig – restoreSecret\<還原檔案\>**，其中**\<還原檔案\>** 是主要密碼所在的檔案名稱與路徑儲存。  
  
     主要密碼儲存在下列位置的登錄中：  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-promote-a-single-sign-on-server-to-master-secret-server-using-the-command-line"></a>使用命令列將單一登入伺服器升級為主要密碼伺服器  
  
1.  建立包含您要升級為主要密碼伺服器的 SSO 伺服器名稱之 XML 檔案。 例如，  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>SSO Server name</secretServer>  
      </globalInfo>  
    </sso>  
    ```  
  
    > [!IMPORTANT]
    >  若要從非主要密碼伺服器的電腦變更主要密碼伺服器，請確認指定的 XML 檔案只包含主要密碼伺服器名稱。 具體來說，它應該包含 SSO 系統管理員 XML 標記或**ssomanage-updatedb**作業將會失敗。  
  
2.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
3.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage – updatedb** \<**更新檔案**\>，其中\<**更新檔案**\>是 XML 檔案的名稱您在步驟 1 中建立。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  重新啟動主要密碼伺服器。  
  
6.  型別**ssoconfig – restoresecret\<還原檔案\>**，其中**\<還原檔案\>** 是主要密碼所在的檔案名稱與路徑儲存。  
  
     主要密碼儲存在下列位置的登錄中：  
  
     HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [主要密碼伺服器](../core/master-secret-server.md)   
 [如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)   
 [如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md)   
 [使用 SSO](../core/using-sso.md)