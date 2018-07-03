---
title: 單一登入： 事件 10693 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 672bac7d-0ccc-4a42-a49d-57e387f4cf3a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f9dd254fd81d54f0c60a2ea8b0a143e94ddd516
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009479"
---
# <a name="single-sign-on-event-10693"></a>單一登入： 事件 10693
## <a name="details"></a>詳細資料  

|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                       企業單一登入                                        |
| 產品版本 |                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                       |
|    事件識別碼     |                                                 10693                                                  |
|  事件來源   |                                                 ENTSSO                                                 |
|    元件    |                                                  N\A                                                   |
|  符號名稱  |                                    SSO_WARNING_REPLAY_CANNOT_CREATE                                    |
|  訊息文字   | 無法建立重新執行或進度 file.%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 錯誤碼： %2 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 找不到 SSO 資料庫的連線遺失時，請建立重新執行和/或進度檔案。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查關聯事件的系統和應用程式事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
