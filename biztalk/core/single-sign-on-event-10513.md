---
title: 單一登入： 事件 10513 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3306223-111f-4abf-ae65-be839b355216
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c61b1b861cb14ec0d16dce27fd26360df7fcdc98
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981623"
---
# <a name="single-sign-on-event-10513"></a>單一登入： 事件 10513
## <a name="details"></a>詳細資料  

|                 |                                                                                      |
|-----------------|--------------------------------------------------------------------------------------|
|  產品名稱   |                              企業單一登入                               |
| 產品版本 |              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]              |
|    事件識別碼     |                                        10513                                         |
|  事件來源   |                                        ENTSSO                                        |
|    元件    |                                         N\A                                          |
|  符號名稱  |                              SSO_ERROR_DB_FIRST_ACCESS                               |
|  訊息文字   | 無法連絡 SSO 資料庫: %1 %r<br /><br /> %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 服務無法在啟動時連絡 SSO 資料庫。 事件訊息包含資料來源名稱 (DSN) 字串，指出指定的 SQL Server 和資料庫名稱，以及 SQL 連接程式庫傳回的錯誤訊息。  

 SSO 服務啟動時，它會嘗試連接到 SSO 資料庫，使用登錄中指定的 SQL Server 與 SSO 資料庫名稱。 SSO 服務會嘗試連線 12 倍，等待 5 秒，每次失敗嘗試，共 1 分鐘之間。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 確認 SQL Server (MSSQLSERVER) 服務正在執行。  

- 確認錯誤訊息中指出的資料來源名稱 (DSN) 字串正確無誤，而且包含正確的 SQL Server 和資料庫名稱。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)  

- [如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)  

- [設定 SSO](../core/configuring-sso.md)  

- SQL Server 線上叢書
