---
title: 運算式的需求與限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Expression Editor, about Expression Editor
- Expression Editor, requirements
- Orchestration Designer, Expression Editor
- Expression Editor, limitations
- Expression Editor
- Expression Editor, Orchestration Designer
ms.assetid: 1e0353d3-c2f3-4c10-86e3-8620e62dd0d5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd819850f62d47c640753e843325c9851da177b5
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22268382"
---
# <a name="requirements-and-limitations-for-expressions"></a><span data-ttu-id="a5589-102">運算式的需求和限制</span><span class="sxs-lookup"><span data-stu-id="a5589-102">Requirements and Limitations for Expressions</span></span>
<span data-ttu-id="a5589-103">協調流程設計師中的 [BizTalk 運算式編輯器] 是標準的 Visual Studio 文字編輯器，這表示它會提供 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="a5589-103">BizTalk Expression Editor in Orchestration Designer is a standard Visual Studio text editor, which means it offers IntelliSense.</span></span> <span data-ttu-id="a5589-104">您可以使用 [BizTalk 運算式編輯器] 輸入文字格式的運算式。</span><span class="sxs-lookup"><span data-stu-id="a5589-104">You use BizTalk Expression Editor to enter an expression in textual form.</span></span>  
  
 <span data-ttu-id="a5589-105">使用文字方塊，以文字格式輸入單一運算式。</span><span class="sxs-lookup"><span data-stu-id="a5589-105">Use the text box to enter a single expression in textual form.</span></span> <span data-ttu-id="a5589-106">運算式可以跨越多行，但必須以一個分號結尾。</span><span class="sxs-lookup"><span data-stu-id="a5589-106">The expression can span multiple lines, but must end with single semicolon.</span></span>  
  
 <span data-ttu-id="a5589-107">以下列出在 [BizTalk 運算式編輯器] 中使用運算式時的限制：</span><span class="sxs-lookup"><span data-stu-id="a5589-107">The following is a list of limitations when using expressions in the BizTalk Expression Editor:</span></span>  
  
-   <span data-ttu-id="a5589-108">不支援複合指派，例如 "+="、"-=" 或 "\*="。</span><span class="sxs-lookup"><span data-stu-id="a5589-108">Compound assignment such as "+=", "-=", or "\*=" is not supported.</span></span>  
  
-   <span data-ttu-id="a5589-109">不支援在陳述式中使用一個以上的設定運算子。</span><span class="sxs-lookup"><span data-stu-id="a5589-109">More than one assignment operator in a statement is not supported.</span></span>  
  
-   <span data-ttu-id="a5589-110">不支援在 "if" 或 "while" 述詞中使用指派。</span><span class="sxs-lookup"><span data-stu-id="a5589-110">Assignment within an “if” or “while” predicate is not supported.</span></span>  
  
-   <span data-ttu-id="a5589-111">不支援遞增和遞減。</span><span class="sxs-lookup"><span data-stu-id="a5589-111">Increment and decrement are not supported.</span></span> <span data-ttu-id="a5589-112">例如，"++" 和 "--"。</span><span class="sxs-lookup"><span data-stu-id="a5589-112">For example, "++" and "--".</span></span>  
  
-   <span data-ttu-id="a5589-113">對於訊息部分，允許在公用方法、巢狀型別、靜態資料欄位、有 Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute 註解的唯讀 .NET 屬性、所有公用資料欄位和非唯讀 .NET 屬性上使用成員存取。</span><span class="sxs-lookup"><span data-stu-id="a5589-113">For message parts, member access is allowed on public methods, nested types, static data fields, read-only .NET properties when annotated with Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute, all public data fields, and non-read-only .NET properties.</span></span>  
  
-   <span data-ttu-id="a5589-114">不支援索引子或參數化 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="a5589-114">Indexers or parameterized .NET properties are not supported.</span></span>  
  
-   <span data-ttu-id="a5589-115">不支援委派和事件。</span><span class="sxs-lookup"><span data-stu-id="a5589-115">Delegates and events are not supported.</span></span>  
  
-   <span data-ttu-id="a5589-116">不支援泛型。</span><span class="sxs-lookup"><span data-stu-id="a5589-116">Generics are not supported.</span></span>  
  
-   <span data-ttu-id="a5589-117">不支援流程控制語法，例如 "foreach"、"for"、"do-while"、"break" 和 "continue"。</span><span class="sxs-lookup"><span data-stu-id="a5589-117">Flow control syntax such as "foreach", "for", "do-while", "break", and "continue" are not supported.</span></span>  
  
-   <span data-ttu-id="a5589-118">不支援三元運算。</span><span class="sxs-lookup"><span data-stu-id="a5589-118">Ternary operations are not supported.</span></span> <span data-ttu-id="a5589-119">例如，"?:"。</span><span class="sxs-lookup"><span data-stu-id="a5589-119">For example, "?:".</span></span>  
  
-   <span data-ttu-id="a5589-120">您可以在「運算式」圖形中加入註解，但是「運算式」圖形必須包含至少一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="a5589-120">You can add comments in the Expression shape, but the Expression shape must contain at least one statement.</span></span>  
  
-   <span data-ttu-id="a5589-121">不支援陣列。</span><span class="sxs-lookup"><span data-stu-id="a5589-121">Arrays are not supported.</span></span>  
  
-   <span data-ttu-id="a5589-122">將「運算式」圖形置入「建構訊息」圖形時，您不可以加入任何控制流程。</span><span class="sxs-lookup"><span data-stu-id="a5589-122">When the Expression shape is placed in a Construct Message shape, you cannot do any control flow.</span></span> <span data-ttu-id="a5589-123">例如，"if-then-else" 或 "while"。</span><span class="sxs-lookup"><span data-stu-id="a5589-123">For example, "if-then-else" or "while".</span></span>  
  
-   <span data-ttu-id="a5589-124">所有有效的運算式陳述式，格式應為：</span><span class="sxs-lookup"><span data-stu-id="a5589-124">All valid expression statements are of the form:</span></span>  
  
    -   <span data-ttu-id="a5589-125">Dotted-name = expression;</span><span class="sxs-lookup"><span data-stu-id="a5589-125">Dotted-name = expression;</span></span>  
  
    -   <span data-ttu-id="a5589-126">Dotted-name = expression;</span><span class="sxs-lookup"><span data-stu-id="a5589-126">Dotted-name = expression;</span></span>  
  
 <span data-ttu-id="a5589-127">雖然使用 [BizTalk 運算式編輯器]，可以輕鬆快速地輸入複雜的運算式，但是您不可以用它輸入任意數量的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a5589-127">Though you can use BizTalk Expression Editor to enter complex expressions easily and quickly, you cannot use it to enter an arbitrary amount of code.</span></span> <span data-ttu-id="a5589-128">究其原因，是為了讓商務程序的程式碼與其實作程式碼分開。</span><span class="sxs-lookup"><span data-stu-id="a5589-128">The reason for this is to keep code for the business process separate from its implementation code.</span></span>