---
title: 訊息表示為 XSD 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Message Assignment shape [Orchestration Designer], maps
- maps, transforms
- Expression Editor, assigning maps
ms.assetid: 646e84d4-1dcc-4f92-9205-84cb6c7df297
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47242dc01ed05ca2ab3c2cb71daffc5a81f9462c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262966"
---
# <a name="messages-represented-as-xsd-schemas"></a>表示為 XSD 結構描述的訊息
XSD 訊息的範本 XML 執行個體是在設計階段定義，接著儲存在磁碟上。 在執行階段，.NET 元件會從磁碟收取 XML，並將它當做 XmlDocument 傳回。 協調流程程式碼可將此 XmlDocument 結果指定至協調流程中宣告的訊息執行個體。  
  
 **訊息指派**圖形只有一行的程式碼：  
  
```  
MsgOut = CreateMsgHelper.Helper.GetXmlDocumentTemplate();  
```  
  
 建立 XmlDocument 的「協助程式元件」具有一個靜態方法：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [訊息會表示為.NET 類別](../core/messages-represented-as-net-classes.md)   
 [表示為 XLANGMessage 的訊息](../core/messages-represented-as-xlangmessage.md)   
 [使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md)