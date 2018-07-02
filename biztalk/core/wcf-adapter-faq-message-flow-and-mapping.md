---
title: WCF 配接器常見問題集： 訊息流程和對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 907e5c6a-a095-4b3a-9362-506832b6bc8c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae55b6447923e9618a3e4776284659d48a2b25a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968175"
---
# <a name="wcf-adapter-faq-message-flow-and-mapping"></a>WCF 配接器常見問題集： 訊息流程和對應
## <a name="what-is-the-message-flow-within-the-wcf-and-biztalk-systems"></a>何謂 WCF 和 BizTalk 系統內的訊息流程  
 以下是流程的 BizTalk Server 內送 WCF 訊息的描述：  
  
1. WCF 訊息到達接收位置，以及 BizTalk Server 具現化裝載的 WCF 服務。  
  
2. 服務的通道堆疊和它的通道接聽程式，具現化 WCF 執行階段。 通道堆疊是一連串的處理不同的處理工作階段。 每個通道堆疊是由至少傳輸通道、 最常訊息編碼器，以及零或多個通訊協定通道所組成。 傳輸通道會讀取內送的訊息資料流在到達時。 它會叫用的編碼器解譯訊息，並產生 WCF Message 物件。 目前每個通訊協定通道會有機會作用於 WCF 訊息的順序。  
  
3. 接聽程式，將它轉送到已設定的 WCF 通道堆疊，並將它分派至適當的服務執行個體所接收 WCF 訊息。 此時將 WCF 訊息會轉換 （對應） 成 BizTalk 訊息。 簡單來說，WCF 訊息的標頭會寫入 BizTalk 訊息內容中，與 WCF 訊息內文寫入 BizTalk 訊息內文部分。 對應可讓您控制 WCF 訊息的哪些部分會變成 BizTalk 訊息內文： 信封、 主體或子元素。  
  
4. 接收位置中所設定的任何管線元件會處理 BizTalk 訊息。  
  
5. BizTalk 訊息會儲存在 MessageBox 資料庫。  
  
   以下是從 BizTalk Server 的外寄 WCF 訊息流程的描述：  
  
6. BizTalk 訊息是透過傳送埠，根據其訂用帳戶接收。  
  
7. 在傳送連接埠的處理程序中設定的任何管線元件的 BizTalk 訊息。  
  
8. WCF 通道堆疊會具現化，以及 BizTalk 訊息根據服務的外部可見的合約的 WCF 訊息是 已轉換 （對應）。  
  
9. WCF 通道堆疊 WCF 將訊息傳送至外部 WCF 服務。  
  
## <a name="how-is-a-wcf-message-converted-mapped-into-a-biztalk-message"></a>如何為 WCF 訊息轉換 （對應） 成 BizTalk 訊息？  
 若要了解此對應，我們要看看 WCF 訊息 」 和 「 BizTalk 訊息的結構。  
  
 WCF 訊息根據 SOAP 訊息結構和訊息屬性、 訊息標頭和單一訊息本文組成。  
  
- **訊息屬性**是附加至訊息物件的 Common Language Runtime (CLR) 物件。 屬性是 WCF 堆疊和通訊的每一端的使用者的應用程式內部。 它們永遠不會直接傳送用戶端與伺服器之間。  
  
- **訊息標頭**，不過，用戶端與伺服器之間傳送。 上一則訊息，可以有許多的標頭只能有一個訊息主體，但標頭與訊息內文資料流處理。 訊息標頭和訊息內文定義為 XML Infoset。  
  
- **主體**WCF 訊息是為其屬性和標頭提供的詳細資訊訊息的主要內容。  
  
  BizTalk 訊息的結構。  
  
- 沒有一組每個訊息上的內容屬性。 每個內容屬性是由命名空間名稱/值組所組成。 內容屬性可以升級或寫入。 如果升級，他們可以參與 BizTalk Server 內執行的路由規則。  
  
- 在 BizTalk Server 中訊息的資料可以包含多個資料流。 因為每個資料流可以獨立讀取，是多部分 BizTalk 訊息。 其中一個訊息部分是特殊的它稱為內文部分。  
  
  因為通訊有時可以是雙向的 WCF 配接器可讓特定轉譯或對應至輸入和輸出的雙向訊息交換的設定。 這可以為接收位置和傳送埠，BizTalk Server 內完成。  
  
  BizTalk WCF 配接器支援在執行階段，這些兩個訊息結構之間進行轉譯的排列數目。 對應透過**訊息**索引標籤中**傳輸屬性**個 WCF 配接器 對話方塊。 比方說，最明顯的轉譯，以及預設值時，傳入 WCF 訊息的主體會變成 BizTalk 訊息內文。 如需對應模式的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkID=119792 ](http://go.microsoft.com/fwlink/?LinkID=119792)。  
  
## <a name="how-can-you-preserve-the-complete-incoming-wcf-message-inside-the-biztalk-message"></a>您可以保留在 BizTalk 訊息內完成的內送 WCF 訊息？  
 輸入 BizTalk 訊息內文的選項之一就是**信封**選項。 選擇此選項會到內送的 BizTalk 訊息內文包含在 soap Envelope： 元素的整個 SOAP 訊息。 產生的 BizTalk 訊息包含信封標籤、 所有標頭和主體。  
  
## <a name="how-can-you-extract-specific-elements-of-the-incoming-wcf-message-into-a-biztalk-message-or-map-elements-of-an-outgoing-biztalk-message-to-an-outgoing-wcf-message"></a>您要如何將內送 WCF 訊息的特定項目擷取到 BizTalk 訊息，或將外寄 BizTalk 訊息的項目對應至外寄 WCF 訊息？  
 若要對應 WCF 或 BizTalk 訊息內文的區段，使用 路徑 或 範本選項。 這可讓您輸入 XPath 運算式來擷取訊息內文的特定部分。 完整的 XPath 語法不支援在此情況下擷取資料流處理，並讀取器必須因此一律逐步往前。 這也是為什麼在**訊息** 索引標籤，它會呼叫 路徑-內容由內文路徑定位 而不是"XPath-內容由內文路徑定位 」。  
  
 在接收端，使用路徑運算式，指出資料的讀取自 WCF 訊息的方式。 用於輸入訊息，BizTalk 訊息內容取得替代路徑陳述式所擷取的特定項目。 配接器會使用此路徑運算式，找出並擷取 BizTalk 訊息所需的資料。  
  
 在傳送端，使用範本來建立 WCF 訊息從 BizTalk 訊息。 對於輸出訊息的 [範本] 選項可允許 XPath 選項完全相反。 在 WCF 配接器組態中，XML 程式碼片段會作為基礎的外寄訊息的結構。 BizTalk 訊息的內容會在執行階段插入這個結構。  
  
 外寄訊息，您也必須選擇使用 [節點編碼] 設定，從 XML、 Base64、 字串或十六進位寫入之項目的類型。 當您想要擷取 WCF 訊息中所包含的二進位資料流，此選項是很有幫助。 使用這項功能會指示 WCF 配接器使用 WCF 訊息本文讀取裝置上的 ReadContextAsBase64 呼叫。 此呼叫可讓要讓使用此功能的二進位資料可以直接從移動 WCF 傳輸到 BizTalk MessageBox 資料庫直接透過 XmlReader API，讀取的二進位資料。 藉由將路徑寫入包含二進位資料的節點可以拉出，並將它放入 BizTalk 訊息。  
  
## <a name="how-do-you-access-wcf-message-properties-within-an-incoming-wcf-message"></a>您要如何存取內送 WCF 訊息內的 WCF 訊息屬性？  
 若要存取內送 WCF 訊息內的屬性，它會轉換為 BizTalk 訊息之前，您可以使用自訂的 WCF 通道元件或服務模型與 WCF 行為的擴充點。 例如， **IDispatchMessageInspector**物件。 BizTalk Wcf-custom 和 Wcf-customisolated 配接器提供簡單的方法，讓您的應用程式，可插入至使用的 WCF 行為的威力**行為**索引標籤中**傳輸屬性**對話方塊這些介面卡。  
  
 若要允許 WCF 訊息可供 WCF 配接器的屬性，這些屬性必須先寫入至訊息本文或標頭做為內容。 標頭會複製到 BizTalk 訊息內容會自動為您。 如果您想要升級的屬性值，您可以使用自訂的 BizTalk 管線元件先將 WCF 訊息屬性升級至 BizTalk 訊息內容中，從**IComponent： 執行**方法。 使用 WCF 自訂配接器自訂 WCF 行為，可讓您利用 WCF 及 BizTalk 功能更強大且富彈性，讓您的解決方案的擴充性。 WCF 配接器可讓您結合現有的 BizTalk 和 WCF extensibilities 來解決問題。  
  
 好消息是這個通用的屬性大小寫的 WCF 配接器中沒有捷徑。 您無須撰寫這兩個擴充性文本的內容，而只要讓 WCF 延伸模組去新建 WCF 配接器可理解的「已知」屬性即可。  
  
 若要撰寫或升級至 BizTalk 訊息內容的 SOAP 標頭值，將 WCF 訊息必須包含屬性名稱和命名空間所組成的值組的集合。 這可讓 WCF 配接器可辨識的標頭值要寫入或升級。  
  
 WCF 訊息必須包含下列訊息屬性，WCF 配接器才能將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容：  
  
-   若要升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 配接器會尋找金鑰組**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote**和值**清單 < KeyValuePair\<XmlQualifiedName，物件\>>**. 使用此配對，WCF 配接器需要命名空間、 名稱和值**XmlQualifiedName**物件，並將它們用於升級的標頭值。  
  
-   若要寫入此項目，但不是升級，SOAP 標頭值到 BizTalk 訊息內容中，WCF 配接器會尋找金鑰組**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext**和值**清單 < KeyValuePair\<XmlQualifiedName，物件\>>。** 使用此配對，WCF 配接器便可將值寫入訊息內容。  
  
> [!NOTE]
>  升級的屬性也必須指定 BizTalk 屬性結構描述中才能被接受，BizTalk 執行階段。  
  
## <a name="you-have-an-existing-orchestration-or-send-port-etc-that-expects-a-biztalk-multipart-message-how-can-you-get-a-multipart-message-in-the-wcf-scenario"></a>您有現有的協調流程 （或傳送埠等），必須要有多部分 BizTalk 訊息。 您要如何在 WCF 案例中取得多部分訊息？  
 多部分 BizTalk 訊息是由一或多個訊息部分所組成。 不過，WCF 會有沒有多部分訊息的概念。 因為 WCF 不會使用多部分訊息，BizTalk WCF 配接器也不會使用它們。 問題是您可能有現有的 BizTalk 協調流程或管線，以產生或取用多部分訊息會寫入。  
  
 如果您要進入 BizTalk Server 中的多部分訊息，使用內送 WCF 訊息和 WCF 配接器時，轉譯為 XML 多部分的資料，您的 WCF 訊息中。 開發自訂的 BizTalk 管線元件來處理內送的 XML 資料流 （WCF 訊息），並建立您的應用程式適當的 BizTalk 多部分訊息。 如有需要，可以完成這些步驟，傳送端的反向。