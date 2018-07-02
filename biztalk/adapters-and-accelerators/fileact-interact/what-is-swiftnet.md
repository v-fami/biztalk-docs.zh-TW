---
title: 何謂 SWIFTNet？ | Microsoft Docs
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
ms.openlocfilehash: 02f09a1ccc9b67b084a6f683125bacaec5eae77c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989335"
---
# <a name="what-is-swiftnet"></a>何謂 SWIFTNet？
SWIFTNet 是一般用途、 財務產業的業界標準方案提供的全球財務社群所參與的所有機構連接的應用程式的應用程式無關的單一視窗介面。 實際的存取控制是商務原則決策的每個服務系統管理員 」 中，而不是由基礎結構技術的限制。  
  
 SWIFTNet 提供以確保商務持續性和災害復原的跨機構界限的任務關鍵性財務應用程式的基礎結構的基礎。 SWIFTNet 被設計來滿足任務關鍵性的金融軟體解決方案的互通性機構社群需求。  
  
 相互連接的商務應用程式 SWIFTNet 提供下列功能：  
  
-   基礎結構的可靠性保證  
  
-   可用性  
  
-   角色型和非角色型存取控制  
  
-   對應和訊息驗證  
  
-   訊息完整性  
  
-   機密性  
  
-   不可否認性支援  
  
-   訊息驗證  
  
-   儲存與轉送  

使用 SWIFTNet **SWIFTNet 連結**(SNL) 為 SWIFTNet 服務，並使用應用程式開發介面**SWIFTAlliance 閘道**連線能力和可用性。 深入的了解本主題中的這些資源。

## <a name="swiftnet-link-overview"></a>SWIFTNet 連結概觀

商務軟體應用程式會使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) 來存取和使用 SWIFTNet 服務。 SNL 是 SWIFTNet 必要的網路介面。 SWIFTNet 需要 SNL 所有的外部介面。 SNL 也包含支援傳訊、 安全性和服務管理功能的背景處理序。 SNL 會併入 SWIFTAlliance WebStation 和 SWIFTAlliance 閘道 (SAG)。  
  
 SNL 會建立商務應用程式元件之間的鬆散偶合的用戶端/伺服器關聯性。 而不是直接叫用方法或函式，就訊息導向的互動： 用戶端和伺服器之間傳遞的結構化的訊息。 通常為 SWIFTNet 服務所設計的商務應用程式是由用戶端和伺服器的一組所組成。 在相同的用戶端或相同的伺服器處理序可以啟動多次。 請注意，您無法預測的同一個應用程式的內送訊息要求的執行個體將會傳遞至哪個處理程序。 用戶端處理序內的多個執行緒可以叫用的 SwCall API 函式。 伺服器處理序可以有多個執行緒也;不過，只有一個執行緒可以叫用 SwCallback。 用戶端和伺服器處理序不能合併在相同的程序中。  
  
 SNL 提供一組專為高可用性和高輸送量的環境而設計的傳輸層級功能。 這些功能包括：  
  
- 負載平衡  
  
- 位置透明度和路由、 防護應用程式元件，從基礎傳輸技術  
  
- 傳輸層級驗證和機密性，SNL 內封裝，並以透明的方式提供給應用程式  
  
- 商業應用程式軟體可能會建立端對端安全性 （使用者應用程式至使用者的應用程式） 的安全性函式時所需。  
  
  在使用 c + + 或 Java 來源程式碼層級進行程式設計，就有只有兩個函數： SwCall 和 SwCallback。 SwCall 是存取伺服器的應用程式透過 SWIFTNet 用戶端應用程式。 SwCallback 供伺服器應用程式中，以回應透過 SWIFTNet 用戶端。  
  
  SwCall 和 SwCallback 函式會存取 SWIFTNet 的功能，將結構化的 XML 訊息 SWIFTNet 來回傳遞。 在執行階段 SNL 包含這兩種軟體程式庫，其中的程式碼執行相同的位址空間，做為商務應用程式用戶端或伺服器處理序內 — 和獨立的處理序 （精靈或服務），此程式在執行自己的位址空間。 軟體程式庫是可透過 SNL Api 存取。  

## <a name="swiftalliance-gateway-overview"></a>SWIFTAlliance 閘道概觀
  
SWIFTAlliance 閘道 (SAG) 是針對 SWIFTNet 介面產品。 它會合併 SWIFTNet 連結的所有功能。 此外，還會提供數個不同的連線能力和可用性功能，對於 SWIFTNet 使用者，提供解決方案以各種不同的系統整合的問題。  
  
 SAG 支援數個不同的作業模式。 其中一種嚴格的 SWIFTNet 連結模式，是特別針對至 SWIFT 的 FileAct 和 InterAct 配接器。 在嚴格的 SWIFTNet 連結模式中，SAG 會呈現的功能上相當於 SWIFTNet 連結介面在這些主題中描述的訊息介面。  
  
 SAG 做為訊息集訊器。 它會從各種其他應用程式接收訊息，並通過 SWIFTNet。 它會接收這些訊息透過主機介面卡，包括可讓商務應用程式在各種不同類型的運算平台上執行，將訊息透過 SWIFTNet WebSphere MQ 主機介面卡。  
 
 ## <a name="next-reading"></a>閱讀下一步
 
 [何謂 FileAct 配接器？](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)  
 [何謂 InterAct 配接器？](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)  
 [BizTalk FileAct 和 InterAct 配接器端對端教學課程](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)
 
 ## <a name="see-also"></a>另請參閱
 [了解 FileAct 和 InterAct 配接器架構](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)