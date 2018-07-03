---
title: Siebel 配接器中的 SiebelConnection 類別 |Microsoft Docs
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
ms.openlocfilehash: 8dd9e4bbf08d73c8fa48113aad1ecf12fdf0f237
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001983"
---
# <a name="siebelconnection-class-in-the-siebel-adapter"></a><span data-ttu-id="2ef25-102">Siebel 配接器中的 SiebelConnection 類別</span><span class="sxs-lookup"><span data-stu-id="2ef25-102">SiebelConnection class in the Siebel adapter</span></span>
<span data-ttu-id="2ef25-103">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]存取基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] `Binding`，則`ConnectionFactory`，和`Channel`連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="2ef25-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] accesses the underlying [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]`Binding`, the `ConnectionFactory`, and `Channel` to connect to the Siebel system.</span></span> <span data-ttu-id="2ef25-104">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]實作`DbConnection`類別，以支援上述功能。</span><span class="sxs-lookup"><span data-stu-id="2ef25-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implements the `DbConnection` class to support the preceding features.</span></span>  

 <span data-ttu-id="2ef25-105">使用的執行個體`Microsoft.Data.SiebelClient.SiebelClientFactory`，用戶端程式可以取得的執行個體`System.Data.Common.DbConnection`類別來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="2ef25-105">Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbConnection` class to connect to the Siebel system.</span></span>  

```  
//In this example, factory is an instance of SiebelClientFactory  
DbConnection connection = factory.CreateConnection();  
```  

 <span data-ttu-id="2ef25-106">或者，可以用下列方法，來建立連線：</span><span class="sxs-lookup"><span data-stu-id="2ef25-106">Alternatively, the following approach can be used to create a connection:</span></span>  

```  

SiebelConnection connection = new SiebelConnection();  
connection.ConnectionString = connectionString;  
```  

 <span data-ttu-id="2ef25-107">`SiebelConnection`類別繼承自`DbConnection`。</span><span class="sxs-lookup"><span data-stu-id="2ef25-107">The `SiebelConnection` class inherits from `DbConnection`.</span></span> <span data-ttu-id="2ef25-108">命名空間中存在`Microsoft.Data.SiebelClient`。</span><span class="sxs-lookup"><span data-stu-id="2ef25-108">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  

## <a name="supported-properties"></a><span data-ttu-id="2ef25-109">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="2ef25-109">Supported Properties</span></span>  
 <span data-ttu-id="2ef25-110">`SiebelConnection`類別支援下列`DbConnection`屬性。</span><span class="sxs-lookup"><span data-stu-id="2ef25-110">The `SiebelConnection` class supports the following `DbConnection` properties.</span></span>  


|         <span data-ttu-id="2ef25-111">[屬性]</span><span class="sxs-lookup"><span data-stu-id="2ef25-111">Name</span></span>         |   <span data-ttu-id="2ef25-112">取得或設定</span><span class="sxs-lookup"><span data-stu-id="2ef25-112">Get/Set</span></span>   |                                                                                                      <span data-ttu-id="2ef25-113">描述</span><span class="sxs-lookup"><span data-stu-id="2ef25-113">Description</span></span>                                                                                                       |
|----------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ef25-114">**ConnectionString**</span><span class="sxs-lookup"><span data-stu-id="2ef25-114">**ConnectionString**</span></span> | <span data-ttu-id="2ef25-115">取得和設定</span><span class="sxs-lookup"><span data-stu-id="2ef25-115">Get and Set</span></span> |                                                                                  <span data-ttu-id="2ef25-116">取得或設定用來開啟連接的字串。</span><span class="sxs-lookup"><span data-stu-id="2ef25-116">Gets or sets the string used to open the connection.</span></span>                                                                                  |
|     <span data-ttu-id="2ef25-117">**[資料庫備份]**</span><span class="sxs-lookup"><span data-stu-id="2ef25-117">**Database**</span></span>     |     <span data-ttu-id="2ef25-118">Get</span><span class="sxs-lookup"><span data-stu-id="2ef25-118">Get</span></span>     |        <span data-ttu-id="2ef25-119">取得後開啟連接時，目前資料庫的名稱或連接開啟之前，連接字串中指定的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="2ef25-119">Gets the name of the current database after a connection is opened, or the database name specified in the connection string before the connection is opened.</span></span> <span data-ttu-id="2ef25-120">這應該是 Siebel 儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="2ef25-120">This should be the Siebel repository name.</span></span>         |
|    <span data-ttu-id="2ef25-121">**DataSource**</span><span class="sxs-lookup"><span data-stu-id="2ef25-121">**DataSource**</span></span>    |     <span data-ttu-id="2ef25-122">Get</span><span class="sxs-lookup"><span data-stu-id="2ef25-122">Get</span></span>     |                                                                                <span data-ttu-id="2ef25-123">取得此連線的 Siebel 閘道的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ef25-123">Gets the name of the Siebel gateway for this connection.</span></span>                                                                                |
|  <span data-ttu-id="2ef25-124">**ServerVersion**</span><span class="sxs-lookup"><span data-stu-id="2ef25-124">**ServerVersion**</span></span>   |     <span data-ttu-id="2ef25-125">Get</span><span class="sxs-lookup"><span data-stu-id="2ef25-125">Get</span></span>     | <span data-ttu-id="2ef25-126">在目前版本中的[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，這個屬性會傳回硬式編碼值，不代表實際的 Siebel 伺服器版本。</span><span class="sxs-lookup"><span data-stu-id="2ef25-126">In the current version of [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], this property returns a hard-coded value, which does not represent the actual version of the Siebel server.</span></span> |
|      <span data-ttu-id="2ef25-127">**State**</span><span class="sxs-lookup"><span data-stu-id="2ef25-127">**State**</span></span>       |     <span data-ttu-id="2ef25-128">Get</span><span class="sxs-lookup"><span data-stu-id="2ef25-128">Get</span></span>     |                                               <span data-ttu-id="2ef25-129">取得描述連接狀態的字串。</span><span class="sxs-lookup"><span data-stu-id="2ef25-129">Gets a string that describes the state of the connection.</span></span> <span data-ttu-id="2ef25-130">這個檔案可以包含三個可能的值： 開啟、 中斷或已關閉。</span><span class="sxs-lookup"><span data-stu-id="2ef25-130">This can contain three possible values: OPEN, BROKEN, or CLOSED.</span></span>                                               |

## <a name="supported-methods"></a><span data-ttu-id="2ef25-131">支援的方法</span><span class="sxs-lookup"><span data-stu-id="2ef25-131">Supported Methods</span></span>  
 <span data-ttu-id="2ef25-132">`SiebelConnection`類別支援下列`DbConnection`方法。</span><span class="sxs-lookup"><span data-stu-id="2ef25-132">The `SiebelConnection` class supports the following `DbConnection` methods.</span></span>  

|<span data-ttu-id="2ef25-133">[屬性]</span><span class="sxs-lookup"><span data-stu-id="2ef25-133">Name</span></span>|<span data-ttu-id="2ef25-134">描述</span><span class="sxs-lookup"><span data-stu-id="2ef25-134">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="2ef25-135">**CreateDbCommand**</span><span class="sxs-lookup"><span data-stu-id="2ef25-135">**CreateDbCommand**</span></span>|<span data-ttu-id="2ef25-136">此受保護的方法提供新的 DbCommand 例項。</span><span class="sxs-lookup"><span data-stu-id="2ef25-136">This protected method provides a new DbCommand instance.</span></span>|  
|<span data-ttu-id="2ef25-137">**ChangeDatabase**</span><span class="sxs-lookup"><span data-stu-id="2ef25-137">**ChangeDatabase**</span></span>|<span data-ttu-id="2ef25-138">這個公用方法不支援，而且將會擲回例外狀況，如果呼叫。</span><span class="sxs-lookup"><span data-stu-id="2ef25-138">This public method is not supported, and will throw an exception if called.</span></span>|  
|<span data-ttu-id="2ef25-139">**開啟**</span><span class="sxs-lookup"><span data-stu-id="2ef25-139">**Open**</span></span>|<span data-ttu-id="2ef25-140">開啟與 Siebel 系統的連線，藉由建立 WCF 通道。</span><span class="sxs-lookup"><span data-stu-id="2ef25-140">Opens a connection with the Siebel system by creating a WCF channel.</span></span>|  
|<span data-ttu-id="2ef25-141">**關閉**</span><span class="sxs-lookup"><span data-stu-id="2ef25-141">**Close**</span></span>|<span data-ttu-id="2ef25-142">關閉 WCF 通道會關閉與 Siebel 系統的連線。</span><span class="sxs-lookup"><span data-stu-id="2ef25-142">Closes a connection with the Siebel system by closing a WCF channel.</span></span>|  
|<span data-ttu-id="2ef25-143">**CreateCommand**</span><span class="sxs-lookup"><span data-stu-id="2ef25-143">**CreateCommand**</span></span>|<span data-ttu-id="2ef25-144">建立命令物件。</span><span class="sxs-lookup"><span data-stu-id="2ef25-144">Creates a command object.</span></span>|  

## <a name="see-also"></a><span data-ttu-id="2ef25-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ef25-145">See Also</span></span>  
 [<span data-ttu-id="2ef25-146">使用 Siebel 配接器擴充 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="2ef25-146">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)