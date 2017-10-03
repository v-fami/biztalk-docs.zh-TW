---
title: "單一登入： 事件 10596 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d70aabcf-aa53-40bf-8937-44f191af1aec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051fdf627edc3f560a8d02026207dc2fe5bb3533
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10596"></a>單一登入： 事件 10596
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10596|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_TICKET_USER_NOT_IN_GROUP|  
|訊息文字|因為票證的核發對象的使用者不是應用程式使用者 account.%r 的成員，就無法贖回票證<br /><br /> 應用程式名稱: %1 %r<br /><br /> 票證核發對: %2 %r<br /><br /> 應用程式使用者： %3|  
  
## <a name="explanation"></a>說明  
 因為票證的核發對象的使用者不是應用程式使用者帳戶的成員，就無法贖回票證。  
  
## <a name="user-action"></a>使用者動作  
 請重新發出票證的使用者可以是應用程式使用者帳戶的成員。