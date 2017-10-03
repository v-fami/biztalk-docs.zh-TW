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
# <a name="how-to-use-debug-diagnostics-to-analyze-a-memory-dump"></a>如何使用 Debug Diagnostics 分析記憶體傾印
IIS Diagnostics**偵錯診斷工具**包含功能，可以提供擷取的記憶體傾印檔案的基本分析。 若要執行記憶體傾印檔案的分析，請遵循以下的步驟：  
  
### <a name="to-analyze-the-dump-file"></a>分析傾印檔案  
  
1.  啟動偵錯診斷工具，從**啟動**，**程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。  
  
2.  按一下**進階分析** 索引標籤。  
  
3.  在下**可用的分析指令碼**按一下以選取**當機/沒有反應分析器**分析當機/沒有反應的傾印，或按一下以選取**記憶體不足的壓力分析**來分析記憶體懷疑流失記憶體之處理序傾印。  
  
4.  按一下**新增資料檔案**按鈕來瀏覽至產生的傾印檔案，並按一下**開啟** 按鈕，新增傾印檔案可能要分析的資料檔案的清單。  
  
5.  按一下可選取已新增的傾印檔案。  
  
6.  按一下**開始分析** 按鈕。  
  
    > [!NOTE]
    >  此分析器會嘗試從網際網路尋找及下載適當的符號檔 (如果本機電腦上未安裝符號檔)。 如果在 BTSNTSvc.exe 處理序正在執行自訂程式碼，更新**符號搜尋路徑的偵錯**中可用的選項**資料夾和搜尋路徑** 索引標籤**選項 （& s)設定**對話方塊包含適當的符號檔。 按一下**工具**功能表，然後選取**選項和設定**顯示**選項和設定**對話方塊。  
  
7.  一旦完成分析，就會產生 .mht 檔案格式的報告，並將其顯示於 Internet Explorer 中。 根據預設，此報告會儲存到本機電腦的 \Program Files\IIS Resources\DebugDiag\Reports 目錄。  
  
## <a name="see-also"></a>另請參閱  
 [如何擷取 BizTalk 程序的記憶體傾印](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)