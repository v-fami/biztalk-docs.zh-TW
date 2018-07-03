---
title: 了解服務導向解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, background information
- service solutions, about service solutions
- service solution tutorial, about service solution tutorial
- Service Oriented Architecture (SOA)
ms.assetid: 56a2ad90-74bb-489a-ab1d-900f3bea3d64
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d3595d664e53a5abc20a69d990391e3c273ee3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010341"
---
# <a name="understanding-the-service-oriented-solution"></a>了解服務導向解決方案
服務導向解決方案提供以服務方式設計的信用結餘報告應用程式。 接著應用程式會使用三個以服務方式公開的後端應用程式，來取得信用結餘所需的資訊。  
  
 「服務導向架構」(SOA) 是一種與建立分散系統部分重疊的方式。 服務導向方法具有一些特色：  
  
- 鬆散耦合。 應用程式的商務邏輯與處理服務的邏輯是分開的。  
  
- 可搜尋的。 應該要有一個應用程式用以尋找服務的機制。  
  
- 合約。 服務的介面會在使用者與服務之間實作合約。  
  
  雖然文獻上通常會將服務導向方法視為與 Web 服務相同，但是它們不全然相同。 Web 服務為實作服務導向解決方案提供一個有效的方法，但您仍可使用其他技術 (例如 .NET 遠端) 來建立服務。  
  
  服務導向架構的詳細資訊，請參閱 < 服務介面 >，網址[ http://go.microsoft.com/fwlink/?LinkId=46185 ](http://go.microsoft.com/fwlink/?LinkId=46185)以及 < Service-Oriented Integration 在[ http://go.microsoft.com/fwlink/?LinkId=46186 ](http://go.microsoft.com/fwlink/?LinkId=46186)。  
  
## <a name="reader-guidance"></a>使用指南  
 此解決方案的文件假設您已熟悉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 它也假設您瞭解企業應用程式整合與 Web 服務的基本概念。  
  
 此外，若要閱讀和依照開發人員文件，您應該了解如何使用建置應用程式[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]並執行下列工作： 建立專案、 設定參考，以及偵錯和測試 BizTalk解決方案。  
  
## <a name="credit-card-reporting-at-woodgrove-bank"></a>Woodgrove 銀行的信用卡報告  
 服務導向架構解決方案是 Woodgrove 銀行的信用卡結餘報告服務。 雖然此銀行是虛構的，不過此實例是根據實際已部署的客戶應用程式所設計。  
  
 在此實例中，信用卡結餘的要求有兩個來源：  
  
- 互動語音回應 (IVR) 應用程式。  
  
- 像網頁或自訂用戶端應用程式等互動式用戶端。  
  
  解決方案會透過 MQSeries 接收 IVR 應用程式的要求。 它會使用 HTTP 與 SOAP，透過 Web 服務來處理互動式用戶端的要求。  
  
  新的服務導向架構應用程式通常需要與使用較舊技術的舊應用程式一起運作，以及與使用 Web 服務的網站等現有的應用程式一起運作。 此實例仿造此真實世界需求：IVR 應用程式代表舊的應用程式，而客戶服務用戶端應用程式則是現有的應用程式。  
  
  Woodgrove 銀行的應用程式會使用來自三個舊後端系統的資料來回應要求：  
  
- 提供整個信用限制的應用程式。 這是主機電腦上的 SAP 系統。  
  
- 擱置交易系統，會報告根據帳戶所擱置的交易總量。 此系統是主機或 AS/400 系統。 解決方案會使用 Web 服務和 Microsoft Host Integration Server (HIS)，與主機或 AS/400 系統通訊。  
  
- 付款交易系統，會提供對系統所做的最後付款。 可使用 MQSeries，抵達付款追蹤系統。  
  
  從舊系統收集和編譯資訊之後，解決方案會將回應傳送回原始應用程式，因此會傳回給客戶。  
  
## <a name="business-requirements"></a>商務需求  
 因為信用報告應用程式會即時回應客戶要求，所以它的延遲必須很短才能快速處理要求。 此外，它也必須處理很高的同時要求數。 解決方案會使用機密資訊與公用介面，因此安全性是一項重要議題。 最後，服務必須是可靠的。  
  
 如需解決方案如何符合這些需求的資訊，請參閱[開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)。  
  
## <a name="performance-characteristics"></a>效能特色  
 為了符合商業需求，實例具有下列效能特色：  
  
-   每秒 40 個內送要求的可維持輸送量。  
  
-   每秒 100 個內送要求的尖峰輸送量。  
  
-   在 1000 毫秒之下，可服務 (BizTalk Server 內外) 90% 的要求。  
  
-   在 2000 毫秒之下，可服務 (BizTalk Server 內外) 95% 的要求。  
  
-   在 5000 毫秒之下，可服務 (BizTalk Server 內外) 100% 的要求。  
  
> [!NOTE]
>  這些時間不包括後端系統的延遲時間。  
  
## <a name="three-versions-of-the-solution"></a>解決方案的三個版本  
 解決方案有三個版本：  
  
- 虛設常式版本會以軟體虛設常式取代所有的後端系統。 虛設常式會模擬後端系統。 這個版本提供在單一電腦上部署和執行解決方案的快速方式。  
  
- 配接器版本會使用 BizTalk 配接器，連線至後端系統。 這個版本是某些人實作解決方案時可能會先考慮的方式。 不過，使用配接器將訊息傳送回後端系統，會在傳回回應時產生明顯的延遲。 雖然配接器本身的延遲時間很短，但是 BizTalk Server 的分散式架構需要配接器使用訊息方塊，與協調流程主控件執行個體進行通訊。 這將造成需往返資料庫，並影響延遲時間。  
  
- 內嵌版本會以直接與後端系統通訊的內嵌程式碼取代配接器。 解決方案的內嵌版本具有最低的延遲與最高的傳送量。  
  
  部署指南為建立和部署解決方案的所有三個版本提供指引，並在每個版本中提供一個方法，以便對擱置的交易系統模擬透過 HIS 的連線。 建置和部署解決方案的相關資訊，請參閱[部署服務導向解決方案](../core/deploying-the-service-oriented-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [服務導向解決方案](../core/service-oriented-solution.md)