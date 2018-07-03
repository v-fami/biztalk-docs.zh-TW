---
title: 單一登入： 事件 10536 |Microsoft Docs
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
ms.openlocfilehash: 49687739fced504c9dccc06969c9eb3e10d9aae4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016128"
---
# <a name="single-sign-on-event-10536"></a>單一登入： 事件 10536
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                     企業單一登入                                                                                      |
| 產品版本 |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                     |
|    事件識別碼     |                                                                                               10536                                                                                                |
|  事件來源   |                                                                                               ENTSSO                                                                                               |
|    元件    |                                                                                                 CO                                                                                                 |
|  符號名稱  |                                                                                         SSO_WARN_API_AUDIT                                                                                         |
|  訊息文字   | SSO AUDIT%r<br /><br /> 函式: %1 %r<br /><br /> 追蹤識別碼: %2 %r<br /><br /> 用戶端電腦: %3 %r<br /><br /> 用戶端使用者: %4 %r<br /><br /> 應用程式名稱: %5 %r<br /><br /> 錯誤碼： %6 |

## <a name="explanation"></a>說明  
 此警告稽核事件會指出發生事件符合使用者定義稽核層級。 此事件訊息包含：  

 **函式：** 正在執行的函式  

 **追蹤識別碼：** 呼叫第一個 SSO API 時，產生的唯一 GUID。  

 **用戶端電腦：** 函式的起源的用戶端電腦。  

 **用戶端使用者：** 叫用函式的使用者帳戶的名稱。  

 **應用程式名稱：** 名稱的 SSO 分支機構應用程式，此函式相關聯。  

 **錯誤碼：** 唯一錯誤識別碼。  

 這種類型的事件用於在開發期間診斷問題、 疑難排解、 或執行的應用程式。 提供的資訊可用來判斷正在進行的 SSO API 呼叫。  

 可以設定的稽核層級為 0/1/2/3-0 表示 「 無 」、 「 低 」 的 1 表示會顯示只記錄錯誤、 2 表示 「 中 」 會顯示錯誤和警告，和 3 表示 「 高 」 會顯示所有的稽核訊息。  

## <a name="user-action"></a>使用者動作  

- 請檢查事件記錄檔相關聯的事件訊息。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何稽核 SSO](../core/how-to-audit-sso.md)  

- [使用 SSO](../core/using-sso.md)
