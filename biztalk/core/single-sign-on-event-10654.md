---
title: 單一登入： 事件 10654 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49372d5a-8136-4bdd-8004-b5736ddbe058
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca59040b340d033ab6c355c0440378f09d87000
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974479"
---
# <a name="single-sign-on-event-10654"></a>單一登入： 事件 10654
## <a name="details"></a>詳細資料  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10654                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            N\A                             |
|  符號名稱  |        SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED         |
|  訊息文字   |    密碼同步伺服器 (針對 Windows) 存取遭拒。%r     |

## <a name="explanation"></a>說明  
 這個錯誤事件表示訊息傳送至 [名稱] 伺服器，但已封鎖的回覆。 原因可能是由數項不同的原因，例如不正確的通訊協定或在伺服器上沒有足夠的安全性權限。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [密碼同步](../core/password-synchronization2.md)
