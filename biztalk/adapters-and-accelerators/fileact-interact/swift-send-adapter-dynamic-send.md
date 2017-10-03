---
title: "SWIFT 傳送配接器的動態傳送 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 105972fe-9dc0-480a-a4d1-2ec682fa7ad9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75d63df8f38346e4f77e2b7bfa8e3effc93f2fce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-send-adapter-dynamic-send"></a>SWIFT 傳送配接器的動態傳送
傳送配接器的動態傳送模式會將訊息從佇列提取。 動態傳送的 URI 是：  
  
```  
SWIFT://<queue name>/<Force Acquire>/<Session Mode>/<Order By>/<Recovery mode>  
```  
  
 您可以使用協調流程或管線來建構 URI。  
  
## <a name="see-also"></a>另請參閱  
 [SWIFT 傳送配接器架構](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)   
 [SWIFT 傳送配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)   
 [SWIFT 傳送配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)   
 [SWIFT 傳送配接器同步模式](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)   
 [SWIFT 傳送配接器的終止](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)