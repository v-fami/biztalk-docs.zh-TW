---
title: "單一登入： 事件 10661 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3418f37-770d-4021-9341-5dbe99689da6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fdc655a87975a89387d84e2aefdd07a603c0ed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10661"></a>單一登入： 事件 10661
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10661|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_PASSWORD_SYNC_WINDOWS_START_FAILED|  
|訊息文字|Windows （來自 PCNS) 的密碼同步無法 start.%r<br /><br /> 錯誤碼： %1|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示 Windows 的密碼同步無法啟動。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   檢查應用程式與系統事件記錄檔相關聯的事件。  
  
-   請確認配接器組態屬性。  
  
## <a name="more-info"></a>其他資訊
  
-   [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)  
  
-   **企業單一登入 UI 說明**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]