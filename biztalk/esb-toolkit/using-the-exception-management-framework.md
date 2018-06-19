---
title: 使用例外狀況管理架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b69c9c01-e7e4-4788-8fe2-43d32075155d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47442604831a3a11bb9d00b65f9dc34961de2367
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295182"
---
# <a name="using-the-exception-management-framework"></a><span data-ttu-id="3befa-102">使用例外狀況管理架構</span><span class="sxs-lookup"><span data-stu-id="3befa-102">Using the Exception Management Framework</span></span>
<span data-ttu-id="3befa-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態轉換和路由，用來通訊失敗 （例如，未部署的對應或不會傳回對應名稱的規則） 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3befa-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses exceptions to communicate failures (for example, a non-deployed map or rules that do not return a map name) for dynamic transformations and routing.</span></span> <span data-ttu-id="3befa-104">當轉換或路由程序失敗時，ESB 建立例外狀況訊息，並將它提交至 Messagebox 資料庫的直接繫結連接埠。</span><span class="sxs-lookup"><span data-stu-id="3befa-104">When a transformation or routing process fails, the ESB creates an exception message and submits it through a direct-bound port to the Message Box database.</span></span> <span data-ttu-id="3befa-105">ESB 也會實作名為所有的傳送埠。訂閱和擷取例外狀況訊息，並將其發行到 ESB 管理入口網站的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3befa-105">The ESB also implements a send port named ALL.Exceptions that subscribes to and retrieves exception messages and publishes them to the ESB Management Portal.</span></span>  
  
 <span data-ttu-id="3befa-106">此外，所有的協調流程範例使用 ESB 無法協調流程例外狀況路由 API 來處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3befa-106">In addition, all orchestration samples use the ESB Failed Orchestration Exception Routing API to handle exceptions.</span></span> <span data-ttu-id="3befa-107">您可以在任何您所部署的協調流程專案中使用此 API。</span><span class="sxs-lookup"><span data-stu-id="3befa-107">You can use this API in any orchestration project you deploy.</span></span> <span data-ttu-id="3befa-108">ESB 無法協調流程的例外狀況路由功能提供截獲並報告 BizTalk Server 環境中的所有例外狀況的標準方法。</span><span class="sxs-lookup"><span data-stu-id="3befa-108">The ESB Failed Orchestration Exception Routing feature provides a standard way to trap and report all exceptions in a BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="3befa-109">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例專案會示範如何使用 ESB 例外狀況管理架構。</span><span class="sxs-lookup"><span data-stu-id="3befa-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains several sample projects that demonstrate how to use the ESB Exception Management Framework.</span></span> <span data-ttu-id="3befa-110">下列兩個專案封裝 ESB 無法協調流程的例外狀況路由 API:</span><span class="sxs-lookup"><span data-stu-id="3befa-110">The following two projects encapsulate the ESB Failed Orchestration Exception Routing API:</span></span>  
  
-   <span data-ttu-id="3befa-111">**ESB。ExceptionHandling**。</span><span class="sxs-lookup"><span data-stu-id="3befa-111">**ESB.ExceptionHandling**.</span></span> <span data-ttu-id="3befa-112">此專案包含用於處理協調流程中的錯誤訊息處理的所有公用方法。</span><span class="sxs-lookup"><span data-stu-id="3befa-112">This project contains all the public methods for handling fault message processing in orchestrations.</span></span> <span data-ttu-id="3befa-113">您必須在全域組件快取在本機伺服器上此專案中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="3befa-113">You must register the assembly in this project in the global assembly cache on the local server.</span></span>  
  
-   <span data-ttu-id="3befa-114">**ESB。ExceptionHandling.Schemas.Faults**。</span><span class="sxs-lookup"><span data-stu-id="3befa-114">**ESB.ExceptionHandling.Schemas.Faults**.</span></span> <span data-ttu-id="3befa-115">此專案包含命名空間所定義的錯誤訊息結構描述**http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**和系統屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="3befa-115">This project contains the fault message schema defined by the namespace **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling** and the system property schema.</span></span> <span data-ttu-id="3befa-116">您必須將此專案部署至 Microsoft.Practices.ESB 應用程式容器中。</span><span class="sxs-lookup"><span data-stu-id="3befa-116">You must deploy this project to the Microsoft.Practices.ESB application container.</span></span>  
  
 <span data-ttu-id="3befa-117">使用 ESB 無法協調流程的例外狀況路由 API 的所有專案必須都參考核心組件：</span><span class="sxs-lookup"><span data-stu-id="3befa-117">All projects that use the ESB Failed Orchestration Exception Routing API must reference the core assemblies:</span></span>  
  
-   <span data-ttu-id="3befa-118">**Microsoft.Practices.ESB.ExceptionHandling.dll**</span><span class="sxs-lookup"><span data-stu-id="3befa-118">**Microsoft.Practices.ESB.ExceptionHandling.dll**</span></span>  
  
-   <span data-ttu-id="3befa-119">**Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**</span><span class="sxs-lookup"><span data-stu-id="3befa-119">**Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**</span></span>  
  
 <span data-ttu-id="3befa-120">下列各節提供有關使用 ESB 例外狀況管理架構的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="3befa-120">The following sections provide more information about using the ESB Exception Management Framework:</span></span>  
  
-   [<span data-ttu-id="3befa-121">ESB 例外狀況應用程式開發介面成員</span><span class="sxs-lookup"><span data-stu-id="3befa-121">The ESB Exception API Members</span></span>](../esb-toolkit/the-esb-exception-api-members.md)  
  
-   [<span data-ttu-id="3befa-122">建立並發佈錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="3befa-122">Creating and Publishing Fault Messages</span></span>](../esb-toolkit/creating-and-publishing-fault-messages.md)  
  
-   [<span data-ttu-id="3befa-123">訂閱和擷取訊息</span><span class="sxs-lookup"><span data-stu-id="3befa-123">Subscribing to and Extracting Messages</span></span>](../esb-toolkit/subscribing-to-and-extracting-messages.md)  
  
-   [<span data-ttu-id="3befa-124">實例解決方案的步驟</span><span class="sxs-lookup"><span data-stu-id="3befa-124">Scenario Solution Steps</span></span>](../esb-toolkit/scenario-solution-steps.md)