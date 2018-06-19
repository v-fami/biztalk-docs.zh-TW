---
title: 訊息類型和事件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, message events
- HL7, message types
- message types
- messages, message types
ms.assetid: d53d51d0-216d-472b-97b7-8a96b8013510
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9880da0ca5fea84c5a2b3d6e9f3a43ace41970
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205950"
---
# <a name="message-types-and-events"></a>訊息類型和事件
HL7 標準已分組到真實世界的事件一起做為特定群組相關的訊息*訊息類型*ADT。 這些訊息包含觸發程序事件，例如病患的管理。 2.4 版 HL7 標準定義 100 個以上的訊息類型，其中每個 HL7 組織已指派唯一三個字元的訊息型別程式碼。 HL7 標準版本進化，HL7 組織已加入新的訊息類型來提供新功能。  
  
 所有的訊息類型包含訊息的事件，也稱為*事件*。 您可以將做為訊息群組內的特定訊息類型的唯一類型事件。 比方說，瀏覽系統管理員/通知 （訊息事件 A01） 和放電/結束，請瀏覽 （訊息事件 A03） 是唯一病患管理訊息類型 (ADT) 所包含的訊息。 HL7 組織已指派唯一的三個字元事件程式碼的每個訊息的事件。  
  
 只有一個訊息類型可以包含特定的訊息事件。 訊息類型可以包含多個訊息的事件。 不過，特定的訊息事件的結構有所不同 HL7 標準版本。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [觸發程序事件和訊息](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md)   
 [HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)