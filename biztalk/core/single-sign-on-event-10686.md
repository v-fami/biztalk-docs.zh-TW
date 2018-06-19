---
title: 單一登入： 事件 10686 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3e71f2a-e51d-4736-b06a-117142d30dae
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600226ef7440b8be9d7927481170291b6c63faae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271022"
---
# <a name="single-sign-on-event-10686"></a>單一登入： 事件 10686
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10686|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_INFO_REPLAY_STARTED|  
|訊息文字|重新執行預存外部密碼 changes.%r<br /><br /> 重新執行檔案： %1|  
  
## <a name="explanation"></a>說明  
 這個資訊事件表示 SSO 已重新執行預存外部密碼變更檔案。 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。  
  
## <a name="user-action"></a>使用者動作  
  
-   使用者不必採取任何動作。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)