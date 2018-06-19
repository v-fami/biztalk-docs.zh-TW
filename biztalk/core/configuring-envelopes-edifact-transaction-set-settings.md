---
title: 設定信封 （EDIFACT 交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec140def-6155-4b8a-8489-6e0a530bd697
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1d910f52d9ea90ae0c486356a7ecb3b01bf07a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234630"
---
# <a name="configuring-envelopes-edifact-transaction-set-settings"></a><span data-ttu-id="2061b-102">設定信封 (EDIFACT 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="2061b-102">Configuring Envelopes (EDIFACT-Transaction Set Settings)</span></span>
<span data-ttu-id="2061b-103">在**信封**頁面**交易集設定** 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象之 EDIFACT 編碼交換的 UNG 和 UNH 區段。</span><span class="sxs-lookup"><span data-stu-id="2061b-103">In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the UNG and UNH segments for an EDIFACT-encoded interchange that it sends to the party.</span></span>  
  
 <span data-ttu-id="2061b-104">UNG 區段是識別和指定 EDIFACT 編碼交換之功能群組的標頭。</span><span class="sxs-lookup"><span data-stu-id="2061b-104">The UNG segment is the header that identifies and specifies a functional group of an EDIFACT-encoded interchange.</span></span> <span data-ttu-id="2061b-105">其中包含準備功能群組的日期與時間資訊，以及功能群組中文件的類型與版本資訊。</span><span class="sxs-lookup"><span data-stu-id="2061b-105">It contains information about the date and time that the functional group was prepared, together with the type and version of the document in the functional group.</span></span>  
  
 <span data-ttu-id="2061b-106">UNH 區段則是 EDIFACT 編碼交換的訊息標頭區段。</span><span class="sxs-lookup"><span data-stu-id="2061b-106">The UNH segment is the message header segment of an EDIFACT-encoded interchange.</span></span> <span data-ttu-id="2061b-107">它提供訊息類型以及負責維護訊息類型發佈之代理商的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2061b-107">It provides information about the message type, and the agency responsible for maintaining the publication of the message type.</span></span> <span data-ttu-id="2061b-108">此區段會指示交換內文件的起始處，以及後面接著的文件的類型。</span><span class="sxs-lookup"><span data-stu-id="2061b-108">This segment indicates the start of a document in an interchange and the type of document that follows.</span></span>  
  
 <span data-ttu-id="2061b-109">在**功能群組標頭 (UNG)**  區段中，您將建立關聯**UNG**值與**UNH**值和命名空間。</span><span class="sxs-lookup"><span data-stu-id="2061b-109">In the **Functional group header (UNG)** section, you associate **UNG** values with **UNH** values and a namespace.</span></span> <span data-ttu-id="2061b-110">BizTalk Server 判斷 BizTalk XML 訊息已設定值**UNH**項目和**目標命名空間**格線資料列，在 BizTalk Server 將會填入**UNG**資料元素，使用方格同一列的值。</span><span class="sxs-lookup"><span data-stu-id="2061b-110">When BizTalk Server determines that a BizTalk XML message has the values set for the **UNH** elements and the **Target namespace** in a row of the grid, BizTalk Server will populate the **UNG** data elements with the values from the same row of the grid.</span></span> <span data-ttu-id="2061b-111">值**UNH**項目和**目標命名空間**必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2061b-111">The values of the **UNH** elements and the **Target namespace** must be unique.</span></span>  
  
 <span data-ttu-id="2061b-112">如果訊息沒有相符項目與**UNH**項目和**目標命名空間**中任何資料列，BizTalk Server 將會填入值的訊息**UNG**預設資料列中的項目。</span><span class="sxs-lookup"><span data-stu-id="2061b-112">If a message does not have a match with the **UNH** elements and the **Target namespace** in any row, BizTalk Server will populate the message with the values of the **UNG** elements in the default row.</span></span> <span data-ttu-id="2061b-113">即使訊息沒有具有相符項目，就會使用這些值**UNH**項目和**目標命名空間**與預設列。</span><span class="sxs-lookup"><span data-stu-id="2061b-113">These values will be used even if the message does not have a match with the **UNH** elements and the **Target namespace** of the default row.</span></span>  
  
 <span data-ttu-id="2061b-114">當 BizTalk 引擎決定 BizTalk XML 訊息具有為 UNH 項目和目標命名空間設定的值時，引擎會以為它們設定在方格中，提供的值填入訊息中的 UNG 元素**建立群組區段**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2061b-114">When the BizTalk engine determines that a BizTalk XML message has the values set for the UNH elements and the Target namespace, the engine will populate the UNG elements in the message with the values set for them in the grid, provided the **Create Grouping Segments** checkbox is checked.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2061b-115">在**功能群組標頭 (UNG)** 區段中，如果您在方格中，輸入欄位的任何設定，然後又刪除該設定，您必須刪除一整列，或該頁面將會通過驗證。</span><span class="sxs-lookup"><span data-stu-id="2061b-115">In the **Functional group header (UNG)**  section, if you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2061b-116">所有屬性已停都用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**檢查方塊的合作對象 a。不過，在相同頁面上啟用的所有屬性**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="2061b-116">All properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are enabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2061b-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="2061b-117">Prerequisites</span></span>  
 <span data-ttu-id="2061b-118">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="2061b-118">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-ung-and-unh-segments"></a><span data-ttu-id="2061b-119">若要定義 UNG 和 UNH 區段</span><span class="sxs-lookup"><span data-stu-id="2061b-119">To define the UNG and UNH segments</span></span>  
  
1.  <span data-ttu-id="2061b-120">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="2061b-120">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="2061b-121">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2061b-121">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2061b-122">在單向協議索引標籤底下**交易集設定**區段中，按一下**信封**。</span><span class="sxs-lookup"><span data-stu-id="2061b-122">On a one-way agreement tab, under **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="2061b-123">在格線的某列中，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="2061b-123">In a row of the grid, enter the following values:</span></span>  
  
    -   <span data-ttu-id="2061b-124">在**針對訊息類型 UNH2.1**資料行中，輸入交易集類型。</span><span class="sxs-lookup"><span data-stu-id="2061b-124">In the **For message type UNH2.1** column, enter a transaction set type.</span></span> <span data-ttu-id="2061b-125">(最多 6 個字元)。</span><span class="sxs-lookup"><span data-stu-id="2061b-125">(Maximum, six characters).</span></span>  
  
    -   <span data-ttu-id="2061b-126">在**UNH2.2**資料行中，輸入訊息版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2061b-126">In the **UNH2.2**  column, enter the message version number.</span></span> <span data-ttu-id="2061b-127">(最少 1 個字元，最多 3 個字元)。</span><span class="sxs-lookup"><span data-stu-id="2061b-127">(Minimum, one character; maximum, three characters).</span></span>  
  
    -   <span data-ttu-id="2061b-128">在**UNH2.3**資料行中，輸入訊息版次號碼。</span><span class="sxs-lookup"><span data-stu-id="2061b-128">In the **UNH2.3** column, enter the message release number.</span></span> <span data-ttu-id="2061b-129">(最少 1 個字元，最多 3 個字元)。</span><span class="sxs-lookup"><span data-stu-id="2061b-129">(Minimum, one character; maximum, three characters).</span></span>  
  
    -   <span data-ttu-id="2061b-130">在**UNH2.5**資料行中，輸入指定的代碼。</span><span class="sxs-lookup"><span data-stu-id="2061b-130">In the **UNH2.5** column, enter the assigned code.</span></span> <span data-ttu-id="2061b-131">(最多 6 個字元。</span><span class="sxs-lookup"><span data-stu-id="2061b-131">(Maximum, six characters.</span></span> <span data-ttu-id="2061b-132">必須是英數字元)。</span><span class="sxs-lookup"><span data-stu-id="2061b-132">Must be alphanumeric).</span></span>  
  
    -   <span data-ttu-id="2061b-133">在**目標命名空間**資料行中，選取的結構描述的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="2061b-133">In the **Target namespace** column, select the target namespace of the schema.</span></span> <span data-ttu-id="2061b-134">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-134">This is a required field.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2061b-135">這些值將由 BizTalk Server 用來與其所建置之交換的關聯值進行比較。</span><span class="sxs-lookup"><span data-stu-id="2061b-135">These will be the values that BizTalk Server will compare with the values associated with the interchange it is building.</span></span>  
  
4.  <span data-ttu-id="2061b-136">在格線的相同列中，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="2061b-136">In the same row of the grid, enter the following values:</span></span>  
  
    -   <span data-ttu-id="2061b-137">如**UNG1** （功能群組識別），輸入最少一個字元，最多六個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-137">For the **UNG1** (Functional group identification), enter an alphanumeric value with a minimum of one character and a maximum of six characters.</span></span> <span data-ttu-id="2061b-138">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-138">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-139">如**UNG2.1** （應用程式傳送者識別），輸入最少一個字元，最多 35 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-139">For **UNG2.1** (Application sender identification), enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="2061b-140">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-140">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-141">如**UNG2.2** （應用程式傳送者辨識符號），輸入英數值，最多四個字元。</span><span class="sxs-lookup"><span data-stu-id="2061b-141">For **UNG2.2** (Application sender code qualifier), enter an alphanumeric value, with a maximum of four characters.</span></span> <span data-ttu-id="2061b-142">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-142">This is an optional field.</span></span>  
  
    -   <span data-ttu-id="2061b-143">如**UNG3.1** （應用程式收件者識別），輸入最少一個字元，最多 35 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-143">For **UNG3.1** (Application recipient identification), enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="2061b-144">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-144">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-145">如**UNG3.2** （應用程式收件者代碼辨識符號，） 輸入最多四個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-145">For **UNG3.2** (Application recipient code qualifier), enter an alphanumeric value, with a maximum of four characters.</span></span> <span data-ttu-id="2061b-146">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-146">This is an optional field.</span></span>  
  
    -   <span data-ttu-id="2061b-147">如**UNG6** （控管單位），輸入最少 1 個，最多兩個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-147">For **UNG6** (Controlling agency), enter an alphanumeric value with a minimum of one and a maximum of two.</span></span> <span data-ttu-id="2061b-148">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-148">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-149">如**UNG7.1** （訊息類型版本號碼），輸入最少一個字元，最多三個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-149">For **UNG7.1** (Message type version number), enter an alphanumeric value with a minimum of one character and a maximum of three characters.</span></span> <span data-ttu-id="2061b-150">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-150">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-151">如**UNG7.2** （訊息類型版次號碼），輸入最少一個字元，最多三個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-151">For **UNG7.2** (Message type release number), enter an alphanumeric value with a minimum of one character and a maximum of three characters.</span></span> <span data-ttu-id="2061b-152">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-152">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-153">如**UNG7.3** （關聯指定代碼），輸入最少 1 個字元，最多 6 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-153">For **UNG7.3** (Association assigned code), enter an alphanumeric value with a minimum of 1 character and a maximum of 6 characters.</span></span> <span data-ttu-id="2061b-154">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-154">This is a required field.</span></span>  
  
    -   <span data-ttu-id="2061b-155">如**UNG8** （應用程式密碼），輸入最少一個字元，最多 14 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="2061b-155">For **UNG8** (Application password), enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="2061b-156">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="2061b-156">This is a required field.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2061b-157">這些會是 BizTalk Server 將在它本身正在建置如果交換的 UNG 欄位中輸入的值**針對訊息類型 UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目標命名空間**相同的資料列中的項目都符合與交換關聯。</span><span class="sxs-lookup"><span data-stu-id="2061b-157">These will be the values that BizTalk Server will enter in the UNG fields of the interchange it is building if the  **For message type UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements in the same row are a match for those associated with the interchange.</span></span>  
  
5.  <span data-ttu-id="2061b-158">重複步驟 4 和 5，將其他列輸入到格線中。</span><span class="sxs-lookup"><span data-stu-id="2061b-158">Repeat steps 4 and 5 to enter additional rows into the grid.</span></span>  
  
6.  <span data-ttu-id="2061b-159">在方格中的一個資料列，按一下 **預設**將它指定為預設資料列。</span><span class="sxs-lookup"><span data-stu-id="2061b-159">For one row in the grid, click **Default** to designate it as the default row.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2061b-160">如果訊息沒有相符項目與**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**的目標命名空間**任何資料列，BizTalk Server 中的項目將會填入訊息的值**UNG1**， **UNG2.1**， **UNG2.2**， **UNG3.1**， **UNG3.2**， **UNG6**， **UNG7.1**， **UNG7.2**， **UNG7.3**，和**UNG8**預設列中的項目。</span><span class="sxs-lookup"><span data-stu-id="2061b-160">If a message does not have a match with the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements in any row, BizTalk Server will populate the message with the values for the **UNG1**, **UNG2.1**, **UNG2.2**, **UNG3.1**, **UNG3.2**, **UNG6**, **UNG7.1**, **UNG7.2**, **UNG7.3**, and **UNG8** elements in the default row.</span></span> <span data-ttu-id="2061b-161">即使訊息沒有具有相符項目，就會使用這些值**針對訊息類型 UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目標命名空間**與預設列的項目。</span><span class="sxs-lookup"><span data-stu-id="2061b-161">These values will be used even if the message does not have a match with the **For message type UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements of the default row.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2061b-162">如果沒有預設值的資料列已選取，而且訊息沒有相符的項目**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目標命名空間**項目中任何資料列，BizTalk 會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="2061b-162">If no default row is selected, and the message does not have a match for the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements in any row, BizTalk will suspend the message.</span></span>  
  
7.  <span data-ttu-id="2061b-163">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2061b-163">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2061b-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2061b-164">See Also</span></span>  
 [<span data-ttu-id="2061b-165">設定交易集設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="2061b-165">Configuring Transaction Set Settings (EDIFACT)</span></span>](../core/configuring-transaction-set-settings-edifact.md)