---
title: Web 服務使用時的考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea7038dc-4740-4c0a-b6a1-08bc22f42bc2
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa1bbb536890a518248f2b328de71172a5df7186
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997743"
---
# <a name="considerations-when-consuming-web-services"></a>使用 Web 服務的考量
本節提供您使用 Web 服務時應該納入考量的相關資訊。  
  
## <a name="using-two-underscore-characters-in-a-parameter-name"></a>在參數名稱中使用兩個底線字元  
 Web 方法的參數名稱不可以 "__" (兩個底線字元) 作為開頭。 以兩個底線字元作為開頭的名稱可能會建立無法為 XLANG/s 所支援 (亦即無法使用) 的 Web 訊息部分。  
  
## <a name="the-any-element-and-the-anyattribute-attributes-are-not-supported-in-web-methods"></a>Web 方法不支援 any 項目與 anyAttribute 屬性  
 您無法使用**任何**項目或**anyAttribute** Web 方法的結構描述中的屬性。  
  
## <a name="using-xlangs-keywords"></a>使用 XLANG/s 關鍵字  
 Web 服務名稱或 Web 方法名稱不能是 XLANG/s 中的關鍵字。 如果在 Web 服務名稱或是 Web 方法名稱中使用 XLANG/s 關鍵字，當您新增 Web 服務時就會出現編譯錯誤。 如需 XLANG/s 語言保留字的清單，請參閱 < [xlang-s 保留字](../core/xlang-s-reserved-words.md)。  
  
## <a name="required-xlangs-support-for-parameter-types"></a>參數類型必要的 XLANG/s 支援  
 使用非 XLANG/s 支援的 Web 方法參數類型將會造成編譯錯誤。 例如，BizTalk Server 不支援包含結構描述類型之單一維度陣列的參數。 此外，BizTalk Server 不支援多維度陣列。 如需在 BizTalk Server 的 XLANG/s 語言保留的字組的清單，請參閱[xlang-s 保留字](../core/xlang-s-reserved-words.md)。  
  
## <a name="avoiding-compilation-errors-caused-by-adding-web-references-containing-c-keywords-or-identifiers"></a>避免因為加入包含 C# 關鍵字或識別項的 Web 參考而造成的編譯錯誤  
 當您使用**加入服務參考**若要加入服務參考加入 BizTalk 專案，BizTalk Server 將會呼叫每個 Web 方法至結構描述所需的結構描述類型。 BizTalk Server 會將這些結構描述加入到 Reference.xsd 中。 如果您的結構描述包含 C# 關鍵字的項目名稱，或者項目名稱不是有效的 C# 識別項，便可能會產生執行階段錯誤。 為了避免執行階段錯誤，請確定您使用的 Web 服務不包含 C# 關鍵字項目名稱或是無效的 C# 識別項。  
  
## <a name="multiple-serviceport-type-definitions-are-unsupported"></a>不支援多個服務/連接埠類型定義  
 BizTalk Server 支援使用單一服務與連接埠類型定義來新增 Web 服務檔。 如果您使用多個服務與連接埠類型定義來新增 WSDL 檔案，可能會出現下列錯誤：  
  
 無法產生 BizTalk 檔案。 物件參考未設定為物件的執行個體。  
  
## <a name="support-for-consuming-arrays-exposed-by-web-services"></a>支援使用 Web 服務所公開的陣列  
 BizTalk Server 可以使用由 Web 服務所公開，但不屬於 BizTalk Web 服務的一維與不規則陣列。 如需如何使用 Web 服務陣列的詳細資訊，請參閱[如何取用 Web 服務陣列](../core/how-to-consume-web-service-arrays.md)。  
  
> [!NOTE]
>  不支援多維度陣列語法。 例如， `MyArray[1,5]`。  
  
> [!NOTE]
>  BizTalk Server 不支援使用各種**資料集**Web 服務所公開的物件。 XLANG/s 子服務原本即支援 .NET DataSet 類別，但是如果您建立了 BizTalk 專案，其中包含了將 .NET DataSet 物件陣列公開的 Web 服務之 Web 參考，則當您嘗試編譯專案時，會產生錯誤。  
  
## <a name="web-method-parameters-must-be-xml-serializable"></a>Web 方法參數必須為可序列化的 Xml  
 在使用的 Web 服務中，所有參數都必須是可序列化的 XML。 如果您新增的 Web 方法中，包含的參數為不可序列化的 Xml，就會產生下列錯誤訊息：  
  
 System.Xml.Element 必須是可序列化的 XML，才能做為訊息部分類型。  
  
> [!NOTE]
>  資料型別**XmlDocument**並**資料集**，不可序列化的 Xml，同時支援。  
  
## <a name="consuming-messaging-only-web-services"></a>使用僅供傳訊的 Web 服務  
 使用僅供傳訊的 Web 服務時，所有的 BizTalk 訊息內文部分名稱都必須符合 Web 方法參數名稱。 例如，如果 Web 服務的簽章為 `WebMethod(MyType1 type1, MyType2 type2)`，則部分名稱必定為 type1 與 type2，且可能發生下列執行階段錯誤：  
  
 無法擷取參數 %1 的訊息部分  
  
 如需詳細資訊，請參閱 <<c0> [ 如何取用 Web 服務通訊只能在情節中](../core/how-to-consume-web-services-in-a-messaging-only-scenario.md)。  
  
## <a name="configuring-a-soap-send-port-programmatically"></a>使用程式來設定 SOAP 傳送埠  
 您可以在訊息內容中，使用程式來設定組態屬性。 不管傳送埠是靜態還是動態，您都可以在協調流程或自訂的管線元件中設定這些屬性。  
  
> [!NOTE]
>  若要設定**MethodName**屬性的靜態 SOAP 傳送埠以程式設計方式，您需要設定**方法名稱**來 **[稍後指定]** 在**Web服務**索引標籤**SOAP 傳輸屬性**BizTalk Server 管理主控台中的對話方塊。  
> 
>  如需詳細資訊**MethodName**屬性，請參閱[如何動態設定取用 Web 服務的 URI](../core/how-to-dynamically-set-the-uri-of-a-consumed-web-service.md)。  
> 
>  如需詳細資訊**SOAP 傳輸屬性** 對話方塊中，請參閱**SOAP 傳輸屬性對話方塊、 Web 服務**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="property-rules"></a>屬性規則  
 如果組態屬性是設於接收管線的協調流程或自訂管線元件中，則會套用下列規則：  
  
- 若訊息傳送至靜態傳送埠，屬性值會以該傳送埠設定的值覆寫。  
  
- 若訊息傳送至動態傳送埠，則不會覆寫屬性值。  
  
  如果組態屬性是設於傳送管線的自訂管線元件中，則會套用下列規則：  
  
- 無論訊息是傳送至靜態或動態傳送埠，都不會覆寫值。 換言之，不管組態屬性設於何處，傳送管線元件都會覆寫組態屬性。  
  
- 如需有關自訂管線元件的詳細資訊，請參閱 <<c0> [ 開發自訂管線元件](../core/developing-custom-pipeline-components.md)。  
  
- 如需 SOAP 傳送配接器的組態屬性的詳細資訊，請參閱[如何以動態方式設定取用 Web 服務的 URI](../core/how-to-dynamically-set-the-uri-of-a-consumed-web-service.md)。  
  
## <a name="adding-a-web-reference-to-a-consumed-web-service-that-contains-a-multi-rooted-schema-will-cause-a-compilation-error"></a>將 Web 參考加入包含多重根目錄結構描述的已使用 Web 服務時，將會產生編譯錯誤  
 如果您針對由已發佈之 BizTalk 協調流程衍生出來的 Web 服務，將 Web 參考加入專案，且協調流程包括含有多重根目錄的結構描述，當您編譯專案時會產生錯誤。 如果您將 Web 參考加入由已發佈之 BizTalk 協調流程衍生出來的專案，請確定協調流程不包含任何多重根目錄的結構描述。  
  
## <a name="using-typeddatasets-as-parameters-to-web-methods"></a>使用 TypedDataSets 作為 Web 方法的參數  
 當您打算使用 TypedDataSets 作為 Web 方法的參數時，需要先進行下列事項來支援此操作：  
  
1. 將 Web 參考加入 C# 專案，然後產生 Proxy。  
  
2. 建立 SOAP 傳送埠，然後指定傳送埠上的 Proxy 並選擇方法。  
  
3. 在協調流程中，定義晚期繫結埠與訊息類型。 需要沒有屬性升級或辨別的欄位存取大部分的情況下，類型可以定義為**XMLDocument**。 選取使用此類型的 PassThrough 管線。  
  
4. 在 BizTalk Server 管理主控台中，在**Web 服務**索引標籤中**SOAP 傳輸屬性**對話方塊中的 soap 傳送埠時，指定您想要使用您所建立的 proxy。 您同時需要指定組件、類型與方法。 如需詳細資訊，請參閱 < **SOAP 傳輸屬性對話方塊、 Web 服務**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="adding-a-web-reference-to-a-consumed-web-service-that-contains-a-web-method-expecting-generic-based-parameters-will-cause-a-compilation-error"></a>將 Web 參考加入包含需要泛型參數之 Web 方法的已使用 Web 服務時，將會產生編譯錯誤  
 如果您將 Web 參考加入包含需要泛型參數 (例如空值參數) 之 Web 方法的 Web 服務專案，編譯專案時會產生錯誤。 不支援這個動作。 您必須使用明確特製化來呼叫 XLANG/s 的泛型類別。  
  
## <a name="biztalk-schema-generation-using-the-add-service-reference"></a>使用加入服務參考來產生 BizTalk 結構描述  
 當您使用**加入服務參考**若要加入服務參考加入 BizTalk 專案，BizTalk Server 將會呼叫每個 Web 方法至結構描述所需的結構描述類型。 BizTalk Server 會將這些結構描述加入到 Reference.xsd 中。 若要確保**加入服務參考**產生 BizTalk 結構描述正確，Web 服務必須符合下列方針：  
  
-   Web 方法應該包含**SoapDocumentMethodAttribute**而不是**SoapRpcMethodAttribute**。  
  
-   必須使用 web 服務和方法**常值**而不繫結**Encoded**這類 **[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**。  
  
-   Web 方法參數和傳回型別必須具有**XmlRootAttribute**的有效**命名空間**屬性除非它們是原生 XSD 類型與 XmlNode 類型。  
  
-   Web 方法不能使用**Soapdocumentmethodattribute**並**Requestnamespace**中的屬性**SoapDocumentMethodAttribute**。  
  
-   Web 服務必須符合 Web 服務互通性 (WSI) Basic Profile version 1.1。  
  
## <a name="xsd-will-not-contain-nodes-for-simple-parameter-types"></a>XSD 不會包含代表簡單參數類型的節點  
 當您新增 Web 參考且 Web 方法具有簡單類型的參數時，所產生的 XSD 將不會包含代表該參數的節點。 但是，所產生的 Multipart 訊息將會包含一個屬於該簡單類型的部分。 協調流程應該要適當處理此訊息部分。 如果該部分是 Web 服務要求的一部分，請使用訊息指派圖形，手動指派值給該部分。 如果該部分是 Web 服務回應的一部分，請在運算式圖形中手動存取該部分以查看值。  
  
## <a name="the-add-service-reference-do-not-support-the-web-services-description-language-wsdl-import-element"></a>「加入服務參考」功能不支援 Web 服務描述語言 (WSDL) Import 項目  
 當您將服務參考加入含有 Import 項目的 WSDL 檔案時，加入服務參考功能將無法運作。  
  
## <a name="see-also"></a>另請參閱  
 [建構 Web 訊息](../core/constructing-web-messages.md)