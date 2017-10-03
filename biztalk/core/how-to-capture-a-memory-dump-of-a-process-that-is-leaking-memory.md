---
title: "如何擷取發生記憶體溢位的處理程序的記憶體傾印 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67404919-33a6-40ac-b1c4-09841db12fcf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2999ce9a188b2d9b94df11328485e8b7440ecec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory"></a>如何擷取已發生記憶體溢位之程序的記憶體傾印
當 BizTalk 程序 BTSNTSvc.exe 無法釋放不再需要的記憶體，因此導致一段時間後可用記憶體數量減少，就會定義為記憶體溢位。 程序的記憶體使用量可以藉由檢視底下的值判斷**記憶體使用量**資料行**處理程序** 索引標籤位於**工作管理員**。 如果程序在一段時間後持續使用記憶體，而未釋放記憶體，便會嚴重影響整體系統效能。  
  
 本主題包含逐步指示，可讓您透過「規則」或手動擷取疑似發生記憶體溢位之 BizTalk 程序的記憶體傾印。 如果無法預測記憶體溢位的發生，請使用手動擷取記憶體傾印的方法。  
  
### <a name="to-capture-a-memory-dump-of-a-process-that-is-leaking-memory-by-using-a-rule"></a>若要使用規則，擷取發生記憶體溢位之程序的記憶體傾印  
  
1.  啟動偵錯診斷工具，從**啟動**，**所有程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。  
  
2.  如果**選取規則類型**不會顯示 新增規則精靈 對話方塊中，按一下**工具**功能表上，選取**規則動作**，然後按一下**加入規則**以顯示 新增規則精靈。  
  
3.  選取**記憶體和控制溢位**選項**選取規則類型**對話方塊，再按一下**下一步**。  
  
4.  選取疑似遺漏記憶體，然後按一下的 BTSNTSvc.exe 處理序**下一步**。  
  
5.  在**設定追蹤持續期間**對話方塊中，依照下列步驟：  
  
    1.  如果立即發生所觀察的程序記憶體成長，核取選項**開始記憶體追蹤立即啟動規則時**。 如果未立即發生所觀察的程序記憶體成長，指定適當分鐘數**熱身時間**之後將啟動記憶體追蹤 文字方塊。  
  
        > [!NOTE]
        >  如果由於載入特定元件至記憶體 (例如 BizTalk 協調流程參考外部元件時) 而導致記憶體溢位，可能不會立即發生所觀察的程序記憶體成長。  
  
    2.  指定的分鐘數的適當數目**追蹤時間**記憶體追蹤會停止在其後的文字方塊。 這必須是可以重現記憶體溢位、足夠長的分鐘數。 經過這段期間，便會擷取程序的記憶體傾印。  
  
    3.  核取選項**損毀的自動建立規則以在非預期的處理序結束取得使用者傾印**。  
  
    4.  按一下 **[下一步]**。  
  
6.  在**選取傾印位置和規則名稱**對話方塊中，按一下**下一步**接受預設值。  
  
7.  在**規則完成**對話方塊中，按一下**完成**以接受預設值的**立即啟動規則**。  
  
8.  根據預設，處理程序的記憶體傾印會儲存到 \Program Files\IIS Resources\DebugDiag\Logs\\<*損毀規則的名稱*> 目錄中所指定的時間間隔之後在本機電腦**設定追蹤持續期間**經過對話方塊。  
  
### <a name="to-manually-capture-a-memory-dump-of-a-process-that-is-leaking-memory"></a>若要手動擷取發生記憶體溢位之程序的記憶體傾印  
  
1.  啟動偵錯診斷工具，從**啟動**，**所有程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。  
  
2.  如果**選取規則類型**對話方塊的 新增規則精靈，請按一下**取消**。  
  
3.  按一下以選取**處理程序**Debug Diagnostic Tool 索引標籤。  
  
4.  以滑鼠右鍵按一下疑似遺漏記憶體，然後按一下的 BTSNTSvc.exe 程序**監視溢**。  
  
5.  監視中的程序的記憶體使用量**工作管理員**和程序的記憶體使用量接近為 BizTalk 電腦上的可用記憶體的 60-80%時手動擷取記憶體傾印程序以滑鼠右鍵按一下處理程序，並選取選項以**建立完整使用者傾印**。  
  
6.  根據預設，程序的記憶體傾印會儲存在本機電腦的 \Program Files\IIS Resources\DebugDiag\Logs\Misc\ 目錄。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 Debug Diagnostics 分析記憶體傾印](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)