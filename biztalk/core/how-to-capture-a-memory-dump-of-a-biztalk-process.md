---
title: "如何擷取 BizTalk 程序的記憶體傾印 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8053fcf3-b331-4245-b3c3-21290463e0c0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87ad0f4a3eb3a49ea789d45a707bbc8b46cb4c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-biztalk-process"></a><span data-ttu-id="1d28f-102">如何擷取 BizTalk 程序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="1d28f-102">How to Capture a Memory Dump of a BizTalk Process</span></span>
<span data-ttu-id="1d28f-103">在特定情況下，您必須擷取執行於 BizTalk Server 之程序的記憶體傾印，以便深入分析程序。</span><span class="sxs-lookup"><span data-stu-id="1d28f-103">Under certain circumstances it may be necessary to capture a memory dump of a process running on a BizTalk Server to perform an in depth analysis of the process.</span></span> <span data-ttu-id="1d28f-104">下列情況可能必須分析記憶體傾印：</span><span class="sxs-lookup"><span data-stu-id="1d28f-104">Situations that may require analysis of a memory dump include the following:</span></span>  
  
-   <span data-ttu-id="1d28f-105">程序無回應時。</span><span class="sxs-lookup"><span data-stu-id="1d28f-105">When a process is unresponsive.</span></span>  
  
-   <span data-ttu-id="1d28f-106">程序損毀時。</span><span class="sxs-lookup"><span data-stu-id="1d28f-106">When a process is crashing.</span></span>  
  
-   <span data-ttu-id="1d28f-107">程序發生記憶體溢位時。</span><span class="sxs-lookup"><span data-stu-id="1d28f-107">When a process leaks memory.</span></span>  
  
 <span data-ttu-id="1d28f-108">本節包含擷取適當類型的記憶體傾印時，應該遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="1d28f-108">This section includes the steps that should be followed to capture the appropriate type of memory dump.</span></span>  
  
## <a name="installation-of-the-iis-diagnostics-toolkit"></a><span data-ttu-id="1d28f-109">安裝 IIS Diagnostics Toolkit</span><span class="sxs-lookup"><span data-stu-id="1d28f-109">Installation of the IIS Diagnostics Toolkit</span></span>  
 <span data-ttu-id="1d28f-110">本節中主題的每個需要使用**偵錯診斷工具**IIS Diagnostics toolkit 來擷取記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="1d28f-110">Each of the topics in this section requires the use of the **Debug Diagnostics Tool** of the IIS Diagnostics Toolkit to capture a memory dump.</span></span> <span data-ttu-id="1d28f-111">若要安裝**偵錯診斷工具**IIS Diagnostics Toolkit 的請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1d28f-111">To install the **Debug Diagnostics Tool** of the IIS Diagnostics Toolkit follow these steps:</span></span>  
  
1.  <span data-ttu-id="1d28f-112">下載 IIS Diagnostics Toolkit 從[Internet Information Services 診斷工具](http://go.microsoft.com/fwlink/?LinkId=64426)。</span><span class="sxs-lookup"><span data-stu-id="1d28f-112">Download the IIS Diagnostics Toolkit from [Internet Information Services Diagnostic Tools](http://go.microsoft.com/fwlink/?LinkId=64426).</span></span>  
  
2.  <span data-ttu-id="1d28f-113">按兩下**[iisdiag.msi]**封裝啟動 IIS Diagnostics Toolkit 安裝程式並選擇**自訂**安裝類型。</span><span class="sxs-lookup"><span data-stu-id="1d28f-113">Double-click the **iisdiag.msi** package to start the IIS Diagnostics Toolkit setup program and choose the **Custom** setup type.</span></span>  
  
3.  <span data-ttu-id="1d28f-114">在**自訂安裝程式** 對話方塊中，請確認選項**Debug Diagnostics Tool 1.0**已啟用，並完成安裝程式中的步驟。</span><span class="sxs-lookup"><span data-stu-id="1d28f-114">In the **Custom Setup** dialog, ensure that the option for the **Debug Diagnostics Tool 1.0** is enabled and complete the steps in the setup program.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d28f-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="1d28f-115">In This Section</span></span>  
  
-   [<span data-ttu-id="1d28f-116">如何擷取非回應的處理序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="1d28f-116">How to Capture a Memory Dump of a Process that is Non Responsive</span></span>](../core/how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive.md)  
  
-   [<span data-ttu-id="1d28f-117">如何擷取損毀程序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="1d28f-117">How to Capture a Memory Dump of a Process that is Crashing</span></span>](../core/how-to-capture-a-memory-dump-of-a-process-that-is-crashing.md)  
  
-   [<span data-ttu-id="1d28f-118">如何擷取發生記憶體溢位的處理程序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="1d28f-118">How to Capture a Memory Dump of a Process that is Leaking Memory</span></span>](../core/how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory.md)  
  
-   [<span data-ttu-id="1d28f-119">如何使用 Debug Diagnostics 分析記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="1d28f-119">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)