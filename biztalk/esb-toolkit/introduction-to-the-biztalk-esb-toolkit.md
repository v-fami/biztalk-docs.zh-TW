---
title: "BizTalk ESB 工具組簡介 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ESBToolkitV2.introduction
ms.assetid: 98a957b8-5855-4872-b7e7-58a2e1d6b2b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9763e55c44fc3ea45ab93127ffae8c9c742f0dc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="introduction-to-the-biztalk-esb-toolkit"></a>BizTalk ESB 工具組簡介
說明的架構和 Microsoft 內容[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 文件也會示範如何套用開發企業應用程式，請啟用彈性且更安全的企業服務匯流排 (ESB) 架構模式和可重複使用的服務，以及快速組織現有服務的新端對端商務程序。  
  
## <a name="what-is-an-enterprise-service-bus"></a>什麼是企業服務匯流排？  
 企業服務匯流排廣泛使用的實作基礎結構啟用 Service-Oriented 架構 (SOA) 的內容中的詞彙。 不過，SOA 方案部署的實際經驗已經示範 ESB 是建置完整 Service-Oriented 基礎結構 (SOI) 所需的許多元件的其中之一。 中的數字的方向發展"ESB 」 一詞，其定義不同的個別 ESB 和整合平台供應商的解譯與特定的 SOA 開發案的需求。  
  
 根據 Microsoft 已收集了與許多成功的真實世界 SOI 實作的經驗，Microsoft 會視為是集合的架構模式基礎上傳統企業應用程式整合 (EAI)，企業服務匯流排訊息導向中介軟體、 Web 服務、.NET 和 Java 的互通性、 主機系統整合，以及與服務和資產的儲存機制的互通性。 圖 1 說明企業服務匯流排的架構。  
  
 ![ESB 概觀](../esb-toolkit/media/esboverview.gif "ESBOverview")  
  
 **圖 1**  
  
 **企業服務匯流排架構所提供的連線的高層級表示法**  

\<！---舊文字與舊的連結
## <a name="the-industry-view-of-esb"></a>ESB [產業] 檢視  
 有許多相關的資訊來源 ESB 設計、 架構、 基礎結構，以及實作從業界供應商、 系統整合者和獨立的來源。  
-->
\<!---    
 IBM 定義 ESB 做為系統，"...enables 商務，讓使用完整、 具彈性，且一致的方法到整合，同時還可降低要整合的應用程式的複雜性。 由於的複雜且不同的商務需求，ESB 統一訊息導向 evolutional 進展，導向事件和服務導向整合的應用程式和服務的方法。 」 IBM 說明優點為"...greater 重複使用的分隔應用程式 logics 和整合工作，以便您可以減少數目、 大小和整合介面的複雜性 IT 資產"以及"..搭配最低限度的.add 或變更服務中斷現有的 IT 環境。降低成本和商務的變更所涉及的風險和新的機會發生 」。 如需詳細資訊，請參閱[WebSphere 軟體](http://go.microsoft.com/fwlink/p/?LinkId=185958)([http://go.microsoft.com/fwlink/p/?LinkId=185958](http://go.microsoft.com/fwlink/p/?LinkId=185958)) IBM 網站上。  
-->
\<！---舊文字的舊 Sonic 解決方案提供 ESB，全面探討討論的主要層面和它的連結和商業優勢。 這些主題說明 ESB 的需求: 「 若要將舊的和新的整合，服務導向架構 (SOA) 需要可以連接任何 IT 資源，無論基礎結構內技術或部署的任一處。" 如需詳細資訊，請參閱[企業服務匯流排 (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185959)([http://go.microsoft.com/fwlink/p/?LinkId=185959](http://go.microsoft.com/fwlink/p/?LinkId=185959)) Sonic 解決方案網站上。  
-->
\<！---與舊連結 TIBCO 軟體的舊文字定義為 ESB"...a 標準為基礎的通訊層中的服務導向架構 (SOA)，可讓服務可用於跨多個通訊協定 [] 簡化服務部署和管理，並將升級服務在異質環境中的重複使用。 」 這些建議，為了提供這些功能，Esb"...support 都屬開放式標準與專利技術，包括 Web 服務和 UDDI 為基礎的登錄，才能探索及發佈服務、 Java 訊息服務 (JMS) 和其他廣泛的已部署訊息通訊協定、 標準式 (XML) 轉換和基本的訊息路由。 」 如需詳細資訊，請參閱[企業服務匯流排 (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185960)([http://go.microsoft.com/fwlink/?LinkId=185960](http://go.microsoft.com/fwlink/p/?LinkId=185960)) TIBCO 網站上。  
-->
\<！---作者為 David Chappell 陳述，舊的連結，在他的書籍，企業服務匯流排，描述中的舊文字 」 而不是比傳統的企業應用程式整合產品的中樞和支點架構符合，ESB 提供高分散式的方式整合。 」 他將新增 「 … with 獨特功能，可以讓個別的部門或業務單位來建置出其整合中的專案、 累加且容易吸收的區塊，同時仍然能夠連接在一起維護自己的本機控制項和自主性，每個整合專案到較大、 更通用整合網狀架構或方格。 」 如需詳細資訊，請參閱 David Chappell 所著的企業服務匯流排：  
-->
\<！---舊文字與舊的連結
-   David Chappell 企業服務匯流排。 O'Reilly Media，Inc.Sebastopol、 CA:2004.  
-->

  
## <a name="the-biztalk-esb-toolkit"></a>BizTalk ESB 工具組
 本文件中的，整個導入了架構設計人員和開發人員 ESB 架構概念因為收件者所[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，並說明 ESB 元件，透過一組普遍接受的 ESB 使用案例的功能。  
  
 本節介紹[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，並包含下列主題：  
  
-   [BizTalk ESB 工具組的概觀](../esb-toolkit/overview-of-the-biztalk-esb-toolkit.md)  
  
-   [BizTalk ESB 工具組的內容](../esb-toolkit/contents-of-the-biztalk-esb-toolkit.md)  
  
 這份文件也包含下列主題章節：  
  
-   [開始使用 BizTalk ESB 工具組](../esb-toolkit/getting-started-with-the-biztalk-esb-toolkit.md)  
  
-   [重要案例及開發工作](../esb-toolkit/key-scenarios-and-development-tasks.md)  
  
-   [建立行程使用路線設計工具](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)  
  
-   [BizTalk ESB 工具組範例應用程式](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)  
  
-   [修改和擴充 BizTalk ESB 工具組](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)  
  
-   [使用 BizTalk ESB 工具組系統管理](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)  
  
-   [SOA 控管整合](../esb-toolkit/soa-governance-integration.md)  
  
-   [疑難排解](../esb-toolkit/troubleshooting-the-biztalk-esb-toolkit.md)