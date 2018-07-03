---
title: 錯誤擷取程式範例類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Error Extractor Sample class
- errors, Error Extractor Sample class
ms.assetid: d0d59b21-d80a-4466-a77a-1d3b7df1bc2a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1085af05221b252bb6942e2c32bbe1f91c8d7688
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010767"
---
# <a name="error-extractor-sample-class"></a>錯誤擷取程式範例類別
Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]解譯器會序列化為 XML 物件，錯誤，並將 XML 物件附加至多部分訊息的錯誤區段。 反組譯工具接著會將失敗的訊息發佈到 MessageBox 資料庫，就像一樣是有效的訊息。 因此，無法至 MessageBox 資料庫的訊息包含錯誤詳細資料。 您可以使用錯誤擷取程式範例類別，來擷取失敗的訊息中的錯誤詳細資料，並產生一個檔案包含錯誤詳細資料和另一個具有原始訊息的檔案。  
  
> [!IMPORTANT]
>  錯誤擷取程式範例類別是在 SDK 中的範例程式碼。 它並不適用於實際執行時使用。  
  
 若要使用錯誤擷取程式範例類別，您必須建立協調流程以處理失敗的訊息。 此協調流程包括失敗訊息的主體擷取、 擷取錯誤訊息的一部分失敗，並接著撰寫本文及到不同的 XML 檔案的錯誤部分的步驟。 協調流程會代表每個步驟中 「 運算式 」 階段錯誤擷取程式範例類別中呼叫一或多個下列方法：  
  
## <a name="getbodypartasstring-method"></a>GetBodyPartAsString 方法  
 這個方法會傳回字串，包含的 XML 位於訊息內文部分 XLANG 'xml'。 方法應包含的內文部分 XLANG 訊息 'xml' 呼叫 「 BodySegment。 」 因此，您必須宣告 'xml' 中呼叫的協調流程，使用此內文部分名稱。 如果 「 BodySegment"不存在 'xml'，過程**GetBodyPartAsString**會擲回例外狀況。  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetBodyPartAsString(XLANGMessage xm);  
```  
  
## <a name="geterrorpartasstring-method"></a>GetErrorPartAsString 方法  
 這個方法會傳回字串，包含的 XML 位於錯誤的 XLANG 訊息部分 'xml'。 方法應包含錯誤部分 XLANG 訊息 'xml' 呼叫 「 ErrorSegment。 」 因此，您必須宣告 'xml' 中呼叫的協調流程，此錯誤的組件名稱。 如果 「 ErrorSegment"不存在 'xml'，過程**GetErrorPartAsString**會擲回例外狀況。  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetErrorPartAsString(XLANGMessage xm);  
```  
  
## <a name="writetofile-method"></a>WriteToFile 方法  
 這個方法會寫入的字串*訊息*參數所指定的檔案*filePath*參數。  
  
```  
SWIFTErrorExtractor.ErrorExtractor.WriteToFile(string filePath, string message);  
```  
  
 A4SWIFT 安裝程式安裝錯誤擷取程式範例類別 (SWIFTErrorExtractor.dll) 在 A4SWIFT SDK 的一部分\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial\SWIFTErrorExtractor。 此資料夾也包含範例類別 (ErrorExtractor.cs) 的原始程式碼。  
  
 若要從協調流程呼叫 SWIFTErrorExtractor.dll，您必須發行至全域組件快取的.dll 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../adapters-and-accelerators/accelerator-swift/tools.md)