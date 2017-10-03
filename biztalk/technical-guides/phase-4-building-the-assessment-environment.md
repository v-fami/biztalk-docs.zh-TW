---
title: "第 4 個階段： 建立評估環境 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b90d7c5-60ca-4a81-b3d9-6d4e9d91e684
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8246ccd34d36f42bf9d8013baf8b73d557fae6eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="phase-4-building-the-assessment-environment"></a>第 4 個階段： 建立評估環境
建立實驗室效能評估階段用來安裝的硬體和軟體環境中前一個階段中的設計決策的一致性。 建立實驗室階段可能會很費時，因為它不重疊稍早階段的此階段不尋常。 在許多情況下，硬體和作業系統可能會先安裝最終決定對於應用程式架構。 效能評定的組建實驗室階段通常包括本主題中討論的工作。  
  
## <a name="obtain-all-build-lab-infrastructure-at-least-a-week-in-advance-of-the-lab-start-date"></a>取得實驗室開始日期之前至少一週的所有組建實驗室基礎結構  
 實驗室開始日期前一週至少有必要的硬體和軟體的所有可用的計劃。 這可確保的必要的基礎結構要為不會浪費寶貴實驗室時間。  
  
## <a name="configure-third-party-software-systems"></a>設定第三方軟體系統  
 可能需要建立和設定，才能開始進行實驗室的協力廠商系統。 如果需要這些系統的相關主題專家 (Sme)，請務必外延展組建和實驗室執行階段排程。 請確定它們完整記錄其建置出程序。  
  
## <a name="install-and-configure-the-biztalk-server-environment"></a>安裝和設定 BizTalk Server 環境  
 詳細的安裝指示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和必要的相依性軟體位於[BizTalk Server 2010 安裝和升級指南](http://go.microsoft.com/fwlink/?LinkID=191321)(http://go.microsoft.com/fwlink/?LinkID=191321)。 已成功安裝和設定 BizTalk Server 環境之後, 就可以完成下列工作：  
  
-   請遵循列示的建議[操作的整備檢查清單](http://go.microsoft.com/fwlink/?LinkId=160134)(http://go.microsoft.com/fwlink/?LinkId=160134)。  
  
-   請遵循建議[最佳化效能](../technical-guides/optimizing-performance.md)。  
  
-   請確定所有電腦的時間正確同步都處理。  
  
-   請確認在環境中的所有電腦之間的 MSDTC 功能。  
  
-   請確定任何自訂的追蹤/記錄已停用，除非絕對必要的。  
  
-   安裝 Visual Studio 2010 Ultimate edition 進行負載測試。  如需如何執行自動化測試使用 Visual Studio 的詳細資訊，請參閱[有助於自動化測試使用 Visual Studio](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)。  
  
-   安裝程式的效能監視器計數器和記錄檔，視需要。  
  
-   安裝程式的偵錯的電腦效能評估的範圍內的程式碼變更時，偵錯方案。  
  
-   所有的硬碟進行磁碟重組。  
  
-   停用防毒即時掃描。  
  
-   備份企業單一登入主要密碼。  
  
## <a name="install-the-biztalk-server-application-to-be-tested"></a>安裝 BizTalk Server 應用程式進行測試  
 要測試應用程式的安裝通常會包含下列步驟：  
  
1.  使用 BizTalk Server 管理主控台執行下列動作：  
  
    -   建立主控件  
  
    -   建立傳送/接收處理常式。  
  
    -   建立主控件執行個體。  
  
    -   建立 BizTalk Server 應用程式。  
  
2.  應用程式安裝：  
  
    1.  將 BizTalk Server 二進位檔部署到 BizTalk Server 群組。  
  
    2.  繫結匯入至 BizTalk Server 群組。  
  
    3.  GAC BizTalk Server 和非 BizTalk Server 二進位檔的所有方塊。  
  
    4.  請確定所有的方塊上存在相依性元件。  
  
3.  安裝相依性的應用程式。  
  
4.  在 BizTalk Server 管理主控台中設定傳輸與實體端點。  
  
5.  啟動服務。  
  
6.  執行基本煙霧測試; 煙霧測試端對端功能測試，測試您的解決方案的基本功能。  
  
## <a name="implement-automated-build-and-load-testing"></a>實作自動化的建置和負載測試  
 自動化的建置和負載測試處理程序的實作可說是 BizTalk Server 效能評定的基石。 如果程式碼變更效能評估的範圍內，就應該實作自動化的建置程序。 自動化的負載測試應該實作所有的負載測試案例。 實作自動化的建置和負載測試所需的初始時間投資的原因是快速，automation 可容納的人為錯誤受限於一般建置/測試工作的快速、 精確地重複。 如需實作自動化的組建和測試程序的詳細資訊，請參閱[實作自動化的測試](../technical-guides/implementing-automated-testing.md)本指南中。  
  
## <a name="configure-performance-monitoring"></a>設定效能監視  
 精確的效能監視成功很重要的效能評估。 決定應評估的效能計量根據 「 範圍 」 階段中定義的輸送量和延遲目標。 效能監視應在 BizTalk Server 環境中的每一部電腦上執行。 如需適用於 BizTalk Server 2010 的效能計數器的詳細資訊，請參閱[效能計數器](http://go.microsoft.com/fwlink/?LinkID=157269)(http://go.microsoft.com/fwlink/?LinkID=157269) BizTalk Server 2010 說明中。 您可以使用效能記錄檔的分析工具 (PAL) 來產生重要的效能計數器的圖表以圖形方式和當超過這些計數器的閾值時產生警示的 HTML 報表。 如需有關[效能分析的記錄檔 (PAL) 工具](http://go.microsoft.com/fwlink/?LinkID=98098)，請參閱[效能分析的記錄檔 (PAL) 工具](http://go.microsoft.com/fwlink/?LinkID=98098)(http://go.microsoft.com/fwlink/?LinkID=98098)。  
  
## <a name="establish-and-document-the-solutions-baseline-performance"></a>建立與記錄方案的基準效能  
 基準效能應該計算，以便您可以測量效能評估期間套用的效能最佳化的效果。  
  
## <a name="see-also"></a>另請參閱  
 [效能評定階段](../technical-guides/phases-of-a-performance-assessment.md)