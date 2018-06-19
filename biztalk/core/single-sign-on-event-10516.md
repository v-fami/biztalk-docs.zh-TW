---
title: 單一登入： 事件 10516 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d20df92f-c995-4cbc-a8f9-21cea30b82c9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b74ca4a47bc62d28b25564bd5843729c56362
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269894"
---
# <a name="single-sign-on-event-10516"></a>單一登入： 事件 10516
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10516|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_BAD_SSO_APP_ADMIN|  
|訊息文字|SSO 分支機構系統管理員帳戶無效。 如果是本機帳戶核取此帳戶是否存在伺服器上。 如果是網域帳戶請連絡您的網域系統管理員。 當帳戶 valid.%r 啟用 SSO<br /><br /> SSO 分支機構系統管理員: %1 %r<br /><br /> 無效的帳戶: %2 %r<br /><br /> 錯誤碼： %3|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示，SSO 分支機構系統管理員帳戶或企業登登入所建立的群組不是有效的 Windows 帳戶。 SSO 分支機構系統管理員帳戶可以是 Windows 群組帳戶或個別帳戶。 SSO 分支機構系統管理員帳戶也可以是網域或本機群組帳戶。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   請確認 SSO 分支機構系統管理員帳戶存在。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [SSO 使用者群組](../core/sso-user-groups.md)  
  
-   [如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md)