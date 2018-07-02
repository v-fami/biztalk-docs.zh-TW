---
title: 單一登入： 事件 10727 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ff7ac94-6f1e-4e56-853e-efc50b1fa1b6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f25dd71e223452707ff00e23b6a3a3bc797d10f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970543"
---
# <a name="single-sign-on-event-10727"></a>單一登入： 事件 10727
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                        企業單一登入                                                         |
| 產品版本 |                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                        |
|    事件識別碼     |                                                                  10727                                                                   |
|  事件來源   |                                                                  ENTSSO                                                                  |
|    元件    |                                                                   N\A                                                                    |
|  符號名稱  |                                                      SSO_WARN_REPLAY_RECORD_FAILED                                                       |
|  訊息文字   | 重新執行預存外部密碼變更 failed.%r<br /><br /> 配接器: %1 %r<br /><br /> 檔案名稱: %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這則警告表示 SSO 無法重新執行記錄重新執行檔案中的密碼變更。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 請檢查關聯事件的系統和應用程式事件記錄檔。  

  如需詳細資訊，請參閱下列資源：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
