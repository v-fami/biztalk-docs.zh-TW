---
title: 互動的介面卡狀態監視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bbc6a45-8d3a-444e-b760-aef0dfa7218a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32cf2f197508c0cd703a05780804c6bc880b5f32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224294"
---
# <a name="interact-adapter-status-monitoring"></a>互動的介面卡狀態監視
SWIFTNet 連結 (SNL C) 保留 SWIFTNet 存放區和該 SNL 上取得的正向 (SnF) 工作階段相關的本機狀態。 若要取得工作階段的相關資訊，請使用 SwCall() 與下列基本項目：  
  
 ![取得工作階段資訊](../../adapters-and-accelerators/fileact-interact/media/b7feb4b4-de92-4bb9-bcfe-363a127d0ed2.gif "b7feb4b4-de92-4bb9-bcfe-363a127d0ed2")  
  
 請注意您不需要提供 AuthorizationContext。 傳回本機 SNL 所看到的資訊，如下圖所示。  
  
 ![工作階段狀態資訊](../../adapters-and-accelerators/fileact-interact/media/afd46393-a11d-4b4a-a66b-eba5f049f306.gif "afd46393-a11d-4b4a-a66b-eba5f049f306")  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)