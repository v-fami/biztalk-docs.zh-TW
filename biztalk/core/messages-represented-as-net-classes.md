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
# <a name="messages-represented-as-net-classes"></a><span data-ttu-id="1d021-102">以 .NET 類別表示訊息</span><span class="sxs-lookup"><span data-stu-id="1d021-102">Messages Represented as .NET Classes</span></span>
<span data-ttu-id="1d021-103">這個方法的第一步是建立定義訊息類型的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="1d021-103">This approach first involves creating a .NET class that defines your message type.</span></span> <span data-ttu-id="1d021-104">這個類別必須擁有預設的建構函式，否則使用此類別的協調流程將無法進行編譯。</span><span class="sxs-lookup"><span data-stu-id="1d021-104">The class must have a default constructor or the orchestration using it will not compile.</span></span> <span data-ttu-id="1d021-105">以下顯示此種類別的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="1d021-105">A simple example of such a class is shown here.</span></span>  
  
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
  
 <span data-ttu-id="1d021-106">在上面的範例中，ShortField 是 PropertyNamespace.ShortPropertyName 型別的屬性，而該屬性的基礎型別必須是 ShortField 型別的 Int16。</span><span class="sxs-lookup"><span data-stu-id="1d021-106">In the above example, ShortField would be a property of type PropertyNamespace.ShortPropertyName and the underlying type of the property would have to be Int16 which is the type of ShortField.</span></span> <span data-ttu-id="1d021-107">StrField 同時是 PropertyNamespace.StringPropertyName 型別的辨別欄位和屬性，而該屬性的基礎型別必須是 StrField 型別的「字串」型別。</span><span class="sxs-lookup"><span data-stu-id="1d021-107">StrField would be both a distinguished field and a property of type PropertyNamespace.StringPropertyName and the underlying type of the property would have to be type of String which is the type of StrField.</span></span> <span data-ttu-id="1d021-108">PropertyNamespace.StringPropertyName 和 PropertyNamespace.ShortPropertyName 兩者通常都必須透過 BizTalk 結構描述編輯器建立成結構描述屬性，而且您必須參考包含 C# 專案中結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="1d021-108">Normally both PropertyNamespace.StringPropertyName and PropertyNamespace.ShortPropertyName would be created through the BizTalk Schema Editor as schema properties, and you need to reference the assembly which contains the schema properties in your C# project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d021-109">在 C# 程式設計語言中，屬性名稱的 Attribute 結尾是選擇項，因此您可以省略 Attribute 結尾，改用 DistinguishedField 或 Property。</span><span class="sxs-lookup"><span data-stu-id="1d021-109">In C# programming language, the Attribute ending of an attribute name is optional, so you can omit the Attribute ending and use DistinguishedField or Property instead.</span></span> <span data-ttu-id="1d021-110">例如，</span><span class="sxs-lookup"><span data-stu-id="1d021-110">For example,</span></span>  
  
```  
[Property(typeof(PropertyNamespace.StringPropertyName))]  
[DistinguishedField]  
public string StrField;  
```  
  
 <span data-ttu-id="1d021-111">一旦定義訊息類型之後，您就可以輕易地在協調流程中撰寫程式碼，以建立這種類型的新訊息。</span><span class="sxs-lookup"><span data-stu-id="1d021-111">Once the message type is defined, it is very easy to write code in the orchestration that will create a new message of this type.</span></span> <span data-ttu-id="1d021-112">內**建構訊息**圖形，請撰寫簡單運算式建立的新訊息**MsgClass**輸入顯示於上方，然後再將值指派給屬性的 Distinguished 的欄位欄位 （如果您想要覆寫預設值）。</span><span class="sxs-lookup"><span data-stu-id="1d021-112">Within a **Construct Message** shape, you write simple expressions to create a new message of the **MsgClass** type shown above, and then assign values to the fields which are attributed as Distinguished Fields (if you wish to override the default values).</span></span> <span data-ttu-id="1d021-113">請注意，MyMsg 是協調流程訊息變數，其類型為 NetClass.MsgClass。</span><span class="sxs-lookup"><span data-stu-id="1d021-113">Note that MyMsg is an orchestration message variable whose type is NetClass.MsgClass.</span></span>  
  
```  
MyMsg = new NetClass.MsgClass();  
MyMsg.StrField = "Changed Value";  
MyMsg.IntField = 15;  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d021-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d021-114">See Also</span></span>  
 <span data-ttu-id="1d021-115">[表示為 XSD 結構描述的訊息](../core/messages-represented-as-xsd-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="1d021-115">[Messages Represented as XSD Schemas](../core/messages-represented-as-xsd-schemas.md) </span></span>  
 <span data-ttu-id="1d021-116">[表示為 XLANGMessage 的訊息](../core/messages-represented-as-xlangmessage.md) </span><span class="sxs-lookup"><span data-stu-id="1d021-116">[Messages Represented as XLANGMessage](../core/messages-represented-as-xlangmessage.md) </span></span>  
 [<span data-ttu-id="1d021-117">使用者程式碼中建構的訊息</span><span class="sxs-lookup"><span data-stu-id="1d021-117">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)