---
title: 單一登入： 事件 11057 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e165e24-fe43-4899-ab6e-1437f639f534
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bce17e6659867d8bcf8c39408ec24d8e79052aa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967655"
---
# <a name="single-sign-on-event-11057"></a>單一登入： 事件 11057
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                企業單一登入                                                                                                                |
| 產品版本 |                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                |
|    事件識別碼     |                                                                                                                          11057                                                                                                                          |
|  事件來源   |                                                                                                                         ENTSSO                                                                                                                          |
|    元件    |                                                                                                                           不適用                                                                                                                           |
|  符號名稱  |                                                                                                        SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS                                                                                                         |
|  訊息文字   | 直接密碼變更。 這種對應的部分遺失外部認證欄位已設為預設值。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 應用程式名稱: %2 %r<br /><br /> Windows 帳戶: %3 %r<br /><br /> 外部帳戶： %4 |
  
## <a name="explanation"></a>說明  
 雖然可能可以使用「直接密碼同步」變更密碼，但是此功能只支援一個外部認證欄位。 在本例中，ENTSSO 系統遇到一個以上的外部認證欄位，且將這些欄位設為預設 (空白) 值。  
  
## <a name="user-action"></a>使用者動作  
 使用者不必採取任何動作。