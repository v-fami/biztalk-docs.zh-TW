---
title: 單一登入： 事件 10676 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec0e86fb-921d-4505-b458-51b565123ea7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63228e82546e100c81bf01c301d7d9507f147671
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991927"
---
# <a name="single-sign-on-event-10676"></a>單一登入： 事件 10676
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                             企業單一登入                                                                                             |
| 產品版本 |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                             |
|    事件識別碼     |                                                                                                       10676                                                                                                       |
|  事件來源   |                                                                                                      ENTSSO                                                                                                       |
|    元件    |                                                                                                        N\A                                                                                                        |
|  符號名稱  |                                                                                          SSO_ERROR_REQUIRE_OLD_PASSWORD                                                                                           |
|  訊息文字   | 外部密碼變更。 變更外部帳戶的密碼時，配接器必須提供舊 password.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 「 密碼同步配接器已設定為預期收到來自外部系統中，舊的密碼，但未提供舊密碼。 可能是未設定外部系統 （外部密碼同步配接器），或如預期般運作或密碼同步配接器設定不正確。 這項錯誤也可能會傳回錯誤的程式碼符號名稱 ENTSSO_E_REQUIRE_OLD_PASSWORD。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

-   若要設定使用者可設定的屬性使用 SSO 管理工具**驗證舊密碼**密碼同步配接器選項內容 索引標籤上。這個屬性也可以設定建立配接器，透過命令列工具 (ssops.exe) 旗標名稱`verifyOldPassword`和也當建立新的密碼同步配接器使用 「 密碼同步配接器精靈 」。  

## <a name="more-info"></a>其他資訊

- [密碼同步](../core/password-synchronization2.md)  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
