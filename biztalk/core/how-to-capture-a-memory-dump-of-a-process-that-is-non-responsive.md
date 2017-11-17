---
title: "如何擷取非回應的處理序的記憶體傾印 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ad53376-2fab-4dee-8a6a-a44d157390f2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 520921010a8bbfd73de8c3b305a1270ca8363c46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive"></a><span data-ttu-id="cb8ff-102">如何擷取沒有回應之處理序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="cb8ff-102">How to Capture a Memory Dump of a Process that is Non Responsive</span></span>
<span data-ttu-id="cb8ff-103">BizTalk 處理序 BTSNTSvc.exe 定義為**溢出**程序似乎停止回應。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-103">The BizTalk process BTSNTSvc.exe is defined as **hanging** when the process seems to stop responding.</span></span> <span data-ttu-id="cb8ff-104">處理序停止回應的常見徵兆包括：</span><span class="sxs-lookup"><span data-stu-id="cb8ff-104">Common symptoms of a process hang include:</span></span>  
  
-   <span data-ttu-id="cb8ff-105">協調流程似乎停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-105">Orchestrations appear to stop running.</span></span>  
  
-   <span data-ttu-id="cb8ff-106">沒有處理訊息。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-106">Messages aren’t being processed.</span></span>  
  
-   <span data-ttu-id="cb8ff-107">發生一般逾時問題。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-107">General timeout issues occur.</span></span>  
  
-   <span data-ttu-id="cb8ff-108">BizTalk 處理序 BTSNTSvc.exe 耗用異常大量的 CPU 週期，如中所示**處理程序** 索引標籤**工作管理員**。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-108">The BizTalk process BTSNTSvc.exe consumes an unusually high amount of CPU cycles as viewed in the **Processes** tab of **Task Manager**.</span></span>  
  
 <span data-ttu-id="cb8ff-109">若要在停止回應的 BTSNTSvc.exe 處理序中擷取記憶體傾印，請遵循以下步驟。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-109">To capture a memory dump of a hanging BTSNTSvc.exe process, follow these steps.</span></span>  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-hang-dump"></a><span data-ttu-id="cb8ff-110">設定 Debug Diagnostics 工具來擷取停止回應的傾印</span><span class="sxs-lookup"><span data-stu-id="cb8ff-110">To configure the Debug Diagnostics tool to capture a hang dump</span></span>  
  
1.  <span data-ttu-id="cb8ff-111">啟動偵錯診斷工具，從**啟動**，**所有程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-111">Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="cb8ff-112">如果**選取規則類型**規則組態精靈 對話方塊隨即出現，請按一下**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-112">If the **Select Rule Type** dialog of the Rules Configuration Wizard is displayed, click the **Cancel** button.</span></span>  
  
3.  <span data-ttu-id="cb8ff-113">按一下**處理程序**Debug Diagnostic Tool 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-113">Click the **Processes** tab of the Debug Diagnostic Tool.</span></span>  
  
4.  <span data-ttu-id="cb8ff-114">以滑鼠右鍵按一下沒有回應的 BTSNTSvc.exe 處理序，然後選取**建立完整使用者傾印**。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-114">Right click the unresponsive BTSNTSvc.exe process and select **Create Full Userdump**.</span></span> <span data-ttu-id="cb8ff-115">根據預設，此處理序的記憶體傾印會儲存到本機電腦的 \Program Files\IIS Resources\DebugDiag\Logs\Misc 目錄。</span><span class="sxs-lookup"><span data-stu-id="cb8ff-115">By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\Misc directory of the local computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8ff-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb8ff-116">See Also</span></span>  
 [<span data-ttu-id="cb8ff-117">如何使用 Debug Diagnostics 分析記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="cb8ff-117">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)