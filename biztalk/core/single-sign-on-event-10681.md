---
title: 單一登入： 事件 10681 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87ce2e50-cf54-4b23-b247-f137ce64ba1d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd0f1b6c27f3e77220d4615da1c0b5bb343344de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22272038"
---
# <a name="single-sign-on-event-10681"></a>單一登入： 事件 10681
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10681|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE|  
|訊息文字|外部密碼變更。 未變更 Windows 密碼，因為一或多個外部帳戶變更 failed.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶： %3|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示，Windows 密碼未變更，因為一個或多個外部帳戶變更失敗。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  
  
-   請檢查系統及應用程式事件記錄檔的相關聯的事件。  
  
-   請確認介面卡設定使用 SSO 管理工具。  
  
-   確認外部系統。  
  
## <a name="more-info"></a>其他資訊
  
-   [密碼同步處理](../core/password-synchronization2.md)  
  
-   **密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]