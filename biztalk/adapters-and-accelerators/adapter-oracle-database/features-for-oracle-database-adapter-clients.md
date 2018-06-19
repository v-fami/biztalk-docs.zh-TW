---
title: Oracle 資料庫配接器用戶端功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data streaming, support for
- binding properties
- adapter, features
- adapters, configuring
- message versioning, support for
- XML data streaming
- performance counters, support for
- dynamic ports in BizTalk, support for
- data streaming
ms.assetid: 63b52573-80a5-4206-95c3-478b86718fee
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b120c948ef3d9821af0a79e91fd718e3a1f33137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214318"
---
# <a name="features-for-oracle-database-adapter-clients"></a><span data-ttu-id="cb267-102">Oracle 資料庫配接器用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="cb267-102">Features for Oracle Database adapter clients</span></span>
<span data-ttu-id="cb267-103">除了所有的主題所討論的功能[概觀的 BizTalk 配接器的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也提供可用於配接器用戶端的下列功能：</span><span class="sxs-lookup"><span data-stu-id="cb267-103">In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md), the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also provides the following features that are useful for adapter clients:</span></span>  
  
-   <span data-ttu-id="cb267-104">**設定配接器使用的繫結屬性的支援**。</span><span class="sxs-lookup"><span data-stu-id="cb267-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="cb267-105">可以設定配接器用戶端[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由指定特定繫結內容。</span><span class="sxs-lookup"><span data-stu-id="cb267-105">Adapter clients can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="cb267-106">例如，用戶端可以設定配接器使用 ODP.NET 連接集區設定**UseOracleConnectionPool**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb267-106">For example, clients can configure the adapter to use the ODP.NET connection pool by setting the **UseOracleConnectionPool** binding property.</span></span> <span data-ttu-id="cb267-107">如需詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="cb267-107">For more information, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
-   <span data-ttu-id="cb267-108">**作業參數的 null 值支援**。</span><span class="sxs-lookup"><span data-stu-id="cb267-108">**Support for null values for operation parameters**.</span></span> <span data-ttu-id="cb267-109">配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。</span><span class="sxs-lookup"><span data-stu-id="cb267-109">Adapter clients can provide null values for operation parameters using the “nil” attribute in the input XML.</span></span>  
  
-   <span data-ttu-id="cb267-110">**支援動態連接埠，在 BizTalk**。</span><span class="sxs-lookup"><span data-stu-id="cb267-110">**Support for dynamic ports in BizTalk**.</span></span> <span data-ttu-id="cb267-111">透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cb267-111">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="cb267-112">如需詳細資訊，請參閱[設定動態連接埠](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cb267-112">For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md).</span></span>  
  
-   <span data-ttu-id="cb267-113">**對效能計數器支援**。</span><span class="sxs-lookup"><span data-stu-id="cb267-113">**Support for performance counters**.</span></span> <span data-ttu-id="cb267-114">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="cb267-114">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports WCF-based performance counters for use by adapter clients.</span></span> <span data-ttu-id="cb267-115">如需有關效能計數器的詳細資訊，請參閱[效能計數器](../../core/performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="cb267-115">For more information about performance counters, see [Performance Counters](../../core/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb267-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb267-116">See Also</span></span>  
 [<span data-ttu-id="cb267-117">BizTalk Adapter for Oracle 資料庫的概觀</span><span class="sxs-lookup"><span data-stu-id="cb267-117">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)