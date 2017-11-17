---
title: "開發自訂管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom]
- pipeline components [custom], about pipeline components
- pipeline components [custom], creating
- customizing, pipeline components
- pipeline interfaces
- IDisassemblerComponent
- pipeline interfaces, about pipeline interfaces
- creating, pipeline components [custom]
- IAssemblerComponent
- IComponent
- pipeline components [custom], customizing
- pipeline interfaces, interface types
- pipeline components [custom], interfaces
- pipeline components [custom], component types
ms.assetid: cce61e0d-f1e3-4ec2-b38c-7c6eaf83ac10
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723cd04a2a907fdb5d770975c27d47e1752d08ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-pipeline-components"></a><span data-ttu-id="437c4-102">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="437c4-102">Developing Custom Pipeline Components</span></span>
<span data-ttu-id="437c4-103">本節描述如何開發管線元件。</span><span class="sxs-lookup"><span data-stu-id="437c4-103">This section describes how to develop a pipeline component.</span></span> <span data-ttu-id="437c4-104">您可建立三種管線元件類型：一般、組譯和反組譯。</span><span class="sxs-lookup"><span data-stu-id="437c4-104">You can create three types of pipeline components: general, assembling, and disassembling.</span></span> <span data-ttu-id="437c4-105">這三種類型都可額外實作探查功能。</span><span class="sxs-lookup"><span data-stu-id="437c4-105">Each of the three types can additionally implement probing functionality.</span></span> <span data-ttu-id="437c4-106">管線元件的每種類型有關聯的介面必須實作才能插入 「 BizTalk 傳訊引擎; 元件區分的元件類型的管線介面為**IComponent**， **IAssemblerComponent**，和**IDisassemblerComponent**。</span><span class="sxs-lookup"><span data-stu-id="437c4-106">Each type of pipeline component has an associated interface that must be implemented for the component to be plugged into the BizTalk Messaging Engine; the pipeline interfaces that distinguish the types of components are **IComponent**, **IAssemblerComponent**, and **IDisassemblerComponent**.</span></span> <span data-ttu-id="437c4-107">對於探查元件，您必須實作**IProbeMessage**介面。</span><span class="sxs-lookup"><span data-stu-id="437c4-107">For probing components, you must implement the **IProbeMessage** interface.</span></span>  
  
 <span data-ttu-id="437c4-108">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含您在建立自己的元件時可參考的範例管線元件。</span><span class="sxs-lookup"><span data-stu-id="437c4-108">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contains a sample pipeline component that you can reference when creating your own component.</span></span> <span data-ttu-id="437c4-109">此範例元件示範如何將資料附加至訊息結尾，以及如何在訊息開頭新增資料。</span><span class="sxs-lookup"><span data-stu-id="437c4-109">The sample component demonstrates how to append data to the end of a message and add data at the beginning of the message.</span></span> <span data-ttu-id="437c4-110">如需範例管線元件的詳細資訊，請參閱[CustomComponent （BizTalk Server 範例）](../core/customcomponent-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="437c4-110">For more information about the sample pipeline component, see [CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="437c4-111">如果您從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的管線參考自訂管線元件，可能會發生編譯階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="437c4-111">If you reference a custom pipeline component from a pipeline in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], a compile-time error may occur.</span></span> <span data-ttu-id="437c4-112">若要修正這個錯誤，請關閉管線設計師，並在編譯之前重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="437c4-112">To correct the error, close Pipeline Designer and reopen it before compiling.</span></span> <span data-ttu-id="437c4-113">或者，您也可以移除此元件，然後再新增它。</span><span class="sxs-lookup"><span data-stu-id="437c4-113">Alternatively, you can remove the component, and then add it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="437c4-114">升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，請確認現有自訂管線元件中的任何字串變數並未包含任何新行字元，例如 '\n'。</span><span class="sxs-lookup"><span data-stu-id="437c4-114">When upgrading to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], ensure that any string variables in your existing custom pipeline components do not contain any newline characters such as ‘\n’.</span></span> <span data-ttu-id="437c4-115">否則，在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中編譯這個元件時，將會出現「常數中包含新行字元」錯誤。</span><span class="sxs-lookup"><span data-stu-id="437c4-115">Otherwise, a “newline in constant” error will occur when compiling this component in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="437c4-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="437c4-116">In This Section</span></span>  
  
-   [<span data-ttu-id="437c4-117">使用管線介面</span><span class="sxs-lookup"><span data-stu-id="437c4-117">Using Pipeline Interfaces</span></span>](../core/using-pipeline-interfaces.md)  
  
-   [<span data-ttu-id="437c4-118">開發一般管線元件</span><span class="sxs-lookup"><span data-stu-id="437c4-118">Developing a General Pipeline Component</span></span>](../core/developing-a-general-pipeline-component.md)  
  
-   [<span data-ttu-id="437c4-119">開發組合管線元件</span><span class="sxs-lookup"><span data-stu-id="437c4-119">Developing an Assembling Pipeline Component</span></span>](../core/developing-an-assembling-pipeline-component.md)  
  
-   [<span data-ttu-id="437c4-120">開發解譯管線元件</span><span class="sxs-lookup"><span data-stu-id="437c4-120">Developing a Disassembling Pipeline Component</span></span>](../core/developing-a-disassembling-pipeline-component.md)  
  
-   [<span data-ttu-id="437c4-121">開發探查管線元件</span><span class="sxs-lookup"><span data-stu-id="437c4-121">Developing a Probing Pipeline Component</span></span>](../core/developing-a-probing-pipeline-component.md)  
  
-   [<span data-ttu-id="437c4-122">實作搜尋方法的 Managed 資料流管線元件中</span><span class="sxs-lookup"><span data-stu-id="437c4-122">Implementing a Seek Method in a Managed Streaming Pipeline Component</span></span>](../core/implementing-a-seek-method-in-a-managed-streaming-pipeline-component.md)  
  
-   [<span data-ttu-id="437c4-123">使用剖析和序列化引擎</span><span class="sxs-lookup"><span data-stu-id="437c4-123">Using the Parsing and Serializing Engines</span></span>](../core/using-the-parsing-and-serializing-engines.md)  
  
-   [<span data-ttu-id="437c4-124">報告管線元件錯誤</span><span class="sxs-lookup"><span data-stu-id="437c4-124">Reporting Errors from Pipeline Components</span></span>](../core/reporting-errors-from-pipeline-components.md)  
  
-   [<span data-ttu-id="437c4-125">部署管線元件</span><span class="sxs-lookup"><span data-stu-id="437c4-125">Deploying Pipeline Components</span></span>](../core/deploying-pipeline-components.md)  
  
-   [<span data-ttu-id="437c4-126">偵錯自訂管線</span><span class="sxs-lookup"><span data-stu-id="437c4-126">Debugging Custom Pipelines</span></span>](../core/debugging-custom-pipelines.md)