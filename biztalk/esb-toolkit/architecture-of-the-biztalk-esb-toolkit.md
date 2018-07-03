---
title: BizTalk ESB 工具組的架構 |Microsoft Docs
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
ms.openlocfilehash: a701b2c0170b8687e48ff61c369ac25ef41ab6bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999383"
---
# <a name="architecture-of-the-biztalk-esb-toolkit"></a>BizTalk ESB 工具組的架構
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]一系列的支援和實作鬆散偶合的傳訊環境，可讓您更輕鬆地建置以訊息為基礎的企業應用程式元件間的互通性所組成。 服務和元件自然可分成下列七個類別：  
  
- **Web 服務。** 這些會公開內部服務，例如路線處理例外狀況管理端點解析和地圖、 BizTalk Server 作業、 通用描述、 探索與整合 (UDDI) 交互操作和轉換的訊息內容.  
  
- **路線的服務。** 這些包括協調流程和傳訊為基礎的服務，來執行轉換和訊息路由。 您可以建立自訂的服務參與路線處理中。 這些包括協調流程和傳訊為基礎的服務，來執行轉換和訊息路由。 您可以建立自訂的服務參與路線處理中。  
  
- **路線入口。** 這些接收外部的訊息、 附加適當的路線的每則訊息，以及執行路線處理;他們使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和動態端點解析和中繼資料的配接器提供者架構。  
  
- **入口。** 不同於路線入口，這些會收到外部訊息格式和傳輸，例如 HTTP、 Java 訊息服務 (JMS)、 IBM WebSphere MQ (WMQ)、 檔案傳輸通訊協定 (FTP)、 一般檔案和 XML 的範圍內。 它們是典型的 BizTalk Server 接收位置，或者使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 的管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和動態端點解析和中繼資料的配接器提供者架構。  
  
- **出口。** 這些實作的傳送埠使用的格式和傳輸，例如 WCF、 JMS、 WMQ、 FTP、 HTTP、 一般檔案、 XML 或任何其他自訂格式的訊息傳遞。 它們是典型的 BizTalk Server 會直接繫結的動態傳送埠到訊息方塊，並選擇性地使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 的管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和動態的端點解析的配接器提供者架構和中繼資料。  
  
- **例外狀況管理架構。** 這包括例外狀況 Web 服務、 例外狀況管理 API，以及豐富、 處理和傳遞給 ESB 管理入口網站的 例外狀況詳細資料的元件。  
  
- **ESB 管理入口網站。** 此範例應用程式提供登錄佈建、 例外狀況中繼、 警示通知，以及分析。  
  
  許多這些元件和服務會依賴實作 BizTalk Server 協調流程、 轉換和商務規則引擎和 Messagebox 資料庫等功能。 [圖 1] 顯示的圖解檢視的類別、 元件和服務通常發生在每個類別，以及所使用核心 BizTalk Server 系統元件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
  ![ESB 架構](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
  **圖 1**  
  
  **架構和元件 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>BizTalk ESB Toolkit 的運作方式  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]接受輸入的訊息，並可能 （但不是一定） 運作，藉由執行程序，例如轉換，路由，或任何其他自訂處理程序。 若要指定作業所需，核心處理元件需要有傳閱名單，其中包含相關聯的指示或定義要套用的程序的中繼資料和要與訊息內容中執行之工作的每個訊息。 這些傳閱名單稱為路線和可以自動解決、 擷取從中央儲存機制，與匝道收到時附加到訊息。  
  
 此路由的傳閱名單方法提供服務，這表示，ESB 不需要事先知道特定的處理每個訊息之間的鬆散結合。 它只有知道處理程序的可能範圍以及套用每個處理序的方式。 各種選項來指定可用的處理序和處理程序與在訊息中的指示之間的對應提供彈性的機制，來設定和調整行為，而不需要變更程式碼和重新部署元件。  
  
## <a name="design-patterns"></a>設計模式  
 使用 ESB，其中程序儲放在 Messagebox 資料庫的訊息，而訂閱者收取訊息中的處理指示為基礎的架構，有效地實作狀態機器設計模式。 此外，ESB 會實作並公開其核心功能，以服務導向的方式，包括外部應用程式可以透過一組核心 Web 服務。  
  
 此鬆散結合的方法來設計 BizTalk Server 和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]-應用程式會產生高彈性的解決方案，而且已經成為業界接受的最佳作法。