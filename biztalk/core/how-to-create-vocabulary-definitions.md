---
title: 如何建立詞彙定義 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, creating
- vocabularies, definitions
ms.assetid: 6f8fc4c2-2c46-4a7d-a02f-89de0396e3e2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff9fdfc7cd444a97d1a24353c13d93460c00d4ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250558"
---
# <a name="how-to-create-vocabulary-definitions"></a><span data-ttu-id="15e53-102">如何建立詞彙定義</span><span class="sxs-lookup"><span data-stu-id="15e53-102">How to Create Vocabulary Definitions</span></span>
<span data-ttu-id="15e53-103">您可以使用「詞彙定義精靈」來建立詞彙定義。</span><span class="sxs-lookup"><span data-stu-id="15e53-103">You can use the Vocabulary Definition Wizard to create vocabulary definitions.</span></span> <span data-ttu-id="15e53-104">您可以定義詞彙定義為常數值、值的範圍、值的集合或是 .NET 組件的項目、XML 文件或資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="15e53-104">You can define a vocabulary definition as a constant value, a range of values, a set of values, or elements of a .NET assembly, XML document, or database table.</span></span> <span data-ttu-id="15e53-105">如果您選取公開變數時，會有**取得**和**設定**選項就像在資料庫和 XML 定義精靈。</span><span class="sxs-lookup"><span data-stu-id="15e53-105">If you select a public variable, there will be **Get** and **Set** options just like in Database and XML definition wizard.</span></span>  
  
 <span data-ttu-id="15e53-106">或者，您可以建立新詞彙定義，其中三個索引標籤中選取一個事實 — 例如，資料庫資料行、 XML 節點或.NET 類別的成員 — 事實拖曳至**詞彙**索引標籤上，並它放置到未發佈詞彙版本。</span><span class="sxs-lookup"><span data-stu-id="15e53-106">Alternatively, you can create a new vocabulary definition by selecting a fact from one of the three tabs—for example, a database column, an XML node, or a member of a .NET class—dragging the fact over to the **Vocabularies** tab, and dropping it to an unpublished version of a vocabulary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15e53-107">您無法將詞彙定義新增至已發佈的詞彙版本。</span><span class="sxs-lookup"><span data-stu-id="15e53-107">You cannot add a vocabulary definition to a vocabulary version that has been published.</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-constant-value"></a><span data-ttu-id="15e53-108">定義詞彙定義為常數值</span><span class="sxs-lookup"><span data-stu-id="15e53-108">To define a vocabulary definition as a constant value</span></span>  
  
1.  <span data-ttu-id="15e53-109">以滑鼠右鍵按一下詞彙版本，然後**新增定義**。</span><span class="sxs-lookup"><span data-stu-id="15e53-109">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-110">您也可以從 [事實總管: XML 結構描述]、[資料庫] 以及 [.NET 類別] 的其他索引標籤拖放項目。</span><span class="sxs-lookup"><span data-stu-id="15e53-110">You can also drag and drop items from other tabs of Fact Explorer: XML Schemas, Databases and .NET Classes</span></span>  
  
2.  <span data-ttu-id="15e53-111">在 詞彙定義精靈 中，選取**常數值、 值的範圍或值的集合**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-111">In the Vocabulary Definition Wizard, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="15e53-112">編輯定義名稱和定義描述。</span><span class="sxs-lookup"><span data-stu-id="15e53-112">Edit the definition name and definition description.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-113">定義顯示名稱最大長度為 512 個字元。</span><span class="sxs-lookup"><span data-stu-id="15e53-113">The maximum length for a definition display name is 512 characters.</span></span>  
  
4.  <span data-ttu-id="15e53-114">選取**常數值**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-114">Select **Constant Value**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="15e53-115">從可用的系統類型下拉式清單選取定義類型。</span><span class="sxs-lookup"><span data-stu-id="15e53-115">Select a definition type from the drop-down list of available system types.</span></span>  
  
6.  <span data-ttu-id="15e53-116">編輯顯示名稱和值，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="15e53-116">Edit the display name and value, and then click **Finish**.</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-range-of-values"></a><span data-ttu-id="15e53-117">定義詞彙定義為值的範圍</span><span class="sxs-lookup"><span data-stu-id="15e53-117">To define a vocabulary definition as a range of values</span></span>  
  
1.  <span data-ttu-id="15e53-118">以滑鼠右鍵按一下詞彙版本，然後**新增定義**。</span><span class="sxs-lookup"><span data-stu-id="15e53-118">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="15e53-119">在 詞彙定義精靈 中，選取**常數值、 值的範圍或值的集合**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-119">In the Vocabulary Definition Wizard, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="15e53-120">編輯定義名稱和定義描述。</span><span class="sxs-lookup"><span data-stu-id="15e53-120">Edit the definition name and definition description.</span></span>  
  
4.  <span data-ttu-id="15e53-121">選取**值的範圍**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-121">Select **Range of Values**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="15e53-122">從下拉式清單選取定義類型。</span><span class="sxs-lookup"><span data-stu-id="15e53-122">Select a definition type from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="15e53-123">按一下**範圍下限**，然後按一下 **編輯**以指定範圍下限的值。</span><span class="sxs-lookup"><span data-stu-id="15e53-123">Click **Range Low**, and then click **Edit** to specify the values for the lower range.</span></span> <span data-ttu-id="15e53-124">將開啟參數定義對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15e53-124">The parameter definition dialog will be opened.</span></span>  
  
7.  <span data-ttu-id="15e53-125">選取**使用常數值**後輸入常數值，或選取**使用的已發佈詞彙定義**並瀏覽至詞彙定義，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="15e53-125">Select **Use Constant Value** and enter a constant value, or select **Use Definition from a Published Vocabulary** and browse to a vocabulary definition, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="15e53-126">重複步驟 6 和 7**範圍上限**。</span><span class="sxs-lookup"><span data-stu-id="15e53-126">Repeat steps 6 and 7 for **Range High**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-127">**範圍上限**值必須超過**範圍下限**值。</span><span class="sxs-lookup"><span data-stu-id="15e53-127">The **Range High** value must exceed the **Range Low** value.</span></span>  
  
9. <span data-ttu-id="15e53-128">輸入的顯示格式字串，或按一下**預設**以還原為預設顯示格式字串，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="15e53-128">Type the display format string or click **Default** to revert to the default display format string, and then click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-129">格式字串應該將參數索引置於大括號，例如"{0}"和"{1}"—to 做為範圍上限與下限參數的預留位置。</span><span class="sxs-lookup"><span data-stu-id="15e53-129">Your format string should include parameter indexes in curly braces—for example, "{0}" and "{1}"—to serve as placeholders for the high and low range parameters.</span></span>  
  
     <span data-ttu-id="15e53-130">![詞彙定義](../core/media/3db84492-d6b8-4059-9d2c-a720ccc207b6.gif "3db84492-d6b8-4059-9d2c-a720ccc207b6")</span><span class="sxs-lookup"><span data-stu-id="15e53-130">![Vocabulary Definitions](../core/media/3db84492-d6b8-4059-9d2c-a720ccc207b6.gif "3db84492-d6b8-4059-9d2c-a720ccc207b6")</span></span>  
<span data-ttu-id="15e53-131">具有格式字串的值範圍</span><span class="sxs-lookup"><span data-stu-id="15e53-131">Range of values with formatted string</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-set-of-values"></a><span data-ttu-id="15e53-132">定義詞彙定義為值的集合</span><span class="sxs-lookup"><span data-stu-id="15e53-132">To define a vocabulary definition as a set of values</span></span>  
  
1.  <span data-ttu-id="15e53-133">以滑鼠右鍵按一下詞彙版本，然後**新增定義**。</span><span class="sxs-lookup"><span data-stu-id="15e53-133">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="15e53-134">在 詞彙定義精靈 中，選取**常數值、 值的範圍或值的集合**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-134">In the Vocabulary Definition Wizard, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="15e53-135">編輯定義名稱和定義描述。</span><span class="sxs-lookup"><span data-stu-id="15e53-135">Edit the definition name and definition description.</span></span>  
  
4.  <span data-ttu-id="15e53-136">選取**值的集合**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-136">Select **Set of Values**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="15e53-137">輸入定義類型和顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="15e53-137">Enter the definition type and display name.</span></span>  
  
6.  <span data-ttu-id="15e53-138">若要將成員加入至集合，選取**使用常數值**後輸入常數值，或選取**使用的已發佈詞彙定義**並瀏覽至詞彙定義，然後再按一下  **新增**。</span><span class="sxs-lookup"><span data-stu-id="15e53-138">To add a member to the set, select **Use Constant Value** and enter a constant value, or select **Use Definition from a Published Vocabulary** and browse to a vocabulary definition, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="15e53-139">針對您想要包括在集合中的所有項目，以任意組合的常數或詞彙定義重複步驟 6。</span><span class="sxs-lookup"><span data-stu-id="15e53-139">Repeat step 6, with any combination of constants or vocabulary definitions, for as many items as you want to include in your set.</span></span>  
  
8.  <span data-ttu-id="15e53-140">若要移動的相對順序的集合內的成員，選取它，然後按一下 **向上**或**向**。</span><span class="sxs-lookup"><span data-stu-id="15e53-140">To move a member within the relative order of the set, select it and then click **Up** or **Down**.</span></span>  
  
9. <span data-ttu-id="15e53-141">若要從集合中移除成員，選取它，然後按一下 **移除**。</span><span class="sxs-lookup"><span data-stu-id="15e53-141">To remove a member from the set, select it and then click **Remove**.</span></span>  
  
10. <span data-ttu-id="15e53-142">完成您的設定後，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="15e53-142">When you have completed your set, click **Finish**.</span></span>  
  
     <span data-ttu-id="15e53-143">![詞彙定義](../core/media/461d0d70-52ed-4f43-927d-3efb1fbfb934.gif "461d0d70-52ed-4f43-927d-3efb1fbfb934")</span><span class="sxs-lookup"><span data-stu-id="15e53-143">![Vocabulary Definitions](../core/media/461d0d70-52ed-4f43-927d-3efb1fbfb934.gif "461d0d70-52ed-4f43-927d-3efb1fbfb934")</span></span>  
<span data-ttu-id="15e53-144">值的集合</span><span class="sxs-lookup"><span data-stu-id="15e53-144">Set of values</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-net-class-or-class-member"></a><span data-ttu-id="15e53-145">定義詞彙定義為 .NET 類別或類別成員</span><span class="sxs-lookup"><span data-stu-id="15e53-145">To define a vocabulary definition as a .NET class or class member</span></span>  
  
1.  <span data-ttu-id="15e53-146">以滑鼠右鍵按一下詞彙版本，然後**新增定義**。</span><span class="sxs-lookup"><span data-stu-id="15e53-146">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="15e53-147">在 詞彙定義精靈 中，選取 **.NET 類別或類別成員**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-147">In the Vocabulary Definition Wizard, select **.NET Class or Class Member**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="15e53-148">編輯**定義名稱**和**描述**欄位。</span><span class="sxs-lookup"><span data-stu-id="15e53-148">Edit the **Definition Name** and **Description** fields.</span></span>  
  
4.  <span data-ttu-id="15e53-149">按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="15e53-149">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="15e53-150">在 **.NET 組件**對話方塊中，選取組件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="15e53-150">In the **.NET Assemblies** dialog box, select an assembly, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-151">組件必須位在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="15e53-151">The assemblies have to be in the global assembly cache (GAC).</span></span> <span data-ttu-id="15e53-152">當您瀏覽.NET 組件中，「 商務規則編輯器 」 會載入.NET 組件**事實總管**視窗或在 **.NET 類別或類別成員定義**頁面**詞彙定義**視窗。</span><span class="sxs-lookup"><span data-stu-id="15e53-152">The business rule composer loads a .NET assembly when you browse for the .NET assembly in the **Facts Explorer** window or in the **.NET Class or Class Member Definition** page of the **Vocabulary Definition** window.</span></span>  <span data-ttu-id="15e53-153">如果您在 GAC 中更新此組件，請關閉商務規則編輯器並將它重新啟動，以載入更新的 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="15e53-153">If you update the assembly in the GAC, close the business rule composer and restart it to load the updated .NET assembly.</span></span> <span data-ttu-id="15e53-154">商務規則編輯器並不會自動重新整理此組件。</span><span class="sxs-lookup"><span data-stu-id="15e53-154">The business rule composer does not refresh the assembly automatically.</span></span>  
  
6.  <span data-ttu-id="15e53-155">展開組件節點。</span><span class="sxs-lookup"><span data-stu-id="15e53-155">Expand the assembly node.</span></span>  
  
7.  <span data-ttu-id="15e53-156">選取一個類別，或展開類別並選取類別成員，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="15e53-156">Select a class, or expand a class and select a class member, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="15e53-157">按一下**下一步**，並指定顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="15e53-157">Click **Next**, and specify the display name.</span></span>  
  
     <span data-ttu-id="15e53-158">如需詳細資訊，請參閱本主題稍後的＜使用參數指定詞彙定義的顯示格式＞。</span><span class="sxs-lookup"><span data-stu-id="15e53-158">For more information, see "To specify the display format of a vocabulary definition by using parameters" later in this topic.</span></span>  
  
9. <span data-ttu-id="15e53-159">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="15e53-159">Click **Finish**.</span></span>  
  
     <span data-ttu-id="15e53-160">![詞彙定義](../core/media/4259101f-26dd-488f-81c0-f8d225e4016e.gif "4259101f-26dd-488f-81c0-f8d225e4016e")</span><span class="sxs-lookup"><span data-stu-id="15e53-160">![Vocabulary Definitions](../core/media/4259101f-26dd-488f-81c0-f8d225e4016e.gif "4259101f-26dd-488f-81c0-f8d225e4016e")</span></span>  
<span data-ttu-id="15e53-161">網路物件詞彙定義</span><span class="sxs-lookup"><span data-stu-id="15e53-161">Net object vocabulary definition</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-an-xml-document-element-or-attribute"></a><span data-ttu-id="15e53-162">定義詞彙定義為 XML 文件項目或屬性</span><span class="sxs-lookup"><span data-stu-id="15e53-162">To define a vocabulary definition as an XML document element or attribute</span></span>  
  
1.  <span data-ttu-id="15e53-163">以滑鼠右鍵按一下詞彙版本，然後**新增定義**。</span><span class="sxs-lookup"><span data-stu-id="15e53-163">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="15e53-164">在 詞彙定義精靈 中，選取**XML 文件項目或屬性**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-164">In the Vocabulary Definition Wizard, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="15e53-165">輸入定義名稱和定義描述。</span><span class="sxs-lookup"><span data-stu-id="15e53-165">Type a definition name and a definition description.</span></span>  
  
4.  <span data-ttu-id="15e53-166">按一下**瀏覽**尋找結構描述檔案，並指定文件項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="15e53-166">Click **Browse** to locate a schema file and specify a document element or attribute.</span></span>  
  
5.  <span data-ttu-id="15e53-167">從下拉式清單，選取與結構描述中的項目或屬性類型相容的類型。</span><span class="sxs-lookup"><span data-stu-id="15e53-167">From the drop-down list, select a type that is compatible with the type of the element or attribute in the schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-168">如果無法有效地將指定類型轉換為文件項目或屬性的類型，在執行階段將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="15e53-168">If a valid cast cannot be done to or from the specified type to the type of the document element or attribute, you will get an error at run time.</span></span>  
  
6.  <span data-ttu-id="15e53-169">選取作業類型以指出您計劃要取得項目或屬性的值，或是設定其值。</span><span class="sxs-lookup"><span data-stu-id="15e53-169">Select an operation type to indicate whether you plan to get the value of the element or attribute, or to set its value.</span></span>  
  
7.  <span data-ttu-id="15e53-170">如果您選擇設定值，請按一下**下一步**，然後指定顯示格式。</span><span class="sxs-lookup"><span data-stu-id="15e53-170">If you chose to set the value, click **Next**, and then specify the display format.</span></span>  
  
8.  <span data-ttu-id="15e53-171">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="15e53-171">Click **Finish**.</span></span>  
  
     <span data-ttu-id="15e53-172">![詞彙定義](../core/media/fd81b534-ec41-4147-b716-1e10ffc01d6f.gif "fd81b534-ec41-4147-b716-1e10ffc01d6f")</span><span class="sxs-lookup"><span data-stu-id="15e53-172">![Vocabulary Definitions](../core/media/fd81b534-ec41-4147-b716-1e10ffc01d6f.gif "fd81b534-ec41-4147-b716-1e10ffc01d6f")</span></span>  
<span data-ttu-id="15e53-173">XML 詞彙定義</span><span class="sxs-lookup"><span data-stu-id="15e53-173">XML vocabulary definition</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15e53-174">永遠不會驗證定義項目的存在和文件類型。</span><span class="sxs-lookup"><span data-stu-id="15e53-174">The existence of the defined element and the document type is never validated.</span></span> <span data-ttu-id="15e53-175">若判斷提示的文件沒有項目，將會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="15e53-175">If the asserted document does not have the element, you will get a runtime error.</span></span> <span data-ttu-id="15e53-176">若以未知的文件類型判斷提示文件，則會直接忽略它。</span><span class="sxs-lookup"><span data-stu-id="15e53-176">If you assert a document with unknown document type, it will simply be ignored.</span></span>  
  
#### <a name="to-define-a-vocabulary-definition-as-a-database-table-or-database-table-column"></a><span data-ttu-id="15e53-177">定義詞彙定義為資料庫資料表或資料庫資料表資料行</span><span class="sxs-lookup"><span data-stu-id="15e53-177">To define a vocabulary definition as a database table or database table column</span></span>  
  
1.  <span data-ttu-id="15e53-178">以滑鼠右鍵按一下詞彙版本，然後按一下 **新增定義**。</span><span class="sxs-lookup"><span data-stu-id="15e53-178">Right-click the vocabulary version and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="15e53-179">在 詞彙定義精靈 中，選取**資料庫資料表或資料庫資料表資料行定義**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="15e53-179">In the Vocabulary Definition Wizard, select **Database Table or Database Table Column Definition**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="15e53-180">輸入定義名稱和定義描述。</span><span class="sxs-lookup"><span data-stu-id="15e53-180">Type a definition name and definition description.</span></span>  
  
4.  <span data-ttu-id="15e53-181">按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="15e53-181">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="15e53-182">選取要連接的 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="15e53-182">Select a SQL Server computer to connect with.</span></span> <span data-ttu-id="15e53-183">如果目前未啟動 SQL Server 電腦，選取**如果它已停止，啟動 SQL Server**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="15e53-183">If the SQL Server computer is not currently started, select the **Start SQL Server if it is stopped** check box.</span></span>  
  
6.  <span data-ttu-id="15e53-184">選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="15e53-184">Select an authentication type.</span></span> <span data-ttu-id="15e53-185">如果您選取 SQL Server 驗證，請輸入您的登入名稱和密碼，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="15e53-185">If you select SQL Server authentication, type your logon name and password, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="15e53-186">選取的資料表或資料表資料行，您想要繫結，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="15e53-186">Select the table or table column that you want to bind to, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="15e53-187">若您已選取資料表資料行，請選取要取得其值或設定其值。</span><span class="sxs-lookup"><span data-stu-id="15e53-187">If you selected a table column, select whether you want to get its value or set its value.</span></span> <span data-ttu-id="15e53-188">若選擇要取得其值，請輸入顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="15e53-188">If you choose to get its value, type the display name.</span></span> <span data-ttu-id="15e53-189">如果您選擇將其值設定，請按一下**下一步**指定顯示格式。</span><span class="sxs-lookup"><span data-stu-id="15e53-189">If you choose to set its value, click **Next** to specify the display format.</span></span>  
  
     <span data-ttu-id="15e53-190">如需詳細資訊，請參閱本主題稍後的＜使用參數指定詞彙定義的顯示格式＞。</span><span class="sxs-lookup"><span data-stu-id="15e53-190">For more information, see "To specify the display format of a vocabulary definition by using parameters" later in this topic.</span></span>  
  
9. <span data-ttu-id="15e53-191">若您已選取資料表，請輸入顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="15e53-191">If you selected a table, type a display name.</span></span>  
  
10. <span data-ttu-id="15e53-192">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="15e53-192">Click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-193">根據預設， **DataConnection**使用繫結</span><span class="sxs-lookup"><span data-stu-id="15e53-193">By default, **DataConnection** binding is used</span></span>  
  
     <span data-ttu-id="15e53-194">![詞彙定義](../core/media/f8121306-cd73-4997-adc4-71a055dfd824.gif "f8121306-cd73-4997-adc4-71a055dfd824")</span><span class="sxs-lookup"><span data-stu-id="15e53-194">![Vocabulary Definitions](../core/media/f8121306-cd73-4997-adc4-71a055dfd824.gif "f8121306-cd73-4997-adc4-71a055dfd824")</span></span>  
<span data-ttu-id="15e53-195">資料庫詞彙定義</span><span class="sxs-lookup"><span data-stu-id="15e53-195">Database vocabulary definition</span></span>  
  
#### <a name="to-specify-the-display-format-of-a-vocabulary-definition-by-using-parameters"></a><span data-ttu-id="15e53-196">使用參數指定詞彙定義的顯示格式</span><span class="sxs-lookup"><span data-stu-id="15e53-196">To specify the display format of a vocabulary definition by using parameters</span></span>  
  
1.  <span data-ttu-id="15e53-197">從清單中選取參數**參數**中詞彙定義精靈，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="15e53-197">Select a parameter from the list of **Parameters** in Vocabulary Definition Wizard, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="15e53-198">選取**使用常數值**後輸入常數值，或選取**使用的已發佈詞彙定義**並瀏覽至詞彙定義，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="15e53-198">Select **Use Constant Value** and enter a constant value, or select **Use Definition from a Published Vocabulary** and browse to a vocabulary definition, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="15e53-199">輸入的顯示格式字串，或按一下**預設**以還原為預設顯示格式字串，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="15e53-199">Type the display format string or click **Default** to revert to the default display format string, and then click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15e53-200">格式字串應該將參數索引置於大括號，例如"{0}"和"{1}"—to 做為參數的預留位置。</span><span class="sxs-lookup"><span data-stu-id="15e53-200">Your format string should include parameter indexes in curly braces—for example, "{0}" and "{1}"—to serve as placeholders for the parameters.</span></span>  
  
     <span data-ttu-id="15e53-201">![詞彙定義](../core/media/822f78f4-278a-4211-83ad-44032fa81f13.gif "822f78f4-278a-4211-83ad-44032fa81f13")</span><span class="sxs-lookup"><span data-stu-id="15e53-201">![Vocabulary Definitions](../core/media/822f78f4-278a-4211-83ad-44032fa81f13.gif "822f78f4-278a-4211-83ad-44032fa81f13")</span></span>  
<span data-ttu-id="15e53-202">具有參數的詞彙定義</span><span class="sxs-lookup"><span data-stu-id="15e53-202">Vocabulary definition with parameters</span></span>