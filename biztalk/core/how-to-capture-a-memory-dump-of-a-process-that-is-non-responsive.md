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
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive"></a>如何擷取沒有回應之處理序的記憶體傾印
BizTalk 處理序 BTSNTSvc.exe 定義為**溢出**程序似乎停止回應。 處理序停止回應的常見徵兆包括：  
  
-   協調流程似乎停止執行。  
  
-   沒有處理訊息。  
  
-   發生一般逾時問題。  
  
-   BizTalk 處理序 BTSNTSvc.exe 耗用異常大量的 CPU 週期，如中所示**處理程序** 索引標籤**工作管理員**。  
  
 若要在停止回應的 BTSNTSvc.exe 處理序中擷取記憶體傾印，請遵循以下步驟。  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-hang-dump"></a>設定 Debug Diagnostics 工具來擷取停止回應的傾印  
  
1.  啟動偵錯診斷工具，從**啟動**，**所有程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。  
  
2.  如果**選取規則類型**規則組態精靈 對話方塊隨即出現，請按一下**取消** 按鈕。  
  
3.  按一下**處理程序**Debug Diagnostic Tool 索引標籤。  
  
4.  以滑鼠右鍵按一下沒有回應的 BTSNTSvc.exe 處理序，然後選取**建立完整使用者傾印**。 根據預設，此處理序的記憶體傾印會儲存到本機電腦的 \Program Files\IIS Resources\DebugDiag\Logs\Misc 目錄。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 Debug Diagnostics 分析記憶體傾印](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)