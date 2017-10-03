---
title: "InterAct 配接器元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aad60b57-4cc8-44b9-98f5-e5a2ba3a41e2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e909e49713377172d01540f4c8e660756d68ed72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-components"></a>InterAct 配接器元件
InterAct 配接器具有用戶端和伺服器元件。 請注意，有可能 A4SWIFT 安裝 （最小） SWIFT 聯盟閘道 (SAG) 在相同電腦上的執行 Windows Server。 也請注意，SWIFTNet 連結 (SNL) 可能 SAG 從一部電腦上。 遠端應用程式發展介面 (API) SWIFT 所提供的主機介面卡用來從 A4SWIFT SAG，不論元件的位置與通訊。  
  
 下圖顯示組成互動的介面卡相關的整個介面卡與通訊鏈結的元件所在的位置。  
  
 ![InterAct 元件](../../adapters-and-accelerators/fileact-interact/media/cf257c5a-3668-4aff-bce9-7acc6eb672bd.gif "cf257c5a-3668-4aff-bce9-7acc6eb672bd")  
  
 在下圖中，用戶端應用程式會使用 A4SWIFT 和 InterAct 配接器。 BizTalk Server 是中介軟體，透過 TCPIP 通訊到遠端應用程式開發介面主機介面卡。  
  
 ![InterAct 用戶端應用程式](../../adapters-and-accelerators/fileact-interact/media/7aeada39-6264-498b-92e8-303eb0cf369b.gif "7aeada39-6264-498b-92e8-303eb0cf369b")  
  
 在下圖中，伺服器應用程式會使用 A4SWIFT 和 InterAct 配接器。 BizTalk Server 是中介軟體，透過 TCPIP 通訊到遠端應用程式開發介面主機介面卡。  
  
 ![InterAct 伺服器應用程式](../../adapters-and-accelerators/fileact-interact/media/51cbae6a-41e9-4a50-9574-5e86bc04ddba.gif "51cbae6a-41e9-4a50-9574-5e86bc04ddba")  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [互動配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)