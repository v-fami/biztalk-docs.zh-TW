---
title: "SQL 配接器進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1be376ba-ad4c-4fa7-b94b-82bfbc8f34cc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8b574a372ed365a22ff9d87d40bf4ab9af8ae4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-sql-adapter"></a><span data-ttu-id="44289-102">SQL 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="44289-102">Troubleshoot the SQL adapter</span></span>
<span data-ttu-id="44289-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]使用或依賴數種 Microsoft 技術，包括但不是限於[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]，和[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="44289-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several Microsoft technologies, including but not limited to the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)], and [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="44289-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]建置最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，這又需要[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]或[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="44289-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which in turn requires the [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] or [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="44289-105">可以使用配接器，或是藉由撰寫應用程式使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或藉由建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="44289-105">The adapters can be consumed either by writing applications using the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> <span data-ttu-id="44289-106">如需有關這些技術和產品的問題，請參閱個別的文件。</span><span class="sxs-lookup"><span data-stu-id="44289-106">For issues related to each of these technologies and products, see the respective documentation.</span></span>  
  
 <span data-ttu-id="44289-107">本章節提供疑難排解資訊[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，包括：</span><span class="sxs-lookup"><span data-stu-id="44289-107">This section provides information about troubleshooting the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], including:</span></span>  
  
-   <span data-ttu-id="44289-108">啟用追蹤，以診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="44289-108">Enabling tracing to diagnose issues with the adapters.</span></span>  
  
-   <span data-ttu-id="44289-109">正在處理安裝和操作時使用配接器，包括可能的原因和解決方案，可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="44289-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause, and a resolution.</span></span>  
  
-   <span data-ttu-id="44289-110">使用效能計數器來測量配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="44289-110">Using performance counters to gauge adapter performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44289-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="44289-111">In This Section</span></span>  
  
-   [<span data-ttu-id="44289-112">診斷追蹤和訊息記錄在 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="44289-112">Diagnostic Tracing and Message Logging in the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md)  
  
-   [<span data-ttu-id="44289-113">SQl 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="44289-113">Troubleshoot Installation Issues with the SQl adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-installation-issues-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="44289-114">SQL 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="44289-114">Troubleshoot Operational Issues with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-operational-issues-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="44289-115">使用 SQL 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="44289-115">Use Performance Counters with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)