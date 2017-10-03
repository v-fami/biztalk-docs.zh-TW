---
title: "單一登入： 事件 11019 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec07b00-d567-4518-89eb-340e4f92429b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4b2d2494a404566c7350a9e9988d429a3e335c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11019"></a>單一登入： 事件 11019
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11019|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED|  
|訊息文字|對應無效，因為 Windows 帳戶不是應用程式的應用程式使用者帳戶。 無法刪除對應。 將 ignored.%r 對應。<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 應用程式使用者: %4 %r<br /><br /> 錯誤碼： %5|  
  
## <a name="explanation"></a>說明  
 請指定的 Windows 帳戶向來是不屬於此應用程式的應用程式使用者帳戶，或它是一次，但已變更或移除。 尚未刪除對應。  
  
## <a name="user-action"></a>使用者動作  
 請檢查您的系統密碼同步處理帳戶資訊，請確定您的資訊有效。 然後重新建立對應。 請注意，使用 建立對應精靈可降低無效的對應資訊的風險。 您可以刪除失敗的對應。 如果您沒有刪除，將會忽略它。