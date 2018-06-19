---
title: 教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MOSS, creating an application in
- Microsoft Office SharePoint Server
- MOSS
- Microsoft Office SharePoint Server, creating an application in
ms.assetid: 6e31c365-446c-4fe1-8538-fa6c869eed63
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdc3ea5e41600aebcef1fda933735c418dec78c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217422"
---
# <a name="tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site"></a><span data-ttu-id="11233-102">教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料</span><span class="sxs-lookup"><span data-stu-id="11233-102">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>
<span data-ttu-id="11233-103">本教學課程提供詳細的指示使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft Office SharePoint Server，在 SharePoint 網站上呈現從 SAP 系統的商務資料。</span><span class="sxs-lookup"><span data-stu-id="11233-103">This tutorial provides detailed instructions on using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft Office SharePoint Server to present business data from an SAP system on a SharePoint portal.</span></span> <span data-ttu-id="11233-104">若要示範如何使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]Office SharePoint Server，請考慮在任何企業中最常見的兩個實體： 客戶和銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="11233-104">To demonstrate how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Office SharePoint Server, consider the two most common entities in any business: customers and sales orders.</span></span> <span data-ttu-id="11233-105">在此範例中，建立應用程式中使用 Office SharePoint Server[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="11233-105">In this example, an application is created in Office SharePoint Server, which uses the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to do the following:</span></span>  
  
-   <span data-ttu-id="11233-106">從搜尋字串為基礎的 SAP 系統中擷取客戶清單。</span><span class="sxs-lookup"><span data-stu-id="11233-106">Retrieve a list of customers from the SAP system based on a search string.</span></span>  
  
-   <span data-ttu-id="11233-107">從選取客戶 清單 和 顯示詳細資料的客戶。</span><span class="sxs-lookup"><span data-stu-id="11233-107">Select a customer from the list and present details for the customer.</span></span>  
  
-   <span data-ttu-id="11233-108">擷取所選客戶的銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="11233-108">Retrieve the sales orders for the selected customer.</span></span>  
  
 <span data-ttu-id="11233-109">若要從 SAP 系統中擷取客戶資料，此範例會使用 SD_RFC_CUSTOMER_GET RFC。</span><span class="sxs-lookup"><span data-stu-id="11233-109">To extract customer data from an SAP system, the example uses the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="11233-110">若要擷取特定客戶的銷售訂單的相關資訊，它會使用 BAPI_SALESORDER_GETLIST RFC。</span><span class="sxs-lookup"><span data-stu-id="11233-110">To extract information about sales orders for a specific customer, it uses the BAPI_SALESORDER_GETLIST RFC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11233-111">某些版本的 SAP 系統公開 （expose) 而不是 SD_RFC_CUSTOMER_GET RFC_CUSTOMER_GET RFC。</span><span class="sxs-lookup"><span data-stu-id="11233-111">Some versions of the SAP system expose an RFC_CUSTOMER_GET RFC instead of SD_RFC_CUSTOMER_GET.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11233-112">本教學課程之前，確定您已安裝使用的所有必要條件[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]Office SharePoint server。</span><span class="sxs-lookup"><span data-stu-id="11233-112">Before proceeding with the tutorial, make sure you have installed all the prerequisites for using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Office SharePoint Server.</span></span> <span data-ttu-id="11233-113">如需有關必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南 》，通常安裝在 c: / Program 檔案/Microsoft  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] /文件。</span><span class="sxs-lookup"><span data-stu-id="11233-113">For more information about the prerequisites, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide, typically installed at C:/Program Files/Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]/Documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11233-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="11233-114">In This Section</span></span>  
  
-   [<span data-ttu-id="11233-115">步驟 1： 將 SAP 成品發佈為 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="11233-115">Step 1: Publish the SAP Artifacts as a WCF Service</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)  
  
-   [<span data-ttu-id="11233-116">步驟 2： 建立應用程式定義檔 SAP 成品</span><span class="sxs-lookup"><span data-stu-id="11233-116">Step 2: Create an Application Definition File for the SAP Artifacts</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)  
  
-   [<span data-ttu-id="11233-117">步驟 3： 建立 SharePoint 應用程式來擷取 SAP 資料</span><span class="sxs-lookup"><span data-stu-id="11233-117">Step 3: Create a SharePoint Application to Retrieve Data from SAP</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)  
  
-   [<span data-ttu-id="11233-118">步驟 4： 測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="11233-118">Step 4: Test Your SharePoint Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md)  
  
## <a name="see-also"></a><span data-ttu-id="11233-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11233-119">See Also</span></span>  
 [<span data-ttu-id="11233-120">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="11233-120">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)