---
title: Oracle EBS 配接器用戶端功能 |Microsoft 文件
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
ms.openlocfilehash: 2da086390fe049a5333dda40a35e19f46298dda1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217254"
---
# <a name="features-for-oracle-ebs-adapter-clients"></a><span data-ttu-id="d5b82-102">Oracle EBS 配接器用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="d5b82-102">Features for Oracle EBS adapter clients</span></span>
<span data-ttu-id="d5b82-103">除了所有的主題所討論的功能[概觀的 BizTalk 配接器 for Oracle E-business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e)、[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]也提供可用於配接器用戶端的下列功能：</span><span class="sxs-lookup"><span data-stu-id="d5b82-103">In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for Oracle E-Business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e), the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] also provides the following features that are useful for adapter clients:</span></span>  
  
-   <span data-ttu-id="d5b82-104">**設定配接器使用的繫結屬性的支援**。</span><span class="sxs-lookup"><span data-stu-id="d5b82-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="d5b82-105">可以設定配接器用戶端[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]藉由指定特定繫結內容。</span><span class="sxs-lookup"><span data-stu-id="d5b82-105">Adapter clients can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="d5b82-106">例如，用戶端可以設定配接器使用 ODP.NET 連接集區設定**UseOracleConnectionPool**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d5b82-106">For example, clients can configure the adapter to use the ODP.NET connection pool by setting the **UseOracleConnectionPool** binding property.</span></span> <span data-ttu-id="d5b82-107">如需詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d5b82-107">For more information, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
-   <span data-ttu-id="d5b82-108">**作業參數的 null 值支援**。</span><span class="sxs-lookup"><span data-stu-id="d5b82-108">**Support for null values for operation parameters**.</span></span> <span data-ttu-id="d5b82-109">配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。</span><span class="sxs-lookup"><span data-stu-id="d5b82-109">Adapter clients can provide null values for operation parameters using the “nil” attribute in the input XML.</span></span>  
  
-   <span data-ttu-id="d5b82-110">**支援動態連接埠，在 BizTalk**。</span><span class="sxs-lookup"><span data-stu-id="d5b82-110">**Support for dynamic ports in BizTalk**.</span></span> <span data-ttu-id="d5b82-111">透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="d5b82-111">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="d5b82-112">如需詳細資訊，請參閱[SQL 配接器中的 設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d5b82-112">For more information, see [Configure Dynamic Ports in the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b82-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5b82-113">See Also</span></span>  
[<span data-ttu-id="d5b82-114">瞭解 BizTalk Adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="d5b82-114">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)