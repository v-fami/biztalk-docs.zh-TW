---
title: 單一登入： 事件 11059 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac5b6ce7-8819-4b9d-85f7-f5dfaf940487
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a22b2a68acc6cd4be3d5cf854a4d965d897e302
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965775"
---
# <a name="single-sign-on-event-11059"></a>單一登入： 事件 11059
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                               企業單一登入                                                                                                               |
| 產品版本 |                                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                               |
|    事件識別碼     |                                                                                                                         11059                                                                                                                         |
|  事件來源   |                                                                                                                        ENTSSO                                                                                                                         |
|    元件    |                                                                                                                          不適用                                                                                                                          |
|  符號名稱  |                                                                                                          SSO_INFO_INVALID_USER_NOT_IN_GROUP                                                                                                           |
|  訊息文字   | 無法建立對應，因為指定的使用者不是應用程式使用者帳戶的成員。%r<br /><br /> Windows 帳戶： %1\\%2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 應用程式使用者: %4 %r<br /><br /> 錯誤碼： %5 |
  
## <a name="explanation"></a>說明  
 無法建立對應，因為指定的使用者不是應用程式使用者帳戶的成員。  
  
## <a name="user-action"></a>使用者動作  
 請連絡您的 ENTSSO 系統管理員如何提升您的應用程式使用者帳戶的成員。