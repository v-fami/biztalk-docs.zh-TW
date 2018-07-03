---
title: 單一登入： 事件 10518 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 274e29f9-1933-4e40-83c0-2e84c6708315
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76b267950d734f6a0935ed22e27782e8a6bcd1f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011407"
---
# <a name="single-sign-on-event-10518"></a>單一登入： 事件 10518
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                                                                                                企業單一登入                                                                                                                                                                                                                                 |
| 產品版本 |                                                                                                                                                                                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                                                                |
|    事件識別碼     |                                                                                                                                                                                                                                          10518                                                                                                                                                                                                                                           |
|  事件來源   |                                                                                                                                                                                                                                          ENTSSO                                                                                                                                                                                                                                          |
|    元件    |                                                                                                                                                                                                                                           N\A                                                                                                                                                                                                                                            |
|  符號名稱  |                                                                                                                                                                                                                                 SSO_WARN_BAD_USER_GROUP                                                                                                                                                                                                                                  |
|  訊息文字   | 此應用程式的應用程式使用者帳戶不是有效的。 如果是本機帳戶核取此帳戶是否存在伺服器上。 如果是網域帳戶請連絡您的網域系統管理員。 有效的帳戶時，請啟用應用程式。 如果您不會在此 computer.%r 上使用此應用程式，您可以忽略此訊息<br /><br /> 應用程式名稱: %1 %r<br /><br /> 應用程式使用者: %2 %r<br /><br /> 無效的帳戶: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示應用程式使用者群組帳戶不是有效的 Windows 帳戶。 沒有一個應用程式使用者帳戶群組，每個分支機構應用程式。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 驗證指定的應用程式使用者帳戶存在。  

- 使用 SSO 管理公用程式來驗證指定的分支機構應用程式設定為使用正確的應用程式的使用者帳戶。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 使用者群組](../core/sso-user-groups.md)  

- [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)  

- [如何更新分支機構應用程式屬性](../core/how-to-update-the-properties-of-an-affiliate-application.md)
