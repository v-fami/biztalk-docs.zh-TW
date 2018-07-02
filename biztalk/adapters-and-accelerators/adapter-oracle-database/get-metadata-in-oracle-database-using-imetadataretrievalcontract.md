---
title: 在 Oracle 資料庫中使用 IMetadataRetrievalContract 取得中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving using IMetadataRetrievalContract
ms.assetid: 7d32694f-4384-4c2f-be72-ac52c7b2e9f5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9510c7ae534251218826a31eea1cc39c8d1f139
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977991"
---
# <a name="get-metadata-in-oracle-database-using-imetadataretrievalcontract"></a><span data-ttu-id="37609-102">在 Oracle 資料庫中使用 IMetadataRetrievalContract 取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="37609-102">Get Metadata in Oracle Database Using IMetadataRetrievalContract</span></span>
<span data-ttu-id="37609-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開**IMetadataRetrievalContract**瀏覽及搜尋 Oracle 資料庫成品，以及擷取表單的 Web 服務描述語言 (WSDL 中的作業的中繼資料，您可以使用的端點) 文件。</span><span class="sxs-lookup"><span data-stu-id="37609-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes an **IMetadataRetrievalContract**endpoint that you can use to browse and search for Oracle database artifacts and to retrieve metadata for operations in the form of a Web Services Description Language (WSDL) document.</span></span>  
  
 <span data-ttu-id="37609-104">**IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供中繼資料瀏覽、 搜尋和擷取功能。</span><span class="sxs-lookup"><span data-stu-id="37609-104">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and provides metadata browse, search, and retrieval capabilities.</span></span> <span data-ttu-id="37609-105">除了**IMetadataRetrievalContract**介面[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開**MetadataRetrievalClient**實作介面的類別。</span><span class="sxs-lookup"><span data-stu-id="37609-105">In addition to the **IMetadataRetrievalContract** interface, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes the **MetadataRetrievalClient** class, which implements the interface.</span></span> <span data-ttu-id="37609-106">您可以使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用中繼資料; 若要瀏覽、 搜尋及擷取中繼資料中公開的方法是在每個案例相同。</span><span class="sxs-lookup"><span data-stu-id="37609-106">You can use either an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with metadata; the methods exposed to browse, search, and retrieve metadata are the same in each case.</span></span>  
  
 <span data-ttu-id="37609-107">下列各節提供有關如何使用資訊**IMetadataRetrievalContract**介面。</span><span class="sxs-lookup"><span data-stu-id="37609-107">The following sections provide information about how to use the **IMetadataRetrievalContract** interface.</span></span>  
  
## <a name="the-imetadataretrievalcontract-interface"></a><span data-ttu-id="37609-108">IMetadataRetrievalContract 介面</span><span class="sxs-lookup"><span data-stu-id="37609-108">The IMetadataRetrievalContract Interface</span></span>  
 <span data-ttu-id="37609-109">下表提供當您使用時所使用的重要類別的相關資訊**IMetadataRetrievalContract**介面。</span><span class="sxs-lookup"><span data-stu-id="37609-109">The following table provides information about important classes that are used when you work with the **IMetadataRetrievalContract** interface.</span></span>  
  
|<span data-ttu-id="37609-110">類別或介面</span><span class="sxs-lookup"><span data-stu-id="37609-110">Class or Interface</span></span>|<span data-ttu-id="37609-111">描述</span><span class="sxs-lookup"><span data-stu-id="37609-111">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="37609-112">**IMetadataRetrievalContract**介面</span><span class="sxs-lookup"><span data-stu-id="37609-112">**IMetadataRetrievalContract** interface</span></span><br /><br /> <span data-ttu-id="37609-113">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="37609-113">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="37609-114">定義**瀏覽**，**搜尋**，並**GetMetadata**方法。</span><span class="sxs-lookup"><span data-stu-id="37609-114">Defines the **Browse**, **Search**, and **GetMetadata** methods.</span></span> <span data-ttu-id="37609-115">您可以叫用這些方法使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**使用配接器中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37609-115">You invoke these methods either by using an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with adapter metadata.</span></span>|  
|<span data-ttu-id="37609-116">**MetadataRetrievalClient**類別</span><span class="sxs-lookup"><span data-stu-id="37609-116">**MetadataRetrievalClient** class</span></span><br /><br /> <span data-ttu-id="37609-117">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="37609-117">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="37609-118">Implements **IMetadataRetrievalContract**介面。</span><span class="sxs-lookup"><span data-stu-id="37609-118">Implements the **IMetadataRetrievalContract** interface.</span></span> <span data-ttu-id="37609-119">您可以建立這個類別的執行個體，並設定 Oracle 資料庫的方法是提供**OracleDBBinding**並**EndpointAddress**。</span><span class="sxs-lookup"><span data-stu-id="37609-119">You can create an instance of this class and configure it for your Oracle database by providing an **OracleDBBinding** and an **EndpointAddress**.</span></span> <span data-ttu-id="37609-120">然後您可以叫用其方法，以使用中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37609-120">Then you can invoke its methods to work with metadata.</span></span>|  
|<span data-ttu-id="37609-121">**MetadataRetrievalNode**類別</span><span class="sxs-lookup"><span data-stu-id="37609-121">**MetadataRetrievalNode** class</span></span><br /><br /> <span data-ttu-id="37609-122">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="37609-122">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="37609-123">表示介面卡上的中繼資料節點。</span><span class="sxs-lookup"><span data-stu-id="37609-123">Represents a metadata node on the adapter.</span></span> <span data-ttu-id="37609-124">**瀏覽**並**搜尋**方法會傳回此節點類型，而**GetMetadata**方法會採用此節點類型做為參數。</span><span class="sxs-lookup"><span data-stu-id="37609-124">The **Browse** and **Search** methods return nodes of this type, and the **GetMetadata** method takes nodes of this type as a parameter.</span></span>|  
|<span data-ttu-id="37609-125">**ServiceDescription**類別</span><span class="sxs-lookup"><span data-stu-id="37609-125">**ServiceDescription** class</span></span><br /><br /> <span data-ttu-id="37609-126">(System.Web.Services.Description)</span><span class="sxs-lookup"><span data-stu-id="37609-126">(System.Web.Services.Description)</span></span>|<span data-ttu-id="37609-127">提供方法來建立和格式化的有效的 WSDL 文件檔案。</span><span class="sxs-lookup"><span data-stu-id="37609-127">Provides a means of creating and formatting a valid WSDL document file.</span></span> <span data-ttu-id="37609-128">**GetMetadata**方法會傳回**ServiceDescription**物件。</span><span class="sxs-lookup"><span data-stu-id="37609-128">The **GetMetadata** method returns a **ServiceDescription** object.</span></span>|  
  
 
### <a name="metadata-node-ids"></a><span data-ttu-id="37609-129">中繼資料節點識別碼</span><span class="sxs-lookup"><span data-stu-id="37609-129">Metadata Node IDs</span></span>  
 <span data-ttu-id="37609-130">配接器會將其中繼資料組織為階層式樹狀結構的節點。</span><span class="sxs-lookup"><span data-stu-id="37609-130">The adapter organizes its metadata as a hierarchical tree of nodes.</span></span> <span data-ttu-id="37609-131">此樹狀結構內有兩種類型的中繼資料節點：</span><span class="sxs-lookup"><span data-stu-id="37609-131">Within this tree structure there are two types of metadata nodes:</span></span>  
  
- <span data-ttu-id="37609-132">**作業節點**代表配接器會呈現 Oracle 資料庫成品的作業。</span><span class="sxs-lookup"><span data-stu-id="37609-132">**Operation nodes** represent operations that the adapter surfaces on Oracle database artifacts.</span></span> <span data-ttu-id="37609-133">作業節點是樹狀結構的分葉。</span><span class="sxs-lookup"><span data-stu-id="37609-133">Operation nodes are the leaves of the tree.</span></span>  
  
- <span data-ttu-id="37609-134">**類別目錄節點**代表作業的介面卡上 Oracle 資料庫成品並不會直接對應的 Oracle 資料庫成品的群組。</span><span class="sxs-lookup"><span data-stu-id="37609-134">**Category nodes** represent Oracle database artifacts and groupings of Oracle database artifacts that do not directly correspond to an operation on the adapter.</span></span> <span data-ttu-id="37609-135">類別目錄節點是樹狀結構; 的分支它們包含其他類別目錄節點和/或作業節點。</span><span class="sxs-lookup"><span data-stu-id="37609-135">Category nodes are the branches of the tree; they contain other category nodes and/or operation nodes.</span></span> <span data-ttu-id="37609-136">例如，Oracle 資料表和封裝被以類別目錄節點。</span><span class="sxs-lookup"><span data-stu-id="37609-136">For example, Oracle tables and packages are represented as category nodes.</span></span>  
  
  <span data-ttu-id="37609-137">每個配接器所顯示的中繼資料節點識別唯一的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="37609-137">Each metadata node surfaced by the adapter is identified by a unique node ID.</span></span> <span data-ttu-id="37609-138">如需有關中繼資料節點識別碼顯示配接器的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。</span><span class="sxs-lookup"><span data-stu-id="37609-138">For more information about the metadata node IDs surfaced by the adapter, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span></span> <span data-ttu-id="37609-139">指定目標 Oracle 資料庫成品，當您使用的情況下，您在使用這些節點 Id **IMetadataRetrievalContract**介面來瀏覽、 搜尋及擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37609-139">You use these node IDs to specify target Oracle database artifacts when you use the **IMetadataRetrievalContract** interface to browse, search, and retrieve metadata.</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="37609-140">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="37609-140">Binding Properties</span></span>  
 <span data-ttu-id="37609-141">您是否使用**IMetadataRetrievalContract**通道或有**IMetadataRetrievalClient**若要使用的中繼資料，您必須指定**OracleDBBinding**時您建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="37609-141">Whether you use an **IMetadataRetrievalContract** channel or an **IMetadataRetrievalClient** to work with metadata, you must specify an **OracleDBBinding** when you create the instance.</span></span>  
  
 <span data-ttu-id="37609-142">有數個會影響配接器如何產生中繼資料的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="37609-142">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="37609-143">這些屬性是：</span><span class="sxs-lookup"><span data-stu-id="37609-143">These properties are:</span></span>  
  
-   <span data-ttu-id="37609-144">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="37609-144">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="37609-145">**UseSchemaInNamespace**</span><span class="sxs-lookup"><span data-stu-id="37609-145">**UseSchemaInNamespace**</span></span>  
  
-   <span data-ttu-id="37609-146">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="37609-146">**PollingStatement**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37609-147">如果您想要擷取 POLLINGSTMT 作業的中繼資料必須設定**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="37609-147">If you want to retrieve metadata for the POLLINGSTMT operation you must set the **PollingStatement** binding property.</span></span>  
  
 <span data-ttu-id="37609-148">您應該確定這些繫結屬性已設為開啟中繼資料擷取物件之前，您的應用程式所需的值。</span><span class="sxs-lookup"><span data-stu-id="37609-148">You should ensure that these binding properties are set to the values required for your application before you open the metadata retrieval object.</span></span> <span data-ttu-id="37609-149">如需詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="37609-149">For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
### <a name="browsing-metadata-nodes"></a><span data-ttu-id="37609-150">瀏覽中繼資料節點</span><span class="sxs-lookup"><span data-stu-id="37609-150">Browsing Metadata Nodes</span></span>  
 <span data-ttu-id="37609-151">您使用**瀏覽**方法來傳回所包含的所有中繼資料節點中的父節點。</span><span class="sxs-lookup"><span data-stu-id="37609-151">You use the **Browse** method to return all the metadata nodes that are contained in a parent node.</span></span> <span data-ttu-id="37609-152">下列範例會瀏覽 Oracle 資料庫上的前三個結構描述。</span><span class="sxs-lookup"><span data-stu-id="37609-152">The following example browses for the first three schemas on the Oracle database.</span></span> <span data-ttu-id="37609-153">在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。</span><span class="sxs-lookup"><span data-stu-id="37609-153">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="37609-154">您只能瀏覽類別節點;您無法瀏覽作業節點。</span><span class="sxs-lookup"><span data-stu-id="37609-154">You can only browse category nodes; you cannot browse operation nodes.</span></span>  
  
### <a name="searching-for-metadata-nodes"></a><span data-ttu-id="37609-155">搜尋中繼資料節點</span><span class="sxs-lookup"><span data-stu-id="37609-155">Searching for Metadata Nodes</span></span>  
 <span data-ttu-id="37609-156">您使用**搜尋**方法，以執行搜尋的父節點所包含的節點。</span><span class="sxs-lookup"><span data-stu-id="37609-156">You use the **Search** method to perform a search for nodes contained by a parent node.</span></span> <span data-ttu-id="37609-157">配接器支援萬用字元搜尋在運算式中;例如，您也可以指定百分比 （%） 比對零或多個字元的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="37609-157">The adapter supports wildcard characters in search expressions; for example you can specify the percent (%) wildcard character to match zero or more characters.</span></span> <span data-ttu-id="37609-158">下列範例會示範包含字串"EMP"SCOTT 結構描述中所有資料表的搜尋。</span><span class="sxs-lookup"><span data-stu-id="37609-158">The following example shows a search for all the tables in the SCOTT schema that contain the string "EMP".</span></span> <span data-ttu-id="37609-159">在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。</span><span class="sxs-lookup"><span data-stu-id="37609-159">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// Search for all nodes that contain "EMP" under the SCOTT.Table node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="37609-160">搜尋僅適用於一組有限的節點上。</span><span class="sxs-lookup"><span data-stu-id="37609-160">Searching is only supported on a limited set of nodes.</span></span> <span data-ttu-id="37609-161">如需有關支援搜尋的節點以及搜尋運算式中支援的萬用字元的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。</span><span class="sxs-lookup"><span data-stu-id="37609-161">For more information about the nodes on which search is supported and about the wildcard characters supported in search expressions, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span></span>  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a><span data-ttu-id="37609-162">擷取作業的中繼資料 (WSDL)</span><span class="sxs-lookup"><span data-stu-id="37609-162">Retrieving Metadata (WSDL) for Operations</span></span>  
 <span data-ttu-id="37609-163">您使用**GetMetadata**方法來擷取群組的作業節點的服務描述 （WSDL 文件）。</span><span class="sxs-lookup"><span data-stu-id="37609-163">You use the **GetMetadata** method to retrieve a service description (WSDL document) for a group of operation nodes.</span></span> <span data-ttu-id="37609-164">下列範例會擷取服務描述，其中包含所有配接器會呈現 scott 的作業。EMP 資料表，藉由指定其節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="37609-164">The following example retrieves a service description that contains all of the operations that the adapter surfaces for the SCOTT.EMP table by specifying its node ID.</span></span> <span data-ttu-id="37609-165">在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。</span><span class="sxs-lookup"><span data-stu-id="37609-165">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// Get a service description that contains all of the operations   
// surfaced for the SCOTT.EMP table. The IsOperation  
// property is set false because this is a category node.  
nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
nodes[0].IsOperation = false;  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="37609-166">**IsOperation**屬性應該是類別目錄節點和運算節點為 true，則為 false。</span><span class="sxs-lookup"><span data-stu-id="37609-166">The **IsOperation** property should be false for category nodes and true for operation nodes.</span></span>  
  
### <a name="using-a-metadataretrievalclient"></a><span data-ttu-id="37609-167">使用 MetadataRetrievalClient</span><span class="sxs-lookup"><span data-stu-id="37609-167">Using a MetadataRetrievalClient</span></span>  
 <span data-ttu-id="37609-168">建立和使用**MetadataRetrievalClient**是非常類似任何其他 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="37609-168">Creating and using a **MetadataRetrievalClient** is much the same as any other WCF client.</span></span> <span data-ttu-id="37609-169">您可以建立用戶端藉由指定端點和執行個體**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="37609-169">You create the client by specifying an endpoint and an instance of **OracleDBBinding**.</span></span> <span data-ttu-id="37609-170">以宣告方式在組態或命令式程式碼中，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="37609-170">You can do this either declaratively in configuration or imperatively in your code.</span></span> <span data-ttu-id="37609-171">然後叫用的方法**MetadataRetrievalClient**瀏覽、 搜尋及擷取配接器的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37609-171">You then invoke the methods of the **MetadataRetrievalClient** to browse, search, and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="37609-172">下列範例示範如何使用**MetadataRetrievalClient**瀏覽、 搜尋及擷取中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="37609-172">The following example shows how to use a **MetadataRetrievalClient** to browse, search, and retrieve metadata from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="37609-173">此範例示範：</span><span class="sxs-lookup"><span data-stu-id="37609-173">The example demonstrates:</span></span>  
  
-   <span data-ttu-id="37609-174">瀏覽 Oracle 資料庫結構描述的中繼資料樹狀結構的根節點。</span><span class="sxs-lookup"><span data-stu-id="37609-174">Browsing the root node of the metadata tree for Oracle Database schemas.</span></span>  
  
-   <span data-ttu-id="37609-175">搜尋名稱中包含字串"EMP"SCOTT 結構描述中的資料表。</span><span class="sxs-lookup"><span data-stu-id="37609-175">Searching for the tables in the SCOTT schema with names that contain the string "EMP".</span></span>  
  
-   <span data-ttu-id="37609-176">正在擷取所有 scott 所支援的作業中繼資料。藉由傳遞的類別目錄節點的 EMP 資料表**GetMetadata**方法。</span><span class="sxs-lookup"><span data-stu-id="37609-176">Retrieving metadata for all of the operations supported for the SCOTT.EMP table by passing a category node to the **GetMetadata** method.</span></span>  
  
-   <span data-ttu-id="37609-177">藉由傳遞 POLLINGSTMT 作業節點，以擷取 POLLINGSTMT 作業的中繼資料**GetMetadata**方法...</span><span class="sxs-lookup"><span data-stu-id="37609-177">Retrieving metadata for the POLLINGSTMT operation by passing the POLLINGSTMT operation node to the **GetMetadata** method..</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace OracleMetadataRetrieval  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //write all the nodes returned to the console.  
            foreach (MetadataRetrievalNode node in nodes)  
            {  
                Console.WriteLine("NodeId = " + node.NodeId);  
                Console.WriteLine("\tDirection   = " + node.Direction.ToString());  
                Console.WriteLine("\tIsOperation = " + node.IsOperation.ToString());  
                Console.WriteLine("\tDisplayName = " + node.DisplayName);  
                Console.WriteLine("\tDescription = " + node.Description);  
            }  
            Console.WriteLine();  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            MetadataRetrievalClient client = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // create a binding and   
                // set the PollingStatement binding property if you want to  
                // return metadata for the POLLINGSTMT operation  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.PollingStatement = "SELECT * FROM EMP";  
  
                // Set PollingId parameter if you want to alter the namespace of the POLLINGSTMT operation  
                EndpointAddress address = new EndpointAddress("oracledb://ADAPTER?PollingId=1");  
  
                client = new MetadataRetrievalClient(binding, address);  
                client.ClientCredentials.UserName.UserName = "SCOTT";  
                client.ClientCredentials.UserName.Password = "TIGER";  
                client.Open();  
  
                // Browse for the first 3 (schema) nodes directly under the root  
                // The parameters are the parent Node ID, the start index, and the maximum number  
                // of nodes to return  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Search for first 3 tables that contain "EMP" in the SCOTT schema  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return  
                nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
                nodeWriter.Write(String.Format("Search results for \"%EMP%\" under {0} node:", "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table"), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // surfaced for the SCOTT.EMP table. The IsOperation property is set false  
                // because this is a category node.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
                nodes[0].IsOperation = false;  
                System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
                description.Write("EmpTableContract.wsdl");  
  
                // Get a WSDL document that specifies a contract that contains the   
                // the POLLINGSTMT operation. The IsOperation property is set true  
                // because this is an operation node.  
                // Note that the operation NodeId is equivalent to the message action.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT";  
                nodes[0].IsOperation = true;  
                description = client.GetMetadata(nodes);  
                description.Write("PollingContract.wsdl");  
  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="37609-178">以下顯示在主控台上此程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="37609-178">The following shows the output of this program on the console.</span></span> <span data-ttu-id="37609-179">您可以看到每個方法所傳回的中繼資料擷取節點的結構。</span><span class="sxs-lookup"><span data-stu-id="37609-179">You can see the structure of the metadata retrieval nodes returned by each method.</span></span> <span data-ttu-id="37609-180">也計劃會將兩個 WSDL 文件寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="37609-180">The program also writes two WSDL documents to files.</span></span>  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTERTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTERTEST  
        Description = Owned By ADAPTERTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTEST  
        Description = Owned By ADAPTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADMIN123  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADMIN123  
        Description = Owned By ADMIN123  
  
Search results for "%EMP%" under http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/AEMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = AEMP  
        Description = Table.AEMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP  
        Description = Table.EMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP1  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP1  
        Description = Table.EMP1  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a><span data-ttu-id="37609-181">使用 IMetadataRetrievalContract 通道</span><span class="sxs-lookup"><span data-stu-id="37609-181">Using an IMetadataRetrievalContract Channel</span></span>  
 <span data-ttu-id="37609-182">您也可以建立**IMetadataRetrievalContract**通道，然後使用此通道瀏覽、 搜尋及擷取配接器的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37609-182">You can also create an **IMetadataRetrievalContract** channel and then use this channel to browse, search, and retrieve metadata from the adapter.</span></span> <span data-ttu-id="37609-183">(是針對相同的方法簽章**MetadataRetrievalClient**類別。)下列範例顯示如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="37609-183">(The method signatures are the same as for the **MetadataRetrievalClient** class.) The following example shows how to do this.</span></span>  
  
```  
…  
//Create a binding and endpoint address.  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER/");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a><span data-ttu-id="37609-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37609-184">See Also</span></span>  
 [<span data-ttu-id="37609-185">從 Oracle 資料庫，以程式設計方式取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="37609-185">Get Metadata Programmatically from the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)