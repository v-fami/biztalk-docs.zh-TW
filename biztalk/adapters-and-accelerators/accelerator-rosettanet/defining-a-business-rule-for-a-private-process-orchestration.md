---
title: 定義私用程序協調流程的商務規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, policies
- vocabularies, saving
- private processes, orchestrations
- business rules, private processes
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- policies, deploying
- vocabularies, creating
- orchestrations, private-process orchestrations
- private processes, customizing
- policies, publishing
- business rules, Set elements
- creating, policies
- customizing private processes
- Set elements
- business rules, orchestrations
- publishing, vocabularies
- vocabularies, publishing
- creating, rules
- business rules, Get elements
- policies, saving
- publishing, policies
- Get elements
- orchestrations, business rules
- rules
- private processes, business rules
- policies, creating
ms.assetid: 5d2b0257-1b15-482b-a562-798b808e9a2d
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 771ef551d70ba6e8d4aa7300ac16967638f471b3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968095"
---
# <a name="defining-a-business-rule-for-a-private-process-orchestration"></a><span data-ttu-id="7b3c8-102">定義私用程序協調流程的商務規則</span><span class="sxs-lookup"><span data-stu-id="7b3c8-102">Defining a Business Rule for a Private Process Orchestration</span></span>
<span data-ttu-id="7b3c8-103">您可以定義要在通知私用程序中使用的商務規則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-103">You can define a business rule for use in an acknowledgement private process.</span></span> <span data-ttu-id="7b3c8-104">這讓您可以動態地修改商務規則，而不需停止私用程序協調流程。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-104">This lets you to modify the business rule dynamically without stopping the private-process orchestration.</span></span> <span data-ttu-id="7b3c8-105">此程序使用 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]商務規則引擎。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-105">This process uses the Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Business Rule Engine.</span></span> <span data-ttu-id="7b3c8-106">這個程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7b3c8-106">This process involves the following steps:</span></span>  
  
1. <span data-ttu-id="7b3c8-107">加入新詞彙。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-107">Adding a new vocabulary.</span></span> <span data-ttu-id="7b3c8-108">這需要定義至少一個詞彙常數值。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-108">This involves defining at least one vocabulary constant value.</span></span> <span data-ttu-id="7b3c8-109">這會設定商務規則閾值，</span><span class="sxs-lookup"><span data-stu-id="7b3c8-109">This sets a business-rule threshold.</span></span> <span data-ttu-id="7b3c8-110">也需要定義 XML 文件 `Get` 和 `Set` 項目。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-110">It also involves defining XML document `Get` and `Set` elements.</span></span> <span data-ttu-id="7b3c8-111">這會建立如何 Microsoft[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]使用臨界值。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-111">This establishes how Microsoft [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] uses the threshold.</span></span>  
  
2. <span data-ttu-id="7b3c8-112">加入新原則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-112">Adding a new policy.</span></span> <span data-ttu-id="7b3c8-113">這需要建立一個原則和一組規則，然後再儲存、發佈及部署該原則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-113">This involves creating a policy, creating a set of rules, and then saving, publishing, and deploying the policy.</span></span>  
  
3. <span data-ttu-id="7b3c8-114">從私用程序協調流程呼叫商務規則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-114">Calling the business rule from the private-process orchestration.</span></span> <span data-ttu-id="7b3c8-115">這牽涉到新增**呼叫規則**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-115">This involves adding a **Call Rules** shape to the orchestration.</span></span>  
  
   <span data-ttu-id="7b3c8-116">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含的範例[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]商務原則名為 samplebtarnpolicy.xml 中\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\pipautomation\3a4。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-116">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes a sample [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] business policy, samplebtarnpolicy.xml, in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4.</span></span> <span data-ttu-id="7b3c8-117">如需詳細資訊，請參閱 < [BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-117">For more information, see [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).</span></span>  
  
   <span data-ttu-id="7b3c8-118">PIP3A4PrivateResponder.odx 範例屬於私用程序協調流程，示範如何實作特定夥伴介面程序 (PIP) 的回應者私用程序，以整合商務規則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-118">PIP3A4PrivateResponder.odx orchestration is a sample private-process orchestration that demonstrates how to implement a Partner Interface Process (PIP)-specific responder private process incorporating a business rule.</span></span> <span data-ttu-id="7b3c8-119">如需有關此範例的詳細資訊，請參閱 < [3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-119">For more information about this sample, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
   <span data-ttu-id="7b3c8-120">如需有關詞彙和原則的詳細資訊，請參閱 BizTalk Server 中的 「 開發與商務規則 」 主題。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-120">For more information about vocabularies and policies, see the "Developing with Business Rules" topic in BizTalk Server.</span></span>  
  
### <a name="to-add-a-new-vocabulary"></a><span data-ttu-id="7b3c8-121">加入新詞彙</span><span class="sxs-lookup"><span data-stu-id="7b3c8-121">To add a new vocabulary</span></span>  
  
1. <span data-ttu-id="7b3c8-122">按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-122">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
2. <span data-ttu-id="7b3c8-123">如果**開啟規則存放區** 對話方塊隨即開啟，請選取**BizTalk 規則引擎**資料庫，您目前的伺服器上設定，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-123">If the **Open Rule Store** dialog box opens, select the **BizTalk Rule Engine** database that you set up on the current server, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="7b3c8-124">在 Microsoft 商務規則編輯器，在事實總管 窗格中，以滑鼠右鍵按一下**詞彙**，然後按一下**新增詞彙**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-124">In Microsoft Business Rule Composer, in the Facts Explorer pane, right-click **Vocabularies**, and then click **Add New Vocabulary**.</span></span>  
  
4. <span data-ttu-id="7b3c8-125">在 [屬性] 窗格 （左下方） 中，設定**名稱**屬性設為名稱，以及與的適當的詞彙，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-125">In the Property pane (lower left), set the **Name** property to the name of the appropriate vocabulary, and then press **Enter**.</span></span>  
  
5. <span data-ttu-id="7b3c8-126">展開您剛才建立的詞彙資料夾，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增定義**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-126">Expand the vocabulary folder you just created, right-click **Version 1.0 (not saved)**, and then click **Add New Definition**.</span></span>  
  
6. <span data-ttu-id="7b3c8-127">在 **詞彙定義精靈**頁面上，選取**常數值、 值的範圍或值的集合**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-127">On the **Vocabulary Definition Wizard** page, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
7. <span data-ttu-id="7b3c8-128">在 [**常數值、 值的範圍或值的集合**頁面上，於**定義名稱**方塊中，輸入適當詞彙常數值的名稱，例如**數量允許的最大**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-128">On the **Constant Value, Range of Values, or Set of Values** page, in the **Definition Name** box, type the name of the appropriate vocabulary constant value, such as **Maximum Quantity Allowed**, and then click **Next**.</span></span>  
  
8. <span data-ttu-id="7b3c8-129">在上**定義常數值**頁面上，於**值欄位**方塊中輸入臨界值，然後再按**完成**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-129">On the **Define a Constant Value** page, in the **Value Field** box, type the threshold, and then click **Finish**.</span></span>  
  
### <a name="to-define-get-and-set-elements"></a><span data-ttu-id="7b3c8-130">定義 Get 和 Set 項目</span><span class="sxs-lookup"><span data-stu-id="7b3c8-130">To define Get and Set elements</span></span>  
  
1.  <span data-ttu-id="7b3c8-131">在商務規則編輯器，在事實總管] 窗格中，在 [要新增的新詞彙程序]，建立詞彙資料夾底下以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 [**新增定義**.</span><span class="sxs-lookup"><span data-stu-id="7b3c8-131">In Business Rule Composer, in the Facts Explorer pane, under the vocabulary folder created in the "To add a new vocabulary procedure", right-click **Version 1.0 (not saved)**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="7b3c8-132">在 **詞彙定義精靈**頁面上，選取**XML 文件項目或屬性**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-132">On the **Vocabulary Definition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="7b3c8-133">在  **XML 文件項目或屬性**頁面上，在 定義名稱 文字方塊中輸入的名稱**取得**項目。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-133">On the **XML Document Element or Attribute** page, in the Definition Name text box, type a name for a **Get** element.</span></span>  
  
4.  <span data-ttu-id="7b3c8-134">按一下 **瀏覽**，移至您想要使用選取結構描述檔案，然後按一下 結構描述的位置**開啟**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-134">Click **Browse**, move to the location of the schema that you want to use, select the schema file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="7b3c8-135">如果**選取根節點**頁面隨即開啟，請選取要瀏覽的根節點。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-135">If the **Select Root Node** page opens, select the root node to browse.</span></span>  
  
6.  <span data-ttu-id="7b3c8-136">在 **選取繫結**頁面上，移至您要定義的臨界值的欄位，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-136">On the **Select Binding** page, move to the field for which you want to define the threshold, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="7b3c8-137">在 **文件類型**方塊中，輸入文件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-137">In the **Document Type** box, type the name of the document.</span></span>  
  
8.  <span data-ttu-id="7b3c8-138">在 **作業類型**區段中，選取**執行 「 取得 」 作業**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-138">In the **Operation Type** section, select **Perform “Get” operation**.</span></span>  
  
9. <span data-ttu-id="7b3c8-139">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-139">Click **Finish**.</span></span>  
  
10. <span data-ttu-id="7b3c8-140">重複這些步驟，以定義一或多個`Set`作業，選取**執行 「 設定 」 作業**如**作業類型**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-140">Repeat these steps to define one or more `Set` operations, select **Perform “Set” operation** for the **Operation Type**.</span></span>  
  
### <a name="to-save-and-publish-the-vocabulary"></a><span data-ttu-id="7b3c8-141">儲存和發佈詞彙</span><span class="sxs-lookup"><span data-stu-id="7b3c8-141">To save and publish the vocabulary</span></span>  
  
1.  <span data-ttu-id="7b3c8-142">在商務規則編輯器，在 [事實總管] 窗格中，您建立詞彙資料夾底下以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-142">In Business Rule Composer, in the Facts Explorer pane, under the vocabulary folder that you created, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="7b3c8-143">在事實總管 窗格的 3a4purchaseordervocabulary 資料夾底下，以滑鼠右鍵按一下**1.0 版**，然後選取**發佈**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-143">In the Facts Explorer pane, under the 3A4PurchaseOrderVocabulary folder, right-click **Version 1.0**, and then select **Publish**.</span></span>  
  
### <a name="to-add-a-new-policy-and-rules"></a><span data-ttu-id="7b3c8-144">加入新原則和規則</span><span class="sxs-lookup"><span data-stu-id="7b3c8-144">To add a new policy and rules</span></span>  
  
1.  <span data-ttu-id="7b3c8-145">在商務規則編輯器，在 [原則總管] 窗格中，以滑鼠右鍵按一下**原則**，然後按一下**新增新的原則**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-145">In Business Rule Composer, in the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
2.  <span data-ttu-id="7b3c8-146">按一下  **Policy1**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-146">Click **Policy1**.</span></span>  
  
3.  <span data-ttu-id="7b3c8-147">在 [屬性] 窗格中，設定**名稱**屬性設為適當的原則名稱。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-147">In the Property pane, set the **Name** property to the appropriate policy name.</span></span>  
  
4.  <span data-ttu-id="7b3c8-148">在 原則總管 窗格中，為新的原則 資料夾底下以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增規則**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-148">In the Policy Explorer pane, under the folder for the new policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span>  
  
5.  <span data-ttu-id="7b3c8-149">按一下  **Rule1**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-149">Click **Rule1**.</span></span>  
  
6.  <span data-ttu-id="7b3c8-150">在 [屬性] 窗格中，設定**名稱**屬性設為規則名稱，然後再按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-150">In the Property pane, set the **Name** property to the rule name you want, and then press **Enter**.</span></span>  
  
7.  <span data-ttu-id="7b3c8-151">在規則編輯器 中下, **IF**窗格中，以滑鼠右鍵按一下**條件**，然後選取的邏輯條件，如果適用的話。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-151">In the Rule Composer, under the **IF** pane, right-click **Conditions**, and then select a logical condition, if appropriate.</span></span>  
  
8.  <span data-ttu-id="7b3c8-152">在 [事實總管] 窗格中下,**詞彙**，展開**述詞**，展開**1.0 版-已發佈**，選取您想要將它拖曳至編輯器介面，述的詞然後將它放置在**條件**或邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-152">In the Facts Explorer pane, under **Vocabularies**, expand **Predicates**, expand **Version 1.0 - Published**, select the predicate you want, drag it to the composer surface, and then drop it on **Conditions** or the logical operator.</span></span>  
  
9. <span data-ttu-id="7b3c8-153">在 [事實總管] 窗格中，在 [詞彙] 資料夾中，依序展開您建立的詞彙中，展開**1.0 版-已發佈**，選取`Get`或`Set`項目，將它拖曳至編輯器介面，並將它放在**引數 1**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-153">In the Facts Explorer pane, under the Vocabularies folder, expand the vocabulary that you created, expand **Version 1.0 - Published**, select a `Get` or `Set` element, drag it to the composer surface, and drop it on **argument1**.</span></span>  
  
10. <span data-ttu-id="7b3c8-154">在 [詞彙] 資料夾中，選取`Get`或是`Set`項目，將它拖曳至編輯器介面並放置在**引數 2**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-154">Under the vocabulary folder, select a `Get` or `Set` element, drag it to the composer surface and drop it on **argument2**.</span></span>  
  
11. <span data-ttu-id="7b3c8-155">在 [詞彙] 資料夾中，選取`Set`項目，將它拖曳至編輯器介面，並將它放**動作**方塊 [THEN] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-155">Under the vocabulary folder, select a `Set` element, drag it to the composer surface, and drop it in the **Actions** box in the THEN pane.</span></span>  
  
12. <span data-ttu-id="7b3c8-156">如果與變數相關聯`Set`項目中，按一下 [變數]，視需要變更，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-156">If a variable is associated with the `Set` element, click the variable, make changes as appropriate, and then press **Enter**.</span></span> <span data-ttu-id="7b3c8-157">如果適當，請對其他 `Set` 項目重複執行上述步驟。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-157">If appropriate, repeat with other `Set` elements.</span></span>  
  
### <a name="to-save-publish-and-deploy-the-policy"></a><span data-ttu-id="7b3c8-158">儲存、發佈和部署原則</span><span class="sxs-lookup"><span data-stu-id="7b3c8-158">To save, publish, and deploy the policy</span></span>  
  
1.  <span data-ttu-id="7b3c8-159">當您完成定義規則，在 [商務規則編輯器，在原則總管] 窗格中，您建立原則資料夾下，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-159">When you have finished defining the rules, in Business Rule Composer, in the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="7b3c8-160">在 [原則總管] 窗格中，您建立原則資料夾下按一下滑鼠右鍵**1.0 版**，然後按一下**發佈**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-160">In the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0**, and then click **Publish**.</span></span>  
  
3.  <span data-ttu-id="7b3c8-161">在 [原則總管] 窗格中，您建立原則資料夾下按一下滑鼠右鍵**1.0 版**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-161">In the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0**, and then click **Deploy**.</span></span>  
  
### <a name="to-call-the-business-rule-from-the-orchestration"></a><span data-ttu-id="7b3c8-162">從協調流程呼叫商務規則</span><span class="sxs-lookup"><span data-stu-id="7b3c8-162">To call the business rule from the orchestration</span></span>  
  
1.  <span data-ttu-id="7b3c8-163">開始**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-163">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="7b3c8-164">在 **檔案**功能表上，指向 開啟，然後**專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-164">On the **File** menu, point to Open, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="7b3c8-165">找出方案，其中包含協調流程，您必須呼叫商務規則，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-165">Locate the solution that contains the orchestration that you must call the business rule from, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="7b3c8-166">按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-166">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
5.  <span data-ttu-id="7b3c8-167">依序展開**變數**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-167">Expand **Variables**.</span></span> <span data-ttu-id="7b3c8-168">請確認協調流程變數清單含有對應至商務原則 (您從協調流程呼叫的商務原則) 中每個參數的變數。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-168">Make sure that the orchestration variable list contains a variable that corresponds to each parameter in the business policy that you call from the orchestration.</span></span> <span data-ttu-id="7b3c8-169">確認變數類型與原則參數相同。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-169">Make sure that the variable has the same type as the policy parameter.</span></span> <span data-ttu-id="7b3c8-170">如果清單不包含每個原則參數的協調流程變數，以滑鼠右鍵按一下**變數**，然後按一下**新的變數**。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-170">If the list does not contain an orchestration variable for each policy parameter, right-click **Variables**, and then click **New Variable**.</span></span> <span data-ttu-id="7b3c8-171">在 [協調流程檢視] 中，輸入變數名稱，然後在 [屬性] 視窗中，輸入參數的類型。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-171">In Orchestration View, type a variable name, and then in the Properties window, enter the type of the parameter.</span></span>  
  
6.  <span data-ttu-id="7b3c8-172">從**工具箱**，拖曳**呼叫規則**圖形至協調流程設計介面，然後再放在**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-172">From the **Toolbox**, drag a **Call Rules** shape to the orchestration design surface, and then drop it under the **Receive** shape.</span></span>  
  
7.  <span data-ttu-id="7b3c8-173">按兩下**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-173">Double-click the **Call Rules** shape.</span></span>  
  
8.  <span data-ttu-id="7b3c8-174">在 **選取您想要呼叫的商務原則**方塊中，從下拉式清單中選取的商務原則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-174">In the **Select the business policy you wish to call** box, select the business policy from the drop-down list.</span></span>  
  
9. <span data-ttu-id="7b3c8-175">第一個參數所示，針對**參數名稱**，從下拉式清單中選取名稱。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-175">For the first parameter shown, for **Parameter Name**, select a name from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7b3c8-176">BTARN 會填入**原則參數**搭配的商務原則的所有參數的清單。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-176">BTARN populates the **Policy Parameter** list with all the parameters in the business policy.</span></span> <span data-ttu-id="7b3c8-177">在清單中每一個參數，BTARN 會輸入中的值**參數類型**透過商務原則。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-177">For each parameter in the list, BTARN enters a value in **Parameter Type** from the business policy.</span></span> <span data-ttu-id="7b3c8-178">在下拉式清單中相關聯**參數名稱**，BTARN 從已與原則參數相同類型的協調流程的變數清單輸入所有的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-178">In the drop-down list associated with **Parameter Name**, BTARN enters the names of all variables from the orchestration's variable list that has the same type as the policy parameters.</span></span> <span data-ttu-id="7b3c8-179">藉由選取協調流程變數，就能與原則參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-179">By selecting an orchestration variable, you are associating that variable with the policy parameter.</span></span> <span data-ttu-id="7b3c8-180">您可以在 [協調流程檢視] 中檢視這些協調流程變數。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-180">You can view the orchestration variables in Orchestration View.</span></span>  
  
10. <span data-ttu-id="7b3c8-181">對所有其他參數重複執行步驟 9。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-181">Repeat step 9 for all other parameters.</span></span>  
  
11. <span data-ttu-id="7b3c8-182">在 [協調流程設計] 視窗中，輸入與商務原則，包括加入相關聯的處理所需的所有其他形狀**決策**圖形下**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-182">In the Orchestration Design window, enter all the additional shapes required for the processing associated with the business policy, including adding a **Decision** shape under the **Call Rules** shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7b3c8-183">如需如何使用的範例**呼叫規則**圖形的協調流程中，請參閱 BTARN SDK 隨附的 PIP3A4PrivateResponder.odx 協調流程。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-183">For an example of how to use a **Call Rules** shape in an orchestration, see the PIP3A4PrivateResponder.odx orchestration included in the BTARN SDK.</span></span> <span data-ttu-id="7b3c8-184">它是位於\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-184">It is located at \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR.</span></span> <span data-ttu-id="7b3c8-185">如需詳細資訊，請參閱 < [3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-185">For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
12. <span data-ttu-id="7b3c8-186">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7b3c8-186">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3c8-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b3c8-187">See Also</span></span>  
 <span data-ttu-id="7b3c8-188">[程式設計手冊](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span><span class="sxs-lookup"><span data-stu-id="7b3c8-188">[Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span></span>  
 <span data-ttu-id="7b3c8-189">[BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md) </span><span class="sxs-lookup"><span data-stu-id="7b3c8-189">[Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md) </span></span>  
 [<span data-ttu-id="7b3c8-190">使用商務規則的 3A4 私用回應者協調流程</span><span class="sxs-lookup"><span data-stu-id="7b3c8-190">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)