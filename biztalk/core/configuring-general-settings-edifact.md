---
title: 設定一般設定 (EDIFACT) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e18892d3-c1a4-41c8-98c2-a116ce2805ba
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a05fab2501c0c3a71c27e22f2138c7a189193c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234566"
---
# <a name="configuring-general-settings-edifact"></a><span data-ttu-id="ac722-102">設定一般設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="ac722-102">Configuring General Settings (EDIFACT)</span></span>
<span data-ttu-id="ac722-103">在一般設定中，您要指定協議名稱、協議將使用的通訊協定 (X12 或 EDIFACT)、協議的合作對象與設定檔，以及是否為透過協議處理的所有訊息啟用報告功能。</span><span class="sxs-lookup"><span data-stu-id="ac722-103">As part of the general settings, you specify agreement name, the protocol it will use (X12 or EDIFACT), the parties and profiles that the agreement is between, and whether to have reporting enabled for all messages processed through the agreement.</span></span> <span data-ttu-id="ac722-104">您也可以在協議中指定合作對象連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="ac722-104">You can also specify the party contact information as part of the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ac722-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="ac722-105">Prerequisites</span></span>  
 <span data-ttu-id="ac722-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="ac722-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-general-agreement-settings"></a><span data-ttu-id="ac722-107">若要設定一般協議設定</span><span class="sxs-lookup"><span data-stu-id="ac722-107">To configure general agreement settings</span></span>  
  
1.  <span data-ttu-id="ac722-108">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**的主控台樹狀目錄中，然後在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下必須是在協議的商務設定檔，您所建立，並指向**新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="ac722-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click a business profile that must be part of the agreement that you are creating, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="ac722-109">下表列出不同的屬性和值中的屬性指定**一般屬性**頁面。</span><span class="sxs-lookup"><span data-stu-id="ac722-109">The following tables list the different properties and the values to be specified for the properties in the **General Properties** page.</span></span>  
  
    1.  <span data-ttu-id="ac722-110">在**協議參數**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-110">In the **Agreement Parameters** section, do the following:</span></span>  
  
        |<span data-ttu-id="ac722-111">使用</span><span class="sxs-lookup"><span data-stu-id="ac722-111">Use this</span></span>|<span data-ttu-id="ac722-112">動作</span><span class="sxs-lookup"><span data-stu-id="ac722-112">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="ac722-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ac722-113">**Name**</span></span>|<span data-ttu-id="ac722-114">指定協議的名稱</span><span class="sxs-lookup"><span data-stu-id="ac722-114">Specify a name for the agreement</span></span>|  
        |<span data-ttu-id="ac722-115">**ID**</span><span class="sxs-lookup"><span data-stu-id="ac722-115">**ID**</span></span>|<span data-ttu-id="ac722-116">列示協議的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="ac722-116">Lists unique identification for the agreement.</span></span> <span data-ttu-id="ac722-117">此文字方塊不是可編輯，並按一下之後，將會顯示協議識別碼**套用**針對接受的第一個時間和設定。</span><span class="sxs-lookup"><span data-stu-id="ac722-117">This text box is not editable and will display the agreement ID after you click **Apply** for the first time and settings are accepted.</span></span>|  
        |<span data-ttu-id="ac722-118">**狀態**</span><span class="sxs-lookup"><span data-stu-id="ac722-118">**Status**</span></span>|<span data-ttu-id="ac722-119">指定協議的狀態。</span><span class="sxs-lookup"><span data-stu-id="ac722-119">Specifies the status of the agreement.</span></span> <span data-ttu-id="ac722-120">根據預設，在建立協議**Active**狀態。</span><span class="sxs-lookup"><span data-stu-id="ac722-120">By default, an agreement is created in an **Active** state.</span></span> <span data-ttu-id="ac722-121">如果您想要停用時第一次建立時，選取協議**停用**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ac722-121">If you want the agreement to be disabled when it is first created, select **Disabled** from the drop-down list.</span></span>|  
        |<span data-ttu-id="ac722-122">**通訊協定**</span><span class="sxs-lookup"><span data-stu-id="ac722-122">**Protocol**</span></span>|<span data-ttu-id="ac722-123">指定協議的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ac722-123">Specifies the protocol for the agreement.</span></span> <span data-ttu-id="ac722-124">針對 EDIFACT 編碼通訊協定，選取**EDIFACT**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ac722-124">For an EDIFACT encoding protocol, select **EDIFACT** from the drop-down list.</span></span>|  
  
    2.  <span data-ttu-id="ac722-125">在**第一個夥伴**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-125">In the **First Partner** section, do the following:</span></span>  
  
        |<span data-ttu-id="ac722-126">使用</span><span class="sxs-lookup"><span data-stu-id="ac722-126">Use this</span></span>|<span data-ttu-id="ac722-127">動作</span><span class="sxs-lookup"><span data-stu-id="ac722-127">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="ac722-128">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ac722-128">**Name**</span></span>|<span data-ttu-id="ac722-129">顯示要建立協議的商務設定檔所屬之夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="ac722-129">Displays the partner name that has the business profile for which you are creating the agreement.</span></span> <span data-ttu-id="ac722-130">這是無法編輯的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ac722-130">This text box is not editable.</span></span>|  
        |<span data-ttu-id="ac722-131">**設定檔**</span><span class="sxs-lookup"><span data-stu-id="ac722-131">**Profile**</span></span>|<span data-ttu-id="ac722-132">顯示您正在為它建立協議的設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="ac722-132">Displays the name of the profile for which you are creating the agreement.</span></span> <span data-ttu-id="ac722-133">這是無法編輯的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ac722-133">This text box is not editable.</span></span>|  
        |<span data-ttu-id="ac722-134">**通訊協定的設定**</span><span class="sxs-lookup"><span data-stu-id="ac722-134">**Protocol Set**</span></span>|<span data-ttu-id="ac722-135">如果您在商務設定檔中建立了 EDIFACT 通訊協定集，即可從下拉式清單中選取該集合。</span><span class="sxs-lookup"><span data-stu-id="ac722-135">If you created an EDIFACT protocol set as part of the business profile, you can select that from the drop-down list.</span></span> <span data-ttu-id="ac722-136">如果您未在商務設定檔中建立 EDIFACT 通訊協定集，可以讓此處空白。</span><span class="sxs-lookup"><span data-stu-id="ac722-136">If you did not create an EDIFACT protocol set as part of the business profile, you can leave this empty.</span></span>|  
  
    3.  <span data-ttu-id="ac722-137">在**第二個夥伴**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-137">In the **Second Partner** section, do the following:</span></span>  
  
        |<span data-ttu-id="ac722-138">使用</span><span class="sxs-lookup"><span data-stu-id="ac722-138">Use this</span></span>|<span data-ttu-id="ac722-139">動作</span><span class="sxs-lookup"><span data-stu-id="ac722-139">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="ac722-140">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ac722-140">**Name**</span></span>|<span data-ttu-id="ac722-141">從下拉式清單中選取要與他的商務設定檔建立協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac722-141">From the drop-down select a party that has the business profile with which you want to create an agreement.</span></span>|  
        |<span data-ttu-id="ac722-142">**設定檔**</span><span class="sxs-lookup"><span data-stu-id="ac722-142">**Profile**</span></span>|<span data-ttu-id="ac722-143">從下拉式清單中選取要和它建立協議的設定檔。</span><span class="sxs-lookup"><span data-stu-id="ac722-143">From the drop-down select a profile with which you want to create an agreement.</span></span>|  
        |<span data-ttu-id="ac722-144">**通訊協定的設定**</span><span class="sxs-lookup"><span data-stu-id="ac722-144">**Protocol Set**</span></span>|<span data-ttu-id="ac722-145">如果您在商務設定檔中建立了 EDIFACT 通訊協定集，即可從下拉式清單中選取該集合。</span><span class="sxs-lookup"><span data-stu-id="ac722-145">If you created an EDIFACT protocol set as part of the business profile, you can select that from the drop-down list.</span></span> <span data-ttu-id="ac722-146">如果您未在商務設定檔中建立 EDIFACT 通訊協定集，可以讓此處空白。</span><span class="sxs-lookup"><span data-stu-id="ac722-146">If you did not create an EDIFACT protocol set as part of the business profile, you can leave this empty.</span></span>|  
  
        > [!TIP]
        >  <span data-ttu-id="ac722-147">按`CTRL`，選取的商務設定檔，將會是合約的一部分，請以滑鼠右鍵按一下任一個商務設定檔，指向**新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="ac722-147">Press `CTRL`, select the business profiles that will be part of the agreement, right-click either business profile, point to **New**, and then click **Agreement**.</span></span> <span data-ttu-id="ac722-148">值夥伴名稱與兩個夥伴的商務設定檔將會自動填入**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ac722-148">The values for partner name and business profiles for both the partners will be automatically populated in the **Agreement Properties** dialog box.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ac722-149">一旦您選取另一個設定檔時，兩個索引標籤會加入至下一步**一般** 索引標籤。每個索引標籤各代表兩個合作對象之間的一個單向 EDIFACT 協議。</span><span class="sxs-lookup"><span data-stu-id="ac722-149">As soon as you select the other profile, two tabs are added next to the **General** tab. Each tab represents a one-way EDIFACT agreement between the two parties.</span></span> <span data-ttu-id="ac722-150">您將使用這些索引標籤來指定交換與交易集相關設定。</span><span class="sxs-lookup"><span data-stu-id="ac722-150">You use the tabs to specify interchange and transaction set related settings in the tabs.</span></span> <span data-ttu-id="ac722-151">如需詳細資訊，請參閱[設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)和[設定交易集設定 (X12)](../core/configuring-transaction-set-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="ac722-151">For more information, see [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md) and [Configuring Transaction Set Settings (X12)](../core/configuring-transaction-set-settings-x12.md).</span></span>  
  
    4.  <span data-ttu-id="ac722-152">選取**啟用協議**核取方塊以啟用協議並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-152">Select the **Enable Agreement** check box to enable the agreement and do the following:</span></span>  
  
        |<span data-ttu-id="ac722-153">使用</span><span class="sxs-lookup"><span data-stu-id="ac722-153">Use this</span></span>|<span data-ttu-id="ac722-154">動作</span><span class="sxs-lookup"><span data-stu-id="ac722-154">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="ac722-155">**來源**</span><span class="sxs-lookup"><span data-stu-id="ac722-155">**From**</span></span>|<span data-ttu-id="ac722-156">選取協議生效的日期與時間。</span><span class="sxs-lookup"><span data-stu-id="ac722-156">Select the date and time from which the agreement will be valid.</span></span>|  
        |<span data-ttu-id="ac722-157">**沒有結束日期**</span><span class="sxs-lookup"><span data-stu-id="ac722-157">**No End Date**</span></span>|<span data-ttu-id="ac722-158">如果不想設定停用協議的結束日期，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="ac722-158">Select this option if you do not want to set an end date when the agreement is disabled.</span></span>|  
        |<span data-ttu-id="ac722-159">**結束於**</span><span class="sxs-lookup"><span data-stu-id="ac722-159">**End By**</span></span>|<span data-ttu-id="ac722-160">選取此選項並指定協議的有效截止日期與時間。</span><span class="sxs-lookup"><span data-stu-id="ac722-160">Select this option and specify the date and time until which the agreement will be valid.</span></span>|  
  
    5.  <span data-ttu-id="ac722-161">在**一般主控件設定**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-161">In the **Common Host Settings** section, do the following:</span></span>  
  
        |<span data-ttu-id="ac722-162">使用</span><span class="sxs-lookup"><span data-stu-id="ac722-162">Use this</span></span>|<span data-ttu-id="ac722-163">動作</span><span class="sxs-lookup"><span data-stu-id="ac722-163">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="ac722-164">**將錯誤記錄到事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="ac722-164">**Log errors to event log**</span></span>|<span data-ttu-id="ac722-165">選取此選項可將 EDI 引擎 (EDI 管線、批次處理協調流程、路由協調流程等) 產生的任何錯誤，與內容資訊一起記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="ac722-165">Select this option if you want to log any errors generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.</span></span>|  
        |<span data-ttu-id="ac722-166">**將警告記錄到事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="ac722-166">**Log warnings to event log**</span></span>|<span data-ttu-id="ac722-167">選取此選項可將 EDI 引擎 (EDI 管線、批次處理協調流程、路由協調流程等) 產生的任何警告，與內容資訊一起記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="ac722-167">Select this option if you want to log any warnings generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.</span></span>|  
        |<span data-ttu-id="ac722-168">**開啟報表**</span><span class="sxs-lookup"><span data-stu-id="ac722-168">**Turn ON reporting**</span></span>|<span data-ttu-id="ac722-169">選取此選項可顯示所有 EDI 訊息 （內送和外寄） 的狀態項目上**EDI 交換和相互關聯的 ACK 狀態** 索引標籤**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac722-169">Select this option to display status entries for all EDI messages (incoming and outgoing) on the **EDI Interchange and Correlated ACK Status** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="ac722-170">如果取消核取此選項，就不會顯示狀態項目。</span><span class="sxs-lookup"><span data-stu-id="ac722-170">If unchecked, no status entries will be displayed.</span></span>|  
        |<span data-ttu-id="ac722-171">**儲存報告的訊息內容**</span><span class="sxs-lookup"><span data-stu-id="ac722-171">**Store message payload for reporting**</span></span>|<span data-ttu-id="ac722-172">如果您選取**開啟報告**，選取此選項來儲存交易設定的追蹤 (BizTalkDTADb) 資料庫 EDI 資料表中。</span><span class="sxs-lookup"><span data-stu-id="ac722-172">If you selected **Turn ON reporting**, select this option to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.</span></span>|  
  
3.  <span data-ttu-id="ac722-173">在**一般**索引標籤**連絡人資訊**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-173">In the **General** tab, on the **Contact Information** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="ac722-174">在**Contact1**索引標籤上，輸入與您要建立協議的合作對象的設定檔的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="ac722-174">In the **Contact1** tab, enter the contact information for the party’s profile with which you are creating an agreement.</span></span> <span data-ttu-id="ac722-175">此資訊僅供參考，BizTalk 執行階段不會使用它。</span><span class="sxs-lookup"><span data-stu-id="ac722-175">This data is for information purposes only; it will not be used by the BizTalk Runtime.</span></span>  
  
    2.  <span data-ttu-id="ac722-176">若要加入另一個連絡人索引標籤上，按一下 [**新增連絡人**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac722-176">To add another tab for contact, click the **New Contact** tab.</span></span>  
  
    3.  <span data-ttu-id="ac722-177">若要刪除連絡人索引標籤，按一下 **刪除**從右上角的索引標籤頁。</span><span class="sxs-lookup"><span data-stu-id="ac722-177">To delete a contact tab, click **Delete** from the top right corner of the tab page.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ac722-178">您無法刪除**Contact1**  索引標籤。您只能刪除您新增的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac722-178">You cannot delete the **Contact1** tab. You can only delete the new tabs that you add.</span></span>  
  
4.  <span data-ttu-id="ac722-179">在**一般**索引標籤**其他屬性**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac722-179">In the **General** tab, on the **Additional Properties** page, do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac722-180">BizTalk Server 不會使用您在此頁面指定的資訊處理任何作業；此資料僅供參考。</span><span class="sxs-lookup"><span data-stu-id="ac722-180">The information you specify on this page is not used by the BizTalk Server for any processing; this data is for information purposes only.</span></span>  
  
    1.  <span data-ttu-id="ac722-181">在**其他屬性**方格中，輸入您想要加入的任何資訊與相關合作對象或協議名稱 / 值組。</span><span class="sxs-lookup"><span data-stu-id="ac722-181">In the **Additional Properties** grid, enter name-value pairs for any information that you want to add related to the party or agreement.</span></span>  <span data-ttu-id="ac722-182">請輸入名稱-值組來儲存合作對象的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="ac722-182">Enter a name-value pair to store any information about the party.</span></span> <span data-ttu-id="ac722-183">您可以視需要新增任意數目的名稱-值組。</span><span class="sxs-lookup"><span data-stu-id="ac722-183">You can add as many name-value pairs as you want.</span></span>  
  
         <span data-ttu-id="ac722-184">刪除名稱-值配對，選取的資料列，然後按一下**刪除**從右上角。</span><span class="sxs-lookup"><span data-stu-id="ac722-184">To delete a name-value pair, select the row and click **Delete** from the top-right corner.</span></span>  
  
    2.  <span data-ttu-id="ac722-185">在**文字 1**，**文字 2**，和**協議**文字方塊中，輸入合作對象的協議的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ac722-185">In the **Text 1**, **Text 2**, and **Agreement** text boxes, enter information about the agreement with a party.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="ac722-186">如果您按一下**確定**或**套用**提供所有的值列在這個頁面之後，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac722-186">If you click **OK** or **Apply** after providing all the values listed in this page, you will get an error.</span></span> <span data-ttu-id="ac722-187">這是因為尚未提供建立協議所需的必要值。</span><span class="sxs-lookup"><span data-stu-id="ac722-187">That is because the mandatory values to create an agreement are not yet provided.</span></span> <span data-ttu-id="ac722-188">這些是上的 UNB2 和 UNB3 值**識別碼**頁面的每個單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac722-188">These are UNB2 and UNB3 values on the **Identifiers** page of each one-way agreement tab.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ac722-189">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ac722-189">Next Steps</span></span>  
 <span data-ttu-id="ac722-190">您現在必須為協議設定交換或交易集設定。</span><span class="sxs-lookup"><span data-stu-id="ac722-190">You must now configure the interchange or transaction set settings for the agreement.</span></span> <span data-ttu-id="ac722-191">如需指示，請參閱[設定交換設定 (EDIFACT)](../core/configuring-interchange-settings-edifact.md)或[設定交易集設定 」 (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="ac722-191">For instructions see [Configuring Interchange Settings (EDIFACT)](../core/configuring-interchange-settings-edifact.md) or [Configuring Transaction Set Settings (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac722-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac722-192">See Also</span></span>  
 [<span data-ttu-id="ac722-193">設定 EDIFACT 特定協議屬性</span><span class="sxs-lookup"><span data-stu-id="ac722-193">Configuring EDIFACT-Specific Agreement Properties</span></span>](../core/configuring-edifact-specific-agreement-properties.md)