---
title: "建構訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- multi-part message types
- messages, modifying
- multi-part message types, about multi-part message types
- modifying, messages
- messages, creating
ms.assetid: c9fc1e97-ff53-42e2-848c-6c8fae7c9122
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fa87c4f3400a80ce83df132747d0004232323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-messages"></a><span data-ttu-id="d493f-102">建構訊息</span><span class="sxs-lookup"><span data-stu-id="d493f-102">Constructing Messages</span></span>
<span data-ttu-id="d493f-103">每次將訊息導入協調流程時，您都可以透過擷取訊息或指派值給訊息變數的方式來建構訊息。</span><span class="sxs-lookup"><span data-stu-id="d493f-103">You construct a message any time that you introduce a message into your orchestration, either by receiving it or by assigning values to a message variable.</span></span> <span data-ttu-id="d493f-104">您所建構的任何訊息都必須具有訊息類型，如此執行階段才會擁有其所使用之物件的完整描述。</span><span class="sxs-lookup"><span data-stu-id="d493f-104">Any message that you construct must have a message type, so that the runtime engine has a complete description of the object that it is working with.</span></span> <span data-ttu-id="d493f-105">多部分訊息類型可以是使用者定義、.NET 類別或結構描述。</span><span class="sxs-lookup"><span data-stu-id="d493f-105">The multi-part message type can be user-defined, it can be a .NET class, or it can be a schema.</span></span> <span data-ttu-id="d493f-106">您可以建構訊息以各種方式： 您可以叫用.NET 類別來建立訊息、 將某個訊息指派到另一個，或使用轉換來將訊息內特定的值對應到另一則訊息內的值。</span><span class="sxs-lookup"><span data-stu-id="d493f-106">You can construct messages in various ways: you can invoke a .NET class to create a message, assign one message to another, or use a transform to map certain values within a message to values within another message.</span></span> <span data-ttu-id="d493f-107">訊息也可由接收動作建構，或是在您的協調流程接受訊息做為參數時建構。</span><span class="sxs-lookup"><span data-stu-id="d493f-107">Messages are also constructed by a receive action or when your orchestration accepts a message as a parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d493f-108">多部分訊息類型不一定要包含多個部分；這種訊息可能只包含一個部分。</span><span class="sxs-lookup"><span data-stu-id="d493f-108">A multi-part message type does not necessarily contain multiple parts; it might contain just one.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d493f-109">訊息在 BizTalk 中是不變；也就是說，一旦您建構了訊息，便無法修改原始訊息。</span><span class="sxs-lookup"><span data-stu-id="d493f-109">Messages are immutable in BizTalk; that is, once you have constructed it, you cannot modify the original.</span></span> <span data-ttu-id="d493f-110">如果需要進行變更，您必須建構訊息的新複本，然後為它指派適當的值。</span><span class="sxs-lookup"><span data-stu-id="d493f-110">If you need to make a change, you must construct a new copy of the message and assign values to it appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d493f-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="d493f-111">In This Section</span></span>  
 [<span data-ttu-id="d493f-112">如何設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="d493f-112">How to Configure the Construct Message Shape</span></span>](../core/how-to-configure-the-construct-message-shape.md)  
  
 [<span data-ttu-id="d493f-113">如何設定訊息指派圖形</span><span class="sxs-lookup"><span data-stu-id="d493f-113">How to Configure the Message Assignment Shape</span></span>](../core/how-to-configure-the-message-assignment-shape.md) 
  
 [<span data-ttu-id="d493f-114">如何設定 「 轉換 」 圖形</span><span class="sxs-lookup"><span data-stu-id="d493f-114">How to Configure the Transform Shape</span></span>](../core/how-to-configure-the-transform-shape.md) 
  
 [<span data-ttu-id="d493f-115">訊息指派圖形中的訊息參考</span><span class="sxs-lookup"><span data-stu-id="d493f-115">Message References in Message Assignment Shape</span></span>](../core/message-references-in-message-assignment-shape.md)  
  
 [<span data-ttu-id="d493f-116">使用者程式碼中的訊息參考</span><span class="sxs-lookup"><span data-stu-id="d493f-116">Message References in User Code</span></span>](../core/message-references-in-user-code.md)  
  
 [<span data-ttu-id="d493f-117">訊息指派中使用 Xpath</span><span class="sxs-lookup"><span data-stu-id="d493f-117">Using XPaths in Message Assignments</span></span>](../core/using-xpaths-in-message-assignments.md)  
  
 [<span data-ttu-id="d493f-118">訊息指派中使用非標準 Xpath</span><span class="sxs-lookup"><span data-stu-id="d493f-118">Using Non-Canonical XPaths in Message Assignments</span></span>](../core/using-non-canonical-xpaths-in-message-assignments.md)  
  
 [<span data-ttu-id="d493f-119">使用者程式碼中建構的訊息</span><span class="sxs-lookup"><span data-stu-id="d493f-119">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)  
  
 [<span data-ttu-id="d493f-120">將節點附加至使用者程式碼中的訊息</span><span class="sxs-lookup"><span data-stu-id="d493f-120">Appending Nodes to Messages in User Code</span></span>](../core/appending-nodes-to-messages-in-user-code.md)  
  
## <a name="see-also"></a><span data-ttu-id="d493f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d493f-121">See Also</span></span>  
 [<span data-ttu-id="d493f-122">協調流程中使用訊息</span><span class="sxs-lookup"><span data-stu-id="d493f-122">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)