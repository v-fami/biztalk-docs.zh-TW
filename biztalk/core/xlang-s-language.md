---
title: XLANG 的語言 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, properties
ms.assetid: 97b62f17-5a8d-4d87-8563-1f6d941f027f
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2329d4bc42617d70227481a0d70064d368f3c0e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-language"></a><span data-ttu-id="0dc39-102">XLANG 的語言</span><span class="sxs-lookup"><span data-stu-id="0dc39-102">XLANG-s Language</span></span>
<span data-ttu-id="0dc39-103">XLANG/s 設計為可使用網際網路標準 (如 XML、XSD 和 Web 服務描述語言 (WSDL))，而且具有內嵌支援來處理 .NET 物件和訊息。</span><span class="sxs-lookup"><span data-stu-id="0dc39-103">XLANG/s was designed to use Internet standards such as XML, XSD, and Web Services Description Language (WSDL), and has embedded support for working with .NET-based objects and messages.</span></span> <span data-ttu-id="0dc39-104">XLANG/s 可視為具有某些 C# 運算式功能的訊息語言。</span><span class="sxs-lookup"><span data-stu-id="0dc39-104">XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#.</span></span> <span data-ttu-id="0dc39-105">但是，XLANG/s 與 C# 之間無法移植程式碼。</span><span class="sxs-lookup"><span data-stu-id="0dc39-105">However, code is not portable between XLANG/s and C#.</span></span>  
  
 <span data-ttu-id="0dc39-106">XLANG/s 鼓勵在處理與實作之間有清楚的分隔，</span><span class="sxs-lookup"><span data-stu-id="0dc39-106">XLANG/s encourages a clear separation between process and implementation.</span></span> <span data-ttu-id="0dc39-107">例如，在 XLANG/s 中指定商務程序或通訊協定，並在其他 .NET 程式語言 (如 C# 或 Visual Basic .NET) 中實作應用程式的本機層面 (如資料庫存取)。</span><span class="sxs-lookup"><span data-stu-id="0dc39-107">For example, the business process or protocol is specified in XLANG/s, and the local aspects of the application, such as database access, are implemented in other .NET programming languages such as C# or Visual Basic.NET.</span></span>  
  
 <span data-ttu-id="0dc39-108">XLANG/s 的指派和運算式語法是以 C# 當做模型，而且您應該參考 C# 規格，以瞭解精確的語法。</span><span class="sxs-lookup"><span data-stu-id="0dc39-108">XLANG/s assignment and expression syntax is modeled after C#, and you should reference the C# specification for exact syntax.</span></span> <span data-ttu-id="0dc39-109">XLANG/s 定義了一組豐富的高層級構造，這組構造是用來定義商務程序。</span><span class="sxs-lookup"><span data-stu-id="0dc39-109">XLANG/s defines a rich set of high-level constructs that are used to define business processes.</span></span> <span data-ttu-id="0dc39-110">雖然 XLANG/s 提供支援，如字串與整數類的低階資料類型，也會定義高層級的資料類型： 訊息、 連接埠、 相互關聯，以及服務連結。</span><span class="sxs-lookup"><span data-stu-id="0dc39-110">While XLANG/s provides support for low-level data types like string and integer, high-level data types are also defined: messages, ports, correlations, and service links.</span></span> <span data-ttu-id="0dc39-111">這些資料類型用來嚴格定義與商務程序相關聯的語意，和會輔以處理序控制陳述式例如**時**或**範圍**。</span><span class="sxs-lookup"><span data-stu-id="0dc39-111">These data types are used to rigorously define the semantics associated with a business process, and are complemented by process control statements such as **while** or **scope**.</span></span>  
  
 <span data-ttu-id="0dc39-112">XLANG/s 陳述式通常分為兩種類別： 簡單的陳述式會處理其本身，例如**接收**或**傳送**，和包含或是分組任一個簡單的陳述式的複雜陳述式或其他複雜的陳述式，例如**範圍**，**平行**，和**接聽**。</span><span class="sxs-lookup"><span data-stu-id="0dc39-112">XLANG/s statements generally fall into one of two categories: simple statements that act on their own, such as **receive** or **send**, and complex statements that contain or group either simple statements or other complex statements, such as **scope**, **parallel**, and **listen**.</span></span> <span data-ttu-id="0dc39-113">以 XLANG/s 具體化的語意是用來反映「Web 服務商務程序執行語言」(BPEL4WS) 規格所定義的語意 (此規格是由 Microsoft、IBM 和 BEA 針對商務程序語意的定義所發佈)。</span><span class="sxs-lookup"><span data-stu-id="0dc39-113">The semantics embodied in XLANG/s are a reflection of those defined in the Business Process Execution Language for Web Services (BPEL4WS) specification published by Microsoft, IBM, and BEA for the definition of business process semantics.</span></span>  
  
 <span data-ttu-id="0dc39-114">您可以選擇瞭解 XLANG/s 的主要構造，因為在 BizTalk 協調流程設計師中繪製協調流程圖時，會產生這些構造。</span><span class="sxs-lookup"><span data-stu-id="0dc39-114">Understanding the main constructs of XLANG/s is optional because they are produced as a result of drawing orchestration diagrams in BizTalk Orchestration Designer.</span></span> <span data-ttu-id="0dc39-115">協調流程設計師是一個功能豐富的圖形工具，可以視覺方式來設計商務程序。</span><span class="sxs-lookup"><span data-stu-id="0dc39-115">Orchestration Designer is a rich graphical tool for visually designing business processes.</span></span> <span data-ttu-id="0dc39-116">它會產生 XLANG/s 檔案，這些檔案具有 .odx 副檔名，而且其標頭中包含其他視覺資訊，本文中則包含自訂屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="0dc39-116">It generates XLANG/s files that have an .odx extension and contain additional visual information in their headers and custom attribute information in their bodies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0dc39-117">XLANG/s 語言是專屬的，而且未完整記錄。</span><span class="sxs-lookup"><span data-stu-id="0dc39-117">The XLANG/s language is proprietary and is not fully documented.</span></span> <span data-ttu-id="0dc39-118">本章節會公開當您開發協調流程時，可能需要注意的某些語言部分。</span><span class="sxs-lookup"><span data-stu-id="0dc39-118">This section exposes certain parts of the language that you might need to be aware of as you develop your orchestrations.</span></span> <span data-ttu-id="0dc39-119">不支援直接修改 .odx 檔案。</span><span class="sxs-lookup"><span data-stu-id="0dc39-119">Direct modification of the .odx files is not supported.</span></span>  
  
## <a name="xlangs-programs"></a><span data-ttu-id="0dc39-120">XLANG/s 程式</span><span class="sxs-lookup"><span data-stu-id="0dc39-120">XLANG/s Programs</span></span>  
 <span data-ttu-id="0dc39-121">最簡單的 XLANG/s 程式需要定義訊息類型，這樣可為協調流程提供一些資料來開始使用。</span><span class="sxs-lookup"><span data-stu-id="0dc39-121">The simplest XLANG/s program requires that a message type be defined, which gives the orchestration some data to start to work with.</span></span> <span data-ttu-id="0dc39-122">協調流程會透過連接埠接收訊息，然後終止。</span><span class="sxs-lookup"><span data-stu-id="0dc39-122">The orchestration receives the message over a port and then terminates.</span></span> <span data-ttu-id="0dc39-123">下列程式碼是一個範例：</span><span class="sxs-lookup"><span data-stu-id="0dc39-123">The following code is an example:</span></span>  
  
```  
module HelloWorldApp  
{  
     private porttype ptPOReceive  
     {  
      oneway opPOReceive  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private porttype ptPOSend  
     {  
      oneway opPOSend  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private service  HelloWorld  
     {  
      port implements HelloWorldApp.ptPOReceive poPOReceive;  
      port uses HelloWorldApp.ptPOSend poPOSend;  
      message HelloWorldApp.PurchaseOrder msgPO;  
      body ()  
      {  
       activate receive (poPOReceive.opPOReceive, msgPO);  
       send (poPOSend.opPOSend, msgPO);  
       }  
     }  
}  
```  
  
 <span data-ttu-id="0dc39-124">在上面的 XLANG/s 程式中，`module` 關鍵字會定義 XLANG/s 程式的編譯單位。</span><span class="sxs-lookup"><span data-stu-id="0dc39-124">In the preceding XLANG/s program, the `module` keyword defines the unit of compilations for an XLANG/s program.</span></span> <span data-ttu-id="0dc39-125">在程式中使用的所有類型 — 例如**porttype**， **correlationsettype**， **servicelinktype**，和**messagetype**— 設定於此層級。</span><span class="sxs-lookup"><span data-stu-id="0dc39-125">All types used in the program—such as **porttype**, **correlationsettype**, **servicelinktype**, and **messagetype**—are scoped at this level.</span></span>  
  
 <span data-ttu-id="0dc39-126">連接埠是 XLANG/s 可以傳送或接收訊息、 或的建構和連接埠有定義的類型，稱為**porttype**。</span><span class="sxs-lookup"><span data-stu-id="0dc39-126">A port is a construct that XLANG/s can send or receive messages to or from, and the port has a defined type called **porttype**.</span></span> <span data-ttu-id="0dc39-127">**Porttype**建構可定義可用的連接埠的作業的集合。</span><span class="sxs-lookup"><span data-stu-id="0dc39-127">The **porttype** construct defines a collection of operations that can be used on the port.</span></span> <span data-ttu-id="0dc39-128">這些作業會定義透過此連接埠的單一有效訊息交換。</span><span class="sxs-lookup"><span data-stu-id="0dc39-128">These operations define a single valid message exchange over the port.</span></span> <span data-ttu-id="0dc39-129">定義**porttype**， **messagetype**， **servicelinktype**，或**correlationsettype**建構，XLANG/s 的作者程式基本上建立複雜資料型別定義。</span><span class="sxs-lookup"><span data-stu-id="0dc39-129">In defining **porttype**, **messagetype**, **servicelinktype**, or **correlationsettype** constructs, the author of an XLANG/s program is essentially creating complex data type definitions.</span></span> <span data-ttu-id="0dc39-130">這些定義具有相同的優點與其他語言中複雜資料型別： 它們抽象概念卻中較高的層級的資料類型，而且可讓使用者容易重複使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0dc39-130">These definitions have the same advantages as complex data types do in other languages: They abstract the notions embodied in the data type to a higher level, and they allow for easy reuse of the data type.</span></span>  
  
 <span data-ttu-id="0dc39-131">**PtPOReceive**中之前 HelloWorldApp 模組會定義為單向連接埠接收連接埠作業**opPOReceive**。</span><span class="sxs-lookup"><span data-stu-id="0dc39-131">The **ptPOReceive** port in the preceding HelloWorldApp module is defined with a one-way receive port operation, **opPOReceive**.</span></span> <span data-ttu-id="0dc39-132">HelloWorld 服務區塊會定義此程序的實際實作以及它可能使用的任何變數 (包括連接埠和訊息變數)。</span><span class="sxs-lookup"><span data-stu-id="0dc39-132">The service HelloWorld block defines the actual implementation of the process and any variables it may use, including port and message variables.</span></span> <span data-ttu-id="0dc39-133">在這個區塊的程式碼的第一次三行定義的連接埠變數**poPOReceive**和**poPOSend**和訊息**msgPO**分別。</span><span class="sxs-lookup"><span data-stu-id="0dc39-133">The first three lines of code within this block define the port variables **poPOReceive** and **poPOSend** and the message **msgPO** respectively.</span></span> <span data-ttu-id="0dc39-134">本文包含的程式碼會描述此服務和執行行為的參數。</span><span class="sxs-lookup"><span data-stu-id="0dc39-134">The body contains the code describing parameters to the service and the execution behavior.</span></span> <span data-ttu-id="0dc39-135">所有的變數 (除非以巢狀範圍區塊定義) 都是以這個層級為範圍。</span><span class="sxs-lookup"><span data-stu-id="0dc39-135">All variables, unless defined with a nested scope block, are scoped to this level.</span></span> <span data-ttu-id="0dc39-136">Receive 陳述式，這是一項啟動接收，接收**msgPO**訊息從**Msgpo**連接埠，建立協調流程的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="0dc39-136">The receive statement, which is an activate receive, receives the **msgPO** message from the **poPOReceive.opPOReceive** port and creates a new instance of the orchestration.</span></span> <span data-ttu-id="0dc39-137">當收到訊息之後，傳送陳述式會將此訊息導向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0dc39-137">After the message is received, the send statement directs the message to a send port.</span></span> <span data-ttu-id="0dc39-138">在上述程式碼中的兩個連接埠宣告**poPOReceive**使用 implements 修飾詞，而**poPOSend**使用 uses 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0dc39-138">In the two port declarations in the preceding code, **poPOReceive** uses the implements modifier, whereas **poPOSend** uses the uses modifier.</span></span> <span data-ttu-id="0dc39-139">implements 修飾詞會告訴執行階段，它將要透過該連接埠來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="0dc39-139">The implements modifier tells the runtime it will be receiving a message over that port.</span></span> <span data-ttu-id="0dc39-140">uses 修飾詞會告訴執行階段，它將要透過該連接埠來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="0dc39-140">The uses modifier tells the runtime that it will be sending a message over that port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0dc39-141">本節內容</span><span class="sxs-lookup"><span data-stu-id="0dc39-141">In This Section</span></span>  
  
-   [<span data-ttu-id="0dc39-142">XLANG 的資料型別</span><span class="sxs-lookup"><span data-stu-id="0dc39-142">XLANG-s Data Types</span></span>](../core/xlang-s-data-types.md)  
  
-   [<span data-ttu-id="0dc39-143">XLANG s 陳述式</span><span class="sxs-lookup"><span data-stu-id="0dc39-143">XLANG-s Statements</span></span>](../core/xlang-s-statements.md)  
  
-   [<span data-ttu-id="0dc39-144">XLANG 的變數和運算子</span><span class="sxs-lookup"><span data-stu-id="0dc39-144">XLANG-s Variables and Operators</span></span>](../core/xlang-s-variables-and-operators.md)  
  
-   [<span data-ttu-id="0dc39-145">XLANG 的運算式</span><span class="sxs-lookup"><span data-stu-id="0dc39-145">XLANG-s Expressions</span></span>](../core/xlang-s-expressions.md)  
  
-   [<span data-ttu-id="0dc39-146">XLANG s 保留字</span><span class="sxs-lookup"><span data-stu-id="0dc39-146">XLANG-s Reserved Words</span></span>](../core/xlang-s-reserved-words.md)  
  
-   [<span data-ttu-id="0dc39-147">XLANG-s 至 BPEL4WS 型別轉換</span><span class="sxs-lookup"><span data-stu-id="0dc39-147">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)  
  
## <a name="see-also"></a><span data-ttu-id="0dc39-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc39-148">See Also</span></span>  
 [<span data-ttu-id="0dc39-149">關於 BizTalk 協調流程引擎</span><span class="sxs-lookup"><span data-stu-id="0dc39-149">About the BizTalk Orchestration Engine</span></span>](../core/about-the-biztalk-orchestration-engine.md)