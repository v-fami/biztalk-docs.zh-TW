---
title: 建立自訂的例外狀況處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 401aec8d-d9ca-4a88-9e5b-d3ab605dc0a1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33d49fddb8a42c440f62acdd4ea337f43b876f6b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971519"
---
# <a name="creating-custom-exception-handlers"></a>建立自訂的例外狀況處理常式
若要偵測和回應例外狀況的應用程式，開發人員必須提供例外狀況處理常式。 這個例外狀況處理常式可以訂閱一種例外狀況訊息或從一個系統或應用程式的部分或所有組件產生的例外狀況訊息。 例如，您可能需要在單一處理常式的所有訊息從特定的系統 （例如薪資系統中發生任何例外），或可能會改為所需目標的處理常式 （例如偵測是否檢查列印程序的特定失敗失敗）。  
  
 若要訂閱特定類型的例外狀況，請使用篩選對啟動的 [接收] 圖形中，協調流程，如下列範例所示。  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.Schemas.Property.FaultCode == "1000";  
```  
  
 您也可以篩選條件將訊息傳送至檔案系統，或透過電子郵件訊息符合特定篩選條件的傳送埠。  
  
## <a name="sample-exception-handling-projects"></a>範例例外狀況處理的專案  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例 BizTalk 應用程式，示範例外狀況處理。 可以在 \Source\Samples\Exception 處理資料夾中找到這些範例。  
  
 另外還有四個 BizTalk 專案，位於 GlobalBank.ESB.Samples.ExceptionHandling 解決方案中，示範如何使用 ESB 失敗的協調流程例外狀況路由機制。 這些專案預先設定為部署到 GlobalBank.ESB BizTalk 應用程式。 這些專案包括下列各項：  
  
- **ESB。ExceptionHandling.Schemas。** 此專案包含範例協調流程使用的結構描述。  
  
- **ESB。ExceptionHandling.Pipelines。** 此專案包含將用於傳送埠訂閱的所有例外狀況的例外狀況處理器設定的傳送管線。 這包括產生 BizTalk 和例外狀況管理架構所產生的例外狀況的例外狀況。  
  
- **ESB。ExceptionHandling.Processes。** 此專案包含 EAIProcess.odx 協調流程，藉由嘗試除以零並呼叫模擬例外狀況**CreateFaultMessage**並**AddMessage**来產生合適的方法錯誤訊息，如 圖 1 所示。  
  
   ![協調流程處理範例](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "第 4 章第 OrchestrationProcessesSample")  
  
   **圖 1**  
  
  **EAIProcess.odx 協調流程中處理程序範例專案**  
  
- **ESB。ExceptionHandling.Handlers。** 此專案包含 EAIGenericHandler.odx 協調流程中，它會呼叫**GetMessages**方法，並逐一**MessageCollection**使用**MoveNext**方法，如 [圖 2] 所示。  
  
  ![協調流程處理常式範例泛型](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "第 4 章第 OrchestrationHandlersSampleGeneric")  
  
  **圖 2**  
  
  **EAIGenericHandler.odx 中的協調流程處理常式範例專案**  
  
  ESB。ExceptionHandling.Handlers 專案也包含 EAIProcessHandler.odx 協調流程中，它會呼叫**GetMessage**並**GetException**方法，如 [圖 3] 所示。  
  
  ![協調流程處理常式範例處理程序](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "第 4 章第 OrchestrationHandlersSampleProcess")  
  
  **圖 3**  
  
  **EAIProcessHandler.odx 中的協調流程處理常式範例專案**