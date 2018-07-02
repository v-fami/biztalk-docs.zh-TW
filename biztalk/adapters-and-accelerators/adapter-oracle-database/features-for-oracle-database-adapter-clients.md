---
title: Oracle 資料庫配接器用戶端的功能 |Microsoft Docs
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
ms.openlocfilehash: ce283c3fd63f72d67e31806e86bf9caa08555dd9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976175"
---
# <a name="features-for-oracle-database-adapter-clients"></a><span data-ttu-id="0748c-102">Oracle 資料庫配接器用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="0748c-102">Features for Oracle Database adapter clients</span></span>
<span data-ttu-id="0748c-103">除了的主題所討論的功能之外[概觀的 BizTalk 配接器用於 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也提供適用於配接器用戶端的下列功能：</span><span class="sxs-lookup"><span data-stu-id="0748c-103">In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md), the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also provides the following features that are useful for adapter clients:</span></span>  
  
- <span data-ttu-id="0748c-104">**設定使用繫結屬性的配接器支援**。</span><span class="sxs-lookup"><span data-stu-id="0748c-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="0748c-105">配接器用戶端可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由指定特定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="0748c-105">Adapter clients can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="0748c-106">比方說，用戶端可以在其中設定配接器使用 ODP.NET 連接集區，只要**UseOracleConnectionPool**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="0748c-106">For example, clients can configure the adapter to use the ODP.NET connection pool by setting the **UseOracleConnectionPool** binding property.</span></span> <span data-ttu-id="0748c-107">如需詳細資訊，請參閱 < [Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="0748c-107">For more information, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
- <span data-ttu-id="0748c-108">**作業參數的 null 值支援**。</span><span class="sxs-lookup"><span data-stu-id="0748c-108">**Support for null values for operation parameters**.</span></span> <span data-ttu-id="0748c-109">配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。</span><span class="sxs-lookup"><span data-stu-id="0748c-109">Adapter clients can provide null values for operation parameters using the “nil” attribute in the input XML.</span></span>  
  
- <span data-ttu-id="0748c-110">**支援在 BizTalk 中的動態連接埠**。</span><span class="sxs-lookup"><span data-stu-id="0748c-110">**Support for dynamic ports in BizTalk**.</span></span> <span data-ttu-id="0748c-111">透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="0748c-111">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="0748c-112">如需詳細資訊，請參閱 <<c0> [ 設定動態連接埠](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0748c-112">For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md).</span></span>  
  
- <span data-ttu-id="0748c-113">**對效能計數器支援**。</span><span class="sxs-lookup"><span data-stu-id="0748c-113">**Support for performance counters**.</span></span> <span data-ttu-id="0748c-114">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援配接器用戶端使用 wcf 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0748c-114">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports WCF-based performance counters for use by adapter clients.</span></span> <span data-ttu-id="0748c-115">如需有關效能計數器的詳細資訊，請參閱 <<c0> [ 效能計數器](../../core/performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="0748c-115">For more information about performance counters, see [Performance Counters](../../core/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0748c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0748c-116">See Also</span></span>  
 [<span data-ttu-id="0748c-117">BizTalk Adapter for Oracle Database 概觀</span><span class="sxs-lookup"><span data-stu-id="0748c-117">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)