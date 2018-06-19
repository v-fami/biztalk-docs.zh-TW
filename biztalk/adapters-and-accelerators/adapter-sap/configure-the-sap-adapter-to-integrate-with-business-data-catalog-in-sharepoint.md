---
title: 設定 SAP 配接器將 SAP 整合商務資料目錄，而且 SharePoint |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ec105c9-0ced-4a45-bc0d-eb72c1ef5d9d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9de78148af79cc8668d01c220799187770c7df4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216534"
---
# <a name="configure-the-sap-adapter-to-integrate-sap-with-the-business-data-catalog-and-sharepoint"></a><span data-ttu-id="2954c-102">設定 SAP 配接器將 SAP 整合商務資料目錄和 SharePoint</span><span class="sxs-lookup"><span data-stu-id="2954c-102">Configure the SAP Adapter to Integrate SAP with the Business Data Catalog and SharePoint</span></span>
<span data-ttu-id="2954c-103">[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]包含[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]，如此就會產生特定 LOB 成品的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="2954c-103">The [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] includes the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)], which generates a WCF service for specific LOB artifacts.</span></span> <span data-ttu-id="2954c-104">例如 Microsoft Internet Information Services (IIS) 裝載環境中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="2954c-104">This WCF service is hosted in a hosting environment such as Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="2954c-105">商務資料目錄定義編輯器使用的 URL 取得 Web 服務描述語言 (WSDL) 的 WCF 服務中裝載 WCF 服務的位置。</span><span class="sxs-lookup"><span data-stu-id="2954c-105">The Business Data Catalog Definition Editor uses the URL where the WCF service is hosted to get the Web Services Description Language (WSDL) for the WCF service.</span></span> <span data-ttu-id="2954c-106">使用 WSDL，商務資料目錄定義編輯器中擷取可用的 WCF 服務的方法。</span><span class="sxs-lookup"><span data-stu-id="2954c-106">Using the WSDL, the Business Data Catalog Definition Editor extracts the methods available to the WCF service.</span></span> <span data-ttu-id="2954c-107">這些方法可以用來建立實體和實體之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="2954c-107">These methods can be used to establish entities and the association between the entities.</span></span>  
  
 <span data-ttu-id="2954c-108">商務資料目錄定義編輯器可協助您建立 Microsoft Office SharePoint Server 可以使用應用程式定義檔案 （XML 檔案）。</span><span class="sxs-lookup"><span data-stu-id="2954c-108">The Business Data Catalog Definition Editor helps you create an application definition file (an XML file) that Microsoft Office SharePoint Server can consume.</span></span> <span data-ttu-id="2954c-109">一旦應用程式定義檔匯入至 Microsoft Office SharePoint Server，您可以建立 Web 組件來呈現企業應用程式中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2954c-109">Once the application definition file is imported to Microsoft Office SharePoint Server, you can create Web Parts to present the information from enterprise applications.</span></span> <span data-ttu-id="2954c-110">如需詳細資訊，請參閱 「 建立的 Web 組件 」 中[步驟 3： 建立 SharePoint 應用程式以擷取資料從 SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)中[教學課程 1： 從 SharePoint 網站上的 SAP 系統的呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="2954c-110">For more information, see “Creating Web Parts” in [Step 3: Create a SharePoint Application to Retrieve Data from SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) in [Tutorial 1: Presenting Data from an SAP System on a SharePoint Site](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).</span></span>  
  
## <a name="tutorial"></a><span data-ttu-id="2954c-111">教學課程</span><span class="sxs-lookup"><span data-stu-id="2954c-111">Tutorial</span></span>  
 <span data-ttu-id="2954c-112">若要示範如何使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft Office SharePoint Server，[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]包含的教學課程，提供逐步指示，以提供從 SharePoint 網站上的 SAP 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="2954c-112">To demonstrate how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft Office SharePoint Server, the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] includes a tutorial that provides step-by-step instructions to present data from an SAP system on a SharePoint site.</span></span> <span data-ttu-id="2954c-113">請參閱[教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="2954c-113">See [Tutorial 1: Presenting Data from an SAP System on a SharePoint Site](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2954c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2954c-114">See Also</span></span>  
[<span data-ttu-id="2954c-115">搭配 SharePoint 使用 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="2954c-115">Use the SAP Adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)