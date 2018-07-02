---
title: 單一登入： 事件 10694 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75faca65-48d9-45f6-b079-2b612ef3de76
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45d5bcd178020e6aee2b16e3cd3fbababd6b8498
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981647"
---
# <a name="single-sign-on-event-10694"></a>單一登入： 事件 10694
## <a name="details"></a>詳細資料  

|                 |                                                                                     |
|-----------------|-------------------------------------------------------------------------------------|
|  產品名稱   |                              企業單一登入                              |
| 產品版本 |             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]              |
|    事件識別碼     |                                        10694                                        |
|  事件來源   |                                       ENTSSO                                        |
|    元件    |                                         N\A                                         |
|  符號名稱  |                         SSO_ERROR_REPLAY_INCORRECT_VERSION                          |
|  訊息文字   | 重新執行或進度 file.%r 中偵測到損毀<br /><br /> 檔案名稱： %1 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 已重新建立與 SSO 資料庫，請連絡，但無法讀取重新執行檔案，因為已損毀。 如果 SSO 無法開啟重新執行檔案，它將繼續進行下一步 重新執行檔案 （如果有的話）。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查關聯事件的系統和應用程式事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
