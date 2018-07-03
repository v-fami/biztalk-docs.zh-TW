---
title: 單一登入： 事件 10746 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8189120b-923a-4c88-937e-f06565bcac56
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3f4fa77909ba53e16d3dffd31073ff93e233ed5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998863"
---
# <a name="single-sign-on-event-10746"></a>單一登入： 事件 10746
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                           企業單一登入                                                           |
| 產品版本 |                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                           |
|    事件識別碼     |                                                                     10746                                                                     |
|  事件來源   |                                                                    ENTSSO                                                                     |
|    元件    |                                                                      N\A                                                                      |
|  符號名稱  |                                                           SSO_WARN_PASSWORD_EXPIRED                                                           |
|  訊息文字   | 外部帳戶的密碼已 expired.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶： %3 |

## <a name="explanation"></a>說明  
 這個警告事件表示外部帳戶的密碼已過期。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請檢查系統和應用程式事件記錄檔相關聯的錯誤。    

## <a name="more-info"></a>其他資訊
如需詳細資訊，請參閱下列資源：  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  

- [密碼同步](../core/password-synchronization2.md)
