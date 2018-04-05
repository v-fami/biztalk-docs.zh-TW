---
title: SAP 配接器在 SAPClientFactory 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPClientFactory, supported methods and classes
ms.assetid: e64de5e4-e53f-4708-ab02-9e12774e94cd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c82e4bea6a16085608ebf1f8fe10ea95b4db394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapclientfactory-class-in-the-sap-adapter"></a><span data-ttu-id="5f261-102">SAP 配接器在 SAPClientFactory 類別</span><span class="sxs-lookup"><span data-stu-id="5f261-102">SAPClientFactory class in the SAP adapter</span></span>
<span data-ttu-id="5f261-103">下節列出方法和屬性的**SAPClientFactory**類別。</span><span class="sxs-lookup"><span data-stu-id="5f261-103">The following section lists the methods and properties for the **SAPClientFactory** class.</span></span> <span data-ttu-id="5f261-104">這衍生自**System.Data.Common.DbProviderFactory**。</span><span class="sxs-lookup"><span data-stu-id="5f261-104">This is derived from **System.Data.Common.DbProviderFactory**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="5f261-105">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="5f261-105">Supported Properties</span></span>  
  
|<span data-ttu-id="5f261-106">名稱</span><span class="sxs-lookup"><span data-stu-id="5f261-106">Name</span></span>|<span data-ttu-id="5f261-107">Get/Set</span><span class="sxs-lookup"><span data-stu-id="5f261-107">Get/Set</span></span>|<span data-ttu-id="5f261-108">Description</span><span class="sxs-lookup"><span data-stu-id="5f261-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="5f261-109">**執行個體**</span><span class="sxs-lookup"><span data-stu-id="5f261-109">**Instance**</span></span>|-|<span data-ttu-id="5f261-110">SAPClientFactory 單一執行個體</span><span class="sxs-lookup"><span data-stu-id="5f261-110">Singleton instance of SAPClientFactory</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="5f261-111">支援的方法</span><span class="sxs-lookup"><span data-stu-id="5f261-111">Supported Methods</span></span>  
  
|<span data-ttu-id="5f261-112">名稱</span><span class="sxs-lookup"><span data-stu-id="5f261-112">Name</span></span>|<span data-ttu-id="5f261-113">Description</span><span class="sxs-lookup"><span data-stu-id="5f261-113">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5f261-114">**CreateCommand()**</span><span class="sxs-lookup"><span data-stu-id="5f261-114">**CreateCommand()**</span></span>|<span data-ttu-id="5f261-115">建立 SAPCommand 的執行個體</span><span class="sxs-lookup"><span data-stu-id="5f261-115">Creates an instance of SAPCommand</span></span>|  
|<span data-ttu-id="5f261-116">**CreateConnection()**</span><span class="sxs-lookup"><span data-stu-id="5f261-116">**CreateConnection()**</span></span>|<span data-ttu-id="5f261-117">建立 SAPConnection 的執行個體</span><span class="sxs-lookup"><span data-stu-id="5f261-117">Creates an instance of SAPConnection</span></span>|  
|<span data-ttu-id="5f261-118">**CreateConnectionStringBuilder()**</span><span class="sxs-lookup"><span data-stu-id="5f261-118">**CreateConnectionStringBuilder()**</span></span>|<span data-ttu-id="5f261-119">建立 SAPConnectionStringBuilder 的執行個體</span><span class="sxs-lookup"><span data-stu-id="5f261-119">Creates an instance of SAPConnectionStringBuilder</span></span>|  
|<span data-ttu-id="5f261-120">**Createparameter （)**</span><span class="sxs-lookup"><span data-stu-id="5f261-120">**CreateParameter()**</span></span>|<span data-ttu-id="5f261-121">建立 SAPParameter 的執行個體</span><span class="sxs-lookup"><span data-stu-id="5f261-121">Creates an instance of SAPParameter</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f261-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f261-122">See Also</span></span>  
 [<span data-ttu-id="5f261-123">SAP 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="5f261-123">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)