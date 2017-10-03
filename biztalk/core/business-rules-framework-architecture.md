---
title: "商務規則架構的架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, caching
- Business Rules Framework, Rule Engine Update service
- rule store [Business Rules Framework]
- Policy class [Business Rules Engine]
- Business Rules Framework, architecture
- Business Rules Framework, RuleEngine class
- Business Rules Framework, Policy class
- Business Rules Framework, authoring tools
- RuleEngine class [Business Rules Engine]
- caching, Business Rules Framework
- Business Rules Framework, fact retrievers
- architecture, Business Rules Framework
- Business Rules Framework, rule store
ms.assetid: f5570cca-7664-4180-af9c-64ef90a0022b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4b23723d01a29606637689966cc07246cdfbc1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-framework-architecture"></a>商務規則架構的架構
下圖顯示「商務規則架構」的元件架構。  
  
 ![商務規則架構的元件架構](../core/media/ebiz-rulesarch-new.gif "ebiz_rulesarch_new")  
「Microsoft 商務規則架構」的架構  
  
 架構的部分元件會在下列段落中描述。  
  
## <a name="policy-class"></a>原則類別  
 A**原則**物件是為商務原則的單一執行個體，並提供以規則為基礎的應用程式所使用的介面。 它提供的抽象概念可以讓應用程式開發人員無需顧慮以下事項：規則存放區位置、從規則存放區擷取規則集、產生基礎規則引擎的執行個體，並確保長期事實會判斷提示至引擎。 在許多案例中，以規則為基礎的應用程式會使用並行的執行個體的**原則**物件。 這些並行執行個體可以代表相同原則、不同版本的相同原則，或是不同版本的不同原則。  
  
## <a name="ruleengine-class"></a>RuleEngine 類別  
 **RuleEngine**物件做為商務原則的執行引擎。 它會使用三個外掛程式元件 (轉譯程式、介面引擎和追蹤攔截器) 以進行實作。 A **RuleEngine**物件會使用**RuleSet**物件代表商務原則做為輸入，並使用轉譯程式、 介面引擎和設定規則集來實作的追蹤攔截器規則集所定義的商務原則。  
  
## <a name="fact-retriever"></a>事實擷取器  
 事實擷取器是一個選擇性、使用者定義的外掛程式元件，負責收集長期事實以供商務原則使用。 如需詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。  
  
 在執行之前，**原則**物件執行個體會提供其**RuleEngine**事實擷取器，並賦予它機會來更新的規則引擎中的事實集的執行個體的工作記憶體。 如需詳細資訊，請參閱[短期事實與。長期事實](../core/short-term-facts-vs-long-term-facts.md)。  
  
## <a name="rule-engine-update-service"></a>規則引擎更新服務  
 「規則引擎更新」服務會在分散式環境中提供動態商務原則更新。 自動啟動的 Microsoft Windows NT 服務應用程式會負責訂閱原則部署和解除部署變更商務原則時，會發生的事件。  
  
 在一般的企業實例中，商務原則會在更新、測試和版本建立之後，進行部署。 部署包含將已更新的原則新增到安全且持續性的規則存放區，以及選擇性地在存放區上執行邏輯，以便將已更新原則的相關資訊發佈給所有感興趣的合作對象 (請注意，是發佈原則的相關資訊而非原則本身)。  
  
 在裝載以規則為基礎之應用程式的伺服器上執行的「規則引擎更新」服務，會接收原則更新通知，並快取資訊以供後續使用。 使用 pub/sub 模型以進行原則更新，可以讓您以近乎即時的方式變更商務原則，而不需將服務停機或中斷。  
  
## <a name="policyvocabulary-authoring-tools"></a>原則/詞彙撰寫工具  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的「商務規則編輯器」，會提供原則與詞彙撰寫功能給一般使用者與開發人員。  
  
## <a name="rule-store"></a>規則存放區  
 A*規則存放區*是商務原則與詞彙的儲存機制。 儲存機制可以是簡單的檔案或安全、 可擴充、 持續性，且可靠的資料庫，例如 Microsoft SQL Server。 (SQL Server 可做為架構的預設規則存放區)。  
  
## <a name="caching"></a>快取  
 商務規則引擎架構提供的快取機制**RuleEngine**執行個體。 每個**RuleEngine**執行個體包含特定的原則版本的記憶體中表示。  
  
 下列步驟說明在新的程序**原則**具現化執行個體 (不是執行的應用程式開發介面上呼叫**呼叫規則**圖形):  
  
1.  **原則**物件要求**RuleEngine**從規則引擎快取的執行個體。  
  
2.  如果**RuleEngine**原則版本存在於快取中，執行個體**RuleEngine**來傳回執行個體**原則**物件。 如果**RuleEngine**執行個體無法使用，快取建立的新執行個體。 當**RuleEngine**具現化執行個體，並不會接著，建立新的事實擷取器執行個體，如果已設定的原則版本。  
  
 當**Execute**上呼叫方法**原則**物件時，會發生下列步驟：  
  
1.  原則物件呼叫**UpdateFacts**事實擷取器是否有事實擷取器執行個體上的方法。 事實擷取器實作的方法可能會長期事實判斷提示至工作記憶體**RuleEngine**。  
  
2.  **原則**物件會判斷提示中所包含的短期事實**陣列**傳入**Execute**呼叫。  
  
3.  **原則**物件會呼叫**Execute**上**RuleEngine**。  
  
4.  **RuleEngine**完成執行，並會將控制傳回**原則**物件。  
  
5.  **原則**物件會撤回短期事實從**RuleEngine**。 由事實擷取器所判斷提示的長期事實將保留於規則引擎的工作記憶體中。  
  
 之後**處置**上呼叫方法**原則**物件**RuleEngine**執行個體釋回規則引擎快取。  
  
 規則引擎快取將會有多個指定原則版本的規則引擎執行個體 (若負載需要它)，而每個規則引擎執行個體都有自己的事實擷取器執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎](../core/business-rules-engine.md)