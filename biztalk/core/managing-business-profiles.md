---
title: 管理商務設定檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.resultsobject.businessprofile
ms.assetid: cf98c5a4-71bb-440b-8172-717ed0eb8373
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 434979376e679f1098557dc5b55f50e599ed21cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-business-profiles"></a><span data-ttu-id="6cf65-102">管理商務設定檔</span><span class="sxs-lookup"><span data-stu-id="6cf65-102">Managing Business Profiles</span></span>
<span data-ttu-id="6cf65-103">商務設定檔代表組織中的商務部門。</span><span class="sxs-lookup"><span data-stu-id="6cf65-103">A business profile represents the business divisions within of an organization.</span></span> <span data-ttu-id="6cf65-104">就像組織可以有各種部門，合作對象可以有各種[商務設定檔](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf)。</span><span class="sxs-lookup"><span data-stu-id="6cf65-104">Just like an organization can have various divisions, a party can have various [business profiles](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf).</span></span> 
  
<span data-ttu-id="6cf65-105">商務設定檔代表組織中的商務部門。</span><span class="sxs-lookup"><span data-stu-id="6cf65-105">A business profile represents a business division in an organization.</span></span> <span data-ttu-id="6cf65-106">就像組織可以有許多部門一樣 (會計、採購、出貨等)，合作對象也可以有許多商務設定檔，分別代表組織中的各部門。</span><span class="sxs-lookup"><span data-stu-id="6cf65-106">Just like an organization can have many divisions (accounting, purchase, shipping, etc.), a party can have many business profiles, each representing a business division in an organization.</span></span> <span data-ttu-id="6cf65-107">商務設定檔屬性包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="6cf65-107">Business profile properties contain the following information:</span></span>  
  
-   <span data-ttu-id="6cf65-108">一般資訊，例如商務設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="6cf65-108">General information such as business profile name</span></span>  
  
-   <span data-ttu-id="6cf65-109">可以與商務設定檔產生關聯的唯一識別項</span><span class="sxs-lookup"><span data-stu-id="6cf65-109">Unique identities that can be associated with a business profile</span></span>  
  
-   <span data-ttu-id="6cf65-110">編碼設定 （適用於 X12 與 EDIFACT 訊息） 和[通訊協定設定](../core/protocol-settings.md)(AS2)，定義如何在商務設定檔可以傳送或接收來自另一個合作對象的訊息。</span><span class="sxs-lookup"><span data-stu-id="6cf65-110">Encoding settings (for X12 and EDIFACT messages) and [protocol settings](../core/protocol-settings.md) (AS2) that defines how the business profile can send or receive messages from another party.</span></span>  
  
<span data-ttu-id="6cf65-111">本主題說明如何建立、 檢視、 編輯或刪除商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cf65-111">This topic shows you how to create, view, edit, or delete a business profile.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6cf65-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="6cf65-112">Prerequisites</span></span>  
 <span data-ttu-id="6cf65-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="6cf65-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="create-a-business-profile"></a><span data-ttu-id="6cf65-114">建立商務設定檔</span><span class="sxs-lookup"><span data-stu-id="6cf65-114">Create a business profile</span></span>  
  
1.  <span data-ttu-id="6cf65-115">在**BizTalk Server 管理**，展開 [BizTalk 群組] 並選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-115">In **BizTalk Server Administration**, expand the BizTalk group, and select **Parties**.</span></span> 
2. <span data-ttu-id="6cf65-116">在**合作對象與商務設定檔**選取窗格中，以滑鼠右鍵按一下合作對象 a**新增**，然後選取**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-116">In the **Parties and Business Profiles** pane, right-click a party, select **New**, and then select **Business Profile**.</span></span>  
  
3.  <span data-ttu-id="6cf65-117">在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6cf65-117">In the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="6cf65-118">使用</span><span class="sxs-lookup"><span data-stu-id="6cf65-118">Use this</span></span>|<span data-ttu-id="6cf65-119">動作</span><span class="sxs-lookup"><span data-stu-id="6cf65-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6cf65-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6cf65-120">**Name**</span></span>|<span data-ttu-id="6cf65-121">輸入商務設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="6cf65-121">Enter a business profile name.</span></span>|  
    |<span data-ttu-id="6cf65-122">**說明**</span><span class="sxs-lookup"><span data-stu-id="6cf65-122">**Description**</span></span>|<span data-ttu-id="6cf65-123">輸入商務設定檔的說明。</span><span class="sxs-lookup"><span data-stu-id="6cf65-123">Enter a description for the business profile.</span></span>|  
    |<span data-ttu-id="6cf65-124">**其他屬性 – 名稱/值**</span><span class="sxs-lookup"><span data-stu-id="6cf65-124">**Additional Properties – Name / Value**</span></span>|<span data-ttu-id="6cf65-125">請輸入名稱-值組來儲存合作對象的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="6cf65-125">Enter a name-value pair to store any information about the party.</span></span> <span data-ttu-id="6cf65-126">您可以視需要新增任意數目的名稱-值組。</span><span class="sxs-lookup"><span data-stu-id="6cf65-126">You can add as many name-value pairs as you want.</span></span> <span data-ttu-id="6cf65-127">**注意：**名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。</span><span class="sxs-lookup"><span data-stu-id="6cf65-127">**Note:**  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only.</span></span>|  
    |<span data-ttu-id="6cf65-128">**Delete**</span><span class="sxs-lookup"><span data-stu-id="6cf65-128">**Delete**</span></span>|<span data-ttu-id="6cf65-129">選取即可刪除選取的名稱 / 值組。</span><span class="sxs-lookup"><span data-stu-id="6cf65-129">Select to delete the selected name-value pair.</span></span>|  
  
4.  <span data-ttu-id="6cf65-130">視需要新增商務設定檔的商務識別。</span><span class="sxs-lookup"><span data-stu-id="6cf65-130">If required, add business identities for the business profiles.</span></span> <span data-ttu-id="6cf65-131">在**識別**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6cf65-131">In the **Identities** tab, do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6cf65-132">在此階段，新增商務識別並非必要動作。</span><span class="sxs-lookup"><span data-stu-id="6cf65-132">Adding business identities at this stage is not mandatory.</span></span> <span data-ttu-id="6cf65-133">您可以更新版本中，新增商務識別，做為商務設定檔的協議的一部分。</span><span class="sxs-lookup"><span data-stu-id="6cf65-133">You can add the business identities later, as part of an agreement for the business profile.</span></span> <span data-ttu-id="6cf65-134">如果您選擇要新增商務識別現在，他們就可以建立此商務設定檔的協議時。</span><span class="sxs-lookup"><span data-stu-id="6cf65-134">If you chose to add the business identifies now, they are available while creating an agreement for this business profile.</span></span>  
  
    |<span data-ttu-id="6cf65-135">使用</span><span class="sxs-lookup"><span data-stu-id="6cf65-135">Use this</span></span>|<span data-ttu-id="6cf65-136">動作</span><span class="sxs-lookup"><span data-stu-id="6cf65-136">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6cf65-137">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6cf65-137">**Name**</span></span>|<span data-ttu-id="6cf65-138">選取空白資料格，然後從下拉式方格中，選取提供給組織的獨特的商務識別驗證內文。</span><span class="sxs-lookup"><span data-stu-id="6cf65-138">Select the empty cell, and from the drop-down grid, select an authenticating body that provides unique business identities to organizations.</span></span> <span data-ttu-id="6cf65-139">例如， **D-U-N-S (Dun & Bradstreet)**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-139">For example, **D-U-N-S (Dun & Bradstreet)**.</span></span> <span data-ttu-id="6cf65-140">兩個商務夥伴可以選擇一個彼此都同意的商務識別。</span><span class="sxs-lookup"><span data-stu-id="6cf65-140">Two business partners can opt for a mutually agreed business identity.</span></span> <span data-ttu-id="6cf65-141">如需這類案例中，選取**使用者相互定義**（適用於 EDIFACT) 或**使用者相互定義 (X12)** （適用 X12)。</span><span class="sxs-lookup"><span data-stu-id="6cf65-141">For such scenarios, select **Mutually Defined** (for EDIFACT) or **Mutually Defined (X12)** (for X12).</span></span>|  
    |<span data-ttu-id="6cf65-142">**Qualifier**</span><span class="sxs-lookup"><span data-stu-id="6cf65-142">**Qualifier**</span></span>|<span data-ttu-id="6cf65-143">會顯示您針對所選取的值為基礎的預先定義的值**名稱**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-143">Displays a predefined value based on the value you selected for **Name**.</span></span>|  
    |<span data-ttu-id="6cf65-144">**值**</span><span class="sxs-lookup"><span data-stu-id="6cf65-144">**Value**</span></span>|<span data-ttu-id="6cf65-145">輸入商務識別的值。</span><span class="sxs-lookup"><span data-stu-id="6cf65-145">Enter a value for the business identity.</span></span> <span data-ttu-id="6cf65-146">提供商務識別的值時，必須考量下列事項。</span><span class="sxs-lookup"><span data-stu-id="6cf65-146">You must make the following considerations while providing a value for business identities.</span></span><br /><br /> <span data-ttu-id="6cf65-147">-針對指定的合作對象，您可以使用相同的識別名稱與識別值組合的多個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cf65-147">-   For a given party, you can have more than one business profile using the same combination of identity name and identity value.</span></span> <span data-ttu-id="6cf65-148">例如，您可以讓兩個商務設定檔的合作對象**名稱**為**使用者相互定義 (X12)**和**值**為**THEM**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-148">For example, you can have two business profiles for a party with **Name** as **Mutually Defined (X12)** and **Value** as **THEM**.</span></span><br /><span data-ttu-id="6cf65-149">-透過合作對象，您不能有兩個商務設定檔使用相同的識別名稱與識別值組合。</span><span class="sxs-lookup"><span data-stu-id="6cf65-149">-   Across parties, you cannot have two business profiles using the same combination of identity name and identity value.</span></span>|  
    |<span data-ttu-id="6cf65-150">**移除**</span><span class="sxs-lookup"><span data-stu-id="6cf65-150">**Remove**</span></span>|<span data-ttu-id="6cf65-151">選取要移除選取的識別。</span><span class="sxs-lookup"><span data-stu-id="6cf65-151">Select to remove the selected identity.</span></span>|  
  
5.  <span data-ttu-id="6cf65-152">視需要，新增 X12 編碼訊息、 EDIFACT 編碼訊息或 AS2 傳輸的通訊協定設定的通訊協定設定。</span><span class="sxs-lookup"><span data-stu-id="6cf65-152">If required, add the protocol settings for X12-encoded messages, EDIFACT-encoded messages, or the protocol settings for AS2 transport.</span></span> <span data-ttu-id="6cf65-153">請參閱[設定商務設定檔屬性](../core/configuring-business-profile-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6cf65-153">See [Configuring Business Profile Properties](../core/configuring-business-profile-properties.md).</span></span>  
  
6.  <span data-ttu-id="6cf65-154">選取**套用**接受這些屬性，或選取**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="6cf65-154">Select **Apply** to accept the properties, or select **OK** to complete the configuration setting.</span></span> <span data-ttu-id="6cf65-155">任何一項動作會驗證設定。</span><span class="sxs-lookup"><span data-stu-id="6cf65-155">Either action validates the settings.</span></span>  
  
## <a name="view-or-change-a-business-profile"></a><span data-ttu-id="6cf65-156">檢視或變更商務設定檔</span><span class="sxs-lookup"><span data-stu-id="6cf65-156">View or change a business profile</span></span>  
  
1.  <span data-ttu-id="6cf65-157">在**BizTalk Server 管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-157">In **BizTalk Server Administration**, select **Parties**.</span></span> 

2. <span data-ttu-id="6cf65-158">在**合作對象與商務設定檔**] 窗格中，展開 [合作對象節點以查看其下方的商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cf65-158">In the **Parties and Business Profiles** pane, expand a party node to see the business profiles under it.</span></span> <span data-ttu-id="6cf65-159">以滑鼠右鍵按一下您想要編輯，然後選取 商務設定檔**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-159">Right-click a business profile you want to edit, and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="6cf65-160">在**設定檔屬性** 對話方塊中，檢視或編輯設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cf65-160">In the **Profile Properties** dialog box, view or edit the profile.</span></span> <span data-ttu-id="6cf65-161">如需有關可以在不同的頁面指定之值的詳細**設定檔屬性**對話方塊中，請參閱[設定商務設定檔屬性](../core/configuring-business-profile-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6cf65-161">For information on the values that can be specified on the different pages in the **Profile Properties** dialog box, see [Configuring Business Profile Properties](../core/configuring-business-profile-properties.md).</span></span>  
  
4.  <span data-ttu-id="6cf65-162">選取**套用**接受這些屬性，或選取**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="6cf65-162">Select **Apply** to accept the properties, or select **OK** to complete the configuration setting.</span></span> <span data-ttu-id="6cf65-163">任何一項動作會驗證設定。</span><span class="sxs-lookup"><span data-stu-id="6cf65-163">Either action validates the settings.</span></span>  

## <a name="delete-a-business-profile"></a><span data-ttu-id="6cf65-164">刪除商務設定檔</span><span class="sxs-lookup"><span data-stu-id="6cf65-164">Delete a business profile</span></span>  
  
1.  <span data-ttu-id="6cf65-165">在**BizTalk Server 管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-165">In **BizTalk Server Administration**, select **Parties**.</span></span>  
  
3.  <span data-ttu-id="6cf65-166">在**合作對象與商務設定檔**] 窗格中，展開 [合作對象節點以查看其下方的商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cf65-166">In the **Parties and Business Profiles** pane, expand a party node to see the business profiles under it.</span></span>  
  
4.  <span data-ttu-id="6cf65-167">以滑鼠右鍵按一下您想要刪除，然後選取 在商務設定檔**刪除**。</span><span class="sxs-lookup"><span data-stu-id="6cf65-167">Right-click the business profile you want to delete, and then select **Delete**.</span></span> 
  
5.  <span data-ttu-id="6cf65-168">在**確認刪除商務設定檔**對話方塊中，選取**是**刪除商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cf65-168">In the **Confirm delete business profile** dialog box, select **Yes** to delete the business profile.</span></span>  


## <a name="see-also"></a><span data-ttu-id="6cf65-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf65-169">See Also</span></span>  
 [<span data-ttu-id="6cf65-170">管理 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="6cf65-170">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)