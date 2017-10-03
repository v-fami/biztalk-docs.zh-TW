---
title: "BizTalk ESB 工具組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08035518-17ad-44d2-ab06-90d725c95ced
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 535fd99ee5c1b9f9c25dd49e2a2441acb855c78a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit"></a>BizTalk ESB 工具組
Microsoft BizTalk ESB 工具組會使用 Microsoft BizTalk Server 支援鬆散偶合的傳訊架構。 BizTalk Server 包含的功能強大的發佈/訂閱機制傳訊的運作方式是建立的應用程式和填滿訂閱，其可提供高效率且可擴充的平台服務導向架構 (SOA) 應用程式。 BizTalk ESB Toolkit 會擴充 BizTalk Server 提供的新功能，專注於建置穩固、 連線、 服務導向整合行程為基礎的服務引動過程輕量型的服務的應用程式範圍的功能組合、 動態解析的端點和地圖、 Web 服務和 WS-* 整合，錯誤管理和報表，以及與第三方 SOA 控管解決方案的整合。  
  
## <a name="overview"></a>概觀  
 BizTalk ESB Toolkit 提供的架構指引、 模式和 BizTalk Server 和.NET Framework 元件，以簡化開發的企業服務匯流排 (ESB) 上的 Microsoft 平台，並允許以擴充 Microsoft 客戶的集合他們自己的訊息和整合解決方案。  
  
## <a name="common-scenarios"></a>常見狀況  
 實作基礎結構啟用服務導向架構 (SOA) 的內容中廣泛使用企業服務匯流排 (ESB) 一詞。 不過，與 SOAs 部署的實際經驗顯示 ESB 是其中一個進行向上完整 Service-Oriented 基礎結構 (SOI) 的許多建置組塊。 ESB 已更改一詞在許多不同的方向，以及其定義取決於個別 ESB 和整合平台廠商解譯和需求的特定 SOA initiatives。 根據 Microsoft 已收集了與許多成功的真實世界 SOI 實作的體驗，您可以想像 ESB 傳統企業應用程式整合 (EAI)、 訊息導向中介軟體為基礎的架構模式的集合Web 服務、.NET 和 Java 的互通性、 主機系統整合，以及與服務和資產的儲存機制的互通性。  
  
## <a name="audience-requirements"></a>對象的需求  
 BizTalk ESB Toolkit 適用於開發人員建立 Microsoft BizTalk Server 解決方案或其他解決方案使用 BizTalk ESB 工具組元件。 若要充分利用 BizTalk ESB Toolkit，開發人員應該擁有知識，並遇到具有下列工作：  
  
1.  Microsoft BizTalk Server  
  
2.  Microsoft Visual Studio  
  
3.  Microsoft.NET 開發技術，包括 ASP.NET Web 服務和.NET Framework 元件的開發  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>BizTalk ESB 工具組的運作方式  
 BizTalk ESB Toolkit 接受輸入的訊息，並執行運算，可能是 （但並非一定） 上執行處理程序，例如轉換、 傳遞或任何其他自訂定義處理程序。 若要指定作業所需，核心處理元件所需的訊息來包含相關聯的指示或定義要套用的程序的中繼資料及訊息內容下執行的工作。   
這種方法可提供服務; 之間的鬆散結合這表示 ESB 不需要事先了解之特定處理的每個訊息。 它只需要知道處理程序，以及如何套用每個處理序的可能範圍。 指定可用的處理序和處理程序與在訊息中的指示之間的對應之選項的各種提供彈性的機制，來設定和調整行為，而不需要變更程式碼和重新部署元件。  
  
## <a name="getting-started"></a>快速入門  
 安裝 BizTalk ESB Toolkit 之後，您應該閱讀中的"Getting Started"主題[BizTalk ESB Toolkit 文件](http://go.microsoft.com/fwlink/?LinkId=193578)瞭解架構、 訊息流程，以及 BizTalk ESB Toolkit 的核心元件。 您也應該安裝並執行範例隨附於 BizTalk ESB Toolkit，可示範"Getting Started"主題和其他傳訊的案例中所述的常見使用案例。 這種方法將協助您快速掌握 BizTalk ESB Toolkit 的運作方式以及您可在自己的 SOA 應用程式中利用其功能。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 企業服務指導方針](http://go.microsoft.com/fwlink/?LinkId=193577)   
 [服務導向解決方案](../core/service-oriented-solution.md)   
 [使用 Web 服務](../core/using-web-services.md)