---
title: 單一登入： 事件 10653 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d85aca-20d9-4d65-8834-b31eacf143c8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9f0edb3ce5fa7f8fb59c4b65914a9c8b6640adc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969455"
---
# <a name="single-sign-on-event-10653"></a>單一登入： 事件 10653
## <a name="details"></a>詳細資料  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10653                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            N\A                             |
|  符號名稱  |        SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED         |
|  訊息文字   |    密碼同步處理伺服器 （針對配接器） 存取 denied.%r    |

## <a name="explanation"></a>說明  
 這個錯誤事件表示用戶端嘗試連線到伺服器，但拒絕呼叫。 原因可能是由數項不同的原因，例如不正確的通訊協定或安全性權限不足。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [密碼同步](../core/password-synchronization2.md)
