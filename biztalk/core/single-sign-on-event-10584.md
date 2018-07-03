---
title: 單一登入： 事件 10584 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8af9377d-b4fd-48a6-961a-3629b3db644a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0188f09ab94bd14df0dbe3fee0b91341cd9eb087
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996719"
---
# <a name="single-sign-on-event-10584"></a>單一登入： 事件 10584
## <a name="details"></a>詳細資料  
  
|                 |                                                                |
|-----------------|----------------------------------------------------------------|
|  產品名稱   |                   企業單一登入                    |
| 產品版本 |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    事件識別碼     |                             10584                              |
|  事件來源   |                             ENTSSO                             |
|    元件    |                              不適用                               |
|  符號名稱  |                   SSO_WARN_NO_IMPERSONATION                    |
|  訊息文字   | 無法模擬用戶端。%r<br /><br /> 錯誤碼： %1 |
  
## <a name="explanation"></a>說明  
 模擬用戶端是指 ENTSSO 系統來驗證用戶端的身分識別。 當系統無法模擬用戶端時，可能會發生三件事的其中一個。 用戶端可能會嘗試執行的一般活動、 用戶端可能嘗試滲透系統安全性，或用戶端應用程式可能已設計可封鎖模擬。  
  
## <a name="user-action"></a>使用者動作  
 找出用戶端應用程式並判斷它正嘗試執行動作，以及它封鎖模擬。