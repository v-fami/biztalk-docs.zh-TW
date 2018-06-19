---
title: 如何使用運算式來建立物件和呼叫物件方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, parameters
- Expression shape [Orchestration Designer], calling objects
- Expression shape [Orchestration Designer], parameters
- Expression shape [Orchestration Designer], passing messages
- orchestrations, methods
- Expression shape [Orchestration Designer], calling methods
- orchestrations, objects
- Expression shape [Orchestration Designer], warning
- Use Default Constructor property
- .NET member invocation
ms.assetid: b6af67eb-8ba5-4c95-9b63-26ebb6617af0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b56cfa46098569863106485fef204f72b23a4ef5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256606"
---
# <a name="how-to-use-expressions-to-create-objects-and-call-object-methods"></a><span data-ttu-id="69b9a-102">如何使用運算式建立物件和呼叫物件方法</span><span class="sxs-lookup"><span data-stu-id="69b9a-102">How to Use Expressions to Create Objects and Call Object Methods</span></span>
<span data-ttu-id="69b9a-103">您可能需要使用運算式來建立物件或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="69b9a-103">You might need to use expressions to create objects or invoke methods.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="69b9a-104">建立物件</span><span class="sxs-lookup"><span data-stu-id="69b9a-104">Creating objects</span></span>  
 <span data-ttu-id="69b9a-105">若要建立具有這個類別是.NET 類別類型的變數，您可以建構中的物件**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="69b9a-105">To create a variable that has a type which is a .NET class, you construct an object in the **Expression** shape.</span></span> <span data-ttu-id="69b9a-106">您的 .NET 類別變數屬性會包含一個建構函式。</span><span class="sxs-lookup"><span data-stu-id="69b9a-106">The properties of your .NET class variable include a constructor.</span></span> <span data-ttu-id="69b9a-107">使用預設的建構函式時，只要和宣告其他變數 (像是類型 bool 或 int 中的其中一項) 一樣直接宣告變數即可。</span><span class="sxs-lookup"><span data-stu-id="69b9a-107">If you use the default constructor, you simply declare the variable directly as you would any other variable, like one of type bool or int.</span></span>  
  
 <span data-ttu-id="69b9a-108">如果您使用會採用參數的建構函式，您必須使用關鍵字**新**，後面接著 object 類別以及括號括住的任何參數：</span><span class="sxs-lookup"><span data-stu-id="69b9a-108">If you use a constructor that takes parameters, you use the keyword **new**, followed by the object class and any parameters in parentheses:</span></span>  
  
```  
new MyClass(myParam1, myParam2)  
```  
  
> [!CAUTION]
>  <span data-ttu-id="69b9a-109">**使用預設建構函式**執行動作，事實上，某些物件具有建構函式，可能不會顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="69b9a-109">The **Use Default Constructor** property might not be displayed for some objects that do, in fact, have constructors.</span></span> <span data-ttu-id="69b9a-110">在此情況下，會自動使用預設建構函式，而且若您嘗試使用不同的建構函式，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="69b9a-110">In this case, the default constructor will be used automatically, and an error will be raised if you attempt to use a different constructor.</span></span>  
  
## <a name="invoking-methods"></a><span data-ttu-id="69b9a-111">呼叫方法</span><span class="sxs-lookup"><span data-stu-id="69b9a-111">Invoking methods</span></span>  
 <span data-ttu-id="69b9a-112">若要呼叫 .NET 類別物件上的方法，請在物件參考上附加一個句號和方法名稱，後面跟著以括號括住的任何參數：</span><span class="sxs-lookup"><span data-stu-id="69b9a-112">To invoke a method on a .NET class object, you append a period and the name of the method to the object reference, followed by any parameters in parentheses:</span></span>  
  
```  
MyObject.MyMethod (param1)  
```  
  
## <a name="passing-and-using-messages-as-parameters"></a><span data-ttu-id="69b9a-113">以參數傳送和使用訊息</span><span class="sxs-lookup"><span data-stu-id="69b9a-113">Passing and using messages as parameters</span></span>  
 <span data-ttu-id="69b9a-114">若要以參數將訊息傳送給 .NET 類別上的方法呼叫，請先在定義該類別的專案上新增 Microsoft.XLANGs.BaseTypes.dll 的參考，然後在方法簽章中使用類型 XLANGMessage。</span><span class="sxs-lookup"><span data-stu-id="69b9a-114">To pass a message as a parameter to a method call on a .NET class, you first add a reference to Microsoft.XLANGs.BaseTypes.dll in the project that defines the class, and then use the type XLANGMessage in the method signature.</span></span>  
  
 <span data-ttu-id="69b9a-115">使用類型 XLANGPart 參考多部分訊息類型，可讓您存取訊息的各個部分：</span><span class="sxs-lookup"><span data-stu-id="69b9a-115">Referencing the multi-part message type enables you to access the various parts of the message by using the type XLANGPart:</span></span>  
  
```  
MyMethod(XLANGMessage myMsg)  
{  
XLANGPart myPart = myMsg["Part1"];  
XmlDocument xmlDoc = (XmlDocument) myPart.RetrieveAs(typeof(XmlDocument));  
}  
```  
  
 <span data-ttu-id="69b9a-116">在呼叫本身中，您只需向對其他參數一樣提供訊息的名稱即可：</span><span class="sxs-lookup"><span data-stu-id="69b9a-116">In the call itself, you simply supply the name of the message as you would any other parameter:</span></span>  
  
```  
MyObject.MyMethod(myMessage)  
```  
  
 <span data-ttu-id="69b9a-117">您也可以類型 XLANGPart 來傳送訊息部分。</span><span class="sxs-lookup"><span data-stu-id="69b9a-117">You can also pass a message part as type XLANGPart.</span></span>  
  
## <a name="net-member-invocation"></a><span data-ttu-id="69b9a-118">.NET 成員呼叫</span><span class="sxs-lookup"><span data-stu-id="69b9a-118">.NET member invocation</span></span>  
 <span data-ttu-id="69b9a-119">您可以存取公用成員，除非在直接存取訊息部分的成員。</span><span class="sxs-lookup"><span data-stu-id="69b9a-119">You can access public members except in the case of direct access to members of a message part.</span></span> <span data-ttu-id="69b9a-120">若要直接存取訊息部分的成員，就必須將它升級為辨別欄位。</span><span class="sxs-lookup"><span data-stu-id="69b9a-120">To directly access a member of a message part it must be promoted as a distinguished field.</span></span>  
  
## <a name="comcom-component-invocation"></a><span data-ttu-id="69b9a-121">COM/COM+ 元件叫用</span><span class="sxs-lookup"><span data-stu-id="69b9a-121">COM/COM+ component invocation</span></span>  
 <span data-ttu-id="69b9a-122">XLANGs 會產生 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="69b9a-122">XLANGs generates C# code.</span></span> <span data-ttu-id="69b9a-123">所有使用者宣告的 XLANGs 變數都會以 C# 變數的形式產生。</span><span class="sxs-lookup"><span data-stu-id="69b9a-123">All user-declared XLANGs variables are generated as C# variables.</span></span> <span data-ttu-id="69b9a-124">除了在不可部分完成的交易中以外，並沒有任何特殊的行為。</span><span class="sxs-lookup"><span data-stu-id="69b9a-124">There is no special behavior except in the case of atomic transactions.</span></span> <span data-ttu-id="69b9a-125">當服務元件 (也就是實作的類別執行個體**System.EnterpriseServices.ServicedComponent**)，然後只宣告中不可部分完成的範圍，則不會 XLANGs 產生及使用真正的 DTC COM + 交易。</span><span class="sxs-lookup"><span data-stu-id="69b9a-125">When a serviced component (that is, an instance of a class that implements **System.EnterpriseServices.ServicedComponent**) is declared in an atomic scope, then and only then does XLANGs generate and use a real DTC COM+ transaction.</span></span>  
  
 <span data-ttu-id="69b9a-126">如果變數在不可部分完成的範圍內當做左值 (L-value，也就是寫入的值) 來參考，但是宣告於外部範圍時，會複製該變數來支援復原。</span><span class="sxs-lookup"><span data-stu-id="69b9a-126">If a variable is referenced as an L-value (that is, it is written to) in the atomic scope, but is declared in an outer scope, the variable is cloned to support rollback.</span></span> <span data-ttu-id="69b9a-127">不過，物件 (例如**XmlDocument**) 可以修改.NET 函式呼叫中參數，當做傳遞時的內部，因此，xlangs 將寫入物件，它將不會正確復原。</span><span class="sxs-lookup"><span data-stu-id="69b9a-127">However, an object (such as an **XmlDocument**) can be modified inside a .NET function call when passed as an in-parameter, and thus XLANGs will miss that the object is being written to and it will not roll back correctly.</span></span> <span data-ttu-id="69b9a-128">此情況的解決方法是將這類物件傳遞為 ref 參數。</span><span class="sxs-lookup"><span data-stu-id="69b9a-128">The workaround in this case is to pass such objects as ref parameters.</span></span>  
  
 <span data-ttu-id="69b9a-129">這裡的底線為元件的行為應該與在其他 C# 程式中一樣。</span><span class="sxs-lookup"><span data-stu-id="69b9a-129">The bottom line is that components should behave as they do in other C# programs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b9a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b9a-130">See Also</span></span>  
 [<span data-ttu-id="69b9a-131">關於 BizTalk 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="69b9a-131">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)