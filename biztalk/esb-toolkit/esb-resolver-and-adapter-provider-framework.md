---
title: "ESB 解析器和配接器提供者架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c82c2247-1f0a-48bd-98c2-9c816f4d68d7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c23fa8aca6def654b594d8b4fccf5d584e12fed4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="esb-resolver-and-adapter-provider-framework"></a>ESB 解析器和配接器提供者架構
解析器和配接器提供者架構提供完整、 可插式架構以動態方式解決端點資訊和 BizTalk Server 對應型別。 它會使用可延伸的元件，可讓開發人員若要變更行為，以符合自己的需求，並擴充以支援替代的解決方式和路由方法的機制。  
  
 解析器和配接器提供者架構提供支援通用描述、 探索與整合 (UDDI)、 商務規則引擎 (BRE) 和 XML 路徑語言 (XPath)。 它也會讓開發人員介面 (**IResolveProvider**和**IAdapterProvider**) 以允許建立自訂的解析器和配接器元件。 以下是解析器和配接器提供者架構的三個主要元件：  
  
-   **解析程式。** 這些定義的結構描述中，連接字串，並透過實作**IResolveProvider** .NET Framework 組件中的介面。 這些會載入快取執行階段，並支援解決類型和連接字串的範圍。  
  
-   **配接器提供者。** 這些透過實作定義**IAdapterProvider** .NET Framework 組件中的介面。 這些會依其設定適當的 BizTalk Server 配接器上的解析程式所提供的端點資訊的 BizTalk Server 傳輸類型註冊。  
  
-   **路線的管線元件。** 這些剖析解決方法指示從連接字串或 ESB 行程 SOAP 標頭，並且會提供端點解析器和配接器提供者架構所使用的解析度或轉換執行功能。 元件可以動態設定 BizTalk Server 端點屬性，或執行解決方法指示從連接字串或 ESB 行程 SOAP 標頭為基礎的 BizTalk Server 對應 」 轉換。 這些元件是負責管理、 更新和跨處理序和服務界限保留的行程。 選擇性的解譯器元件所提供的訊息和實作的原生 BizTalk Server 剖析[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路由至多個端點，而不需要協調流程服務的功能。  
  
 如需動態解析和動態路由的詳細資訊，請參閱[使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)和[使用動態轉換](../esb-toolkit/using-dynamic-transformation.md)。 解決方式和配接器提供者架構的相關資訊，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。