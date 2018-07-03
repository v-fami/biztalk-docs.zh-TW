---
title: 具現化並初始化接收配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5cb5ba7-e2b5-49d2-adf5-a8df0bb81def
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f14a6262a8f0ed816700f3e3c34307487874d25
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983335"
---
# <a name="instantiating-and-initializing-a-receive-adapter"></a>產生並初始化接收配接器
接收配接器一旦產生，便會立即由傳訊引擎初始化，此引擎會呼叫 IBTTransportControl 的 QueryInteraface。 然後它會呼叫 IBTTransportControl<strong>。初始化</strong>傳入配接器的傳輸 proxy，它會保存在成員變數中的配接器。 接下來，引擎會呼叫**QueryInterface** for **IPersistPropertyBag**。 這是選擇性的介面;如果配接器實作它，處理常式組態會傳遞至配接器**負載**方法呼叫。 初始化接收配接器的最後階段需要將結束點組態傳遞到配接器。 在這個階段，引擎會呼叫**IBTTransportConfig.AddReceiveEndpoint**一次為每個作用中的端點，傳入的 URI 端點、 端點、 配接器特定組態和 BizTalk 組態該端點。  
  
 下圖顯示 API 呼叫的順序。 配接器會實作標示為藍色的介面。  
  
 ![](../core/media/sequence-of-init-calls.gif "Sequence_of_init_calls")  
  
 **實作秘訣：** 一般情況下，配接器應該不會封鎖呼叫中的傳訊引擎這類**IBTTransportControl.Initialize**， **IPersistPropertyBag.Load**，和**IBTTransportConfig.AddReceiveEndpoint**。 在這些呼叫中執行過多的處理，可能對服務啟動時間會有負面影響。  
  
 具有一或多個相關接收位置的所有接收配接器都是在服務啟動時建立的。 所有接收配接器都是非同步且支援批次處理的， 可能屬於內含式或外掛式。 如需有關接收配接器變數，請參閱 <<c0> [ 配接器變數](../core/adapter-variables.md)。