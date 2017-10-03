---
title: "單一登入： 事件 10682 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46f0f425-3946-4bac-a412-488c4afe460d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79aeff556fbbbbbbbcf41f63a37ab3b47311d697
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10682"></a>單一登入： 事件 10682
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10682|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_REPLAY_INVALID_DIR_FOUND|  
|訊息文字|目錄中找不到重新執行檔案目錄-將 ignored.%r<br />目錄： %1|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示目錄已重新執行檔案目錄中找到。 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 在此情況下密碼變更會儲存在暫時加密檔案，而且當它再次可用時傳回至 SSO 資料庫重新執行。 重新執行檔案目錄必須只包含重新執行檔案 – 如果找到目錄，則會發出這則錯誤訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  
  
-   使用命令列工具 ssoconfig replayFiles 變更重新執行目錄。  
  
-   如果未使用，請刪除不正確的目錄。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)