---
title: "單一登入： 事件 11023 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feeb4ede-6045-46bf-9f2b-65062c583faa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd65ac5cab5b49f43e0c3649cf205f7f6dc2ceaf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11023"></a>單一登入： 事件 11023
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11023|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_WINDOWS_PASSWORD_DELETED|  
|訊息文字|若要防止帳戶 lockout.%r 刪除 SSO 資料庫中的無效 Windows 密碼<br /><br /> 若要設定此 Windows account.%r 的外部認證使用 SSO 管理工具<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶： %3|  
  
## <a name="explanation"></a>說明  
 已刪除的無效 Windows 密碼。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用 SSO 管理工具來設定此 Windows 帳戶的外部認證。 如需詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。