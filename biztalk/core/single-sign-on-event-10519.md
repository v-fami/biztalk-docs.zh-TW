---
title: 單一登入： 事件 10519 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e709957e-a690-4a44-a863-07b2a55dae7b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928892ff1d0ee461a26095ddc7a72fd3accecf10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271006"
---
# <a name="single-sign-on-event-10519"></a>單一登入： 事件 10519
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10519|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_BAD_APP_ADMIN_GROUP|  
|訊息文字|此應用程式的應用程式系統管理員帳戶無效。 如果是本機帳戶核取此帳戶是否存在伺服器上。 如果是網域帳戶請連絡您的網域系統管理員。 當帳戶有效，請讓應用程式。 如果您不打算使用此應用程式在此 computer.%r 上，您可以忽略這個訊息<br /><br /> 應用程式名稱: %1 %r<br /><br /> 應用程式系統管理員: %2 %r<br /><br /> 無效的帳戶: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示應用程式系統管理員群組的帳戶不是有效的 Windows 帳戶。 沒有一個應用程式 Administraotrs 帳戶群組，每個分支機構應用程式。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  
  
-   請確認指定的應用程式系統管理員帳戶存在。  
  
-   使用 SSO 管理公用程式來驗證指定的分支機構應用程式設定為使用正確的應用程式系統管理員帳戶。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [SSO 使用者群組](../core/sso-user-groups.md)  
  
-   [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)  
  
-   [如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md)