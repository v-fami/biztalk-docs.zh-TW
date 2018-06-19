---
title: 單一登入： 事件 10584 |Microsoft 文件
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
ms.openlocfilehash: d08be0100d53f081eb7d8f4faa27d1e7f46f6f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270366"
---
# <a name="single-sign-on-event-10584"></a>單一登入： 事件 10584
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10584|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_NO_IMPERSONATION|  
|訊息文字|無法模擬用戶端。%r<br /><br /> 錯誤碼： %1|  
  
## <a name="explanation"></a>說明  
 模擬用戶端是 ENTSSO 系統會驗證用戶端的身分識別的項目。 當系統無法模擬用戶端，其中三種情況可能會發生。 用戶端可能會嘗試執行的一般活動、 用戶端可能嘗試滲透系統安全性，或用戶端應用程式可能已設計可封鎖模擬。  
  
## <a name="user-action"></a>使用者動作  
 找出用戶端應用程式並判斷它正嘗試執行作業，以及它封鎖模擬。