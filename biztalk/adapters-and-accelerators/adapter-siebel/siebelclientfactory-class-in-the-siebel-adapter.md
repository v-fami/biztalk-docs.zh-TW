---
title: Siebel 配接器中的 SiebelClientFactory 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SiebelClientFactory
- Data Provider for Siebel, SiebelClientFactory
- SiebelClientFactory, supported properties and methods
ms.assetid: f3a807d3-a030-47d8-b145-e18075ec353c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50e47b22c1d5a2575b0da3fae432acd79886e2c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222062"
---
# <a name="siebelclientfactory-class-in-the-siebel-adapter"></a><span data-ttu-id="9f513-102">Siebel 配接器中 SiebelClientFactory 類別</span><span class="sxs-lookup"><span data-stu-id="9f513-102">SiebelClientFactory class in the Siebel adapter</span></span>
<span data-ttu-id="9f513-103">ADO.NET 用戶端會存取[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用泛型的 ADO.NET 類別和介面。</span><span class="sxs-lookup"><span data-stu-id="9f513-103">An ADO.NET client accesses the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] using generic ADO.NET classes and interfaces.</span></span> <span data-ttu-id="9f513-104">若要啟用這項功能，[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]繼承**System.Data.Common.DbProviderFactory**類別。</span><span class="sxs-lookup"><span data-stu-id="9f513-104">To enable this feature, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] inherits the **System.Data.Common.DbProviderFactory** class.</span></span> <span data-ttu-id="9f513-105">用戶端，也會耗用用戶端，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9f513-105">The client program consumes the client as follows:</span></span>  
  
```  
  
DbProviderFactory factory = DbProviderFactories.GetFactory("Microsoft.Data.SiebelClient");  
DbConnection connection = factory.CreateConnection();  
```  
  
 <span data-ttu-id="9f513-106">另一個方法是，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9f513-106">An alternative approach is as follows:</span></span>  
  
```  
SiebelClientFactory factory = SiebelClientFactory.Instance;  
DbConnection connection = factory.CreateConnection();  
```  
  
 <span data-ttu-id="9f513-107">SiebelClientFactory 存在 Microsoft.Data.SiebelClient 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="9f513-107">SiebelClientFactory exists in the namespace Microsoft.Data.SiebelClient.</span></span>  
  
## <a name="supported-members"></a><span data-ttu-id="9f513-108">支援的成員</span><span class="sxs-lookup"><span data-stu-id="9f513-108">Supported Members</span></span>  
 <span data-ttu-id="9f513-109">**SiebelClientFactory**擴充**System.Data.CommonDbProviderFactory**。</span><span class="sxs-lookup"><span data-stu-id="9f513-109">**SiebelClientFactory** extends **System.Data.CommonDbProviderFactory**.</span></span>  <span data-ttu-id="9f513-110">下表提供之成員的說明， **SiebelClientFactory**會覆寫。</span><span class="sxs-lookup"><span data-stu-id="9f513-110">The following table provides a description of the members that **SiebelClientFactory** overrides.</span></span>  
  
|<span data-ttu-id="9f513-111">名稱</span><span class="sxs-lookup"><span data-stu-id="9f513-111">Name</span></span>|<span data-ttu-id="9f513-112">Description</span><span class="sxs-lookup"><span data-stu-id="9f513-112">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9f513-113">**執行個體**</span><span class="sxs-lookup"><span data-stu-id="9f513-113">**Instance**</span></span>|<span data-ttu-id="9f513-114">這是成員變數。</span><span class="sxs-lookup"><span data-stu-id="9f513-114">This is a member variable.</span></span>  <span data-ttu-id="9f513-115">它提供 SiebelClientFactory 的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f513-115">It provides a singleton instance of SiebelClientFactory.</span></span>|  
|<span data-ttu-id="9f513-116">**CreateCommand()**</span><span class="sxs-lookup"><span data-stu-id="9f513-116">**CreateCommand()**</span></span>|<span data-ttu-id="9f513-117">建立 SiebelCommand 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f513-117">Creates an instance of SiebelCommand.</span></span>|  
|<span data-ttu-id="9f513-118">**CreateConnection()**</span><span class="sxs-lookup"><span data-stu-id="9f513-118">**CreateConnection()**</span></span>|<span data-ttu-id="9f513-119">建立 SiebelConnection 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f513-119">Creates an instance of SiebelConnection.</span></span>|  
|<span data-ttu-id="9f513-120">**CreateConnectionStringBuilder()**</span><span class="sxs-lookup"><span data-stu-id="9f513-120">**CreateConnectionStringBuilder()**</span></span>|<span data-ttu-id="9f513-121">建立 SiebelConnectionStringBuilder 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f513-121">Creates an instance of SiebelConnectionStringBuilder.</span></span>|  
|<span data-ttu-id="9f513-122">**Createparameter （)**</span><span class="sxs-lookup"><span data-stu-id="9f513-122">**CreateParameter()**</span></span>|<span data-ttu-id="9f513-123">建立 SiebelParameter 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f513-123">Creates an instance of SiebelParameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f513-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f513-124">See Also</span></span>  
 [<span data-ttu-id="9f513-125">Siebel 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="9f513-125">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)