---
title: 單一登入： 事件 11071 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c0f61b9-cd86-482b-a8fe-0093a928c89b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74bc4793937574cc90021b95b6c1850409d57871
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975887"
---
# <a name="single-sign-on-event-11071"></a>單一登入： 事件 11071
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                   企業單一登入                                                                                   |
| 產品版本 |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                   |
|    事件識別碼     |                                                                                             11071                                                                                             |
|  事件來源   |                                                                                            ENTSSO                                                                                             |
|    元件    |                                                                                              不適用                                                                                              |
|  符號名稱  |                                                                         SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH                                                                          |
|  訊息文字   | Windows 密碼變更已被捨棄，因為 Windows 密碼長度為零個字元。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 用戶端使用者： %3 |
  
## <a name="explanation"></a>說明  
 已捨棄 Windows 密碼變更，因為 Windows 密碼長度為零個字元。 提供的 Windows 帳戶和用戶端使用者名稱。  
  
## <a name="user-action"></a>使用者動作  
 變更密碼同樣地，使用的 SSO 系統所需的字元類型與數量。