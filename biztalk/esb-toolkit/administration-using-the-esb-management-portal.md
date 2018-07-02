---
title: 使用 ESB 管理入口網站管理 |Microsoft Docs
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
ms.openlocfilehash: 24c44951b4284e0d17b2d8e69011cedfa213c219
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967759"
---
# <a name="administration-using-the-esb-management-portal"></a><span data-ttu-id="cec11-102">使用 ESB 管理入口網站管理</span><span class="sxs-lookup"><span data-stu-id="cec11-102">Administration Using the ESB Management Portal</span></span>
<span data-ttu-id="cec11-103">ESB 管理入口網站中，包含[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，會示範如何使用計量和可能性在於擴充 BizTalk ESB 工具組範例網站。</span><span class="sxs-lookup"><span data-stu-id="cec11-103">The ESB Management Portal, included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], is a sample site that demonstrates the use of metrics and the possibilities that exist for extending the BizTalk ESB Toolkit.</span></span> <span data-ttu-id="cec11-104">在入口網站提供您可以用來建置您自己自訂的入口網站的起點。</span><span class="sxs-lookup"><span data-stu-id="cec11-104">The portal provides a starting point from which you can build your own customized portal.</span></span>  
  
 <span data-ttu-id="cec11-105">ESB 管理入口網站也是高度有效且實用的工具，可協助最大化的使用和 ESB 例外狀況管理系統的效率。</span><span class="sxs-lookup"><span data-stu-id="cec11-105">The ESB Management Portal is also a highly capable and useful tool that can help to maximize the use and efficiency of the ESB exception management system.</span></span> <span data-ttu-id="cec11-106">此外，入口網站提供使用者介面為基礎的通用描述、 探索與整合 (UDDI) 登錄伺服器和稽核等功能的圖形化的組態功能檢視歷程記錄資訊設定警示和通知，以及讓使用者訂閱警示，表示在 ESB 應用程式中發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cec11-106">In addition, the portal provides a user interface for an underlying Universal Description, Discovery, and Integration (UDDI) registry server and graphical configuration capabilities for features such as auditing, viewing history information, configuring alerts and notifications, and allowing users to subscribe to alerts that indicate faults occurring in ESB applications.</span></span>  
  
 <span data-ttu-id="cec11-107">本章節描述您可以使用 ESB 管理入口網站中，包括下列來完成常見工作：</span><span class="sxs-lookup"><span data-stu-id="cec11-107">This section describes the common tasks you can accomplish using the ESB Management Portal, including the following:</span></span>  
  
-   [<span data-ttu-id="cec11-108">使用例外狀況和錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="cec11-108">Working with Exceptions and Fault Messages</span></span>](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [<span data-ttu-id="cec11-109">設定警示、通知和訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="cec11-109">Configuring Alerts, Notifications, and Subscriptions</span></span>](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [<span data-ttu-id="cec11-110">檢視和管理稽核和歷程記錄</span><span class="sxs-lookup"><span data-stu-id="cec11-110">Viewing and Managing Auditing and History</span></span>](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [<span data-ttu-id="cec11-111">使用圖表和報告分析錯誤趨勢</span><span class="sxs-lookup"><span data-stu-id="cec11-111">Analyzing Fault Trends Using Charts and Reports</span></span>](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [<span data-ttu-id="cec11-112">檢視和發佈 UDDI 註冊</span><span class="sxs-lookup"><span data-stu-id="cec11-112">Viewing and Publishing UDDI Registrations</span></span>](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  <span data-ttu-id="cec11-113">ESB 管理入口網站的個別功能的詳細說明，請參閱 < [ESB 管理入口網站功能參考](../esb-toolkit/esb-management-portal-feature-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="cec11-113">For a detailed description of the individual features of the ESB Management Portal, see [ESB Management Portal Feature Reference](../esb-toolkit/esb-management-portal-feature-reference.md).</span></span>  
  
## <a name="esb-portal-technologies"></a><span data-ttu-id="cec11-114">ESB 入口網站的技術</span><span class="sxs-lookup"><span data-stu-id="cec11-114">ESB Portal Technologies</span></span>  
 <span data-ttu-id="cec11-115">ESB 管理入口網站會利用下列技術：</span><span class="sxs-lookup"><span data-stu-id="cec11-115">The ESB Management Portal takes advantage of the following technologies:</span></span>  
  
- [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
- <span data-ttu-id="cec11-116">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cec11-116">ASP.NET</span></span>
  
- <span data-ttu-id="cec11-117">[Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292))。</span><span class="sxs-lookup"><span data-stu-id="cec11-117">[Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292)).</span></span> <span data-ttu-id="cec11-118">ESB 管理入口網站會使用下列的企業程式庫組件：</span><span class="sxs-lookup"><span data-stu-id="cec11-118">The ESB Management Portal uses the following Enterprise Library assemblies:</span></span>  
  
  -   <span data-ttu-id="cec11-119">**Microsoft.Practices.EnterpriseLibrary.Caching**</span><span class="sxs-lookup"><span data-stu-id="cec11-119">**Microsoft.Practices.EnterpriseLibrary.Caching**</span></span>  
  
  -   <span data-ttu-id="cec11-120">**Microsoft.Practices.EnterpriseLibrary.Common**</span><span class="sxs-lookup"><span data-stu-id="cec11-120">**Microsoft.Practices.EnterpriseLibrary.Common**</span></span>  
  
  -   <span data-ttu-id="cec11-121">**Microsoft.Practices.EnterpriseLibrary.Data**</span><span class="sxs-lookup"><span data-stu-id="cec11-121">**Microsoft.Practices.EnterpriseLibrary.Data**</span></span>  
  
  -   <span data-ttu-id="cec11-122">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**</span><span class="sxs-lookup"><span data-stu-id="cec11-122">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**</span></span>  
  
  -   <span data-ttu-id="cec11-123">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**</span><span class="sxs-lookup"><span data-stu-id="cec11-123">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**</span></span>  
  
  -   <span data-ttu-id="cec11-124">**Microsoft.Practices.EnterpriseLibrary.Logging**</span><span class="sxs-lookup"><span data-stu-id="cec11-124">**Microsoft.Practices.EnterpriseLibrary.Logging**</span></span>  
  
  -   <span data-ttu-id="cec11-125">**Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**</span><span class="sxs-lookup"><span data-stu-id="cec11-125">**Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**</span></span>  
  
  -   <span data-ttu-id="cec11-126">**Microsoft.Practices.EnterpriseLibrary.Validation**</span><span class="sxs-lookup"><span data-stu-id="cec11-126">**Microsoft.Practices.EnterpriseLibrary.Validation**</span></span>  
  
  -   <span data-ttu-id="cec11-127">Microsoft.Practices.Unity</span><span class="sxs-lookup"><span data-stu-id="cec11-127">Microsoft.Practices.Unity</span></span>  
  
- <span data-ttu-id="cec11-128">[Microsoft Chart Controls](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293)適用於 Microsoft.NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="cec11-128">[Microsoft Chart Controls](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293) for Microsoft .NET Framework 4</span></span>  
  
<span data-ttu-id="cec11-129">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]計量追蹤只會延伸到錯誤的例外狀況管理系統的追蹤。</span><span class="sxs-lookup"><span data-stu-id="cec11-129">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] metric tracking extends only to fault tracking for the exception management system.</span></span>