---
title: 加入和移除成品時，會發生什麼情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, deleting
- artifacts, creating
- deleting, artifacts
ms.assetid: 811166ba-3ff4-4224-9d84-a2f4ed31bf4d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 464964714993205ef65d5a67de3399935f79320f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288878"
---
# <a name="what-happens-when-artifacts-are-added-and-removed"></a><span data-ttu-id="0cf68-102">加入和移除成品時發生的狀況</span><span class="sxs-lookup"><span data-stu-id="0cf68-102">What Happens When Artifacts Are Added and Removed</span></span>
<span data-ttu-id="0cf68-103">本主題說明在應用程式中加入成品時發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="0cf68-103">This topic describes what happens when you add artifacts to an application.</span></span> <span data-ttu-id="0cf68-104">您可以使用 BizTalk Server 管理主控台或 BTSTask 命令列工具，將以檔案為基礎的成品加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cf68-104">You can add file-based artifacts to an application by using the BizTalk Server Administration console or the BTSTask command-line tool.</span></span> <span data-ttu-id="0cf68-105">以檔案為基礎的成品包含下列類型：</span><span class="sxs-lookup"><span data-stu-id="0cf68-105">File-based artifacts include the following types:</span></span>  
  
-   <span data-ttu-id="0cf68-106">BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="0cf68-106">BizTalk assemblies</span></span>  
  
-   <span data-ttu-id="0cf68-107">非 BizTalk 專屬的 .NET 組件</span><span class="sxs-lookup"><span data-stu-id="0cf68-107">.NET assemblies that are not BizTalk-specific</span></span>  
  
-   <span data-ttu-id="0cf68-108">繫結 (.xml) 檔案</span><span class="sxs-lookup"><span data-stu-id="0cf68-108">Binding (.xml) files</span></span>  
  
-   <span data-ttu-id="0cf68-109">COM 元件</span><span class="sxs-lookup"><span data-stu-id="0cf68-109">COM components</span></span>  
  
-   <span data-ttu-id="0cf68-110">憑證</span><span class="sxs-lookup"><span data-stu-id="0cf68-110">Certificates</span></span>  
  
-   <span data-ttu-id="0cf68-111">前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="0cf68-111">Pre- and post-processing scripts</span></span>  
  
-   <span data-ttu-id="0cf68-112">原則</span><span class="sxs-lookup"><span data-stu-id="0cf68-112">Policies</span></span>  
  
-   <span data-ttu-id="0cf68-113">臨機操作檔案，例如讀我檔案</span><span class="sxs-lookup"><span data-stu-id="0cf68-113">Ad hoc files, such as Readme files</span></span>  
  
-   <span data-ttu-id="0cf68-114">虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="0cf68-114">Virtual directories</span></span>  
  
-   <span data-ttu-id="0cf68-115">BAM 成品</span><span class="sxs-lookup"><span data-stu-id="0cf68-115">BAM artifacts</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cf68-116">傳送埠、傳送埠群組、接收位置和接收埠不是以檔案為基礎的成品，無法加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cf68-116">Send ports, send port groups, receive locations, and receive ports are not file-based artifacts and cannot be added to an application.</span></span> <span data-ttu-id="0cf68-117">您必須在指定的應用程式中建立這些成品。</span><span class="sxs-lookup"><span data-stu-id="0cf68-117">You must create these artifacts within a given application.</span></span> <span data-ttu-id="0cf68-118">必要時，再將它們移至另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cf68-118">You can then move them to a different application, if you want.</span></span> <span data-ttu-id="0cf68-119">協調流程、結構描述、對應和管線全部會做為包含組件的一部分，來進行部署和管理。</span><span class="sxs-lookup"><span data-stu-id="0cf68-119">Orchestrations, schemas, maps and pipelines are all deployed and managed as part of the assemblies that contain them.</span></span>  
  
 <span data-ttu-id="0cf68-120">當您將成品加入至應用程式時，成品會與 BizTalk 管理資料庫中的應用程式相關聯，而且成品以檔案為基礎的資料也會加入至管理資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0cf68-120">When you add an artifact to an application, the artifact is associated with the application in the BizTalk Management database, and file-based data for the artifact is added to the Management database as well.</span></span> <span data-ttu-id="0cf68-121">這可讓您輕鬆地將應用程式和成品從一個 BizTalk 群組傳輸至另一個群組，因為您可以將應用程式和成品資料從管理資料庫匯出至 .msi 檔案，然後再將它匯入至另一個 BizTalk 群組中的管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="0cf68-121">This allows you to easily transport applications and artifacts from one BizTalk group to another because you can export the application and the data for its artifacts into an .msi file from the Management database, and then import it into a Management database in a different BizTalk group.</span></span>  
  
 <span data-ttu-id="0cf68-122">當您將繫結檔案加入至應用程式時，可以指定要套用繫結的目標部署環境。</span><span class="sxs-lookup"><span data-stu-id="0cf68-122">When you add a binding file to an application, you can specify the target deployment environment in which you want the bindings to be applied.</span></span> <span data-ttu-id="0cf68-123">與匯入繫結檔案不同，加入繫結檔案不會套用其繫結。</span><span class="sxs-lookup"><span data-stu-id="0cf68-123">Unlike importing a binding file, when you add a binding file, its bindings are not applied.</span></span>  
  
 <span data-ttu-id="0cf68-124">如果您指定這個選項，當您將 BizTalk 組件或 .NET 組件加入至應用程式時，便會將組件加入至全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="0cf68-124">When you add a BizTalk assembly or a .NET assembly to an application, the assembly is added to the global assembly cache if you specify this option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf68-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cf68-125">See Also</span></span>  
 <span data-ttu-id="0cf68-126">[會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="0cf68-126">[What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md) </span></span>  
 <span data-ttu-id="0cf68-127">[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md) </span><span class="sxs-lookup"><span data-stu-id="0cf68-127">[How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md) </span></span>  
 <span data-ttu-id="0cf68-128">[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="0cf68-128">[How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="0cf68-129">如何匯出 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="0cf68-129">How to Export a BizTalk Application</span></span>](../core/how-to-export-a-biztalk-application.md)