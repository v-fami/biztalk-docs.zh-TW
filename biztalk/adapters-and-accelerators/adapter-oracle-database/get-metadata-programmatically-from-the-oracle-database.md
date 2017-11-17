---
title: "以程式設計方式取得中繼資料，從 Oracle 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving programmatically from the Oracle database
ms.assetid: 28a55935-6078-41d0-abfa-ac86e9ca8471
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c36fcd6a791f1d960a4dd4dfd78ca199d2e49cb5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-programmatically-from-the-oracle-database"></a><span data-ttu-id="0923a-102">以程式設計方式從 Oracle 資料庫中取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="0923a-102">Get Metadata Programmatically from the Oracle Database</span></span>
<span data-ttu-id="0923a-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是自訂的 WCF 繫結會公開為 WCF 服務的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0923a-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a custom WCF binding that exposes an Oracle database as a WCF service.</span></span> <span data-ttu-id="0923a-104">配接器公開 Oracle 資料庫為自我描述的服務。也就是能夠發行中繼資料支援的作業有關的服務。</span><span class="sxs-lookup"><span data-stu-id="0923a-104">The adapter exposes the Oracle database as a self-describing service; that is, a service that is capable of publishing metadata about the operations that it supports.</span></span> <span data-ttu-id="0923a-105">中繼資料描述至 WCF 服務; 的邏輯介面也就是服務合約、 訊息和訊息結構描述必須用來與服務互動。</span><span class="sxs-lookup"><span data-stu-id="0923a-105">Metadata describes the logical interface to a WCF service; that is, the service contract, messages, and message schemas that must be used to interact with the service.</span></span>  
  
 <span data-ttu-id="0923a-106">此中繼資料工具會使用這類：</span><span class="sxs-lookup"><span data-stu-id="0923a-106">This metadata is used by tools such as:</span></span>  
  
-   <span data-ttu-id="0923a-107">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 managed 程式碼表示法的服務合約，以及</span><span class="sxs-lookup"><span data-stu-id="0923a-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate managed code representations of the service contract, and</span></span>  
  
-   <span data-ttu-id="0923a-108">[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="0923a-108">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate message schemas.</span></span>  
  
 <span data-ttu-id="0923a-109">不過，您也可以擷取中繼資料以程式設計方式從配接器。</span><span class="sxs-lookup"><span data-stu-id="0923a-109">However, you can also retrieve metadata programmatically from the adapter.</span></span> <span data-ttu-id="0923a-110">比方說，您可能想要執行此作業以建立要在現有的應用程式中使用的自訂中繼資料擷取工具。</span><span class="sxs-lookup"><span data-stu-id="0923a-110">For example, you might want to do this to create a custom metadata retrieval tool to use in an existing application.</span></span>  
  
 <span data-ttu-id="0923a-111">配接器會將發佈到兩個端點的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="0923a-111">The adapter publishes metadata through two endpoints:</span></span>  
  
-   <span data-ttu-id="0923a-112">WS 中繼資料交換 (MEX) 端點。</span><span class="sxs-lookup"><span data-stu-id="0923a-112">A WS-Metadata Exchange (MEX) endpoint.</span></span> <span data-ttu-id="0923a-113">WCF 會自動提供 MEX 端點，所有的 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="0923a-113">WCF automatically provides a MEX endpoint for all WCF bindings.</span></span> <span data-ttu-id="0923a-114">您可以使用中繼資料交換來擷取中繼資料為基礎的 Oracle 資料庫上的介面卡所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="0923a-114">You can use metadata exchange to retrieve metadata for operations supported by the adapter on the underlying Oracle database.</span></span>  
  
-   <span data-ttu-id="0923a-115">**IMetadataRetrievalContract**端點。</span><span class="sxs-lookup"><span data-stu-id="0923a-115">An **IMetadataRetrievalContract** endpoint.</span></span> <span data-ttu-id="0923a-116">**IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0923a-116">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> <span data-ttu-id="0923a-117">它將分類多個邏輯層級的 Oracle 資料庫成品並呈現為樹狀結構的中繼資料節點。</span><span class="sxs-lookup"><span data-stu-id="0923a-117">It categorizes Oracle database artifacts at multiple logical levels and presents them as a tree of metadata nodes.</span></span> <span data-ttu-id="0923a-118">您可以使用所公開的方法**IMetadataRetrievalContract**瀏覽和搜尋此樹狀結構的節點，並傳回您感興趣的作業的中繼資料的介面。</span><span class="sxs-lookup"><span data-stu-id="0923a-118">You can use methods exposed by the **IMetadataRetrievalContract** interface to browse and search the nodes of this tree and to return metadata for operations in which you are interested.</span></span>  
  
 <span data-ttu-id="0923a-119">本節中的主題描述如何使用 MEX 和**IMetadataRetrievalContract**從配接器，以程式設計方式擷取中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="0923a-119">The topics in this section describe how to use MEX and **IMetadataRetrievalContract** endpoints to retrieve metadata programmatically from the adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0923a-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="0923a-120">In This Section</span></span>  
  
-   [<span data-ttu-id="0923a-121">取得使用 Ws-metadata Exchange Oracle 資料庫中的中繼資料</span><span class="sxs-lookup"><span data-stu-id="0923a-121">Get Metadata Using WS-Metadata Exchange in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-using-ws-metadata-exchange-in-oracle-database.md)  
  
-   [<span data-ttu-id="0923a-122">使用 IMetadataRetrievalContract Oracle 資料庫中取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="0923a-122">Get Metadata in Oracle Database Using IMetadataRetrievalContract</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-in-oracle-database-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a><span data-ttu-id="0923a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0923a-123">See Also</span></span>  
[<span data-ttu-id="0923a-124">開發應用程式的 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="0923a-124">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)