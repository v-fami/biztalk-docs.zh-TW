---
title: 教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dd06f75-75d1-4fad-8f34-51c97c7790e3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd82dc1f8328645e59aa8c7b0fc668cbe2509ab6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963084"
---
# <a name="tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site"></a><span data-ttu-id="8f2e0-102">教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料</span><span class="sxs-lookup"><span data-stu-id="8f2e0-102">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>
<span data-ttu-id="8f2e0-103">本教學課程提供詳細的指示使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft Office SharePoint Server，在 SharePoint 網站上呈現從 Siebel 系統的商務資料。</span><span class="sxs-lookup"><span data-stu-id="8f2e0-103">This tutorial provides detailed instructions on using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft Office SharePoint Server to present business data from a Siebel system on a SharePoint portal.</span></span> <span data-ttu-id="8f2e0-104">若要示範如何使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]Office SharePoint Server，以建立應用程式中擷取一份客戶帳戶從 Siebel 儲存機制使用 Office SharePoint Server [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8f2e0-104">To demonstrate how to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Office SharePoint Server, we create an application in Office SharePoint Server to retrieve a list of customer accounts from the Siebel repository using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
 <span data-ttu-id="8f2e0-105">若要擷取此資訊來自 Siebel 系統，範例會叫用的查詢方法上**帳戶**商務元件。</span><span class="sxs-lookup"><span data-stu-id="8f2e0-105">To extract this information from the Siebel system, the example invokes the Query method on the **Account** business components.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f2e0-106">本教學課程之前，確定您已安裝使用的所有必要條件[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]Office SharePoint server。</span><span class="sxs-lookup"><span data-stu-id="8f2e0-106">Before proceeding with the tutorial, make sure you have installed all the prerequisites for using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Office SharePoint Server.</span></span> <span data-ttu-id="8f2e0-107">如需有關必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南 》，通常安裝在\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="8f2e0-107">For more information about the prerequisites, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide, typically installed at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f2e0-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="8f2e0-108">In This Section</span></span>  
  
-   [<span data-ttu-id="8f2e0-109">步驟 1：將 Siebel 商務元件作業發佈為 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="8f2e0-109">Step 1: Publish the Siebel Business Component Operations as a WCF Service</span></span>](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)  
  
-   [<span data-ttu-id="8f2e0-110">步驟 2：建立 Siebel 商務元件作業的應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="8f2e0-110">Step 2: Create an Application Definition File for Siebel Business Component Operations</span></span>](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)  
  
-   [<span data-ttu-id="8f2e0-111">步驟 3：建立 SharePoint 應用程式來擷取 Siebel　的資料</span><span class="sxs-lookup"><span data-stu-id="8f2e0-111">Step 3: Create a SharePoint Application to Retrieve Data from Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)  
  
-  [<span data-ttu-id="8f2e0-112">步驟 4：測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="8f2e0-112">Step 4: Test Your SharePoint Application</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f2e0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f2e0-113">See Also</span></span>  
 [<span data-ttu-id="8f2e0-114">Siebel 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="8f2e0-114">Siebel Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)