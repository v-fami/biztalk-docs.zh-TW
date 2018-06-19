---
title: 減少傳輸類型與處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transport types, decoupling processing
- processing, decoupling transport types
- transport types
- transport types, service solutions
- service solution tutorial, MQSeries adapters
- processing, service solutions
- service solution tutorial, decoupling transport type and processing
- correlations, MQSeries adapters
- MQSeries adapters, correlations
- MQSeries adapters, service solutions
ms.assetid: 0b2c733a-e2c7-42ff-a733-f712fde38f7e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b14522c6bbf9393bc22f632c4db5eeb5e4a22a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238598"
---
# <a name="decoupling-transport-type-and-processing"></a>減少傳輸類型與處理
在服務導向解決方案中，清除線段經常存在於商務程序與特定的傳輸及接收訊息之間。 這讓您能單獨變更解決方案的商務程序或訊息部分。  
  
 服務導向解決方案會在某個地方違反此設計原則。 本節將描述此情況、可能的替代方案以及選取的結構。  
  
## <a name="correlation-and-the-mqseries-adapter"></a>相互關聯與 MQSeries 配接器  
 為了使用 MQSeries 配接器，您無法使用標準的 BizTalk Server 相互關聯識別碼。 這是因為相互關聯識別碼會進入 IBM 後端系統，而該系統會有自己的相互關聯識別碼系統。 相反地，您必須使用**MQSeries.MQMD_CorrelId**和**MQSeries.MQMD_MsgID**屬性。 使用這些屬性會潛在地將傳輸專用的資訊置於協調流程與商務程序中。  
  
 處理此相依性的一種方法便是使用 BizTalk Server 相互關聯識別碼，並使用自訂管線元件來轉譯 MQSeries 的相互關聯識別碼。 這會增加實例的複雜度。 此外，若傳輸變更時，必須變更兩個管線元件。 而且，最後它會重新定位相依性 (位於管線元件中)，而不是解析它。  
  
 另一個選項便是隔離 MQSeries 專用的相互關聯處理，以隔離協調流程及呼叫該協調流程。 這會保留商務程序的獨立性。 不過，這會在協調流程之間引入編譯階段相依性。 修改傳輸需要重新編譯兩個協調流程 (例如，從虛設常式到解決方案的配接器版本)。 該呼叫也會增加解決方案的回應時間。  
  
 為了避免增加額外的複雜度和可能降低效能，直接在協調流程中使用 MQSeries 相互關聯似乎是最簡易的。  
  
 如需配接器和協調流程中的相互關聯的詳細資訊，請參閱[MQSCorrelationSetOrchestration （BizTalk Server 範例）](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)。  
  
## <a name="see-also"></a>另請參閱  
 [實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md)   
 [MQSCorrelationSetOrchestration （BizTalk Server 範例）](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)