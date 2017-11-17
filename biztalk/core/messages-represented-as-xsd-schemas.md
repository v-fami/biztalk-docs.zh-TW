---
title: "訊息表示為 XSD 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Assignment shape [Orchestration Designer], maps
- maps, transforms
- Expression Editor, assigning maps
ms.assetid: 646e84d4-1dcc-4f92-9205-84cb6c7df297
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47242dc01ed05ca2ab3c2cb71daffc5a81f9462c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-represented-as-xsd-schemas"></a><span data-ttu-id="75ba2-102">表示為 XSD 結構描述的訊息</span><span class="sxs-lookup"><span data-stu-id="75ba2-102">Messages Represented as XSD Schemas</span></span>
<span data-ttu-id="75ba2-103">XSD 訊息的範本 XML 執行個體是在設計階段定義，接著儲存在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="75ba2-103">A template XML instance of the XSD message type is defined at design time and then stored on disk.</span></span> <span data-ttu-id="75ba2-104">在執行階段，.NET 元件會從磁碟收取 XML，並將它當做 XmlDocument 傳回。</span><span class="sxs-lookup"><span data-stu-id="75ba2-104">At run time, a .NET component picks up the XML from disk and returns it as an XmlDocument.</span></span> <span data-ttu-id="75ba2-105">協調流程程式碼可將此 XmlDocument 結果指定至協調流程中宣告的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="75ba2-105">The orchestration code can assign this XmlDocument result to the message instance declared in the orchestration.</span></span>  
  
 <span data-ttu-id="75ba2-106">**訊息指派**圖形只有一行的程式碼：</span><span class="sxs-lookup"><span data-stu-id="75ba2-106">The **Message Assignment** shape has a single line of code:</span></span>  
  
```  
MsgOut = CreateMsgHelper.Helper.GetXmlDocumentTemplate();  
```  
  
 <span data-ttu-id="75ba2-107">建立 XmlDocument 的「協助程式元件」具有一個靜態方法：</span><span class="sxs-lookup"><span data-stu-id="75ba2-107">The Helper Component that creates the XmlDocument has a single static method:</span></span>  
  
```  
private static XmlDocument _template = null;  
private static object _sync = new object();  
private static String LOCATION = @"C:\MyTemplateLocation\MyMsgTemplate.xml";  
  
public static XmlDocument GetXmlDocumentTemplate()  
{  
   XmlDocument doc = _template;  
   if (doc == null)  
   {  
      // Load the doc template from disk.  
      doc = new XmlDocument();  
      XmlTextReader reader = new XmlTextReader(LOCATION);  
      doc.Load(reader);  
  
      // Synchronize assignment to _template.  
      lock (_sync)  
      {  
         XmlDocument doc2 = _template;  
         if (doc2 == null)  
         {  
            _template = doc;  
         }  
         else  
         {  
            // Another thread beat us to it.  
            doc = doc2;  
         }  
      }  
   }  
  
   // Need to explicitly create a clone so that we are not  
   // referencing the same object statically held by this class.  
   doc = (XmlDocument) doc.CloneNode(true);  
   return doc;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="75ba2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75ba2-108">See Also</span></span>  
 <span data-ttu-id="75ba2-109">[訊息會表示為.NET 類別](../core/messages-represented-as-net-classes.md) </span><span class="sxs-lookup"><span data-stu-id="75ba2-109">[Messages Represented as .NET Classes](../core/messages-represented-as-net-classes.md) </span></span>  
 <span data-ttu-id="75ba2-110">[表示為 XLANGMessage 的訊息](../core/messages-represented-as-xlangmessage.md) </span><span class="sxs-lookup"><span data-stu-id="75ba2-110">[Messages Represented as XLANGMessage](../core/messages-represented-as-xlangmessage.md) </span></span>  
 [<span data-ttu-id="75ba2-111">使用者程式碼中建構的訊息</span><span class="sxs-lookup"><span data-stu-id="75ba2-111">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)