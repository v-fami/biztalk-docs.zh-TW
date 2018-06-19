---
title: 協調流程中使用的相互關聯 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, orchestrations
- messages, correlation sets
- correlation sets
- orchestrations, messages
- messages, validating
ms.assetid: d919afa9-bada-406a-bf4b-7b46c831c6d5
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3be56c2171205bb49d2ff1f589c77ac309ea188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287366"
---
# <a name="using-correlations-in-orchestrations"></a>使用協調流程中的相互關聯
相互關聯是將內送訊息與適當協調流程執行個體相比對的程序。 例如，協調流程會傳送訊息，並將回應接收到相同的協調流程中。 相互關聯的訊息交換模式共有三種：  
  
-   傳統交握  
  
-   循序群組  
  
-   平行群組  
  
 在傳統交握模式中，交握存在協調流程或商務程序間的訊息交換之間，而您可以透過在協調流程中定義相互關聯集合來完成交握程序；協調流程中的相互關聯集合是一份具有特定值的升級屬性清單，您可以使用這些特定的值，將訊息路由到特定的協調流程執行個體。  
  
 例如，如果您的協調流程是設計用來發出訂單、接收發票及送出付款，您必須確定接收發票訊息的協調流程執行個體與傳送對應訂單的執行個體相同，因為當時可能已處理許多筆訂單。 在這個範例中，訂單識別碼可以當做相互關聯集合中的參數，以便使訂單訊息和發票訊息產生相互關聯。 此範例的實例流程如下：  
  
1.  範例流程 A 將訂單訊息傳送至協調流程 B。相互關聯集合會在傳送訂單訊息之前初始化。  
  
2.  協調流程 B 會處理訂單、產生並傳回發票；在這個協調流程中，第一個「接收」圖形會遵照同一個相互關聯集合來接收訂單訊息。  
  
3.  在處理訂單訊息之後，將發票傳回協調流程 A 時，也會遵照相同的相互關聯流程。  
  
4.  在協調流程 A 中，從協調流程 B 接收發票訊息的「接收」圖形，也會遵照同一個相互關聯集合，以確實依據預先定義的相互關聯集合來接收相互關聯發票訊息。  
  
 每當多個單一項目必須相互關聯，以達到個別項目無法單獨完成的工作時，都可以使用循序群組和平行群組模式。 如需詳細資訊，請參閱[使用群組實例](../core/working-with-convoy-scenarios.md)。  
  
 除了相互關聯訊息交換模式之外，協調流程中還有兩種相互關聯類型：  
  
-   手動相互關聯  
  
-   自動相互關聯  
  
 在手動相互關聯實例中，您可手動設定協調流程，以初始化並遵照相互關聯集合，使訊息與適當的執行個體產生關聯。 在自動相互關聯實例中，傳訊引擎會代替您建立訊息與執行個體的相互關聯，例如，當您在自己的協調流程中設定要求-回應連接埠或自我相互關聯連接埠時。  
  
 只要您的協調流程沒有可以讓訊息與執行個體產生關聯的明確途徑，例如啟動接收、要求-回應或自我相互關聯連接埠，您就必須使用相互關聯。  
  
## <a name="examples-of-using-correlations"></a>相互關聯的使用範例  
  
-   [PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)  
  
-   從下載 SDK 範例 < 相互關聯訊息與協調流程執行個體 > [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
-   從下載 SDK 範例 「 平行群組 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [相互關聯集](../core/correlation-sets.md) 
  
-   [相互關聯類型](../core/correlation-types.md) 
  
-   [如何新增及移除相互關聯集](../core/how-to-add-and-remove-correlation-sets.md) 
  
-   [如何設定相互關聯集](../core/how-to-configure-correlation-sets.md)  
  
-   [如何設定相互關聯類型](../core/how-to-configure-correlation-types.md)  
  
-   [使用群組實例](../core/working-with-convoy-scenarios.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何使用自我相互關聯直接繫結連接埠](../core/how-to-use-self-correlating-direct-bound-ports.md)