---
title: "如何設定密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], replay files
- Password Synchronization [SSO], maximum age
- SSOCONFIG command line utility
- Password Synchronization [SSO], SSOCONFIG command line utility
- Password Synchronization [SSO], configuring
- configuring, Password Synchronization [SSO]
ms.assetid: 04000dfc-02b9-4d50-babe-8bc8a07a33b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb913c1719f4833ef36cf9f73f6a96432217f2af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-password-synchronization"></a>如何設定密碼同步化
使用 SSOCONFIG 命令列公用程式可設定您的密碼同步設定。  
  
### <a name="to-specify-the-directory-for-replay-files"></a>指定重新執行檔案的目錄  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssoconfig replayfiles\<重新執行檔案目錄 > &#124; 預設**按下 Enter。  
  
> [!NOTE]
>  變更服務帳戶時不會刪除重新執行檔案。 若變更此帳戶，您需要手動刪除重新執行檔案。  
  
#### <a name="to-display-or-change-maximum-password-synchronization-age"></a>顯示或變更最長密碼同步時間  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssoconfig-syncage\<以小時為單位的最大密碼存在時間 >**按下 Enter。  
  
> [!NOTE]
>  SSOCONFIG 公用程式會使用 SQL Server 電腦上的時間做為系統時間。 使用任何與時間有關的命令時請謹記這點。  
  
## <a name="see-also"></a>另請參閱  
 [密碼同步處理](../core/password-synchronization2.md)