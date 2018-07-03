---
title: 單一登入： 事件 10596 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d70aabcf-aa53-40bf-8937-44f191af1aec
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a1e565ca3b96663e0ece5a2cf68c02d3258ac5d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008791"
---
# <a name="single-sign-on-event-10596"></a>單一登入： 事件 10596
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                         企業單一登入                                                                                                          |
| 產品版本 |                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                         |
|    事件識別碼     |                                                                                                                   10596                                                                                                                    |
|  事件來源   |                                                                                                                   ENTSSO                                                                                                                   |
|    元件    |                                                                                                                    不適用                                                                                                                     |
|  符號名稱  |                                                                                                     SSO_WARN_TICKET_USER_NOT_IN_GROUP                                                                                                      |
|  訊息文字   | 無法贖回票證，因為的使用者票證的核發對象不是應用程式使用者 account.%r 的成員<br /><br /> 應用程式名稱: %1 %r<br /><br /> 票證核發對: %2 %r<br /><br /> 應用程式使用者： %3 |
  
## <a name="explanation"></a>說明  
 因為票證的核發對象的使用者不是應用程式使用者帳戶的成員，就無法贖回票證。  
  
## <a name="user-action"></a>使用者動作  
 請重新發出的票證應用程式使用者帳戶隸屬的使用者。