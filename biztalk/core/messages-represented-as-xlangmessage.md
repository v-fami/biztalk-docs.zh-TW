---
title: 表示為 XLANGMessage 的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aadca870-2f93-4be3-8733-a0cd3815add7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62c5b4b192602896d0cfe301834844b4b7cab12b
ms.sourcegitcommit: c3070a7a3f332857357f056dc632829b43869c17
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51630323"
---
# <a name="messages-represented-as-xlangmessage"></a><span data-ttu-id="635a6-102">表示為 XLANGMessage 的訊息</span><span class="sxs-lookup"><span data-stu-id="635a6-102">Messages Represented as XLANGMessage</span></span>
<span data-ttu-id="635a6-103">**XLANGMessage**物件代表以 XLANG 服務宣告的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="635a6-103">An **XLANGMessage** object represents a message instance declared with an XLANG service.</span></span> <span data-ttu-id="635a6-104">這個物件的取得方式，是在方法引動過程中將訊息的參考傳遞為參數。</span><span class="sxs-lookup"><span data-stu-id="635a6-104">This object is obtained by passing a reference to a message as a parameter in a method invocation.</span></span> <span data-ttu-id="635a6-105">**XLANGPart**物件都代表在 XLANG 服務中的訊息執行個體中所包含的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="635a6-105">An **XLANGPart** object represents a message part contained in a message instance within an XLANG service.</span></span> <span data-ttu-id="635a6-106">此物件取自藉由傳遞部分參考中的方法引動過程，其中的接收參數類型**XLANGPart**或傳遞的參考上列舉**XLANGMessage**。</span><span class="sxs-lookup"><span data-stu-id="635a6-106">This object is obtained either by passing a part reference in a method invocation where the receiving parameter type is **XLANGPart** or by enumerating on a passed reference of **XLANGMessage**.</span></span>  
  
 <span data-ttu-id="635a6-107">協調流程訊息變數，可能會傳遞給使用者元件，並以接收**XLANGMessage**物件。</span><span class="sxs-lookup"><span data-stu-id="635a6-107">An orchestration message variable may be passed to a user component and received as an **XLANGMessage** object.</span></span> <span data-ttu-id="635a6-108">**XLANGMessage**物件可用來存取部分和存取訊息屬性。使用者可能會 「 保留 」 **XLANGMessage** ，進而擴充到宣告的範圍超過其生命週期。</span><span class="sxs-lookup"><span data-stu-id="635a6-108">The **XLANGMessage** object allows accessing the parts and accessing message properties.The user may "hold on" to an **XLANGMessage** and thereby extend its lifetime beyond the declared scope.</span></span> <span data-ttu-id="635a6-109">接著， **XLANGMessage**可能從方法傳回並指派給協調流程中的訊息變數。</span><span class="sxs-lookup"><span data-stu-id="635a6-109">Subsequently, an **XLANGMessage** may be returned from a method and assigned to a message variable in an orchestration.</span></span>  
  
## <a name="constructing-an-xlangmessage"></a><span data-ttu-id="635a6-110">建構 XLANGMessage</span><span class="sxs-lookup"><span data-stu-id="635a6-110">Constructing an XLANGMessage</span></span>  
 <span data-ttu-id="635a6-111">在建構時**XLANGMessage**使用的資料流的資料流類型必須實作**IStreamFactory**也**MemoryStream**。</span><span class="sxs-lookup"><span data-stu-id="635a6-111">When constructing an **XLANGMessage** with a stream, the stream type must either implement **IStreamFactory** or be a **MemoryStream**.</span></span> <span data-ttu-id="635a6-112">下列程式碼範例示範如何建構**XLANGMessage**:</span><span class="sxs-lookup"><span data-stu-id="635a6-112">The following code sample shows how to construct an **XLANGMessage**:</span></span>  
  
```csharp
public class FileStreamFactory : IStreamFactory  
{  
    string _fname;  
  
    public FileStreamFactory(string fname)  
    {  
        _fname = fname;  
    }  
  
    public Stream CreateStream()  
    {  
        return new FileStream  
        (  
            _fname,  
            FileMode.Open,  
            FileAccess.Read,  
            FileShare.Read  
        );  
    }  
}  
  
public static void AssignStreamFactoryToPart(XLANGMessage msg)  
{  
    IStreamFactory sf = new FileStreamFactory( @”c:\data.xml” );  
    msg[0].LoadFrom( sf );  
}  
```  
  
 <span data-ttu-id="635a6-113">您有時可能會想要建立新的訊息，而不要轉換來源訊息。</span><span class="sxs-lookup"><span data-stu-id="635a6-113">There may be times when you want to create a new message without transforming a source message.</span></span> <span data-ttu-id="635a6-114">您可以使用類型的變數**System.Xml.XmlDocument**和載入或否則建構適當的內容。</span><span class="sxs-lookup"><span data-stu-id="635a6-114">You can do this by using a variable of type **System.Xml.XmlDocument** and loading or otherwise constructing appropriate content.</span></span> <span data-ttu-id="635a6-115">在下列範例中，XML 從字串使用載入**LoadXml**方法**XmlDocument**:</span><span class="sxs-lookup"><span data-stu-id="635a6-115">In the following example, XML is loaded from a string by using the **LoadXml** method of **XmlDocument**:</span></span>  
  
```csharp
XmlVariable.LoadXml("<ns0:Root PONumber="047745351122111" xmlns:ns0="http://BTSHTTPSend.SimpleSchema"><MyChildRecord SubAttr1="Simple Attribute " /></ns0:Root>");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
 <span data-ttu-id="635a6-116">下列範例從檔案載入 XML，利用**負載**方法**XmlDocument**:</span><span class="sxs-lookup"><span data-stu-id="635a6-116">The following example loads XML from a file by using the **Load** method of **XmlDocument**:</span></span>  
  
```csharp
XmlVariable.Load("C:\MyData.xml");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="635a6-117">如果您想要建構更大的訊息，使用其中一種資料流上一節中所示範的方法，或考慮使用**轉換**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="635a6-117">If you want to construct larger messages, use one of the streaming methods demonstrated in the previous section or consider using the **Transform** shape in Orchestration Designer.</span></span>  
  
## <a name="considerations-when-using-xlangmessage-and-xlangpart"></a><span data-ttu-id="635a6-118">使用 XLANGMessage 和 XLANGPart 時的考量</span><span class="sxs-lookup"><span data-stu-id="635a6-118">Considerations When Using XLANGMessage and XLANGPart</span></span>  
 <span data-ttu-id="635a6-119">使用時**XLANGMessage**並**XLANGPart**在使用者程式碼，請考慮下列：</span><span class="sxs-lookup"><span data-stu-id="635a6-119">When using **XLANGMessage** and **XLANGPart** in user code, consider the following:</span></span>  
  
-   <span data-ttu-id="635a6-120">請勿將傳遞做為訊息部分**XLANGPart**引數或傳回型別的值**XLANGPart**。</span><span class="sxs-lookup"><span data-stu-id="635a6-120">Do not pass a message part as an **XLANGPart** argument or return a value of type **XLANGPart**.</span></span> <span data-ttu-id="635a6-121">您應傳入**XLANGPart**做為組件的類型。</span><span class="sxs-lookup"><span data-stu-id="635a6-121">You should pass **XLANGPart** as the type of the part.</span></span> <span data-ttu-id="635a6-122">例如：</span><span class="sxs-lookup"><span data-stu-id="635a6-122">For example:</span></span>  
  
    ```csharp
    Message String msg;  
    Class.Test(msg);  
    // or you can do the following  
    Messagetype mt  
    {  
         String part;  
    };  
    Message mt msg;  
    Class.Test(msg,part);  
  
    ```  
  
     <span data-ttu-id="635a6-123">您也可以傳遞訊息本身做**XLANGMessage**並用**XLANGMessage**註標運算子來存取函式呼叫的部分。</span><span class="sxs-lookup"><span data-stu-id="635a6-123">You can also pass the message itself as an **XLANGMessage** and use the **XLANGMessage** subscript operators to access the part inside the function call.</span></span> <span data-ttu-id="635a6-124">不過，您不應該放置**XLANGPart**存留期會延伸超過函式呼叫的存留期集合中。</span><span class="sxs-lookup"><span data-stu-id="635a6-124">However, you should not put an **XLANGPart** in a collection whose lifetime extends past the lifetime of the function call.</span></span> <span data-ttu-id="635a6-125">相反地，您應該在其中放置**XLANGMessage**集合中。</span><span class="sxs-lookup"><span data-stu-id="635a6-125">Instead, you should put the **XLANGMessage** in the collection.</span></span> <span data-ttu-id="635a6-126">例如：</span><span class="sxs-lookup"><span data-stu-id="635a6-126">For example:</span></span>  
  
    ```csharp
    Void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          XLANGPart xlp = xlm[0];  
          String sval = (String) xlp.RetrieveAs(typeof(string));  
         }  
         finally  
         {  
          Xlm.Dispose();  
         }  
    }  
    ```  
  
-   <span data-ttu-id="635a6-127">不會定義為協調流程參數**XLANGMessage**或是**XLANGPart**。</span><span class="sxs-lookup"><span data-stu-id="635a6-127">Do not define an orchestration parameter as **XLANGMessage** or **XLANGPart**.</span></span> <span data-ttu-id="635a6-128">如果您要傳遞訊息，請使用訊息類型參數來傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="635a6-128">If you want to pass a message, then use a message type parameter to pass the message.</span></span> <span data-ttu-id="635a6-129">如果您要傳遞某個部分，請改為傳遞訊息，然後再使用此部分。</span><span class="sxs-lookup"><span data-stu-id="635a6-129">If you want to pass a part, then pass the message instead and then use the part.</span></span> <span data-ttu-id="635a6-130">如果您只想要此部分值，請使用此部分類型來傳遞此部分。</span><span class="sxs-lookup"><span data-stu-id="635a6-130">If you only want the part value, then use the part type to pass the part.</span></span>  
  
-   <span data-ttu-id="635a6-131">不會傳回**XLANGMessage**方法呼叫的參數。</span><span class="sxs-lookup"><span data-stu-id="635a6-131">Do not return an **XLANGMessage** parameter for a method call.</span></span> <span data-ttu-id="635a6-132">如果您傳回**XLANGMessage**無法呼叫，會傳入的參數，然後**處置**方法上方法呼叫內的參數，它會直覺式地違反存留期間的假設，而且也擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="635a6-132">If you return an **XLANGMessage** parameter that is passed in, and then you cannot call the **Dispose** method on the parameter inside the method call, it intuitively violates lifetime assumptions and it also throws an exception.</span></span> <span data-ttu-id="635a6-133">傳遞到訊息時**XLANGMessage**參數加入使用者程式碼，參考的特殊的內容，通常不會具有訊息參考訊息。</span><span class="sxs-lookup"><span data-stu-id="635a6-133">When passing a message through an **XLANGMessage** parameter to user code, you reference the message to a special context that does not normally have messages referenced to it.</span></span> <span data-ttu-id="635a6-134">此內容的存留期間就是協調流程執行個體的存留期間。</span><span class="sxs-lookup"><span data-stu-id="635a6-134">The lifetime of this context is the lifetime of the orchestration instance.</span></span> <span data-ttu-id="635a6-135">這是因為 BizTalk Server 並不知道使用者程式碼是否會保留此訊息。</span><span class="sxs-lookup"><span data-stu-id="635a6-135">This is because BizTalk Server does not know whether the user code will hold onto the message.</span></span>  
  
     <span data-ttu-id="635a6-136">當協調流程執行個體結束時，該執行個體中建立的任何訊息便不再有效，所以這類集合的存留期間應該小於或等於此執行個體的存留期間。</span><span class="sxs-lookup"><span data-stu-id="635a6-136">When an orchestration instance exits, any messages created in that instance are no longer valid, so the lifetime of such a collection should be less than or equal to that of the instance lifetime.</span></span> <span data-ttu-id="635a6-137">不過，如果您想要透過傳遞訊息時，釋放迴圈中的訊息參考**XLANGMessage**有相同的存留期，與協調流程執行個體，則您可以呼叫的引數**XLANGMessage.Dispose**以釋出的參考。</span><span class="sxs-lookup"><span data-stu-id="635a6-137">However, if you want to release a message reference in a loop when the message was passed through an **XLANGMessage** argument that has the same lifetime as the orchestration instance, then you can call **XLANGMessage.Dispose** to free up the reference.</span></span> <span data-ttu-id="635a6-138">此外，如果在使用者程式碼方法中， **XLANGMessage**只有在本機使用參數和參數的存留期包含在函式呼叫中，您也可以呼叫**XLANGMessage.Dispose**釋出根內容的參考，並回到正常的存留期間行為讓對應的訊息。</span><span class="sxs-lookup"><span data-stu-id="635a6-138">Moreover, if inside the user code method, the **XLANGMessage** parameter is only used locally and the lifetime of the parameter is contained in that of the function call, you can also call **XLANGMessage.Dispose** to free up the reference to the root context and give the corresponding message back the normal lifetime behavior.</span></span> <span data-ttu-id="635a6-139">例如：</span><span class="sxs-lookup"><span data-stu-id="635a6-139">For example:</span></span>  
  
    ```csharp
    void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          //XLANGMessage is only used locally  
         }  
         finally  
         {  
          xlm.Dispose();  
         }  
    }  
    ```  
  
     <span data-ttu-id="635a6-140">如果您在集合中，放置此 xlm，則必須有類別本身**處置**方法來進行清除。</span><span class="sxs-lookup"><span data-stu-id="635a6-140">If you place the xlm in a collection, then the class itself must have a **Dispose** method for cleanup.</span></span> <span data-ttu-id="635a6-141">例如：</span><span class="sxs-lookup"><span data-stu-id="635a6-141">For example:</span></span>  
  
    ```csharp
    Public class A  
    {  
         Hashtable h = new Hashtable();  
         Public Test(XLANGMessage xlm)  
         {  
          h[xlm] = 1;  
         }  
         //You can have more methods here  
         Public Dispose()  
         {  
          foreach (XLANGMessage xlm in h.Keys)  
           Xlm.Dispose();  
         }  
    }  
    ```  
  
     <span data-ttu-id="635a6-142">您可以呼叫**xlangmessages**當您已完成的集合**A.dispose**。</span><span class="sxs-lookup"><span data-stu-id="635a6-142">You would call **A.Dispose** when you are finished with the collection of **XLANGMessages**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635a6-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="635a6-143">See Also</span></span>  
 <span data-ttu-id="635a6-144">[表示為 XSD 結構描述的訊息](../core/messages-represented-as-xsd-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="635a6-144">[Messages Represented as XSD Schemas](../core/messages-represented-as-xsd-schemas.md) </span></span>  
 <span data-ttu-id="635a6-145">[表示為.NET 類別的訊息](../core/messages-represented-as-net-classes.md) </span><span class="sxs-lookup"><span data-stu-id="635a6-145">[Messages Represented as .NET Classes](../core/messages-represented-as-net-classes.md) </span></span>  
 [<span data-ttu-id="635a6-146">在使用者程式碼中建構訊息</span><span class="sxs-lookup"><span data-stu-id="635a6-146">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)
