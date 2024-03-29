---
title: 單一登入： 事件 10709 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98e86890-88dd-49f0-bb2c-1234507e8be5
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b114b8afb55c41171ef537a9dfc56d341943a226
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014247"
---
# <a name="single-sign-on-event-10709"></a>單一登入： 事件 10709
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                  企業單一登入                                                                                                                   |
| 產品版本 |                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                  |
|    事件識別碼     |                                                                                                                            10709                                                                                                                             |
|  事件來源   |                                                                                                                            ENTSSO                                                                                                                            |
|    元件    |                                                                                                                             N\A                                                                                                                              |
|  符號名稱  |                                                                                                                SSO_WARN_PS_PCNS_ACCESS_DENIED                                                                                                                |
|  訊息文字   | 來自 PCNS 的 Windows 密碼變更將只會接受來自網域控制站存取 domain.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> 存取網域: %3 %r<br /><br /> 存取 Sid: %4 %r<br /><br /> 錯誤碼： %5 |

## <a name="explanation"></a>說明  
 這個警告事件表示 Windows 密碼變更已收到 ENTSSO 伺服器的網域外部的伺服器從密碼變更通知服務 (PCNS)。 從 ENTSSO 伺服器相同的網域中網域控制站，將只會接受 Windows 密碼變更。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 設定 PCNS 與相同的網域中的 ENTSSO 伺服器。  

  如需詳細資訊，請參閱下列資源：  

- [密碼同步](../core/password-synchronization2.md)
