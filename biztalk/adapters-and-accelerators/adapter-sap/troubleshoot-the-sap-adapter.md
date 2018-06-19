---
title: SAP 配接器進行疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 2c554a7b-18be-4c94-8bf2-f22ac080794c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1994f7c2d6d32dc394783a68edb91532118434aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216334"
---
# <a name="troubleshoot-the-sap-adapter"></a><span data-ttu-id="6ccd3-102">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="6ccd3-102">Troubleshoot the SAP adapter</span></span>
<span data-ttu-id="6ccd3-103">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]使用或依賴數種 Microsoft 技術，包括但不是限於[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，與 Microsoft[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]或[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several Microsoft technologies, including but not limited to the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and the Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] or [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="6ccd3-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]建置最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，這又需要[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]或[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which in turn requires the [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] or [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="6ccd3-105">可以使用配接器，或是藉由撰寫應用程式使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或藉由建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-105">The adapters can be consumed either by writing applications using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> <span data-ttu-id="6ccd3-106">如需有關這些技術和產品的問題，請參閱個別的文件。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-106">For issues related to each of these technologies and products, see the respective documentation.</span></span>  
  
 <span data-ttu-id="6ccd3-107">本章節提供疑難排解資訊[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，包括：</span><span class="sxs-lookup"><span data-stu-id="6ccd3-107">This section provides information about troubleshooting the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], including:</span></span>  
  
-   <span data-ttu-id="6ccd3-108">啟用追蹤，以診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-108">Enabling tracing to diagnose issues with the adapters.</span></span>  
  
-   <span data-ttu-id="6ccd3-109">正在處理安裝和操作時使用配接器，包括可能的原因和解決方案，可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause, and a resolution.</span></span>  
  
-   <span data-ttu-id="6ccd3-110">使用效能計數器來測量配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-110">Using performance counters to gauge adapter performance.</span></span>  
  
-   <span data-ttu-id="6ccd3-111">處理例外狀況和錯誤，包括可能的原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="6ccd3-111">Handling exceptions and errors, including probable cause, and a resolution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ccd3-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="6ccd3-112">In This Section</span></span>  
  
-   [<span data-ttu-id="6ccd3-113">診斷追蹤和 SAP 配接器的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="6ccd3-113">Diagnostic Tracing and Message Logging for the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md)  
  
-   [<span data-ttu-id="6ccd3-114">SAP 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="6ccd3-114">Troubleshoot Installation Issues with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-installation-issues-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="6ccd3-115">SAP 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="6ccd3-115">Troubleshoot Operational Issues with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="6ccd3-116">疑難排解 SAP 配接器的效能問題</span><span class="sxs-lookup"><span data-stu-id="6ccd3-116">Troubleshoot Performance Issues with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-performance-issues-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="6ccd3-117">疑難排解資料提供者適用於 SAP 的問題</span><span class="sxs-lookup"><span data-stu-id="6ccd3-117">Troubleshoot Issues with the Data Provider for SAP</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-issues-with-the-data-provider-for-sap.md)  
  
-   [<span data-ttu-id="6ccd3-118">SAP 配接器搭配使用效能計數器</span><span class="sxs-lookup"><span data-stu-id="6ccd3-118">Use Performance Counters with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="6ccd3-119">例外狀況和錯誤處理與 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="6ccd3-119">Exceptions and Error Handling with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)