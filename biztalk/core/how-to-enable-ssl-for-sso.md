---
title: 如何為 SSO 啟用 SSL |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, SSL
- managing [SSO], enabling SSL
- SSL
ms.assetid: 0d75962a-a0b0-4e69-8001-54e7df617006
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cd617fd955100930b513bc6c364626e4912eb81
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969908"
---
# <a name="how-to-enable-ssl-for-sso"></a>如何為 SSO 啟用 SSL
使用此命令以啟用所有「企業單一登入」(SSO) 伺服器與 SSO 資料庫之間的「安全通訊端層」(SSL)。  
  
### <a name="to-enable-ssl-for-enterprise-single-sign-on"></a>若要啟用企業單一登入的 SSL  
  
1.  依序按一下 **[開始]** 及 **[執行]**，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoconfig – setSSL\<是/否\>**，其中\<**是/否**\>指出您是否要啟用 SSO 系統中的 SSL。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [使用 SSO](../core/using-sso.md)