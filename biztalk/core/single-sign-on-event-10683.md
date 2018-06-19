---
title: 單一登入： 事件 10683 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83cd1b96-cd79-4ddc-952b-94a7de216666
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c383a02400523686f00011c5eb6f71c9542ec5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271542"
---
# <a name="single-sign-on-event-10683"></a>單一登入： 事件 10683
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10683|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD|  
|訊息文字|重新執行檔案已刪除，因為它太 old.%r<br />重新執行檔案： %1|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示已刪除重新執行檔案，因為它太舊。 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 在此案例中，密碼變更會儲存在暫時加密檔案，並且會在可用時重新執行回 SSO 資料庫。 可以將檔案重新執行回 SSO 資料庫時，如果檔案經偵測已經太舊，則會遭到捨棄。 SSO 密碼同步系統會捨棄所有舊的密碼變更`password sync age`參數會決定密碼最長存留期的變更要求和，可以使用命令列工具來控制**ssoconfig – syncAge**或 SSO 管理 MMC。  
  
## <a name="user-action"></a>使用者動作  
  
-   使用者不必採取任何動作。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)