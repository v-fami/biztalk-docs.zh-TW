---
title: 取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving in Visual Studio
- metadata
ms.assetid: d903b408-1144-4625-909d-710826e37769
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f1afec8c125d2350d7fa7706b523931a3c6bdfd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003447"
---
# <a name="get-metadata-for-oracle-database-operations-in-visual-studio"></a><span data-ttu-id="70ceb-102">取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="70ceb-102">Get metadata for Oracle Database operations in Visual Studio</span></span>
<span data-ttu-id="70ceb-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件。</span><span class="sxs-lookup"><span data-stu-id="70ceb-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter.</span></span>  
  
- <span data-ttu-id="70ceb-104">[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]而[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]適用於 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="70ceb-104">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] and the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] are available in BizTalk Server projects.</span></span> <span data-ttu-id="70ceb-105">您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]而[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="70ceb-105">You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution.</span></span> <span data-ttu-id="70ceb-106">如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱[使用 Oracle 資料庫配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="70ceb-106">For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)</span></span>  
  
- <span data-ttu-id="70ceb-107">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]用於非 BizTalk 的程式設計專案。</span><span class="sxs-lookup"><span data-stu-id="70ceb-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] is available in non-BizTalk programming projects.</span></span> <span data-ttu-id="70ceb-108">您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來開發使用 WCF 服務模型的方案時，產生 WCF 用戶端類別或 WCF 服務的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="70ceb-108">You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model.</span></span> <span data-ttu-id="70ceb-109">如需有關如何使用 WCF 服務模型開發解決方案的詳細資訊，請參閱 <<c0> [ 開發 Oracle 資料庫應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="70ceb-109">For more information about developing solutions with the WCF service model, see [Develop Oracle Database Applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).</span></span>  
  
  <span data-ttu-id="70ceb-110">所有這三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：</span><span class="sxs-lookup"><span data-stu-id="70ceb-110">All these three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
- <span data-ttu-id="70ceb-111">提供的 Microsoft Windows 介面，您可以透過它瀏覽，然後搜尋您想要使用您的方案中的作業。</span><span class="sxs-lookup"><span data-stu-id="70ceb-111">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
- <span data-ttu-id="70ceb-112">正在擷取這些目標作業的配接器所公開的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70ceb-112">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
- <span data-ttu-id="70ceb-113">轉換該中繼資料，這會以 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的解決方案 （BizTalk 專案的 XSD 訊息結構描述或針對 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="70ceb-113">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
  <span data-ttu-id="70ceb-114">本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ceb-114">This section provides instructions about how to use [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70ceb-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="70ceb-115">In This Section</span></span>  
  
-   [<span data-ttu-id="70ceb-116">連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務</span><span class="sxs-lookup"><span data-stu-id="70ceb-116">Connect to the Oracle Database in Visual Studio using the Consume Adapter Service</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md) 
  
-   [<span data-ttu-id="70ceb-117">瀏覽、 搜尋及取得 Oracle 資料庫作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="70ceb-117">Browse, search, and get metadata for Oracle Database operations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="70ceb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ceb-118">See Also</span></span>  
[<span data-ttu-id="70ceb-119">開發您的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="70ceb-119">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)