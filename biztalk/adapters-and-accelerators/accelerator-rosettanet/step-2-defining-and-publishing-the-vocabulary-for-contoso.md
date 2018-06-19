---
title: 步驟 2： 定義與發佈 Contoso 的詞彙 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vocabularies, creating
- vocabularies, publishing
- private process tutorial, creating vocabularies
ms.assetid: e23880c0-772c-48c6-a6b5-32eb951527c8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15937a1235cc1776be38fe2b0e5529c19d3f6fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211086"
---
# <a name="step-2-defining-and-publishing-the-vocabulary-for-contoso"></a><span data-ttu-id="41700-102">步驟 2： 定義與發佈 Contoso 的詞彙</span><span class="sxs-lookup"><span data-stu-id="41700-102">Step 2: Defining and Publishing the Vocabulary for Contoso</span></span>
<span data-ttu-id="41700-103">在此實例中，Contoso 會實作商務原則，以確保即使發生緊急狀況，也一定有足夠的存貨。</span><span class="sxs-lookup"><span data-stu-id="41700-103">In this scenario, Contoso implements a business policy that makes sure that inventory is always on hand if an emergency occurs.</span></span> <span data-ttu-id="41700-104">您將使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 中的「商務規則編輯器」建立商務原則。</span><span class="sxs-lookup"><span data-stu-id="41700-104">You create business policies using the Business Rule Composer in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="41700-105">在此步驟中，您將建立在定義商務原則時要使用的詞彙。</span><span class="sxs-lookup"><span data-stu-id="41700-105">In this step, you create the vocabulary to use when you define the business policy.</span></span>  
  
### <a name="to-add-a-new-vocabulary"></a><span data-ttu-id="41700-106">加入新詞彙</span><span class="sxs-lookup"><span data-stu-id="41700-106">To add a new vocabulary</span></span>  
  
1.  <span data-ttu-id="41700-107">按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="41700-107">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="41700-108">在 [開啟規則存放區] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="41700-108">In the Open Rule Store dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="41700-109">在 事實總管 窗格中，在**詞彙**索引標籤上，以滑鼠右鍵按一下**詞彙**，然後按一下 **新增詞彙**。</span><span class="sxs-lookup"><span data-stu-id="41700-109">In the Facts Explorer pane, on the **Vocabularies** tab, right-click **Vocabularies**, and then click **Add New Vocabulary**.</span></span>  
  
4.  <span data-ttu-id="41700-110">將詞彙**3A2PriceAvailabilityVocabulary**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="41700-110">Name the vocabulary **3A2PriceAvailabilityVocabulary**, and then press **Enter**.</span></span>  
  
### <a name="to-define-a-constant-vocabulary-value"></a><span data-ttu-id="41700-111">定義常數詞彙值</span><span class="sxs-lookup"><span data-stu-id="41700-111">To define a constant vocabulary value</span></span>  
  
1.  <span data-ttu-id="41700-112">在 商務規則編輯器 中按一下**3A2PriceAvailabilityVocabulary**，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增定義**。</span><span class="sxs-lookup"><span data-stu-id="41700-112">In Business Rule Composer, click **3A2PriceAvailabilityVocabulary**, right-click **Version 1.0(not saved)**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="41700-113">在**詞彙定義精靈**頁面上，選取**常數值、 值的範圍或值的集合**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="41700-113">On the **Vocabulary Definition Wizard** page, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="41700-114">在**常數值、 值的範圍或值的集合**頁面上，於**定義名稱**方塊中，輸入**Emergency Quantity Needed**，然後按一下 [**下一步]**.</span><span class="sxs-lookup"><span data-stu-id="41700-114">On the **Constant Value, Range of Values, or Set of Values** page, in the **Definition name** box, type **Emergency Quantity Needed**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="41700-115">在**定義常數值**頁面上，於**值**方塊中，輸入**800**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="41700-115">On the **Define a Constant Value** page, in the **Value** box, type **800**, and then click **Finish**.</span></span>  
  
### <a name="to-define-an-xml-document-get-element"></a><span data-ttu-id="41700-116">定義 XML 文件的 Get 項目</span><span class="sxs-lookup"><span data-stu-id="41700-116">To define an XML document 'Get' element</span></span>  
  
1.  <span data-ttu-id="41700-117">商務規則編輯器 中的事實總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）** 下**3A2PriceAvailabilityVocabulary**，然後按一下 **新增定義**.</span><span class="sxs-lookup"><span data-stu-id="41700-117">In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="41700-118">在**VocabularyDefinition 精靈**頁面上，選取**XML 文件項目或屬性**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="41700-118">On the **VocabularyDefinition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="41700-119">在**XML 文件項目或屬性**頁面上，於**定義名稱**方塊中，輸入**Quantity Available**。</span><span class="sxs-lookup"><span data-stu-id="41700-119">On the **XML Document Element or Attribute** page, in the **Definition Name** box, type **Quantity Available**.</span></span>  
  
4.  <span data-ttu-id="41700-120">按一下**瀏覽**(旁**結構描述**欄位)，移至**ContosoPriceAndAvailability**專案在方案資料夾中，選取**ContosoPriceAndAvailability.xsd**結構描述，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="41700-120">Click **Browse** (next to the **Schema** field), move to the **ContosoPriceAndAvailability** project in your solution folder, select the **ContosoPriceAndAvailability.xsd** schema, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="41700-121">在 [選取繫結] 對話方塊中，依序展開**rootPriceResponse**，依序展開**產品**，選取**NumberAvailable**項目，然後再按一下**確定**.</span><span class="sxs-lookup"><span data-stu-id="41700-121">In the Select Binding dialog box, expand **rootPriceResponse**, expand **Products**, select the **NumberAvailable** element, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="41700-122">在**XML 文件項目或屬性**頁面上，於**文件類型**方塊中，確認值為**ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span><span class="sxs-lookup"><span data-stu-id="41700-122">On the **XML Document Element or Attribute** page, in the **Document Type** box, ensure that the value is **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span></span>  
  
7.  <span data-ttu-id="41700-123">在**選取作業**區段中，選取**執行 「 取得 」 作業**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="41700-123">In the **Select operation** section, select **Perform "Get" Operation**, and then click **Finish**.</span></span>  
  
### <a name="to-define-an-xml-document-set-element"></a><span data-ttu-id="41700-124">定義 XML 文件的 Set 項目</span><span class="sxs-lookup"><span data-stu-id="41700-124">To define an XML document 'Set' element</span></span>  
  
1.  <span data-ttu-id="41700-125">商務規則編輯器 中的事實總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）** 下**3A2PriceAvailabilityVocabulary**，然後按一下 **新增定義**.</span><span class="sxs-lookup"><span data-stu-id="41700-125">In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="41700-126">在**VocabularyDefinition 精靈**頁面上，選取**XML 文件項目或屬性**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="41700-126">On the **VocabularyDefinition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="41700-127">在**XML 文件項目或屬性**頁面上，於**定義名稱**方塊中，輸入**最後可用量**。</span><span class="sxs-lookup"><span data-stu-id="41700-127">On the **XML Document Element or Attribute** page, in the **Definition Name** box, type **Final Quantity Available**.</span></span>  
  
4.  <span data-ttu-id="41700-128">按一下**瀏覽**(旁**結構描述**欄位)，移至**ContosoPriceAndAvailability**專案在方案資料夾中，選取**ContosoPriceAndAvailability.xsd**結構描述，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="41700-128">Click **Browse** (next to the **Schema** field), move to the **ContosoPriceAndAvailability** project in your solution folder, select the **ContosoPriceAndAvailability.xsd** schema, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="41700-129">在**選取繫結**對話方塊方塊中，展開  **rootPriceResponse**，依序展開**產品**，然後選取**NumberAvailable**項目。</span><span class="sxs-lookup"><span data-stu-id="41700-129">In the **Select Binding** dialog box, expand **rootPriceResponse**, expand **Products**, and then select the **NumberAvailable** element.</span></span> <span data-ttu-id="41700-130">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="41700-130">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="41700-131">在**XML 文件項目或屬性**頁面上，於**文件類型**方塊中，確認值為**ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span><span class="sxs-lookup"><span data-stu-id="41700-131">On the **XML Document Element or Attribute** page, in the **Document Type** box, ensure that the value is **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span></span>  
  
7.  <span data-ttu-id="41700-132">在**選取作業**區段中，選取**執行 「 設定 」 作業**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="41700-132">In the **Select operation** section, select **Perform "Set" Operation**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="41700-133">在**指定顯示名稱**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="41700-133">In the **Specify the Display Name** page, click **Finish**.</span></span>  
  
### <a name="to-save-and-publish-the-vocabulary"></a><span data-ttu-id="41700-134">儲存和發佈詞彙</span><span class="sxs-lookup"><span data-stu-id="41700-134">To save and publish the vocabulary</span></span>  
  
1.  <span data-ttu-id="41700-135">商務規則編輯器 中的事實總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）** 下**3A2PriceAvailabilityVocabulary**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="41700-135">In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="41700-136">以滑鼠右鍵按一下該相同**1.0 版**節點，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="41700-136">Right-click that same **Version 1.0** node and then click **Publish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41700-137">讓 [商務規則編輯器] 保持開啟，供教學課程中的下個步驟使用。</span><span class="sxs-lookup"><span data-stu-id="41700-137">Leave the Business Rule Composer open for the next step in the tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41700-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41700-138">See Also</span></span>  
 [<span data-ttu-id="41700-139">步驟 3： 定義、 發佈與部署 Contoso 的商務原則</span><span class="sxs-lookup"><span data-stu-id="41700-139">Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)