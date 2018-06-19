---
title: 單一登入： 事件 11017 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a4f7264-18aa-4eca-97c9-d5fd7e90e2cc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25ef3f3be84e775fe522b508f7726f3e4e88870b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276774"
---
# <a name="single-sign-on-event-11017"></a>單一登入： 事件 11017
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11017|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK|  
|訊息文字|對應無效，因為 Windows 帳戶不是應用程式的應用程式使用者帳戶。 對應已 deleted.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 應用程式使用者： %4|  
  
## <a name="explanation"></a>說明  
 請指定的 Windows 帳戶向來是不屬於此應用程式的應用程式使用者帳戶，或它是一次，但已變更或移除。 對應已被刪除。  
  
## <a name="user-action"></a>使用者動作  
 請檢查您的系統密碼同步處理帳戶資訊，請確定您的資訊有效。 然後重新建立對應。 請注意，使用 建立對應精靈可降低無效的對應資訊的風險。