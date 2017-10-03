---
title: "執行階段架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- architecture, runtime
- runtime
ms.assetid: feff9a84-f19b-44c9-8d05-8e6015bb1ef9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e45ac745dbf6704f06f61155b3f57edfdec9e09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-architecture"></a>執行階段架構
檢視有關在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中各種元件的更多詳細資訊之前，您必須先瞭解元件如何適用於產品的整體架構。 BizTalk Server 執行階段是在發佈/訂閱架構中建置的，在其中訊息會發佈到系統，然後由一或多個作用中訂閱者所接收。 這個架構的不同類別存在，但在 BizTalk Server 中實作模型通常稱為*以內容為基礎的發佈/訂閱*。  
  
 在以內容為基礎的發佈/訂閱模型中，訂閱者會使用有關訊息的準則集，來指定他們想接收的訊息。 訊息會在發佈時進行評估，而所有具有相符訂閱 (由篩選條件運算式所指定) 的作用中訂閱者，將會接收訊息。 不過在套用到 BizTalk Server 時，以內文為基礎會有一點點的誤稱，因為用來建置訂閱的準則不一定是來自訊息內文，也可能包含與訊息有關的內容資訊。 如需訂閱機制的詳細資訊，請參閱[發行和訂閱架構](../core/publish-and-subscribe-architecture.md)。  
  
 下列各節描述 BizTalk Server 執行階段架構的各種元件。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Server 訊息](../core/the-biztalk-server-message.md)  
  
-   [訊息的生命週期](../core/lifecycle-of-a-message.md)  
  
-   [處理訊息](../core/processing-the-message.md)  
  
-   [要求-回應傳訊](../core/request-response-messaging.md)  
  
-   [傳訊引擎](../core/the-messaging-engine.md)  
  
-   [實體](../core/entities.md)  
  
-   [成品](../core/artifacts.md)  
  
-   [企業單一登入 (SSO)](../core/enterprise-single-sign-on-sso.md)  
  
-   [商務規則引擎](../core/business-rules-engine.md)  
  
-   [BizTalk 組件](../core/biztalk-assemblies.md)