---
title: 在協調流程中使用 SOAP 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, creating
- SOAP headers, properties
- Web services, SOAP headers
- orchestrations, SOAP headers
- creating, SOAP headers
ms.assetid: 4754dd23-386b-4093-8ea4-4da6b4d9279c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faae7013c824926adea67feab296e1993f93e326
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288534"
---
# <a name="using-soap-headers-in-orchestrations"></a>在協調流程中使用 SOAP 標頭
協調流程會使用屬性結構描述來定義 SOAP 標頭內容屬性。 您可以使用 BizTalk 編輯器設定 SOAP 標頭內容屬性。  
  
## <a name="defining-soap-header-context-properties-with-property-schemas"></a>使用屬性結構描述定義 SOAP 標頭內容屬性  
 您需要屬性結構描述，才能在協調流程中使用已定義的 SOAP 標頭內容屬性。 屬性結構描述必須有目標命名空間**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**，而**Property Schema Base**屬性設定為**MessageContextPropertyBase**。 屬性結構描述中的各根項目名稱，必須符合已定義 SOAP 標頭中的根項目名稱。 您接著便可以使用屬性結構描述的命名空間和屬性名稱，來設定內容屬性的值。  
  
> [!NOTE]
>  屬性結構描述的命名空間是不同的目標結構描述命名空間 (**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**)。 雖然您的命名空間可以是任何字串，但通常會預設為專案名稱。  
  
 下列程式碼顯示指定 SOAP 標頭內容屬性的屬性結構描述命名空間所在**SOAPHeader**與屬性名稱的**OrigDest**:  
  
```  
requestMessageInstance(SOAPHeader.OrigDest) = stringVar;  
```  
  
 如需屬性結構描述和內容屬性的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。  
  
## <a name="using-biztalk-editor-to-set-soap-header-context-properties"></a>使用 BizTalk 編輯器設定 SOAP 標頭內容屬性  
 針對協調流程，SOAP 標頭內容屬性會設為包含 XML 資料的字串。 設定這些字串時，使用 BizTalk 運算式編輯器**訊息指派**或**運算式**圖形。  
  
 下列範例說明設定內容屬性的字串：  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = "<?xml version=\"1.0\"?>  
<OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
<Origination>Home</Origination>  
<Destination>Work</Destination>  
</OrigDest>"  
```  
  
## <a name="using-biztalk-editor-to-create-an-instance-of-a-soap-header-root-element"></a>使用 BizTalk 編輯器建立 SOAP 標頭根項目的執行個體  
 要將 SOAP 標頭設定為正確的字串，可能並不容易。 將 Web 參考加入到 BizTalk 專案時，所有複雜的 Web 訊息部分都會當做根項目加入到 Reference.xsd 中。 Reference.xsd 還包含每個已定義的 SOAP 標頭的根項目。 為確保您使用正確的字串設定 SOAP 標頭，請使用 BizTalk 編輯器為 Reference.xsd 建立 SOAP 標頭根項目的執行個體。 您可以直接使用產生的執行個體資料，或使用執行個體資料來包含實際的資料。  
  
 如需有關如何使用 BizTalk 編輯器產生執行個體資料的詳細資訊，請參閱[如何產生執行個體訊息](../core/how-to-generate-instance-messages.md)。  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a>建立 XmlDocument 來設定內容屬性  
 您可以設定內容屬性，藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。 宣告類型的變數**XMLDocument**並指派 XML 資料。  
  
 下列範例示範如何設定宣告型別的變數**XMLDocument**並指派 XML 資料：  
  
```  
xmlDoc.LoadXml("<?xml version=\"1.0\"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination>Home</Origination><Destination>Work</Destination></OrigDest>");  
```  
  
 下列範例說明如何設定內容屬性：  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = xmlDoc.OuterXml;  
```  
  
 如需有關如何使用 BizTalk 運算式編輯器的詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。 如需呼叫.NET 類別的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
## <a name="creating-soap-headers-for-a-soap-request"></a>建立 SOAP 要求的 SOAP 標頭  
 建立 SOAP 要求的 SOAP 標頭時，您必須確定建立的 SOAP 標頭是否正確無誤。 SOAP 配接器不會驗證 SOAP 標頭內容屬性的內容。  
  
> [!NOTE]
>  如果 SOAP 標頭不正確，BizTalk 將無法傳送 SOAP 要求至 Web 服務。  
  
 BizTalk 傳回 Web 服務的 SOAP 回應可能也包含 SOAP 標頭。 您只能存取其中已定義的 SOAP 標頭。  
  
> [!NOTE]
>  已使用的 Web 服務只支援已定義的 SOAP 標頭。  
  
 如需定義的 SOAP 標頭的詳細資訊，請參閱[使用 SOAP 標頭](../core/using-soap-headers.md)。 將回應 SOAP 標頭設定為內容屬性所使用的語法，與設定要求 SOAP 標頭的語法相同。  
  
 下列程式碼說明如何存取回應 SOAP 標頭：  
  
```  
stringVar = ResponseMessageInstance(SOAPHeader.OrigDest);  
```  
  
 內容屬性中包含的值是包含 XML 資料的字串。 設定這些字串時，使用 BizTalk 運算式編輯器**訊息指派**或**運算式**圖形。 您可以將字串載入**XmlDocument**並使用 XPath 查詢來存取特定欄位。  
  
 如需在 [BizTalk 運算式編輯器] 中建立 XML 文件的詳細資訊，請參閱[XLANG 的語言](../core/xlang-s-language.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XLANG 的語言](../core/xlang-s-language.md)   
 [SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md)