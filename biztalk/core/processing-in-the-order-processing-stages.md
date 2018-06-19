---
title: 訂單處理階段中的處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 698005da-1ba8-4972-83db-f5ae45fd6a83
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a8eae6b814af36d0ea07065726ca66518984703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265094"
---
# <a name="processing-in-the-order-processing-stages"></a>訂單處理階段中的處理
商務程序管理解決方案包含兩個階段， **CableOrder1**和**CableOrder2**協調流程會執行訂單處理動作。 如需如何訂單程序分成兩階段的詳細資訊，請參閱[的處理階段的數目](../core/number-of-processing-stages.md)。  
  
 兩個處理階段開始時收到訂單訊息，並同時回覆狀態訊息，以**OrderManager**在開始之後的協調流程。 同樣地，這兩個將訊息傳回**OrderManager**指出階段是否已完成或終止並產生錯誤。 如需詳細資訊之間的連線**OrderManager**協調流程和處理階段，請參閱[反向直接夥伴繫結](../core/inverse-direct-partner-binding.md)。  
  
 這兩種處理階段使用自我相互關聯，動態連接埠，以將資訊傳送回**OrderManger**。 配合動態連接埠時，協調流程會將連接埠位址從訊息複製到傳送埠。  
  
 所有的處理階段所接收的訂單訊息都是正規化及標準訂單訊息中建立**OrderBroker**。  
  
> [!NOTE]
>  因為**CableOrder1**和**CableOrder2**協調流程，您可以閱讀此節與 Microsoft Visual Studio 中開啟協調流程。  
  
## <a name="the-cableorder1-orchestration"></a>CableOrder1 協調流程  
 **CableOrder1**收到訂單訊息時，會啟動協調流程。 接著，它會將回覆位址從訊息複製到階段完成通訊埠。 接下來，以建構應答訊息，然後將它做為回應傳送**BeginStagePort**連接埠，，然後將路由資訊儲存在區域變數中。  
  
 這樣，此協調流程就會自 SSO 取得組態資訊。 如需解決方案如何使用 SSO 的詳細資訊，請參閱[使用 SSO 有效率地在商務程序管理解決方案中](../core/using-sso-efficiently-in-the-business-process-management-solution.md)。  
  
 協調流程接著會建立執行個體**OrderHandler**物件來與後端處理序通訊，會檢查訊息的有效性，分析訊息，判斷服務類型，並採取的動作。 根據要採取的動作，它會呼叫其中一個訂單動作協調流程**Activate**，**變更**，或**取消**並傳遞**OrderHandler**協調流程的物件。  
  
 **CableOrder1**協調流程會接著檢查中斷，訊息聆聽設備群組並等待傳送回。 如果協調流程收到來自設備群組的回應訊息，它就會繼續處理。 否則，若有發生中斷，協調流程就會擲出中斷例外錯誤。  
  
 透過建構完成訊息，並將它透過傳送完成的協調流程**StageCompletion**連接埠。  
  
## <a name="the-cableorder2-orchestration"></a>CableOrder2 協調流程  
 CableOrder2 協調流程會執行相同步驟開始與 CableOrder1 協調流程來路由資訊 SSO 組態資訊，以及建立的執行個體**OrderHandler**物件。  
  
 協調流程會接著檢查中斷，並傳遞**OrderHandler**物件的呼叫中**完成**協調流程。 協調流程接下來，建立訂單狀態訊息、 更新訂單歷程記錄，以及傳送完成訊息透過**StageCompletion**連接埠。  
  
## <a name="see-also"></a>另請參閱  
 [版本控制商務程序管理解決方案](../core/versioning-the-business-process-management-solution.md)   
 [商務程序管理解決方案中的處理](../core/processing-in-the-business-process-management-solution.md)