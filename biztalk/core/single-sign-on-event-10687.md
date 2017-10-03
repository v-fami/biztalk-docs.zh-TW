---
title: "單一登入： 事件 10687 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b3fe2c-a7ba-47e1-a753-4eaa64b01a60
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 368e9bbad42e49ebd71bc1a581b0fb18bbcc2d5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10687"></a>單一登入： 事件 10687
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10687|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_INFO_REPLAY_COMPLETE|  
|訊息文字|重新執行預存外部密碼變更已完成。%r<br /><br /> 重新執行檔案: %1 %r<br /><br /> 其他資料： %2|  
  
## <a name="explanation"></a>說明  
 這個資訊事件表示 SSO 已完成重新執行預存外部密碼變更檔案。 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。  
  
## <a name="user-action"></a>使用者動作  
  
-   使用者不必採取任何動作。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)