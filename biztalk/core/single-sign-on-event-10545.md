---
title: 單一登入： 事件 10545 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64cb10ceef5827f9c0b0aab5d9810db061af8a71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270646"
---
# <a name="single-sign-on-event-10545"></a>單一登入： 事件 10545
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10545|  
|事件來源|ENTSSO|  
|元件|CO|  
|符號名稱|SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED|  
|訊息文字|未啟用 SSO 系統的票證。|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示不 SSO 系統啟用票證。 如果在系統層級停用票證，票證無法使用分支機構應用程式層級是。 可以在系統層級中啟用票證，然後在分支機構應用程式層級中將它停用。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   在中啟用票證的 SSO 系統層級。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [SSO 票證](../core/sso-tickets.md)  
  
-   [如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)