---
title: "如何擷取損毀程序的記憶體傾印 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f436b72-2b6a-4519-acc3-e7ba978651fe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda8dd26908b241a9897bb4f1b2ba697b55f6532
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-crashing"></a><span data-ttu-id="fc108-102">如何擷取損毀程序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="fc108-102">How to Capture a Memory Dump of a Process that is Crashing</span></span>
<span data-ttu-id="fc108-103">BizTalk 處理序 BTSNTSvc.exe 定義為**損毀**windows 已意外終止程序。</span><span class="sxs-lookup"><span data-stu-id="fc108-103">The BizTalk process BTSNTSvc.exe is defined as **crashing** when the process is unexpectedly terminated by Windows.</span></span> <span data-ttu-id="fc108-104">損毀一般是由程序中未處理的例外狀況造成的，例如存取違規或堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="fc108-104">A crash is typically caused by an unhandled exception in the process such as an access violation or a stack overflow.</span></span> <span data-ttu-id="fc108-105">在這些情況下，Windows 預設偵錯工具，Dr。Watson (drwtsn32.exe) 攔截例外狀況和終止處理序。</span><span class="sxs-lookup"><span data-stu-id="fc108-105">In these situations, the Windows default debugger, Dr. Watson (drwtsn32.exe) catches the exception and terminates the process.</span></span>  
  
 <span data-ttu-id="fc108-106">若要擷取損毀程序的記憶體傾印，請依照下列步驟設定 Debug Diagnostics 工具，攔截未處理的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="fc108-106">To capture a memory dump of a process that is crashing, configure the Debug Diagnostics tool to catch the unhandled exception by following these steps:</span></span>  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-crash-dump"></a><span data-ttu-id="fc108-107">若要設定 Debug Diagnostics 工具來擷取損毀的傾印</span><span class="sxs-lookup"><span data-stu-id="fc108-107">To configure the Debug Diagnostics tool to capture a crash dump</span></span>  
  
1.  <span data-ttu-id="fc108-108">啟動偵錯診斷工具，從**啟動**，**所有程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。</span><span class="sxs-lookup"><span data-stu-id="fc108-108">Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="fc108-109">如果**選取規則類型**不會顯示 新增規則精靈 對話方塊中，按一下**工具**功能表上，選取**規則動作**，然後按一下**加入規則**以顯示 新增規則精靈。</span><span class="sxs-lookup"><span data-stu-id="fc108-109">If the **Select Rule Type** dialog of the Add Rule Wizard is not displayed, click the **Tools** menu, select **Rule Actions**, and click **Add Rule** to display the Add Rule Wizard.</span></span>  
  
3.  <span data-ttu-id="fc108-110">選取**損毀**選項**選取規則類型**對話方塊，再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fc108-110">Select the **Crash** option in the **Select Rule Type** dialog and click **Next**.</span></span>  
  
4.  <span data-ttu-id="fc108-111">選取**特定處理序**中**選取目標類型**對話方塊，再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fc108-111">Select **A specific process** in the **Select Target Type** dialog and click **Next**.</span></span>  
  
5.  <span data-ttu-id="fc108-112">選取的 BTSNTSvc.exe 處理序已當機，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fc108-112">Select the BTSNTSvc.exe process that is crashing and click **Next**.</span></span>  
  
6.  <span data-ttu-id="fc108-113">在**進階組態**對話方塊中，按一下**下一步**接受預設值。</span><span class="sxs-lookup"><span data-stu-id="fc108-113">In the **Advanced Configuration** dialog click **Next** to accept the default values.</span></span>  
  
7.  <span data-ttu-id="fc108-114">在**選取傾印位置和規則名稱**對話方塊中，按一下**下一步**接受預設值。</span><span class="sxs-lookup"><span data-stu-id="fc108-114">In the **Select Dump Location And Rule Name** dialog click **Next** to accept the default values.</span></span>  
  
8.  <span data-ttu-id="fc108-115">在**規則完成**對話方塊中，按一下**完成**以接受預設值的**立即啟動規則**。</span><span class="sxs-lookup"><span data-stu-id="fc108-115">In the **Rule Completed** dialog click **Finish** to accept the default value of **Activate the rule now**.</span></span>  
  
9. <span data-ttu-id="fc108-116">根據預設，處理程序的記憶體傾印會儲存到 \Program Files\IIS Resources\DebugDiag\Logs\\<*損毀規則的名稱*> 目錄的本機電腦下一次未處理處理序中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fc108-116">By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\\<*name of crash rule*> directory of the local computer the next time that an unhandled exception occurs in the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc108-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc108-117">See Also</span></span>  
 [<span data-ttu-id="fc108-118">如何使用 Debug Diagnostics 分析記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="fc108-118">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)