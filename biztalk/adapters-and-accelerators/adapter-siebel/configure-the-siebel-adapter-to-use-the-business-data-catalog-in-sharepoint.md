---
title: 設定 Siebel 配接器 Siebel 系統整合的商務資料目錄，而且 SharePoint |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49b575e8-5f33-4e6e-a914-95d357671ab5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d02e14b8c996acbfb07f9d422aee70cb0d94fa59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221934"
---
# <a name="configure-the-siebel-adapter-to-integrate-the-siebel-system-with-the-business-data-catalog-and-sharepoint"></a><span data-ttu-id="a720a-102">設定 Siebel 配接器 Siebel 系統整合的商務資料目錄和 SharePoint</span><span class="sxs-lookup"><span data-stu-id="a720a-102">Configure the Siebel Adapter to Integrate the Siebel System with the Business Data Catalog and SharePoint</span></span>
<span data-ttu-id="a720a-103">[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]包含[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]，如此就會產生特定 LOB 成品的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="a720a-103">The [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] includes the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)], which generates a WCF service for specific LOB artifacts.</span></span> <span data-ttu-id="a720a-104">例如 Microsoft Internet Information Services (IIS) 裝載環境中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="a720a-104">This WCF service is hosted in a hosting environment such as Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="a720a-105">商務資料目錄定義編輯器使用的 URL 取得 Web 服務描述語言 (WSDL) 的 WCF 服務中裝載 WCF 服務的位置。</span><span class="sxs-lookup"><span data-stu-id="a720a-105">The Business Data Catalog Definition Editor uses the URL where the WCF service is hosted to get the Web Services Description Language (WSDL) for the WCF service.</span></span> <span data-ttu-id="a720a-106">使用 WSDL，商務資料目錄定義編輯器中擷取可用的 WCF 服務的方法。</span><span class="sxs-lookup"><span data-stu-id="a720a-106">Using the WSDL, the Business Data Catalog Definition Editor extracts the methods available to the WCF service.</span></span> <span data-ttu-id="a720a-107">這些方法可以用來建立實體和實體之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="a720a-107">These methods can be used to establish entities and the association between the entities.</span></span>  
  
 <span data-ttu-id="a720a-108">商務資料目錄定義編輯器可協助您建立 Microsoft Office SharePoint Server 可以使用應用程式定義檔案 （XML 檔案）。</span><span class="sxs-lookup"><span data-stu-id="a720a-108">The Business Data Catalog Definition Editor helps you create an application definition file (an XML file) that Microsoft Office SharePoint Server can consume.</span></span> <span data-ttu-id="a720a-109">一旦應用程式定義檔匯入至 Microsoft Office SharePoint Server，您可以建立 Web 組件來呈現企業應用程式中的資訊。</span><span class="sxs-lookup"><span data-stu-id="a720a-109">Once the application definition file is imported to Microsoft Office SharePoint Server, you can create Web Parts to present the information from enterprise applications.</span></span> <span data-ttu-id="a720a-110">如需詳細資訊，請參閱 「 建立的 Web 組件 」 中[步驟 3： 建立 SharePoint 應用程式以擷取資料從 Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)中[教學課程 1： 呈現的資料從 Siebel 系統的 SharePoint 網站上](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="a720a-110">For more information, see “Creating Web Parts” in [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) in [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).</span></span>  
  
## <a name="tutorial"></a><span data-ttu-id="a720a-111">教學課程</span><span class="sxs-lookup"><span data-stu-id="a720a-111">Tutorial</span></span>  
 <span data-ttu-id="a720a-112">若要示範如何使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft Office SharePoint Server，[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]包含的教學課程，提供逐步指示，以提供從 SharePoint 網站上的 Siebel 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="a720a-112">To demonstrate how to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft Office SharePoint Server, the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] includes a tutorial that provides step-by-step instructions to present data from a Siebel system on a SharePoint site.</span></span> <span data-ttu-id="a720a-113">請參閱[教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="a720a-113">See [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a720a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a720a-114">See Also</span></span>  
 [<span data-ttu-id="a720a-115">搭配 SharePoint 使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="a720a-115">Use the Siebel Adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)