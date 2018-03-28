---
title: BizTalk ESB 工具組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08035518-17ad-44d2-ab06-90d725c95ced
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 535fd99ee5c1b9f9c25dd49e2a2441acb855c78a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="biztalk-esb-toolkit"></a>BizTalk ESB 工具組
Microsoft BizTalk ESB 工具組會使用 Microsoft BizTalk Server 支援鬆散結合的訊息結構。 BizTalk Server 包含功能強大的發佈/訂閱機制訊息的方式就是建立應用程式和填滿訂閱，可提供高度有效率且可擴充的平台的服務導向架構 (SOA) 應用程式。 BizTalk ESB Toolkit 擴充功能的 BizTalk Server 提供一系列的新功能，著重於建置穩固、 連線、 服務導向應用程式，納入行程為基礎的服務引動過程的輕量服務組合、 動態的解決方式的端點和地圖、 Web 服務和 WS-* 整合、 錯誤管理和報告，以及與協力廠商 SOA 控管解決方案整合。  
  
## <a name="overview"></a>概觀  
 BizTalk ESB 工具組提供架構指導方針、 模式和簡化開發工作的企業服務匯流排 (ESB) 在 Microsoft 平台，並允許 Microsoft 客戶延伸自己的訊息和整合方案的 BizTalk Server 和.NET Framework 元件的集合。  
  
## <a name="common-scenarios"></a>常見狀況  
 企業服務匯流排 (ESB) 廣泛實作啟用服務導向架構 (SOA) 的基礎結構的內容中的詞彙。 不過，與 soa 都極為部署的實際經驗顯示 ESB 是其中一個多進行完整推動基礎結構 (SOI) 組成的建置組塊。 ESB 已更改一詞在許多不同的方向，以及其定義取決於個別的 ESB 和整合平台廠商的解譯和特定的 SOA 開發案的需求。 Microsoft 已收集了許多成功的真實世界 SOI 實作從經驗為基礎，您可以想像 ESB 架構模式，根據傳統的企業應用程式整合 (EAI)、 訊息導向中介軟體、 Web 服務、.NET 和 Java 互通性、 主機系統整合，以及與服務註冊和資產的儲存機制的互通性的集合。  
  
## <a name="audience-requirements"></a>必備條件  
 BizTalk ESB 工具組適用於開發人員建立 Microsoft BizTalk Server 解決方案或其他解決方案使用 BizTalk ESB 工具組元件。 若要充分利用 BizTalk ESB 工具組，開發人員應該具備的知識和經驗提供了下列工作︰  
  
1.  Microsoft BizTalk Server  
  
2.  Microsoft Visual Studio  
  
3.  Microsoft.NET 開發技術，包括 ASP.NET Web 服務與.NET Framework 元件開發  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>BizTalk ESB Toolkit 的運作方式  
 BizTalk ESB Toolkit 接受輸入的訊息，並執行運算，或許是 （但不是一定） 執行處理序，例如轉換、 傳遞或任何其他自訂定義程序。 若要指定作業所需，核心處理元件所需的訊息包含相關聯的指示或定義要套用的程序的中繼資料及訊息內容下執行的工作。   
這種方法可提供服務; 之間的鬆散結合這表示 ESB 不需要事先知道特定處理的每個訊息。 它只需要知道處理程序，以及如何套用每個處理序的可能範圍。 指定可用的處理序和處理程序與在訊息中的指示之間的對應選項的各種提供彈性的機制，來設定和調整行為，而不需要變更程式碼，並重新部署的元件。  
  
## <a name="getting-started"></a>快速入門  
 安裝之後 BizTalk ESB 工具組，您應該閱讀 「 開始 」 中的主題 [BizTalk ESB Toolkit 文件](http://go.microsoft.com/fwlink/?LinkId=193578) 了解架構、 訊息流程的 BizTalk ESB 工具組的核心元件。 您也應該安裝並執行範例 BizTalk ESB 工具組提供示範常見的使用案例的 「 開始 」 主題和其他傳訊案例中所述。 這種方法將協助您快速掌握 BizTalk ESB Toolkit 的運作方式以及您可以利用它的功能在您自己的 SOA 應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 企業服務指導方針](http://go.microsoft.com/fwlink/?LinkId=193577)   
 [服務導向解決方案](../core/service-oriented-solution.md)   
 [使用 Web 服務](../core/using-web-services.md)