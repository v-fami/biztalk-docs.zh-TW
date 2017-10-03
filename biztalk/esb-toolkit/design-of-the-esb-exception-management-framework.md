---
title: "在 ESB 例外狀況管理架構的設計 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfc2688c-c01c-4244-9e35-3d482135d8b7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c9bf8691701aa9fba8060865fcd3cb5abfba06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="design-of-the-esb-exception-management-framework"></a>在 ESB 例外狀況管理架構的設計
一致且可重複使用管理例外狀況的模式是核心考量任何開發專案。這些資訊可協助最大化可維護性，並簡化支援應用程式部署之後。  
  
 典型的 BizTalk 應用程式可能會使用 BizTalk 傳訊功能、 選擇性地開始處理協調流程、 呼叫商務規則引擎、 數的特定業務 (LOB) 或企業資源規劃 (ERP) 系統互動以及傳回個別的協力廠商系統的回應。 此外，這些元件，包括 BizTalk 子系統的執行階段位置可能位於分散於整個目前環境的一或多個伺服器上。 這是常見的案例，並且需要系統支援攔截和報告例外狀況，可能會發生的任何 ESB 或 BizTalk 分離子系統，或在各種協力廠商 LOB 系統中，每一個都有它自己的例外狀況處理條件約束。 例如，大型主機可能會拒絕正常處理期間，從網站傳送訂單網站必須修正這個錯誤，並通知使用者。  
  
 ESB 應用程式的複雜性和其環境中，由於一致的應用程式例外狀況管理方案的開發應該只限下列常見的設計目標：  
  
-   提供標準化的方法來偵測及 BizTalk Server 環境中發生的例外狀況處理 (亦即，傳訊與協調流程子系統中)。  
  
-   提供一般模式，好讓自動化程序來回應，以及管理應用程式例外狀況。  
  
-   提供的鬆散偶合的例外狀況管理模式，可促進重複使用。  
  
-   應用程式例外狀況，其可用的訊息狀態可套用至任何 BizTalk 子系統提供常見的報告機制。  
  
 若要了解為什麼[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供一個機制，自訂錯誤，也就是在例外狀況管理架構，以及它的運作方式，就必須了解可在 BizTalk Server 和為什麼這些功能不是完整的例外狀況管理功能能夠達到上述的設計目標。  
  
## <a name="biztalk-server-exception-reporting"></a>BizTalk Server 例外狀況報告  
 BizTalk Server 支援下列的例外狀況處理和報告機制：  
  
-   失敗的訊息路由  
  
-   BizTalk Server 管理主控台  
  
-   Microsoft 事件記錄檔  
  
-   自訂開發選項  
  
 根據預設，BizTalk Server 例外狀況處理功能依賴許多操作人員介入。 例如，假設當使用者送出至 BizTalk Server 會在驗證階段期間發生例外狀況的訊息。 根據預設，訊息會發佈到 Messagebox 資料庫，則會路由傳送到擱置佇列。 這表示，操作員必須下列作業：  
  
-   獨立偵測到發生例外狀況。  
  
-   手動儲存失敗的訊息，使用磁碟[!INCLUDE[prague](../includes/prague-md.md)]管理主控台。  
  
-   手動編輯和更正的訊息，並重新送出至系統。 在某些情況下，此程序可能會發生遺失的重要內容資訊。  
  
 若要解決這些問題，[!INCLUDE[prague](../includes/prague-md.md)]提供失敗訊息路由的機制。 開發人員和管理員可以使用這個來建立協調流程或傳訊的傳送埠設定為訂閱傳訊子系統中發生任何例外狀況。 這可提供自動化的錯誤偵測與路由機制，會保留原始訊息的狀態，並解決偵測到例外狀況的問題。  
  
 協調流程未提供自動的失敗的訊息路由，因為開發人員必須負責錯誤例外狀況處理常式區塊新增到協調流程範圍圖形。 使用此解決方案中，每個協調流程可以有它自己的例外狀況處理，但沒有任何機制可重複使用例外狀況處理跨多個協調流程的功能。  
  
 這表示，現在有兩個非常不同的方式在其中訊息的例外狀況處理與在 BizTalk Server 系統中，管理，以及哪一個協調流程中處理例外狀況的第三個方法。 因此，開發人員必須自訂的例外狀況處理機制，以符合自己的需求，如果他們想要實作符合本節中稍早所述之需求的系統。  
  
## <a name="biztalk-server-administration-console"></a>BizTalk Server 管理主控台  
 [!INCLUDE[prague](../includes/prague-md.md)]管理主控台提供一組群組概觀頁面，稱為 BizTalk 群組的中樞。 使用這些頁面時，系統管理員可以查詢擱置的訊息和例外狀況，依應用程式、 服務名稱、 錯誤代碼或 URI，如圖 1 所示。  
  
 ![系統管理員主控台](../esb-toolkit/media/ch4-adminconsole.gif "第 4 章第 AdminConsole")  
  
 **圖 1**  
  
 **[!INCLUDE[prague](../includes/prague-md.md)]系統管理主控台群組概觀頁面**  
  
 雖然 [群組概觀] 功能提供了通用使用者介面來檢視例外狀況，但是這些檢視會受限於 「 即時 」 服務執行個體。 檢查狀態可以是麻煩的工作，因為系統管理員必須向下鑽研至每個項目樹狀結構。 此外，許多其他因素會限制 BizTalk Server 管理主控台功能做為應用程式例外狀況報告工具：  
  
-   沒有任何功能採礦的商業智慧資料。 比方說，您無法查詢的每月為基礎的最差違規應用程式，或檢查應用程式例外狀況的每季趨勢。  
  
-   企業可能會需要某些應用程式例外狀況發生時或達到特定的閾值時發出警示，但沒有任何設備，訂閱這些類型的例外狀況事件。  
  
-   Microsoft Management Console (MMC) 的管理主控台會使用為其使用者介面 (UI) 機制不是理想的介面，而且它不一定方便在生產環境中存取。 最小值，會要求使用者必須是 「 BizTalk 操作員 」 角色; 的成員而，在生產環境中存取 MMC 也通常僅能透過終端機伺服器。  
  
-   主控台會顯示只有未處理例外狀況 （已擱置的服務執行個體）。 如果開發人員可以處理協調流程中的例外狀況，讓協調流程，一般來說，完成的例外狀況資訊會永遠不會出現在 [管理] 主控台。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]透過 ESB 無法協調流程的例外狀況路由機制會解決這些限制。 這會非常接近的失敗訊息路由機制[!INCLUDE[prague](../includes/prague-md.md)]。 此外，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]訂閱從 ESB 無法協調流程的例外狀況路由的機制和失敗訊息路由機制產生的訊息的傳送埠中包含的管線元件，然後加以正規化。  
  
 在 ESB 例外狀況管理架構利用其他功能在 BizTalk Server 中，例如訂閱模型和以事件為基礎商務活動監控 (BAM)。 這表示 ESB 例外狀況管理架構可以追蹤例外狀況資料點與 BAM，並將它們發行到 BizTalk BAM 入口網站使用監視。