---
title: "檢視支援的訊息交換模式中 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6662f17-b4f8-45fe-a22f-5d027dc9f2ff
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77fee95033e669bf584220461b330afbb9fd25b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="view-the-supported-message-exchange-patterns-in-the-wcf-lob-adapter-sdk"></a>檢視 WCF LOB 配接器 SDK 中的 支援的訊息交換模式
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]支援數個支援的基礎訊息模式[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]包括要求-回覆和單向通訊。 不同傳輸支援不同傳訊模式，並因此會影響它們所支援的互動類型。  
  
 下表所列的模式由處理[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
|模式|Description|  
|-------------|-----------------|  
|單向輸入|收到來自特定業務系統的輸入的訊息，但不需要回應從配接器。|  
|要求-回應輸入|從特定業務系統必須要有適當的回應從配接器接收內送的訊息。|  
|單向輸出|輸出訊息傳送至特定業務系統，但不需要回應從配接器。|  
|要求-回應輸出|輸出訊息從配接器預期的回應會傳送給特定業務系統。|  
|工作階段輸入|從特定業務系統接收輸入的訊息內的唯一工作階段。 不需要回應的特定業務系統從配接器。|  
|工作階段的輸出|輸出訊息會傳送至特定業務系統中，唯一的工作階段內。 不需要回應的特定業務系統從配接器。|  
  
 目標應用程式的功能，將會引導您選擇的訊息模式。  
  
## <a name="planning-for-sessions"></a>規劃的工作階段  
 訊息模式可能會使用工作的階段，當它想要確保所有配接器與特定業務系統之間交換的訊息必須是相同的交談的一部分。 通常需要傳遞保證，但也可以用來支援訊息交換的配接器開發人員可能會有其他需求時，會使用工作階段。  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]依賴[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]的工作階段支援。 如需工作階段的詳細資訊，請參閱[工作階段、 執行個體，以及並行](https://msdn.microsoft.com/library/ms731193.aspx)。 
  
## <a name="see-also"></a>另請參閱  
 [計劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)