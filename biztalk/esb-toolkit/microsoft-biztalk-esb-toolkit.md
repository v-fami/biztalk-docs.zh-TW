---
title: "Microsoft BizTalk ESB 工具組 |Microsoft 文件"
description: "簡介、 常見的案例和 ESB toolkit，BizTalk Server 中的元件"
caps.latest.revision: "14"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17ffaebc-7e33-4de8-8e94-109cd5d16ca0
ms.author: mandia
ms.openlocfilehash: 1763ed4bb7f090b91565c3a5f5f480d2c081b48c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="microsoft-biztalk-esb-toolkit"></a>Microsoft BizTalk ESB 工具組
![BizTalk ESB 工具組標誌](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")  
  
## <a name="summary"></a>摘要  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]支援鬆散偶合的傳訊架構。 BizTalk Server 包含的功能強大的發佈/訂閱機制傳訊的運作方式是建立的應用程式和填滿訂閱，其可提供高效率且可擴充的平台服務導向架構 (SOA) 應用程式。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk Server 提供的新功能，專注於建置穩固、 連線、 服務導向整合行程為基礎的服務引動過程輕量型的服務的應用程式範圍的功能組合、 動態解析的端點和地圖、 Web 服務和 WS-* 整合，錯誤管理和報表，以及與第三方 SOA 控管解決方案的整合。  
  
## <a name="overview"></a>概觀  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供的架構指引、 模式和 BizTalk Server 和.NET Framework 元件，以簡化開發的企業服務匯流排 (ESB) 上的 Microsoft 平台，並允許以擴充 Microsoft 客戶的集合他們自己的訊息和整合解決方案。  
  
## <a name="common-scenarios"></a>常見狀況  
 實作基礎結構啟用服務導向架構 (SOA) 的內容中廣泛使用企業服務匯流排 (ESB) 一詞。 不過，與 SOAs 部署的實際經驗顯示 ESB 是其中一個進行向上完整 Service-Oriented 基礎結構 (SOI) 的許多建置組塊。 ESB 已更改一詞在許多不同的方向，以及其定義取決於個別 ESB 和整合平台廠商解譯和需求的特定 SOA initiatives。  
  
 根據 Microsoft 已收集了與許多成功的真實世界 SOI 實作的體驗，您可以想像 ESB 傳統企業應用程式整合 (EAI)、 訊息導向中介軟體為基礎的架構模式的集合Web 服務、.NET 和 Java 的互通性、 主機系統整合，以及與服務和資產的儲存機制的互通性。  
  
 圖 1 顯示的互連 ESB 架構可以提供類型的高階檢視。  
  
 ![ESB 概觀](../esb-toolkit/media/esboverview.gif "ESBOverview")  
  
 **圖 1**  
  
 **連線的高階範例提供的企業服務匯流排架構**  
  
## <a name="audience-requirements"></a>對象的需求  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]僅供開發人員建立 Microsoft BizTalk Server 解決方案或其他解決方案使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件。 若要充分利用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，開發人員應該擁有知識和遇到具有下列工作：  

- [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

- [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]
  
-   Microsoft.NET 開發技術，包括 ASP.NET Web 服務和.NET Framework 元件的開發  
  
## <a name="design-goals"></a>設計目標  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含一系列的支援和實作鬆散偶合的傳訊環境，可讓您更輕鬆地建立以訊息為基礎的企業應用程式元件間的互通性。 服務和元件自然可分成下列七個類別：  
  
-   **Web 服務**： 這些公開內部服務，例如路線處理例外狀況管理、 端點和地圖、 BizTalk Server 作業，以及訊息轉換的解析度。  
  
-   **路線服務**： 包括執行行程為基礎的路由協調流程和傳訊為主服務[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 您可以建立自訂服務的行程為基礎的路由。  
  
-   **路線上-坡道提升。** 這些接收外部的訊息、 附加適當的路線，每個訊息，以及執行路線處理;他們使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，來動態解析的端點和中繼資料。  
  
-   **在坡道提升**： 這些接收外部訊息格式和傳輸，例如 HTTP、 JMS、 WMQ、 FTP、 一般檔案和 XML 的範圍中。 它們是典型的 BizTalk Server 接收位置，或者使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，來動態解析的端點和中繼資料。  
  
-   **關閉坡道提升**： 這些實作使用之格式和傳輸，例如 SOAP、 WCF、 JMS、 WMQ、 FTP、 HTTP、 一般檔案、 XML 或任何其他自訂格式的訊息的傳遞傳送埠。 它們是一般 BizTalk Server 動態傳送埠，會直接繫結至 Messagebox，並選擇性地使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和動態的端點解析的配接器提供者架構與中繼資料。  
  
-   **例外狀況管理架構**： 這包括例外狀況的例外狀況管理應用程式開發介面，Web 服務和元件的擴充，程序，將例外狀況詳細資料傳遞給 ESB 管理入口網站。  
  
-   **ESB 管理入口網站**： 這會提供登錄佈建、 例外狀況中繼、 警示的通知和分析。  
  
 許多這些元件和服務所實作的功能上都必須依賴[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，例如協調流程、 轉換和商務規則引擎和 Messagebox 資料庫。 圖 2 顯示的圖解檢視的類別。元件和服務通常發生在每個類別。所使用的核心 BizTalk Server 系統元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
 ![ESB 架構](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
 **圖 2**  
  
 **架構和元件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>BizTalk ESB 工具組的運作方式  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]接受輸入的訊息，並執行運算，可能是 （但並非一定） 上執行處理程序，例如轉換、 傳遞或任何其他自訂定義處理程序。 若要指定作業所需，核心處理元件所需的訊息來包含相關聯的指示或定義要套用的程序的中繼資料及訊息內容下執行的工作。  
  
 這種方法可提供服務; 之間的鬆散結合這表示 ESB 不需要事先了解之特定處理的每個訊息。 它只需要知道處理程序，以及如何套用每個處理序的可能範圍。 指定可用的處理序和處理程序與在訊息中的指示之間的對應之選項的各種提供彈性的機制，來設定和調整行為，而不需要變更程式碼和重新部署元件。  
  
## <a name="in-this-section"></a>本節內容

- [安裝和設定 Microsoft BizTalk ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)

- [BizTalk ESB 工具組簡介](introduction-to-the-biztalk-esb-toolkit.md)

- [開始使用，並了解 BizTalk ESB Toolkit](getting-started-with-the-biztalk-esb-toolkit.md)

- [重要案例及開發工作](key-scenarios-and-development-tasks.md)

- [建立行程使用路線設計工具](creating-itineraries-using-itinerary-designer.md)

- [BizTalk ESB 工具組範例應用程式](biztalk-esb-toolkit-sample-applications.md)

- [修改和擴充 BizTalk ESB Toolkit](modifying-and-extending-the-biztalk-esb-toolkit.md)

- [使用 BizTalk ESB 工具組系統管理](administration-with-the-biztalk-esb-toolkit.md)

- [SOA 控管整合](soa-governance-integration.md)

- [疑難排解 BizTalk ESB 工具組](troubleshooting-the-biztalk-esb-toolkit.md)
  
## <a name="related-topics"></a>相關主題  
  
-   [BizTalk 服務導向解決方案](../core/service-oriented-solution.md)

- [使用 BizTalk Server Web 服務](../core/using-web-services.md)  