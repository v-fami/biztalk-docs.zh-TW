---
title: 單一登入： 事件 10517 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b63e4b0-0ef6-45c2-b8b1-55ac20e79e26
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c1426b4a45d55985ace0548b8e33bb2637f09c0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011399"
---
# <a name="single-sign-on-event-10517"></a>單一登入： 事件 10517
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                  企業單一登入                                                                                                                                                  |
| 產品版本 |                                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                  |
|    事件識別碼     |                                                                                                                                                            10517                                                                                                                                                            |
|  事件來源   |                                                                                                                                                           ENTSSO                                                                                                                                                            |
|    元件    |                                                                                                                                                             N\A                                                                                                                                                             |
|  符號名稱  |                                                                                                                                                   SSO_ERROR_BAD_SSO_ADMIN                                                                                                                                                   |
|  訊息文字   | SSO 系統管理員帳戶不是有效的。 如果是本機帳戶核取此帳戶是否存在伺服器上。 如果是網域帳戶請連絡您的網域系統管理員。 當帳戶有效 valid.%r 時啟用 SSO<br /><br /> SSO 系統管理員: %1 %r<br /><br /> 無效的帳戶: %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示針對企業單一登入指定的 SSO 系統管理員帳戶不是有效的 Windows 帳戶。 執行「企業單一登入」服務的服務帳戶需為此帳戶的成員。 SSO 系統管理員帳戶可以是 Windows 群組帳戶或個別帳戶。 網域或本機群組帳戶，也可以是 SSO 系統管理員帳戶。 若使用個人帳戶，您無法將此帳戶改為另一個個人帳戶。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請確認 SSO 系統管理員帳戶存在。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 使用者群組](../core/sso-user-groups.md)
