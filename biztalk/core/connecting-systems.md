---
title: 系統連線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c4895e5-7272-415f-a0de-905256fa0a43
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6113629ebe28e8ca6b6bb4d781933770bcb6883c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008647"
---
# <a name="connecting-systems"></a>連接系統
進行整合的首要條件是能在不同機器上使用不同軟體有效地交換訊息。 存在的通訊樣式的多樣性，BizTalk Server 必須支援各種不同的通訊協定和訊息格式。 下面將描述一種新的引擎，能夠適用此種多元化的溝通方式。 不過，必須記住一項重要的概念就是，這種引擎內部只能使用 XML 文件。 不管接收到何種格式的訊息，接收後都必須將訊息轉換為 XML 文件。 同樣地，若文件的接收者無法接受 XML 文件，該引擎也會將文件轉換為目標接受的格式。  
  
## <a name="sending-and-receiving-messages-adapters"></a>傳送和接收訊息： 配接器  
 BizTalk Server 必須與各種不同的軟體溝通，因為它必須依賴配接器進行這項作業。 配接器是通訊機制的實作，例如一個特殊的通訊協定。 開發人員會判定在哪種狀況下使用哪一種配接器。 他可能會選擇其中一個，例如 BizTalk Server 提供內建配接器或使用 Windows SharePoint Services，例如為熱門產品所建立的配接器，或甚至建立自訂的配接器。 在以上任何一種情形中，配接器是建立在稱為「配接器架構」的標準上。 此架構提供建立及執行配接器的常用方法，且也支援用來管理所有配接器類型的相同工具。  
  
 Microsoft BizTalk Server 包含下列原生配接器：  
  
-   File 配接器： 支援讀取和寫入檔案，在 Windows 檔案系統中。 因為涉及商務程序的應用程式通常存取相同的檔案系統 (無論在本機或網路上)，所以透過檔案來交換訊息是很方便的選擇。  
  
-   FTP 配接器： 支援傳送及接收檔案傳輸通訊協定 (FTP) 伺服器與 BizTalk Server 之間的資訊。  
  
-   HTTP 配接器： 支援傳送及接收資訊使用 HTTP。 BizTalk Server 會公開一或多個 Url，讓其他應用程式將資料傳送給它，而且它可以使用此配接器將資料傳送至其他 Url。  
  
-   MSMQ 配接器： 支援傳送和接收訊息，使用 Microsoft Message Queuing (MSMQ)。  
  
-   WebSphere MQ 配接器： 支援傳送和接收訊息使用 IBM WebSphere MQ （先前稱為 MQSeries）。  
  
-   POP3 配接器： 支援接收電子郵件訊息與使用 「 郵局通訊協定 (POP3) 的第三版及其附件。  
  
-   SMTP 配接器： 支援使用 SMTP 傳送訊息。 使用標準電子郵件地址來識別合作對象。  
  
-   SOAP 配接器： 支援傳送和接收 Web 服務要求，讓 BizTalk Server 來連接到 Web 服務。  
  
-   WCF 配接器： 支援傳送及接收資訊使用 Windows Communication Foundation。  
  
-   Windows SharePoint Services (WSS) 配接器： 支援存取及發佈儲存在 Microsoft Windows SharePoint 文件庫中的文件。  
  
 Microsoft 也提供一些常用商務軟體的配接器，包括：  
  
-   Microsoft BizTalk Adapter for JD Edwards OneWorld  
  
-   Microsoft BizTalk Adapter for JD Edwards EnterpriseOne  
  
-   Microsoft BizTalk Adapter for PeopleSoft Enterprise  
  
-   Microsoft BizTalk Adapter for TIBCO Rendezvous  
  
-   Microsoft BizTalk Adapter for TIBCO Enterprise Message Service  
  
 如需有關這些介面卡的詳細資訊，請參閱[配接器在 BizTalk Server](../core/adapters-in-biztalk-server.md)。  
  
 不管用來接收資料的配接器為何，所接收的訊息必須經過處理，協調流程才能存取。 同樣地，由協調流程產生的外寄訊息一般會先經過處理，然後配接卡才會傳送它們。  
  
## <a name="processing-messages-pipelines"></a>處理訊息： 管線  
 商務程序的應用程式交換不同種類的文件來進行通訊： 如需範例，訂單及發票。 BizTalk Server 應用程式執行商務程序，它必須能夠正確處理包含這些文件的訊息。 這項處理可能包含多個步驟，因此會由訊息管線執行。 內送訊息透過接收管線處理，而外寄訊息則是透過傳送管線傳送。  
  
 例如，雖然越來越多的應用程式都設計為可瞭解 XML 文件，但是目前多數的應用程式仍無法瞭解。 BizTalk Server 只能搭配 XML 文件的內部運作，因為它必須提供的方式與 XML 之間來回轉換其他格式。 也可能需要其他服務，例如驗證訊息的寄件者。 若要在模組中處理這些工作，而不是自訂程序，會在某幾個階段中建構管線，而每個階段都包含一或多個啟用的 .NET 或「元件物件模型」(COM) 元件。 每個元件會處理特定的訊息處理程序部分。 BizTalk Server 會提供數個標準元件，可解決最常見的狀況。 若這樣還不夠，開發人員也可以為接收和傳送管線二者建立自訂元件。  
  
 ![](../core/media/understandingbts-05-pipelinereceive.gif "UnderstandingBTS_05_PipelineReceive")  
  
 上圖說明接收管線中的階段，以及為每一個階段提供的標準元件。 這些階段與其相關元件如下：  
  
-   解碼： BizTalk Server 可以提供一個標準元件的這個階段，則 MIME/SMIME 解碼器。 此元件可以處理訊息以及任何包含在 MIME 或 Secure MIME (S/MIME) 格式的附件。 元件會將這兩種類型的訊息轉換成 XML，而且它也可以解碼 S/MIME 訊息以及驗證其數位簽章。  
  
-   反組譯： 提供三個標準元件。 一般檔案解譯器元件可將一般檔案轉換成 XML 文件。 這些檔案可以是序數 (每一筆記錄有相同長度和結構) 或分隔 (指派的字元是用於分隔檔案中的記錄)。 第二個標準元件是 XML 解譯器，可剖析已使用 XML 描述的內送訊息。 第三個標準元件是目前不常用的 BizTalk Framework 解譯器。 它接受使用 BizTalk Framework 中，BizTalk Server 2000 中實作時所定義之可靠訊息機制所傳送訊息。  
  
-   BizTalk Server 進行驗證： 此階段提供 XML 驗證器元件。 如其名稱所示，此元件會驗證由「解譯」階段為指定之結構描述或結構描述群組產生的 XML 文件，然後當文件不符合其中一個結構描述時傳回錯誤。  
  
-   解析合作對象： 此階段中，合作對象解析的唯一標準元件嘗試判斷此訊息的寄件者的身分識別。 如果訊息經過數位簽署，簽章用來查詢 BizTalk Server 中的 「 管理 」 資料庫中使用 Windows 身分識別。 (之後會提到，BizTalk Server 的管理工具也會使用此資料庫)。若訊息包含 Windows 使用者已驗證的安全性識別項 (SID)，就會使用此身分。 若任何機制皆未成功，訊息寄件者會被指派預設匿名身分。  
  
 ![](../core/media/understandingbts-06-pipelinesend.gif "UnderstandingBTS_06_PipelineSend")  
  
 外寄訊息也可以透過多個階段傳送，如使用中傳送管線定義一般。 上圖顯示傳送管線的階段和標準元件。 其中包括：  
  
-   預先組合： 提供沒有標準的元件。 反之，可以視需要將自訂元件插入此處。  
  
-   組合： 平行化解接收管線中的 「 解譯 」 階段，此階段也有三個標準元件。 一般檔案組合器會將 XML 訊息轉換為位置或分隔的一般檔案，而 XML 組合器則支援新增信封及對外寄 XML 訊息進行變更。 第三個選擇就是 BizTalk Framework 組合器，它會使用 BizTalk Framework 傳訊技術封裝訊息以進行可靠的傳輸。  
  
-   編碼： BizTalk Server 只定義一個標準元件的這個階段，MIME/SMIME 編碼器。 此元件會用 MIME 或 S/MIME 格式封裝外寄訊息。 若使用 S/MIME，也可以數位簽章和加密訊息。  
  
 BizTalk Server 定義部分預設管線，包括簡單的接收/傳送配對，可用來處理在 XML 中表示的訊息。 開發人員也可使用「管線設計師」建立自訂管線。 此工具是在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中執行，它提供圖形化介面，可以讓開發人員拖放元件來建立具備必要行為的管線。  
  
## <a name="choosing-messages-subscriptions"></a>選擇訊息： 訂用帳戶  
 當訊息已經進入配接器及接收管線後，下一步就是判定它的目的地。 訊息最常目標至協調流程，但也可能直接移至傳送管線，讓 BizTalk Server 来做為單純的傳訊系統的訊息。 在任何狀況下，都會使用訂閱讓訊息與其目的地相符。  
  
 當接收管線處理訊息時，會建立包含多個訊息屬性的訊息內容。 協調流程或傳送管線可以以這些屬性的值為基礎，訂閱訊息。 例如，協調流程可以建立符合所有「發票」類型訊息的訂閱、或從 QwickBank 公司接收到所有「發票」類型的訊息、或從 QwickBank 公司收到且超過 $10,000 的「發票」類型訊息。 不管指定什麼，訂閱只會將符合訂閱定義的訊息傳回給訂閱者。 接收的訊息可能會建立部分協調流程來起始商務程序，或者它可能啟動執行中商務程序的其他步驟。 同樣地，當協調程序傳送訊息時，該訊息會符合以管線建立之訂閱為基礎的傳送管線。  
  
-   在 BizTalk Server 中，所以也可以訂閱特定錯誤狀況。 可以特定方式處理錯誤訊息或路由傳送到特定目的地，如 Windows SharePoint Services 資料夾。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Server 傳訊引擎](../core/the-biztalk-server-messaging-engine.md)   
 [發佈和訂閱架構](../core/publish-and-subscribe-architecture.md)   
 [配接器](../core/adapters.md)   
 [管線](../core/pipelines.md)