---
title: 單一登入： 事件 10516 |Microsoft Docs
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
ms.openlocfilehash: 0d0f3ab8e5d368c04b1a93b9e7e00efa76c50283
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023524"
---
# <a name="single-sign-on-event-10516"></a>單一登入： 事件 10516
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                            企業單一登入                                                                                                                                                            |
| 產品版本 |                                                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                            |
|    事件識別碼     |                                                                                                                                                                      10516                                                                                                                                                                      |
|  事件來源   |                                                                                                                                                                     ENTSSO                                                                                                                                                                      |
|    元件    |                                                                                                                                                                       N\A                                                                                                                                                                       |
|  符號名稱  |                                                                                                                                                           SSO_ERROR_BAD_SSO_APP_ADMIN                                                                                                                                                           |
|  訊息文字   | SSO 分支機構系統管理員帳戶不是有效的。 如果是本機帳戶核取此帳戶是否存在伺服器上。 如果是網域帳戶請連絡您的網域系統管理員。 當帳戶有效 valid.%r 時啟用 SSO<br /><br /> SSO 分支機構系統管理員: %1 %r<br /><br /> 無效的帳戶: %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 分支機構系統管理員帳戶或企業發揚光大登入所建立的群組不是有效的 Windows 帳戶。 SSO 分支機構系統管理員帳戶可以是 Windows 群組帳戶或個別帳戶。 SSO 分支機構系統管理員帳戶也可以是網域或本機群組帳戶。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請確認 SSO 分支機構系統管理員帳戶存在。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 使用者群組](../core/sso-user-groups.md)  

- [如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md)
