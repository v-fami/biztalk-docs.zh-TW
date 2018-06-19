---
title: Siebel 配接器中的 SiebelConnection 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, SiebelConnection
- SiebelConnection, supported properties and methods
- SiebelConnection
ms.assetid: 661d9876-4c14-4748-b05f-cc4fd1c4ebcf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fc99c2e3f019f2ddf88647b0faeb7e41644fd0e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222334"
---
# <a name="siebelconnection-class-in-the-siebel-adapter"></a><span data-ttu-id="d2361-102">Siebel 配接器中 SiebelConnection 類別</span><span class="sxs-lookup"><span data-stu-id="d2361-102">SiebelConnection class in the Siebel adapter</span></span>
<span data-ttu-id="d2361-103">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]存取基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] `Binding`、 `ConnectionFactory`，和`Channel`連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="d2361-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] accesses the underlying [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]`Binding`, the `ConnectionFactory`, and `Channel` to connect to the Siebel system.</span></span> <span data-ttu-id="d2361-104">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]實作`DbConnection`類別，以支援上述功能。</span><span class="sxs-lookup"><span data-stu-id="d2361-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implements the `DbConnection` class to support the preceding features.</span></span>  
  
 <span data-ttu-id="d2361-105">使用的執行個體`Microsoft.Data.SiebelClient.SiebelClientFactory`，用戶端程式可以取得的執行個體`System.Data.Common.DbConnection`類別來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="d2361-105">Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbConnection` class to connect to the Siebel system.</span></span>  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbConnection connection = factory.CreateConnection();  
```  
  
 <span data-ttu-id="d2361-106">或者，可以使用下列的方法，來建立連接：</span><span class="sxs-lookup"><span data-stu-id="d2361-106">Alternatively, the following approach can be used to create a connection:</span></span>  
  
```  
  
SiebelConnection connection = new SiebelConnection();  
connection.ConnectionString = connectionString;  
```  
  
 <span data-ttu-id="d2361-107">`SiebelConnection`類別繼承自`DbConnection`。</span><span class="sxs-lookup"><span data-stu-id="d2361-107">The `SiebelConnection` class inherits from `DbConnection`.</span></span> <span data-ttu-id="d2361-108">命名空間中存在`Microsoft.Data.SiebelClient`。</span><span class="sxs-lookup"><span data-stu-id="d2361-108">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="d2361-109">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="d2361-109">Supported Properties</span></span>  
 <span data-ttu-id="d2361-110">`SiebelConnection`類別支援下列`DbConnection`屬性。</span><span class="sxs-lookup"><span data-stu-id="d2361-110">The `SiebelConnection` class supports the following `DbConnection` properties.</span></span>  
  
|<span data-ttu-id="d2361-111">名稱</span><span class="sxs-lookup"><span data-stu-id="d2361-111">Name</span></span>|<span data-ttu-id="d2361-112">Get/Set</span><span class="sxs-lookup"><span data-stu-id="d2361-112">Get/Set</span></span>|<span data-ttu-id="d2361-113">Description</span><span class="sxs-lookup"><span data-stu-id="d2361-113">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="d2361-114">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="d2361-114">**ConnectionString**</span></span>|<span data-ttu-id="d2361-115">取得和設定</span><span class="sxs-lookup"><span data-stu-id="d2361-115">Get and Set</span></span>|<span data-ttu-id="d2361-116">取得或設定用來開啟連接的字串。</span><span class="sxs-lookup"><span data-stu-id="d2361-116">Gets or sets the string used to open the connection.</span></span>|  
|<span data-ttu-id="d2361-117">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="d2361-117">**Database**</span></span>|<span data-ttu-id="d2361-118">Get</span><span class="sxs-lookup"><span data-stu-id="d2361-118">Get</span></span>|<span data-ttu-id="d2361-119">取得後開啟連接時，目前資料庫的名稱或之前開啟連接，連接字串中指定的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d2361-119">Gets the name of the current database after a connection is opened, or the database name specified in the connection string before the connection is opened.</span></span> <span data-ttu-id="d2361-120">這應該是 Siebel 儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="d2361-120">This should be the Siebel repository name.</span></span>|  
|<span data-ttu-id="d2361-121">**DataSource**</span><span class="sxs-lookup"><span data-stu-id="d2361-121">**DataSource**</span></span>|<span data-ttu-id="d2361-122">Get</span><span class="sxs-lookup"><span data-stu-id="d2361-122">Get</span></span>|<span data-ttu-id="d2361-123">取得此連接 Siebel 閘道的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2361-123">Gets the name of the Siebel gateway for this connection.</span></span>|  
|<span data-ttu-id="d2361-124">**ServerVersion**</span><span class="sxs-lookup"><span data-stu-id="d2361-124">**ServerVersion**</span></span>|<span data-ttu-id="d2361-125">Get</span><span class="sxs-lookup"><span data-stu-id="d2361-125">Get</span></span>|<span data-ttu-id="d2361-126">在目前版本中的[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，這個屬性會傳回硬式編碼的值，這不是實際的 Siebel 伺服器的版本。</span><span class="sxs-lookup"><span data-stu-id="d2361-126">In the current version of [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], this property returns a hard-coded value, which does not represent the actual version of the Siebel server.</span></span>|  
|<span data-ttu-id="d2361-127">**State**</span><span class="sxs-lookup"><span data-stu-id="d2361-127">**State**</span></span>|<span data-ttu-id="d2361-128">Get</span><span class="sxs-lookup"><span data-stu-id="d2361-128">Get</span></span>|<span data-ttu-id="d2361-129">取得描述連接狀態的字串。</span><span class="sxs-lookup"><span data-stu-id="d2361-129">Gets a string that describes the state of the connection.</span></span> <span data-ttu-id="d2361-130">這個檔案可以包含三個可能值： 開啟、 中斷或已關閉。</span><span class="sxs-lookup"><span data-stu-id="d2361-130">This can contain three possible values: OPEN, BROKEN, or CLOSED.</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="d2361-131">支援的方法</span><span class="sxs-lookup"><span data-stu-id="d2361-131">Supported Methods</span></span>  
 <span data-ttu-id="d2361-132">`SiebelConnection`類別支援下列`DbConnection`方法。</span><span class="sxs-lookup"><span data-stu-id="d2361-132">The `SiebelConnection` class supports the following `DbConnection` methods.</span></span>  
  
|<span data-ttu-id="d2361-133">名稱</span><span class="sxs-lookup"><span data-stu-id="d2361-133">Name</span></span>|<span data-ttu-id="d2361-134">Description</span><span class="sxs-lookup"><span data-stu-id="d2361-134">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d2361-135">**CreateDbCommand**</span><span class="sxs-lookup"><span data-stu-id="d2361-135">**CreateDbCommand**</span></span>|<span data-ttu-id="d2361-136">此受保護的方法提供 DbCommand 新執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2361-136">This protected method provides a new DbCommand instance.</span></span>|  
|<span data-ttu-id="d2361-137">**ChangeDatabase**</span><span class="sxs-lookup"><span data-stu-id="d2361-137">**ChangeDatabase**</span></span>|<span data-ttu-id="d2361-138">這個公用方法不支援，如果呼叫將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d2361-138">This public method is not supported, and will throw an exception if called.</span></span>|  
|<span data-ttu-id="d2361-139">**開啟**</span><span class="sxs-lookup"><span data-stu-id="d2361-139">**Open**</span></span>|<span data-ttu-id="d2361-140">藉由建立 WCF 通道開啟 Siebel 系統的連接。</span><span class="sxs-lookup"><span data-stu-id="d2361-140">Opens a connection with the Siebel system by creating a WCF channel.</span></span>|  
|<span data-ttu-id="d2361-141">**關閉**</span><span class="sxs-lookup"><span data-stu-id="d2361-141">**Close**</span></span>|<span data-ttu-id="d2361-142">關閉 WCF 通道會關閉與 Siebel 系統的連線。</span><span class="sxs-lookup"><span data-stu-id="d2361-142">Closes a connection with the Siebel system by closing a WCF channel.</span></span>|  
|<span data-ttu-id="d2361-143">**CreateCommand**</span><span class="sxs-lookup"><span data-stu-id="d2361-143">**CreateCommand**</span></span>|<span data-ttu-id="d2361-144">建立命令物件。</span><span class="sxs-lookup"><span data-stu-id="d2361-144">Creates a command object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2361-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2361-145">See Also</span></span>  
 [<span data-ttu-id="d2361-146">Siebel 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="d2361-146">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)