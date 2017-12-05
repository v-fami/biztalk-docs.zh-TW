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
ms.openlocfilehash: e87664180b7ad4d5fdcd121542974a08b8634d55
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-crashing"></a>如何擷取損毀程序的記憶體傾印
BizTalk 處理序 BTSNTSvc.exe 定義為**損毀**windows 已意外終止程序。 損毀一般是由程序中未處理的例外狀況造成的，例如存取違規或堆疊溢位。 在這些情況下，Windows 預設偵錯工具，Dr。Watson (drwtsn32.exe) 攔截例外狀況和終止處理序。  
  
 若要擷取損毀程序的記憶體傾印，請依照下列步驟設定 Debug Diagnostics 工具，攔截未處理的例外狀況：  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-crash-dump"></a>若要設定 Debug Diagnostics 工具來擷取損毀的傾印  
  
1.  啟動偵錯診斷工具，從**啟動**，**所有程式**， **IIS Diagnostics**， **Debug Diagnostics Tools**， **偵錯診斷工具 1.0**。  
  
2.  如果**選取規則類型**不會顯示 新增規則精靈 對話方塊中，按一下**工具**功能表上，選取**規則動作**，然後按一下**加入規則**以顯示 新增規則精靈。  
  
3.  選取**損毀**選項**選取規則類型**對話方塊，再按一下**下一步**。  
  
4.  選取**特定處理序**中**選取目標類型**對話方塊，再按一下**下一步**。  
  
5.  選取的 BTSNTSvc.exe 處理序已當機，然後按**下一步**。  
  
6.  在**進階組態**對話方塊中，按一下**下一步**接受預設值。  
  
7.  在**選取傾印位置和規則名稱**對話方塊中，按一下**下一步**接受預設值。  
  
8.  在**規則完成**對話方塊中，按一下**完成**以接受預設值的**立即啟動規則**。  
  
9. 根據預設，處理程序的記憶體傾印會儲存到 \Program Files\IIS Resources\DebugDiag\Logs\\<*損毀規則的名稱*\>目錄的本機電腦下一次處理序中發生未處理的例外狀況。  
  
## <a name="see-also"></a>請參閱  
 [如何使用 Debug Diagnostics 分析記憶體傾印](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)