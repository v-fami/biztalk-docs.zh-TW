---
title: "擷取和訊息修復擴充解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages, errors
- code samples, errors
- errors, code sample
- repairing messages, code sample
- ErrorCollection objects
ms.assetid: 93f463a0-ecff-4f3e-a145-7c506f42c767
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb2f5fb1960a149c96a179ba596c67c9f402016
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-solution-for-capture-and-message-repair"></a>擷取和訊息修復擴充解決方案
在此說明中的 MT103 端對端教學課程會示範如何建構 BizTalk 協調流程訂閱失敗 SWIFT 的訊息。  
  
 MT103 端對端教學課程中的協調流程會使用協助程式類別的靜態方法**ErrorExtractor**，以從訊息中的錯誤部分和主體擷取為字串。 協調流程接著會寫入至不同的檔案部分。  
  
 因為錯誤部份的失敗訊息的序列化**ErrorCollection**管線元件所建構，您可以還原序列化集合並用它來自動化多個錯誤報告和處理。 下列[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]程式碼片段說明如何還原序列化失敗訊息的錯誤訊息部分，並逐一查看集合中的剖析錯誤。 程式碼片段會省略命名空間限定性條件來提高可讀性：  
  
```  
// instantiate an appropriate XmlTextReader  
// xm contains the message  
string sError = ErrorExtractor.GetErrorPartAsString(xm);  
StringReader sRdr = new StringReader(sError);  
XmlTextReader xRdr = new XmlTextReader(sRdr);  
  
// deserialize the collection  
ErrorCollection eC = ErrorCollection.GetErrorCollection(xRdr);  
  
// loop over the parsing errors in the collection  
IEnumerator pEnum = eC.GetParseErrorEnumerator();  
while(pEnum.MoveNext())   
{  
  // pEnum.Current() returns a ParseError object for processing  
}  
  
```  
  
 **ErrorCollection**包含方法，用於逐一查看依類型以及來反覆查看集合中的錯誤的所有錯誤。 如需有關**ErrorCollection**，請參閱 ErrorCollection 成員。  
  
## <a name="see-also"></a>另請參閱  
 [失敗的訊息和 ErrorCollection 物件](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)