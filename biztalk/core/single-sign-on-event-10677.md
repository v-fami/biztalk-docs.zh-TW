---
title: 單一登入： 事件 10677 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2894792b-e1c9-4c24-875d-9193cbb5cd35
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1fc5bfbb6df26f1b1125a0d5d8b06a75e441f15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021996"
---
# <a name="single-sign-on-event-10677"></a>單一登入： 事件 10677
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                    企業單一登入                                                                                                                     |
| 產品版本 |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                    |
|    事件識別碼     |                                                                                                                              10677                                                                                                                               |
|  事件來源   |                                                                                                                              ENTSSO                                                                                                                              |
|    元件    |                                                                                                                               N\A                                                                                                                                |
|  符號名稱  |                                                                                                                  SSO_WARN_NO_EXISTING_PASSWORD                                                                                                                   |
|  訊息文字   | 外部密碼變更。 無法驗證舊密碼，因為沒有任何現有的認證，此外部 account.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示外部密碼變更不會發生的因為舊密碼並沒有現有的認證。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

-   判斷哪些應用程式已指派給此配接器 （在事件記錄檔訊息中的名稱），然後再使用 設定此外部帳戶的外部認證的 SSO 管理工具。 您必須在所有這些應用程式設定 （適用於指定的帳戶） 的外部密碼。  

## <a name="more-info"></a>其他資訊

- [密碼同步](../core/password-synchronization2.md)  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
