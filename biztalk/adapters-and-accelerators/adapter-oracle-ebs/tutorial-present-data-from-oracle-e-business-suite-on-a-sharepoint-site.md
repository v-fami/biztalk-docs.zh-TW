---
title: "教學課程： 將資料呈現從 SharePoint 網站上的 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1272b76c-29a1-4912-9c2d-8a4cf43df59d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aa1b709c317438c9614e412496eedb318dea3a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-present-data-from-oracle-e-business-suite-on-a-sharepoint-site"></a><span data-ttu-id="48b67-102">教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料</span><span class="sxs-lookup"><span data-stu-id="48b67-102">Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site</span></span>
<span data-ttu-id="48b67-103">本教學課程提供詳細的指示使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Microsoft Office SharePoint Server 上的 SharePoint 入口網站，從 Oracle E-business Suite 呈現資料。</span><span class="sxs-lookup"><span data-stu-id="48b67-103">This tutorial provides detailed instructions on using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with Microsoft Office SharePoint Server to present data from Oracle E-Business Suite on a SharePoint portal.</span></span> <span data-ttu-id="48b67-104">它也會示範如何設定可讓您從 SharePoint 入口網站上設定的 Oracle E-business Suite 成品執行全文檢索搜尋 Microsoft Office SharePoint Server 中的搜尋應用程式。</span><span class="sxs-lookup"><span data-stu-id="48b67-104">It also demonstrates how to configure a search application in the Microsoft Office SharePoint Server that allows you to do a full-text search from a SharePoint portal on the configured Oracle E-Business Suite artifact.</span></span>  
  
 <span data-ttu-id="48b67-105">若要示範如何執行這項操作，請考慮儲存員工的相關資訊的 Oracle E-business Suite 中的範例介面資料表。</span><span class="sxs-lookup"><span data-stu-id="48b67-105">To demonstrate how to do so, consider a sample interface table in Oracle E-Business Suite that stores information about employees.</span></span> <span data-ttu-id="48b67-106">在本教學課程中，會從根據搜尋字串使用 Oracle E-business Suite 擷取一份客戶的 Microsoft Office SharePoint Server 中建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="48b67-106">In this tutorial, an application is created in Microsoft Office SharePoint Server that retrieve a list of customers from Oracle E-Business Suite based on a search string using:</span></span>  
  
-   <span data-ttu-id="48b67-107">商務資料清單網頁組件中 Microsoft Office SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="48b67-107">A Business Data List Web Part in Microsoft Office SharePoint Server</span></span>  
  
-   <span data-ttu-id="48b67-108">Microsoft Office SharePoint Server 中的搜尋功能</span><span class="sxs-lookup"><span data-stu-id="48b67-108">The search feature in Microsoft Office SharePoint Server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48b67-109">本教學課程之前，確定您已安裝使用的所有必要條件[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Microsoft Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="48b67-109">Before proceeding with the tutorial, make sure you have installed all the prerequisites for using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="48b67-110">必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南 》，通常安裝在 C:\Program Files\Microsoft BizTalk 配接器 Pack\Documents。</span><span class="sxs-lookup"><span data-stu-id="48b67-110">For information about the prerequisites, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide, typically installed at C:\Program Files\Microsoft BizTalk Adapter Pack\Documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48b67-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="48b67-111">In This Section</span></span>  
  
-   [<span data-ttu-id="48b67-112">步驟 1： 使用 Oracle E-business 配接器來建立和發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="48b67-112">Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)  
  
-   [<span data-ttu-id="48b67-113">步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="48b67-113">Step 2: Create an Application Definition File for the Oracle E-Business Suite Artifacts</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)  
  
-   [<span data-ttu-id="48b67-114">步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料</span><span class="sxs-lookup"><span data-stu-id="48b67-114">Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
  
-   [<span data-ttu-id="48b67-115">步驟 4： 測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="48b67-115">Step 4: Test Your SharePoint Application</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)