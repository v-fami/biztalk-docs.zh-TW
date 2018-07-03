---
title: 單一登入： 事件 10725 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89218d73-bda0-4e98-a578-cd244af79041
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 206173f45d6702290eef7cd8e203c2439ce44cc2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016136"
---
# <a name="single-sign-on-event-10725"></a>單一登入： 事件 10725
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                        企業單一登入                                                                                        |
| 產品版本 |                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                        |
|    事件識別碼     |                                                                                                  10725                                                                                                  |
|  事件來源   |                                                                                                 ENTSSO                                                                                                  |
|    元件    |                                                                                                   N\A                                                                                                   |
|  符號名稱  |                                                                                       SSO_ERROR_REPLAY_SECURITY_3                                                                                       |
|  訊息文字   | 重新執行檔案目錄的安全性不符上重新執行或進度 file.%r 的安全性<br /><br /> 檔案名稱: %1 %r<br /><br /> 檔案安全性: %2 %r<br /><br /> 目錄安全性： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示重新執行檔案目錄的安全性不符上重新執行或進度檔案的安全性。  

 重新執行檔案會儲存在重新執行檔案目錄。 根據預設，SSO 服務帳戶用來建立重新執行檔案和重新執行檔案目錄。 SSO 驗證，任何已變更的重新執行檔案和重新執行檔案目錄的安全性組態建立之後。 如果重新執行檔案目錄已建立具有不同的帳戶，密碼同步處理嘗試建立該目錄中的重新執行檔案時，可以會傳回此錯誤。 強烈建議使用者未變更的重新執行檔案和重新執行檔案目錄的任何安全性設定。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查用來建立重新執行檔案目錄的帳戶。 如果目錄是空的請嘗試再次執行密碼同步處理。 它可能需要重新建立為 SSO 服務使用相同的服務帳戶的目錄。 如果您無法重新建立為 SSO 服務使用相同的帳戶重新執行檔案目錄，請檢查該帳戶的權限。  

  如需詳細資訊，請參閱下列資源：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
