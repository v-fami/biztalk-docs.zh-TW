---
title: 以程式設計方式取得中繼資料，從 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving programmatically from the Oracle database
ms.assetid: 28a55935-6078-41d0-abfa-ac86e9ca8471
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2380e58605cf401e7ed1138b078d19d5279144f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972871"
---
# <a name="get-metadata-programmatically-from-the-oracle-database"></a><span data-ttu-id="2ba70-102">從 Oracle 資料庫，以程式設計方式取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="2ba70-102">Get Metadata Programmatically from the Oracle Database</span></span>
<span data-ttu-id="2ba70-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是自訂的 WCF 繫結會公開為 WCF 服務的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ba70-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a custom WCF binding that exposes an Oracle database as a WCF service.</span></span> <span data-ttu-id="2ba70-104">配接器會將 Oracle 資料庫公開為自我描述的服務;也就是一項服務，能夠支援之作業相關的中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="2ba70-104">The adapter exposes the Oracle database as a self-describing service; that is, a service that is capable of publishing metadata about the operations that it supports.</span></span> <span data-ttu-id="2ba70-105">中繼資料描述的 WCF 服務; 的邏輯介面也就是服務合約、 訊息和訊息結構描述，必須用來與服務互動。</span><span class="sxs-lookup"><span data-stu-id="2ba70-105">Metadata describes the logical interface to a WCF service; that is, the service contract, messages, and message schemas that must be used to interact with the service.</span></span>  
  
 <span data-ttu-id="2ba70-106">此中繼資料工具會使用這類：</span><span class="sxs-lookup"><span data-stu-id="2ba70-106">This metadata is used by tools such as:</span></span>  
  
- <span data-ttu-id="2ba70-107">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 managed 程式碼表示法的服務合約，以及</span><span class="sxs-lookup"><span data-stu-id="2ba70-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate managed code representations of the service contract, and</span></span>  
  
- <span data-ttu-id="2ba70-108">[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="2ba70-108">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate message schemas.</span></span>  
  
  <span data-ttu-id="2ba70-109">不過，您也可以擷取中繼資料以程式設計方式從配接器。</span><span class="sxs-lookup"><span data-stu-id="2ba70-109">However, you can also retrieve metadata programmatically from the adapter.</span></span> <span data-ttu-id="2ba70-110">比方說，您可能會想這麼做可以建立自訂的中繼資料擷取工具，將現有的應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="2ba70-110">For example, you might want to do this to create a custom metadata retrieval tool to use in an existing application.</span></span>  
  
  <span data-ttu-id="2ba70-111">配接器會發行透過兩個端點的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="2ba70-111">The adapter publishes metadata through two endpoints:</span></span>  
  
- <span data-ttu-id="2ba70-112">WS 中繼資料交換 (MEX) 端點。</span><span class="sxs-lookup"><span data-stu-id="2ba70-112">A WS-Metadata Exchange (MEX) endpoint.</span></span> <span data-ttu-id="2ba70-113">WCF 會自動提供所有的 WCF 繫結 MEX 端點。</span><span class="sxs-lookup"><span data-stu-id="2ba70-113">WCF automatically provides a MEX endpoint for all WCF bindings.</span></span> <span data-ttu-id="2ba70-114">您可以使用中繼資料交換來擷取中繼資料為基礎的 Oracle 資料庫配接器所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="2ba70-114">You can use metadata exchange to retrieve metadata for operations supported by the adapter on the underlying Oracle database.</span></span>  
  
- <span data-ttu-id="2ba70-115">**IMetadataRetrievalContract**端點。</span><span class="sxs-lookup"><span data-stu-id="2ba70-115">An **IMetadataRetrievalContract** endpoint.</span></span> <span data-ttu-id="2ba70-116">**IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ba70-116">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> <span data-ttu-id="2ba70-117">它將多個邏輯層級的 Oracle 資料庫成品的分類，並將它們呈現為樹狀結構的中繼資料節點。</span><span class="sxs-lookup"><span data-stu-id="2ba70-117">It categorizes Oracle database artifacts at multiple logical levels and presents them as a tree of metadata nodes.</span></span> <span data-ttu-id="2ba70-118">您可以使用所公開的方法**IMetadataRetrievalContract**介面瀏覽和搜尋此樹狀結構的節點，並傳回您感興趣的作業的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2ba70-118">You can use methods exposed by the **IMetadataRetrievalContract** interface to browse and search the nodes of this tree and to return metadata for operations in which you are interested.</span></span>  
  
  <span data-ttu-id="2ba70-119">在本節中的主題描述如何使用 MEX 並**IMetadataRetrievalContract**從配接器，以程式設計方式擷取中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="2ba70-119">The topics in this section describe how to use MEX and **IMetadataRetrievalContract** endpoints to retrieve metadata programmatically from the adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ba70-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="2ba70-120">In This Section</span></span>  
  
-   [<span data-ttu-id="2ba70-121">Oracle 資料庫中使用 Ws-metadata 交換取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="2ba70-121">Get Metadata Using WS-Metadata Exchange in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-using-ws-metadata-exchange-in-oracle-database.md)  
  
-   [<span data-ttu-id="2ba70-122">在 Oracle 資料庫中使用 IMetadataRetrievalContract 取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="2ba70-122">Get Metadata in Oracle Database Using IMetadataRetrievalContract</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-in-oracle-database-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ba70-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ba70-123">See Also</span></span>  
[<span data-ttu-id="2ba70-124">開發您的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="2ba70-124">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)