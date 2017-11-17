---
title: "建構 Web 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, about Web messages
- Web messages, message types
- Web services, Web messages
- Web messages, parts
- Web messages
- messages, Web messages
ms.assetid: ca1792be-5fba-4f5d-a88e-b854f6a8ce33
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c344bbb836a6524ec1fd2656a5ba3f8bc8fad7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-web-messages"></a><span data-ttu-id="006ae-102">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="006ae-102">Constructing Web Messages</span></span>
<span data-ttu-id="006ae-103">您會從 Web 訊息類型建構 Web 訊息。</span><span class="sxs-lookup"><span data-stu-id="006ae-103">You construct a Web message from a Web message type.</span></span> <span data-ttu-id="006ae-104">新增 Web 參考時，BizTalk 會根據所新增 Web 服務的 Web 方法，自動建立 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-104">When you add a Web reference, BizTalk automatically creates Web message types, which BizTalk creates based on the Web methods from the added Web service.</span></span> <span data-ttu-id="006ae-105">您會在協調流程中新增 Web 訊息，並將訊息類型設定為其中一個 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-105">You add a Web message to your orchestration, setting the message type to one of the Web message types.</span></span> <span data-ttu-id="006ae-106">您會根據基本 .NET 或結構描述類型，建立個別的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="006ae-106">You create individual message parts based on primitive .NET or schema types.</span></span> <span data-ttu-id="006ae-107">您也可以建構不含任何訊息部分的 Web 訊息。</span><span class="sxs-lookup"><span data-stu-id="006ae-107">You can construct a Web message that contains no message parts.</span></span>  
  
 <span data-ttu-id="006ae-108">**Web 訊息類型**</span><span class="sxs-lookup"><span data-stu-id="006ae-108">**Web message types**</span></span>  
  
 <span data-ttu-id="006ae-109">Web 訊息類型是在 Reference.odx 中定義，除了無法修改、重新命名或刪除之外，與一般訊息類型完全相同。</span><span class="sxs-lookup"><span data-stu-id="006ae-109">Web message types, defined in the Reference.odx, are identical to a normal message type, except you cannot modify, rename or delete them.</span></span> <span data-ttu-id="006ae-110">若要刪除 Web 訊息類型，必須從 BizTalk 專案中移除 Web 參考。</span><span class="sxs-lookup"><span data-stu-id="006ae-110">To delete a Web message type, you must remove the Web reference from your BizTalk project.</span></span>  
  
 <span data-ttu-id="006ae-111">BizTalk 專案會針對該新增 Web 服務中的每個 Web 方法，分別建立一個要求和一個回應 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-111">BizTalk project creates one request and one response Web message type for each Web method in the added Web service.</span></span> <span data-ttu-id="006ae-112">如果 Web 方法是單向作業，BizTalk 將只會建立要求 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-112">If the Web method is a one-way operation, BizTalk only creates a request Web message type.</span></span> <span data-ttu-id="006ae-113">要求 Web 訊息類型會針對 Web 方法的各個輸入參數，分別包含一個訊息部分。</span><span class="sxs-lookup"><span data-stu-id="006ae-113">A request Web message type contains one message part for each input parameter of the Web method.</span></span> <span data-ttu-id="006ae-114">回應 Web 訊息類型則包含傳回值的一個訊息部分，並針對 Web 方法的各個輸出參數，分別包含一個訊息部分。</span><span class="sxs-lookup"><span data-stu-id="006ae-114">A response Web message type contains one message part for the return value and one message part for each output parameter of the Web method.</span></span>  
  
 <span data-ttu-id="006ae-115">BizTalk 會根據不同的 Web 方法參數 (輸入或輸出)，從基本 .NET 類型或結構描述類型建立 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-115">Depending on the Web method parameter (input or output), BizTalk creates a Web message type from a primitive .NET type or a schema type.</span></span> <span data-ttu-id="006ae-116">如果 Web 方法參數是基本 .NET 類型，訊息部分就會使用基本 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-116">If the Web method parameter is a primitive .NET type, the message part uses a primitive .NET type.</span></span> <span data-ttu-id="006ae-117">如果 Web 方法參數是結構描述類型，BizTalk 就會將該結構描述類型加入至 BizTalk 專案來做為 Reference.xsd 中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="006ae-117">If the Web method parameter is a schema type, BizTalk adds the schema type to the BizTalk project as a schema in Reference.xsd.</span></span> <span data-ttu-id="006ae-118">結構描述是訊息部分的基礎。</span><span class="sxs-lookup"><span data-stu-id="006ae-118">The schema is the basis for the message part.</span></span> <span data-ttu-id="006ae-119">您可以在 Web 參考資料夾中找到 Reference.xsd。</span><span class="sxs-lookup"><span data-stu-id="006ae-119">You can find Reference.xsd in the Web references folder.</span></span>  
  
 <span data-ttu-id="006ae-120">或者，您也可以藉由呼叫 .NET 類別，同時建立基本類型和結構描述 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-120">Alternatively, you can create both primitive and schema .NET types by calling a .NET class.</span></span> <span data-ttu-id="006ae-121">如需有關使用.NET 類別建立訊息類型的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="006ae-121">For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
 <span data-ttu-id="006ae-122">**Web 訊息**</span><span class="sxs-lookup"><span data-stu-id="006ae-122">**Web messages**</span></span>  
  
 <span data-ttu-id="006ae-123">當您使用 (呼叫) Web 服務時，您就會使用 Web 訊息。</span><span class="sxs-lookup"><span data-stu-id="006ae-123">Web messages are the messages you use when you consume (call) a Web service.</span></span> <span data-ttu-id="006ae-124">在協調流程中加入 Web 訊息與加入一般訊息的方式相同，唯一差異是訊息類型要設定為 BizTalk 在您加入 Web 參考時所建立的其中一種 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="006ae-124">You add a Web message to an orchestration the same way that you add a regular message, except that you set the message type to one of the Web message types that BizTalk created when you added a Web reference.</span></span>  
  
 <span data-ttu-id="006ae-125">**訊息部分**</span><span class="sxs-lookup"><span data-stu-id="006ae-125">**Message parts**</span></span>  
  
 <span data-ttu-id="006ae-126">建立 Web 訊息之後，您可以建構個別的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="006ae-126">After you create the Web message, you construct the individual message parts.</span></span> <span data-ttu-id="006ae-127">訊息部分使用基本.NET 類型，如果您使用**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="006ae-127">If your message part uses a primitive .NET type, you use a **Message Assignment** shape.</span></span> <span data-ttu-id="006ae-128">訊息部分使用結構描述型別，如果您使用**轉換**圖形或**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="006ae-128">If your message part uses a schema type, you use a **Transform** shape or **Message Assignment** shape.</span></span> <span data-ttu-id="006ae-129">如需詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="006ae-129">For more information, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="006ae-130">本節內容</span><span class="sxs-lookup"><span data-stu-id="006ae-130">In This Section</span></span>  
  
-   [<span data-ttu-id="006ae-131">如何新增 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="006ae-131">How to Add Web Messages</span></span>](../core/how-to-add-web-messages.md)  
  
-   [<span data-ttu-id="006ae-132">如何判斷 Web 訊息部分類型</span><span class="sxs-lookup"><span data-stu-id="006ae-132">How to Determine a Web Message Part Type</span></span>](../core/how-to-determine-a-web-message-part-type.md)  
  
-   [<span data-ttu-id="006ae-133">如何建構 Web 訊息部分，從基本.NET 類型</span><span class="sxs-lookup"><span data-stu-id="006ae-133">How to Construct a Web Message Part from a Primitive .NET Type</span></span>](../core/how-to-construct-a-web-message-part-from-a-primitive-net-type.md)  
  
-   [<span data-ttu-id="006ae-134">如何建構 Web 訊息部分的結構描述型別</span><span class="sxs-lookup"><span data-stu-id="006ae-134">How to Construct a Web Message Part from a Schema Type</span></span>](../core/how-to-construct-a-web-message-part-from-a-schema-type.md)  
  
-   [<span data-ttu-id="006ae-135">如何建構不含訊息部分的 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="006ae-135">How to Construct a Web Message with No Message Parts</span></span>](../core/how-to-construct-a-web-message-with-no-message-parts.md)