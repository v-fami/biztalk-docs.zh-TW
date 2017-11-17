---
title: "Siebel 配接器進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: de11ffe3-3622-40df-b9c5-11c96f8460e0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e12b877eaabb629bb9e9e1da81cf5343e1780cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-siebel-adapter"></a><span data-ttu-id="12f19-102">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="12f19-102">Troubleshoot the Siebel adapter</span></span>
<span data-ttu-id="12f19-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]使用或依賴數種不同的 Microsoft 技術包括但不是限於[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，與 Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] / [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12f19-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several different Microsoft technologies including but not limited to [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and the Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]/[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="12f19-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]建置最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，這又需要[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]和[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12f19-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which in turn requires [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] and [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="12f19-105">可以使用配接器，或是藉由撰寫應用程式使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或藉由建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="12f19-105">The adapters can be consumed either by writing applications using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> <span data-ttu-id="12f19-106">如需有關這些技術和產品的問題，請參閱個別的文件。</span><span class="sxs-lookup"><span data-stu-id="12f19-106">For issues related to each of these technologies and products, refer to the respective documentation.</span></span>  
  
 <span data-ttu-id="12f19-107">本章節提供疑難排解資訊[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，包括：</span><span class="sxs-lookup"><span data-stu-id="12f19-107">This section provides information about troubleshooting the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], including:</span></span>  
  
-   <span data-ttu-id="12f19-108">啟用追蹤，以診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="12f19-108">Enabling tracing to diagnose issues with the adapters.</span></span>  
  
-   <span data-ttu-id="12f19-109">正在處理安裝和操作時使用配接器，包括可能的原因和解決方案，可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="12f19-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause, and a resolution.</span></span>  
  
-   <span data-ttu-id="12f19-110">使用效能計數器來測量配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="12f19-110">Using performance counters to gauge adapter performance.</span></span>  
  
-   <span data-ttu-id="12f19-111">處理例外狀況和錯誤，包括可能的原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="12f19-111">Handling exceptions and errors, including probable cause, and a resolution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12f19-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="12f19-112">In This Section</span></span>  
  
-   [<span data-ttu-id="12f19-113">診斷追蹤和 Siebel 配接器的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="12f19-113">Diagnostic Tracing and Message Logging for the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="12f19-114">使用 Siebel 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="12f19-114">Troubleshoot Installation Issues with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-installation-issues-with-the-siebel-adapter.md) 
  
-   [<span data-ttu-id="12f19-115">使用 Siebel 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="12f19-115">Troubleshoot Operational Issues with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-operational-issues-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="12f19-116">Siebel 配接器疑難排解效能問題</span><span class="sxs-lookup"><span data-stu-id="12f19-116">Troubleshoot Performance Issues with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-performance-issues-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="12f19-117">疑難排解問題的 siebel 資料提供者</span><span class="sxs-lookup"><span data-stu-id="12f19-117">Troubleshoot Issues with the Data Provider for Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-issues-with-the-data-provider-for-siebel.md) 
  
-   [<span data-ttu-id="12f19-118">使用 Siebel 配接器的效能計數器</span><span class="sxs-lookup"><span data-stu-id="12f19-118">Use Performance Counters with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/use-performance-counters-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="12f19-119">例外狀況和錯誤處理 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="12f19-119">Exceptions and Error Handling with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md)