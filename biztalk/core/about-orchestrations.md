---
title: 關於協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations
- Orchestration Designer
- orchestrations, about orchestrations
- Orchestration Designer, about Orchestration Designer
ms.assetid: c0d9a3fb-da87-42cc-9e9e-e2c37232e606
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd3c1abeeb2c42c399a54aea4ba0128cc19bcd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225134"
---
# <a name="about-orchestrations"></a>關於協調流程
協調流程是一種靈活、功能強大的工具，用於代表以 XLANG/s 語言為基礎的可執行商務程序。 XLANG/s 可視為具有某些 C# 運算式功能的訊息語言。 您可以在直覺式的視覺繪圖中，設計流程、解譯及產生資料、呼叫自訂程式碼，以及組織完整的流程，而在執行階段中，BizTalk 協調流程引擎則會執行 XLANG/s 檔案，也就是 BizTalk 協調流程設計師所產生的可執行商務流程。  
  
 訊息、對訊息執行的傳送與接收動作、傳輸訊息時的連接埠，都是協調流程的基礎項目。 訊息是協調流程和外界通訊及進行電子商務的媒介。  
  
 **接收**和**傳送**圖形封裝您需要為您的協調流程接收訊息，並從該處傳送訊息的功能。 您應該熟悉「協調流程設計師」所提供用來代表您協調流程之邏輯流程的各種圖形。  
  
 還應該瞭解一些進階的協調流程概念，例如 Web 服務、相互關聯及長時間執行的交易。 您可能不需使用全部的功能，但知道它們的作用是有幫助的。  
  
 Web 服務是一些程式，其介面符合為 Web 服務描述語言 (WSDL) 設定的標準。 透過以標準方式定義訊息類型、連接埠、連接埠類型及作業，不同的系統能彼此有效地溝通。  
  
 「相互關聯」是讓訊息與協調流程的特定執行中執行個體產生關聯的機制，可以在執行多個執行個體且有許多訊息來回傳遞時，讓您的商務程序取得適當的資訊。  
  
 交易可讓您在未預期的問題發生時，適當地維持協調流程的狀態。 「協調流程設計師」提供處理例外狀況的各種方法，使您能夠透過可控管和預測的方式來處理錯誤。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [協調流程設計介面](../core/the-orchestration-design-surface.md)  
  
-   [BizTalk 協調流程 索引標籤工具箱](../core/biztalk-orchestrations-tab-toolbox.md)  
  
-   [在協調流程開發中的步驟](../core/steps-in-orchestration-development.md)  
  
-   [開發協調流程的安全性考量](../core/security-considerations-for-developing-orchestrations.md)  
  
-   [XLANG 的語言](../core/xlang-s-language.md)  
  
-   [關於 BizTalk 協調流程引擎](../core/about-the-biztalk-orchestration-engine.md)