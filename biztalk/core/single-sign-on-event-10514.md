---
title: "單一登入： 事件 10514 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b527841-a2e2-44c7-a9cb-6e9a8eea2fba
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40077ead4157b4cc6c91a2c44b4a19569d76ebc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10514"></a>單一登入： 事件 10514
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10514|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_DB_ACCESS|  
|訊息文字|嘗試存取 SSO database.%r 時發生錯誤<br /><br /> 函式: %1 %r<br /><br /> 檔案: %2 %r<br /><br /> %3.%r<br /><br /> SQL 錯誤碼: %4 %r<br /><br /> 錯誤碼： %5|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示當您嘗試存取 SSO 資料庫時，已從 SQL Server 收到錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   確認 SQL Server (MSSQLSERVER) 服務正在執行。  
  
-   檢查 SQL Server 錯誤程式碼使用事件和錯誤訊息中心在[http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869)。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)  
  
-   [如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)  
  
 另請參閱 SQL Server 線上叢書。