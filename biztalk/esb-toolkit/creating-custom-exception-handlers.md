---
title: "建立自訂例外狀況處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401aec8d-d9ca-4a88-9e5b-d3ab605dc0a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91f725084c838d026f9028f0ac2e684ec2d727c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-exception-handlers"></a>建立自訂例外狀況處理常式
若要偵測和回應例外狀況的應用程式，開發人員必須提供例外狀況處理常式。 這個例外狀況處理常式可以訂閱至單一類型的例外狀況訊息，或從部分或所有組件的系統或應用程式產生的例外狀況訊息。 例如，從特定的系統 （例如的薪資系統中發生任何例外），所有訊息，您可能需要單一處理常式，或可能會改為所需目標的處理常式專屬的失敗 （例如偵測是否檢查列印程序失敗）。  
  
 若要訂閱特定類型的例外狀況，請使用協調流程具有 「 啟動接收 」 圖形上的篩選，如下列範例所示。  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.Schemas.Property.FaultCode == "1000";  
```  
  
 您也可能篩選條件將訊息傳送至檔案系統，或透過電子郵件訊息符合特定篩選條件的傳送埠。  
  
## <a name="sample-exception-handling-projects"></a>範例例外狀況處理專案  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例 BizTalk 應用程式，示範例外狀況處理。 這些範例可以找到 \Source\Samples\Exception 處理資料夾中。  
  
 也有四個 BizTalk 專案中，位於 GlobalBank.ESB.Samples.ExceptionHandling 方案中，示範如何使用 ESB 無法協調流程的例外狀況路由機制。 這些專案已預先設定以部署到 GlobalBank.ESB BizTalk 應用程式。 專案如下所示：  
  
-   **ESB。ExceptionHandling.Schemas。** 此專案包含的範例協調流程使用的結構描述。  
  
-   **ESB。ExceptionHandling.Pipelines。** 此專案包含將用於傳送埠，以訂閱的所有例外狀況的例外狀況處理器設定的傳送管線。 這包括由 BizTalk 和例外狀況管理架構所產生的例外狀況產生的例外狀況。  
  
-   **ESB。ExceptionHandling.Processes。** 此專案包含 EAIProcess.odx 協調流程，會嘗試除以零並呼叫模擬例外狀況**CreateFaultMessage**和**AddMessage**来產生適當的方法錯誤訊息，如圖 1 所示。  
  
     ![協調流程處理範例](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "第 4 章第 OrchestrationProcessesSample")  
  
     **圖 1**  
  
 **EAIProcess.odx 協調流程處理程序範例專案中**  
  
-   **ESB。ExceptionHandling.Handlers。** 此專案包含 EAIGenericHandler.odx 協調流程中，它會呼叫**GetMessages**方法逐一查看**MessageCollection**使用**MoveNext**方法，如圖 2 所示。  
  
 ![協調流程處理常式範例泛型](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "第 4 章第 OrchestrationHandlersSampleGeneric")  
  
 **圖 2**  
  
 **EAIGenericHandler.odx 協調流程處理常式範例專案中**  
  
 ESB。ExceptionHandling.Handlers 專案也包含 EAIProcessHandler.odx 協調流程中，它會呼叫**GetMessage**和**GetException**方法，如圖 3 所示。  
  
 ![協調流程處理常式範例處理序](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "第 4 章第 OrchestrationHandlersSampleProcess")  
  
 **圖 3**  
  
 **EAIProcessHandler.odx 協調流程處理常式範例專案中**