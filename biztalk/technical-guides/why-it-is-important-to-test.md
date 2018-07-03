---
title: 請務必測試的原因 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce91aca5-56d3-4fb8-abe2-af0039804706
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a74f22813f9752f82985d2e984f5effeb3208e6e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009167"
---
# <a name="why-it-is-important-to-test"></a>要測試的重要性
本主題提供概略說明心態上沒有足夠的測試，說明無法測試 BizTalk 解決方案的相關風險，以及比對的手動測試的自動化測試優點陷阱。  
  
## <a name="testing-as-overhead"></a>測試 「 負擔 」  
 不幸的是，與不斷增加的投資回報率 (ROI) 需求，專案的測試階段是經常會看到第一個部分可以是專案計劃的隨相應的上一步。  
  
 針對測試 BizTalk 解決方案的一個引數是 「 我們不需要測試我們的解決方案，因為 Microsoft 已經徹底測試 BizTalk Server。 」 不同的使用案例，則為 true，Microsoft 徹底測試 BizTalk Server 時，輸送量、 高可用性、 配接器使用狀況、 延遲、 追蹤需求，需要其中一個幾乎無數的商務需求的排列數目協調流程使用方式，以及自訂程式碼。 BizTalk Server 極具彈性，而且可以容納許多不同的使用案例，因為它不只能夠預測，並測試所有人都。 此外，BizTalk Server 環境中套用的預設設定應該最佳化，可容納每個使用案例。 判斷特定使用案例的最佳設定的唯一方式是測試方案、 測量各種不同的參數，調整環境，並重新測試。 請考慮下列圖表描述 BizTalk Server 解決方案的範例實體架構。  
  
 ![BizTalk Server 部署架構](../technical-guides/media/5359cf00-e285-4168-a988-8d3b677eb6ba.gif "5359cf00-e285-4168-a988-8d3b677eb6ba")  
實體 BizTalk 架構範例  
  
 您可以看到在其上方圖表中的 BizTalk Server 解決方案包含許多移動組件，包括多部電腦執行 BizTalk Server 中，執行 SQL Server、 伺服器叢集節點，以及 Active Directory 網域的電腦。 系統已啟動並執行之後，將會套用至最佳化每個商務需求，對於整體解決方案的 ROI 最大化應用程式的許多設定調整。 此單一案例會示範在 play 中有許多變數。 除了實體環境的架構，請考慮下列圖表說明透過 BizTalk Server 訊息的流程。  
  
 ![透過 BizTalk Server 訊息的流程](../technical-guides/media/dea79a42-5f60-49a1-abdb-870988784ffe.gif "dea79a42-5f60-49a1-abdb-870988784ffe")  
範例 BizTalk 的邏輯訊息流程  
  
 當我們查看的訊息通過 BizTalk Server 的邏輯圖時，我們會看到其他需要測試每個專案，包括自訂傳送和接收管線元件，您可以從 BizTalk 協調流程呼叫的自訂類別的變數。 假設的型別複雜性和使用自訂的元件和 BizTalk 元件各有不同的專案對專案，會變得更加明顯極為重要來執行測試，每個特定使用實例的原因。  
  
## <a name="testing-methodology-and-timelines"></a>測試方法與時間軸  
 若要確保有效率而有效地測試執行，測試控管應該能完全自動化，並且讓它輕鬆地重現的人為疏失的機會降到最低。 此外，應配置足夠的時間，測試計劃專案時。 若要測試最簡單的方法，但是構成如下所示的手動步驟：  
  
1. 手動載入接收結束點，例如檔案的卸除，或使用 SOAP 用戶端來呼叫 Web 服務的一個或多個訊息。  
  
2. 手動驗證正確的內容和訊息的結構。 多個結構描述通常會出現在專案中的因為訊息可能會混用一般檔案和 XML，而且可能也會包含欄位交互相依性。  
  
   > [!NOTE]  
   >  這個範例會涉及 SWIFT 訊息的任何專案。 這些是具有欄位交互相依性的一般檔案訊息。 也就是一個欄位的值取決於另一個-簡單的 XSD 驗證將不會做因此 SWIFT 加速器會使用 BizTalk 規則引擎以進行驗證的訊息。 如需詳細資訊[SWIFT 加速器](http://go.microsoft.com/fwlink/?LinkID=79657)，請參閱[SWIFT 加速器](http://go.microsoft.com/fwlink/?LinkID=79657)(http://go.microsoft.com/fwlink/?LinkID=79657)。  
  
3. 手動檢查有錯誤的 BizTalk Server 電腦上的事件日誌。  
  
4. 手動檢查 BAM 資料庫 （如果使用） 以驗證活動的資訊正確的記錄。  
  
   使用手動程序，如上面所述，測試是主觀又容易出錯。 請考慮需要檢查幾百行 SWIFT 訊息與跨欄位的 10 個不同的測試案例的相依性。 大部分的專案不能以開發人員，或即使它們，就不比較傾向於穩定且更精確地參與這類工作。 主觀、 手動錯誤容易發生測試程序的實作新增至專案的風險，並增加的失敗機率。  
  
   專案計劃不包含足夠的時間進行測試的時間軸通常是而擴大失敗的風險。 常常策略鉸鏈上即是單一的手動測試通過的測試專案會排定一週推出的日期之前。 這種有限的測試會有風險的專案。 如果偵測到任何問題，請進行測試，提供這種有限的時間軸，然後專案可能會延遲因為已經沒有時間分配以修正問題。 此外，如果問題是發現並修正，有可能不足，無法在系統上線之前，請執行後續的測試進行剩餘的時間。  
  
   "單一的最終建置，單一測試通過，take 專案 live"的測試時，它通常會導致延遲的專案、 預算或更糟，將專案、 專案完全失敗 ！ 對於關鍵任務系統，這種測試方法會是注定發生災難。  
  
## <a name="testing-effectively-and-efficiently"></a>測試有效的方式  
 適當測試通常視為昂貴的 luxury，而不是整數類資料的需求，因為它會常常附加在專案結尾結束。 指定用於異質性企業環境中的軟體和硬體堆疊的複雜性，這個方法會變得不切實際。 可以依需求重新執行自動化的測試方法的實作是測試有效且有效率的最佳方式，也是最終的商業提供絕佳的投資報酬率的成功完成專案不可或缺的元件。 藉由投資在整個系統的每個程式碼路徑的完整端對端功能測試中的專案開始，您會產生測試資產。 這些資產需要投資 （也就是開發時間），以便稍後獲得增加測試的成效與效率的優勢。 若要從專案才能衍生這類架構的投資降到最低，我們建議您利用 Visual Studio 2010 負載測試架構。 Visual Studio 2010 包含大部分的測試成功所需的通用測試步驟，是在本指南中稍後提供的測試案例中使用的架構。  
  
## <a name="see-also"></a>另請參閱  
 [實作自動化的測試](../technical-guides/implementing-automated-testing.md)