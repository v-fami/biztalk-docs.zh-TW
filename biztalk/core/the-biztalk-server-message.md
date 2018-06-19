---
title: BizTalk Server 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, properties
- messages, about messages
ms.assetid: 6048c191-b495-4fdc-b547-e3e322340a49
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4fd150a0b93cac10c4d1f79a526846629c62e67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279894"
---
# <a name="the-biztalk-server-message"></a>BizTalk Server 訊息
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的核心為訊息處理引擎。 若要瞭解 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的詳細資料，則有必要瞭解訊息，以及 BizTalk Server 如何顯示、儲存和處理它們。 在您瞭解何謂訊息之後，就會比較容易理解 BizTalk Server 如何使用訊息的詳細資料。  
  
 BizTalk Server 中的每個訊息都會視為多部分訊息，並由零或多個部分所組成。 具有一或多個部分的每個訊息都有一個部分會識別為內文部分。 每個部分都是由資料的二進位區塊所組成，這些區塊代表 XML 文件、一般檔案、序列化的 .NET 類別，或是資料的其他二進位資料流。 您可以使用訊息的內文部分，來識別可用以路由的訊息類型。  
  
 您必須瞭解一個非常重要的概念，就是所有的訊息在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中是不變的。 這表示在建構訊息之後，便無法變更。 在將它放入 MessageBox 資料庫之後，即會將訊息視為已建構。 任何對訊息的變更都需要建立新訊息，並從該點以後改為使用它。 這在「協調流程設計師」中特別明顯，在此編譯規則會強制您遵循在使用訊息之前先建構它的嚴格指導方針，而且不允許在其建構區塊之外修改訊息。 若您想要變更訊息，就必須建立一個建立相同類型之訊息的新建構區塊，將原始訊息複製到新訊息，然後在離開建構區塊之前對新訊息進行變更。  
  
## <a name="message-properties"></a>訊息屬性  
 除了構成訊息的部分，在系統中的每個訊息都有一組屬性，從而中所謂的*訊息內容*。 這些屬性可能是從訊息擷取的值，或者是與訊息本身相關的值。 例如，配接器會將屬性放入與接收訊息相關的內容中，例如，接收訊息的位置，以及用以接收訊息的配接器類型。 請將屬性寫入至內容，或*升級*至內容。 這兩個選項的差異在於，升級屬性可以做為訊息路由中的準則，而寫入的屬性則不行。  
  
 將值寫入或升級為內容的概念與在 BizTalk 編輯器中升級屬性的概念相關，但不相同。 在 BizTalk 編輯器中，結構描述中的項目或屬性可標示為升級屬性或辨別欄位。 訊息結構描述中以 PropertyField 註解標示的項目，會導致管線解譯器在內容中放置「升級」屬性。 訊息結構描述中以 DistinguishedField 註解標示的項目，會導致管線解譯器在內容中放置「寫入」屬性。  
  
 升級屬性的設計的設計開始*訊息相互關聯*: 能夠將收到訊息與已執行的協調流程執行個體建立關聯性。 如為相互關聯，則需要定義屬性或屬性集，以便在協調流程中的訊息之間提供連結。 例如，在採購程序中，您需要根據 PurchaseOrderID 相互關聯訊息。 然而，在許多商業案例中，訊息中特定欄位或屬性的名稱可能不相符。 訂購單結構描述可能會有名為 POId 的項目，而隨附的發票結構描述可能會有名為 OrderID 的項目。 若要在具名屬性 (在此情況中為 PurchaseOrderID) 上相互關聯訊息，開發人員必須能夠從值的來源擷取要相互關聯的屬性名稱。 屬性結構描述支援此擷取。  
  
 A*屬性結構描述*可讓您定義升級的屬性的一般位置，並讓其他結構描述參考它們。 就像其他結構描述一樣，屬性結構描述也有命名空間，但與其他結構描述不同的是，它只能有定義的項目 (而不是記錄或屬性)。 在屬性結構描述中定義的每個項目都具有名稱與型別。 因為可能會有一個以上的結構描述參考屬性結構描述，而且因為屬性結構描述中的資訊必須在執行階段供元件使用，所以必須將屬性結構描述部署到 BizTalk Server 中，就像所有其他的結構描述一樣。 除了一般結構描述部署步驟之外，還會擷取升級屬性的相關資訊，並將它儲存在管理資料庫的 bts_documentSpec 資料表中。  
  
 建立屬性結構描述之後，項目和屬性具有相同輸入 （例如。 整數），可升級為屬性結構描述中的具名屬性的其中一個。  
  
 **若要完成上述範例，開發人員會執行下列步驟，以定義相互關聯所需的共用的屬性。**  
  
1.  建立屬性結構描述，並定義名為 PurchaseOrderId 且型別為 xs:int 的項目。  
  
2.  建立 PurchaseOrder 結構描述，並新增名為 POId 且型別為 xs:int 的項目或屬性。  
  
3.  使用 BizTalk 編輯器中的顯示升級命令時，開發人員可將 POId 欄位新增至升級屬性清單，並指出應該從清單選取 PurchaseOrderId 具名屬性，以便將它升級為屬性結構描述中定義的 PurchaseOrderId 屬性。  
  
4.  建立發票結構描述，並新增名為 OrderId 且型別為 xs:int 的項目或屬性。  
  
5.  使用 BizTalk 編輯器中的顯示升級命令時，開發人員可將 OrderId 欄位新增至升級屬性清單，並指出是否應該從清單選取 PurchaseOrderId 具名屬性，以便將它升級為屬性結構描述中定義的 PurchaseOrderId 屬性。  
  
 現在此定義已存在於文件結構描述中，管線元件就可以將 OrderId 與 POId 適當地升級為具名屬性 PurchaseOrderID，這樣就可將它用於路由和相互關聯。 如需此升級程序的詳細資訊，請參閱本文件中的＜訊息升級＞主題。  
  
 升級屬性的其中一項優點就是已升級的項目值可在訊息內容中使用。 這表示接收該值是經濟的，因為它不需要將訊息載入記憶體中，就能在訊息上執行 XPath 陳述式。 而是使用簡單的屬性包及索引鍵來取得該值。 這種行為比訊息路由更能為大部分的情況所接受，而且也是建立辨別欄位的充分理由。 升級屬性會升級為訊息內容，而辨別欄位則會寫入至訊息內容。 不過，與升級屬性不同的是，辨別欄位沒有屬性結構描述。 這也是為何辨別欄位不能用於路由，而且也無法在傳送埠或協調流程接收圖形中做為篩選準則來使用。 不過，辨別欄位也可用於協調流程中，以便在訊息內容中讀取或寫入值，而不需將訊息載入至記憶體中並擷取值。  
  
 除了將屬性升級為或是寫入至訊息內容之外，也可以將訊息屬性新增至內容中。 訊息屬性在 BizTalk Server 中是一種安全性措施，並提供關於訊息的內容資訊，它必須符合為路由訊息的目的地之主控件所指定的值。 此安全性措施可讓您用這種方式來設定 BizTalk Server 環境：允許特定主控件做為可接收和處理特定訊息的唯一主控件。 舉例來說，在 [BizTalk Server 管理主控台] 中，可以使用憑證指紋來設定主控件，以用於訊息解碼和解密。 設定此屬性會為 MesageBox 中的該主控件建立應用程式屬性。 使用此指紋來接收和加密的安全訊息，接著只會路由至已設定指紋的主控件。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段架構](../core/runtime-architecture.md)