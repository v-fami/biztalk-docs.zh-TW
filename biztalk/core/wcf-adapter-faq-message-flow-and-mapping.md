---
title: "WCF 配接器 FAQ： 訊息流程和對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 907e5c6a-a095-4b3a-9362-506832b6bc8c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58909b0d0cb0a126dd84e21809ca8e8f3941d758
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-adapter-faq-message-flow-and-mapping"></a>WCF 配接器 FAQ： 訊息流程和對應
## <a name="what-is-the-message-flow-within-the-wcf-and-biztalk-systems"></a>何謂 WCF 和 BizTalk 系統內的訊息流程  
 以下是 BizTalk Server 內送 WCF 訊息流程的描述：  
  
1.  WCF 訊息到達接收位置，而且 BizTalk Server 會具現化託管的 WCF 服務。  
  
2.  WCF 執行階段具現化服務的通道堆疊與通道接聽程式。 通道堆疊是一串處理不同的處理工作階段。 每個通道堆疊是由至少一個傳輸通道、 最常訊息編碼器，以及零或多個通訊協定通道所組成。 傳輸通道會讀取內送的訊息資料流，在到達時。 它會叫用編碼器解譯訊息，並產生 WCF 訊息物件。 此時每個通訊協定通道將有機會在 WCF 中的訊息順序上運作。  
  
3.  將它轉送到已設定的 WCF 通道堆疊並將它分派至正確的服務執行個體的接聽程式接收 WCF 訊息。 此時 WCF 訊息已轉換 （對應） BizTalk 訊息。 簡短所述，WCF 訊息標頭寫入到 BizTalk 訊息內容中，與 WCF 訊息內文會寫入 BizTalk 訊息內文部分。 對應可讓您控制的 WCF 訊息的哪些部分會變成 BizTalk 訊息內文： 信封、 主體或子元素。  
  
4.  設定接收位置中任何管線元件處理 BizTalk 訊息。  
  
5.  BizTalk 訊息會儲存在 MessageBox 資料庫。  
  
 以下是從 BizTalk Server 外寄 WCF 訊息流程的描述：  
  
1.  由傳送埠，根據其訂閱接收 BizTalk 訊息。  
  
2.  任何管線元件會設定傳送埠處理序中 BizTalk 訊息。  
  
3.  WCF 通道堆疊會具現化，和 BizTalk 訊息到 WCF 訊息，根據服務的外部可見的合約是 已轉換 （對應）。  
  
4.  WCF 通道堆疊會傳輸至外部 WCF 服務的 WCF 訊息。  
  
## <a name="how-is-a-wcf-message-converted-mapped-into-a-biztalk-message"></a>如何為 WCF 訊息轉換 （對應） 為 BizTalk 訊息？  
 若要了解對應，我們要查看 WCF 訊息和 BizTalk 訊息的結構。  
  
 WCF 訊息根據 SOAP 訊息結構和訊息屬性、 訊息標頭和單一訊息本文所組成。  
  
-   **訊息屬性**是附加至訊息物件的 Common Language Runtime (CLR) 物件。 屬性是內部 WCF 堆疊與通訊的每一端的使用者的應用程式。 用戶端與伺服器之間直接傳輸。  
  
-   **訊息標頭**，不過，用戶端與伺服器之間傳輸。 上一則訊息，可以有許多的標頭，但沒有只能有一個訊息本文，而標頭與訊息內文資料流處理。 訊息標頭和訊息本文會定義當做 XML Infoset。  
  
-   **主體**WCF 訊息是為其屬性和標頭提供的詳細資訊訊息的主要內容。  
  
 BizTalk 訊息的結構。  
  
-   沒有一組內容屬性，每個訊息上。 每個內容屬性的命名空間名稱/值組所組成。 內容屬性可以升級或寫入。 如果升級，他們可以參與執行 BizTalk Server 中的路由規則。  
  
-   訊息在 BizTalk Server 中的資料可以包含多個資料流。 因為每個資料流可以獨立讀取多部分 BizTalk 訊息。 是特殊的其中一個訊息部分，它稱為內文部分。  
  
 有時候很雙向通訊，因為 WCF 配接器可讓特定轉譯或要設定的傳入和傳出的訊息交換的方向的對應。 這可以為接收位置和傳送埠，BizTalk Server 中的完成。  
  
 BizTalk WCF 配接器支援轉譯在執行階段之間這些兩個訊息結構的排列的數目。 對應由**訊息**索引標籤中**傳輸屬性**個 WCF 配接器 對話方塊。 例如，最明顯的轉譯，以及預設值，時，傳入 WCF 訊息的本文會變成 BizTalk 訊息的本文。 如需對應模式的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=119792](http://go.microsoft.com/fwlink/?LinkID=119792)。  
  
## <a name="how-can-you-preserve-the-complete-incoming-wcf-message-inside-the-biztalk-message"></a>您可以保留完整的內送 WCF 訊息的 BizTalk 訊息內？  
 輸入 BizTalk 訊息內文的選項的其中一個是**信封**選項。 選擇此選項會包含在 soap: Envelope 元素到內送的 BizTalk 訊息內文的整個 SOAP 訊息。 產生的 BizTalk 訊息包含信封標籤、 所有標頭和主體。  
  
## <a name="how-can-you-extract-specific-elements-of-the-incoming-wcf-message-into-a-biztalk-message-or-map-elements-of-an-outgoing-biztalk-message-to-an-outgoing-wcf-message"></a>您要如何將內送 WCF 訊息的特定項目擷取至 BizTalk 訊息，或外寄 BizTalk 訊息的項目對應至外寄 WCF 訊息？  
 若要對應的 WCF 或 BizTalk 訊息內文的區段，使用的路徑或範本的選項。 這可讓您輸入 XPath 運算式來擷取特定的訊息內文部分。 完整的 XPath 語法不支援在此情況下擷取資料流處理，並讀取器必須因此永遠逐步往前。 這就是為什麼在**訊息** 索引標籤，它會呼叫 路徑-內容由內文路徑定位 而不是 「 XPath-內容由內文路徑定位 」。  
  
 在接收端，使用路徑運算式，指出要從 WCF 訊息中讀取資料的方式。 用於輸入訊息，BizTalk 訊息內容取得取代路徑陳述式所擷取的特定項目。 配接器會使用此路徑運算式來找出並擷取 BizTalk 訊息所需的資料。  
  
 在傳送端，使用範本來建立 WCF 訊息從 BizTalk 訊息。 輸出訊息的範本選項被為了允許完全相反的 XPath 選項。 在 WCF 配接器組態中，XML 的程式碼片段用於做為基礎的外寄訊息的結構。 BizTalk 訊息的內容會在執行階段插入此結構。  
  
 外寄訊息，您也必須選擇使用 XML、 Base64、 字串或十六進位的節點編碼設定所撰寫的項目類型。 您想要擷取 WCF 訊息內包含二進位資料流時，很有幫助此選項。 使用這項功能會指示 WCF 訊息本文讀取裝置上使用 ReadContextAsBase64 呼叫 WCF 配接器。 這個呼叫可讓讀取直接透過 XmlReader API，所以使用這個功能的二進位資料可以直接從移動 WCF 傳輸到 BizTalk MessageBox 資料庫的二進位資料。 寫入包含二進位資料的節點路徑可以拉出，並將它放入 BizTalk 訊息。  
  
## <a name="how-do-you-access-wcf-message-properties-within-an-incoming-wcf-message"></a>您要如何存取內送 WCF 訊息內的 WCF 訊息屬性？  
 若要存取內送 WCF 訊息內的屬性，它會轉換為 BizTalk 訊息之前，您可以使用自訂的 WCF 通道元件或服務模型與 WCF 行為的擴充點。 例如， **IDispatchMessageInspector**物件。 BizTalk Wcf-custom 和 Wcf-customisolated 配接器提供簡單的方法讓您的應用程式使用 WCF 行為的電源插入**行為**索引標籤中**傳輸屬性**對話方塊這些介面卡。  
  
 若要讓 WCF 訊息的 WCF 配接器可用的屬性，這些屬性需要先將寫入訊息內文或標頭做為內容。 標頭會複製到 BizTalk 訊息內容會自動為您。 如果您想升級屬性值，您可以使用自訂的 BizTalk 管線元件要將 WCF 訊息屬性升級至 BizTalk 訊息內容中，從**IComponent： 執行**方法。 使用 WCF 自訂配接器自訂 WCF 行為可讓您利用 WCF 和 BizTalk 的擴充性功能更強大且彈性，讓您的方案。 WCF 配接器可讓您結合現有的 BizTalk 和 WCF extensibilities 來解決問題。  
  
 好消息是這個通用的屬性大小寫的 WCF 配接器中沒有捷徑。 您無須撰寫這兩個擴充性文本的內容，而只要讓 WCF 延伸模組去新建 WCF 配接器可理解的「已知」屬性即可。  
  
 若要撰寫或升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 訊息必須包含屬性名稱和命名空間所組成的值組的集合。 這可讓 WCF 配接器能夠辨識的標頭值會以寫入或升級。  
  
 WCF 訊息必須包含下列訊息屬性，WCF 配接器才能將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容：  
  
-   若要升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 配接器會尋找的索引鍵配對**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote**和值**清單 <KeyValuePair\<XmlQualifiedName，物件\>>**。 使用此配對，WCF 配接器需要命名空間、 名稱和值從**XmlQualifiedName**物件，並使用它們來升級標頭值。  
  
-   若要撰寫，但不要升級，SOAP 標頭值到 BizTalk 訊息內容中，WCF 配接器會尋找的索引鍵配對**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext**和值**清單 < KeyValuePair\<XmlQualifiedName，物件\>>。** 使用此配對，WCF 配接器便可將值寫入訊息內容。  
  
> [!NOTE]
>  升級的屬性也必須指定 BizTalk 屬性結構描述中才能被接受，BizTalk 執行階段。  
  
## <a name="you-have-an-existing-orchestration-or-send-port-etc-that-expects-a-biztalk-multipart-message-how-can-you-get-a-multipart-message-in-the-wcf-scenario"></a>您有現有的協調流程 （或傳送埠等），必須要有多部分 BizTalk 訊息。 如何取得多部分訊息在 WCF 案例？  
 多部分 BizTalk 訊息是由一或多個訊息部分所組成。 不過，WCF 會有沒有多部分訊息的概念。 因為 WCF 不會使用多部分訊息，BizTalk WCF 配接器也請勿使用它們。 問題是您可能有現有的 BizTalk 協調流程或管線產生或取用多部分訊息寫入。  
  
 如果您需要進入 BizTalk Server 中的多部分訊息，使用內送 WCF 訊息和 WCF 配接器，轉譯為 XML 多部分資料，WCF 訊息中。 開發自訂的 BizTalk 管線元件來處理內送的 XML 資料流 （WCF 訊息），並建立您的應用程式適當的 BizTalk 多部分訊息。 如果需要，可以在傳送端的反向完成這些步驟。