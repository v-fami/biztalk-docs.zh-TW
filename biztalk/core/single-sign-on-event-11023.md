---
title: 單一登入： 事件 11023 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: feeb4ede-6045-46bf-9f2b-65062c583faa
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cecf9536babaf2510444abade571149c5fc0e0a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991535"
---
# <a name="single-sign-on-event-11023"></a>單一登入： 事件 11023
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                 企業單一登入                                                                                                                                  |
| 產品版本 |                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                 |
|    事件識別碼     |                                                                                                                                           11023                                                                                                                                            |
|  事件來源   |                                                                                                                                           ENTSSO                                                                                                                                           |
|    元件    |                                                                                                                                            不適用                                                                                                                                             |
|  符號名稱  |                                                                                                                             SSO_WARN_WINDOWS_PASSWORD_DELETED                                                                                                                              |
|  訊息文字   | 無效的 Windows 密碼在 SSO 資料庫中已刪除，以防止帳戶 lockout.%r<br /><br /> 若要設定此 Windows account.%r 的外部認證使用 SSO 管理工具<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶： %3 |
  
## <a name="explanation"></a>說明  
 已刪除無效的 Windows 密碼。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用 SSO 管理工具來設定此 Windows 帳戶的外部認證。 如需詳細資訊，請參閱 <<c0> [ 使用 SSO](../core/using-sso.md)。