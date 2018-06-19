---
title: 錯誤處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Messaging Engine, errors
- errors, Messaging Engine
- errors, messages
- messages, errors
ms.assetid: ebc889cc-eeac-483c-baf3-407a218f6d14
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cbf0d898f7af193220cf8f1c24e809aefa1b782
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242614"
---
# <a name="error-handling"></a>錯誤處理
訊息通過 BizTalk Server 傳訊子系統的路徑中包含數個處理和傳輸點。 沿著此路徑上的每個點，失敗有可能發生在 BizTalk Server 基礎結構與應用程式提供的項目中，例如自訂管線元與協調流程。  
  
 本節以及本節中所包含的主題討論眾所皆知的處理階段之一般失敗模式，以及如何透過 BizTalk Server 組態與應用程式提供的項目 (例如協調流程) 來處理失敗模式。 失敗影響包含訊息配置、擷取和記錄診斷以及作業考量。  
  
 訊息失敗時產生的事件依存於失敗的位置以及失敗訊息路由和可復原交換處理的狀態。 下表摘要出管線和訂閱失敗的失敗行為和繼續位置。  
  
|失敗類型|失敗訊息路由|可復原交換處理|失敗行為|繼續位置|  
|------------------|----------------------------|----------------------------------------|----------------------|---------------------|  
|管線|已停用|已停用|訊息會在管線處理前被擱置|在管線處理之前。|  
|管線|已停用|已啟用|訊息會在管線處理後被擱置|在管線處理之前。 如需有關可復原交換處理的詳細資訊，請參閱[可復原交換處理](../core/recoverable-interchange-processing.md)。|  
|管線|已啟用|已停用|訊息是藉由升級錯誤報告相關的訊息內容屬性所發佈|訊息未被擱置。 如需有關路由失敗訊息的詳細資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。|  
|管線|已啟用|已啟用|訊息是藉由升級錯誤報告相關的訊息內容屬性所發佈。|訊息未被擱置。|  
|訂閱|已停用|已停用|訊息會在管線處理前被擱置。 已建立路由失敗報告。|訊息將會在管線處理前繼續。 路由失敗報告是不可繼續的。|  
|訂閱|已停用|已啟用|訊息會在管線處理後被擱置。 已建立路由失敗報告。|訊息將會在管線處理前繼續。 路由失敗報告是不可繼續的。 如需有關可復原交換處理的詳細資訊，請參閱[可復原交換處理](../core/recoverable-interchange-processing.md)。|  
|訂閱|已啟用|已停用|訊息是藉由升級錯誤報告相關的訊息內容屬性所發佈。 已建立路由失敗報告。|訊息未被擱置。 路由失敗報告是不可繼續的。 如需有關路由失敗訊息的詳細資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。|  
|訂閱|已啟用|已啟用|訊息是藉由升級錯誤報告相關的訊息內容屬性所發佈。 已建立路由失敗報告。|訊息未被擱置。 路由失敗報告是不可繼續的。|  
  
 這些列舉的失敗模式有許多都可對應到 BizTalk Server 中，為處理失敗模式所設計的特定功能，例如可復原的交換處理與錯誤報告。 其他的失敗模式則與 BizTalk Server 如何傳遞失敗資訊給應用程式項目，以及應用程式項目 (例如，自訂管線元件、配接器以及協調流程) 如何傳遞失敗資訊給 BizTalk Server 有關。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用失敗的訊息路由](../core/using-failed-message-routing.md)  
  
-   [如何啟用失敗訊息的路由](../core/how-to-enable-routing-for-failed-messages.md)  
  
-   [使用通知](../core/using-acknowledgments.md)  
  
## <a name="see-also"></a>另請參閱  
 [可復原交換處理](../core/recoverable-interchange-processing.md)   
 [訊息失敗的類型](../core/types-of-message-failures.md)