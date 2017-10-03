---
title: "WCF 配接器 FAQ： 一般概念 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbeac135-3ba8-4b0b-a8ca-4eb5eb3d3ca3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f5acc3cb968ab35436fe684edd0eb41088b48a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-general-conceptual"></a>WCF 配接器 FAQ： 一般概念
以下是一些常見問題一般和概念性關於 Windows® Communication Foundation (WCF) 配接器。  
  
## <a name="what-is-a-wcf-adapter"></a>何謂 WCF 配接器？  
 BizTalk 配接器是方式的 Microsoft® BizTalk® Server 會與外界通訊的重要部分。 WCF 配接器是一種元件，管理 BizTalk 應用程式與它需要傳送和接收訊息，WCF 端點之間的通訊程序。 在 [!INCLUDE[prague](../includes/prague-md.md)] 中，WCF 配接器會公開為 WCF 繫結。 這表示可以使用 WCF 繫結任何 WCF 應用程式可以直接通訊，WCF 配接器而不需要介入的 BizTalk Server。 不過，使用 WCF 配接器透過 BizTalk Server 可讓您的應用程式基礎結構的優點，BizTalk Server 提供許多。 這些常見問題集焦點主要使用 WCF 配接器從 BizTalk Server 環境內。  
  
 WCF 配接器可讓 BizTalk Server 傳送和接收 WCF 訊息中使用的 WCF 繫結。 WCF 用戶端應用程式可以的傳送 WCF 訊息至 BizTalk 接收的訊息由 WCF 接收的位置接收配接器。 配接器使用 WCF 訊息，並將它轉換成 BizTalk 訊息。 轉換發生的方式，取決於它使用 BizTalk Server 管理主控台來設定特定配接器組態設定。 配接器將提交到 BizTalk MessageBox 資料庫內部的 BizTalk 訊息。 相對的 BizTalk 傳送埠使用 WCF 配接器可以訂閱此訊息類型、 取得 BizTalk 訊息、 將它轉換成 WCF 訊息，和 WCF 訊息傳送至使用其中一種支援的 WCF 通訊協定的 WCF 服務端點。  
  
 使用 WCF 配接器從 BizTalk Server 中的擷取 BizTalk WCF 應用程式解決方案，例如選擇與實作通訊協定、 安全性問題，以及交易作業為隱藏的複雜性。  
  
## <a name="what-are-the-wcf-adapter-bindings"></a>WCF 配接器繫結有哪些？  
 WCF 繫結分為兩類：  
  
-   **自訂繫結：**特殊的自訂繫結的繫結彈性增加時，存在。 這包含需要偏離標準的繫結的通訊狀況。 Wcf-custom 和 Wcf-customisolated 配接器可讓開發的廣泛的繫結的自訂項目。 這是藉由使用現有的繫結項目 （BindingElement 類別） 的組合和應用程式的行為 （Behavior 類別）。  
  
-   **標準繫結：** Microsoft 的目標是要開發著重於最常見的通訊案例的配接器。 使用標準繫結，藉以隱藏許多通訊協定的細節簡化開發人員的體驗。 [!INCLUDE[prague](../includes/prague-md.md)] 中的這一組 WCF 配接器會反映 .NET Framework 4.0 WCF 程式庫中提供的那一組繫結。 標準繫結是導入.NET WCF 程式庫，讓您更輕鬆地使用一般的繫結模式。 它們會配合一些最常用的通訊案例，包括：  
  
    -   Wcf-wshttp  
  
    -   WCF-BasicHttp  
  
    -   WCF-NetTcp  
  
    -   WCF NetMsmg  
  
    -   WCF-NetNamedPipe  
  
 BizTalk Server R2 隨附下列 WCF 配接器：  
  
1.  **Wcf-wshttp 配接器：**提供 WS-* 標準支援透過 HTTP 傳輸。 WCF-WSHttp 配接器會實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是文字或 Message Transmission Optimization Mechanism (MTOM) 編碼。  
  
2.  **Wcf-basichttp 配接器：**通訊與 ASMX 架構 Web 服務和用戶端和其他符合 WS-I-Basic Profile 1.1。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是文字編碼。  
  
3.  **Wcf-nettcp 配接器：**提供 WS-* 標準支援透過 TCP 傳輸。 WCF-NetTcp 配接器會提供有效率的通訊並實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。 傳輸方式是 TCP，訊息編碼方式則是二進位編碼。  
  
4.  **Wcf-netmsmq 配接器：**提供支援佇列利用 Message Queuing (也稱為 MSMQ) 做為傳輸並支援鬆散偶合的應用程式、 失敗隔離、 負載調節，以及中斷連線的作業。  
  
5.  **Wcf-netnamedpipe 配接器：**提供安全的最佳化，針對機器上跨處理序通訊。 WCF-NetNamedPipe 配接器會針對傳輸安全性使用轉送安全性，針對訊息傳遞使用具名管線，並使用二進位訊息編碼。  
  
     每個剛才所提到的五個配接器會對應至一個 1:1 關聯性中的 WCF 繫結。 兩個自訂配接器的結構，我們將討論稍微符號與 WCF 模型中，以產生實際兩個相異自訂配接器，對應至單一 WCF CustomBinding。  
  
6.  **Wcf-custom 配接器：**可讓您使用 WCF 擴充性功能。 配接器可讓您選取及設定 WCF 繫結以及接收位置或傳送埠裝載於 BizTalk Server 處理序的行為資訊。  
  
7.  **Wcf-customisolated 配接器：**透過 HTTP 傳輸啟用 WCF 擴充性功能。 配接器可讓您選取及設定 WCF 繫結和行為資訊在外掛式主控件的網際網路資訊服務 (IIS) 中執行的接收位置。  
  
## <a name="what-is-the-difference-between-the-wcf-xxx-adapter-and-the-wcf-xxx-binding"></a>WCF xxx 配接器和 WCF xxx 繫結之間的差異為何？  
 每個 WCF 配接器都會對應至其中一個內建的 WCF 繫結。 在較高層級，這些條款是幾乎交換時使用說 WCF xxx 配接器使用 WCF xxx 繫結。 例如，Wcf-basichttp 配接器使用 WCF BasicHttpBinding 類別。 WCF 繫結是 WCF 端點定義的一部分。 這被指中"ABC"的 WCF 端點，其中這些字母獨立位址、 繫結和合約。  
  
 繫結是由繫結項目集合所組成。 用戶端與端點通訊的方式稍加描述每個項目。 繫結必須包含：  
  
-   至少一個傳輸繫結項目。  
  
-   至少一個訊息編碼繫結項目 （由傳輸繫結項目來提供預設）。  
  
-   任何數目的其他通訊協定繫結項目。  
  
 由此描述在執行階段環境的建置程序可讓每個程式碼撰寫到該環境的繫結項目。 通常需要符合相同的繫結型別和被呼叫的 WCF 服務支援的配接器用戶端。 在 WCF 層級，在組態檔中，或明確地執行程式碼，則可以以宣告方式定義繫結。 WCF 配接器，協助使用特定 WCF 繫結的通訊，因此詞彙 「 配接器 」 和 「 繫結 」 通常會成為在其使用方式幾乎完全相同。  
  
## <a name="when-using-the-wcf-adapters-how-do-you-decide-which-wcf-binding-to-use"></a>使用 WCF 配接器，當您要如何決定要使用的 WCF 繫結？  
 您可以進行這項決定傳訊模式、 外部的條件約束和效能，依序為基礎。  
  
1.  **訊息模式：**如何進行根據訊息的流程通訊的通訊模式。 例如，訊息可能是單向 （要求） 或雙向 （要求-回應），可能交易處理，它可能會排入佇列，依此類推。  
  
    -   如果會排入佇列，您需要使用 Wcf-netmsmq 配接器，可支援單向排入佇列的交易的通訊。  
  
    -   如果模式是雙向要求-回應和兩部電腦之間的流程，您會使用 HTTP （如果您擔心盡可能有彈性的） 或 WCF NetTcp （如果您是在意效能）。  
  
    -   如果訊息維持在單一電腦上，而且只是處理序之間流動，您可以使用 Wcf-netnamedpipe 繫結。  
  
2.  **外部條件約束：**可能會要求您使用特定的繫結的問題。 比方說，假設在外部系統要求 SOAP Web 服務版本 1.2 與定址 1.0。 在此情況下，繫結是最佳選擇使用 Wcf-wshttp 配接器的 WSHttpBinding。 在所有的可能性，外部系統也必須設定需求的特定安全性模式。 如果外部系統所需的 Soap Web 服務 1.1 HTTP 繫結使用 Wcf-basichttp 配接器 」。  
  
3.  **效能：**進行呼叫，速度可能會在哪一個繫結您選擇使用您的應用程式中的決定因素：  
  
    -   如果 WCF 服務是與 BizTalk Server 在相同電腦上，使用 Wcf-netnamedpipe 配接器是最佳的效能選項。  
  
    -   如果 WCF 服務，本機網路上 Wcf-nettcp 得到最佳效能。  
  
    -   如果效能並不是主要的考量，且呼叫會透過網際網路，其中一個 HTTP 配接器 （Wcf-wshttp 或 Wcf-basichttp） 是正確的介面卡。  
  
         您使用任何進階的 HTTP 功能 (Wcf-wshttp) 還是基本功能 (Wcf-basichttp) 會規定哪些 HTTP 為基礎配接器是使用最佳的選擇。  
  
## <a name="when-do-you-use-one-of-the-two-custom-wcf-adapters"></a>何時您使用其中兩個自訂 WCF 配接器？  
 有兩個自訂 WCF 配接器隨附[!INCLUDE[prague](../includes/prague-md.md)]。 發生的原因是兩個自訂配接器是因為 BizTalk Server 需要的裝載特定配接器類型必須是系統向其註冊的一部分。 雖然 WCF Framework 中只有一個 CustomBinding 型別，但有兩個自訂配接器以配合這項限制預先存在的 BizTalk 配接器模型中的 BizTalk Server。 實際上，這些配接器其實是唯一的配接器需要因為它允許 WCF 通道堆疊設定的完整控制權。  
  
 自訂配接器的唯一缺點是，它們也需要您必須非常了解 WCF 組態和各種擴充性的技巧。  簡化的組態就是為什麼 Microsoft 配接器提供標準的 WCF 繫結。 標準繫結是預先定義來涵蓋大部分的常見使用案例，並讓傳送和接收訊息透過 BizTalk Server 越簡單越好。 若要使用其中一個這些自訂的配接器通常需要才會發生完全精確地符合您的傳送埠或接收位置的標準繫結失敗。 例如，可能是使用專屬的壓縮配置其訊息的應用程式。 若要支援此功能，自訂繫結項目必須寫入。 使用其中兩個標準自訂配接器可讓處理傳輸需求此自訂繫結的組態。 因此，自訂配接器可讓較高層級的通訊程序透過通道堆疊的繫結的組態控制。  
  
 自訂和自訂外掛式配接器之間的主要差異是其中一個裝載，而且裝載只會影響 BizTalk server 接收端。 Wcf-customisolated 配接器會使用與只接收位置，而不是與傳送埠。 「 外掛式 」 一詞是指的是裝載在 BizTalk Server 的 BtsNtSvc.exe 程序之外的 BizTalk 片語。 因此，當傳輸裝載在標準的 BtsNtSvc.exe 處理序內網際網路資訊服務 (IIS) 使用 HTTP 傳輸之外，會使用 Wcf-customisolated 配接器。 Wcf-custom 配接器可以搭配接收位置或傳送埠。 它用於裝載在標準的 BtsNtSvc.exe 程序內，傳輸。  
  
## <a name="how-does-a-wcf-endpoint-relate-to-biztalk-server"></a>WCF 端點如何與 BizTalk server？  
 WCF 端點是由位址、 繫結和合約 (ABC) 所組成。 BizTalk Server 中的使用者接收位置中指定的位址，或傳送埠。 WCF 配接器，使用者已選擇取決於繫結。 合約是程式設計人員導向，它會指定端點所公開的介面。  
  
 實際的端點存在，為傳送訊息之 WCF 接收位置。  有多種方式可以在 BizTalk Server 應用程式的 WCF 端點公開 （expose）：  
  
-   您可以使用 BizTalk WCF 服務發佈精靈發佈 BizTalk 協調流程做為 WCF 端點。  
  
-   您可以使用 BizTalk WCF 服務發佈精靈來建立接收位置中現有的 BizTalk 應用程式。  
  
-   您可以在程式碼中設定接收位置的繫結和位址，手動建立的 WCF 端點。  在此情況下接收位置是實際上不具型別。  它有指定完全根據 WCF 訊息類別，讓它能夠接收至 MessageBox 資料庫的任何訊息格式的合約。  
  
 每個 BizTalk 接收位置使用 WCF 配接器會公開為 WCF 用戶端能夠在其中進行呼叫的 WCF 端點。  接收位置在內部使用它自己的 WCF ServiceHost 允許啟用或停用各自不同的接收位置。 服務端點的存留期間存在，只要接收位置已啟用。 它是由於此存留期問題 WCF ServiceHosts 對應到接收位置而不是至接收埠。 WCF 的設計可確保個別 ServiceHosts 不會耗用大量資源執行階段，並有許多可以執行相同的可執行檔沒有任何問題。  
  
 每個使用 WCF 配接器的 BizTalk 傳送埠會對應至對 WCF 服務進行呼叫。 要傳送的訊息時，BizTalk Server 可讓配接器對應的訊息建立 BizTalk WCF 配接器內的 WCF 用戶端 proxy。 這些訊息會傳送之後會釋出 WCF 用戶端 proxy。 傳送埠上的 WCF 存留期不斷出現，且會建立、 使用，以及終止 proxy。