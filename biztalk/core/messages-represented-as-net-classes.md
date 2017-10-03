---
title: "以.NET 類別表示訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, expressions
- orchestrations, filters
ms.assetid: cdbea200-552e-4734-a370-2f93da07ea81
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16f0ea95f02de6e9fda411fa0183569dc0779033
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-represented-as-net-classes"></a>以 .NET 類別表示訊息
這個方法的第一步是建立定義訊息類型的 .NET 類別。 這個類別必須擁有預設的建構函式，否則使用此類別的協調流程將無法進行編譯。 以下顯示此種類別的簡單範例。  
  
```  
using System;  
using Microsoft.XLANGs.BaseTypes;  
Using PropertyNamespace;  
  
namespace NetClass  
{  
   [Serializable]  
   public class MsgClass  
   {  
      public MsgClass()  
      {  
         StrField = "OK";  
         IntField = 1;  
         ShortField = 1;  
      }  
  
      [PropertyNamespace.ShortPropertyName]  
      public Int16 ShortField;  
  
      [PropertyAttribute(typeof(PropertyNamespace.StringPropertyName)]  
      [DistinguishedFieldAttribute()]  
      public String StrField;  
  
      [DistinguishedFieldAttribute()]  
      public int IntField;  
   }  
}  
```  
  
 在上面的範例中，ShortField 是 PropertyNamespace.ShortPropertyName 型別的屬性，而該屬性的基礎型別必須是 ShortField 型別的 Int16。 StrField 同時是 PropertyNamespace.StringPropertyName 型別的辨別欄位和屬性，而該屬性的基礎型別必須是 StrField 型別的「字串」型別。 PropertyNamespace.StringPropertyName 和 PropertyNamespace.ShortPropertyName 兩者通常都必須透過 BizTalk 結構描述編輯器建立成結構描述屬性，而且您必須參考包含 C# 專案中結構描述的組件。  
  
> [!NOTE]
>  在 C# 程式設計語言中，屬性名稱的 Attribute 結尾是選擇項，因此您可以省略 Attribute 結尾，改用 DistinguishedField 或 Property。 例如，  
  
```  
[Property(typeof(PropertyNamespace.StringPropertyName))]  
[DistinguishedField]  
public string StrField;  
```  
  
 一旦定義訊息類型之後，您就可以輕易地在協調流程中撰寫程式碼，以建立這種類型的新訊息。 內**建構訊息**圖形，請撰寫簡單運算式建立的新訊息**MsgClass**輸入顯示於上方，然後再將值指派給屬性的 Distinguished 的欄位欄位 （如果您想要覆寫預設值）。 請注意，MyMsg 是協調流程訊息變數，其類型為 NetClass.MsgClass。  
  
```  
MyMsg = new NetClass.MsgClass();  
MyMsg.StrField = "Changed Value";  
MyMsg.IntField = 15;  
```  
  
## <a name="see-also"></a>另請參閱  
 [表示為 XSD 結構描述的訊息](../core/messages-represented-as-xsd-schemas.md)   
 [表示為 XLANGMessage 的訊息](../core/messages-represented-as-xlangmessage.md)   
 [使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md)