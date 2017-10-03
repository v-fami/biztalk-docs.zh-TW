---
title: "單一登入： 事件 10735 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c791c6-1901-4441-b329-ed75833cb83e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94417860296cf01c2266a678832f8b02b9b51055
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10735"></a>單一登入： 事件 10735
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10735|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PS_APP_DISABLED|  
|訊息文字|外部密碼變更。 因為應用程式 disabled.%r 密碼未變更外部帳戶<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶： %4|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示，密碼未變更外部帳戶因為應用程式已停用。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   啟用分支機構應用程式  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)