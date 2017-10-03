---
title: "規劃使用 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24863069-929b-4b0b-9643-073965fb5532
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a13151a5dd76b20b70872b963dc6a688370444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-consuming-web-services"></a>規劃使用 Web 服務
Web 服務的規劃可以分成兩個類別，規劃發佈 Web 服務，以及規劃使用 Web 服務。 本主題說明使用 Web 服務的考量。 如需發佈 Web 服務資訊，請參閱[Planning for Publishing Web Services1](../technical-guides/planning-for-publishing-web-services1.md)。  
  
 當您建立您的計劃，請記住下列：  
  
-   **在參數名稱中使用兩個底線字元**  
  
     Web 方法的參數名稱不可以 "__" (兩個底線字元) 作為開頭。 以兩個底線字元作為開頭的名稱可能會建立無法為 XLANG/s 所支援 (亦即無法使用) 的 Web 訊息部分。  
  
-   **Any 項目與 anyAttribute 屬性不支援 Web 方法**  
  
     您無法使用**任何**項目或**anyAttribute** Web 方法的結構描述中的屬性。  
  
-   **使用 XLANG/s 關鍵字**  
  
     Web 服務名稱或 Web 方法名稱不能是 XLANG/s 中的關鍵字。 如果在 Web 服務名稱或是 Web 方法名稱中使用 XLANG/s 關鍵字，當您新增 Web 服務時就會出現編譯錯誤。 如需 XLANG/s 語言保留字的清單，請參閱[XLANG/s 保留字](http://go.microsoft.com/fwlink/?LinkId=155765)(http://go.microsoft.com/fwlink/?LinkId=155765)。  
  
-   **必要的 XLANG/s 支援的參數型別**  
  
     使用非 XLANG/s 支援的 Web 方法參數的類型會造成編譯錯誤。 例如，BizTalk Server 不支援包含結構描述類型之單一維度陣列的參數。 此外，BizTalk Server 不支援多維陣列。 如需在 BizTalk Server 的 XLANG/s 語言保留字的清單，請參閱[XLANG/s 保留字](http://go.microsoft.com/fwlink/?LinkId=155765)(http://go.microsoft.com/fwlink/?LinkId=155765)。  
  
-   **避免加入 Web 參考包含 C# 關鍵字或識別項所造成的編譯錯誤**  
  
     當您使用**加入 Web 參考**若要加入 Web 參考加入 BizTalk 專案，BizTalk Server 將會呼叫每個 Web 方法至結構描述所需的結構描述類型。 BizTalk Server 會將這些結構描述加入到 Reference.xsd 中。 如果您的結構描述包含 C# 關鍵字的項目名稱，或者項目名稱不是有效的 C# 識別項，便可能會產生執行階段錯誤。 為了避免執行階段錯誤，請確定您使用的 Web 服務不包含 C# 關鍵字項目名稱或是無效的 C# 識別項。  
  
-   **多個服務/連接埠類型定義不受支援**  
  
     BizTalk Server 支援使用單一服務與連接埠類型定義來新增 Web 服務檔。 如果您使用多個服務與連接埠類型定義來新增 WSDL 檔案，可能會出現下列錯誤：  
  
     `Could not generate BizTalk files. Object reference not set to an instance of an object.`  
  
-   **支援使用 Web 服務所公開的陣列**  
  
     BizTalk Server 可以使用不是 BizTalk Server Web 服務的 Web 服務所公開的一維和不規則陣列。 如需如何使用 Web 服務陣列的詳細資訊，請參閱[如何取用 Web 服務陣列](http://go.microsoft.com/fwlink/?LinkId=155766)(http://go.microsoft.com/fwlink/?LinkId=155766)。  
  
    > [!NOTE]  
    >  不支援多維度陣列語法。 例如， *MyArray [1,5]*。  
  
    > [!NOTE]  
    >  BizTalk Server 不支援使用的陣列**資料集**Web 服務所公開的物件。 XLANG/s 子服務原本即支援.NET DataSet 類別，但如果您建立 BizTalk 專案，其中包含 Web 參考加入 Web 服務會公開.NET DataSet 物件的陣列，您就會發生錯誤，當您嘗試編譯專案。  
  
-   **Web 方法參數必須是可序列化的 Xml**  
  
     在使用的 Web 服務中，所有參數都必須是可序列化的 XML。 如果您新增的 Web 方法中，包含的參數為不可序列化的 Xml，就會產生下列錯誤訊息：  
  
     System.Xml.Element 必須是可序列化的 XML，才能做為訊息部分類型。  
  
    > [!NOTE]  
    >  資料型別**XmlDocument**和**資料集**，沒有可序列化的 Xml，同時支援。  
  
-   **使用僅限傳訊的 Web 服務**  
  
     取用僅限傳訊的 Web 服務時，所有的 BizTalk Server 訊息內文部分名稱必須符合 Web 方法參數名稱。 例如，如果 Web 服務的簽章為 `WebMethod(MyType1 type1, MyType2 type2)`，則部分名稱必定為 type1 與 type2，且可能發生下列執行階段錯誤：  
  
     `Failed to retrieve the message part for parameter %1`  
  
     如需詳細資訊，請參閱[取用 Web 服務在 Messaging-Only 案例如何](http://go.microsoft.com/fwlink/?LinkId=155767)(http://go.microsoft.com/fwlink/?LinkId=155767)。  
  
-   **以程式設計方式設定 SOAP 傳送埠**  
  
     您可以在訊息內容中，使用程式來設定組態屬性。 您可以在協調流程或自訂管線元件中設定這些屬性，是否傳送埠是靜態或動態。  
  
    > [!NOTE]  
    >  若要設定**MethodName**屬性靜態 soap 傳送埠以程式設計的方式，您需要設定**方法名稱**至**[稍後指定]**中**Web服務** 索引標籤**SOAP 傳輸屬性**] 對話方塊 [BizTalk Server 管理主控台中的。  
  
     如需有關**MethodName**屬性，請參閱[如何動態設定取用 Web 服務的 URI](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768)。  
  
-   **屬性規則**  
  
     如果組態屬性是設於接收管線的協調流程或自訂管線元件中，則會套用下列規則：  
  
    -   若訊息傳送至靜態傳送埠，屬性值會以該傳送埠設定的值覆寫。  
  
    -   若訊息傳送至動態傳送埠，則不會覆寫屬性值。  
  
     如果組態屬性是設於傳送管線的自訂管線元件中，則會套用下列規則：  
  
    -   無論訊息是傳送至靜態或動態傳送埠，都不會覆寫值。 換言之，不管組態屬性設於何處，傳送管線元件都會覆寫組態屬性。  
  
    -   如需自訂管線元件的詳細資訊，請參閱[開發自訂管線元件](http://go.microsoft.com/fwlink/?LinkId=155769)(http://go.microsoft.com/fwlink/?LinkId=155769)。  
  
    -   如需 SOAP 傳送配接器的組態屬性的詳細資訊，請參閱[如何動態設定取用 Web 服務的 URI](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768)。  
  
-   **加入 Web 參考加入包含多重根目錄結構描述將導致編譯錯誤的已使用的 Web 服務**  
  
     如果您新增 Web 參考加入專案，以衍生自發佈 BizTalk 協調流程 Web 服務，且協調流程包含具有多個根節點的結構描述，然後會發生錯誤，編譯專案時。 如果您將 Web 參考加入由已發佈之 BizTalk 協調流程衍生出來的專案，請確定協調流程不包含任何多重根目錄的結構描述。  
  
-   **使用 TypedDataSets 作為 Web 方法的參數**  
  
     當您打算使用 TypedDataSets 作為 Web 方法的參數時，需要先進行下列事項來支援此操作：  
  
    1.  將 Web 參考加入 C# 專案，然後產生 Proxy。  
  
    2.  建立 SOAP 傳送埠，然後指定傳送埠上的 Proxy 並選擇方法。  
  
    3.  在協調流程中，定義晚期繫結埠與訊息類型。 需要沒有屬性升級或辨別的欄位存取大部分的情況下，可以定義型別為**XMLDocument**。 選取使用此類型的 PassThrough 管線。  
  
    4.  在 BizTalk Server 管理主控台中，在**Web 服務**索引標籤中**SOAP 傳輸屬性**對話方塊中的 soap 傳送埠時，指定您想要使用您建立該 proxy。 您同時需要指定組件、類型與方法。  
  
-   **加入 Web 參考加入包含需要泛型參數將導致編譯錯誤之 Web 方法的已使用的 Web 服務**  
  
     如果您加入 Web 參考加入包含需要泛型為基礎的參數，例如可為 null 的參數之 Web 方法的 Web 服務專案，編譯專案時，會發生錯誤。 不支援這個動作。 您必須使用明確特製化來呼叫 XLANG/s 的泛型類別。  
  
-   **使用 加入 Web 參考產生 BizTalk 結構描述**  
  
     當您使用**加入 Web 參考**若要加入 Web 參考加入 BizTalk 專案，BizTalk Server 將會呼叫每個 Web 方法至結構描述所需的結構描述類型。 BizTalk Server 會將這些結構描述加入到 Reference.xsd 中。 若要確保**加入 Web 參考**產生 BizTalk 結構描述正確，Web 服務必須符合下列指導方針：  
  
    -   Web 方法應該包含**SoapDocumentMethodAttribute**而不是**SoapRpcMethodAttribute**。  
  
    -   Web 服務和方法必須使用**常值**繫結，而不**Encoded**例如**[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**。  
  
    -   Web 方法參數和傳回型別都必須有**XmlRootAttribute**的有效**命名空間**屬性除非它們是原生 XSD 類型與 XmlNode 類型。  
  
    -   Web 方法不能使用**RequestNamespace**和**ResponseNamespace**中的屬性**SoapDocumentMethodAttribute**。  
  
    -   Web 服務必須符合 Web 服務互通性 (WSI) Basic Profile version 1.1。  
  
-   **加入 Web 參考不支援 Web 服務描述語言 (WSDL) Import 項目**  
  
     當您將 Web 參考加入含有 Import 項目的 WSDL 檔案時，加入 Web 參考功能將無法運作。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)