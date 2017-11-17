---
title: "管理資源 |Microsoft 文件"
description: "工作與組件、 指令碼、 憑證、 繫結檔案和其他 BizTalk Server 中使用 btstask 」 或 「 BizTalk 管理"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b478ef2e-1363-4c2c-a4b7-6a582a6b33a5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07248c1689adf6b6474fd8e1f3e01f2d660becdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-resources"></a><span data-ttu-id="18de2-103">管理資源</span><span class="sxs-lookup"><span data-stu-id="18de2-103">Manage Resources</span></span>

## <a name="overview"></a><span data-ttu-id="18de2-104">概觀</span><span class="sxs-lookup"><span data-stu-id="18de2-104">Overview</span></span>
<span data-ttu-id="18de2-105">本節中的主題提供如何使用 BizTalk Server 管理主控台或 BTSTask 命令列工具，在將 BizTalk Server 資源部署至 BizTalk 群組後管理這些資源的指示。</span><span class="sxs-lookup"><span data-stu-id="18de2-105">The topics in this section provide instructions on how to use the BizTalk Server Administration console or the BTSTask command-line tool to manage BizTalk Server resources after they have been deployed into a BizTalk group.</span></span> <span data-ttu-id="18de2-106">資源包括下列成品類型：</span><span class="sxs-lookup"><span data-stu-id="18de2-106">Resources include the following types of artifacts:</span></span>  
  
-   <span data-ttu-id="18de2-107">BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="18de2-107">BizTalk Assemblies</span></span>  
  
-   <span data-ttu-id="18de2-108">前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="18de2-108">Pre- and post-processing scripts</span></span>  
  
-   <span data-ttu-id="18de2-109">.NET 組件</span><span class="sxs-lookup"><span data-stu-id="18de2-109">.NET assemblies</span></span>  
  
-   <span data-ttu-id="18de2-110">COM 元件</span><span class="sxs-lookup"><span data-stu-id="18de2-110">COM components</span></span>  
  
-   <span data-ttu-id="18de2-111">憑證</span><span class="sxs-lookup"><span data-stu-id="18de2-111">Certificates</span></span>  
  
-   <span data-ttu-id="18de2-112">臨機操作檔案</span><span class="sxs-lookup"><span data-stu-id="18de2-112">Ad hoc files</span></span>  
  
-   <span data-ttu-id="18de2-113">BAM 定義</span><span class="sxs-lookup"><span data-stu-id="18de2-113">BAM definitions</span></span>  
  
-   <span data-ttu-id="18de2-114">繫結檔案</span><span class="sxs-lookup"><span data-stu-id="18de2-114">Binding files</span></span>  
  
-   <span data-ttu-id="18de2-115">虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="18de2-115">Virtual directories</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18de2-116">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="18de2-116">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="18de2-117">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="18de2-117">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
> [!NOTE]
>  <span data-ttu-id="18de2-118">請勿將具有相同名稱 (不論大小寫) 的多個資源新增到 BizTalk Server 群組。</span><span class="sxs-lookup"><span data-stu-id="18de2-118">Do not add multiple resources with the same name, regardless of case, to a BizTalk Server group.</span></span> <span data-ttu-id="18de2-119">不支援將具有相同的名稱的多個資源新增到 BizTalk Server 群組，即使在 BizTalk Server 管理資料庫儲存在設定為使用二進位定序並支援區分大小寫功能的 SQL Server 上也一樣。</span><span class="sxs-lookup"><span data-stu-id="18de2-119">Adding multiple resources with the same name to a BizTalk Server group is not supported, even when the BizTalk Server management database is housed on a SQL Server that is configured to use binary collation and supports case sensitivity.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="18de2-120">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="18de2-120">Next steps</span></span>
  
-   [<span data-ttu-id="18de2-121">管理 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="18de2-121">Managing BizTalk Assemblies</span></span>](../core/managing-biztalk-assemblies.md)  
  
-   [<span data-ttu-id="18de2-122">管理前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="18de2-122">Managing Pre- and Post-processing Scripts</span></span>](../core/managing-pre-and-post-processing-scripts.md)  
  
-   [<span data-ttu-id="18de2-123">管理.NET 組件、 憑證和其他資源</span><span class="sxs-lookup"><span data-stu-id="18de2-123">Managing .NET Assemblies, Certificates, and Other Resources</span></span>](../core/managing-net-assemblies-certificates-and-other-resources.md)  
  
-   [<span data-ttu-id="18de2-124">重新整理資源</span><span class="sxs-lookup"><span data-stu-id="18de2-124">Refresh a Resource</span></span>](../core/how-to-refresh-a-resource.md)