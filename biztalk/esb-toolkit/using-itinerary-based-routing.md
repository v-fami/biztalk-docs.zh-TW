---
title: 使用以路線為基礎的路由 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d5b5d13-cbf2-4f3c-8a1a-3bb852f048a0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adcb32367a42403e769111f7b3d3d343c604671
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978687"
---
# <a name="using-itinerary-based-routing"></a>使用以路線為基礎的路由
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供以路線為基礎的訊息路由所實作的傳閱名單模式，以啟用案例時的處理順序逐步執行特定的訊息不知道在設計階段，且每個訊息可能會有所不同。 實作此模式代表集合，這些步驟，以 XML 格式時，用以傳閱名單，並判斷哪些步驟要在執行階段期間發生。 狀態的傳閱名單，通常稱為 「 ESB 路線 」，是必須針對訊息執行，因為它正在處理的步驟定義的宣告式指示的已排序的集合[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件和 BizTalk Server 執行階段。 ESB 路線中指定特定的處理指示相關聯[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件，也稱為 「 ESB 路線服務 」。 ESB 路線服務的目的是要執行的處理指示，並更新狀態的傳閱名單，來指示暫止的指示下一步。  

 本節說明以路線為基礎的處理功能[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 它包含下列主題：  

- [ESB 路線管理](../esb-toolkit/esb-itinerary-management.md)  

- [入口和出口](../esb-toolkit/on-ramps-and-off-ramps.md)  

- [選擇傳訊與協調流程路線服務](../esb-toolkit/choosing-between-messaging-and-orchestration-itinerary-services.md)  

- [使用管線元件選取現有路線](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)  

- [使用管線元件讀取路線](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)  

- [使用管線元件快取請求-回應的路線](../esb-toolkit/using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response.md)  

- [建立路線訂閱者](../esb-toolkit/creating-itinerary-subscribers.md)  

- [執行路線服務](../esb-toolkit/executing-an-itinerary-service.md)  

- 超連結"<http://msdn.microsoft.com/library/ee236752(BTS.10).aspx>"[以路線為基礎的路由成品](../esb-toolkit/itinerary-based-routing-artifacts.md)
