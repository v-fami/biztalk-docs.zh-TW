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
# <a name="extending-the-solution-for-capture-and-message-repair"></a><span data-ttu-id="8255c-102">延伸 Capture 和 Message Repair 的解決方案</span><span class="sxs-lookup"><span data-stu-id="8255c-102">Extending the Solution for Capture and Message Repair</span></span>
<span data-ttu-id="8255c-103">在此說明中的 MT103 端對端教學課程會示範如何建構 BizTalk 協調流程訂閱失敗 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="8255c-103">The MT103 End-to-End Tutorial in this Help shows you how to construct a BizTalk orchestration that subscribes to failed SWIFT messages.</span></span>  
  
 <span data-ttu-id="8255c-104">MT103 端對端教學課程中的協調流程會使用協助程式類別的靜態方法**ErrorExtractor**，以從訊息擷取錯誤的組件和本文為字串。</span><span class="sxs-lookup"><span data-stu-id="8255c-104">The orchestration in the MT103 End-to-End Tutorial uses the static methods of a helper class, **ErrorExtractor**, to extract the error part and body from the message as strings.</span></span> <span data-ttu-id="8255c-105">協調流程接著會寫入至不同的檔案部分。</span><span class="sxs-lookup"><span data-stu-id="8255c-105">The orchestration then writes the parts to separate files.</span></span>  
  
 <span data-ttu-id="8255c-106">因為錯誤部份的失敗訊息的序列化**ErrorCollection**建構管線元件，您可以還原序列化集合並用它來更多的錯誤報告和處理自動化。</span><span class="sxs-lookup"><span data-stu-id="8255c-106">Because the error part of the failed message is a serialization of the **ErrorCollection** constructed by the pipeline component, you can deserialize the collection and use it to automate more of the error reporting and handling.</span></span> <span data-ttu-id="8255c-107">下列 Microsoft[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]程式碼片段說明如何還原序列化失敗的訊息的錯誤訊息部分，並逐一查看集合中的剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="8255c-107">The following Microsoft [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] code fragment illustrates how to deserialize the error message part of a failed message and iterate over the parsing errors in the collection.</span></span> <span data-ttu-id="8255c-108">程式碼片段省略以提高可讀性的命名空間限定項目：</span><span class="sxs-lookup"><span data-stu-id="8255c-108">The code fragment omits namespace qualifications for readability:</span></span>  
  
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
  
 <span data-ttu-id="8255c-109">**ErrorCollection**包含用於逐一查看依類型以及逐一查看集合中的錯誤的所有錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="8255c-109">The **ErrorCollection** includes methods for iterating over errors by type as well as for iterating over all of the errors in the collection.</span></span> <span data-ttu-id="8255c-110">如需詳細資訊**ErrorCollection**，請參閱 ErrorCollection 成員。</span><span class="sxs-lookup"><span data-stu-id="8255c-110">For more information about the **ErrorCollection**, see ErrorCollection Members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8255c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8255c-111">See Also</span></span>  
 [<span data-ttu-id="8255c-112">失敗的訊息和 ErrorCollection 物件</span><span class="sxs-lookup"><span data-stu-id="8255c-112">Failed Messages and ErrorCollection Objects</span></span>](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)