---
title: "如何使用運算式執行訊息指派 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- orchestrations, expressions
- messages, manipulating
- messages, assigning messages
- messages, expressions
- messages, message parts
- orchestrations, messages
- messages, components
ms.assetid: 9989caf5-012c-4fc4-b5d8-981ca9a69f43
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f423e1b797cfff95bae1d9b1dd862d28210cd26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-perform-message-assignments"></a><span data-ttu-id="a9eaf-102">如何使用運算式執行訊息指派</span><span class="sxs-lookup"><span data-stu-id="a9eaf-102">How to Use Expressions to Perform Message Assignments</span></span>
<span data-ttu-id="a9eaf-103">您可使用運算式在協調流程中以各種方式處理訊息。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-103">You can use expressions to manipulate messages in various ways in your orchestration.</span></span>  
  
## <a name="referring-to-message-fields"></a><span data-ttu-id="a9eaf-104">指稱訊息欄位</span><span class="sxs-lookup"><span data-stu-id="a9eaf-104">Referring to message fields</span></span>  
 <span data-ttu-id="a9eaf-105">您可將欄位名稱附加至訊息名稱，來指稱訊息中的不同欄位，方法如下：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-105">You can refer to a distinguished field in a message by appending the field name to the message name as follows:</span></span>  
  
```  
MyMsg.Amount  
```  
  
 <span data-ttu-id="a9eaf-106">在此範例中，MyMsg 是訊息，Amount 是已被識別為 MyMsg 所依據之訊息類型的辨別欄位。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-106">In this example, MyMsg is the message, and Amount is a field that has been identified as a distinguished field for the message type that MyMsg is based on.</span></span>  
  
## <a name="assigning-to-messages-and-message-parts"></a><span data-ttu-id="a9eaf-107">指派至訊息和訊息部分</span><span class="sxs-lookup"><span data-stu-id="a9eaf-107">Assigning to messages and message parts</span></span>  
 <span data-ttu-id="a9eaf-108">您可以將訊息直接指派至另一訊息，或將訊息部分直接指派至另一個訊息部分：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-108">You can assign a message directly to another message, or a message part to a message part:</span></span>  
  
```  
MyMsg=IncomingMsg;  
MyMsg.Invoice=IncomingMsg.Invoice;  
```  
  
 <span data-ttu-id="a9eaf-109">在此範例中，Invoice 是以結構描述為依據的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-109">In this example, Invoice is a message part based on a schema.</span></span>  
  
 <span data-ttu-id="a9eaf-110">若您想修改已建構的訊息 (例如已接收之訊息) 之屬性，您必須在 [建構訊息] 圖形中，將第一個訊息指派至第二個訊息來建構新訊息，然後在相同的 [建構訊息] 圖形內修改新訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-110">If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message by assigning the first to the second in a Construct Message shape, and modify the property on the new message within the same Construct Message shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9eaf-111">您不能對訊息欄位進行指稱或指派 (例如 MyMsg.Invoice.MyField)，除非這些訊息欄位已經升級；您只能對整個訊息、訊息部分、升級的訊息屬性或辨別欄位進行指稱或指派。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-111">You cannot refer or assign to message fields, such as MyMsg.Invoice.MyField, unless they have been promoted; you can only refer or assign to entire messages, message parts, promoted message properties, or distinguished fields.</span></span>  
  
## <a name="adding-message-parts"></a><span data-ttu-id="a9eaf-112">新增訊息部分</span><span class="sxs-lookup"><span data-stu-id="a9eaf-112">Adding message parts</span></span>  
 <span data-ttu-id="a9eaf-113">您可以將其他組件加入現有的 multipart 訊息使用**XLANGs.BaseTypes.XLANGMessage.AddPart**方法。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-113">You can add additional parts to an existing multipart message by using the **XLANGs.BaseTypes.XLANGMessage.AddPart** method.</span></span> <span data-ttu-id="a9eaf-114">若要這樣做，請執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-114">To do so, do the following:</span></span>  
  
-   <span data-ttu-id="a9eaf-115">建立 C# 專案，並將參考加入**Microsoft.XLANGs.BaseTypes**。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-115">Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes**.</span></span>  
  
-   <span data-ttu-id="a9eaf-116">實作類似於以下的公用類別：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-116">Implement a public class similar to the following:</span></span>  
  
    ```  
    public class MyAddPartHelper  
    {  
         public static void AddPart(XLANGMessage msg, object part, String partName)  
         {  
              msg.AddPart(part, partName);  
         }  
    }  
    ```  
  
     <span data-ttu-id="a9eaf-117">有三個多載的方法，如**Microsoft.XLANGs.BaseTypes.AddPart**:</span><span class="sxs-lookup"><span data-stu-id="a9eaf-117">There are three overloaded methods for **Microsoft.XLANGs.BaseTypes.AddPart**:</span></span>  
  
    ```  
    public void AddPart(object part, String partName);  
    public void AddPart(XLANGPart part);  
    public void AddPart(XLANGPart part, String partName);  
    ```  
  
-   <span data-ttu-id="a9eaf-118">在 BizTalk 專案中，新增參考的公用類別和呼叫**AddPart**方法從**運算式**圖形在協調流程中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-118">In your BizTalk project, add a reference to the public class and call the **AddPart** method from the **Expression** shape in your orchestration as follows:</span></span>  
  
    ```  
    MyAddPartHelper.AddPart(myMessage, myStringObject, “StringObject1”);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="a9eaf-119">您無法將非可序列化的物件或自訂格式化物件新增為訊息部分。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-119">You cannot add non-serializable objects or custom formatted objects as message parts.</span></span> <span data-ttu-id="a9eaf-120">必須先初始化所有的靜態部分新增其他部分使用**AddPart**方法。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-120">All static parts must be initialized before adding additional parts using the **AddPart** method.</span></span> <span data-ttu-id="a9eaf-121">只有在訊息的建構陳述式中，您才可以新增任意部分至此訊息。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-121">You can add arbitrary parts to a message only inside its message construct statement.</span></span> <span data-ttu-id="a9eaf-122">不支援在訊息建構陳述式的外面新增其他部分。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-122">Adding additional parts outside of the message construct statement is not supported.</span></span>  
  
## <a name="retrieving-message-parts"></a><span data-ttu-id="a9eaf-123">擷取訊息部分</span><span class="sxs-lookup"><span data-stu-id="a9eaf-123">Retrieving message parts</span></span>  
 <span data-ttu-id="a9eaf-124">您可以從現有的 multipart 訊息擷取訊息部分使用**RetrieveAs**方法從**Microsoft.XLANGs.BaseTypes**。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-124">You can retrieve a message part from an existing multipart message by using the **RetrieveAs** method from **Microsoft.XLANGs.BaseTypes**.</span></span> <span data-ttu-id="a9eaf-125">若要這樣做，請執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-125">To do so, do the following:</span></span>  
  
-   <span data-ttu-id="a9eaf-126">建立 C# 專案，並將參考加入**Microsoft.XLANGs.BaseTypes**。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-126">Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes**.</span></span>  
  
-   <span data-ttu-id="a9eaf-127">實作類似於以下的公用類別：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-127">Implement a public class similar to the following:</span></span>  
  
    ```  
    Public class MyAddPartHelper  
    {  
         public static Object GetPart(XLANGMessage msg, string sName, Type t)  
         {  
              XLANGPart p =  msg[sName];  
              return p.RetrieveAs(t);  
         }  
         public static Object GetPart(XLANGMessage msg, int partIndex, Type t)  
         {  
               XLANGPart p = msg[partIndex];  
               return p.RetrieveAs(t);  
          }  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a9eaf-128">**RetrieveAs**方法支援擷取訊息部分，依名稱和索引。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-128">The **RetrieveAs** method supports retrieving message parts by name and by index.</span></span>  
  
-   <span data-ttu-id="a9eaf-129">在 BizTalk 專案中，新增參考的公用類別和呼叫**GetPart**方法從**運算式**圖形在協調流程中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-129">In your BizTalk project, add a reference to the public class and call the **GetPart** method from the **Expression** shape in your orchestration as follows:</span></span>  
  
    ```  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, "StringObject1" , typeof(System.String));  
    //sPart is a type of System.String  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, 1, typeof(System.String));  
    //Retriving the message part with index = 1  
    ```  
  
## <a name="message-part-context-property-access"></a><span data-ttu-id="a9eaf-130">訊息部分內容屬性存取</span><span class="sxs-lookup"><span data-stu-id="a9eaf-130">Message part context property access</span></span>  
 <span data-ttu-id="a9eaf-131">訊息部分的內容與訊息內容不同。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-131">A message part has context separate from the message context.</span></span> <span data-ttu-id="a9eaf-132">當您設定時，您可以建構訊息部分內容屬性，透過結構描述編輯器**Property Schema Base**屬性相關聯的項目**PartContextPropertyBase。**</span><span class="sxs-lookup"><span data-stu-id="a9eaf-132">You can construct message part context properties through the schema editor when you set the **Property Schema Base** property for the associated element to **PartContextPropertyBase.**</span></span>  
  
 <span data-ttu-id="a9eaf-133">存取和訊息屬性類似，都是透過如下的運算式：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-133">The access is similar to message properties, through an expression like:</span></span>  
  
```  
Msg.PartName(myPartContextProperty)  
```  
  
 <span data-ttu-id="a9eaf-134">例如：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-134">For example:</span></span>  
  
```  
Str=Msg.PartName(myPartContextProperty); //assumes myPartContextProperty is of type string  
```  
  
## <a name="xlangmessage-context-property-access"></a><span data-ttu-id="a9eaf-135">XLANGMessage 內容屬性存取</span><span class="sxs-lookup"><span data-stu-id="a9eaf-135">XLANGMessage context property access</span></span>  
 <span data-ttu-id="a9eaf-136">如果您想要存取訊息屬性**XLANGMessage**介面從程式碼中，您可以將訊息傳遞做為參數的型別**Microsoft.XLANGs.BaseTypes.XLANGMessage**方法從運算式圖形，然後使用**Microsoft.XLANGs.BaseTypes.XLANGMessage**方法**SetPropertyValue**和**GetPropertyValue**來達成此。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-136">If you would like to access message properties from the **XLANGMessage** interface from your code, you can pass the message as a parameter of type **Microsoft.XLANGs.BaseTypes.XLANGMessage** to a method from an Expression shape, and then use the **Microsoft.XLANGs.BaseTypes.XLANGMessage** methods **SetPropertyValue** and **GetPropertyValue** to achieve this.</span></span> <span data-ttu-id="a9eaf-137">若要這樣做，請執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-137">To do so, do the following:</span></span>  
  
-   <span data-ttu-id="a9eaf-138">建立 C# 專案，並將參考加入**Microsoft.XLANGs.BaseTypes**和**Microsoft.BizTalk.GlobalPropertySchemas**。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-138">Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes** and **Microsoft.BizTalk.GlobalPropertySchemas**.</span></span>  
  
-   <span data-ttu-id="a9eaf-139">使用類似以下的程式碼來存取內容屬性：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-139">Access the context property using the code similar to the below:</span></span>  
  
    ```  
    MyMsg.GetPropertyValue(typeof(BTS.MessageID));  
    MyMsg.SetPropertyValue(typeof(MIME.IsMultipartRelated), true);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="a9eaf-140">如果您想要取得或設定自訂內容屬性，您需要新增對屬性結構描述專案的參考，或是新增對組件 (此組件包含 C# 專案中的屬性結構描述) 的參考。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-140">If you would like to get or set your own custom context properties, you need to add a reference to your property schema project or add a reference to the assembly contains the property schemas in your C# project.</span></span>  
  
## <a name="assigning-to-message-properties"></a><span data-ttu-id="a9eaf-141">指派至訊息屬性</span><span class="sxs-lookup"><span data-stu-id="a9eaf-141">Assigning to message properties</span></span>  
 <span data-ttu-id="a9eaf-142">您可以將某個值指派至訊息屬性：</span><span class="sxs-lookup"><span data-stu-id="a9eaf-142">You can assign a value to a message property:</span></span>  
  
```  
MyMessage(MySchemaNamespace.MyProperty)=True;  
```  
  
 <span data-ttu-id="a9eaf-143">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您可以對多部分訊息的 MIME 屬性進行指稱和指派值。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-143">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you can refer to and assign values to the MIME properties of a multi-part message:</span></span>  
  
```  
Message_Out.MessagePart_1(MIME.FileName)="document.doc";  
```  
  
> [!NOTE]
>  <span data-ttu-id="a9eaf-144">BizTalk 訊息是由訊息內容和訊息部分所組成。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-144">A BizTalk message consists of message context and message parts.</span></span> <span data-ttu-id="a9eaf-145">您必須先初始化訊息部分，然後才可以取得或設定任何訊息內容屬性，否則您在 XLANG 編譯時會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9eaf-145">You must first initialize the message parts before you can get or set any message context property; otherwise, you will receive error during the XLANG compile time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9eaf-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9eaf-146">See Also</span></span>  
 <span data-ttu-id="a9eaf-147">[協調流程中使用訊息](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="a9eaf-147">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="a9eaf-148">使用者程式碼中建構的訊息</span><span class="sxs-lookup"><span data-stu-id="a9eaf-148">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)   