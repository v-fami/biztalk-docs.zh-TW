---
title: 使用協調流程偵錯工具時的考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, modified orchestrations
- Orchestration Debugger, planning
- atomic scopes
- planning, Orchestration Debugger
- Orchestration Debugger, atomic scopes
- Orchestration Debugger, simple types
- orchestrations, modifying
ms.assetid: 55bfef48-08bd-48bb-abd5-7264e683da46
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e3e244691d61ef27c55f606414dd08857d58f14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998151"
---
# <a name="considerations-when-using-orchestration-debugger"></a>使用協調流程偵錯工具時的考量
以下為使用協調流程偵錯工具時需考量的事項。  
  
## <a name="tracking-atomic-scopes"></a>追蹤不可部分完成的範圍  
 協調流程會包含不可部分完成的範圍，以包含對規則引擎的呼叫。 當您連接至協調流程偵錯工具中的執行個體時，協調流程執行個體中不可部分完成的範圍將會導致追蹤的事件清單中出現間距。 發生的原因有兩個：  
  
- 因為直到範圍認可之前，不可部分完成交易中圖形的事件都不會持續。  
  
- 偵錯工具會將事件重新載入至清單結尾，因此在即時工作階段，所有的間距都還沒有填滿。  
  
  若您重新整理檢視即可消除間距。  
  
> [!NOTE]
>  您無法在不可部分完成範圍內的圖形上設定中斷點。  
  
## <a name="setting-breakpoints-in-the-exception-handler-scope"></a>在例外處理常式範圍內設定中斷點  
 如果在例外狀況 Catch 處理常式設定中斷點，例外狀況類型必須標示為可序列化，否則協調流程偵錯工具便不會在設定的中斷點停止。 這是因為協調流程偵錯工具會在中斷點持續，因此，當不可序列化物件處於協調流程執行個體狀態中時，便會擲回持續性例外狀況。在此情況下，您也會收到 DebugBreakPointFailedException 例外狀況。  
  
## <a name="tracking-a-modified-orchestration"></a>追蹤修改的協調流程  
 若您不變更版本編號而想追蹤修改的協調流程，則必須重新啟動已登錄協調流程的所有主控件執行個體。 如此即可在您逐步完成協調流程偵錯工具時，確保新部署版本中的圖形變更可正確顯示。  
  
## <a name="tracking-simple-types"></a>追蹤簡單型別  
 協調流程偵錯工具僅支援簡單型別。 例如，若您追蹤包含 .NET 物件的多個訊息，您可以檢視所有訊息部分的屬性，但是 .NET 物件屬性為例外。  
  
 當協調流程顯示為「在中斷點」狀態，且協調流程偵錯工具已啟動時，您可以執行下列動作：  
  
-   使用**附加**服務選項。  
  
-   檢視已完成的步驟。  
  
-   檢視變數和訊息的狀態。  
  
-   設定其他中斷點。  
  
-   選取 **繼續服務**選項。  
  
-   視需要重複任何步驟。  
  
## <a name="see-also"></a>另請參閱  
 [在協調流程偵錯工具的互動模式](../core/interactive-mode-in-orchestration-debugger.md)   
 [偵錯協調流程](../core/debugging-an-orchestration.md)