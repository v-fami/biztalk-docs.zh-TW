---
title: "存取協調流程中的 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, properties
- orchestrations, SOAP headers
ms.assetid: 91fe053a-3f16-497c-b4bb-5fb54bec62e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 516b2bcc57bef507a028f30c61fd329a5fd7a598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-soap-headers-in-orchestrations"></a>在協調流程中存取 SOAP 標頭
您可以在協調流程中，存取定義和未知之 SOAP 標頭的 SOAP 標頭內容屬性。 如需屬性結構描述和內容屬性的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。  
  
## <a name="defined-soap-header-context-properties"></a>已定義的 SOAP 標頭內容屬性  
 在協調流程中定義的 SOAP 標頭內容屬性需要屬性結構描述。 屬性結構描述必須有目標命名空間**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**，而**Property Schema Base**屬性設定為**MessageContextPropertyBase**。 屬性結構描述中的每個根項目名稱必須符合定義的 SOAP 標頭的根項目名稱。 然後，您可以存取使用的命名空間屬性結構描述和屬性名稱的內容屬性的值。 屬性結構描述的命名空間會與上面所列的目標命名空間不同。 雖然屬性結構描述的命名空間可以是任何字串，則通常會預設為專案的名稱。  
  
 下列範例將示範存取 SOAP 標頭內容屬性，屬性結構描述命名空間**SOAPHeader**，和屬性名稱**OrigDest**:  
  
```  
stringVar = requestMessageInstance(SOAPHeader.OrigDest);  
```  
  
> [!NOTE]
>  已定義的 SOAP 標題會視為 "in" 或 "out" 標頭。 若精靈為要求和回應訊息定義相同的 SOAP 標頭，就不會自動在回應中傳回內送的值。 您必須以明確的方式，將要求訊息的 SOAP 標頭內容屬性複製至回應訊息的 SOAP 標頭內容屬性。  
  
## <a name="copying-soap-header-context-property-of-incoming-message"></a>複製內送訊息的 SOAP 標頭內容屬性  
 您可將內送訊息的 SOAP 標頭內容屬性複製至回應訊息的同一個 SOAP 標頭內容屬性。  
  
 下列是複製 SOAP 標頭內容屬性的範例：  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = RequestMessageInstance(SOAPHeader.OrigDest);  
```  
  
 建立 SOAP 回應的 SOAP 標頭時，請確定是否正確地建立 SOAP 標頭。 SOAP 配接器不會驗證 SOAP 標頭內容屬性的內容。 若回應 SOAP 標頭的值不正確，SOAP 配接器便無法將回應訊息傳送給 Web 服務的取用者。  
  
## <a name="unknown-soap-header-context-property"></a>未知的 SOAP 標頭內容屬性  
 未知的 SOAP 標頭內容屬性不需要屬性結構描述。 您可以存取此全域內容屬性**SOAP。UnknownHeaders**。  
  
 下列範例將示範存取未知的 SOAP 標頭內容屬性**SOAP。UnknownHeaders**:  
  
```  
stringVar = RequestMessageInstance(SOAP.UnknownHeaders);  
```  
  
 內容屬性中包含的值是包含 XML 資料的字串。 若要存取此資料最簡單的方式是使用 BizTalk 運算式編輯器，在**訊息指派**或**運算式**圖形，並將字串載入**XmlDocument**並使用若要存取特定欄位的 XPATH 查詢。 在 BizTalk 運算式編輯器 」 中建立 XML 文件的詳細資訊，請參閱[XLANG 的語言](../core/xlang-s-language.md)。  
  
 內容屬性與特定的訊息有關聯。 「 傳訊引擎不會自動對應已知 SOAP 標頭從要求訊息給回應訊息的值。 在建立 Web 服務的回應訊息時，您必須特別設定 SOAP 標頭值。 下列命令是設定 SOAP 標頭內容屬性的最簡單的方法：  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = "<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination xmlns=\"\">Home</Origination><Destination xmlns=\"\">Work</Destination> </OrigDest>"  
```  
  
 您也可以達到這藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。  
  
> [!NOTE]
>  如果**SOAP。UnknownHeaders**屬性為 null，BizTalk 會自動傳回未知的 SOAP 回應的 SOAP 要求中收到的標頭。 如果**SOAP。UnknownHeaders**回應訊息上的內容屬性不是 null，則 BizTalk 會將該值傳回至 SOAP 回應。  
  
## <a name="see-also"></a>另請參閱  
 [SOAP 標頭與已發佈的 Web 服務](../core/soap-headers-with-published-web-services.md)