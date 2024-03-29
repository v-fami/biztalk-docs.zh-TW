---
title: 單一登入： 事件 10743 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2908bc9-1fac-4ab9-869f-0c5512864da4
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd0c8c170a17fade96daa0b9ecc0a3613afb1236
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003663"
---
# <a name="single-sign-on-event-10743"></a>單一登入： 事件 10743
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                   企業單一登入                                                                    |
| 產品版本 |                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                   |
|    事件識別碼     |                                                                             10743                                                                              |
|  事件來源   |                                                                             ENTSSO                                                                             |
|    元件    |                                                                              N\A                                                                               |
|  符號名稱  |                                                                    SSO_ERROR_REPLAY_STOPPED                                                                    |
|  訊息文字   | 由於 errors.%r 停止的重新執行預存外部密碼變更<br /><br /> 重新執行檔案: %1 %r<br /><br /> 其他資料: %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示該重新執行預存外部密碼變更因為錯誤而停止。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查關聯事件的系統和應用程式事件記錄檔。  

  如需詳細資訊，請參閱下列資源：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
