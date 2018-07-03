---
title: WCF 配接器常見問題集： 一般概念 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbeac135-3ba8-4b0b-a8ca-4eb5eb3d3ca3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e250c57b6a0de73b1a7f62ab73515e9c04cb2d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992452"
---
# <a name="wcf-adapter-faq-general-conceptual"></a>WCF 配接器常見問題集： 一般概念
以下是一些常見問題一般和概念性關於 Windows® Communication Foundation (WCF) 配接器。  
  
## <a name="what-is-a-wcf-adapter"></a>何謂 WCF 配接器？  
 BizTalk 配接器是方式的 Microsoft® BizTalk® Server 會與外界通訊的重要部分。 WCF 配接器是一個元件，管理 BizTalk 應用程式與它需要傳送和接收訊息，WCF 結束點之間的通訊程序。 BizTalk server 中，WCF 配接器會公開為 WCF 繫結。 這表示任何可以使用 WCF 繫結的 WCF 應用程式可以直接通訊，WCF 配接器而不需要介入的 BizTalk Server。 不過，使用透過 BizTalk Server WCF 配接器提供許多 BizTalk Server 提供的應用程式基礎結構優點。 這些常見問題集的重點主要使用 WCF 配接器從 BizTalk Server 環境內。  
  
 WCF 配接器可讓 BizTalk Server 傳送和接收 WCF 訊息中使用的 WCF 繫結。 WCF 用戶端應用程式可以的傳送 WCF 訊息至 BizTalk 接收的位置，接收訊息的 WCF 接收配接器。 配接器會將 WCF 訊息，並將它轉換成 BizTalk 訊息。 轉換發生的方式，取決於使用 BizTalk Server 管理主控台來設定特定配接器組態設定。 配接器提交到內部的 BizTalk MessageBox 資料庫的 BizTalk 訊息。 同樣地，BizTalk 傳送埠會使用 WCF 配接器可以訂閱此訊息類型、 取得 BizTalk 訊息、 將它轉換成 WCF 訊息，以及 WCF 訊息傳送至使用其中一個支援的 WCF 通訊協定的 WCF 服務端點。  
  
 使用 WCF 配接器從 BizTalk Server 中的抽取 BizTalk WCF 應用程式解決方案，例如選擇與實作通訊協定、 安全性問題和交易式作業的隱藏的複雜性。  
  
## <a name="what-are-the-wcf-adapter-bindings"></a>WCF 配接器繫結有哪些？  
 WCF 繫結分為兩類：  
  
- **自訂繫結：** 增加繫結的彈性，特殊的自訂繫結存在。 這涵蓋的通訊情況需要偏離標準繫結。 Wcf-custom 和 Wcf-customisolated 配接器可讓開發廣泛的繫結自訂。 這是藉由使用現有的繫結項目 （BindingElement 類別） 組成和行為 （行為類別） 的應用程式。  
  
- **標準繫結：** Microsoft 的目標是要開發著重於常見的通訊案例的配接器。 使用標準繫結，則藉由隱藏許多詳細資料，通訊協定的簡化的開發人員體驗。 BizTalk Server 中的 WCF 配接器集反映出.NET Framework 4.0 WCF 程式庫中繫結的集合。 標準繫結是導入.NET WCF 程式庫，讓您更輕鬆地使用一般的繫結模式。 它們會涵蓋最常使用的通訊案例，包括：  
  
  -   Wcf-wshttp  
  
  -   WCF-BasicHttp  
  
  -   WCF-NetTcp  
  
  -   WCF NetMsmg  
  
  -   WCF-NetNamedPipe  
  
  BizTalk Server R2 隨附下列 WCF 配接器：  
  
1.  **Wcf-wshttp 配接器：** 提供 WS-* 標準支援透過 HTTP 傳輸。 WCF-WSHttp 配接器會實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是文字或 Message Transmission Optimization Mechanism (MTOM) 編碼。  
  
2.  **Wcf-basichttp 配接器：** 進行通訊與 ASMX 架構 Web 服務和用戶端和其他符合 WS-I-Basic Profile 1.1。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是文字編碼。  
  
3.  **Wcf-nettcp 配接器：** 提供 WS-* 標準支援透過 TCP 傳輸。 WCF-NetTcp 配接器會提供有效率的通訊並實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。 傳輸方式是 TCP，訊息編碼方式則是二進位編碼。  
  
4.  **Wcf-netmsmq 配接器：** 提供支援佇列利用 Message Queuing (也稱為 MSMQ) 做為傳輸並支援鬆散偶合的應用程式、 失敗隔離、 負載調節，以及中斷連線的作業。  
  
5.  **Wcf-netnamedpipe 配接器：** 提供安全的最佳化的機器上跨處理序通訊。 WCF-NetNamedPipe 配接器會針對傳輸安全性使用轉送安全性，針對訊息傳遞使用具名管線，並使用二進位訊息編碼。  
  
     剛剛提到的五個介面卡的每個對應至一個 1 對 1 關聯性中的 WCF 繫結。 結構的兩個自訂配接器，我們即將討論稍微 WCF 模型免於中斷，因為有確實兩個不同自訂配接器對應至單一 WCF CustomBinding。  
  
6.  **Wcf-custom 配接器：** 啟用 WCF 擴充性功能。 配接器可讓您選取和設定 WCF 繫結和行為資訊，接收位置或傳送埠，裝載於 BizTalk Server 處理序。  
  
7.  **Wcf-customisolated 配接器：** 透過 HTTP 傳輸啟用 WCF 擴充性功能。 配接器可讓您選取及設定 WCF 繫結和行為資訊在外掛式主控件的網際網路資訊服務 (IIS) 中執行的接收位置。  
  
## <a name="what-is-the-difference-between-the-wcf-xxx-adapter-and-the-wcf-xxx-binding"></a>WCF xxx 配接器和 WCF xxx 繫結之間的差異為何？  
 每個 WCF 配接器對應至其中一個內建的 WCF 繫結。 在較高的層級，，說 WCF xxx 配接器使用 WCF xxx 繫結時，會幾乎交替使用這些詞彙。 比方說，Wcf-basichttp 配接器使用 WCF BasicHttpBinding 類別。 WCF 繫結是 WCF 端點定義的一部分。 這被指中"ABC"的 WCF 端點，其中這些字母就能位址、 繫結和合約。  
  
 繫結是由繫結項目集合所組成。 每個項目描述端點如何與用戶端通訊的某些層面。 繫結必須包括：  
  
- 至少一個傳輸繫結項目。  
  
- 至少一個訊息編碼繫結項目 （根據預設，可以提供傳輸繫結項目）。  
  
- 任意數目的其他通訊協定繫結項目。  
  
  建立由此描述執行階段環境的程序可讓每個參與該環境的程式碼的繫結項目。 通常需要符合相同的繫結類型和被呼叫的 WCF 服務支援的配接器的用戶端。 在 WCF 層級中，組態檔中，或明確地執行程式碼，則可以宣告方式定義繫結。 WCF 配接器可促進使用特定 WCF 繫結的通訊，因此詞彙 「 配接器 」 和 「 繫結 」 通常會成為在其使用方式幾乎完全相同。  
  
## <a name="when-using-the-wcf-adapters-how-do-you-decide-which-wcf-binding-to-use"></a>當使用 WCF 配接器，您要如何決定要使用的 WCF 繫結？  
 您可以進行這項決策依據訊息模式、 外部條件約束和效能，請在該訂單。  
  
1.  **傳訊模式：** 通訊的模式是如何通訊發生時，根據訊息的流程。 比方說，訊息可能是單向 （要求） 或雙向 （要求-回應），它可能交易式，它可能會排入佇列，並依此類推。  
  
    -   已排入佇列，如果您要使用 Wcf-netmsmq 配接器，它支援單向已排入佇列的交易的通訊。  
  
    -   如果模式是雙向要求-回應和兩部電腦之間的流程，您會使用 HTTP （如果您不想要盡可能彈性地） 或 WCF NetTcp （如果您關心的效能）。  
  
    -   如果訊息會保留在單一電腦上，而且只是處理序之間的流程，您可以使用 Wcf-netnamedpipe 繫結。  
  
2.  **外部條件約束：** 可能有問題，以指定使用特定的繫結。 比方說，假設外部系統需要 SOAP Web 服務版本 1.2 與定址 1.0。 在此情況下，最好的繫結是 WSHttpBinding 使用 Wcf-wshttp 配接器。 所有可能性而言外部系統也會解決特定的安全性模式設定的需求。 如果外部系統所需的 Soap Web 服務 1.1 HTTP 繫結可使用 Wcf-basichttp 配接器。  
  
3.  **效能：** 進行呼叫，速度可能會在繫結您選擇使用您的應用程式中的決定因素：  
  
    -   如果 WCF 服務是在 BizTalk Server 的同一部電腦上，使用 Wcf-netnamedpipe 配接器是最佳的效能選擇。  
  
    -   區域網路上的 WCF 服務時，WCF NetTcp 得到最佳效能。  
  
    -   如果效能不是主要的考量，而呼叫會透過網際網路，其中一種 HTTP 配接器 （Wcf-wshttp 或 Wcf-basichttp） 是正確的配接器。  
  
         您使用的任何進階的 HTTP 功能 (Wcf-wshttp)，或只是基本的功能 (Wcf-basichttp) 會指定哪些 HTTP 架構的配接器要使用的最佳選擇。  
  
## <a name="when-do-you-use-one-of-the-two-custom-wcf-adapters"></a>何時您使用其中兩個自訂 WCF 配接器？  
 有兩個自訂 WCF 配接器隨附於 BizTalk Server。 原因有兩個自訂的配接器是因為 BizTalk Server 需要的裝載特定配接器類型必須是其註冊到系統的一部分。 雖然 WCF Framework 中只能有一個 CustomBinding 類型，但兩個自訂的配接器中有 BizTalk Server 來因應這項限制在預先存在的 BizTalk 配接器模型。 事實上，這些配接器其實是唯一的配接器需要因為它們可讓 WCF 通道堆疊組態的完整控制權。  
  
 自訂配接器的唯一缺點就是，它們也需要您要非常了解 WCF 組態和各種擴充性的技巧。  簡化的組態就是為什麼 Microsoft 會提供標準的 WCF 繫結中的配接器。 標準繫結是預先定義的以涵蓋大部分的常見使用案例，並讓傳送和接收訊息透過 BizTalk Server 越簡單越好。 只有在標準繫結無法完全精確地符合需求的傳送埠或接收位置時，才，就會發生通常使用其中一個這些自訂的配接器的需求。 例如，可能有的應用程式使用其訊息的專屬的壓縮配置。 若要支援此功能，自訂繫結項目必須可寫入。 使用其中兩個標準的自訂配接器可讓處理傳輸需求這個自訂繫結組態。 因此，自訂配接器可讓較高層級的控制該通訊處理程序，透過通道堆疊的繫結組態。  
  
 自訂和自訂外掛式配接器的主要差異是其中一個裝載，而且裝載只會影響 BizTalk server 接收端。 Wcf-customisolated 配接器會使用與唯一的接收位置，而不是與傳送埠。 詞彙 「 隔離 」 是指裝載在 BizTalk Server 的 BtsNtSvc.exe 程序之外的 BizTalk 片語。 因此，當傳輸裝載在標準的 BtsNtSvc.exe 處理序在網際網路資訊服務 (IIS) 使用 HTTP 傳輸之外時，會使用 Wcf-customisolated 配接器。 Wcf-custom 配接器可以搭配接收位置或傳送埠。 它是用來傳輸裝載在標準的 BtsNtSvc.exe 程序。  
  
## <a name="how-does-a-wcf-endpoint-relate-to-biztalk-server"></a>WCF 端點如何與 BizTalk server？  
 WCF 端點是由位址、 繫結和合約 (ABC) 所組成。 在 BizTalk Server，使用者會接收位置中指定的位址，或傳送埠。 繫結會決定使用者選擇的 WCF 配接器。 合約是程式設計人員導向，它會指定端點所公開的介面。  
  
 實際的端點傳送訊息的 WCF 接收位置的形式存在。  有多種方式來公開 （expose） 在 BizTalk Server 應用程式中的 WCF 端點：  
  
- 您可以使用 BizTalk WCF 服務發佈精靈發佈 BizTalk 協調流程做為 WCF 端點。  
  
- 您可以使用 BizTalk WCF 服務發佈精靈來建立接收位置中現有的 BizTalk 應用程式。  
  
- 您可以在程式碼中設定接收位置的繫結和位址，手動建立的 WCF 端點。  在此情況下接收位置就是實際上不具類型。  它具有純粹根據 WCF 訊息的類別，使其至 MessageBox 資料庫接收訊息的任何格式來指定的合約。  
  
  每個 BizTalk 接收位置使用 WCF 配接器會公開為 WCF 用戶端能夠在其中進行呼叫的 WCF 端點。  接收位置在內部使用它自己的 WCF ServiceHost，以便啟用或停用各自不同的接收位置。 服務端點的存留期存在，只要接收位置已啟用。 它是因為此存留期問題 WCF ServiceHosts 對應到接收位置而不是以接收連接埠。 WCF 的設計可確保個別 ServiceHosts 不在執行階段資源耗用，且許多可執行相同的可執行檔，而不需要任何問題。  
  
  每個使用 WCF 配接器的 BizTalk 傳送埠會對應至對 WCF 服務的呼叫。 要傳送的訊息時，BizTalk Server 可讓配接器對應的訊息建立 BizTalk WCF 配接器內的 WCF 用戶端 proxy。 傳送訊息之後會釋出 WCF 用戶端 proxy。 傳送埠上的 WCF 存留期不斷出現，而且會設為 proxy 建立、 使用，並終止。