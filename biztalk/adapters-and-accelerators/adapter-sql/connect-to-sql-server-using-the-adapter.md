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
# <a name="connect-to-sql-server-using-the-adapter"></a><span data-ttu-id="ab291-102">連接到 SQL Server 使用配接器</span><span class="sxs-lookup"><span data-stu-id="ab291-102">Connect to SQL Server using the adapter</span></span>
<span data-ttu-id="ab291-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]需要配接器用戶端提供的連接字串，呼叫統一資源識別元 (URI)，連接到 SQL Server 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="ab291-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI), to connect to the SQL Server database.</span></span> <span data-ttu-id="ab291-104">就內部而言，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]對應連接到 SQL Server 資料庫的資料庫連接字串的 URI。</span><span class="sxs-lookup"><span data-stu-id="ab291-104">Internally, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] maps the URI to a database connection string to connect to the SQL Server database.</span></span> <span data-ttu-id="ab291-105">使用 連線 URI，配接器用戶端可以指定連線參數，以連接到外部系統。</span><span class="sxs-lookup"><span data-stu-id="ab291-105">With a connection URI, adapter clients can specify connection parameters to connect to an external system.</span></span> <span data-ttu-id="ab291-106">如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="ab291-106">For more information about the connection URI, see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
 <span data-ttu-id="ab291-107">在 連線 URI，您也可以指定容錯移轉 SQL Server 資料庫的名稱如果無法使用主要 SQL Server 資料庫，連接到待命電腦上。</span><span class="sxs-lookup"><span data-stu-id="ab291-107">In the connection URI, you can also specify the name of a failover SQL Server database on a standby computer to connect to if the primary SQL Server database is not available.</span></span> <span data-ttu-id="ab291-108">容錯移轉 SQL Server 資料庫必須是主要的 SQL Server 資料庫的鏡像。</span><span class="sxs-lookup"><span data-stu-id="ab291-108">The failover SQL Server database must be a mirror of the primary SQL Server database.</span></span> <span data-ttu-id="ab291-109">使用中的選擇性參數，FailoverPartner，連線 URI，指定容錯移轉 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab291-109">The failover SQL Server database is specified using an optional parameter, FailoverPartner, in the connection URI.</span></span> <span data-ttu-id="ab291-110">提供容錯移轉 SQL Server 資料庫，可確保高可用性與資料冗餘。</span><span class="sxs-lookup"><span data-stu-id="ab291-110">Providing a failover SQL Server database ensures high availability and data redundancy.</span></span> <span data-ttu-id="ab291-111">如需高可用性 SQL Server 」 方面的詳細資訊，請參閱[中 SQL Server 資料庫鏡像](https://msdn.microsoft.com/library/5h52hef8.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ab291-111">For more information about high availability with respect to SQL Server, see [Database Mirroring in SQL Server](https://msdn.microsoft.com/library/5h52hef8.aspx).</span></span>
  
 <span data-ttu-id="ab291-112">請確定您遵循安全性指導方針建立與 SQL Server 資料庫的連接時。</span><span class="sxs-lookup"><span data-stu-id="ab291-112">Make sure you comply with the security guidelines when establishing a connection with the SQL Server database.</span></span> <span data-ttu-id="ab291-113">如需安全性指導方針的詳細資訊，請參閱[安全 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ab291-113">For more information about security guidelines, see [Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab291-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab291-114">See Also</span></span>  
 <span data-ttu-id="ab291-115">[BizTalk Adapter for SQL Server 的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab291-115">[Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md) </span></span>  
 [<span data-ttu-id="ab291-116">建立 SQL Server 的連接</span><span class="sxs-lookup"><span data-stu-id="ab291-116">Create a Connection to SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)