---
title: "單一登入： 事件 10613 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a87ca19-24a0-4cf8-984f-2f70d7b5018c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7230a0d6400a7265ef9f3cedb6bb47cc23aade
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10613"></a>單一登入： 事件 10613
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10613|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_RPC_CALLBACK|  
|訊息文字|SSO 伺服器存取遭拒。%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> RPC 呼叫資訊: %2: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 呼叫已從用戶端對 SSO 伺服器，但不是被接受。 原因可能是由數種不同原因，例如不正確的通訊協定或用戶端上沒有足夠的安全性權限。  
  
## <a name="user-action"></a>使用者動作  
 請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。