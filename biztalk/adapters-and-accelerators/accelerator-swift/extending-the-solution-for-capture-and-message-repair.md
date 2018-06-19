---
title: 擷取和訊息修復擴充解決方案 |Microsoft 文件
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
ms.openlocfilehash: 2bb2f5fb1960a149c96a179ba596c67c9f402016
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209086"
---
# <a name="extending-the-solution-for-capture-and-message-repair"></a><span data-ttu-id="950fa-102">擷取和訊息修復擴充解決方案</span><span class="sxs-lookup"><span data-stu-id="950fa-102">Extending the Solution for Capture and Message Repair</span></span>
<span data-ttu-id="950fa-103">在此說明中的 MT103 端對端教學課程會示範如何建構 BizTalk 協調流程訂閱失敗 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="950fa-103">The MT103 End-to-End Tutorial in this Help shows you how to construct a BizTalk orchestration that subscribes to failed SWIFT messages.</span></span>  
  
 <span data-ttu-id="950fa-104">MT103 端對端教學課程中的協調流程會使用協助程式類別的靜態方法**ErrorExtractor**，以從訊息中的錯誤部分和主體擷取為字串。</span><span class="sxs-lookup"><span data-stu-id="950fa-104">The orchestration in the MT103 End-to-End Tutorial uses the static methods of a helper class, **ErrorExtractor**, to extract the error part and body from the message as strings.</span></span> <span data-ttu-id="950fa-105">協調流程接著會寫入至不同的檔案部分。</span><span class="sxs-lookup"><span data-stu-id="950fa-105">The orchestration then writes the parts to separate files.</span></span>  
  
 <span data-ttu-id="950fa-106">因為錯誤部份的失敗訊息的序列化**ErrorCollection**管線元件所建構，您可以還原序列化集合並用它來自動化多個錯誤報告和處理。</span><span class="sxs-lookup"><span data-stu-id="950fa-106">Because the error part of the failed message is a serialization of the **ErrorCollection** constructed by the pipeline component, you can deserialize the collection and use it to automate more of the error reporting and handling.</span></span> <span data-ttu-id="950fa-107">下列[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]程式碼片段說明如何還原序列化失敗訊息的錯誤訊息部分，並逐一查看集合中的剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="950fa-107">The following [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] code fragment illustrates how to deserialize the error message part of a failed message and iterate over the parsing errors in the collection.</span></span> <span data-ttu-id="950fa-108">程式碼片段會省略命名空間限定性條件來提高可讀性：</span><span class="sxs-lookup"><span data-stu-id="950fa-108">The code fragment omits namespace qualifications for readability:</span></span>  
  
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
  
 <span data-ttu-id="950fa-109">**ErrorCollection**包含方法，用於逐一查看依類型以及來反覆查看集合中的錯誤的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="950fa-109">The **ErrorCollection** includes methods for iterating over errors by type as well as for iterating over all of the errors in the collection.</span></span> <span data-ttu-id="950fa-110">如需有關**ErrorCollection**，請參閱 ErrorCollection 成員。</span><span class="sxs-lookup"><span data-stu-id="950fa-110">For more information about the **ErrorCollection**, see ErrorCollection Members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950fa-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="950fa-111">See Also</span></span>  
 [<span data-ttu-id="950fa-112">失敗的訊息和 ErrorCollection 物件</span><span class="sxs-lookup"><span data-stu-id="950fa-112">Failed Messages and ErrorCollection Objects</span></span>](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)