---
title: 採用運算式的圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Expression Editor, shapes
- Decide shape [Orchestration Designer], expressions
- Message Assignment shape [Orchestration Designer], expressions
- Filter Expression property
- Listen shape [Orchestration Designer], expressions
- Delay shape [Orchestration Designer], expressions
- shapes, expressions
- Receive shape [Orchestration Designer], expressions
- Loop shape [Orchestration Designer], expressions
- Rule shape [Orchestration Designer]
ms.assetid: 0d27f711-ff7c-422b-b231-aa3c9a42ed0c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e78ada2c69205a0201c4bae9f3c7fa5b0656fa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270782"
---
# <a name="shapes-that-take-expressions"></a><span data-ttu-id="ec249-102">採用運算式的圖形</span><span class="sxs-lookup"><span data-stu-id="ec249-102">Shapes that Take Expressions</span></span>
<span data-ttu-id="ec249-103">數個圖形在協調流程設計師中，包括**決定**和**迴圈**，使用布林運算式來控制分支的格式規則。</span><span class="sxs-lookup"><span data-stu-id="ec249-103">Several shapes in Orchestration Designer, including **Decide** and **Loop**, use Boolean expressions to form rules that control branching.</span></span> <span data-ttu-id="ec249-104">其他的圖形則使用其他目的運算式。</span><span class="sxs-lookup"><span data-stu-id="ec249-104">Other shapes use expressions for other purposes.</span></span> <span data-ttu-id="ec249-105">您可以使用 BizTalk 運算式編輯器，為這些圖形建立或編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="ec249-105">You can create or edit an expression for these shapes by using BizTalk Expression Editor.</span></span>  
  
 <span data-ttu-id="ec249-106">下表摘要了使用協調流程設計師中運算式的圖形，並列出這些運算式的有效資料型別。</span><span class="sxs-lookup"><span data-stu-id="ec249-106">The following table summarizes the shapes that use expressions in Orchestration Designer and lists the data types that are valid for those expressions.</span></span>  
  
|<span data-ttu-id="ec249-107">形狀圖</span><span class="sxs-lookup"><span data-stu-id="ec249-107">Shape</span></span>|<span data-ttu-id="ec249-108">運算式使用的描述</span><span class="sxs-lookup"><span data-stu-id="ec249-108">Description of expression use</span></span>|<span data-ttu-id="ec249-109">有效的運算式資料型別</span><span class="sxs-lookup"><span data-stu-id="ec249-109">Valid expression data types</span></span>|  
|-----------|-----------------------------------|---------------------------------|  
|<span data-ttu-id="ec249-110">**決定**</span><span class="sxs-lookup"><span data-stu-id="ec249-110">**Decide**</span></span>|<span data-ttu-id="ec249-111">**決定**圖形包含**規則**圖形，它會使用布林值運算式。</span><span class="sxs-lookup"><span data-stu-id="ec249-111">**Decide** shapes contain **Rule** shapes, which use Boolean expressions.</span></span>|<span data-ttu-id="ec249-112">布林</span><span class="sxs-lookup"><span data-stu-id="ec249-112">Boolean</span></span>|  
|<span data-ttu-id="ec249-113">**接收**</span><span class="sxs-lookup"><span data-stu-id="ec249-113">**Receive**</span></span>|<span data-ttu-id="ec249-114">**接收**圖形，將啟動屬性設定為 True 使用**篩選條件運算式**屬性來篩選內送訊息。</span><span class="sxs-lookup"><span data-stu-id="ec249-114">**Receive** shapes that have the Activate property set to True use the **Filter Expression** property to filter incoming messages.</span></span> <span data-ttu-id="ec249-115">此屬性中的運算式必須評估為布林值，其值會決定是否接受內送訊息。</span><span class="sxs-lookup"><span data-stu-id="ec249-115">The expression in this property must evaluate to a Boolean, whose value determines whether or not to accept an incoming message.</span></span><br /><br /> <span data-ttu-id="ec249-116">**篩選條件運算式**對話方塊用來建立篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="ec249-116">The **Filter Expression** dialog box is used to create filter expressions.</span></span>|<span data-ttu-id="ec249-117">布林</span><span class="sxs-lookup"><span data-stu-id="ec249-117">Boolean</span></span>|  
|<span data-ttu-id="ec249-118">**迴圈**</span><span class="sxs-lookup"><span data-stu-id="ec249-118">**Loop**</span></span>|<span data-ttu-id="ec249-119">A**迴圈**圖形需要**規則**形狀，接著必須包含布林運算式。</span><span class="sxs-lookup"><span data-stu-id="ec249-119">A **Loop** shape requires a **Rule** shape, which in turn must contain a Boolean expression.</span></span>|<span data-ttu-id="ec249-120">布林</span><span class="sxs-lookup"><span data-stu-id="ec249-120">Boolean</span></span>|  
|<span data-ttu-id="ec249-121">**規則**</span><span class="sxs-lookup"><span data-stu-id="ec249-121">**Rule**</span></span>|<span data-ttu-id="ec249-122">**規則**圖形 （以 「 分支 」 圖形方式顯示於 「 處理區域） 是包含布林值運算式和其他 （複雜） 圖形中用來管理分支的簡單圖形。</span><span class="sxs-lookup"><span data-stu-id="ec249-122">**Rule** shapes (displayed on the Process Area as "branch" shapes) are simple shapes that contain Boolean expressions and are used within other (complex) shapes to govern branching.</span></span>|<span data-ttu-id="ec249-123">布林</span><span class="sxs-lookup"><span data-stu-id="ec249-123">Boolean</span></span>|  
|<span data-ttu-id="ec249-124">**接聽**</span><span class="sxs-lookup"><span data-stu-id="ec249-124">**Listen**</span></span>|<span data-ttu-id="ec249-125">每個分支**接聽**圖形包含，最少，請**接收**圖形，僅針對篩選條件運算式中使用布林運算式 (請參閱的項目**接收**)或**延遲**圖形，它會使用**System.DateTime**物件或**System.TimeSpan**物件。</span><span class="sxs-lookup"><span data-stu-id="ec249-125">Each branch of a **Listen** shape contains, at a minimum, either a **Receive** shape, which uses a Boolean expression only for filter expressions (see the entry for **Receive**), or a **Delay** shape, which uses a **System.DateTime** object or **System.TimeSpan** object.</span></span>|<span data-ttu-id="ec249-126">布林值、System.DateTime、System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="ec249-126">Boolean, System.DateTime, System.TimeSpan</span></span>|  
|<span data-ttu-id="ec249-127">**延遲**</span><span class="sxs-lookup"><span data-stu-id="ec249-127">**Delay**</span></span>|<span data-ttu-id="ec249-128">中使用的運算式**延遲**圖形必須評估為**System.DateTime**物件，以表示期限，或**System.TimeSpan**物件來表示持續時間。</span><span class="sxs-lookup"><span data-stu-id="ec249-128">The expression used in a **Delay** shape must evaluate to a **System.DateTime** object, to express a deadline, or a **System.TimeSpan** object, to express duration.</span></span>|<span data-ttu-id="ec249-129">System.DateTime、System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="ec249-129">System.DateTime, System.TimeSpan</span></span>|  
|<span data-ttu-id="ec249-130">**訊息指派**</span><span class="sxs-lookup"><span data-stu-id="ec249-130">**Message Assignment**</span></span>|<span data-ttu-id="ec249-131">中的運算式**訊息指派**圖形會將值指派至訊息。</span><span class="sxs-lookup"><span data-stu-id="ec249-131">The expression in a **Message Assignment** shape assigns a value to a message.</span></span> <span data-ttu-id="ec249-132">一般來說，雖然會指派訊息，但是指派的值可以是任何型別。</span><span class="sxs-lookup"><span data-stu-id="ec249-132">The value assigned can be of any type, though typically a message is assigned.</span></span>|<span data-ttu-id="ec249-133">任意</span><span class="sxs-lookup"><span data-stu-id="ec249-133">Any</span></span>|  
|<span data-ttu-id="ec249-134">**運算式**</span><span class="sxs-lookup"><span data-stu-id="ec249-134">**Expression**</span></span>|<span data-ttu-id="ec249-135">**運算式**圖形可讓您輸入您的協調流程中所選擇的運算式。</span><span class="sxs-lookup"><span data-stu-id="ec249-135">The **Expression** shape enables you to enter any expression you choose in your orchestration.</span></span> <span data-ttu-id="ec249-136">例如，您可以進行 .NET 呼叫以執行外部程式，或是只管理協調流程變數的值。</span><span class="sxs-lookup"><span data-stu-id="ec249-136">For example, you can make a .NET call to run an external program, or simply manipulate the values of your orchestration variables.</span></span>|<span data-ttu-id="ec249-137">任意</span><span class="sxs-lookup"><span data-stu-id="ec249-137">Any</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="ec249-138">本節內容</span><span class="sxs-lookup"><span data-stu-id="ec249-138">In This Section</span></span>  
 [<span data-ttu-id="ec249-139">如何使用運算式圖形</span><span class="sxs-lookup"><span data-stu-id="ec249-139">How to Use Expression Shape</span></span>](../core/how-to-use-expression-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec249-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec249-140">See Also</span></span>  
 <span data-ttu-id="ec249-141">[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="ec249-141">[Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md) </span></span>  
 <span data-ttu-id="ec249-142">[建構訊息](../core/constructing-messages.md) </span><span class="sxs-lookup"><span data-stu-id="ec249-142">[Constructing Messages](../core/constructing-messages.md) </span></span>  
 [<span data-ttu-id="ec249-143">設定流程控制圖形</span><span class="sxs-lookup"><span data-stu-id="ec249-143">Configuring Flow Control Shapes</span></span>](../core/configuring-flow-control-shapes.md)