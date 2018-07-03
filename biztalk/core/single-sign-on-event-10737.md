---
title: 單一登入： 事件 10737 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2102930b-8b1f-4d48-a14d-e8884dc7f9aa
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd21b244e86c14aaf0f3af7418f1ca2ed8fbf067
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987679"
---
# <a name="single-sign-on-event-10737"></a>單一登入： 事件 10737
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                               企業單一登入                                                                                                |
| 產品版本 |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    事件識別碼     |                                                                                                         10737                                                                                                          |
|  事件來源   |                                                                                                         ENTSSO                                                                                                         |
|    元件    |                                                                                                          N\A                                                                                                           |
|  符號名稱  |                                                                                           SSO_WARN_PS_SET_EXTERNAL_PASSWORD                                                                                            |
|  訊息文字   | 無法更新 SSO database.%r 中的外部密碼<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶: %4 %r<br /><br /> 錯誤碼： %5 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 無法更新 SSO 資料庫中的外部密碼。 有各種可能的原因的警告訊息中指出的失敗在某些情況下，這個警告可能表示設定有問題，或對應可能已刪除，處理密碼變更時。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 重試一次變更密碼。  

- 如果其他嘗試繼續失敗，變更的密碼使用 UI 或命令列工具，以手動方式。  

  如需詳細資訊，請參閱下列資源：  

- [密碼同步](../core/password-synchronization2.md)
