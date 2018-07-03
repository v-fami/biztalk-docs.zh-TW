---
title: 從 SAP，以程式設計方式取得中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IMetadataRetrievalContract endpoint
- metadata, retrieving programmatically
- WS-Metadata Exchange (MEX) endpoint
ms.assetid: 8d75332e-c103-4bd5-a9a2-56d21747a04e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0bf41b8213afd1c1af00c113e4a5406e6289dac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013847"
---
# <a name="get-metadata-programmatically-from-sap"></a><span data-ttu-id="955fd-102">從 SAP，以程式設計方式取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="955fd-102">Get Metadata Programmatically from SAP</span></span>
<span data-ttu-id="955fd-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是自訂的 WCF 繫結會公開為 WCF 服務的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="955fd-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a custom WCF binding that exposes an SAP system as a WCF service.</span></span> <span data-ttu-id="955fd-104">配接器會將 SAP 系統公開為自我描述的服務;也就是一項服務，能夠支援之作業相關的中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="955fd-104">The adapter exposes the SAP system as a self-describing service; that is, a service that is capable of publishing metadata about the operations that it supports.</span></span> <span data-ttu-id="955fd-105">中繼資料描述的 WCF 服務; 的邏輯介面也就是服務合約、 訊息和訊息結構描述，必須用來與服務互動。</span><span class="sxs-lookup"><span data-stu-id="955fd-105">Metadata describes the logical interface to a WCF service; that is, the service contract, messages, and message schemas that must be used to interact with the service.</span></span>  
  
 <span data-ttu-id="955fd-106">此中繼資料工具會使用這類：</span><span class="sxs-lookup"><span data-stu-id="955fd-106">This metadata is used by tools such as:</span></span>  
  
- <span data-ttu-id="955fd-107">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 managed 程式碼表示法的服務合約，以及</span><span class="sxs-lookup"><span data-stu-id="955fd-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate managed code representations of the service contract, and</span></span>  
  
- <span data-ttu-id="955fd-108">[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="955fd-108">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate message schemas.</span></span>  
  
  <span data-ttu-id="955fd-109">不過，您也可以擷取中繼資料以程式設計方式從配接器。</span><span class="sxs-lookup"><span data-stu-id="955fd-109">However, you can also retrieve metadata programmatically from the adapter.</span></span> <span data-ttu-id="955fd-110">比方說，您可能會想這麼做可以建立自訂的中繼資料擷取工具，將現有的應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="955fd-110">For example, you might want to do this to create a custom metadata retrieval tool to use in an existing application.</span></span>  
  
  <span data-ttu-id="955fd-111">配接器會發行透過兩個端點的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="955fd-111">The adapter publishes metadata through two endpoints:</span></span>  
  
- <span data-ttu-id="955fd-112">WS 中繼資料交換 (MEX) 端點。</span><span class="sxs-lookup"><span data-stu-id="955fd-112">A WS-Metadata Exchange (MEX) endpoint.</span></span> <span data-ttu-id="955fd-113">WCF 會自動提供所有的 WCF 繫結 MEX 端點。</span><span class="sxs-lookup"><span data-stu-id="955fd-113">WCF automatically provides a MEX endpoint for all WCF bindings.</span></span> <span data-ttu-id="955fd-114">您可以使用中繼資料交換來擷取中繼資料為基礎的 SAP 系統上的介面卡所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="955fd-114">You can use metadata exchange to retrieve metadata for operations supported by the adapter on the underlying SAP system.</span></span>  
  
- <span data-ttu-id="955fd-115">**IMetadataRetrievalContract**端點。</span><span class="sxs-lookup"><span data-stu-id="955fd-115">An **IMetadataRetrievalContract** endpoint.</span></span> <span data-ttu-id="955fd-116">**IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="955fd-116">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> <span data-ttu-id="955fd-117">它將多個邏輯層級的 SAP 系統成品的分類，並將它們呈現為樹狀結構的中繼資料節點。</span><span class="sxs-lookup"><span data-stu-id="955fd-117">It categorizes SAP system artifacts at multiple logical levels and presents them as a tree of metadata nodes.</span></span> <span data-ttu-id="955fd-118">您可以使用所公開的方法**IMetadataRetrievalContract**介面瀏覽和搜尋此樹狀結構的節點，並傳回您感興趣的作業的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="955fd-118">You can use methods exposed by the **IMetadataRetrievalContract** interface to browse and search the nodes of this tree and to return metadata for operations in which you are interested.</span></span>  
  
  <span data-ttu-id="955fd-119">在本節中的主題描述如何使用 MEX 並**IMetadataRetrievalContract**從配接器，以程式設計方式擷取中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="955fd-119">The topics in this section describe how to use MEX and **IMetadataRetrievalContract** endpoints to retrieve metadata programmatically from the adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="955fd-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="955fd-120">In This Section</span></span>  
  
-   [<span data-ttu-id="955fd-121">使用 Ws-metadata Exchange 在 SAP 中擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="955fd-121">Retrieving Metadata Using WS-Metadata Exchange in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-using-ws-metadata-exchange-in-sap.md)  
  
-   [<span data-ttu-id="955fd-122">使用 IMetadataRetrievalContract SAP 中擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="955fd-122">Retrieving Metadata in SAP Using IMetadataRetrievalContract</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a><span data-ttu-id="955fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="955fd-123">See Also</span></span>  
[<span data-ttu-id="955fd-124">開發您的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="955fd-124">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)