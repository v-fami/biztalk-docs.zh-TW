---
title: 如何測試原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, policies
- Business Rule Composer, testing
- Business Rule Composer, policies
- testing, Business Rule Composer
- policies, testing
ms.assetid: 122dee26-d1f1-49a6-a6d5-a9d3d861a66b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7a0f8c0d63d14d5a529039a6e1c8af5b363cc9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255806"
---
# <a name="how-to-test-policies"></a><span data-ttu-id="e279e-102">如何測試原則</span><span class="sxs-lookup"><span data-stu-id="e279e-102">How to Test Policies</span></span>
<span data-ttu-id="e279e-103">若要測試原則，您需要可在其上執行規則的事實。</span><span class="sxs-lookup"><span data-stu-id="e279e-103">To test a policy, you need facts on which the rules can be executed.</span></span> <span data-ttu-id="e279e-104">您可以透過指定 XML 文件中的值或指定您要在原則測試器中指向的資料庫資料表，以新增事實，或是使用事實建立者以提供 .NET 物件陣列給引擎作為事實。</span><span class="sxs-lookup"><span data-stu-id="e279e-104">You can add facts by specifying values in XML documents or database tables that you will point to in the policy tester, or you can use a fact creator to supply to the engine an array of .NET objects as facts.</span></span> <span data-ttu-id="e279e-105">如需詳細資訊，請參閱[建立事實建立者](../core/how-to-create-a-fact-creator.md)。</span><span class="sxs-lookup"><span data-stu-id="e279e-105">For more information, see [Creating a Fact Creator](../core/how-to-create-a-fact-creator.md).</span></span>  
  
### <a name="to-test-a-policy-in-the-business-rule-composer"></a><span data-ttu-id="e279e-106">在商務規則編輯器中測試原則</span><span class="sxs-lookup"><span data-stu-id="e279e-106">To test a policy in the Business Rule Composer</span></span>  
  
1.  <span data-ttu-id="e279e-107">在 [原則總管] 視窗中，按一下您要測試的原則版本。</span><span class="sxs-lookup"><span data-stu-id="e279e-107">In the Policy Explorer window, click the policy version that you want to test.</span></span>  
  
2.  <span data-ttu-id="e279e-108">按一下**測試原則**功能表列上的按鈕 （綠色箭頭）。</span><span class="sxs-lookup"><span data-stu-id="e279e-108">Click the **Test Policy** button (green arrow) on the menu bar.</span></span>  
  
     <span data-ttu-id="e279e-109">頂端窗格會顯示原則規則參考的事實類型。</span><span class="sxs-lookup"><span data-stu-id="e279e-109">The top pane displays the fact types that the policy rules reference.</span></span>  
  
3.  <span data-ttu-id="e279e-110">若要新增事實執行個體，請按一下**XML 文件**或**資料庫資料表**事實類型，然後再按**新增執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e279e-110">To add a fact instance, click an **XML Document** or **Database Table** fact type, and then click **Add Instance**.</span></span>  
  
4.  <span data-ttu-id="e279e-111">如果您想要移除事實執行個體，按一下對應的事實類型，然後按一下**移除執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e279e-111">If you want to remove a fact instance, click the corresponding fact type, and then click **Remove Instance**.</span></span>  
  
5.  <span data-ttu-id="e279e-112">如果您想要新增您所撰寫的事實建立者，請按一下**新增**事實建立者窗格中。</span><span class="sxs-lookup"><span data-stu-id="e279e-112">If you want to add a fact creator that you have written, click **Add** in the fact creator pane.</span></span>  
  
6.  <span data-ttu-id="e279e-113">按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="e279e-113">Click **Test**.</span></span>  
  
     <span data-ttu-id="e279e-114">原則測試追蹤輸出會顯示在測試輸出視窗中。</span><span class="sxs-lookup"><span data-stu-id="e279e-114">The policy test trace output appears in the test output window.</span></span>  
  
7.  <span data-ttu-id="e279e-115">在輸出視窗中，使用滑鼠右鍵按一下以儲存、清除、選取或複製輸出文字。</span><span class="sxs-lookup"><span data-stu-id="e279e-115">Right-click in the output window to save, clear, select, or copy the output text.</span></span>  
  
     ![](../core/media/ebiz-testpolicy.gif "ebiz_testpolicy")  
<span data-ttu-id="e279e-116">選取事實以測試原則</span><span class="sxs-lookup"><span data-stu-id="e279e-116">Selecting fact to test a policy</span></span>