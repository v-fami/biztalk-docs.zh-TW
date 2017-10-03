---
title: "單一登入： 事件 10714 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59d8509f-cc3e-40fa-ba3d-3dcb0e73c67a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba63ab9197dcf9629f03f3d6c96f064345aaa46e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10714"></a>單一登入： 事件 10714
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10714|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED|  
|訊息文字|重試已過期，捨棄通知。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器： %2|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示密碼同步通知重試已過期，已捨棄通知。  
  
 密碼變更 (從 Windows 到外部系統) 傳送到密碼同步配接器時，密碼同步配接器會通知已成功處理密碼變更。 如果密碼變更未在指定的時間內發生，或者如果變更期間發生其他問題，則密碼變更會再次傳送到密碼同步配接器。 這是有限的時間 （最大重試次數） 和密碼變更通知則會捨棄。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   檢查關聯事件的系統和應用程式事件記錄檔。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)