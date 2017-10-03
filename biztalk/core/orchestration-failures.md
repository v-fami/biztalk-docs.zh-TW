---
title: "協調流程失敗 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Catch Exception block [Orchestration Designer], suspended orchestrations
- HAT, Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], HAT
- orchestrations, troubleshooting [HAT]
- orchestrations, errors
- HAT, Orchestration Debugger
- Orchestration Debugger
- errors, orchestrations
- HAT, troubleshooting orchestrations
- orchestrations, HAT
- HAT, orchestrations
ms.assetid: d0a799fb-7859-4774-b444-979f22f04215
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d95cab903ae9bf5faacdf385f667c33f9a2d5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-failures"></a>協調流程失敗
協調流程的複雜性不同；例如，協調流程可能呼叫 .NET 物件，或經由轉換和指派圖形來建構訊息。 所以，因為其內容的多樣性以及自訂化程度的不同，不可能將每個可能的失敗都列出。 不過，協調流程中發生的所有失敗都會顯示為例外狀況。  
  
 如果協調流程不包含任何**CatchException**例外狀況，例外狀況的圖形會導致協調流程為 「 暫止，但不可繼續。 這表示訊息和服務執行個體的追蹤或 WMI 指令碼中，無法復原的執行個體。 不過，您可以在其中儲存與 「 已擱置相關聯的所有訊息 （不可繼續） 的執行個體的診斷和手動重試使用追蹤 （或 WMI 指令碼）。  
  
 若要診斷此問題，請使用協調流程偵錯工具若要查看執行個體已暫停之前執行的最後一個圖形。 您也可以使用「協調流程偵錯工具」檢視例外狀況的詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、 連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)   
 [偵錯協調流程](../core/debugging-an-orchestration.md)