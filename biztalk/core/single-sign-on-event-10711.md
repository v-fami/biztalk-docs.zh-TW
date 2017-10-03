---
title: "單一登入： 事件 10711 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40722fe1-4be9-40d3-b5c5-a740a4b59f45
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6c6bb3f85d45edd971a38b7e7fa4c1df3efb3cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10711"></a>單一登入： 事件 10711
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10711|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PS_MISSING_INITIAL_CREDS|  
|訊息文字|外部密碼變更。 這種對應的部分遺失外部認證欄位已設為預設值。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶： %4|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示已收到外部密碼變更但是有認證遺失。 在這些欄位中使用預設值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   如有必要，設定要比對的認證。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)