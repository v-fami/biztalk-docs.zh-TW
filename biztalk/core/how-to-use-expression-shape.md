---
title: "如何使用運算式圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Expression shapes
- Expression shape [Orchestration Designer]
- Expression shape [Orchestration Designer], configuring
- Expression shape [Orchestration Designer], about Expression shape
ms.assetid: 2d702aa9-b824-4f47-a416-70707ce8ef29
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e263454db9674d5bc86b6b7dae1649003f3d129c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expression-shape"></a><span data-ttu-id="e6083-102">如何使用運算式圖形</span><span class="sxs-lookup"><span data-stu-id="e6083-102">How to Use Expression Shape</span></span>
<span data-ttu-id="e6083-103">**運算式**圖形可讓您輸入您的協調流程中所選擇的 XLANG/s 運算式。</span><span class="sxs-lookup"><span data-stu-id="e6083-103">The **Expression** shape enables you to enter any XLANG/s expression you choose in your orchestration.</span></span> <span data-ttu-id="e6083-104">例如，您可以進行 .NET 呼叫以執行外部程式，或是只管理協調流程變數的值。</span><span class="sxs-lookup"><span data-stu-id="e6083-104">For example, you can make a .NET call to run an external program, or simply manipulate the values of your orchestration variables.</span></span>  
  
 <span data-ttu-id="e6083-105">雖然**運算式**圖形相當具有彈性，並不適合用來執行高階協調流程邏輯，最好是會顯示在 協調流程繪圖本身中。</span><span class="sxs-lookup"><span data-stu-id="e6083-105">While the **Expression** shape is quite flexible, it is not good practice to use it to perform high-level orchestration logic, which preferably would be visible in the orchestration drawing itself.</span></span> <span data-ttu-id="e6083-106">一般情況下，很容易了解和維護您的協調流程，如果您**運算式**圖形包含簡單、 模組化的運算式。</span><span class="sxs-lookup"><span data-stu-id="e6083-106">In general, it is easier to understand and maintain your orchestrations if your **Expression** shapes contain simple and modular expressions.</span></span>  
  
### <a name="to-configure-an-expression-shape"></a><span data-ttu-id="e6083-107">設定運算式圖形</span><span class="sxs-lookup"><span data-stu-id="e6083-107">To configure an Expression shape</span></span>  
  
1.  <span data-ttu-id="e6083-108">如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下**運算式**圖形，並按一下**編輯運算式**或在 屬性 視窗中，按一下省略符號 (**...**) 按鈕**運算式**屬性。</span><span class="sxs-lookup"><span data-stu-id="e6083-108">If BizTalk Expression Editor is not visible, right-click the **Expression** shape and click **Edit Expression** or, in the Properties window, click the Ellipsis (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="e6083-109">在「BizTalk 運算式編輯器」中，建立運算式以指派值。</span><span class="sxs-lookup"><span data-stu-id="e6083-109">In BizTalk Expression Editor, create an expression to assign values.</span></span> <span data-ttu-id="e6083-110">如需詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e6083-110">For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6083-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6083-111">See Also</span></span>  
 [<span data-ttu-id="e6083-112">XLANG 的語言</span><span class="sxs-lookup"><span data-stu-id="e6083-112">XLANG-s Language</span></span>](../core/xlang-s-language.md)