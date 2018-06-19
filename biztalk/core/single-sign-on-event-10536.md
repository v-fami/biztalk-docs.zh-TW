---
title: 單一登入： 事件 10536 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d493a45b-c4ed-40fc-8803-b3ca12f9795b
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 273533009d68c36d15f08b7ed106a3e1f7a1b380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271230"
---
# <a name="single-sign-on-event-10536"></a>單一登入： 事件 10536
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10536|  
|事件來源|ENTSSO|  
|元件|CO|  
|符號名稱|SSO_WARN_API_AUDIT|  
|訊息文字|SSO AUDIT%r<br /><br /> 函式: %1 %r<br /><br /> 追蹤識別碼: %2 %r<br /><br /> 用戶端電腦: %3 %r<br /><br /> 用戶端使用者: %4 %r<br /><br /> 應用程式名稱: %5 %r<br /><br /> 錯誤碼： %6|  
  
## <a name="explanation"></a>說明  
 此稽核警告事件表示已發生事件符合使用者定義稽核層級。 包含此事件訊息：  
  
 **函式：** 正在執行的函式  
  
 **追蹤識別碼：** 呼叫第一個 SSO 應用程式開發介面時，產生的唯一 GUID。  
  
 **用戶端電腦：** 參予函式的用戶端電腦。  
  
 **用戶端使用者：** 叫用該函數的使用者帳戶的名稱。  
  
 **應用程式名稱：** 名稱的 sso 分支機構應用程式與這個函式相關聯。  
  
 **錯誤碼：** 唯一的錯誤識別碼。  
  
 這種類型的事件用於診斷問題，在開發期間疑難排解，或執行應用程式。 提供的資訊可以用來判斷正在進行的 SSO 應用程式開發介面呼叫。  
  
 您可以將稽核層級為 0/1/2/3-0 表示 「 無 」，1 表示 「 低 」 會顯示錯誤只，2 代表"medium"會顯示錯誤和警告，而 3 表示 「 高 」 會顯示所有稽核訊息。  
  
## <a name="user-action"></a>使用者動作  
  
-   請檢查事件記錄檔中相關聯的事件訊息。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何稽核 SSO](../core/how-to-audit-sso.md)  
  
-   [使用 SSO](../core/using-sso.md)