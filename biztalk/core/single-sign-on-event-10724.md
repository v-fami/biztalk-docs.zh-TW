---
title: 單一登入： 事件 10724 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 022a6f73-a24b-4058-91a5-b831f6875409
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b53fcdeaaadefbbb90738c9e8d4e2c0d234e338b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986167"
---
# <a name="single-sign-on-event-10724"></a>單一登入： 事件 10724
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                     企業單一登入                                                                                      |
| 產品版本 |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                     |
|    事件識別碼     |                                                                                               10724                                                                                                |
|  事件來源   |                                                                                               ENTSSO                                                                                               |
|    元件    |                                                                                                N\A                                                                                                 |
|  符號名稱  |                                                                                    SSO_ERROR_REPLAY_SECURITY_2                                                                                     |
|  訊息文字   | 重新執行或進度檔案上的安全性已從其原始值變更。%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 目前的檔案安全性: %2 %r<br /><br /> 原始的檔案安全性： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示已變更的重新執行或進度檔案上的安全性。  

 重新執行檔案會儲存在重新執行檔案目錄。 根據預設，SSO 服務帳戶用來建立重新執行檔案和重新執行檔案目錄。 SSO 驗證，任何已變更的重新執行檔案和重新執行檔案目錄的安全性組態建立之後。 如果重新執行檔案目錄已建立具有不同的帳戶，密碼同步處理嘗試建立該目錄中的重新執行檔案時，可以會傳回此錯誤。 強烈建議使用者未變更的重新執行檔案和重新執行檔案目錄的任何安全性設定。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 檢查權限帳戶用來建立重新執行檔案。 這通常是 SSO 系統帳戶。  

  如需詳細資訊，請參閱下列資源：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
