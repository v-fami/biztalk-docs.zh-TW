---
title: Siebel 配接器中的 SiebelCommand 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SiebelCommand
- Data Provider for Siebel, SiebelCommand
- SiebelCommand, supported methods and properties
ms.assetid: 7cba0e47-634b-4878-b480-80fbcbbf5c90
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d268e9a1d5954d703d392070a53c84bd9cee0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222358"
---
# <a name="siebelcommand-class-in-the-siebel-adapter"></a><span data-ttu-id="5eac3-102">Siebel 配接器中 SiebelCommand 類別</span><span class="sxs-lookup"><span data-stu-id="5eac3-102">SiebelCommand class in the Siebel adapter</span></span>
<span data-ttu-id="5eac3-103">建立與 Siebel 系統的連線後[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]剖析 Siebel 命令字串和 ADO.NET 用戶端所提供的命令參數，並將命令對應到 WCF 要求訊息。</span><span class="sxs-lookup"><span data-stu-id="5eac3-103">After establishing a connection with the Siebel system, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] parses the Siebel command strings and command parameters provided by the ADO.NET client and maps the command into a WCF request message.</span></span> <span data-ttu-id="5eac3-104">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]然後會傳送要求給[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]並取得回應 XML 以及從配接器的本文內容。</span><span class="sxs-lookup"><span data-stu-id="5eac3-104">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] then sends the request to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and obtains the response XML and the body contents from the adapter.</span></span> <span data-ttu-id="5eac3-105">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]接著會使用`XMLDataReader`來擷取關聯式資料的 XML 主體。</span><span class="sxs-lookup"><span data-stu-id="5eac3-105">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] then uses the `XMLDataReader` to retrieve the relational data from the XML body.</span></span>  
  
 <span data-ttu-id="5eac3-106">使用的執行個體`Microsoft.Data.SiebelClient.SiebelClientFactory`，用戶端程式可以取得的執行個體`System.Data.Common.DbCommand`類別以建構 Siebel 命令。</span><span class="sxs-lookup"><span data-stu-id="5eac3-106">Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbCommand` class to construct a Siebel command.</span></span>  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbCommand command = factory.CreateCommand();  
```  
  
 <span data-ttu-id="5eac3-107">或者，可以使用下列方法，來建立命令：</span><span class="sxs-lookup"><span data-stu-id="5eac3-107">Alternatively, the following approach can be used to create a command:</span></span>  
  
```  
//Here connection is an instance of SiebelConnection  
SiebelCommand cmd = (SiebelCommand) connection.CreateCommand();  
cmd.CommandText = "SELECT [Name] as MyName, [City], [Country]  from Account.Account WHERE Name LIKE '3Com*' OPTION 'ViewMode 1'";  
```  
  
 <span data-ttu-id="5eac3-108">`SiebelCommand`類別繼承自`DbCommand`。</span><span class="sxs-lookup"><span data-stu-id="5eac3-108">The `SiebelCommand` class inherits from `DbCommand`.</span></span>  <span data-ttu-id="5eac3-109">命名空間中存在`Microsoft.Data.SiebelClient`。</span><span class="sxs-lookup"><span data-stu-id="5eac3-109">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="5eac3-110">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="5eac3-110">Supported Properties</span></span>  
 <span data-ttu-id="5eac3-111">**SiebelCommand**類別支援下列`DbCommand`*保護*屬性：</span><span class="sxs-lookup"><span data-stu-id="5eac3-111">The **SiebelCommand** class supports the following `DbCommand`*protected* properties:</span></span>  
  
|<span data-ttu-id="5eac3-112">名稱</span><span class="sxs-lookup"><span data-stu-id="5eac3-112">Name</span></span>|<span data-ttu-id="5eac3-113">Get/Set</span><span class="sxs-lookup"><span data-stu-id="5eac3-113">Get/Set</span></span>|<span data-ttu-id="5eac3-114">Description</span><span class="sxs-lookup"><span data-stu-id="5eac3-114">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="5eac3-115">**DbConnection**</span><span class="sxs-lookup"><span data-stu-id="5eac3-115">**DbConnection**</span></span>|<span data-ttu-id="5eac3-116">取得和設定</span><span class="sxs-lookup"><span data-stu-id="5eac3-116">Get and Set</span></span>|<span data-ttu-id="5eac3-117">這會包含基礎`DbConnection`從這個執行個體`DbCommand`取得執行個體。</span><span class="sxs-lookup"><span data-stu-id="5eac3-117">This should contain the underlying `DbConnection` instance from which this `DbCommand` instance is obtained.</span></span>|  
|<span data-ttu-id="5eac3-118">**DbParameterCollection**</span><span class="sxs-lookup"><span data-stu-id="5eac3-118">**DbParameterCollection**</span></span>|<span data-ttu-id="5eac3-119">Get</span><span class="sxs-lookup"><span data-stu-id="5eac3-119">Get</span></span>|<span data-ttu-id="5eac3-120">取得集合`DbParameter`物件。</span><span class="sxs-lookup"><span data-stu-id="5eac3-120">Gets the collection of `DbParameter` objects.</span></span>|  
  
 <span data-ttu-id="5eac3-121">`SiebelCommand`也支援下列`DbCommand`*公用*屬性：</span><span class="sxs-lookup"><span data-stu-id="5eac3-121">`SiebelCommand` also supports the following `DbCommand`*public* properties:</span></span>  
  
|<span data-ttu-id="5eac3-122">名稱</span><span class="sxs-lookup"><span data-stu-id="5eac3-122">Name</span></span>|<span data-ttu-id="5eac3-123">Get/Set</span><span class="sxs-lookup"><span data-stu-id="5eac3-123">Get/Set</span></span>|<span data-ttu-id="5eac3-124">Description</span><span class="sxs-lookup"><span data-stu-id="5eac3-124">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="5eac3-125">**CommandText**</span><span class="sxs-lookup"><span data-stu-id="5eac3-125">**CommandText**</span></span>|<span data-ttu-id="5eac3-126">取得和設定</span><span class="sxs-lookup"><span data-stu-id="5eac3-126">Get and Set</span></span>|<span data-ttu-id="5eac3-127">這包含 ADO.NET 用戶端想要執行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5eac3-127">This contain the SQL statement that the ADO.NET client wishes to execute.</span></span>|  
|<span data-ttu-id="5eac3-128">**CommandType**</span><span class="sxs-lookup"><span data-stu-id="5eac3-128">**CommandType**</span></span>|<span data-ttu-id="5eac3-129">取得和設定</span><span class="sxs-lookup"><span data-stu-id="5eac3-129">Get and Set</span></span>|<span data-ttu-id="5eac3-130">只有`CommandType.Text`支援。</span><span class="sxs-lookup"><span data-stu-id="5eac3-130">Only `CommandType.Text` is supported.</span></span>|  
|<span data-ttu-id="5eac3-131">**連接**</span><span class="sxs-lookup"><span data-stu-id="5eac3-131">**Connection**</span></span>|<span data-ttu-id="5eac3-132">取得和設定</span><span class="sxs-lookup"><span data-stu-id="5eac3-132">Get and Set</span></span>|<span data-ttu-id="5eac3-133">這會使用`DbConnection`成員。</span><span class="sxs-lookup"><span data-stu-id="5eac3-133">This uses the `DbConnection` member.</span></span>|  
|<span data-ttu-id="5eac3-134">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eac3-134">**Parameters**</span></span>|<span data-ttu-id="5eac3-135">Get</span><span class="sxs-lookup"><span data-stu-id="5eac3-135">Get</span></span>|<span data-ttu-id="5eac3-136">這會使用`DbParameterCollection`成員。</span><span class="sxs-lookup"><span data-stu-id="5eac3-136">This uses the `DbParameterCollection` member.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="5eac3-137">`SiebelCommand`類別會忽略`CommandTimeout`， `DesignTimeVisible`，和`DbTransaction`屬性。</span><span class="sxs-lookup"><span data-stu-id="5eac3-137">The `SiebelCommand` class ignores the `CommandTimeout`, `DesignTimeVisible`, and `DbTransaction` properties.</span></span>  
  
## <a name="supported-methods"></a><span data-ttu-id="5eac3-138">支援的方法</span><span class="sxs-lookup"><span data-stu-id="5eac3-138">Supported Methods</span></span>  
 <span data-ttu-id="5eac3-139">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援下列`DbCommand`*保護*方法：</span><span class="sxs-lookup"><span data-stu-id="5eac3-139">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports the following `DbCommand`*protected* methods:</span></span>  
  
|<span data-ttu-id="5eac3-140">名稱</span><span class="sxs-lookup"><span data-stu-id="5eac3-140">Name</span></span>|<span data-ttu-id="5eac3-141">Description</span><span class="sxs-lookup"><span data-stu-id="5eac3-141">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5eac3-142">**CreateDbParameter**</span><span class="sxs-lookup"><span data-stu-id="5eac3-142">**CreateDbParameter**</span></span>|<span data-ttu-id="5eac3-143">建立新`DbParameter`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5eac3-143">Creates a new `DbParameter` instance.</span></span>|  
|<span data-ttu-id="5eac3-144">**ExecuteDbDataReader**</span><span class="sxs-lookup"><span data-stu-id="5eac3-144">**ExecuteDbDataReader**</span></span>|<span data-ttu-id="5eac3-145">這會執行 SELECT 和 EXEC 命令並傳回`DbDataReader`。</span><span class="sxs-lookup"><span data-stu-id="5eac3-145">This executes the SELECT and EXEC commands and returns a `DbDataReader`.</span></span>|  
  
 <span data-ttu-id="5eac3-146">`SiebelCommand`也支援下列`DbCommand`*公用*方法：</span><span class="sxs-lookup"><span data-stu-id="5eac3-146">`SiebelCommand` also supports the following `DbCommand`*public* methods:</span></span>  
  
|<span data-ttu-id="5eac3-147">名稱</span><span class="sxs-lookup"><span data-stu-id="5eac3-147">Name</span></span>|<span data-ttu-id="5eac3-148">Description</span><span class="sxs-lookup"><span data-stu-id="5eac3-148">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5eac3-149">**CreateParameter**</span><span class="sxs-lookup"><span data-stu-id="5eac3-149">**CreateParameter**</span></span>|<span data-ttu-id="5eac3-150">建立新`DbParameter`透過執行個體`CreateDbParameter().`</span><span class="sxs-lookup"><span data-stu-id="5eac3-150">Creates a new `DbParameter` instance through `CreateDbParameter().`</span></span>|  
|<span data-ttu-id="5eac3-151">**ExecuteReader**</span><span class="sxs-lookup"><span data-stu-id="5eac3-151">**ExecuteReader**</span></span>|<span data-ttu-id="5eac3-152">執行`CommandText`針對`Connection`並傳回`DbDataReader`透過`ExecuteDbDataReader()`。</span><span class="sxs-lookup"><span data-stu-id="5eac3-152">Executes `CommandText` against the `Connection` and returns `DbDataReader` through `ExecuteDbDataReader()`.</span></span>|  
|<span data-ttu-id="5eac3-153">**準備**</span><span class="sxs-lookup"><span data-stu-id="5eac3-153">**Prepare**</span></span>|<span data-ttu-id="5eac3-154">這會剖析`CommandText`並建立 SQL 命令剖析樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="5eac3-154">This parses the `CommandText` and builds the SQL command parse tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eac3-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eac3-155">See Also</span></span>  
 [<span data-ttu-id="5eac3-156">Siebel 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="5eac3-156">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)