---
title: "錯誤抽選程式範例類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Error Extractor Sample class
- errors, Error Extractor Sample class
ms.assetid: d0d59b21-d80a-4466-a77a-1d3b7df1bc2a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53ceb305dcd30164e385022f66140fcaa626b133
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error-extractor-sample-class"></a>錯誤抽選程式範例類別
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]解譯器將序列化為 XML 物件，錯誤，並將 XML 物件附加至多部分訊息的錯誤區段。 解譯器接著會將失敗的訊息發佈到 MessageBox 資料庫，就像是有效的訊息。 因此，無法至 MessageBox 資料庫的訊息包含錯誤詳細資料。 您可以使用錯誤抽選程式範例類別從失敗的訊息中擷取錯誤詳細資料，以及產生一個檔案包含錯誤詳細資料和另一個具有原始訊息的檔案。  
  
> [!IMPORTANT]
>  錯誤抽選程式範例類別是 SDK 中的範例程式碼。 不適合在生產環境中使用。  
  
 若要使用錯誤抽選程式範例類別，您必須建立協調流程以處理失敗的訊息。 此協調流程包括步驟來擷取失敗訊息的本文、 擷取錯誤訊息的部分失敗，然後撰寫本文和錯誤組件到不同的 XML 檔案。 協調流程代表每個步驟中的一或多個下列方法會呼叫錯誤抽選程式範例類別中的運算式階段：  
  
## <a name="getbodypartasstring-method"></a>GetBodyPartAsString 方法  
 這個方法會傳回訊息內文部分 XLANG 'xml' 中找到的字串，包含的 XML。 在方法預期要包含的內文部分 XLANG 訊息 'xml' 稱為 「 BodySegment。 」 因此，您必須宣告 'xml' 中呼叫的協調流程中使用此內文部分名稱。 如果"BodySegment"不存在的 'xml'，一部分**GetBodyPartAsString**擲回例外狀況。  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetBodyPartAsString(XLANGMessage xm);  
```  
  
## <a name="geterrorpartasstring-method"></a>GetErrorPartAsString 方法  
 這個方法會傳回錯誤部分 XLANG 訊息 'xml' 中找到的字串，包含的 XML。 在方法預期 XLANG 訊息 'xml' 包含錯誤組件稱為 「 ErrorSegment。 」 因此，您必須宣告 'xml' 中呼叫的協調流程，此錯誤的組件名稱。 如果"ErrorSegment"不存在的 'xml'，一部分**GetErrorPartAsString**擲回例外狀況。  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetErrorPartAsString(XLANGMessage xm);  
```  
  
## <a name="writetofile-method"></a>WriteToFile 方法  
 這個方法會將字串從*訊息*參數所指定的檔案來*filePath*參數。  
  
```  
SWIFTErrorExtractor.ErrorExtractor.WriteToFile(string filePath, string message);  
```  
  
 A4SWIFT 安裝程式會安裝成 A4SWIFT SDK 中的一部分的錯誤抽選程式範例類別 (SWIFTErrorExtractor.dll) \<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial\SWIFTErrorExtractor。 此資料夾也包含範例類別 (ErrorExtractor.cs) 的原始程式碼。  
  
 若要從協調流程呼叫 SWIFTErrorExtractor.dll，您必須發佈至全域組件快取的.dll 檔案。  
  
## <a name="see-also"></a>請參閱  
 [工具](../../adapters-and-accelerators/accelerator-swift/tools.md)