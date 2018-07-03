---
title: 單一登入： 事件 10699 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff26533-e4d7-47b5-92d5-bd8c72fab89a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3802f04d2adf7d95a6ff10ae208acabbc1acf8ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983367"
---
# <a name="single-sign-on-event-10699"></a>單一登入： 事件 10699
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                       企業單一登入                                                                                                       |
| 產品版本 |                                                                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                       |
|    事件識別碼     |                                                                                                                 10699                                                                                                                 |
|  事件來源   |                                                                                                                ENTSSO                                                                                                                 |
|    元件    |                                                                                                                  N\A                                                                                                                  |
|  符號名稱  |                                                                                           SSO_INFO_EXTERNAL_PASSWORD_CHANGE_RECEIVED_REPLAY                                                                                           |
|  訊息文字   | 從 （從重新執行 file).%r 配接器收到外部密碼變更<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶: %3 %r<br /><br /> 用戶端使用者: %4 %r<br /><br /> 資料錄數目： %5 |

## <a name="explanation"></a>說明  
 這個資訊事件表示，從記錄到重新執行檔案配接器收到外部密碼變更。 SSO 時，執行重新執行檔案的預存外部密碼變更。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
