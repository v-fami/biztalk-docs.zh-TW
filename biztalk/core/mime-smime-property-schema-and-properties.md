---
title: "MIME SMIME 屬性結構描述和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26dd25b9-7eb8-4354-9929-dc1985dd1d77
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 882b25733a46b8b7b973c992d465132df4c47b75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mime-smime-property-schema-and-properties"></a>MIME SMIME 屬性結構描述和屬性

## <a name="namespace-properties"></a>命名空間屬性
**http://schemas.microsoft.com/BizTalk/2003/mime-properties**命名空間包含可用來設定 MIME/SMIME 編碼器管線元件的訊息和部分內容屬性的屬性。 MIME/SMIME 編碼器使用這些屬性在建立的訊息中產生適當的 MIME/SMIME 標頭。 下表描述這些 MIME/SMIME 屬性。  
  
|屬性|範圍。|類型|Description|  
|--------------|-----------|----------|-----------------|  
|**FileName**|每個訊息部分|xs:string|設定 MIME/SMIME 部分的檔案名稱標頭。|  
|**ContentID**|每個訊息部分|xs:string|設定 MIME/SMIME 部分的 Content-ID 標頭。|  
|**ContentDescription**|每個訊息部分|xs:string|設定 MIME/SMIME 部分的 Content-Description 標頭。|  
|**ContentTransferEncoding**|每個訊息部分|xs:string|設定產生的 MIME/SMIME 部分之 Content-Transfer-Encoding 標頭。<br /><br /> 這個值會覆寫**內容轉移編碼**管線設計師 」 中設定的值。 若為 Multipart 訊息，您可以針對不同的 MIME/SMIME 部分使用不同的編碼。|  
|**ContentLocation**|每個訊息部分|xs:string|設定產生的 MIME/SMIME 部分之 Content-Location 標頭。|  
|**IsMIMEEncoded**|每個訊息部分|xs:boolean|指定訊息是否有 MIME/SMIME 內容。 MIME 元件會寫入此值，因此無需設定。|  
  
 MIME/SMIME 編碼器也會使用下列部分屬性**系統**命名空間。  
  
|屬性|型別|Description|  
|--------------|----------|-----------------|  
|ContentType|xs:string|對應至產生的 MIME/SMIME 部分之 Content-Type 標頭。|  
|FileName|xs:string|對應至檔案名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)   
 **訊息內容屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]