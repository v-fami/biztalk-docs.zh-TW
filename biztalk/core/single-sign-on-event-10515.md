---
title: 單一登入： 事件 10515 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41edc008-b6d3-401d-97af-80b36ab0ba55
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1c3d7498bcd6a045936103d682d3643761a182c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980815"
---
# <a name="single-sign-on-event-10515"></a>單一登入： 事件 10515
## <a name="details"></a>詳細資料  
  
|                 |                                                                               |
|-----------------|-------------------------------------------------------------------------------|
|  產品名稱   |                           企業單一登入                           |
| 產品版本 |          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]           |
|    事件識別碼     |                                     10515                                     |
|  事件來源   |                                    ENTSSO                                     |
|    元件    |                                      N\A                                      |
|  符號名稱  |                            SSO_ERROR_POLL_DATABASE                            |
|  訊息文字   | 失去與 SSO 資料庫的連絡。 請檢查 SSO 資料庫是否可用。 |
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 服務已失去與 SSO 資料庫的聯繫。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
- 確認 SQL Server (MSSQLSERVER) 服務正在執行。  
  
- 請確認網路連線到 SQL Server 的遠端伺服器上。  
  
  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
- [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)  
  
- [如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)  
  
- [設定 SSO](../core/configuring-sso.md)  
  
  另請參閱 SQL Server 線上叢書