---
title: "商務規則引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Engine
- Business Rules Engine
- Business Rules Engine, rules
- Business Rules Engine, about Business Rules Engine
ms.assetid: 87b38507-9f6d-4863-88a6-9c20f15a4e55
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d99cff10324f1cf1ba97d99431524474ed5f039b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-engine"></a>商務規則引擎
「商務規則架構」是一個 Microsoft .NET 相容的類別庫。 它提供一個有效的推斷引擎，可將易讀、宣告式且語意豐富的規則連結到任何商務物件 (.NET 元件)、XML文件或資料庫資料表。 應用程式開發人員可從小型的商務邏輯建置區塊 (小型的規則集) 開始建構規則，以執行 .NET 物件、資料庫資料表和 XML 文件中包含的資訊 (事實)，以建立商務規則。 此設計模式可提升程式碼重複使用率、簡化設計和商務邏輯的模組化程序。 此外，規則引擎並非利用商務應用程式的架構或設計。 事實上，您可以直接叫用規則引擎將規則技術加入商務應用程式，或是取得叫用您的商務物件的外部邏輯，無需修改。 總之，開發人員若採用該技術，只需耗費最少的精力便能建立和維護應用程式。  
  
 在規劃開發規則應用程式方面，首先必須決定規則與商務程序要如何配合。 應用程式將會建立原則的執行個體，並提供所要執行的資料或事實。 原則物件可封裝規則引擎，並提供透過其執行的單一進入點。  
  
 您也必須規劃開發工作和測試所設計的規則。 還必須考慮如何部署和更新您的原則。 您很可能想要追蹤規則引擎的執行進度和監控目前的狀態。  
  
 規劃您的規則開發工作時，請說明下列步驟：  
  
1.  規劃如何將規則併入應用程式。  
  
2.  識別想要在應用程式中以規則表示的商務邏輯。 「商務邏輯」一詞可指許多事情；「超過五百美元的訂單均必須由經理核准」即為商務邏輯的一個範例。  
  
3.  識別規則項目的資料來源。 您可以選擇性地定義和發佈詞彙 (表示基礎繫結的網域特有術語表)。  
  
4.  從詞彙定義或直接從資料繫結來定義規則，然後再由規則來編輯代表商務邏輯的原則。  
  
    > [!NOTE]
    >  必須先發佈詞彙，才能在規則中套用詞彙。  
  
5.  以事實範例測試原則並進行偵錯。 您可以使用 「 商務規則編輯器 」 測試原則功能，或使用**原則**或**PolicyTester**從應用程式、 命令列程式或協調流程執行的類別。  
  
6.  將原則版本發佈至規則存放區。  
  
7.  部署原則版本。  
  
8.  在裝載的應用程式中產生和建置短期事實清單。 使用**呼叫規則**執行商務原則，或以程式設計方式產生原則版本裝載的應用程式中使用協調流程。  
  
9. 視需要監控和追蹤規則執行。  
  
    > [!NOTE]
    >  預設的追蹤攔截器可搭配協調流程使用。 若您裝載的應用程式並非協調流程，則必須撰寫自訂的追蹤攔截器來執行此項工作。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [規則](../core/rules.md)  
  
-   [原則](../core/policies.md)  
  
-   [詞彙](../core/vocabularies.md)  
  
-   [商務規則架構的架構](../core/business-rules-framework-architecture.md)  
  
-   [事實](../core/facts.md)  
  
-   [規則引擎](../core/rule-engine.md)