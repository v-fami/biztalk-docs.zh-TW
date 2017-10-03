---
title: "單一登入： 事件 10521 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00d427ff-74d0-45f5-bb55-ab12b564d767
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 827771fe479084719db18152fd86da7d1fc01a2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10521"></a>單一登入： 事件 10521
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10521|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_SECRETS_NOT_LOADED|  
|訊息文字|無法從主要密碼伺服器的登錄載入密碼。|  
  
## <a name="explanation"></a>說明  
 當無法從登錄取得主要密碼主要密碼伺服器上就會發生這個錯誤事件。 事件記錄檔以取得進一步資訊，可能會有相關的錯誤訊息。 最可能的原因是有權限錯誤或加密錯誤時嘗試存取登錄的 SSO 服務帳戶。 發生這個問題，SSO 服務帳戶已變更。 主要密碼加密的 SSO 服務帳戶識別為基礎的索引鍵。 如果該帳戶已變更，在登錄中現有的主要密碼可以無法再解密。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   變更備份主要密碼，然後變更 SSO 服務帳戶，然後再還原主要密碼的 SSO 服務帳戶。 這可以還原主要密碼，並應可修正這個錯誤。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [主要密碼伺服器](../core/master-secret-server.md)  
  
-   [管理主要密碼](../core/managing-the-master-secret.md)  
  
-   [設定 SSO](../core/configuring-sso.md)  
  
-   [SSO 安全性建議](../core/sso-security-recommendations.md)