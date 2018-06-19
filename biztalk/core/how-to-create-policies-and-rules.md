---
title: 如何建立原則和規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, business rules
- policies, rules
- policies, predicates
- business rules, creating
- creating, policies
- policies, logical operators
- policies, examples
- policies, default actions
- policies
- policies, arguments
- policies, creating
ms.assetid: 59f06a67-edde-443b-9fbb-55ec4429837a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fb3d835b39a4059fc7a4a1644d7653257ea3dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250326"
---
# <a name="how-to-create-policies-and-rules"></a><span data-ttu-id="498c7-102">如何建立原則和規則</span><span class="sxs-lookup"><span data-stu-id="498c7-102">How to Create Policies and Rules</span></span>
<span data-ttu-id="498c7-103">您可以使用邏輯群組的邏輯運算子的條件建立規則 (**AND**， **OR**，和**不**) 套用到述詞 （內建或使用者定義函式或運算子），不接受引數 （內建或使用者定義的事實參考）。</span><span class="sxs-lookup"><span data-stu-id="498c7-103">You can create rules with conditions that are logical groupings of logical operators (**AND**, **OR**, and **NOT**) applied to predicates (built-in or user-defined functions or operators) that take arguments (built-in or user-defined fact references).</span></span> <span data-ttu-id="498c7-104">您也可以以滑鼠右鍵按一下**條件**或邏輯運算子，從內容功能表中選取邏輯運算子或內建述詞。</span><span class="sxs-lookup"><span data-stu-id="498c7-104">You can also right-click **Conditions** or logical operators and select a logical operator or built-in predicate from the context menu.</span></span>  
  
 <span data-ttu-id="498c7-105">您可以定義若規則條件評估為要執行的動作 （內建或使用者定義函式） **true**。</span><span class="sxs-lookup"><span data-stu-id="498c7-105">You can define actions (built-in or user-defined functions) to be executed if the rule condition evaluates to **true**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="498c7-106">若在一個規則中包含一個以上的述詞，則所有述詞必須顯示為邏輯運算子的引數。</span><span class="sxs-lookup"><span data-stu-id="498c7-106">If you include more than one predicate in a rule, all predicates must appear as arguments to a logical operator.</span></span> <span data-ttu-id="498c7-107">(最上層可以是屬於布林類型的單一 .NET 成員、資料庫資料行或 XML 欄位/屬性。)</span><span class="sxs-lookup"><span data-stu-id="498c7-107">(The top level can be a single .NET member, db column, or XML field/attribute that is of boolean type.)</span></span>  
  
### <a name="to-create-a-policy"></a><span data-ttu-id="498c7-108">若要建立原則</span><span class="sxs-lookup"><span data-stu-id="498c7-108">To create a policy</span></span>  
  
1.  <span data-ttu-id="498c7-109">在 原則總管 窗格中，以滑鼠右鍵按一下**原則**，然後按一下 **新增原則**。</span><span class="sxs-lookup"><span data-stu-id="498c7-109">In the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
     <span data-ttu-id="498c7-110">新的資料夾， **[policy1]**，下方會建立**原則**。</span><span class="sxs-lookup"><span data-stu-id="498c7-110">A new folder, **Policy1**, is created under **Policies**.</span></span> <span data-ttu-id="498c7-111">依照預設，會為您建立版本 1 的新原則。</span><span class="sxs-lookup"><span data-stu-id="498c7-111">By default, version 1 of a new policy is created for you.</span></span>  
  
2.  <span data-ttu-id="498c7-112">按一下 **[policy1]**。</span><span class="sxs-lookup"><span data-stu-id="498c7-112">Click **Policy1**.</span></span>  
  
3.  <span data-ttu-id="498c7-113">在 [名稱] 屬性窗格中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="498c7-113">In the Name property pane, type a name.</span></span>  
  
### <a name="to-add-a-rule-to-a-policy-version"></a><span data-ttu-id="498c7-114">新增規則到原則版本</span><span class="sxs-lookup"><span data-stu-id="498c7-114">To add a rule to a policy version</span></span>  
  
-   <span data-ttu-id="498c7-115">在 [原則總管] 窗格中，展開 [**原則**]，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後選取**新增規則**。</span><span class="sxs-lookup"><span data-stu-id="498c7-115">In the Policy Explorer pane, expand [**your policy**], right-click **Version 1.0 (not saved)**, and then select **Add New Rule**.</span></span>  
  
### <a name="to-add-a-logical-operator-to-a-rule-condition"></a><span data-ttu-id="498c7-116">新增邏輯運算子到規則條件</span><span class="sxs-lookup"><span data-stu-id="498c7-116">To add a logical operator to a rule condition</span></span>  
  
-   <span data-ttu-id="498c7-117">在 [規則定義] 視窗中，以滑鼠右鍵按一下**條件**，然後按一下其中一個**新增邏輯 AND**，**新增邏輯 OR**，或**新增邏輯 NOT**.</span><span class="sxs-lookup"><span data-stu-id="498c7-117">In the Rule Definition window, right-click **Conditions**, and then click one of **Add Logical AND**, **Add Logical OR**, or **Add Logical NOT**.</span></span>  
  
### <a name="to-add-a-built-in-predicate-to-a-rule-condition-or-logical-operator"></a><span data-ttu-id="498c7-118">新增內建述詞到規則條件或邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="498c7-118">To add a built-in predicate to a rule condition or logical operator</span></span>  
  
1.  <span data-ttu-id="498c7-119">在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後再按一下**述詞**資料夾。</span><span class="sxs-lookup"><span data-stu-id="498c7-119">In the Facts Explorer window, click the **Vocabularies** tab, and then click the **Predicates** folder.</span></span>  
  
2.  <span data-ttu-id="498c7-120">展開述詞詞彙的已發佈版本，然後按一下所需的述詞。</span><span class="sxs-lookup"><span data-stu-id="498c7-120">Expand a published version of a predicate vocabulary, and click the predicate you want.</span></span>  
  
3.  <span data-ttu-id="498c7-121">將述詞拖曳到邏輯運算子，或拖曳至**條件**如果您的規則將會包含一個述詞。</span><span class="sxs-lookup"><span data-stu-id="498c7-121">Drag the predicate onto the logical operator, or onto **Conditions** if your rule will contain only one predicate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="498c7-122">您也可以加入述詞直接從資料來源，前提是資料元素做為述詞 (評估為**true**或**false**)。</span><span class="sxs-lookup"><span data-stu-id="498c7-122">You can also add a predicate directly from a data source, provided that the data element acts as a predicate (evaluates to **true** or **false**).</span></span>  
  
### <a name="to-add-a-built-in-action-to-a-rule"></a><span data-ttu-id="498c7-123">新增內建動作到規則</span><span class="sxs-lookup"><span data-stu-id="498c7-123">To add a built-in action to a rule</span></span>  
  
1.  <span data-ttu-id="498c7-124">在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後再按一下**函式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="498c7-124">In the Facts Explorer window, click the **Vocabularies** tab, and then click the **Functions** folder.</span></span>  
  
2.  <span data-ttu-id="498c7-125">展開函式詞彙的已發佈版本，然後按一下所需的函式。</span><span class="sxs-lookup"><span data-stu-id="498c7-125">Expand a published version of the function vocabulary, and click the function you want.</span></span>  
  
3.  <span data-ttu-id="498c7-126">拖曳函式到**動作**。</span><span class="sxs-lookup"><span data-stu-id="498c7-126">Drag the function onto **Actions**.</span></span> <span data-ttu-id="498c7-127">您也可以以滑鼠右鍵按一下**動作**，然後從內容功能表選取內建動作。</span><span class="sxs-lookup"><span data-stu-id="498c7-127">You can also right-click **Actions**, and select a built-in action from the context menu.</span></span>  
  
### <a name="to-add-an-argument-to-a-condition-or-action"></a><span data-ttu-id="498c7-128">新增引數到條件或動作</span><span class="sxs-lookup"><span data-stu-id="498c7-128">To add an argument to a condition or action</span></span>  
  
1.  <span data-ttu-id="498c7-129">在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後再按一下 [詞彙] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="498c7-129">In the Facts Explorer window, click the **Vocabularies** tab, and then click a vocabulary folder.</span></span>  
  
2.  <span data-ttu-id="498c7-130">展開詞彙的已發佈版本，然後按一下所需的詞彙。</span><span class="sxs-lookup"><span data-stu-id="498c7-130">Expand a published version of the vocabulary, and click the term you want.</span></span> <span data-ttu-id="498c7-131">該詞彙必須是述詞或函式所預期的類型。</span><span class="sxs-lookup"><span data-stu-id="498c7-131">The term must be of a type expected by the predicate or function.</span></span>  
  
3.  <span data-ttu-id="498c7-132">將詞彙拖曳到條件中的述詞引數或動作中的函式引數。</span><span class="sxs-lookup"><span data-stu-id="498c7-132">Drag the term onto a predicate argument in a condition or a function argument in an action.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="498c7-133">您也可以從資料來源直接新增引數，或者在 XML 中，可以在選取欄位時在屬性中指定欄位類型，但必須與資料本身相容，且資料項目必須是述詞或動作所預期的類型。</span><span class="sxs-lookup"><span data-stu-id="498c7-133">You can also add an argument directly from a data source or in the case of XML you can specify the field type in the properties when selecting a field; this must of course be compatible with the data itself , provided that the data element is of a type expected by the predicate or action.</span></span> <span data-ttu-id="498c7-134">若要直接從資料來源新增引數，在 [事實總管] 視窗中，按一下適當的索引標籤，巡覽至您所需的項目，然後拖曳到述詞引數或函式引數。</span><span class="sxs-lookup"><span data-stu-id="498c7-134">To add an argument directly from a data source, click the appropriate tab in the Facts Explorer window, navigate to the item you want, and drag it onto a predicate argument or function argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="498c7-135">按一下引數並輸入想要的常數值，即可直接新增常數值到引數。</span><span class="sxs-lookup"><span data-stu-id="498c7-135">You can add a constant value to an argument directly by clicking the argument and entering the constant value you want.</span></span>