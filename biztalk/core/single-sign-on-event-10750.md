---
title: 單一登入： 事件 10750 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a0fdaf2-d429-40b9-adc3-eb134687fb1a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28526c6695cbf8f9c29e99621d6cb2f852fa7021
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984367"
---
# <a name="single-sign-on-event-10750"></a>單一登入： 事件 10750
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                    企業單一登入                                                                                                                     |
| 產品版本 |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                    |
|    事件識別碼     |                                                                                                                              10750                                                                                                                               |
|  事件來源   |                                                                                                                              ENTSSO                                                                                                                              |
|    元件    |                                                                                                                               N\A                                                                                                                                |
|  符號名稱  |                                                                                                                SSO_ERROR_PS_WRONG_USER_NAME_TYPE                                                                                                                 |
|  訊息文字   | PasswordChangeNotify： 不正確的使用者名稱類型。 接受的值只有 USER_NAME_TYPE_NT4。<br /><br /> 設定目標 Active Directory.%r 中，不正確<br /><br /> 使用者名稱類型: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示密碼同步處理收到的密碼變更的密碼變更通知服務 (PCNS)，但密碼變更是格式錯誤。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 檢查 PCNS 設定。 PCNS 可以只在網域控制站上執行。  

- Active Directory 中設定使用者名稱類型 USER_NAME_TYPE_NT4。  

  如需詳細資訊，請參閱下列資源：  

- 請參閱 Active Directory 文件，如需有關如何指定使用者名稱類型資訊。  

- [密碼同步](../core/password-synchronization2.md)
