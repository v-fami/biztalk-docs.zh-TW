---
title: 管理使用 ESB 管理入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 478d1dcc-e9b2-443b-be98-5b7545322401
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 351d06df4d6384607564778c4b86d8c509379488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290270"
---
# <a name="administration-using-the-esb-management-portal"></a><span data-ttu-id="5147f-102">使用 ESB 管理入口網站的系統管理</span><span class="sxs-lookup"><span data-stu-id="5147f-102">Administration Using the ESB Management Portal</span></span>
<span data-ttu-id="5147f-103">ESB 管理入口網站中，包含[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，會示範如何使用計量，以及可能存在的值來擴充 BizTalk ESB Toolkit 的範例網站。</span><span class="sxs-lookup"><span data-stu-id="5147f-103">The ESB Management Portal, included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], is a sample site that demonstrates the use of metrics and the possibilities that exist for extending the BizTalk ESB Toolkit.</span></span> <span data-ttu-id="5147f-104">入口網站提供的起點，您可以從中建立您自己的自訂入口網站。</span><span class="sxs-lookup"><span data-stu-id="5147f-104">The portal provides a starting point from which you can build your own customized portal.</span></span>  
  
 <span data-ttu-id="5147f-105">ESB 管理入口網站也是高度能夠且有用的工具，可協助最大化的使用方式和 ESB 例外狀況管理系統的效率。</span><span class="sxs-lookup"><span data-stu-id="5147f-105">The ESB Management Portal is also a highly capable and useful tool that can help to maximize the use and efficiency of the ESB exception management system.</span></span> <span data-ttu-id="5147f-106">此外，入口網站提供使用者介面為基礎的通用描述、 探索與整合 (UDDI) 登錄伺服器圖形化設定功能的功能，例如稽核，檢視記錄資訊設定警示和通知，以及讓使用者訂閱警示指出 ESB 應用程式中發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5147f-106">In addition, the portal provides a user interface for an underlying Universal Description, Discovery, and Integration (UDDI) registry server and graphical configuration capabilities for features such as auditing, viewing history information, configuring alerts and notifications, and allowing users to subscribe to alerts that indicate faults occurring in ESB applications.</span></span>  
  
 <span data-ttu-id="5147f-107">本章節描述您可以完成使用 ESB 管理入口網站中，包括下列的一般工作：</span><span class="sxs-lookup"><span data-stu-id="5147f-107">This section describes the common tasks you can accomplish using the ESB Management Portal, including the following:</span></span>  
  
-   [<span data-ttu-id="5147f-108">使用例外狀況和錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="5147f-108">Working with Exceptions and Fault Messages</span></span>](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [<span data-ttu-id="5147f-109">設定警示、 通知和訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="5147f-109">Configuring Alerts, Notifications, and Subscriptions</span></span>](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [<span data-ttu-id="5147f-110">檢視及管理稽核和記錄</span><span class="sxs-lookup"><span data-stu-id="5147f-110">Viewing and Managing Auditing and History</span></span>](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [<span data-ttu-id="5147f-111">使用圖表和報告的錯誤趨勢分析</span><span class="sxs-lookup"><span data-stu-id="5147f-111">Analyzing Fault Trends Using Charts and Reports</span></span>](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [<span data-ttu-id="5147f-112">檢視與發行 UDDI 登錄</span><span class="sxs-lookup"><span data-stu-id="5147f-112">Viewing and Publishing UDDI Registrations</span></span>](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  <span data-ttu-id="5147f-113">ESB 管理入口網站的個別功能的詳細說明，請參閱[ESB Management 入口網站功能參考](../esb-toolkit/esb-management-portal-feature-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="5147f-113">For a detailed description of the individual features of the ESB Management Portal, see [ESB Management Portal Feature Reference](../esb-toolkit/esb-management-portal-feature-reference.md).</span></span>  
  
## <a name="esb-portal-technologies"></a><span data-ttu-id="5147f-114">ESB 入口網站的技術</span><span class="sxs-lookup"><span data-stu-id="5147f-114">ESB Portal Technologies</span></span>  
 <span data-ttu-id="5147f-115">ESB 管理入口網站會利用下列技術：</span><span class="sxs-lookup"><span data-stu-id="5147f-115">The ESB Management Portal takes advantage of the following technologies:</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
-   <span data-ttu-id="5147f-116">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5147f-116">ASP.NET</span></span>
  
-   <span data-ttu-id="5147f-117">[Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292))。</span><span class="sxs-lookup"><span data-stu-id="5147f-117">[Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292)).</span></span> <span data-ttu-id="5147f-118">ESB 管理入口網站會使用下列的企業程式庫組件：</span><span class="sxs-lookup"><span data-stu-id="5147f-118">The ESB Management Portal uses the following Enterprise Library assemblies:</span></span>  
  
    -   <span data-ttu-id="5147f-119">**Microsoft.Practices.EnterpriseLibrary.Caching**</span><span class="sxs-lookup"><span data-stu-id="5147f-119">**Microsoft.Practices.EnterpriseLibrary.Caching**</span></span>  
  
    -   <span data-ttu-id="5147f-120">**Microsoft.Practices.EnterpriseLibrary.Common**</span><span class="sxs-lookup"><span data-stu-id="5147f-120">**Microsoft.Practices.EnterpriseLibrary.Common**</span></span>  
  
    -   <span data-ttu-id="5147f-121">**Microsoft.Practices.EnterpriseLibrary.Data**</span><span class="sxs-lookup"><span data-stu-id="5147f-121">**Microsoft.Practices.EnterpriseLibrary.Data**</span></span>  
  
    -   <span data-ttu-id="5147f-122">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**</span><span class="sxs-lookup"><span data-stu-id="5147f-122">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**</span></span>  
  
    -   <span data-ttu-id="5147f-123">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**</span><span class="sxs-lookup"><span data-stu-id="5147f-123">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**</span></span>  
  
    -   <span data-ttu-id="5147f-124">**Microsoft.Practices.EnterpriseLibrary.Logging**</span><span class="sxs-lookup"><span data-stu-id="5147f-124">**Microsoft.Practices.EnterpriseLibrary.Logging**</span></span>  
  
    -   <span data-ttu-id="5147f-125">**Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**</span><span class="sxs-lookup"><span data-stu-id="5147f-125">**Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**</span></span>  
  
    -   <span data-ttu-id="5147f-126">**Microsoft.Practices.EnterpriseLibrary.Validation**</span><span class="sxs-lookup"><span data-stu-id="5147f-126">**Microsoft.Practices.EnterpriseLibrary.Validation**</span></span>  
  
    -   <span data-ttu-id="5147f-127">Microsoft.Practices.Unity</span><span class="sxs-lookup"><span data-stu-id="5147f-127">Microsoft.Practices.Unity</span></span>  
  
-   <span data-ttu-id="5147f-128">[Microsoft 圖表控制項](http://go.microsoft.com/fwlink/?LinkId=188293)(http://go.microsoft.com/fwlink/?LinkId=188293) 的 Microsoft.NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="5147f-128">[Microsoft Chart Controls](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293) for Microsoft .NET Framework 4</span></span>  
  
<span data-ttu-id="5147f-129">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]度量追蹤只會延伸到錯誤追蹤的例外狀況管理系統。</span><span class="sxs-lookup"><span data-stu-id="5147f-129">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] metric tracking extends only to fault tracking for the exception management system.</span></span>