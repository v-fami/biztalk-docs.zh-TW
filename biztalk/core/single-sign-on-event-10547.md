---
title: 單一登入： 事件 10547 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be25cdc9-d6c1-488d-9ead-877a2454c3d1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f6162461b1eb04993ca681049fe1fbb797ca014
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270718"
---
# <a name="single-sign-on-event-10547"></a>單一登入： 事件 10547
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10547|  
|事件來源|ENTSSO|  
|元件|CO|  
|符號名稱|SSO_WARN_UPDATE_FAILED|  
|訊息文字|無法重新加密期間，更新 SSO 資料庫中的認證|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示它是不可行的新加密結果更新的認證。 主要密碼已變更，正在產生新的密碼，或還原舊的密碼，是在解密以舊的密碼、 加密機密資料，並使用新密碼重新加密 SSO 資料庫上執行重新加密。 如果認證已刪除程序正在重新加密一樣，可能會發生此事件。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   等候另一個短暫的延遲; 之後發生的重新加密如果，不會自動發生，請重新啟動 SSO 服務，其會觸發新的重新加密，如果需要。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [瞭解 SSO](../core/understanding-sso.md)