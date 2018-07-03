---
title: 單一登入： 事件 10652 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae7fe452-bcec-4722-8ec6-78d4fe462a0a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2e27c678f2c031c642107cd770566f92d7ca708
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985743"
---
# <a name="single-sign-on-event-10652"></a>單一登入： 事件 10652
## <a name="details"></a>詳細資料  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  產品名稱   |                         企業單一登入                         |
| 產品版本 |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    事件識別碼     |                                   10652                                   |
|  事件來源   |                                  ENTSSO                                   |
|    元件    |                                    N\A                                    |
|  符號名稱  |                   SSO_ERROR_PASSWORD_SYNC_START_FAILED                    |
|  訊息文字   | 密碼同步處理服務無法 initialize.%r<br /><br /> 錯誤碼： %1 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示密碼同步處理服務無法啟動因為發生例外狀況。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [密碼同步](../core/password-synchronization2.md)
