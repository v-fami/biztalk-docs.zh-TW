---
title: 步驟 3： 定義、 發佈與部署 Contoso 的商務原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, deploying
- policies, publishing
- private process tutorial, creating policies
- policies, creating
ms.assetid: 529b16d8-226b-4046-a95d-64162ebd59a3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbdd1133145aada8b1a1abf0ccdde25547b7fed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210662"
---
# <a name="step-3-defining-publishing-and-deploying-the-business-policy-for-contoso"></a><span data-ttu-id="25eb1-102">步驟 3： 定義、 發佈與部署 Contoso 的商務原則</span><span class="sxs-lookup"><span data-stu-id="25eb1-102">Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso</span></span>
<span data-ttu-id="25eb1-103">在此步驟中，您將建立可保留每個產品一定單位數量的商務原則，讓 Contoso 製造商可以在緊急時使用這些存貨。</span><span class="sxs-lookup"><span data-stu-id="25eb1-103">In this step, you create a business policy that reserves a set quantity of units for each product that Contoso manufactures to be used in case of an emergency.</span></span>  
  
### <a name="to-add-a-new-policy"></a><span data-ttu-id="25eb1-104">新增原則</span><span class="sxs-lookup"><span data-stu-id="25eb1-104">To add a new policy</span></span>  
  
1.  <span data-ttu-id="25eb1-105">在商務規則編輯器] 中 [原則總管] 窗格中，以滑鼠右鍵按一下**原則**，然後按一下 [**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-105">In the Business Rule Composer, in the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
2.  <span data-ttu-id="25eb1-106">將新原則**3A2PriceAvailabilityPolicy**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-106">Name the new policy **3A2PriceAvailabilityPolicy**, and then press **Enter**.</span></span>  
  
### <a name="to-add-a-policy-rule-to-enforce-the-emergency-quantity-needs"></a><span data-ttu-id="25eb1-107">新增原則規則以強制執行緊急數量需求</span><span class="sxs-lookup"><span data-stu-id="25eb1-107">To add a policy rule to enforce the emergency quantity needs</span></span>  
  
1.  <span data-ttu-id="25eb1-108">以滑鼠右鍵按一下**版本 1.0 （未儲存）** 下**3A2PriceAvailabilityPolicy**，然後按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-108">Right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Add New Rule**.</span></span>  
  
2.  <span data-ttu-id="25eb1-109">命名規則**Emergency Supply Rule-Quantity Exhausted**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-109">Name the rule **Emergency Supply Rule - Quantity Exhausted**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="25eb1-110">在右窗格中，「 商務規則編輯器 」 中以滑鼠右鍵按一下**條件**下 IF] 窗格中，指向**述詞**，然後按一下 [**小於等於**述詞。</span><span class="sxs-lookup"><span data-stu-id="25eb1-110">In the Business Rule Composer, in the right pane, right-click **Conditions** under the IF pane, point to **Predicates**, and then click the **Less than equal** predicate.</span></span>  
  
4.  <span data-ttu-id="25eb1-111">在 [事實總管] 窗格中，依序展開**詞彙**，依序展開**3A2PriceAvailabilityVocabulary**，依序展開**1.0 版-已發佈**，選取**數量可用**，並將它拖曳至`argument1`編輯器介面上的預留位置。</span><span class="sxs-lookup"><span data-stu-id="25eb1-111">In the Facts Explorer pane, expand **Vocabularies**, expand **3A2PriceAvailabilityVocabulary**, expand **Version 1.0 - Published**, select **Quantity Available**, and drag it onto the `argument1` placeholder on the composer surface.</span></span>  
  
5.  <span data-ttu-id="25eb1-112">重複步驟 4 拖曳**Emergency Quantity Needed**到`argument2`預留位置。</span><span class="sxs-lookup"><span data-stu-id="25eb1-112">Repeat step 4 by dragging **Emergency Quantity Needed** onto the `argument2` placeholder.</span></span>  
  
6.  <span data-ttu-id="25eb1-113">選取**最後可用量**，然後將它拖曳至拖曳**動作**THEN 窗格中。</span><span class="sxs-lookup"><span data-stu-id="25eb1-113">Select **Final Quantity Available**, and then drag it onto **Actions** in the THEN pane.</span></span>  
  
### <a name="to-add-a-policy-to-revise-the-number-available-field-in-the-response"></a><span data-ttu-id="25eb1-114">新增原則以修訂回應中的可用數目欄位</span><span class="sxs-lookup"><span data-stu-id="25eb1-114">To add a policy to revise the Number Available field in the response</span></span>  
  
1.  <span data-ttu-id="25eb1-115">以滑鼠右鍵按一下**版本 1.0 （未儲存）** 下**3A2PriceAvailabilityPolicy**，然後按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-115">Right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Add New Rule**.</span></span>  
  
2.  <span data-ttu-id="25eb1-116">將新的規則**Emergency Supply Rule-Quantity Available**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-116">Name the new rule **Emergency Supply Rule - Quantity Available**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="25eb1-117">在右窗格中，「 商務規則編輯器 」 中以滑鼠右鍵按一下**條件**下 IF] 窗格中，指向**述詞**，然後按一下 [**大於**述詞。</span><span class="sxs-lookup"><span data-stu-id="25eb1-117">In the Business Rule Composer, in the right pane, right click **Conditions** under the IF pane, point to **Predicates**, and then click the **Greater than** predicate.</span></span>  
  
4.  <span data-ttu-id="25eb1-118">在 [事實總管] 窗格中，依序展開**詞彙**，依序展開**3A2PriceAvailabilityVocabulary**，依序展開**1.0 版-已發佈**，選取**數量可用**，然後將它拖曳至拖曳`argument1`編輯器介面上的預留位置。</span><span class="sxs-lookup"><span data-stu-id="25eb1-118">In the Facts Explorer pane, expand **Vocabularies**, expand **3A2PriceAvailabilityVocabulary**, expand **Version 1.0 - Published**, select **Quantity Available**, and then drag it onto the `argument1` placeholder on the composer surface.</span></span>  
  
5.  <span data-ttu-id="25eb1-119">重複相同的步驟，藉由拖曳**Emergency Quantity Needed**到`argument2`預留位置。</span><span class="sxs-lookup"><span data-stu-id="25eb1-119">Repeat that same step by dragging **Emergency Quantity Needed** onto the `argument2` placeholder.</span></span>  
  
6.  <span data-ttu-id="25eb1-120">選取**最後可用量**，然後將它拖曳至拖曳**動作**THEN 窗格中。</span><span class="sxs-lookup"><span data-stu-id="25eb1-120">Select **Final Quantity Available**, and then drag it onto **Actions** in the THEN pane.</span></span>  
  
7.  <span data-ttu-id="25eb1-121">在 事實總管 窗格中，依序展開**1.0 版-已發佈**下**函式**，並拖曳`Subtract`函式到**0**旁的引數**最後可用量**THEN 窗格中。</span><span class="sxs-lookup"><span data-stu-id="25eb1-121">In the Facts Explorer pane, expand **Version 1.0 - Published** under **Functions**, and drag the `Subtract` function onto the **0** argument next to **Final Quantity Available** in the THEN pane.</span></span>  
  
8.  <span data-ttu-id="25eb1-122">拖曳**Quantity Available** (下**3A2PriceAvailabilityVocabulary**) 並將它放在`value1`THEN 窗格中的預留位置。</span><span class="sxs-lookup"><span data-stu-id="25eb1-122">Drag **Quantity Available** (under **3A2PriceAvailabilityVocabulary**) and drop it on the `value1` placeholder in the THEN pane.</span></span>  
  
9. <span data-ttu-id="25eb1-123">拖曳**Emergency Quantity Needed**，並將它放在`value2`THEN 窗格中的預留位置。</span><span class="sxs-lookup"><span data-stu-id="25eb1-123">Drag **Emergency Quantity Needed**, and drop it on the `value2` placeholder in the THEN pane.</span></span>  
  
### <a name="to-save-publish-and-deploy-the-business-policy"></a><span data-ttu-id="25eb1-124">若要儲存、發佈和部署商務原則</span><span class="sxs-lookup"><span data-stu-id="25eb1-124">To save, publish, and deploy the business policy</span></span>  
  
1.  <span data-ttu-id="25eb1-125">在 原則總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）** 下**3A2PriceAvailabilityPolicy**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-125">In the Policy Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="25eb1-126">以滑鼠右鍵按一下相同節點，然後**發行**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-126">Right-click that same node, and then click **Publish**.</span></span>  
  
3.  <span data-ttu-id="25eb1-127">以滑鼠右鍵按一下相同節點，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="25eb1-127">Right-click that same node, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25eb1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25eb1-128">See Also</span></span>  
 [<span data-ttu-id="25eb1-129">步驟 4： 建立 HeaderHelper 專案</span><span class="sxs-lookup"><span data-stu-id="25eb1-129">Step 4: Creating the HeaderHelper Project</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)