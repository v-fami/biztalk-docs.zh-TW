---
title: "單一登入： 事件 11042 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1927bb5-a400-4e3a-8f80-95ef5693216c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da20346fbf2f73ac2ab64db3c9137394aa5bd366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11042"></a>單一登入： 事件 11042
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11042|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_ACCESS_DENIED_ACCOUNTS|  
|訊息文字|拒絕存取。<br /><br /> 用戶端使用者必須是其中一個下列帳戶的成員，才能執行此 function.%r<br /><br /> SSO 系統管理員: %1 %r<br /><br /> SSO 分支機構系統管理員: %2 %r<br /><br /> 應用程式系統管理員: %3 %r<br /><br /> 應用程式使用者: %4 %r<br /><br /> 其他資料： %5|  
  
## <a name="explanation"></a>說明  
 用戶端使用者必須是其中一個警告，以執行此函式中列出的帳戶的成員。  
  
## <a name="user-action"></a>使用者動作  
 您必須加入其中一個帳戶來執行此函式。