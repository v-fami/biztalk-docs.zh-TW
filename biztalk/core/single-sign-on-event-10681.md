---
title: 單一登入： 事件 10681 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87ce2e50-cf54-4b23-b247-f137ce64ba1d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d2b400db062dc76b32d071032ee75c55ef48046
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011663"
---
# <a name="single-sign-on-event-10681"></a>單一登入： 事件 10681
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                              企業單一登入                                                                                               |
| 產品版本 |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                              |
|    事件識別碼     |                                                                                                        10681                                                                                                         |
|  事件來源   |                                                                                                        ENTSSO                                                                                                        |
|    元件    |                                                                                                         N\A                                                                                                          |
|  符號名稱  |                                                                                         SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE                                                                                          |
|  訊息文字   | 外部密碼變更。 無法變更 Windows 密碼，因為一個或多個外部帳戶變更 failed.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶： %3 |

## <a name="explanation"></a>說明  
 這個警告事件表示因為一個或多個外部帳戶變更失敗，已不會變更 Windows 密碼。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

-   請檢查關聯事件的系統和應用程式事件記錄檔。  

-   確認配接器使用 SSO 管理工具的組態。  

-   確認外部系統。  

## <a name="more-info"></a>其他資訊

- [密碼同步](../core/password-synchronization2.md)  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
