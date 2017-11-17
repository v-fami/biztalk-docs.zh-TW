---
title: "Oracle EBS 配接器疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78d5335-b860-47d9-9f3a-7f74d628d8ff
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7b36316612bda541d9bf608f7da22c399ade045
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-oracle-ebs-adapter"></a><span data-ttu-id="637cf-102">Oracle EBS 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="637cf-102">Troubleshooting the Oracle EBS adapter</span></span>
## <a name="overview"></a><span data-ttu-id="637cf-103">概觀</span><span class="sxs-lookup"><span data-stu-id="637cf-103">Overview</span></span>
<span data-ttu-id="637cf-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]使用或依賴數種 Microsoft 技術，包括但不是限於[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，和[!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="637cf-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several Microsoft technologies, including but not limited to the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span></span> <span data-ttu-id="637cf-105">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]建置最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，這也會使用[!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="637cf-105">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which also uses the [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span></span> <span data-ttu-id="637cf-106">可以使用配接器，或是藉由撰寫應用程式使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或藉由建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="637cf-106">The adapters can be consumed either by writing applications using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> 
  
 <span data-ttu-id="637cf-107">此章節提供疑難排解的相關資訊，包括：</span><span class="sxs-lookup"><span data-stu-id="637cf-107">This section provides information about troubleshooting, including:</span></span>  
  
-   <span data-ttu-id="637cf-108">啟用追蹤來診斷問題使用配接器</span><span class="sxs-lookup"><span data-stu-id="637cf-108">Enabling tracing to diagnose issues with the adapters</span></span>
  
-   <span data-ttu-id="637cf-109">處理安裝和使用配接器，包括可能的原因和解決方案時，可能會遇到的操作問題</span><span class="sxs-lookup"><span data-stu-id="637cf-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause and a resolution</span></span>
  
-   <span data-ttu-id="637cf-110">使用效能計數器以檢閱配接器效能</span><span class="sxs-lookup"><span data-stu-id="637cf-110">Using performance counters to review adapter performance</span></span>
  
-   <span data-ttu-id="637cf-111">處理例外狀況和錯誤，包括可能的原因和解決方式</span><span class="sxs-lookup"><span data-stu-id="637cf-111">Handling exceptions and errors, including probable cause, and a resolution</span></span>
  
## <a name="lets-get-started"></a><span data-ttu-id="637cf-112">讓我們開始吧</span><span class="sxs-lookup"><span data-stu-id="637cf-112">Let's get started</span></span>  
  
-   [<span data-ttu-id="637cf-113">診斷追蹤和訊息記錄在 Oracle E-business Suite 配接器</span><span class="sxs-lookup"><span data-stu-id="637cf-113">Diagnostic Tracing and Message Logging in the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md) 
  
-   [<span data-ttu-id="637cf-114">Oracle E-business Suite 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="637cf-114">Troubleshoot Installation Issues with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshoot-installation-issues-with-the-oracle-e-business-suite-adapter.md)  
  
-   [<span data-ttu-id="637cf-115">Oracle E-business Suite 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="637cf-115">Troubleshoot Operational Issues with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshoot-operational-issues-with-the-oracle-e-business-suite-adapter.md)
  
-   [<span data-ttu-id="637cf-116">使用效能計數器與 Oracle E-business Suite 介面卡</span><span class="sxs-lookup"><span data-stu-id="637cf-116">Use Performance Counters with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/use-performance-counters-with-the-oracle-e-business-suite-adapter.md)