---
title: Oracle EBS 配接器用戶端的功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50256fb7-5f0c-4b32-87e6-98f49da0b360
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 974f75eaa2416ae11572a1b29eb682d6bc7c0172
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968879"
---
# <a name="features-for-oracle-ebs-adapter-clients"></a><span data-ttu-id="b32b2-102">Oracle EBS 配接器用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="b32b2-102">Features for Oracle EBS adapter clients</span></span>
<span data-ttu-id="b32b2-103">除了的主題所討論的功能之外[概觀的 BizTalk 配接器 for Oracle E-business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e)，則[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]也提供適用於配接器用戶端的下列功能：</span><span class="sxs-lookup"><span data-stu-id="b32b2-103">In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for Oracle E-Business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e), the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] also provides the following features that are useful for adapter clients:</span></span>  
  
- <span data-ttu-id="b32b2-104">**設定使用繫結屬性的配接器支援**。</span><span class="sxs-lookup"><span data-stu-id="b32b2-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="b32b2-105">配接器用戶端可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]藉由指定特定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b32b2-105">Adapter clients can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="b32b2-106">比方說，用戶端可以在其中設定配接器使用 ODP.NET 連接集區，只要**UseOracleConnectionPool**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b32b2-106">For example, clients can configure the adapter to use the ODP.NET connection pool by setting the **UseOracleConnectionPool** binding property.</span></span> <span data-ttu-id="b32b2-107">如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b32b2-107">For more information, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
- <span data-ttu-id="b32b2-108">**作業參數的 null 值支援**。</span><span class="sxs-lookup"><span data-stu-id="b32b2-108">**Support for null values for operation parameters**.</span></span> <span data-ttu-id="b32b2-109">配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。</span><span class="sxs-lookup"><span data-stu-id="b32b2-109">Adapter clients can provide null values for operation parameters using the “nil” attribute in the input XML.</span></span>  
  
- <span data-ttu-id="b32b2-110">**支援在 BizTalk 中的動態連接埠**。</span><span class="sxs-lookup"><span data-stu-id="b32b2-110">**Support for dynamic ports in BizTalk**.</span></span> <span data-ttu-id="b32b2-111">透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，則[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b32b2-111">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="b32b2-112">如需詳細資訊，請參閱 < [SQL 配接器中的 設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b32b2-112">For more information, see [Configure Dynamic Ports in the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b32b2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b32b2-113">See Also</span></span>  
[<span data-ttu-id="b32b2-114">了解 BizTalk Adapter for Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="b32b2-114">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)