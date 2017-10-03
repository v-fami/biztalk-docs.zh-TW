---
title: "執行 Orchestrations3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, running
- Receive shape [Orchestration Designer], starting orchestrations
- Start Orchestration shape [Orchestration Designer], starting orchestrations
- Call Orchestration shape [Orchestration Designer], starting orchestrations
- Receive shape [Orchestration Designer], activating orchestrations
ms.assetid: 5bfe61c9-80e0-4a0a-b6b1-ab48037e665e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 550fc1e03f3583215a817028917000c9a9c3074a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-orchestrations"></a>執行協調流程
協調流程執行個體都是設計成觸發藉由從另一個協調流程的明確呼叫 — 使用**呼叫協調流程**圖形或**啟動協調流程**圖形 — 或透過接收啟動訊息。 啟動訊息結構描述中指定**訊息**屬性。 您應該同理，設計您的協調流程，而且其中一個設定**Activate**屬性**接收**true，或請確定呼叫的協調流程存在且已正確設定成執行圖形新的協調流程。  
  
 執行任何執行個體之前，您必須先繫結和部署 BizTalk 組件，然後登錄和啟動協調流程引擎以開始處理。 如需詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)和[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。 當協調流程由另一個協調流程叫用，或訊息呈現給符合啟動接收中準則的引擎時，引擎會建立新的協調流程執行個體並執行該執行個體。 可以同時執行許多不同的執行個體。  
  
## <a name="calling-and-starting-orchestrations"></a>呼叫和啟動協調流程  
 **呼叫協調流程**圖形和**啟動協調流程**圖形可以用來啟動另一個協調流程。 在這兩種情況下，呼叫者可傳送參數與其他協調流程交換資訊。 如需詳細資訊，請參閱[如何將參數加入至協調流程](../core/how-to-add-parameters-to-orchestrations.md)。  
  
## <a name="using-activation-receives-with-filter-expression"></a>搭配篩選條件運算式使用啟動接收  
 **接收**圖形也可以使用以要求啟用的其他條件的篩選條件運算式。 如果訊息是正確的型別，而且某些屬性或訊息屬性符合所有條件的篩選運算式，**接收**圖形會接受訊息，且協調流程會啟動。 這類 「 接收 」 圖形指*啟動接收*。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定呼叫協調流程圖形](../core/how-to-configure-the-call-orchestration-shape.md)   
 [如何設定啟動協調流程圖形](../core/how-to-configure-the-start-orchestration-shape.md)   
 [如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md)   
 [建置和執行協調流程](../core/building-and-running-orchestrations.md)