---
title: 連接到 SQL Server 使用配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 727d73e6-fb84-48ce-ae72-5de70dcae8b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9b837aa4e0bc0a815434307b10d249dccf54d70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222134"
---
# <a name="connect-to-sql-server-using-the-adapter"></a>連接到 SQL Server 使用配接器
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]需要配接器用戶端提供的連接字串，呼叫統一資源識別元 (URI)，連接到 SQL Server 資料庫的連接。 就內部而言，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]對應連接到 SQL Server 資料庫的資料庫連接字串的 URI。 使用 連線 URI，配接器用戶端可以指定連線參數，以連接到外部系統。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
 在 連線 URI，您也可以指定容錯移轉 SQL Server 資料庫的名稱如果無法使用主要 SQL Server 資料庫，連接到待命電腦上。 容錯移轉 SQL Server 資料庫必須是主要的 SQL Server 資料庫的鏡像。 使用中的選擇性參數，FailoverPartner，連線 URI，指定容錯移轉 SQL Server 資料庫。 提供容錯移轉 SQL Server 資料庫，可確保高可用性與資料冗餘。 如需高可用性 SQL Server 」 方面的詳細資訊，請參閱[中 SQL Server 資料庫鏡像](https://msdn.microsoft.com/library/5h52hef8.aspx)。
  
 請確定您遵循安全性指導方針建立與 SQL Server 資料庫的連接時。 如需安全性指導方針的詳細資訊，請參閱[安全 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for SQL Server 的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [建立 SQL Server 的連接](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)