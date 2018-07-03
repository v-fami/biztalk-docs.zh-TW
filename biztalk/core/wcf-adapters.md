---
title: WCF 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e64cd189-8805-4209-bd06-971363f38585
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c4980eb1045d12986ec486308231ab2f219445b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993807"
---
# <a name="wcf-adapters"></a>WCF 配接器

## <a name="overview"></a>概觀
適用於 Windows Communication Foundation (WCF) 的 BizTalk 配接器讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 能與 WCF 應用程式通訊。 BizTalk WCF 配接器包括表示 WCF 預先定義繫結的五個實體配接器 —**BasicHttpBinding**， **WsHttpBinding**， **NetTcpBinding**， **NetNamedPipeBinding**，並**NetMsmqBinding**。 提供這些表示預先定義繫結之 WCF 配接器的目的，是要讓您能夠輕鬆設定多數應用程式需求的必要資訊。  
  
 BizTalk WCF 配接器也包括兩個配接器，可讓您針對接收位置和傳送埠，自由設定 WCF 繫結和行為資訊。  

## <a name="available-wcf-adapters"></a>可用的 WCF 配接器
    
- **Wcf-wshttp 配接器**。 提供透過 HTTP 傳輸的 WS-* 標準支援。 WCF-WSHttp 配接器會實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是「文字」或「訊息傳輸最佳化機制」(Message Transmission Optimization Mechanism，MTOM) 編碼。  
  
- **Wcf-basichttp 配接器**。 與 ASMX 架構 Web 服務和用戶端，以及其他符合 WS-I 基本設定檔 1.1 的服務和用戶端進行通訊。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是文字編碼。  
  
- **Wcf-nettcp 配接器**。 提供透過 TCP 傳輸的 WS-* 標準支援。 WCF-NetTcp 配接器在 WCF-to-WCF 環境中提供有效率的通訊。 配接器實作下列規格： WS-交易之間外部應用程式和 MessageBox 資料庫，以及 Ws-security 用於訊息安全性和驗證的交易式互動。 傳輸方式是 TCP，訊息編碼方式則是二進位編碼。  
  
- **Wcf-netmsmq 配接器**。 提供利用 [!INCLUDE[btsCoName](../includes/btsconame-md.md)] 訊息佇列 (Message Queuing，MSMQ) 為傳輸方式的佇列支援，並支援鬆散偶合的應用程式、失敗隔離、負載調節，以及已中斷連線作業。  
  
- **Wcf-netnamedpipe 配接器**。 針對機器上跨處理序通訊提供安全的最佳化。 WCF-NetNamedPipe 配接器會針對傳輸安全性使用轉送安全性，針對訊息傳遞使用具名管線，並使用二進位訊息編碼。  
  
- **Wcf-custom 配接器**。 啟用使用 WCF 擴充性功能。 這個配接器讓您能夠針對接收位置和傳送埠，選取及設定 WCF 繫結和行為資訊。  
  
- **Wcf-customisolated 配接器**。 啟用透過 HTTP 傳輸使用 WCF 擴充性功能。 這個配接器讓您能夠針對在外掛式主控件中執行的接收位置，選取和設定 WCF 繫結和行為資訊。  
  
  此外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 還提供「BizTalk WCF 服務發佈精靈」和「BizTalk WCF 服務使用精靈」。 您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 BizTalk 協調流程，並將其發佈成 WCF 服務，同時將結構描述發佈為 WCF 服務。 您可以使用 [BizTalk WCF 服務使用精靈] 來產生 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 成品 (例如協調流程和型別)，以根據 WCF 服務的中繼資料文件來使用 WCF 服務。  
  
  本節提供可協助您設定和部署 WCF 配接器的資源。  
  
## <a name="next"></a>下一個 
  
-   [何謂 WCF 配接器？](../core/what-are-the-wcf-adapters.md)  
  
-   [設定 WCF 配接器](../core/configuring-the-wcf-adapters.md)  
  
-   [WCF-BasicHttp 配接器](../core/wcf-basichttp-adapter.md)  
  
-   [WCF-WSHttp 配接器](../core/wcf-wshttp-adapter.md)  
  
-   [WCF-NetTcp 配接器](../core/wcf-nettcp-adapter.md)  
  
-   [WCF-NetMsmq 配接器](../core/wcf-netmsmq-adapter.md)  
  
-   [WCF-NetNamedPipe 配接器](../core/wcf-netnamedpipe-adapter.md)  
  
-   [WCF-Custom 配接器](../core/wcf-custom-adapter.md)  
  
-   [WCF-CustomIsolated 配接器](../core/wcf-customisolated-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務](../core/using-wcf-services.md)   