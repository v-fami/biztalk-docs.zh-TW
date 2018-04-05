---
title: 取得 Visual Studio 中的 Siebel 作業的中繼資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving for Siebel operations in Visual Studio
ms.assetid: 63643942-6497-4891-ad7d-34b1df9acbc1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30935631052adf4c455e730c476104b54a6a352b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-siebel-operations-in-visual-studio"></a><span data-ttu-id="6b69c-102">取得 Visual Studio 中的 Siebel 作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="6b69c-102">Get Metadata for Siebel Operations in Visual Studio</span></span>
<span data-ttu-id="6b69c-103">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]提供兩個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件。</span><span class="sxs-lookup"><span data-stu-id="6b69c-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] provides two [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter.</span></span>  
  
-   <span data-ttu-id="6b69c-104">[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]用於 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="6b69c-104">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] is available in BizTalk Server projects.</span></span> <span data-ttu-id="6b69c-105">您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="6b69c-105">You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution.</span></span> <span data-ttu-id="6b69c-106">如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 BizTalk 應用程式使用 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6b69c-106">For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).</span></span>
  
-   <span data-ttu-id="6b69c-107">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]用於非 BizTalk 開發專案。</span><span class="sxs-lookup"><span data-stu-id="6b69c-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] is available in non-BizTalk programming projects.</span></span> <span data-ttu-id="6b69c-108">您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端類別或 WCF 服務的回呼介面，當您開發使用 WCF 服務模型的解決方案。</span><span class="sxs-lookup"><span data-stu-id="6b69c-108">You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model.</span></span> <span data-ttu-id="6b69c-109">如需有關開發 WCF 服務模型的方案的詳細資訊，請參閱[開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6b69c-109">For more information about developing solutions with the WCF service model, see [Develop Siebel applications using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="6b69c-110">這兩種[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：</span><span class="sxs-lookup"><span data-stu-id="6b69c-110">Both of these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="6b69c-111">提供的 Microsoft Windows 介面，您可以瀏覽和搜尋您想要使用您的方案中的作業。</span><span class="sxs-lookup"><span data-stu-id="6b69c-111">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="6b69c-112">正在擷取這些目標作業的配接器所公開的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6b69c-112">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="6b69c-113">轉換的中繼資料，這表示做為 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的方案 （BizTalk 專案的 XSD 訊息結構描述或 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="6b69c-113">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="6b69c-114">本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6b69c-114">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="6b69c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b69c-115">See Also</span></span>  
[<span data-ttu-id="6b69c-116">開發 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="6b69c-116">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)