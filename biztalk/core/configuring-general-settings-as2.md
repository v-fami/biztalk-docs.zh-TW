---
title: 設定一般設定 (AS2) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8592c52e-5156-418c-9c49-7478f73c372e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20a0fa1ea7e9a3c6462f09eddee564850c4820dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001447"
---
# <a name="configuring-general-settings-as2"></a><span data-ttu-id="cd9a4-102">設定一般設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="cd9a4-102">Configuring General Settings (AS2)</span></span>
<span data-ttu-id="cd9a4-103">在一般設定中，您會指定協議名稱、協議將使用的通訊協定 (AS2)、協議兩方的合作對象與設定檔，以及是否針對所有透過協議處理的訊息啟用報告功能。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-103">As part of the general settings, you specify agreement name, the protocol it will use (AS2), the parties and profiles that the agreement is between, and whether to have reporting enabled for all messages processed through the agreement.</span></span> <span data-ttu-id="cd9a4-104">您也可以在協議中指定合作對象連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-104">You can also specify the party contact information as part of the agreement.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="cd9a4-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="cd9a4-105">Prerequisites</span></span>  
 <span data-ttu-id="cd9a4-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  

### <a name="to-configure-general-agreement-settings"></a><span data-ttu-id="cd9a4-107">若要設定一般協議設定</span><span class="sxs-lookup"><span data-stu-id="cd9a4-107">To configure general agreement settings</span></span>  

1. <span data-ttu-id="cd9a4-108">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象**的主控台樹狀目錄中，然後在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下必須是在協議的商務設定檔，您所建立，並指向**的新**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click a business profile that must be part of the agreement that you are creating, point to **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="cd9a4-109">下表列出不同的屬性和值中的屬性指定**一般屬性**頁面。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-109">The following tables list the different properties and the values to be specified for the properties in the **General Properties** page.</span></span>  

   1. <span data-ttu-id="cd9a4-110">在 **協議參數**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-110">In the **Agreement Parameters** section, do the following:</span></span>  


      |   <span data-ttu-id="cd9a4-111">使用</span><span class="sxs-lookup"><span data-stu-id="cd9a4-111">Use this</span></span>   |                                                                                                     <span data-ttu-id="cd9a4-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cd9a4-112">To do this</span></span>                                                                                                     |
      |--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |   <span data-ttu-id="cd9a4-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-113">**Name**</span></span>   |                                                                                          <span data-ttu-id="cd9a4-114">指定協議的名稱</span><span class="sxs-lookup"><span data-stu-id="cd9a4-114">Specify a name for the agreement</span></span>                                                                                          |
      |    <span data-ttu-id="cd9a4-115">**ID**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-115">**ID**</span></span>    |               <span data-ttu-id="cd9a4-116">列示協議的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-116">Lists unique identification for the agreement.</span></span> <span data-ttu-id="cd9a4-117">此文字方塊不能編輯，並將顯示協議識別碼，在您按下後**套用**已接受的第一個時間和設定。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-117">This text box is not editable and will display the agreement ID after you click **Apply** for the first time and settings are accepted.</span></span>               |
      |  <span data-ttu-id="cd9a4-118">**狀態**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-118">**Status**</span></span>  | <span data-ttu-id="cd9a4-119">指定協議的狀態。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-119">Specifies the status of the agreement.</span></span> <span data-ttu-id="cd9a4-120">根據預設，在建立協議**Active**狀態。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-120">By default, an agreement is created in an **Active** state.</span></span> <span data-ttu-id="cd9a4-121">如果您想要停用時建立的第一個選取的協議**停用**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-121">If you want the agreement to be disabled when it is first created, select **Disabled** from the drop-down list.</span></span> |
      | <span data-ttu-id="cd9a4-122">**通訊協定**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-122">**Protocol**</span></span> |                                                  <span data-ttu-id="cd9a4-123">指定協議的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-123">Specifies the protocol for the agreement.</span></span> <span data-ttu-id="cd9a4-124">AS2 傳輸通訊協定中，選取**AS2**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-124">For an AS2 transport protocol, select **AS2** from the drop-down list.</span></span>                                                  |


   2. <span data-ttu-id="cd9a4-125">在 **第一夥伴**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-125">In the **First Partner** section, do the following:</span></span>  


      |     <span data-ttu-id="cd9a4-126">使用</span><span class="sxs-lookup"><span data-stu-id="cd9a4-126">Use this</span></span>     |                                                                                                      <span data-ttu-id="cd9a4-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cd9a4-127">To do this</span></span>                                                                                                       |
      |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     <span data-ttu-id="cd9a4-128">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-128">**Name**</span></span>     |                                           <span data-ttu-id="cd9a4-129">顯示要建立協議的商務設定檔所屬之夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-129">Displays the partner name that has the business profile for which you are creating the agreement.</span></span> <span data-ttu-id="cd9a4-130">這是無法編輯的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-130">This text box is not editable.</span></span>                                            |
      |   <span data-ttu-id="cd9a4-131">**設定檔**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-131">**Profile**</span></span>    |                                                       <span data-ttu-id="cd9a4-132">顯示您正在為它建立協議的設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-132">Displays the name of the profile for which you are creating the agreement.</span></span> <span data-ttu-id="cd9a4-133">這是無法編輯的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-133">This text box is not editable.</span></span>                                                       |
      | <span data-ttu-id="cd9a4-134">**通訊協定的設定**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-134">**Protocol Set**</span></span> | <span data-ttu-id="cd9a4-135">如果您在商務設定檔中建立了 AS2 通訊協定集，即可從下拉式清單中選取該集合。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-135">If you created an AS2 protocol set as part of the business profile, you can select that from the drop-down list.</span></span> <span data-ttu-id="cd9a4-136">如果您未在商務設定檔中建立 AS2 通訊協定集，可以讓此處空白。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-136">If you did not create an AS2 protocol set as part of the business profile, you can leave this empty.</span></span> |


   3. <span data-ttu-id="cd9a4-137">在 **第二個夥伴**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-137">In the **Second Partner** section, do the following:</span></span>  

      |<span data-ttu-id="cd9a4-138">使用</span><span class="sxs-lookup"><span data-stu-id="cd9a4-138">Use this</span></span>|<span data-ttu-id="cd9a4-139">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cd9a4-139">To do this</span></span>|  
      |--------------|----------------|  
      |<span data-ttu-id="cd9a4-140">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-140">**Name**</span></span>|<span data-ttu-id="cd9a4-141">從下拉式清單中選取要與他的商務設定檔建立協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-141">From the drop-down select a party that has the business profile with which you want to create an agreement.</span></span>|  
      |<span data-ttu-id="cd9a4-142">**設定檔**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-142">**Profile**</span></span>|<span data-ttu-id="cd9a4-143">從下拉式清單中選取要和它建立協議的設定檔。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-143">From the drop-down select a profile with which you want to create an agreement.</span></span>|  
      |<span data-ttu-id="cd9a4-144">**通訊協定的設定**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-144">**Protocol Set**</span></span>|<span data-ttu-id="cd9a4-145">如果您在商務設定檔中建立了 AS2 通訊協定集，即可從下拉式清單中選取該集合。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-145">If you created an AS2 protocol set as part of the business profile, you can select that from the drop-down list.</span></span> <span data-ttu-id="cd9a4-146">如果您未在商務設定檔中建立 AS2 通訊協定集，可以讓此處空白。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-146">If you did not create an AS2 protocol set as part of the business profile, you can leave this empty.</span></span>|  

      > [!TIP]
      >  <span data-ttu-id="cd9a4-147">按下`CTRL`，選取 商務設定檔，將會是 「 合約 」 的一部分，請以滑鼠右鍵按一下其中一個商務設定檔，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-147">Press `CTRL`, select the business profiles that will be part of the agreement, right-click either business profile, point to **New**, and then click **Agreement**.</span></span> <span data-ttu-id="cd9a4-148">值夥伴名稱與兩個夥伴的商務設定檔將會自動填入**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-148">The values for partner name and business profiles for both the partners will be automatically populated in the **Agreement Properties** dialog box.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="cd9a4-149">當您選取另一個設定檔時，兩個索引標籤已新增旁**一般** 索引標籤。每個索引標籤各代表兩個合作對象之間的一個單向 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-149">As soon as you select the other profile, two tabs are added next to the **General** tab. Each tab represents a one-way AS2 agreement between the two parties.</span></span> <span data-ttu-id="cd9a4-150">您將使用這些索引標籤來指定交換與交易集相關設定。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-150">You use the tabs to specify interchange and transaction set related settings in the tabs.</span></span>  

   4. <span data-ttu-id="cd9a4-151">選取 **啟用協議**核取方塊以啟用協議，並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-151">Select the **Enable Agreement** check box to enable the agreement and do the following:</span></span>  


      |    <span data-ttu-id="cd9a4-152">使用</span><span class="sxs-lookup"><span data-stu-id="cd9a4-152">Use this</span></span>     |                                        <span data-ttu-id="cd9a4-153">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cd9a4-153">To do this</span></span>                                         |
      |-----------------|-------------------------------------------------------------------------------------------|
      |    <span data-ttu-id="cd9a4-154">**來源**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-154">**From**</span></span>     |             <span data-ttu-id="cd9a4-155">選取協議生效的日期與時間。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-155">Select the date and time from which the agreement will be valid.</span></span>              |
      | <span data-ttu-id="cd9a4-156">**沒有結束日期**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-156">**No End Date**</span></span> | <span data-ttu-id="cd9a4-157">如果不想設定停用協議的結束日期，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-157">Select this option if you do not want to set an end date when the agreement is disabled.</span></span>  |
      |   <span data-ttu-id="cd9a4-158">**結束於**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-158">**End By**</span></span>    | <span data-ttu-id="cd9a4-159">選取此選項並指定協議的有效截止日期與時間。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-159">Select this option and specify the date and time until which the agreement will be valid.</span></span> |


   5. <span data-ttu-id="cd9a4-160">在 **一般主控件設定**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-160">In the **Common Host Settings** section, do the following:</span></span>  


      |       <span data-ttu-id="cd9a4-161">使用</span><span class="sxs-lookup"><span data-stu-id="cd9a4-161">Use this</span></span>        |                                                                                                                                                          <span data-ttu-id="cd9a4-162">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cd9a4-162">To do this</span></span>                                                                                                                                                          |
      |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | <span data-ttu-id="cd9a4-163">**開啟報表**</span><span class="sxs-lookup"><span data-stu-id="cd9a4-163">**Turn ON reporting**</span></span> | <span data-ttu-id="cd9a4-164">若要顯示所有 AS2 訊息 （內送和外寄） 中的狀態項目**AS2 訊息和相互關聯的 MDN 狀態**索引標籤**群組概觀**窗格中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-164">to display status entries for all AS2 messages (incoming and outgoing) in the **AS2 Message and Correlated MDN Status** tab of the **Group Overview** pane in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="cd9a4-165">如果清除此選項，就不會顯示狀態項目。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-165">If cleared, no status entries will be displayed</span></span> |


3. <span data-ttu-id="cd9a4-166">在 **一般**索引標籤**連絡人資訊**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-166">In the **General** tab, on the **Contact Information** page, do the following:</span></span>  

   1.  <span data-ttu-id="cd9a4-167">在  **Contact1**索引標籤上，輸入與您要建立協議的合作對象的設定檔的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-167">In the **Contact1** tab, enter the contact information for the party’s profile with which you are creating an agreement.</span></span> <span data-ttu-id="cd9a4-168">此資訊僅供參考，BizTalk 執行階段不會使用它。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-168">This data is for information purposes only; it will not be used by the BizTalk Runtime.</span></span>  

   2.  <span data-ttu-id="cd9a4-169">若要新增連絡人的另一個索引標籤，按一下**的新連絡人** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-169">To add another tab for contact, click the **New Contact** tab.</span></span>  

   3.  <span data-ttu-id="cd9a4-170">若要刪除連絡人索引標籤，按一下**刪除**從右上角的索引標籤頁。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-170">To delete a contact tab, click **Delete** from the top right corner of the tab page.</span></span>  

       > [!NOTE]
       >  <span data-ttu-id="cd9a4-171">您無法刪除**Contact1**  索引標籤。您只能刪除您新增的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-171">You cannot delete the **Contact1** tab. You can only delete the new tabs that you add.</span></span>  

4. <span data-ttu-id="cd9a4-172">在 **一般**索引標籤**其他屬性**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd9a4-172">In the **General** tab, on the **Additional Properties** page, do the following:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="cd9a4-173">BizTalk Server 不會使用您在此頁面指定的資訊處理任何作業；此資料僅供參考。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-173">The information you specify on this page is not used by the BizTalk Server for any processing; this data is for information purposes only.</span></span>  

   1.  <span data-ttu-id="cd9a4-174">在 **其他屬性**方格中，輸入您想要新增的任何資訊與相關的合作對象或協議名稱 / 值組。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-174">In the **Additional Properties** grid, enter name-value pairs for any information that you want to add related to the party or agreement.</span></span>  <span data-ttu-id="cd9a4-175">請輸入名稱-值組來儲存合作對象的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-175">Enter a name-value pair to store any information about the party.</span></span> <span data-ttu-id="cd9a4-176">您可以視需要新增任意數目的名稱-值組。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-176">You can add as many name-value pairs as you want.</span></span>  

        <span data-ttu-id="cd9a4-177">若要刪除的名稱 / 值組，選取的資料列，按一下**刪除**從右上角。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-177">To delete a name-value pair, select the row and click **Delete** from the top-right corner.</span></span>  

   2.  <span data-ttu-id="cd9a4-178">在 **文字 1**，**文字 2**，並**協議**文字方塊中，輸入合作對象的協議的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-178">In the **Text 1**, **Text 2**, and **Agreement** text boxes, enter information about the agreement with a party.</span></span>  

       > [!IMPORTANT]
       >  <span data-ttu-id="cd9a4-179">如果您按一下 **[確定]** 或是**套用**提供所有值列在這個頁面之後，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-179">If you click **OK** or **Apply** after providing all the values listed in this page, you will get an error.</span></span> <span data-ttu-id="cd9a4-180">這是因為尚未提供建立協議所需的必要值。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-180">That is because the mandatory values to create an agreement are not yet provided.</span></span> <span data-ttu-id="cd9a4-181">這些是 AS2-從至 AS2-值上**識別碼**頁面的每個單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-181">These are AS2-From to AS2-To values on the **Identifiers** page of each one-way agreement tab.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="cd9a4-182">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cd9a4-182">Next Steps</span></span>  
 <span data-ttu-id="cd9a4-183">您現在必須設定協議的識別項設定。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-183">You must now configure the identifier settings for the agreement.</span></span> <span data-ttu-id="cd9a4-184">如需指示，請參閱[設定的識別項 (AS2)](../core/configuring-identifiers-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="cd9a4-184">For instructions see [Configuring Identifiers (AS2)](../core/configuring-identifiers-as2.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="cd9a4-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd9a4-185">See Also</span></span>  
 [<span data-ttu-id="cd9a4-186">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="cd9a4-186">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)