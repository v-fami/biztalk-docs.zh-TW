---
title: 協調流程開發中的步驟 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- designing, orchestrations
- orchestrations, designing
- orchestrations, creating
- creating, orchestrations
- Copy Local property
ms.assetid: 556b1e6c-63a6-4805-a0a5-e555f198fe4e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd0a19754871a6e736365e622513b193dcbf06a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277390"
---
# <a name="steps-in-orchestration-development"></a><span data-ttu-id="e4e1f-102">協調流程開發的步驟</span><span class="sxs-lookup"><span data-stu-id="e4e1f-102">Steps in Orchestration Development</span></span>
<span data-ttu-id="e4e1f-103">若要開發協調流程，您通常會執行下列基本動作：</span><span class="sxs-lookup"><span data-stu-id="e4e1f-103">To develop an orchestration, you typically perform the following basic actions:</span></span>  
  
-   <span data-ttu-id="e4e1f-104">新增圖形以代表您的商務程序。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-104">Add shapes to represent your business processes.</span></span>  
  
     <span data-ttu-id="e4e1f-105">「協調流程設計師」提供一個圖形工具箱，可以用來代表不同的動作或其他抽象概念。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-105">Orchestration Designer provides you with a toolbox of shapes that can be used to represent different actions or other abstractions.</span></span> <span data-ttu-id="e4e1f-106">如需詳細資訊，請參閱[協調流程圖形](../core/orchestration-shapes.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-106">For more information, see [Orchestration Shapes](../core/orchestration-shapes.md).</span></span>  
  
-   <span data-ttu-id="e4e1f-107">定義結構描述以說明訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-107">Define schemas to describe the format of your messages.</span></span>  
  
     <span data-ttu-id="e4e1f-108">您可以使用「BizTalk 編輯器」定義結構描述。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-108">You can define schemas with BizTalk Editor.</span></span> <span data-ttu-id="e4e1f-109">如需詳細資訊，請參閱[如何建立 XML 訊息結構描述](../core/how-to-create-schemas-for-xml-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-109">For more information, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).</span></span>  
  
-   <span data-ttu-id="e4e1f-110">定義傳送和接收訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-110">Define ports through which messages are sent and received.</span></span>  
  
     <span data-ttu-id="e4e1f-111">您可以定義連接埠，以指定訊息傳送和接收的方式和位置。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-111">You can define ports to specify how and where messages are sent and received.</span></span> <span data-ttu-id="e4e1f-112">如需詳細資訊，請參閱[協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-112">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
-   <span data-ttu-id="e4e1f-113">繫結**傳送**和**接收**圖形到連接埠。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-113">Bind **Send** and **Receive** shapes to ports.</span></span>  
  
     <span data-ttu-id="e4e1f-114">您可以連接您**傳送**和**接收**圖形連接到連接埠，並指定它們使用的連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-114">You can connect your **Send** and **Receive** shapes to ports and specify the port operations that they use.</span></span> <span data-ttu-id="e4e1f-115">如需詳細資訊，請參閱[如何設定 「 傳送 」 圖形](../core/how-to-configure-the-send-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-115">For more information, see [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md).</span></span> <span data-ttu-id="e4e1f-116">另請參閱[如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-116">Also see [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md).</span></span>  
  
-   <span data-ttu-id="e4e1f-117">在訊息之間指派或轉換資料。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-117">Assign or transform data between messages.</span></span>  
  
     <span data-ttu-id="e4e1f-118">您可以使用**建構訊息**圖形，以指派訊息值或執行訊息轉換。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-118">You can use the **Construct Message** shape to assign message values or do message transformations.</span></span> <span data-ttu-id="e4e1f-119">如需詳細資訊，請參閱[建構訊息](../core/constructing-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-119">For more information, see [Constructing Messages](../core/constructing-messages.md).</span></span>  
  
-   <span data-ttu-id="e4e1f-120">指定您要撰寫或新增為參考，以便在協調流程中使用的任何自訂元件。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-120">Identify any custom components that you might want to write or add as reference to work within your orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4e1f-121">如果**複製到本機**參考組件的屬性設定為**True**，協調流程將無法拾取之後的初始新增參考的外部組件所做的變更BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-121">If the **Copy Local** property of the referenced assembly is set to **True**, Orchestration will not be able to pick up any changes made to the external assembly after the initial add reference takes place in BizTalk project.</span></span>  
  
-   <span data-ttu-id="e4e1f-122">定義和指派協調流程變數，以管理您正在執行的協調流程中的資料。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-122">Define and assign orchestration variables to manage data in your running orchestration.</span></span>  
  
     <span data-ttu-id="e4e1f-123">您可以使用 [協調流程檢視] 視窗中的 [變數] 資料夾，以宣告您的協調流程變數，以及使用「BizTalk 運算式編輯器」，以編輯可指派和使用不同圖形中的變數之運算式。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-123">You can use the Variables folder in the Orchestration View window to declare your orchestration variables, and BizTalk Expression Editor to edit expressions that assign and use the variables in various shapes.</span></span> <span data-ttu-id="e4e1f-124">如需詳細資訊，請參閱[XLANG 的資料型別](../core/xlang-s-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-124">For more information, see [XLANG-s Data Types](../core/xlang-s-data-types.md).</span></span>  
  
-   <span data-ttu-id="e4e1f-125">建置協調流程以測試是否完整。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-125">Build your orchestration to test it for completeness.</span></span>  
  
     <span data-ttu-id="e4e1f-126">當您編譯專案或包含該專案的解決方案時，需要建置協調流程。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-126">You build your orchestration when you compile the project or solution that contains it.</span></span> <span data-ttu-id="e4e1f-127">如需詳細資訊，請參閱[如何建置協調流程](../core/how-to-build-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e1f-127">For more information, see [How to Build Orchestrations](../core/how-to-build-orchestrations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e1f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4e1f-128">See Also</span></span>  
 <span data-ttu-id="e4e1f-129">[建置和執行協調流程](../core/building-and-running-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="e4e1f-129">[Building and Running Orchestrations](../core/building-and-running-orchestrations.md) </span></span>  
 <span data-ttu-id="e4e1f-130">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="e4e1f-130">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="e4e1f-131">建立協調流程使用協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="e4e1f-131">Creating Orchestrations Using Orchestration Designer</span></span>](../core/creating-orchestrations-using-orchestration-designer.md)