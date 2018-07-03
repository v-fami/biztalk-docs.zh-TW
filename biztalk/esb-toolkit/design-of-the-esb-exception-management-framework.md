---
title: ESB 例外狀況管理架構的設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfc2688c-c01c-4244-9e35-3d482135d8b7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f25bec37d7ee6ec02db5db28e32ce8ed5b62f724
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996575"
---
# <a name="design-of-the-esb-exception-management-framework"></a>ESB 例外狀況管理架構的設計
管理例外狀況一致且可重複使用模式是任何開發專案; 的 core 考量這些資訊可協助最大化可維護性，並讓它更容易支援在部署後的應用程式。  
  
 典型的 BizTalk 應用程式可能會使用 BizTalk 傳訊功能，選擇性地開始處理協調流程、 呼叫商務規則引擎、 互動數個的營運 (LOB) 或企業資源規劃 (ERP) 系統，並傳回個別的協力廠商系統的回應。 此外，這些元件，包括 BizTalk 子系統中，執行階段位置可能位於分散於目前的環境的一或多個伺服器上。 這是典型的案例，而且需要系統支援攔截並報告例外狀況，可能會發生的任何 ESB 或 BizTalk 分離子系統，或在各種協力廠商 LOB 系統中，每個都有它自己的例外狀況處理條件約束。 例如，大型主機可能會拒絕在正常處理週期內，從網站傳送訂單網站必須補償這項錯誤，並通知使用者。  
  
 因為 ESB 應用程式的複雜性和其環境，開發應用程式例外狀況管理一致的解決方案應該對下列常見的設計目標：  
  
- 提供的標準的方法來偵測及 BizTalk Server 環境中發生的例外狀況處理 (也就是傳訊與協調流程的子系統中)。  
  
- 提供允許自動化的程序來回應，以及管理應用程式例外狀況的常見模式。  
  
- 提供鬆散耦合的例外狀況管理模式，可促進重複使用。  
  
- 應用程式例外狀況和其可用的訊息狀態可套用至任何 BizTalk 子系統提供常見的報告機制。  
  
  若要了解為什麼[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供自訂錯誤的機制，也就是例外狀況管理架構，以及其運作方式，就必須了解適用於 BizTalk Server 和為什麼這些功能不完整的例外狀況管理功能能夠達到上述的設計目標。  
  
## <a name="biztalk-server-exception-reporting"></a>BizTalk Server 例外狀況報告  
 BizTalk Server 支援下列的例外狀況處理和報告機制：  
  
- 失敗的訊息路由  
  
- BizTalk Server 管理主控台  
  
- Microsoft 事件記錄檔  
  
- 自訂開發選項  
  
  根據預設，處理例外狀況的 BizTalk Server 功能依賴大量操作人員介入。 比方說，請考慮當使用者送出訊息至 BizTalk Server 會在驗證階段期間發生例外狀況的情況。 根據預設，訊息會發佈到 Messagebox 資料庫，它會路由傳送到擱置佇列。 這表示，操作員必須下列作業：  
  
- 獨立偵測到發生例外狀況。  
  
- 手動儲存使用 BizTalk Server 管理主控台，在磁碟失敗的訊息。  
  
- 手動編輯，並修正訊息，並重新送出至系統。 在某些情況下，此程序可能會發生遺失的重要內容資訊。  
  
  若要解決這些問題，BizTalk Server 會提供失敗訊息路由的機制。 開發人員和管理員可以使用這個來建立協調流程或傳訊傳送埠設定為訂閱傳訊子系統中發生任何例外狀況。 這會提供自動化的錯誤偵測與路由機制，會保留原始的 「 訊息 」 狀態，並解決偵測到例外狀況的問題。  
  
  因為協調流程不提供自動的失敗的訊息路由，開發人員必須考慮錯誤例外狀況處理常式區塊新增到協調流程範圍圖形。 此解決方案中，每個協調流程可以有它自己的例外狀況處理，但沒有機制可以重複使用的例外狀況處理功能，跨多個協調流程。  
  
  這表示，現在有兩個非常不同的方式在其中傳訊例外狀況處理與在 BizTalk Server 系統中，管理和例外狀況處理的協調流程中的第三個方法。 因此，開發人員必須自訂的例外狀況處理機制，以符合他們自己的需求，如果他們想要實作系統符合本章節稍早所述的需求。  
  
## <a name="biztalk-server-administration-console"></a>BizTalk Server 管理主控台  
 BizTalk Server 管理主控台提供一組群組概觀頁面，稱為 BizTalk 群組的中樞。 使用這些頁面時，系統管理員可以查詢擱置的訊息和例外狀況，依應用程式、 服務名稱、 錯誤代碼或 URI，如 圖 1 所示。  
  
 ![系統管理員主控台](../esb-toolkit/media/ch4-adminconsole.gif "第 4 章第 AdminConsole")  
  
 **圖 1**  
  
 **[BizTalk Server 管理主控台群組概觀] 頁面**  
  
 雖然 [群組概觀] 功能提供常見的使用者介面，以檢視例外狀況，但檢視會受限於 「 即時 」 服務執行個體。 檢查狀態可能會很麻煩的工作，因為系統管理員必須向下鑽研至每個項目樹狀結構。 此外，許多其他因素會限制 BizTalk Server 管理主控台功能做為應用程式例外狀況報告工具：  
  
- 沒有適用於採礦的資料商業智慧功能。 比方說，您無法查詢的最差有問題的應用程式，每月為基礎，或檢查應用程式例外狀況的每季趨勢。  
  
- 企業可能需要以特定的應用程式例外狀況發生時或達到特定臨界值，會引發的警示，但沒有任何設備可訂閱這些類型的例外狀況事件。  
  
- Microsoft Management Console (MMC) 的 [管理] 主控台做為其使用者介面 (UI) 機制不是理想的介面，而且它不一定便利在生產環境中存取。 最小值，會要求使用者必須是 「 BizTalk 操作員 」 角色; 的成員而，生產環境中，存取 MMC 也通常僅能透過終端機伺服器。  
  
- 主控台會顯示只有未處理例外狀況 （已擱置的服務執行個體）。 如果開發人員處理協調流程中的例外狀況，讓協調流程，一般來說，完成的例外狀況資訊會永遠不會出現在 [管理] 主控台。  
  
  [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] ESB 失敗的協調流程例外狀況路由機制透過解決了這些限制。 這類似 BizTalk Server 的失敗訊息路由機制。 颾魤 ㄛ[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]訂閱訊息產生自 ESB 失敗的協調流程例外狀況路由機制和失敗訊息路由的機制傳送埠中包含的管線元件，並將它們正規化。  
  
  ESB 例外狀況管理架構利用其他功能在 BizTalk Server 中，例如訂用帳戶模型，以及事件為基礎商務活動監控 (BAM)。 這表示可以追蹤例外狀況的資料點，使用 BAM，ESB 例外狀況管理架構，並將其發行至 BizTalk BAM 入口網站來監視。