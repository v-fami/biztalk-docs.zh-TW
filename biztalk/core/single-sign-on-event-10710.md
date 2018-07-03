---
title: 單一登入： 事件 10710 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 469dc407-be7a-45a1-bcf5-2ba7060a19e2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 888468da03c01f654bd550ce210b02c4a03ad40b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989919"
---
# <a name="single-sign-on-event-10710"></a>單一登入： 事件 10710
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                          企業單一登入                                                                          |
| 產品版本 |                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                          |
|    事件識別碼     |                                                                                    10710                                                                                    |
|  事件來源   |                                                                                   ENTSSO                                                                                    |
|    元件    |                                                                                     N\A                                                                                     |
|  符號名稱  |                                                                        SSO_INFO_PS_WIN_CHANGE_DAMPED                                                                        |
|  訊息文字   | Windows 密碼變更已禁止 （偵測到重複的和 discarded).%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 用戶端使用者： %3 |

## <a name="explanation"></a>說明  
 這個資訊事件表示已捨棄 Windows 密碼變更，因為它偵測到為重複。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱下列資源：  

- [密碼同步](../core/password-synchronization2.md)
