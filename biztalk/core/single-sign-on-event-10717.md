---
title: "單一登入： 事件 10717 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14691e0f-a399-4b4d-9dd5-516bf8d3a167
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70195251b599daebd50b57f0b137dd026dd032e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10717"></a>單一登入： 事件 10717
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10717|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_NEW_REPLAY_DIR_FAILED|  
|訊息文字|無法建立重新執行檔案 directory.%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> 重新執行檔案目錄: %2 %r<br /><br /> 錯誤碼： %3|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示無法建立重新執行檔案目錄。  
  
 當 SSO 服務，從密碼同步配接器接收密碼變更時，它們會儲存在 SSO 資料庫。 如果 SSO 資料庫暫時無法使用時，密碼變更會在本機儲存在重新執行檔案。 重新執行檔案會儲存在重新執行檔案目錄。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   重新執行檔案目錄，如果一個核取不存在，嘗試建立它以手動方式為 SSO 服務使用相同的服務帳戶。 如果您無法建立重新執行檔案目錄使用相同的帳戶做為 SSO 服務，請檢查該帳戶的權限。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)