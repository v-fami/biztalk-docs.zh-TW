---
title: SWIFTNet 是什麼？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b074385-352c-40f4-b73e-1891c627aa4e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1668c1f568a6cfb853957b3598b41f1cbdf6e33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225310"
---
# <a name="what-is-swiftnet"></a>SWIFTNet 是什麼？
做為一般用途，財務產業的業界標準方案 SWIFTNet 提供通用的財務社群的參與的所有機構所有連接的應用程式的應用程式無關的單一視窗介面。 實際的存取控制是商務原則決策的每個服務系統管理員，而不是由基礎結構的技術限制。  
  
 SWIFTNet 提供基礎以確保跨機構界限的關鍵任務財務應用程式的基礎結構的業務續航力和災難復原。 SWIFTNet 被為了滿足機構社群需求的互通性的關鍵任務的財務軟體解決方案。  
  
 互連的商務應用程式及 SWIFTNet 提供下列功能：  
  
-   Assurance 的基礎結構的可靠性  
  
-   可用性  
  
-   角色型和非角色型存取控制  
  
-   對應和訊息驗證  
  
-   訊息完整性  
  
-   機密性  
  
-   不可否認性支援  
  
-   訊息驗證  
  
-   儲存與轉送  

SWIFTNet 使用**SWIFTNet 連結**(SNL) 做為應用程式開發介面，用於 SWIFTNet 服務，並會使用**SWIFTAlliance 閘道**連線及可用性。 深入了解本主題中的這些資源。

## <a name="swiftnet-link-overview"></a>SWIFTNet 連結概觀

商務軟體應用程式使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) 來存取及使用 SWIFTNet 服務。 SNL 是 SWIFTNet 必要的網路介面。 SWIFTNet SNL 需要所有的外部介面。 SNL 也包含支援傳訊、 安全性和服務管理功能的背景處理序。 SNL 會併入 SWIFTAlliance WebStation 和 SWIFTAlliance 閘道 (SAG) 而定。  
  
 SNL 建立鬆散偶合的用戶端/伺服器之間的關聯性的商業應用程式元件。 而不是直接叫用方法或函式，就訊息導向的互動： 用戶端和伺服器之間傳送結構化的訊息。 通常為 SWIFTNet 服務所設計的商務應用程式是由用戶端和伺服器的一組所組成。 相同的用戶端相同的伺服器處理序可以啟動或多次。 請注意，您無法預測相同的應用程式的內送訊息要求的執行個體將會傳遞至哪一個處理序。 用戶端處理序內的多個執行緒可以叫用 SwCall API 函式。 伺服器處理序可以有多個執行緒。不過，只有一個執行緒，可以叫用 SwCallback。 用戶端和伺服器處理序不能合併在相同的程序。  
  
 SNL 提供一組專為高可用性和高輸送量環境所設計的傳輸層級功能。 這些功能包括：  
  
-   負載平衡  
  
-   位置透明度和路由、 防護從基礎傳輸技術的應用程式元件  
  
-   傳輸層級驗證和機密性，封裝在 SNL 內並無障礙地提供給應用程式  
  
-   安全性函數商業應用程式軟體可能會建立端對端安全性 （使用者應用程式使用者應用程式），必要時。  
  
 在原始程式碼層使用 c + + 或 Java 程式設計，方面有只有兩個函數： SwCall 和 SwCallback。 SwCall 用戶端應用程式用於透過 SWIFTNet 存取伺服器應用程式。 SwCallback 伺服器應用程式用於透過 SWIFTNet 用戶端的回應。  
  
 SwCall 和 SwCallback 函式藉由傳遞結構化的 XML 訊息與從 SWIFTNet 存取 SWIFTNet 的功能。 在執行階段 SNL 包含這兩種軟體程式庫 — 中相同的位址空間，做為商務應用程式用戶端或伺服器處理序執行的程式碼，以及獨立的處理序 （精靈或服務），在執行自己的位址空間。 軟體程式庫是可透過 SNL Api 存取。  

## <a name="swiftalliance-gateway-overview"></a>SWIFTAlliance 閘道概觀
  
SWIFTAlliance 閘道 (SAG) 是針對 SWIFTNet 介面產品。 它會合併 SWIFTNet 連結的所有功能。 此外，它會提供數個不同的連接和可用性功能，針對 SWIFTNet 使用者，提供各種不同的系統的解決方案整合問題。  
  
 SAG 支援數個不同的作業模式。 其中一種嚴格的 SWIFTNet 連結模式，是特別 for SWIFT FileAct 和 InterAct 配接器。 在嚴格 SWIFTNet 連結模式中，SAG 會呈現其作用相當於 SWIFTNet 連結介面描述所有這些主題的傳訊介面。  
  
 SAG 可做為訊息集訊器。 它會從各種其他應用程式接收訊息並通過 SWIFTNet。 它會接收這些訊息透過主機介面卡，包括可讓商務應用程式執行各種不同類型的運算平台上，將訊息透過 SWIFTNet WebSphere MQ 主機介面卡。  
 
 ## <a name="next-reading"></a>下一步讀取
 
 [FileAct 配接器為何？](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)  
 [什麼是互動配接器？](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)  
 [BizTalk FileAct 和互動配接器的端對端教學課程](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)
 
 ## <a name="see-also"></a>另請參閱
 [了解 FileAct 和互動的配接器架構](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)