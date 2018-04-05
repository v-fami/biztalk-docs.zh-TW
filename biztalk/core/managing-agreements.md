---
title: 管理協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.resultsobject.agreement
ms.assetid: e9c6cdd1-8c17-4b1e-a556-2b287593bb9d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 012a4a5032bd9f9e9a66b855d41a83b5dc5736d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-agreements"></a><span data-ttu-id="745f7-102">管理協議</span><span class="sxs-lookup"><span data-stu-id="745f7-102">Managing Agreements</span></span>
<span data-ttu-id="745f7-103">交易夥伴協議 (TPA) 的定義是，兩個交易夥伴之間透過特定 B2B 通訊協定交易訊息時所採用的決定性與繫結性協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-103">A Trading Partner Agreement (TPA) is defined as a definitive and binding agreement between two trading partners for transacting messages over a specific B2B Protocol.</span></span> <span data-ttu-id="745f7-104">請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="745f7-104">See [Trading Partner Agreement](../core/trading-partner-agreement.md).</span></span> 

<span data-ttu-id="745f7-105">本主題顯示如何建立、 檢視、 編輯、 啟用、 停用，或刪除協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-105">This topics shows you how to create, view, edit, enable, disable, or delete an agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="745f7-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="745f7-106">Prerequisites</span></span>  
 <span data-ttu-id="745f7-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="745f7-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="create-an-agreement"></a><span data-ttu-id="745f7-108">建立協議</span><span class="sxs-lookup"><span data-stu-id="745f7-108">Create an agreement</span></span>  
  
1.  <span data-ttu-id="745f7-109">開啟**BizTalk Server 管理**，展開 [BizTalk 群組] 並選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="745f7-109">Open **BizTalk Server Administration**, expand the BizTalk group, and select **Parties**.</span></span> 
2. <span data-ttu-id="745f7-110">在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下您要建立的合約選取一部分的商務設定檔**新增**，然後選取**協議**。</span><span class="sxs-lookup"><span data-stu-id="745f7-110">In the **Parties and Business Profiles** page, right-click a business profile that is part of the agreement you are creating, select **New**, and then select **Agreement**.</span></span>  
  
3.  <span data-ttu-id="745f7-111">在**一般屬性**:</span><span class="sxs-lookup"><span data-stu-id="745f7-111">In the **General Properties**:</span></span> 
  
    1.  <span data-ttu-id="745f7-112">在**協議參數**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-112">In the **Agreement Parameters** section, do the following:</span></span>  
  
        |<span data-ttu-id="745f7-113">使用</span><span class="sxs-lookup"><span data-stu-id="745f7-113">Use this</span></span>|<span data-ttu-id="745f7-114">動作</span><span class="sxs-lookup"><span data-stu-id="745f7-114">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="745f7-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="745f7-115">**Name**</span></span>|<span data-ttu-id="745f7-116">輸入協議的名稱</span><span class="sxs-lookup"><span data-stu-id="745f7-116">Enter a name for the agreement</span></span>|  
        |<span data-ttu-id="745f7-117">**ID**</span><span class="sxs-lookup"><span data-stu-id="745f7-117">**ID**</span></span>|<span data-ttu-id="745f7-118">列示協議的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="745f7-118">Lists unique identification for the agreement.</span></span> <span data-ttu-id="745f7-119">此文字方塊是唯讀的並顯示協議識別碼，當您選取之後**套用**第一個時間，以及設定會被接受。</span><span class="sxs-lookup"><span data-stu-id="745f7-119">This text box is read-only, and display the agreement ID after you select **Apply** for the first time, and the settings are accepted.</span></span>|  
        |<span data-ttu-id="745f7-120">**狀態**</span><span class="sxs-lookup"><span data-stu-id="745f7-120">**Status**</span></span>|<span data-ttu-id="745f7-121">指定協議的狀態。</span><span class="sxs-lookup"><span data-stu-id="745f7-121">Specifies the status of the agreement.</span></span> <span data-ttu-id="745f7-122">根據預設，在建立協議**Active**狀態。</span><span class="sxs-lookup"><span data-stu-id="745f7-122">By default, an agreement is created in an **Active** state.</span></span> <span data-ttu-id="745f7-123">如果您想要停用時第一次建立時，選取協議**停用**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="745f7-123">If you want the agreement to be disabled when it is first created, select **Disabled** from the drop-down list.</span></span>|  
        |<span data-ttu-id="745f7-124">**通訊協定**</span><span class="sxs-lookup"><span data-stu-id="745f7-124">**Protocol**</span></span>|<span data-ttu-id="745f7-125">指定協議的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="745f7-125">Specifies the protocol for the agreement.</span></span><br /><br /> <span data-ttu-id="745f7-126">-若為 X12 編碼通訊協定，請選取**X12**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="745f7-126">-   For an X12 encoding protocol, select **X12** from the drop-down list.</span></span> <span data-ttu-id="745f7-127">請參閱[設定 X12 特有協議屬性](../core/configuring-x12-specific-agreement-properties.md)</span><span class="sxs-lookup"><span data-stu-id="745f7-127">See [Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md)</span></span><br /><span data-ttu-id="745f7-128">-若為 EDIFACT 編碼通訊協定，請選取**EDIFACT**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="745f7-128">-   For an EDIFACT encoding protocol, select **EDIFACT** from the drop-down list.</span></span>  <span data-ttu-id="745f7-129">請參閱[設定 EDIFACT 特定協議屬性](../core/configuring-edifact-specific-agreement-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="745f7-129">See [Configuring EDIFACT-Specific Agreement Properties](../core/configuring-edifact-specific-agreement-properties.md).</span></span><br /><span data-ttu-id="745f7-130">-若為 AS2 編碼通訊協定，請選取**AS2**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="745f7-130">-   For an AS2 encoding protocol, select **AS2** from the drop-down list.</span></span> <span data-ttu-id="745f7-131">請參閱[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="745f7-131">See [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).</span></span> <br/><br/><span data-ttu-id="745f7-132">**注意**</span><span class="sxs-lookup"><span data-stu-id="745f7-132">**Note**</span></span><br/>  <span data-ttu-id="745f7-133">單向協議索引標籤中會提供協議屬性。</span><span class="sxs-lookup"><span data-stu-id="745f7-133">The agreement properties are provided in the one-way agreement tabs.</span></span> <span data-ttu-id="745f7-134">當您選取要用來建立協議的第二個設定檔之後，單向協議索引標籤就會顯示。</span><span class="sxs-lookup"><span data-stu-id="745f7-134">The one-way agreement tabs appear after you have selected the second profile with which the agreement will be created.</span></span> <span data-ttu-id="745f7-135">您會在下列步驟中選取第二個夥伴。</span><span class="sxs-lookup"><span data-stu-id="745f7-135">You select the second partner in the following steps.</span></span>|  
  
    2.  <span data-ttu-id="745f7-136">在**第一個夥伴**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-136">In the **First Partner** section, do the following:</span></span>  
  
        |<span data-ttu-id="745f7-137">使用</span><span class="sxs-lookup"><span data-stu-id="745f7-137">Use this</span></span>|<span data-ttu-id="745f7-138">動作</span><span class="sxs-lookup"><span data-stu-id="745f7-138">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="745f7-139">**名稱**</span><span class="sxs-lookup"><span data-stu-id="745f7-139">**Name**</span></span>|<span data-ttu-id="745f7-140">顯示要建立協議的商務設定檔所屬之夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="745f7-140">Displays the partner name that has the business profile for which you are creating the agreement.</span></span> <span data-ttu-id="745f7-141">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="745f7-141">This text box is read-only.</span></span>|  
        |<span data-ttu-id="745f7-142">**設定檔**</span><span class="sxs-lookup"><span data-stu-id="745f7-142">**Profile**</span></span>|<span data-ttu-id="745f7-143">顯示您正在為它建立協議的設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="745f7-143">Displays the name of the profile for which you are creating the agreement.</span></span> <span data-ttu-id="745f7-144">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="745f7-144">This text box is read-only.</span></span>|  
        |<span data-ttu-id="745f7-145">**通訊協定的設定**</span><span class="sxs-lookup"><span data-stu-id="745f7-145">**Protocol Set**</span></span>|<span data-ttu-id="745f7-146">如果您在商務設定檔中建立了 X12 通訊協定集，即可從下拉式清單中選取該集合。</span><span class="sxs-lookup"><span data-stu-id="745f7-146">If you created an X12 protocol set as part of the business profile, you can select that from the drop-down list.</span></span> <span data-ttu-id="745f7-147">如果您未在商務設定檔建立 X12 通訊協定集，可以保留空白。</span><span class="sxs-lookup"><span data-stu-id="745f7-147">If you did not create an X12 protocol set as part of the business profile, you can leave this empty.</span></span>|  
  
    3.  <span data-ttu-id="745f7-148">在**第二個夥伴**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-148">In the **Second Partner** section, do the following:</span></span>  
  
        |<span data-ttu-id="745f7-149">使用</span><span class="sxs-lookup"><span data-stu-id="745f7-149">Use this</span></span>|<span data-ttu-id="745f7-150">動作</span><span class="sxs-lookup"><span data-stu-id="745f7-150">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="745f7-151">**名稱**</span><span class="sxs-lookup"><span data-stu-id="745f7-151">**Name**</span></span>|<span data-ttu-id="745f7-152">從下拉式清單中選取要與他的商務設定檔建立協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="745f7-152">From the drop-down select a party that has the business profile with which you want to create an agreement.</span></span>|  
        |<span data-ttu-id="745f7-153">**設定檔**</span><span class="sxs-lookup"><span data-stu-id="745f7-153">**Profile**</span></span>|<span data-ttu-id="745f7-154">從下拉式清單中選取要和它建立協議的設定檔。</span><span class="sxs-lookup"><span data-stu-id="745f7-154">From the drop-down select a profile with which you want to create an agreement.</span></span>|  
        |<span data-ttu-id="745f7-155">**通訊協定的設定**</span><span class="sxs-lookup"><span data-stu-id="745f7-155">**Protocol Set**</span></span>|<span data-ttu-id="745f7-156">如果您在商務設定檔中建立了 X12 通訊協定集，即可從下拉式清單中選取該集合。</span><span class="sxs-lookup"><span data-stu-id="745f7-156">If you created an X12 protocol set as part of the business profile, you can select that from the drop-down list.</span></span> <span data-ttu-id="745f7-157">如果您未在商務設定檔建立 X12 通訊協定集，可以保留空白。</span><span class="sxs-lookup"><span data-stu-id="745f7-157">If you did not create an X12 protocol set as part of the business profile, you can leave this empty.</span></span>|  
  
        > [!TIP]
        >  <span data-ttu-id="745f7-158">按`CTRL`，選取的商務設定檔會是合約的一部分，以滑鼠右鍵按一下任一個商務設定檔，請選取**新增**，然後選取**協議**。</span><span class="sxs-lookup"><span data-stu-id="745f7-158">Press `CTRL`, select the business profiles that will be part of the agreement, right-click either business profile, select **New**, and then select **Agreement**.</span></span> <span data-ttu-id="745f7-159">值夥伴名稱與兩個夥伴的商務設定檔會自動填入中**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="745f7-159">The values for partner name and business profiles for both the partners are automatically populated in the **Agreement Properties** dialog box.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="745f7-160">一旦您選取另一個設定檔時，兩個索引標籤會加入至下一步**一般** 索引標籤。每個索引標籤各代表兩個合作對象之間的一個單向協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-160">As soon as you select the other profile, two tabs are added next to the **General** tab. Each tab represents a one-way agreement between the two parties.</span></span> <span data-ttu-id="745f7-161">您可以使用索引標籤來輸入協議屬性。</span><span class="sxs-lookup"><span data-stu-id="745f7-161">You use the tabs to enter the agreement properties.</span></span>  
  
    4.  <span data-ttu-id="745f7-162">選取**啟用協議**核取方塊以啟用協議，並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-162">Select the **Enable Agreement** check box to enable the agreement, and do the following:</span></span>  
  
        |<span data-ttu-id="745f7-163">使用</span><span class="sxs-lookup"><span data-stu-id="745f7-163">Use this</span></span>|<span data-ttu-id="745f7-164">動作</span><span class="sxs-lookup"><span data-stu-id="745f7-164">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="745f7-165">**來源**</span><span class="sxs-lookup"><span data-stu-id="745f7-165">**From**</span></span>|<span data-ttu-id="745f7-166">選取的日期和時間的協議的有效來源。</span><span class="sxs-lookup"><span data-stu-id="745f7-166">Select the date and time from which the agreement is valid.</span></span>|  
        |<span data-ttu-id="745f7-167">**沒有結束日期**</span><span class="sxs-lookup"><span data-stu-id="745f7-167">**No End Date**</span></span>|<span data-ttu-id="745f7-168">如果不想設定停用協議的結束日期，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="745f7-168">Select this option if you do not want to set an end date when the agreement is disabled.</span></span>|  
        |<span data-ttu-id="745f7-169">**結束於**</span><span class="sxs-lookup"><span data-stu-id="745f7-169">**End By**</span></span>|<span data-ttu-id="745f7-170">選取此選項可輸入的日期和時間，直到協議有效。</span><span class="sxs-lookup"><span data-stu-id="745f7-170">Select this option to enter the date and time until the agreement is valid.</span></span>|  
  
    5.  <span data-ttu-id="745f7-171">在**一般主控件設定**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-171">In the **Common Host Settings** section, do the following:</span></span>  
  
        |<span data-ttu-id="745f7-172">使用</span><span class="sxs-lookup"><span data-stu-id="745f7-172">Use this</span></span>|<span data-ttu-id="745f7-173">動作</span><span class="sxs-lookup"><span data-stu-id="745f7-173">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="745f7-174">**將錯誤記錄到事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="745f7-174">**Log errors to event log**</span></span>|<span data-ttu-id="745f7-175">選取此選項可將 EDI 引擎 (EDI 管線、批次處理協調流程、路由協調流程等) 產生的任何錯誤，與內容資訊一起記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="745f7-175">Select this option if you want to log any errors generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.</span></span><br/><br/><span data-ttu-id="745f7-176">**請注意**： 不適用於 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-176">**Note**:  Does not apply to AS2 agreements.</span></span>|  
        |<span data-ttu-id="745f7-177">**將警告記錄到事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="745f7-177">**Log warnings to event log**</span></span>|<span data-ttu-id="745f7-178">選取此選項可將 EDI 引擎 (EDI 管線、批次處理協調流程、路由協調流程等) 產生的任何警告，與內容資訊一起記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="745f7-178">Select this option if you want to log any warnings generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.</span></span> <br/><br/><span data-ttu-id="745f7-179">**請注意**： 不適用於 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-179">**Note**:  Does not apply to AS2 agreements.</span></span>|  
        |<span data-ttu-id="745f7-180">**開啟報表**</span><span class="sxs-lookup"><span data-stu-id="745f7-180">**Turn ON reporting**</span></span>|<span data-ttu-id="745f7-181">選取此選項可顯示所有 EDI 訊息 （內送和外寄） 的狀態項目上**EDI 交換和相互關聯的 ACK 狀態** 索引標籤**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="745f7-181">Select this option to display status entries for all EDI messages (incoming and outgoing) on the **EDI Interchange and Correlated ACK Status** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="745f7-182">如果未選取，則會不顯示任何狀態項目。</span><span class="sxs-lookup"><span data-stu-id="745f7-182">If unchecked, no status entries are displayed.</span></span>|  
        |<span data-ttu-id="745f7-183">**儲存報告的訊息內容**</span><span class="sxs-lookup"><span data-stu-id="745f7-183">**Store message payload for reporting**</span></span>|<span data-ttu-id="745f7-184">如果您選取**開啟報告**，選取此選項來儲存交易設定的追蹤 (BizTalkDTADb) 資料庫 EDI 資料表中。</span><span class="sxs-lookup"><span data-stu-id="745f7-184">If you selected **Turn ON reporting**, select this option to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.</span></span> <br/><br/><span data-ttu-id="745f7-185">**請注意**： 不適用於 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-185">**Note**:  Does not apply to AS2 agreements.</span></span>|  
  
4.  <span data-ttu-id="745f7-186">在**一般**索引標籤**連絡人資訊**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-186">In the **General** tab, on the **Contact Information** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="745f7-187">在**Contact1**索引標籤上，輸入與您要建立協議的合作對象的設定檔的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="745f7-187">In the **Contact1** tab, enter the contact information for the party’s profile with which you are creating an agreement.</span></span> <span data-ttu-id="745f7-188">此資料僅供資訊之用; 僅限BizTalk 執行階段不使用它。</span><span class="sxs-lookup"><span data-stu-id="745f7-188">This data is for information purposes only; it is not used by the BizTalk Runtime.</span></span>  
  
    2.  <span data-ttu-id="745f7-189">若要新增連絡人的另一個索引標籤，選取**新增連絡人** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="745f7-189">To add another tab for contact, select the **New Contact** tab.</span></span>  
  
    3.  <span data-ttu-id="745f7-190">若要刪除連絡人索引標籤，選取**刪除**從右上角的索引標籤頁。</span><span class="sxs-lookup"><span data-stu-id="745f7-190">To delete a contact tab, select **Delete** from the top right corner of the tab page.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="745f7-191">您無法刪除**Contact1**  索引標籤。您只能刪除您新增的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="745f7-191">You cannot delete the **Contact1** tab. You can only delete the new tabs that you add.</span></span>  
  
5.  <span data-ttu-id="745f7-192">在**一般**索引標籤**其他屬性**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="745f7-192">In the **General** tab, on the **Additional Properties** page, do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="745f7-193">在此頁面上輸入的資訊不是由 BizTalk Server 進行任何處理。此資料是僅供資訊。</span><span class="sxs-lookup"><span data-stu-id="745f7-193">The information you enter on this page is not used by the BizTalk Server for any processing; this data is for information purposes only.</span></span>  
  
    1.  <span data-ttu-id="745f7-194">在**其他屬性**方格中，輸入您想要加入的任何資訊與相關合作對象或協議名稱 / 值組。</span><span class="sxs-lookup"><span data-stu-id="745f7-194">In the **Additional Properties** grid, enter name-value pairs for any information that you want to add related to the party or agreement.</span></span>  <span data-ttu-id="745f7-195">請輸入名稱-值組來儲存合作對象的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="745f7-195">Enter a name-value pair to store any information about the party.</span></span> <span data-ttu-id="745f7-196">您可以視需要新增任意數目的名稱-值組。</span><span class="sxs-lookup"><span data-stu-id="745f7-196">You can add as many name-value pairs as you want.</span></span>  
  
         <span data-ttu-id="745f7-197">刪除名稱-值配對，選取資料列，並選取**刪除**從右上角。</span><span class="sxs-lookup"><span data-stu-id="745f7-197">To delete a name-value pair, select the row, and select **Delete** from the top-right corner.</span></span>  
  
    2.  <span data-ttu-id="745f7-198">在**文字 1**，**文字 2**，和**協議**文字方塊中，輸入合作對象的協議的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="745f7-198">In the **Text 1**, **Text 2**, and **Agreement** text boxes, enter information about the agreement with a party.</span></span>  
  
    3.  <span data-ttu-id="745f7-199">選取**套用**接受這些屬性，或選取**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="745f7-199">Select **Apply** to accept the properties, or select **OK** to complete the configuration setting.</span></span> <span data-ttu-id="745f7-200">任何一項動作會驗證設定。</span><span class="sxs-lookup"><span data-stu-id="745f7-200">Either action validates the settings.</span></span>  

## <a name="view-or-change-an-agreement"></a><span data-ttu-id="745f7-201">檢視或變更協議</span><span class="sxs-lookup"><span data-stu-id="745f7-201">View or change an agreement</span></span>  
  
1.  <span data-ttu-id="745f7-202">在**BizTalk Server 管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="745f7-202">In **BizTalk Server Administration**, select **Parties**.</span></span> 

2. <span data-ttu-id="745f7-203">在**合作對象與商務設定檔**頁面上，選取任何您想要檢視或編輯協議的兩個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="745f7-203">In the **Parties and Business Profiles** page, select any of the two business profile that have the agreement that you want to view or edit.</span></span>  
  
3.  <span data-ttu-id="745f7-204">在**協議**區段中，以滑鼠右鍵按一下 協議，然後再選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="745f7-204">In the **Agreements** section, right-click the agreement, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="745f7-205">在**協議屬性**、 檢視或編輯協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-205">In the **Agreement Properties**, view or edit the agreement.</span></span> <span data-ttu-id="745f7-206">您可以在不同的索引標籤和中的頁面上輸入的值**協議屬性**對話方塊方塊中，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="745f7-206">For the values that can be entered on the different tabs and pages in the **Agreement Properties** dialog box, see the following:</span></span>  
  
    |<span data-ttu-id="745f7-207">如需</span><span class="sxs-lookup"><span data-stu-id="745f7-207">For this</span></span>|<span data-ttu-id="745f7-208">請參閱</span><span class="sxs-lookup"><span data-stu-id="745f7-208">See this</span></span>|  
    |--------------|--------------|  
    |<span data-ttu-id="745f7-209">X12 協議</span><span class="sxs-lookup"><span data-stu-id="745f7-209">For X12 agreement</span></span>|[<span data-ttu-id="745f7-210">設定 X12 特有協議屬性</span><span class="sxs-lookup"><span data-stu-id="745f7-210">Configuring X12-Specific Agreement Properties</span></span>](../core/configuring-x12-specific-agreement-properties.md)|  
    |<span data-ttu-id="745f7-211">EDIFACT 協議</span><span class="sxs-lookup"><span data-stu-id="745f7-211">For EDIFACT agreement</span></span>|[<span data-ttu-id="745f7-212">設定 EDIFACT 特定協議屬性</span><span class="sxs-lookup"><span data-stu-id="745f7-212">Configuring EDIFACT-Specific Agreement Properties</span></span>](../core/configuring-edifact-specific-agreement-properties.md)|  
    |<span data-ttu-id="745f7-213">AS2 協議</span><span class="sxs-lookup"><span data-stu-id="745f7-213">For AS2 agreement</span></span>|[<span data-ttu-id="745f7-214">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="745f7-214">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)|  
  
5.  <span data-ttu-id="745f7-215">選取**套用**接受這些屬性，或選取**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="745f7-215">Select **Apply** to accept the properties, or select **OK** to complete the configuration setting.</span></span> <span data-ttu-id="745f7-216">任何一項動作會驗證設定。</span><span class="sxs-lookup"><span data-stu-id="745f7-216">Either action validates the settings.</span></span> 

## <a name="enable-or-disable-an-agreement"></a><span data-ttu-id="745f7-217">啟用或停用協議</span><span class="sxs-lookup"><span data-stu-id="745f7-217">Enable or disable an agreement</span></span>  
  
1.  <span data-ttu-id="745f7-218">在**BizTalk Server 管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="745f7-218">In **BizTalk Server Administration**, select **Parties**.</span></span> 

2. <span data-ttu-id="745f7-219">在**合作對象與商務設定檔**頁面上，選取任何具有您想要編輯的協議的兩個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="745f7-219">In the **Parties and Business Profiles** page, select any of the two business profile that have the agreement that you want to edit.</span></span>  
  
3.  <span data-ttu-id="745f7-220">在**協議**區段中，以滑鼠右鍵按一下 協議，然後再選取**啟用**或**停用**。</span><span class="sxs-lookup"><span data-stu-id="745f7-220">In the **Agreements** section, right-click the agreement, and then select **Enable** or **Disable**.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="745f7-221">根據預設，初次建立的協議一定是啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="745f7-221">When an agreement is first created, it is always enabled by default.</span></span> <span data-ttu-id="745f7-222">**啟用**選項才可以使用只有當協議停用。</span><span class="sxs-lookup"><span data-stu-id="745f7-222">The **Enable** option is available only when the agreement is disabled.</span></span> <span data-ttu-id="745f7-223">**停用**會提供選項只有在啟用協議時。</span><span class="sxs-lookup"><span data-stu-id="745f7-223">The **Disable** option is available only when the agreement is enabled.</span></span>  

## <a name="delete-an-agreement"></a><span data-ttu-id="745f7-224">刪除協議</span><span class="sxs-lookup"><span data-stu-id="745f7-224">Delete an agreement</span></span>  
1.  <span data-ttu-id="745f7-225">在**BizTalk Server 管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="745f7-225">In **BizTalk Server Administration**, select **Parties**.</span></span> 
  
2.  <span data-ttu-id="745f7-226">在**合作對象與商務設定檔**頁面上，選取任何具有您想要刪除的協議的兩個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="745f7-226">In the **Parties and Business Profiles** page, select any of the two business profile that have the agreement that you want to delete.</span></span>  
  
3.  <span data-ttu-id="745f7-227">在**協議**區段中，以滑鼠右鍵按一下您想要刪除，然後選取 協議**刪除**。</span><span class="sxs-lookup"><span data-stu-id="745f7-227">In the **Agreements** section, right-click the agreement that you want to delete, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="745f7-228">在**確認刪除協議**對話方塊中，選取**是**刪除協議。</span><span class="sxs-lookup"><span data-stu-id="745f7-228">In the **Confirm delete agreement** dialog box, select **Yes** to delete the agreement.</span></span>  

      
## <a name="see-also"></a><span data-ttu-id="745f7-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="745f7-229">See Also</span></span>  
 [<span data-ttu-id="745f7-230">管理 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="745f7-230">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)