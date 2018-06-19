---
title: 何謂 WCF 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18ca8535-3386-4018-8b5b-d32bdb9ebf70
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41c942c7c2ef870b2a61c519e79fb8a124059f03
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22291214"
---
# <a name="what-are-the-wcf-adapters"></a>何謂 WCF 配接器？
Windows Communication Foundation (WCF) 配接器有兩種，一種是接收配接器，另一種是傳送配接器。 您可以使用 WCF 接收配接器接收 WCF 服務要求。 WCF 接收配接器會接收要求、建立 BizTalk 訊息物件，並將關聯的屬性升級為訊息內容。 您可以使用 WCF 傳送配接器來呼叫 WCF 服務。 WCF 傳送配接器會經由無類型合約來呼叫 WCF 服務。  
  
> [!NOTE]
>  WCF 配接器不支援使用遠端程序呼叫 (RPC) 樣式的 Web 服務，因為 RPC 樣式之 Web 服務的訊息部分參考的是訊息類型，而不是 WCF 將元素用於訊息部分的訊息元素。 建議您透過 [加入 Web 參考] 精靈加入 RPC 樣式的 Web 服務，以便在 BizTalk 專案中使用 Web 服務。  
  
## <a name="web-services-standards-support"></a>Web 服務標準支援  
 WCF 配接器提供諸如 WS-Addressing、WS-Security 和 WS-AtomicTransaction 等 WS-* 標準的支援。 此版本的 WCF 配接器不支援 WS-ReliableMessaging。 如需 WCF 支援的規格的清單，請參閱[ http://go.microsoft.com/fwlink/?LinkId=88314 ](http://go.microsoft.com/fwlink/?LinkId=88314)。  
  
### <a name="ws-addressing"></a>WS-Addressing  
 WCF 配接器需依賴 WCF 所提供的 WS-Addressing 標準支援。 WCF 配接器提供下列功能：  
  
-   設定在中繼交換要求期間取得的傳送埠端點位址。  
  
-   設定傳送埠端點位址的定位標頭。  
  
-   設定 BizTalk 接收位置中公開之端點的定位標頭。  
  
### <a name="ws-security"></a>WS-Security  
 WCF 配接器需依賴 WCF 所提供的安全性標準支援。 WCF 配接器支援下列標準：  
  
-   Web 服務安全性︰ SOAP 訊息安全性 (Ws-security) 1.0 和 1.1 版  
  
-   Web Services Secure Conversation Language (WS-SecureConversation)  
  
-   Web Services Trust Language (WS-Trust)  
  
-   Web Services Security X.509 Certificate Token Profile  
  
-   Web Services Security Username Token Profile 1.0  
  
-   Web Services Security Kerberos Token Profile 1.0  
  
#### <a name="service-authentication-types"></a>服務驗證類型  
 支援的 WCF 服務驗證類型如下：  
  
-   無  
  
-   視窗  
  
-   憑證  
  
#### <a name="client-authentication-types"></a>用戶端驗證類型  
 支援的 WCF 用戶端驗證類型如下：  
  
-   匿名  
  
-   UserName  
  
-   視窗  
  
-   憑證  
  
#### <a name="security-modes"></a>安全性模式  
 支援的安全性模式如下：  
  
-   傳輸  
  
-   訊息  
  
-   混合 (傳輸層安全性和訊息層驗證)  
  
### <a name="ws-atomictransaction"></a>WS-AtomicTransaction  
 WCF-WsHttp、WCF-NetTcp 和 WCF-NetMsmq 配接器支援 WS-AtomicTransaction 通訊協定。 這項支援適用於下列實例：  
  
-   交易式提交訊息至 MessageBox 資料庫。  
  
-   從 MessageBox 至交易式目的地的交易式訊息傳輸。  
  
> [!NOTE]
>  交易式範圍受限於 MessageBox。 例如，BizTalk 協調流程不能參與用戶端的交易。 同樣地，目的端點也不能參與 BizTalk 協調流程起始的交易。  
  
#### <a name="transactional-submission"></a>交易式提交  
 Wcf-wshttp 和 Wcf-nettcp 配接器的交易式提交至 BizTalk Server 會啟用選取 **啟用交易** 接收位置傳輸屬性對話方塊中核取方塊。 Wcf-netmsmq 配接器， **交易式** 預設會選取核取方塊。 如果訊息提取來源的訊息佇列未標示為交易式，您必須清除這個核取方塊，否則便會收到錯誤訊息。  
  
 如果交易功能已啟用，訊息便會利用戶端的交易提交到 MessageBox 資料庫。 如果用戶端嘗試在交易式範圍之外提交訊息，配接器會將例外狀況傳回到用戶端， 但是不會擱置任何訊息。 如果交易功能已停用，訊息將提交到 MessageBox 資料庫，而且不會使用用戶端的交易。 如果用戶端嘗試在交易式範圍內提交訊息，配接器會將例外狀況傳回到用戶端，而且不會擱置任何訊息。  
  
#### <a name="transactions-and-receive-location-type"></a>交易和接收位置類型  
 交易式提交只適用於單向接收位置。 如果用戶端嘗試在雙向接收位置的交易式範圍中提交訊息，系統會將例外狀況傳回到用戶端，而且不會擱置任何訊息。  
  
#### <a name="transactional-transmission"></a>交易式傳輸  
 Wcf-wshttp 和 Wcf-nettcp 配接器，BizTalk Server 從交易式傳輸會啟用選取 **啟用交易** 傳送埠傳輸屬性對話方塊中核取方塊。 Wcf-netmsmq 配接器， **交易式** 預設會選取核取方塊。 如果訊息傳送目標的訊息佇列未標示為交易式，您必須清除這個核取方塊，否則便會收到錯誤訊息。  
  
 如果交易功能已啟用，訊息便會從正在進行交易的 MessageBox 資料庫中傳輸並刪除。 如果目的地服務在接收訊息之後執行過任何工作，而且沒有從 MessageBox 刪除訊息，則交易將會中止，而且服務的所有交易工作也都會回復。 如果交易功能已停用，則會以不使用交易的方式，從正在進行交易的 MessageBox 資料庫傳輸並刪除訊息。  
  
## <a name="single-sign-on-support"></a>單一登入支援  
 您可以模擬及取得企業單一登入 (SSO) 票證，以便將 SSO 與 WCF 配接器搭配使用。 如需如何搭配 WCF 配接器使用 SSO 的詳細資訊，請參閱[WCF 配接器的單一登入支援](../core/single-sign-on-support-for-the-wcf-adapters.md)。  
  
 下表摘要說明將 SSO 支援與 WCF 接收配接器搭配使用時無法支援的實例。  
  
|安全性模式|認證|  
|-------------------|----------------|  
|無|無|  
|傳輸|無|  
|訊息|無|  
|TransportWithMessageCredentials|無|  
|TransportCredentialOnly|無|  
  
## <a name="wcf-extensibility"></a>WCF 擴充性  
 您可以透過開發下列延伸模組並將這些模組用於 WCF-Custom 和 WCF-CustomIsolated 配接器的方式，來擴充 WCF 的功能：  
  
-   自訂繫結  
  
-   自訂繫結元素  
  
### <a name="custom-bindings"></a>自訂繫結  
 自訂繫結的開發方式是將個別繫結元素封裝成容器，以公開特定使用實例的組態屬性子集。 您必須將組件安裝到全域組件快取 (GAC)，然後再將延伸模組元素加入電腦組態檔中，以註冊繫結延伸模組。 若要使用自訂繫結，您必須在 BizTalk 群組的每一部伺服器上設定繫結。 在安裝繫結之後，它就會變成 WCF-Custom 和 WCF-CustomIsolated 配接器的可見項目。 WCF-Custom 和 WCF-CustomIsolated 配接器將會在繫結組態項目上使用反映，以取得繫結組態屬性。  
  
### <a name="custom-binding-elements"></a>自訂繫結元素  
 開發自訂繫結元素的方式是加入或修改特定的傳輸通道元件。 例如，自訂解壓縮元件會封裝成繫結元素，或者 UDP 傳輸會表示為繫結元素。 這些繫結元素可以在 WCF 配接器內使用。 您可以定義通道堆疊，使其將自訂繫結元素與其他現成或自訂的繫結元素搭配使用。 您必須將組件安裝到 GAC，然後再將延伸模組元素加入電腦組態檔中，以註冊繫結元件延伸模組。 若要使用自訂繫結，您必須在 BizTalk 群組的每一部伺服器上設定繫結。 若要使用自訂繫結項目，您可以選取 **CustomBinding** 繫結類型，然後新增、 修改或重新排列的繫結項目所需的順序。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [WCF 接收配接器](../core/wcf-receive-adapter.md)  
  
-   [WCF 傳送配接器](../core/wcf-send-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
-  [WCF 配接器](../core/wcf-adapters.md)   
-  **WCF 配接器服務合約參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]