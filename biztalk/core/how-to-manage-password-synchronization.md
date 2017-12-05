---
title: "如何管理密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], managing
- managing [SSO], disabling features
- managing [SSO], enabling features
- Password Synchronization [SSO], SSOMANAGE command line utility
- SSO database, SSOMANAGE command line utility
- managing, Password Synchronization [SSO]
- SSO database, database settings
- SSOMANAGE command line utility
ms.assetid: 033e63f2-e5b0-4400-99c3-145679d9b84e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce76f2ca16cca44af1658983c49d11f6931e931
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-password-synchronization"></a>如何管理密碼同步處理
使用 MMC 嵌入式管理單元或 SSOMANAGE 命令列公用程式來啟用或停用 SSO 功能，以及顯示目前的 SSO 資料庫設定。  
  
### <a name="to-manage-features-or-display-settings-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元管理功能或顯示設定  
  
1.  使用滑鼠右鍵按一下適當的功能或資料庫。  
  
2.  按一下適當的功能表項目。  
  
### <a name="to-enable-sso-features-using-the-command-line"></a>使用命令列啟用 SSO 功能  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-啟用**按下 Enter。  
  
### <a name="to-disable-sso-features-using-the-command-line"></a>使用命令列停用 SSO 功能  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-停用**按下 Enter。  
  
### <a name="to-display-current-database-settings-using-the-command-line"></a>使用命令列顯示目前的資料庫設定  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-displaydb**按下 Enter。  
  
## <a name="see-also"></a>請參閱  
 [密碼同步](../core/password-synchronization2.md)