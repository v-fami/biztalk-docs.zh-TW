---
title: BizTalk ESB toolkit 架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41674f5-5ea4-4a8f-a270-b67fd6854028
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6a85e8e98e7ea2874935656553b18abac7ca88a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007847"
---
# <a name="architecture-of-the-biztalk-esb-toolkit"></a>BizTalk ESB Toolkit 的架構
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含一系列的支援和實作鬆散偶合的傳訊環境，可讓您更輕鬆地建立以訊息為基礎的企業應用程式元件間的互通性。 服務和元件自然可分成下列七個類別：  
  
-   **Web 服務。** 這些公開內部服務，例如行程處理例外狀況管理、 端點和地圖、 BizTalk Server 作業、 通用描述、 探索與整合 (UDDI) 相互操作及轉換的訊息內容的解析度.  
  
-   **路線服務。** 其中包括執行轉換和路由訊息的協調流程和傳訊為主的服務。 您可以建立自訂的服務參與行程處理中。 其中包括執行轉換和路由訊息的協調流程和傳訊為主的服務。 您可以建立自訂的服務參與行程處理中。  
  
-   **路線上-坡道提升。** 這些接收外部的訊息、 附加適當的路線，每個訊息，以及執行路線處理;他們使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，來動態解析的端點和中繼資料。  
  
-   **在-坡道提升。** 不同於路線上-坡道提升，這些會收到外部訊息格式和傳輸，例如 HTTP、 Java 訊息服務 (JMS)、 IBM WebSphere MQ (WMQ)、 檔案傳輸通訊協定 (FTP)、 一般檔案和 XML 的範圍中。 它們是典型的 BizTalk Server 接收位置，或者使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，來動態解析的端點和中繼資料。  
  
-   **關閉-坡道提升。** 這些實作的傳送埠傳送訊息使用的格式和傳輸，例如 WCF、 JMS、 WMQ、 FTP、 HTTP、 一般檔案、 XML 或任何其他自訂格式。 它們是動態傳送埠會直接繫結至 Messagebox，並選擇性地使用一般 BizTalk Server [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop 管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和動態的端點解析的配接器提供者架構和中繼資料。  
  
-   **例外狀況管理架構。** 這包括例外狀況的 Web 服務、 例外狀況管理 API 和擴充，程序，並傳遞例外狀況詳細資料 ESB 管理入口網站的元件。  
  
-   **ESB 管理入口網站。** 此範例應用程式提供登錄佈建、 例外狀況中繼、 警示的通知和分析。  
  
 許多這些元件和服務依賴 BizTalk Server 所實作的協調流程、 轉換和商務規則引擎等 Messagebox 資料庫的功能。 圖 1 顯示的圖解檢視的類別、 元件和服務通常發生在每個類別，並使用核心 BizTalk Server 系統元件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
 ![ESB 架構](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
 **圖 1**  
  
 **架構和元件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>BizTalk ESB 工具組的運作方式  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]接受輸入的訊息，並可能 （但並非一定），運作方式，透過執行處理序，例如轉換，路由，或任何其他自訂程序。 若要指定作業所需，核心處理元件需要有路由的受控滑動包含相關聯的指令或定義要套用的程序的中繼資料和要與訊息內容中執行之工作的每個訊息。 這些路由順延稱為旅和可以自動解決、 擷取從中央儲存機制，與上遞增收到時附加至訊息。  
  
 此路由的名單方法提供服務，這表示 ESB 不需要事先了解之特定處理的每個訊息之間的鬆散偶合。 它只需要知道處理程序的可能範圍以及套用每個處理序的方式。 指定可用的處理序和處理程序與在訊息中的指示之間的對應之選項的各種提供彈性的機制，來設定和調整行為，而不需要變更程式碼和重新部署元件。  
  
## <a name="design-patterns"></a>設計模式  
 ESB 使用，其中處理程序儲放訊息在 Messagebox 資料庫，並 「 訂閱者 」 在訊息中，處理指示為基礎的架構，有效地實作的狀態機器設計模式。 此外，ESB 實作，而且會以服務為導向的方式，包括外部應用程式可以透過一組核心 Web 服務公開其核心功能。  
  
 這鬆散耦合方法設計 BizTalk Server 和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]-應用程式它會產生彈性極高的解決方案，而且已經成為業界接受的最佳作法。