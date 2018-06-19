---
title: 取得中繼資料中使用 IMetadataRetrievalContract SAP |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, search metadata
- searching metadata
- how to, browse metadata
- browsing metadata
ms.assetid: 0944fc39-9ee5-4702-8b52-e0bc87f202c6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa36eee26dd9467a71f7e8dd4d28d2e37e26606
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218270"
---
# <a name="get-metadata-in-sap-using-imetadataretrievalcontract"></a><span data-ttu-id="bc455-102">使用 IMetadataRetrievalContract SAP 中取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="bc455-102">Get Metadata in SAP using IMetadataRetrievalContract</span></span>
<span data-ttu-id="bc455-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開**IMetadataRetrievalContract**端點可讓您瀏覽及搜尋 SAP 系統成品，以及擷取中繼資料的 Web 服務描述語言 (WSDL) 文件形式作業。</span><span class="sxs-lookup"><span data-stu-id="bc455-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes an **IMetadataRetrievalContract**endpoint that you can use to browse and search for SAP system artifacts and to retrieve metadata in the form of a Web Services Description Language (WSDL) document for operations.</span></span>  
  
 <span data-ttu-id="bc455-104">**IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供中繼資料瀏覽、 搜尋和擷取功能。</span><span class="sxs-lookup"><span data-stu-id="bc455-104">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and provides metadata browse, search, and retrieval capabilities.</span></span> <span data-ttu-id="bc455-105">除了**IMetadataRetrievalContract**介面，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開**MetadataRetrievalClient**類別，實作介面。</span><span class="sxs-lookup"><span data-stu-id="bc455-105">In addition to the **IMetadataRetrievalContract** interface, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes the **MetadataRetrievalClient** class, which implements the interface.</span></span> <span data-ttu-id="bc455-106">您可以使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用中繼資料; 若要瀏覽、 搜尋和擷取中繼資料中公開的方法會在每個案例相同。</span><span class="sxs-lookup"><span data-stu-id="bc455-106">You can use either an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with metadata; the methods exposed to browse, search, and retrieve metadata are the same in each case.</span></span>  
  
 <span data-ttu-id="bc455-107">下列各節提供有關如何使用資訊**IMetadataRetrievalContract**介面。</span><span class="sxs-lookup"><span data-stu-id="bc455-107">The following sections provide information about how to use the **IMetadataRetrievalContract** interface.</span></span>  
  
## <a name="the-imetadataretrievalcontract-interface"></a><span data-ttu-id="bc455-108">IMetadataRetrievalContract 介面</span><span class="sxs-lookup"><span data-stu-id="bc455-108">The IMetadataRetrievalContract Interface</span></span>  
 <span data-ttu-id="bc455-109">下表提供當您使用時所使用的重要類別的相關資訊**IMetadataRetrievalContract**介面。</span><span class="sxs-lookup"><span data-stu-id="bc455-109">The following table provides information about important classes that are used when you work with the **IMetadataRetrievalContract** interface.</span></span>  
  
|<span data-ttu-id="bc455-110">類別或介面</span><span class="sxs-lookup"><span data-stu-id="bc455-110">Class or Interface</span></span>|<span data-ttu-id="bc455-111">Description</span><span class="sxs-lookup"><span data-stu-id="bc455-111">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="bc455-112">**IMetadataRetrievalContract**介面</span><span class="sxs-lookup"><span data-stu-id="bc455-112">**IMetadataRetrievalContract** interface</span></span><br /><br /> <span data-ttu-id="bc455-113">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="bc455-113">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="bc455-114">定義**瀏覽**，**搜尋**，和**GetMetadata**方法。</span><span class="sxs-lookup"><span data-stu-id="bc455-114">Defines the **Browse**, **Search**, and **GetMetadata** methods.</span></span> <span data-ttu-id="bc455-115">您呼叫這些方法，藉由使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用配接器中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bc455-115">You invoke these methods either by using an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with adapter metadata.</span></span>|  
|<span data-ttu-id="bc455-116">**MetadataRetrievalClient**類別</span><span class="sxs-lookup"><span data-stu-id="bc455-116">**MetadataRetrievalClient** class</span></span><br /><br /> <span data-ttu-id="bc455-117">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="bc455-117">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="bc455-118">實作**IMetadataRetrievalContract**介面。</span><span class="sxs-lookup"><span data-stu-id="bc455-118">Implements the **IMetadataRetrievalContract** interface.</span></span> <span data-ttu-id="bc455-119">您可以建立這個類別的執行個體，並可藉由提供將它設定為 SAP 系統**SAPBinding**和**EndpointAddress**。</span><span class="sxs-lookup"><span data-stu-id="bc455-119">You can create an instance of this class and configure it for your SAP system by providing an **SAPBinding** and an **EndpointAddress**.</span></span> <span data-ttu-id="bc455-120">然後您可以叫用其方法與中繼資料一起運作。</span><span class="sxs-lookup"><span data-stu-id="bc455-120">Then you can invoke its methods to work with metadata.</span></span>|  
|<span data-ttu-id="bc455-121">**MetadataRetrievalNode**類別</span><span class="sxs-lookup"><span data-stu-id="bc455-121">**MetadataRetrievalNode** class</span></span><br /><br /> <span data-ttu-id="bc455-122">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="bc455-122">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="bc455-123">表示介面卡上的中繼資料節點。</span><span class="sxs-lookup"><span data-stu-id="bc455-123">Represents a metadata node on the adapter.</span></span> <span data-ttu-id="bc455-124">**瀏覽**和**搜尋**方法會傳回此節點類型，而**GetMetadata**方法會採用此節點類型做為參數。</span><span class="sxs-lookup"><span data-stu-id="bc455-124">The **Browse** and **Search** methods return nodes of this type, and the **GetMetadata** method takes nodes of this type as a parameter.</span></span>|  
|<span data-ttu-id="bc455-125">**ServiceDescription**類別</span><span class="sxs-lookup"><span data-stu-id="bc455-125">**ServiceDescription** class</span></span><br /><br /> <span data-ttu-id="bc455-126">(System.Web.Services.Description)</span><span class="sxs-lookup"><span data-stu-id="bc455-126">(System.Web.Services.Description)</span></span>|<span data-ttu-id="bc455-127">提供建立和格式化有效的 WSDL 文件檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="bc455-127">Provides a means of creating and formatting a valid WSDL document file.</span></span> <span data-ttu-id="bc455-128">**GetMetadata**方法會傳回**ServiceDescription**物件。</span><span class="sxs-lookup"><span data-stu-id="bc455-128">The **GetMetadata** method returns a **ServiceDescription** object.</span></span>|  
  
 <span data-ttu-id="bc455-129">如需有關**IMetadataRetrievalContract**介面， **MetadataRetrievalClient**類別，而**MetadataRetrievalNode**類別，請參閱 < **Microsoft.ServiceModel.Channels**受管理參考在[http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566)。</span><span class="sxs-lookup"><span data-stu-id="bc455-129">For more information about the **IMetadataRetrievalContract** interface, the **MetadataRetrievalClient** class, and the **MetadataRetrievalNode** class; see the **Microsoft.ServiceModel.Channels** managed reference at [http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566).</span></span>  
  
### <a name="metadata-node-ids"></a><span data-ttu-id="bc455-130">中繼資料節點識別碼</span><span class="sxs-lookup"><span data-stu-id="bc455-130">Metadata Node IDs</span></span>  
 <span data-ttu-id="bc455-131">配接器會將它的中繼資料組織為階層式樹狀結構的節點。</span><span class="sxs-lookup"><span data-stu-id="bc455-131">The adapter organizes its metadata as a hierarchical tree of nodes.</span></span> <span data-ttu-id="bc455-132">此樹狀結構中有兩種類型的中繼資料節點：</span><span class="sxs-lookup"><span data-stu-id="bc455-132">Within this tree structure there are two types of metadata nodes:</span></span>  
  
-   <span data-ttu-id="bc455-133">**作業節點**代表 SAP 成品會呈現配接器的作業。</span><span class="sxs-lookup"><span data-stu-id="bc455-133">**Operation nodes** represent operations that the adapter surfaces on SAP artifacts.</span></span> <span data-ttu-id="bc455-134">作業的節點是樹狀結構的分葉。</span><span class="sxs-lookup"><span data-stu-id="bc455-134">Operation nodes are the leaves of the tree.</span></span>  
  
-   <span data-ttu-id="bc455-135">**分類節點**代表 SAP 成品，並不會直接對應的 SAP 成品的群組給配接器上的作業。</span><span class="sxs-lookup"><span data-stu-id="bc455-135">**Category nodes** represent SAP artifacts and groupings of SAP artifacts that do not directly correspond to an operation on the adapter.</span></span> <span data-ttu-id="bc455-136">分類節點是樹狀結構中; 的分支它們包含其他分類節點和/或運算節點。</span><span class="sxs-lookup"><span data-stu-id="bc455-136">Category nodes are the branches of the tree; they contain other category nodes and/or operation nodes.</span></span> <span data-ttu-id="bc455-137">例如，RFC 功能群組或 SAP 商務物件會以類別目錄節點表示。</span><span class="sxs-lookup"><span data-stu-id="bc455-137">For example, RFC functional groups or SAP business objects are represented as category nodes.</span></span>  
  
 <span data-ttu-id="bc455-138">每個配接器所提出的中繼資料節點識別唯一的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="bc455-138">Each metadata node surfaced by the adapter is identified by a unique node ID.</span></span> <span data-ttu-id="bc455-139">與節點有關的中繼資料顯示配接器的識別碼的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。</span><span class="sxs-lookup"><span data-stu-id="bc455-139">For more information about the metadata node IDs surfaced by the adapter, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span> <span data-ttu-id="bc455-140">您可以使用這些節點識別碼來指定當您使用的目標 SAP 成品**IMetadataRetrievalContract**介面，以瀏覽、 搜尋及擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bc455-140">You use these node IDs to specify target SAP artifacts when you use the **IMetadataRetrievalContract** interface to browse, search, and retrieve metadata.</span></span> <span data-ttu-id="bc455-141">您可以使用中定義的常數`Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants`和`Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants`來協助您建構中繼資料節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="bc455-141">You can use the constants defined in `Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants` and `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` to help you construct metadata node IDs.</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="bc455-142">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="bc455-142">Binding Properties</span></span>  
 <span data-ttu-id="bc455-143">不論您是使用**IMetadataRetrievalContract**通道或**IMetadataRetrievalClient**若要使用中繼資料，您必須指定**SAPBinding**當您建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc455-143">Whether you use an **IMetadataRetrievalContract** channel or an **IMetadataRetrievalClient** to work with metadata, you must specify an **SAPBinding** when you create the instance.</span></span>  
  
 <span data-ttu-id="bc455-144">有幾個會影響配接器如何產生中繼資料的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="bc455-144">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="bc455-145">這些屬性如下：</span><span class="sxs-lookup"><span data-stu-id="bc455-145">These properties are:</span></span>  
  
-   <span data-ttu-id="bc455-146">**GenerateFlatfileCompatibleIdocSchema**</span><span class="sxs-lookup"><span data-stu-id="bc455-146">**GenerateFlatfileCompatibleIdocSchema**</span></span>  
  
-   <span data-ttu-id="bc455-147">**ReceiveIDocFormat**</span><span class="sxs-lookup"><span data-stu-id="bc455-147">**ReceiveIDocFormat**</span></span>  
  
-   <span data-ttu-id="bc455-148">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="bc455-148">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="bc455-149">**FlatFileSegmentIndicator**</span><span class="sxs-lookup"><span data-stu-id="bc455-149">**FlatFileSegmentIndicator**</span></span>  
  
 <span data-ttu-id="bc455-150">您應該確定這些繫結屬性設定為需要您的應用程式之前開啟中繼資料擷取物件的值。</span><span class="sxs-lookup"><span data-stu-id="bc455-150">You should ensure that these binding properties are set to the values required for your application before you open the metadata retrieval object.</span></span> <span data-ttu-id="bc455-151">如需有關 SAP 配接器繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bc455-151">For more information about the SAP adapter binding properties, see [Read about  BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
### <a name="browsing-metadata-nodes"></a><span data-ttu-id="bc455-152">瀏覽中繼資料節點</span><span class="sxs-lookup"><span data-stu-id="bc455-152">Browsing Metadata Nodes</span></span>  
 <span data-ttu-id="bc455-153">您使用**瀏覽**方法以傳回所包含的所有中繼資料節點中的父節點。</span><span class="sxs-lookup"><span data-stu-id="bc455-153">You use the **Browse** method to return all the metadata nodes that are contained in a parent node.</span></span> <span data-ttu-id="bc455-154">下列範例會瀏覽的 SAP 系統上的前三個 RFC 功能群組。</span><span class="sxs-lookup"><span data-stu-id="bc455-154">The following example browses for the first three RFC functional groups on the SAP system.</span></span> <span data-ttu-id="bc455-155">在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。</span><span class="sxs-lookup"><span data-stu-id="bc455-155">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc455-156">您只能瀏覽類別節點;您無法瀏覽作業節點。</span><span class="sxs-lookup"><span data-stu-id="bc455-156">You can only browse category nodes; you cannot browse operation nodes.</span></span>  
  
### <a name="searching-for-metadata-nodes"></a><span data-ttu-id="bc455-157">搜尋中繼資料節點</span><span class="sxs-lookup"><span data-stu-id="bc455-157">Searching for Metadata Nodes</span></span>  
 <span data-ttu-id="bc455-158">您使用**搜尋**方法來執行搜尋的父節點所包含的節點。</span><span class="sxs-lookup"><span data-stu-id="bc455-158">You use the **Search** method to perform a search for nodes contained by a parent node.</span></span> <span data-ttu-id="bc455-159">您可以指定星號 (\*) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bc455-159">You can specify the asterisk (\*) wildcard character.</span></span> <span data-ttu-id="bc455-160">此字元會比對零個或多個字元。</span><span class="sxs-lookup"><span data-stu-id="bc455-160">This character matches zero or more characters.</span></span> <span data-ttu-id="bc455-161">下列範例會顯示搜尋所有包含字串"BAPI"的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="bc455-161">The following example shows a search for all RFCs that contain the string "BAPI".</span></span> <span data-ttu-id="bc455-162">在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。</span><span class="sxs-lookup"><span data-stu-id="bc455-162">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// Search for all nodes that contain "BAPI" under the RFC node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI*", int.MaxValue);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc455-163">搜尋只支援一組有限的節點上。</span><span class="sxs-lookup"><span data-stu-id="bc455-163">Searching is only supported on a limited set of nodes.</span></span> <span data-ttu-id="bc455-164">如需有關支援搜尋的節點，以及搜尋運算式中支援的萬用字元的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。</span><span class="sxs-lookup"><span data-stu-id="bc455-164">For more information about the nodes on which search is supported and about the wildcard character supported in search expressions, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a><span data-ttu-id="bc455-165">擷取作業的中繼資料 (WSDL)</span><span class="sxs-lookup"><span data-stu-id="bc455-165">Retrieving Metadata (WSDL) for Operations</span></span>  
 <span data-ttu-id="bc455-166">您使用**GetMetadata**方法來擷取群組的作業節點的服務描述 （WSDL 文件）。</span><span class="sxs-lookup"><span data-stu-id="bc455-166">You use the **GetMetadata** method to retrieve a service description (WSDL document) for a group of operation nodes.</span></span> <span data-ttu-id="bc455-167">下列範例會擷取 BAPI_TRANSACTION_COMMIT RFC 的服務描述。</span><span class="sxs-lookup"><span data-stu-id="bc455-167">The following example retrieves a service description for the BAPI_TRANSACTION_COMMIT RFC.</span></span> <span data-ttu-id="bc455-168">在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。</span><span class="sxs-lookup"><span data-stu-id="bc455-168">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span> <span data-ttu-id="bc455-169">請注意，運算節點的節點識別碼相當於該作業的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="bc455-169">Note that the node ID for an operation node is equivalent to the message action for that operation.</span></span>  
  
```  
// Get a WSDL document that specifies a contract that contains the  
// BAPI_TRANSACTION_COMMIT operation.  
MetadataRetrievalNode[] nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
nodes[0].IsOperation = true;  
  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc455-170">您只需要指定作業中的節點**GetMetadata**方法。</span><span class="sxs-lookup"><span data-stu-id="bc455-170">You should only specify operation nodes in the **GetMetadata** method.</span></span>  
  
### <a name="using-a-metadataretrievalclient"></a><span data-ttu-id="bc455-171">使用 MetadataRetrievalClient</span><span class="sxs-lookup"><span data-stu-id="bc455-171">Using a MetadataRetrievalClient</span></span>  
 <span data-ttu-id="bc455-172">建立和使用**MetadataRetrievalClient**是非常類似任何其他 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="bc455-172">Creating and using a **MetadataRetrievalClient** is much the same as any other WCF client.</span></span> <span data-ttu-id="bc455-173">您指定端點和執行個體建立用戶端**SAPBinding**。</span><span class="sxs-lookup"><span data-stu-id="bc455-173">You create the client by specifying an endpoint and an instance of **SAPBinding**.</span></span> <span data-ttu-id="bc455-174">以宣告方式在組態或命令式程式碼中，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="bc455-174">You can do this either declaratively in configuration or imperatively in your code.</span></span> <span data-ttu-id="bc455-175">然後叫用的方法**MetadataRetrievalClient**瀏覽，搜尋，然後從配接器擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bc455-175">You then invoke the methods of the **MetadataRetrievalClient** to browse, search, and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="bc455-176">下列範例示範如何使用**MetadataRetrievalClient**來瀏覽，搜尋和擷取中繼資料從[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc455-176">The following example shows how to use a **MetadataRetrievalClient** to browse, search, and retrieve metadata from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace SapMetaDataBrowseClient  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console.  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //Write all the nodes returned to the console.  
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
            MetadataRetrievalClient browser = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // Create a binding  
                SAPBinding binding = new SAPBinding();  
  
                EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
                browser = new MetadataRetrievalClient(binding, address);  
                browser.ClientCredentials.UserName.UserName = "YourUserName";  
                browser.ClientCredentials.UserName.Password = "YourPassword";  
                browser.Open();  
  
                // Return the nodes directly under the root.  
                // The parameters are the parent node ID, the start index, and the maximum number  
                // of nodes to return.  
                MetadataRetrievalNode[] nodes = browser.Browse(MetadataRetrievalNode.Root.NodeId, 0, int.MaxValue);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Return first 3 RFC group nodes.  
                nodes = browser.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
                nodeWriter.Write(String.Format("Browse results for the first {1} nodes of {0}:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, nodes.Length), nodes);  
  
                // Search for first 3 nodes that begin with "BAPI_TRANSACTION" under the RFC node.  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return.  
                nodes = browser.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI_TRANSACTION*", 3);  
                nodeWriter.Write(String.Format("Search results for \"*BAPI_TRANSACTION*\" under {0} node:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // found in the search and write it to a file.  
                // You could explicitly specify operations as in the following:  
                //    nodes[0] = new MetadataRetrievalNode();  
                //    nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
                //    nodes[0].IsOperation = true;  
                // Note that the operation NodeId is equivalent to the message action.  
                System.Web.Services.Description.ServiceDescription description = browser.GetMetadata(nodes);  
                description.Write("SampleContract.wsdl");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (browser != null)  
                {  
                    if (browser.State == CommunicationState.Opened)  
                        browser.Close();  
                    else  
                        browser.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="bc455-177">以下顯示在主控台上此程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="bc455-177">The following shows the output of this program on the console.</span></span> <span data-ttu-id="bc455-178">您可以看到每個方法所傳回的中繼資料擷取節點的結構。</span><span class="sxs-lookup"><span data-stu-id="bc455-178">You can see the structure of the metadata retrieval nodes returned for each method.</span></span> <span data-ttu-id="bc455-179">程式也會寫入 WSDL 文件描述的檔案搜尋傳回的節點所組成的服務合約。</span><span class="sxs-lookup"><span data-stu-id="bc455-179">The program also writes a WSDL document that describes a service contract consisting of the nodes returned by the search to a file.</span></span> <span data-ttu-id="bc455-180">（大部分的 SAP 安裝的服務描述會包含 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 作業）。</span><span class="sxs-lookup"><span data-stu-id="bc455-180">(For most SAP installations, the service description will contain the BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK operations.)</span></span>  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/BAPISECTION/000001  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = BAPI  
        Description = BAPI  
NodeId = http://Microsoft.LobServices.Sap/2007/03/IDOCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = IDOC  
        Description = IDOC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = RFC  
        Description = RFC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/TRFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = TRFC  
        Description = TRFC  
  
Browse results for the first 3 nodes of http://Microsoft.LobServices.Sap/2007/03  
/RFCSECTION/:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/A  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Asset Accounting  
        Description = Asset Accounting  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/S  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Basis  
        Description = Basis  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/B  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Business Information Warehouse  
        Description = Business Information Warehouse  
  
Search results for "*BAPI_TRANSACTION*" under http://Microsoft.LobServices.Sap/2  
007/03/RFCSECTION/ node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_COMMIT  
        Description = Execute external Commit when using BAPIs  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_ROLLBACK  
        Description = Execute external Rollback when using BAPIs  
  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a><span data-ttu-id="bc455-181">使用 IMetadataRetrievalContract 通道</span><span class="sxs-lookup"><span data-stu-id="bc455-181">Using an IMetadataRetrievalContract Channel</span></span>  
 <span data-ttu-id="bc455-182">您也可以建立**IMetadataRetrievalContract**通道，並接著使用這個通道來瀏覽、 搜尋及擷取中繼資料從配接器。</span><span class="sxs-lookup"><span data-stu-id="bc455-182">You can also create an **IMetadataRetrievalContract** channel and then use this channel to browse, search, and retrieve metadata from the adapter.</span></span> <span data-ttu-id="bc455-183">(方法簽章是不一樣**MetadataRetrievalClient**類別。)下列範例顯示如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="bc455-183">(The method signatures are the same as for the **MetadataRetrievalClient** class.) The following example shows how to do this.</span></span>  
  
```  
…  
//Create a binding and endpoint address.  
SAPBinding binding = new SAPBinding();  
EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "BAPI_TRANSACTION*", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc455-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc455-184">See Also</span></span>  
 [<span data-ttu-id="bc455-185">以程式設計方式從 SAP 擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="bc455-185">Retrieving Metadata Programmatically from SAP</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md)