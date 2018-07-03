---
title: 單一登入： 事件 10682 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46f0f425-3946-4bac-a412-488c4afe460d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c7ed830c44404e0365505b7dc0f3a5c6fec8a85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999711"
---
# <a name="single-sign-on-event-10682"></a>單一登入： 事件 10682
## <a name="details"></a>詳細資料  

|                 |                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------|
|  產品名稱   |                                   企業單一登入                                    |
| 產品版本 |                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                   |
|    事件識別碼     |                                             10682                                              |
|  事件來源   |                                             ENTSSO                                             |
|    元件    |                                              N\A                                               |
|  符號名稱  |                               SSO_WARN_REPLAY_INVALID_DIR_FOUND                                |
|  訊息文字   | 已找到的目錄中重新執行檔案目錄中-將予以 ignored.%r<br />目錄： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示在重新執行檔案目錄中已找到的目錄。 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 在此情況下變更密碼會儲存在暫時加密檔案，並會重新執行回 SSO 資料庫當它再次可用時。 重新執行檔案目錄必須包含只重新執行檔案，如果找到目錄，則會發出此錯誤訊息。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 您可以使用命令列工具 ssoconfig-replayFiles 變更重新執行目錄。  

- 如果未使用，請刪除不正確的目錄。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
