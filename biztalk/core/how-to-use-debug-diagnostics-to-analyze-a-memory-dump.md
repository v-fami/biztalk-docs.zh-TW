---
title: "如何使用 Debug Diagnostics 分析記憶體傾印 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986a91a7-feab-4014-bbd5-e8b966b8b841
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccc0faf72c9123ab7a501af8520f273e8c528b8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-debug-diagnostics-to-analyze-a-memory-dump"></a><span data-ttu-id="0a1dd-102">如何使用 Debug Diagnostics 分析記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="0a1dd-102">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>
<span data-ttu-id="0a1dd-103">IIS Diagnostics**偵錯診斷工具**包含功能，可以提供擷取的記憶體傾印檔案的基本分析。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-103">The IIS Diagnostics **Debug Diagnostics Tool** includes a feature that can provide a basic analysis of a captured memory dump file.</span></span> <span data-ttu-id="0a1dd-104">若要執行記憶體傾印檔案的分析，請遵循以下的步驟：</span><span class="sxs-lookup"><span data-stu-id="0a1dd-104">To perform an analysis of a memory dump file follow these steps.</span></span>  
  
### <a name="to-analyze-the-dump-file"></a><span data-ttu-id="0a1dd-105">分析傾印檔案</span><span class="sxs-lookup"><span data-stu-id="0a1dd-105">To analyze the dump file</span></span>  
  
1.  <span data-ttu-id="0a1dd-106">啟動偵錯診斷工具，從**啟動**，**程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-106">Launch the Debug Diagnostics tool from **Start**, **Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="0a1dd-107">按一下**進階分析** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-107">Click the **Advanced Analysis** tab.</span></span>  
  
3.  <span data-ttu-id="0a1dd-108">在下**可用的分析指令碼**按一下以選取**當機/沒有反應分析器**分析當機/沒有反應的傾印，或按一下以選取**記憶體不足的壓力分析**來分析記憶體懷疑流失記憶體之處理序傾印。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-108">Under **Available Analysis Scripts** click to select **Crash/Hang Analyzers** to analyze a crash/hang dump or click to select **Memory Pressure Analysis** to analyze a memory dump of a process suspected of leaking memory.</span></span>  
  
4.  <span data-ttu-id="0a1dd-109">按一下**新增資料檔案**按鈕來瀏覽至產生的傾印檔案，並按一下**開啟** 按鈕，新增傾印檔案可能要分析的資料檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-109">Click the **Add Data Files** button to browse to the generated dump file and click the **Open** button to add the dump file to the possible list of data files to be analyzed.</span></span>  
  
5.  <span data-ttu-id="0a1dd-110">按一下可選取已新增的傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-110">Click to select the dump file that was added.</span></span>  
  
6.  <span data-ttu-id="0a1dd-111">按一下**開始分析** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-111">Click the **Start Analysis** button.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a1dd-112">此分析器會嘗試從網際網路尋找及下載適當的符號檔 (如果本機電腦上未安裝符號檔)。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-112">The analyzer attempts to locate and download the appropriate symbol files from the internet if the symbol files are not installed on the local computer.</span></span> <span data-ttu-id="0a1dd-113">如果在 BTSNTSvc.exe 處理序正在執行自訂程式碼，更新**符號搜尋路徑的偵錯**中可用的選項**資料夾和搜尋路徑** 索引標籤**選項 （& s)設定**對話方塊包含適當的符號檔。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-113">If custom code is being executed in the BTSNTSvc.exe process, update the **Symbol Search Path For Debugging** option available in the **Folder And Search Paths** tab of the **Options & Settings** dialog to include the appropriate symbol files.</span></span> <span data-ttu-id="0a1dd-114">按一下**工具**功能表，然後選取**選項和設定**顯示**選項和設定**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-114">Click the **Tools** menu and select **Options And Settings** to display the **Options & Settings** dialog.</span></span>  
  
7.  <span data-ttu-id="0a1dd-115">一旦完成分析，就會產生 .mht 檔案格式的報告，並將其顯示於 Internet Explorer 中。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-115">Once the analysis is complete a report is generated in .mht file format and displayed in Internet Explorer.</span></span> <span data-ttu-id="0a1dd-116">根據預設，此報告會儲存到本機電腦的 \Program Files\IIS Resources\DebugDiag\Reports 目錄。</span><span class="sxs-lookup"><span data-stu-id="0a1dd-116">By default this report is saved to the \Program Files\IIS Resources\DebugDiag\Reports directory of the local computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1dd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a1dd-117">See Also</span></span>  
 [<span data-ttu-id="0a1dd-118">如何擷取 BizTalk 程序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="0a1dd-118">How to Capture a Memory Dump of a BizTalk Process</span></span>](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)