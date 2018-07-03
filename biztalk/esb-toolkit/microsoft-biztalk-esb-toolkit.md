---
title: Microsoft BizTalk ESB 工具組 |Microsoft Docs
description: 簡介、 常見案例及 BizTalk Server 中的 ESB 工具組的元件
caps.latest.revision: 14
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ffaebc-7e33-4de8-8e94-109cd5d16ca0
ms.author: mandia
ms.openlocfilehash: f425c02e8f869952658f93185c78474e58df304b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023396"
---
# <a name="microsoft-biztalk-esb-toolkit"></a>Microsoft BizTalk ESB 工具組
![BizTalk ESB 工具組標誌](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")  
  
## <a name="summary"></a>摘要  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]支援鬆散偶合的傳訊架構。 BizTalk Server 包含的功能強大的發佈/訂閱機制傳訊的運作方式是建立的應用程式和填滿的訂用帳戶，為服務導向架構 (SOA) 應用程式提供高有效率且可調整的平台。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充功能的 BizTalk Server 提供各種新功能，著重於建置強固、 連結、 服務導向整合以路線為基礎的服務引動過程的輕量服務的應用程式組合、 動態端點解析和地圖，Web 服務和 WS-* 整合、 錯誤管理和報告，以及與第三方 SOA 控管解決方案整合。  
  
## <a name="overview"></a>概觀  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供架構指引、 模式和 BizTalk Server 和.NET Framework 元件，可簡化開發的企業服務匯流排 (ESB) 在 Microsoft 平台，並允許 Microsoft 客戶，將擴充的集合他們自己的傳訊與整合解決方案。  
  
## <a name="common-scenarios"></a>常見狀況  
 Enterprise Service Bus (ESB) 廣泛用於實作基礎結構的方式啟用服務導向架構 (SOA) 的內容中的詞彙。 不過，與部署 soa 都極為的實際經驗顯示，ESB 都只有一個，請設定完整服務導向基礎結構 (SOI) 的許多建置組塊。 ESB 有變形一詞在許多不同的方向，以及其定義取決於個別的 ESB 」 和 「 整合平台廠商的解譯和特定的 SOA 方案的需求。  
  
 Microsoft 已收集了許多成功的真實世界 SOI 實作從經驗為基礎，您可以想像的 ESB 傳統企業應用程式整合 (EAI)、 訊息導向中介軟體為基礎的架構模式的集合Web 服務、.NET 和 Java 互通性、 主機系統整合，以及與服務登錄與資產存放庫的互通性。  
  
 [圖 1] 顯示的 ESB 架構可以提供的內部連線類型的高階檢視。  
  
 ![ESB 概觀](../esb-toolkit/media/esboverview.gif "ESBOverview")  
  
 **圖 1**  
  
 **連線的高階範例提供的企業服務匯流排架構**  
  
## <a name="audience-requirements"></a>必備條件  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]適用於開發人員建立 Microsoft BizTalk Server 解決方案或使用其他解決方案[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件。 若要充分利用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，開發人員應該具備的知識和體驗使用下列工作：  

- [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

- [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]
  
- Microsoft.NET 開發技術，包括開發 ASP.NET Web 服務和.NET Framework 元件  
  
## <a name="design-goals"></a>設計目標  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]一系列的支援和實作鬆散偶合的傳訊環境，可讓您更輕鬆地建置以訊息為基礎的企業應用程式元件間的互通性所組成。 服務和元件自然可分成下列七個類別：  
  
- **Web 服務**： 這些公開內部服務，例如路線處理例外狀況管理端點解析和地圖、 BizTalk Server 作業和訊息轉換。  
  
- **路線服務**： 這些包括協調流程和傳訊為基礎的服務，來執行以路線為基礎的路由[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 您可以建立自訂路線為基礎的路由服務。  
  
- **路線入口。** 這些接收外部的訊息、 附加適當的路線的每則訊息，以及執行路線處理;他們使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和動態端點解析和中繼資料的配接器提供者架構。  
  
- **入口**： 這些接收外部訊息格式和傳輸，例如 HTTP、 JMS、 WMQ、 FTP、 一般檔案和 XML 的範圍內。 它們是典型的 BizTalk Server 接收位置，或者使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 的管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和動態端點解析和中繼資料的配接器提供者架構。  
  
- **出口**： 這些實作使用的格式和傳輸，例如 SOAP、 WCF、 JMS、 WMQ、 FTP、 HTTP、 一般檔案、 XML 或任何其他自訂格式的訊息傳遞的傳送埠。 它們是一般 BizTalk Server 動態傳送埠，會直接繫結至 Messagebox，並選擇性地使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 的管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和動態的端點解析的配接器提供者架構與中繼資料。  
  
- **例外狀況管理架構**： 這包括例外狀況的例外狀況管理 API，Web 服務和元件可強化，處理時，將 ESB 管理入口網站中的例外狀況詳細資料。  
  
- **ESB 管理入口網站**： 這會提供登錄佈建、 例外狀況中繼、 警示通知，以及分析。  
  
  許多這些元件和服務所實作的功能都必須依賴[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，例如協調流程、 轉換和商務規則引擎和 Messagebox 資料庫。 圖 2 顯示一個類別目錄; 的圖解檢視元件和服務通常發生在每個類別中;所使用之核心 BizTalk Server 系統元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
  ![ESB 架構](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
  **圖 2**  
  
  **架構和元件 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>BizTalk ESB Toolkit 的運作方式  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]接受輸入的訊息，並可能 （但不是一定） 運作，執行程序，例如轉換、 傳遞或任何其他自訂定義程序。 若要指定作業所需，核心處理元件所需的訊息包含相關聯的指示或定義要套用的程序的中繼資料和工作，以在訊息內容執行。  
  
 這種方法可提供服務; 之間的鬆散結合這表示，ESB 不需要事先知道特定的處理每個訊息。 它只有知道處理程序，以及如何套用每個處理序的可能範圍。 各種選項來指定可用的處理序和處理程序與在訊息中的指示之間的對應提供彈性的機制，來設定和調整行為，而不需要變更程式碼和重新部署元件。  
  
## <a name="in-this-section"></a>本節內容

- [安裝和設定 Microsoft BizTalk ESB 工具組](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)

- [BizTalk ESB 工具組簡介](introduction-to-the-biztalk-esb-toolkit.md)

- [開始使用和了解 BizTalk ESB 工具組](getting-started-with-the-biztalk-esb-toolkit.md)

- [主要案例及開發工作](key-scenarios-and-development-tasks.md)

- [建立使用路線設計工具的路線](creating-itineraries-using-itinerary-designer.md)

- [BizTalk ESB 工具組範例應用程式](biztalk-esb-toolkit-sample-applications.md)

- [修改和擴充 BizTalk ESB 工具組](modifying-and-extending-the-biztalk-esb-toolkit.md)

- [使用 BizTalk ESB 工具組管理](administration-with-the-biztalk-esb-toolkit.md)

- [SOA 控管整合](soa-governance-integration.md)

- [針對 BizTalk ESB 工具組進行疑難排解](troubleshooting-the-biztalk-esb-toolkit.md)
  
## <a name="related-topics"></a>相關主題  
  
-   [BizTalk 服務導向解決方案](../core/service-oriented-solution.md)

- [使用 BizTalk Server 中的 Web 服務](../core/using-web-services.md)  