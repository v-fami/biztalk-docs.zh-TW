---
title: "監視與 BAM 商務程序管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, monitoring
- monitoring, process management solutions
ms.assetid: 7c5fde9d-6eef-41c9-979c-ac7e5a172812
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26a8b795b90b75518f6c1ec21a6ca6d8f0f0d6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-the-business-process-management-solution-with-bam"></a>使用 BAM 監控商務程序管理解決方案
解決方案可使用「商務活動監控」(BAM) API 監控處理訂單的步驟。 商務程序的設計會分割多個階段中的活動。 整個活動可以重新組合，以建立連續的程序。 BAM 也提供彙總資料，讓您知道不同的後端系統需要花費多少時間、已完成的訂單數和其他類似資料。  
  
 如同服務導向解決方案中，使用新**OrchestrationEventStream**物件。 如需討論**OrchestrationEventStream**物件，請參閱中的 「 什麼是 OrchestrationEventStream 物件 >[監控服務導向解決方案使用 BAM](../core/monitoring-the-service-oriented-solution-with-bam.md)。  
  
 如需 BAM 的一般資訊，請參閱[使用商務活動監控](../core/using-business-activity-monitoring.md)。 如需追蹤設定檔編輯器 (TPE) 的相關資訊，請參閱[追蹤設定檔編輯器](../core/tracking-profile-editor.md)。  
  
## <a name="wrapping-the-orchestrationeventstream-object"></a>包裝 OrchestrationEventStream 物件  
 如同服務導向解決方案，商務程序管理解決方案會包裝**OrchestrationEventStream**物件。 而且和服務導向解決方案一樣，所有方法均為靜態，如此協調流程不需要建立物件的執行個體便能使用方法。 這也代表若引擎凍結協調流程，並不需要序列化用於追蹤的物件，也不需要儲存物件 (不需要為可序列化)。 商務程序管理解決方案，不過，包裝**OrchestrationEventStream**全都衍生自單一的數個物件，與抽象物件。  
  
 抽象類別是**BasicActivity**。 雖然為抽象類別，但此類別實際上並未當作衍生類別的範本使用。 而是透過它的靜態方法提供一組可用的方法，不以衍生類別為限。 實際上，這可讓您實作四種預設方法。 四個靜態方法是： **CreateActivityId**， **BeginActivity**， **UpdateActivity**，和**EndActivity**。  
  
 類別可多載**BeginActivity**方法。 其中一個版本可將活動名稱做為單一引數，建立 GUID 以做為活動識別碼使用，然後呼叫採用活動名稱和活動識別碼的版本，再傳回活動識別碼。 當訂單沒有唯一的識別碼時，此單一引數版本就非常有用。  
  
 **CreateActivityId**方法採用字串和唯一的識別項，例如要求識別項，並傳回它們以底線串連的字串。 這可以提供唯一的活動識別碼，而且可在衍生類別中廣泛的使用。 **BeginActivity**， **UpdateActivity**，和**EndActivity**方法呼叫**Orchestrationeventstream**， **UpdateActivity**，和**EndActivity**方法**OrchestrationEventStream**。  
  
 方案衍生的類別**BasicActivity**訂單仲介 (**Ordermanager**)，訂單管理員 (**OrderManager**)，和處理階段 (**Basicactivity**)。 每個類別均對應至一個活動。 每個類別會提供要用於活動名稱的字串**CreateActivityId**建立活動識別碼，以及方法專門供活動里程碑。  
  
 因為訂單仲介可傳遞訂單並於之後接收回應，所以它包含一種方法，可復原指定給訂單之要求識別碼的活動識別碼。 這可讓商務程序持續追蹤處理訂單的最終項目。  
  
> [!NOTE]
>  若透過檔案功能提交訂單而非透過客戶服務 Web 應用程式，便必須對各要求新增其特有的識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [開發商務程序管理解決方案](../core/developing-a-business-process-management-solution.md)