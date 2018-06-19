---
title: 如何建立運算式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, expressions [Expression Editor]
- opening, Expression Editor [Orchestration Designer]
- Expression Editor, opening
- editing, expressions [Expression Editor]
- Expression Editor, editing expressions
- Expression Editor, creating expressions
ms.assetid: 48f8b00f-6ef1-4145-ad17-15c95518fc8a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d4dbb6e5494856abea00a999a455542c5f4996e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248862"
---
# <a name="how-to-create-expressions"></a><span data-ttu-id="d643c-102">如何建立運算式</span><span class="sxs-lookup"><span data-stu-id="d643c-102">How to Create Expressions</span></span>
<span data-ttu-id="d643c-103">「BizTalk 運算式編輯器」可讓您建立 XLANG/s 運算式，以擴充各種「協調流程設計師」圖形的功能。</span><span class="sxs-lookup"><span data-stu-id="d643c-103">BizTalk Expression Editor enables you to create XLANG/s expressions to expand the capabilities of various Orchestration Designer shapes.</span></span> <span data-ttu-id="d643c-104">您可以建立 XLANG/s 運算式以進行決定、設定延遲、進行 .NET 呼叫，以及測試 while 迴圈條件。</span><span class="sxs-lookup"><span data-stu-id="d643c-104">You can create XLANG/s expressions to make decisions, set delays, make .NET calls, and test while loop conditions.</span></span>  
  
 <span data-ttu-id="d643c-105">它可讓您將值指派給訊息或訊息部分，在訊息指派圖形中，以及進行.NET 呼叫和操作中的變數值**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="d643c-105">It enables you to assign values to messages or message parts in the Message Assignment shape, and to make .NET calls and manipulate the values of variables in the **Expression** shape.</span></span> <span data-ttu-id="d643c-106">您也可以使用它來建構複雜的布林運算式中**迴圈**和**決定**圖形，並設定延遲**延遲**圖形。</span><span class="sxs-lookup"><span data-stu-id="d643c-106">You can also use it to construct complex Boolean expressions in the **Loop** and **Decide** shapes, and to set a delay in the **Delay** shape.</span></span>  
  
### <a name="to-open-biztalk-expression-editor"></a><span data-ttu-id="d643c-107">若要開啟 BizTalk 運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="d643c-107">To open BizTalk Expression Editor</span></span>  
  
1.  <span data-ttu-id="d643c-108">以滑鼠右鍵按一下**運算式**圖形，**迴圈**圖形，**訊息指派**圖形，**延遲**圖案或分支**決定**圖形。</span><span class="sxs-lookup"><span data-stu-id="d643c-108">Right-click an **Expression** shape, a **Loop** shape, a **Message Assignment** shape, a **Delay** shape, or a branch of a **Decide** shape.</span></span>  
  
2.  <span data-ttu-id="d643c-109">按一下**編輯運算式**。</span><span class="sxs-lookup"><span data-stu-id="d643c-109">Click **Edit Expression**.</span></span>  
  
3.  <span data-ttu-id="d643c-110">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="d643c-110">BizTalk Expression Editor appears.</span></span>  
  
### <a name="to-create-or-edit-an-expression"></a><span data-ttu-id="d643c-111">若要建立或編輯運算式</span><span class="sxs-lookup"><span data-stu-id="d643c-111">To create or edit an expression</span></span>  
  
1.  <span data-ttu-id="d643c-112">在「BizTalk 運算式編輯器」的文字欄位中輸入或編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="d643c-112">Type or edit the expression in the text field of BizTalk Expression Editor.</span></span>  
  
2.  <span data-ttu-id="d643c-113">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d643c-113">Click OK.</span></span> <span data-ttu-id="d643c-114">這樣便會儲存運算式並將其套用到選取的圖形。</span><span class="sxs-lookup"><span data-stu-id="d643c-114">This saves the expression and applies it to the selected shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d643c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d643c-115">See Also</span></span>  
 [<span data-ttu-id="d643c-116">XLANG 的語言</span><span class="sxs-lookup"><span data-stu-id="d643c-116">XLANG-s Language</span></span>](../core/xlang-s-language.md)