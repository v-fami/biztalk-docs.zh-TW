---
title: SQL 配接器用戶端的功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f638154b-0a09-4f89-9c52-2a62fafec7dc
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0d1df3a7d5c5748db4b0d3f365d80d84ff1f670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222710"
---
# <a name="features-for-sql-adapter-clients"></a><span data-ttu-id="10fd4-102">SQL 配接器用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="10fd4-102">Features for SQL adapter clients</span></span>
<span data-ttu-id="10fd4-103">除了所有的主題所討論的功能[概觀的 BizTalk 配接器適用於 SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)、[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]也提供可用於配接器用戶端的下列功能：</span><span class="sxs-lookup"><span data-stu-id="10fd4-103">In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md), the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] also provides the following features that are useful for adapter clients:</span></span>  
  
-   <span data-ttu-id="10fd4-104">**設定配接器使用的繫結屬性的支援**。</span><span class="sxs-lookup"><span data-stu-id="10fd4-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="10fd4-105">可以設定配接器用戶端[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]藉由指定特定繫結內容。</span><span class="sxs-lookup"><span data-stu-id="10fd4-105">Adapter clients can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="10fd4-106">例如，用戶端可以指定連接集區中允許的特定連接字串的設定連線的數目上限**MaxConnectionPoolSize**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="10fd4-106">For example, clients can specify the maximum number of connections allowed in a connection pool for a specific connection string by setting the **MaxConnectionPoolSize** binding property.</span></span> <span data-ttu-id="10fd4-107">如需詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="10fd4-107">For more information, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
-   <span data-ttu-id="10fd4-108">**作業參數的 null 值支援**。</span><span class="sxs-lookup"><span data-stu-id="10fd4-108">**Support for null values for operation parameters**.</span></span> <span data-ttu-id="10fd4-109">配接器用戶端可以使用 XSD 的"nillable"屬性的作業參數提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="10fd4-109">Adapter clients can provide null values for operation parameters using the XSD "nillable" attribute.</span></span>  
  
-   <span data-ttu-id="10fd4-110">**支援動態連接埠，在 BizTalk**。</span><span class="sxs-lookup"><span data-stu-id="10fd4-110">**Support for dynamic ports in BizTalk**.</span></span> <span data-ttu-id="10fd4-111">透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="10fd4-111">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="10fd4-112">如需詳細資訊，請參閱[設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="10fd4-112">For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md).</span></span>  
  
-   <span data-ttu-id="10fd4-113">**對效能計數器支援**。</span><span class="sxs-lookup"><span data-stu-id="10fd4-113">**Support for performance counters**.</span></span> <span data-ttu-id="10fd4-114">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="10fd4-114">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports WCF-based performance counters for use by adapter clients.</span></span> <span data-ttu-id="10fd4-115">如需有關效能計數器的詳細資訊，請參閱[使用 SQL 配接器的效能計數器](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="10fd4-115">For more information about performance counters, see [Use Performance Counters with the SQL adapter](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10fd4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10fd4-116">See Also</span></span>  
 [<span data-ttu-id="10fd4-117">BizTalk Adapter for SQL Server 的概觀</span><span class="sxs-lookup"><span data-stu-id="10fd4-117">Overview of BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)