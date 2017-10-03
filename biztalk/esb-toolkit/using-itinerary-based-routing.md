---
title: "使用行程為基礎的路由 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d5b5d13-cbf2-4f3c-8a1a-3bb852f048a0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc0a0eb3a212efccd4ddbe4e275042ecb850095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-itinerary-based-routing"></a>使用行程為基礎的路由
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供行程為基礎之訊息路由，方法是實作傳閱名單模式，以啟用案例時的處理順序的特定訊息的步驟不知道在設計階段，且每個訊息會有所不同。 此模式的實作用於路由 slip 代表集合，這些步驟，以 XML 格式，並判斷必須在執行階段期間發生的步驟。 路由名單，通常稱為 「 ESB 行程 」，狀態為已排序的集合的宣告式定義必須在處理的訊息執行的步驟的指示[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件和 BizTalk Server 執行階段。 ESB 行程中指定特定的處理指示聯[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件，也稱為 「 ESB 路線服務 」。 ESB 路線服務的目的是要執行的處理指示，並更新路由 slip 表示暫止的指示下一個狀態。  
  
 本章節描述的行程為基礎的處理功能[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 它包含下列主題：  
  
-   [ESB 路線管理](../esb-toolkit/esb-itinerary-management.md)  
  
-   [在坡道提升和關閉坡道提升](../esb-toolkit/on-ramps-and-off-ramps.md)  
  
-   [選擇傳訊和協調流程路線服務](../esb-toolkit/choosing-between-messaging-and-orchestration-itinerary-services.md)  
  
-   [選取現有的行程中使用的管線元件](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)  
  
-   [使用管線元件讀取行程](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)  
  
-   [使用快取路線請求-回應管線元件](../esb-toolkit/using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response.md)  
  
-   [建立計劃的訂閱者](../esb-toolkit/creating-itinerary-subscribers.md)  
  
-   [執行路線的服務](../esb-toolkit/executing-an-itinerary-service.md)  
  
-   超連結"http://msdn.microsoft.com/en-us/library/ee236752 (BTS.10).aspx"[行程為基礎的路由成品](../esb-toolkit/itinerary-based-routing-artifacts.md)