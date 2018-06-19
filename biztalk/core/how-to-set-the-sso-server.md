---
title: 如何設定 SSO 伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, selecting [SSO]
- SSO, selecting servers
- managing [SSO], selecting servers
- SSOManage [SSO]
ms.assetid: a0b0176d-b426-4ab1-8a7e-1f96f4214683
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7dab9df7b5444b437f12737c37036b592a70aad
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972164"
---
# <a name="how-to-set-the-sso-server"></a>如何設定 SSO 伺服器
每次使用 ssomanage 時，您必須先將使用者指向您要連接的「單一登入」伺服器。  
  
 您可以使用下列其中一種作法：  
  
-   個別使用者可以將自己指向正確的「單一登入伺服器」。  
  
-   「單一登入」伺服器的本機電腦系統管理員可以將「單一登入使用者」帳戶的所有成員指向這個伺服器。  
  
### <a name="to-set-the-enterprise-single-sign-on-server-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元設定「企業單一登入伺服器」  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 MMC 嵌入式管理單元在**主控台根目錄**，以滑鼠右鍵按一下**企業單一登入**，然後按一下**選取**。  
  
3.  瀏覽到想要的伺服器。  
  
4.  視情況選取**設定所有使用者的 SSO 伺服器**核取方塊。  
  
5.  按一下 **[確定]**。  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-a-single-user-using-the-command-line"></a>使用命令列設定單一使用者的「企業單一登入」  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – server \<SSO 伺服器名稱\>**，其中 **\<SSO 伺服器名稱\>** 是單一登入伺服器的電腦名稱的使用者想要連接到。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-all-users-using-the-command-line"></a>使用命令列設定所有使用者的「企業單一登入」  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – serverall \<SSO 伺服器名稱\>**，其中 **\<SSO 伺服器名稱\>** 是單一登入伺服器的所有電腦名稱會指向單一登入使用者帳戶的成員。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-determine-the-enterprise-single-sign-on-server-to-which-a-user-is-connected-using-the-command-line"></a>使用命令列決定使用者將連接的「企業單一登入伺服器」  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – showserver**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
> [!NOTE]
>  這個命令會顯示目前使用者以及其他使用者 (若存在) 的設定。  
  
## <a name="see-also"></a>請參閱  
 [如何啟用 SSO](../core/how-to-enable-sso.md)   
 [如何停用 SSO](../core/how-to-disable-sso.md)   
 [如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)   
 [使用 SSO](../core/using-sso.md)