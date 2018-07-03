---
title: 單一登入： 事件 10514 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b527841-a2e2-44c7-a9cb-6e9a8eea2fba
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fff4fbbb9b5c4d32968312b0f585ffbf2f5bb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995303"
---
# <a name="single-sign-on-event-10514"></a>單一登入： 事件 10514
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                    企業單一登入                                                                                     |
| 產品版本 |                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                    |
|    事件識別碼     |                                                                                              10514                                                                                               |
|  事件來源   |                                                                                              ENTSSO                                                                                              |
|    元件    |                                                                                               N\A                                                                                                |
|  符號名稱  |                                                                                       SSO_ERROR_DB_ACCESS                                                                                        |
|  訊息文字   | 嘗試存取 SSO database.%r 時發生錯誤<br /><br /> 函式: %1 %r<br /><br /> 檔案: %2 %r<br /><br /> %3.%r<br /><br /> SQL 錯誤碼: %4 %r<br /><br /> 錯誤碼： %5 |
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示當您嘗試存取 SSO 資料庫時，已從 SQL Server 收到錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
- 確認 SQL Server (MSSQLSERVER) 服務正在執行。  
  
- 請檢查使用的事件和錯誤訊息中心，在 SQL Server 錯誤碼[ http://go.microsoft.com/fwlink/?LinkID=20869 ](http://go.microsoft.com/fwlink/?LinkID=20869)。  
  
  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
- [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)  
  
- [如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)  
  
  另請參閱 SQL Server 線上叢書。