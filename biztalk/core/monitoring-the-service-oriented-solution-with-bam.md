---
title: "監控服務導向解決方案使用 BAM |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring, service solutions
- service solution tutorial, monitoring
- OrchestrationEventStream object
ms.assetid: 9b251580-9371-490e-9218-0ce3f6b00fa6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1aeaec2513ebe3c6d7fe62ef542b6f044bca56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-the-service-oriented-solution-with-bam"></a>監控服務導向 BAM 解決方案
解決方案會監視所有版本中的活動**CustomerService**協調流程使用商務活動監控 (BAM) API。 更具體來說，它會使用新**OrchestrationEventStream**物件。  
  
## <a name="what-is-the-orchestrationeventstream-object"></a>何謂 OrchestrationEventStream 物件？  
 新**OrchestrationEventStream**物件可讓追蹤及監控從協調流程。 擷取的資訊在交易上會與協調流程狀態一致。 例如，若協調流程主控件執行個體在協調流程執行中期重新開始，則協調流程執行個體會從執行個體的最後持續點重新開始。 **OrchestrationEventStream**類別可確保擷取的資料在交易上一致的協調流程執行個體的上次保存點。 所有的**OrchestrationEventStream**方法是靜態的因此您的協調流程不需要建立它的執行個體。  
  
> [!NOTE]
>  若要使用**OrchestrationEventStream**物件，您需要將參考加入至**Microsoft.BizTalk.Bam.XLANGs**和**Microsoft.BizTalk.Bam.EventObservation**組件。 雖然**OrchestrationEventStream**物件是處於**Microsoft.BizTalk.Bam.EventObservation**命名空間，它位於**Microsoft.BizTalk.Bam.XLANGs**組件。  
  
 雖然追蹤設定檔編輯器 (TPE) 是使用 BAM 的偏好方式，但是 TPE 無法擷取協調流程變數值，也無法處理自訂物件。 解決方案可使用 BAM API 來克服這些限制。  
  
 如需 BAM 的一般資訊，請參閱[使用商務活動監控](../core/using-business-activity-monitoring.md)。 如需追蹤設定檔編輯器 (TPE) 的相關資訊，請參閱[追蹤設定檔編輯器](../core/tracking-profile-editor.md)。  
  
## <a name="wrapping-the-orchestrationeventstream-object"></a>包裝 OrchestrationEventStream 物件  
 服務導向解決方案會包裝**OrchestrationEventStream**類別**ServiceLevelTracking**類別。 **ServiceLevelTracking**類別提供應用程式特定的里程碑方法，並隱藏一些詳細資料的使用**OrchestrationEventStream**。  
  
 在**OrchestrationEventStream**的所有方法**ServiceLevelTracking**都是靜態的。 所以，協調流程或自訂元件不需要建立它的執行個體。 開始追蹤活動的方法， **TrackingBeginRequest**，傳回唯一的活動執行個體識別碼。 所有後續的追蹤事件必須與此活動的執行個體 ID 相關聯才能正確擷取服務層級資料，因為它是執行個體的唯一**CustomerService**協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)   
 [實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md)