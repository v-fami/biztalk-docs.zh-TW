---
title: 單一登入： 事件 10692 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78a476ca-32eb-4f37-a807-25850503db6e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37148a774504599b99665b57691316c35d0783bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987279"
---
# <a name="single-sign-on-event-10692"></a>單一登入： 事件 10692
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                      企業單一登入                                                                                                                      |
| 產品版本 |                                                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                      |
|    事件識別碼     |                                                                                                                                10692                                                                                                                                |
|  事件來源   |                                                                                                                               ENTSSO                                                                                                                                |
|    元件    |                                                                                                                                 N\A                                                                                                                                 |
|  符號名稱  |                                                                                                                    SSO_WARN_REPLAY_ACCESS_DENIED                                                                                                                    |
|  訊息文字   | 無法重新執行的外部密碼變更，因為原始呼叫端不再 adapter.%r 存取帳戶的成員<br /><br /> 重新執行檔案: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 原始的呼叫端: %3 %r<br /><br /> 存取帳戶： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法進行變更 （在 SSO 資料庫） 中指定重新執行檔案因為原本所指定變更的帳戶已不再有效。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 請檢查關聯事件的系統和應用程式事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
