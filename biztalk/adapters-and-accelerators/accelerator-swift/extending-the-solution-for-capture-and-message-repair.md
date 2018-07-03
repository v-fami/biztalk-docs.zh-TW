---
title: 延伸 Capture 和 Message Repair 的解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages, errors
- code samples, errors
- errors, code sample
- repairing messages, code sample
- ErrorCollection objects
ms.assetid: 93f463a0-ecff-4f3e-a145-7c506f42c767
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc2b4436906b1df913deec8b525143773dd43e4e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979639"
---
# <a name="extending-the-solution-for-capture-and-message-repair"></a>延伸 Capture 和 Message Repair 的解決方案
在此說明中的 MT103 端對端教學課程會示範如何建構 BizTalk 協調流程訂閱失敗 SWIFT 的訊息。  
  
 MT103 端對端教學課程中的協調流程會使用協助程式類別的靜態方法**ErrorExtractor**，以從訊息擷取錯誤的組件和本文為字串。 協調流程接著會寫入至不同的檔案部分。  
  
 因為錯誤部份的失敗訊息的序列化**ErrorCollection**建構管線元件，您可以還原序列化集合並用它來更多的錯誤報告和處理自動化。 下列 Microsoft[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]程式碼片段說明如何還原序列化失敗的訊息的錯誤訊息部分，並逐一查看集合中的剖析錯誤。 程式碼片段省略以提高可讀性的命名空間限定項目：  
  
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
  
 **ErrorCollection**包含用於逐一查看依類型以及逐一查看集合中的錯誤的所有錯誤的方法。 如需詳細資訊**ErrorCollection**，請參閱 ErrorCollection 成員。  
  
## <a name="see-also"></a>另請參閱  
 [失敗的訊息和 ErrorCollection 物件](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)