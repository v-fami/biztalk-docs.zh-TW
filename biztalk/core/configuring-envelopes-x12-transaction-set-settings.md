---
title: 設定信封 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9313a7b9-72fa-4071-8c65-007371643179
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 519062fa4647cdc2c7c39dda19373ff888eaf601
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234334"
---
# <a name="configuring-envelopes-x12-transaction-set-settings"></a><span data-ttu-id="7a041-102">設定信封 (X12 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="7a041-102">Configuring Envelopes (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="7a041-103">在**可以**頁面**交易集設定** 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象的 X12 編碼交換的 GS 和 ST 區段。</span><span class="sxs-lookup"><span data-stu-id="7a041-103">In the **Envelops** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the GS and ST segments for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="7a041-104">GS 區段可識別並指定 X12 編碼交換的功能群組。</span><span class="sxs-lookup"><span data-stu-id="7a041-104">A GS segment identifies and specifies a functional group for an X12-encoded interchange.</span></span> <span data-ttu-id="7a041-105">ST 區段則是 X12 編碼交換的訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="7a041-105">An ST segment is the message header for an X12-encoded interchange.</span></span>  
  
 <span data-ttu-id="7a041-106">在此頁面上，您將相關聯的值**GS1**， **GS2**， **GS3**， **GS4**， **GS5**， **GS7**，和**GS8**資料元素的值與**交易類型**，**版本/版次**，和**目標命名空間**資料元素。</span><span class="sxs-lookup"><span data-stu-id="7a041-106">In this page, you associate values of the **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, and **GS8** data elements with values of the **Transaction Type**, **Version/Release**, and **Target namespace** data elements.</span></span> <span data-ttu-id="7a041-107">當 BizTalk 決定 BizTalk XML 訊息已設定值**交易類型**，**版本/版次**，和**目標命名空間**格線的某列中的項目BizTalk 將會填入**GS1**， **GS2**， **GS3**， **GS4**， **GS5**， **GS7**，和**GS8**資料元素中之信封的外寄交換使用方格同一列的值。</span><span class="sxs-lookup"><span data-stu-id="7a041-107">When BizTalk determines that a BizTalk XML message has the values set for the **Transaction Type**, **Version/Release**, and **Target namespace** elements in a row of the grid, BizTalk will populate the **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, and **GS8** data elements in the envelope of the outgoing interchange with the values from the same row of the grid.</span></span> <span data-ttu-id="7a041-108">值**交易類型**，**版本/版次**，和**目標命名空間**必須是唯一的項目。</span><span class="sxs-lookup"><span data-stu-id="7a041-108">The values of the **Transaction Type**, **Version/Release**, and **Target namespace** elements must be unique.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a041-109">如果您為格線中的任何欄位輸入設定，然後又要刪除該設定，那麼就必須刪除一整列，否則該頁面將不會讓您通過驗證。</span><span class="sxs-lookup"><span data-stu-id="7a041-109">If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a041-110">這個主題也適用於 HIPAA 相關設定。</span><span class="sxs-lookup"><span data-stu-id="7a041-110">This topic applies also to HIPAA-related settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7a041-111">所有屬性已停都用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**檢查方塊的合作對象 a。不過，在相同頁面上啟用的所有屬性**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="7a041-111">All properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are enabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7a041-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="7a041-112">Prerequisites</span></span>  
 <span data-ttu-id="7a041-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="7a041-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-gs-and-st-segments"></a><span data-ttu-id="7a041-114">若要定義 GS 和 ST 區段</span><span class="sxs-lookup"><span data-stu-id="7a041-114">To define the GS and ST segments</span></span>  
  
1.  <span data-ttu-id="7a041-115">建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="7a041-115">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="7a041-116">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7a041-116">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7a041-117">在單向協議索引標籤底下**交易集設定**區段中，按一下**信封**。</span><span class="sxs-lookup"><span data-stu-id="7a041-117">On a one-way agreement tab, under **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="7a041-118">在方格的某一列，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="7a041-118">In a row of the grid, enter the following:</span></span>  
  
    -   <span data-ttu-id="7a041-119">如**交易類型**欄位中，選取代表 「 交易集識別項代碼，從下拉式清單的值。</span><span class="sxs-lookup"><span data-stu-id="7a041-119">For the **Transaction Type** field, select a value for the transaction set identifier code from the drop-down list.</span></span>  
  
    -   <span data-ttu-id="7a041-120">如**版本/版次**，輸入最少一個字元，最多 12 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="7a041-120">For **Version/Release**, enter an alphanumeric value with a minimum of one character and a maximum of 12 characters.</span></span>  
  
    -   <span data-ttu-id="7a041-121">如**目標命名空間**項目，從下拉式清單中選取值，或輸入命名空間。</span><span class="sxs-lookup"><span data-stu-id="7a041-121">For **Target namespace** elements, select a value from the drop-down list, or enter a namespace.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7a041-122">這些值將由 BizTalk Server 用來與其所建置之交換的關聯值進行比較。</span><span class="sxs-lookup"><span data-stu-id="7a041-122">These will be the values that BizTalk Server will compare with the values associated with the interchange it is building.</span></span>  
  
4.  <span data-ttu-id="7a041-123">在方格的同一列中，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="7a041-123">In the same row of the grid, enter the following:</span></span>  
  
    -   <span data-ttu-id="7a041-124">如**GS1**，從下拉式清單中選取功能代碼的值。</span><span class="sxs-lookup"><span data-stu-id="7a041-124">For **GS1**, select a value for the functional code from the drop-down list.</span></span> <span data-ttu-id="7a041-125">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-125">This is an optional field.</span></span>  
  
    -   <span data-ttu-id="7a041-126">如**GS2**，輸入應用程式傳送者最少 2 個字元，最多 15 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="7a041-126">For **GS2**, enter an alphanumeric value for the application sender with a minimum of two characters and a maximum of 15 characters.</span></span> <span data-ttu-id="7a041-127">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-127">This is a required field.</span></span>  
  
    -   <span data-ttu-id="7a041-128">如**GS3**，輸入最少 2 個字元，最多 15 個字元的應用程式接收者的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="7a041-128">For **GS3**, enter an alphanumeric value for the application receiver with a minimum of two characters and a maximum of 15 characters.</span></span> <span data-ttu-id="7a041-129">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-129">This is a required field.</span></span>  
  
    -   <span data-ttu-id="7a041-130">如**GS4**，選取**CCYYMMDD**或**YYMMDD**。</span><span class="sxs-lookup"><span data-stu-id="7a041-130">For **GS4**, select **CCYYMMDD** or **YYMMDD**.</span></span> <span data-ttu-id="7a041-131">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-131">This is an optional field</span></span>  
  
    -   <span data-ttu-id="7a041-132">如**GS5**，選取**HHMM**， **HHMMSS**，或 **[hhmmssdd]**。</span><span class="sxs-lookup"><span data-stu-id="7a041-132">For **GS5**, select **HHMM**, **HHMMSS**, or **HHMMSSdd**.</span></span> <span data-ttu-id="7a041-133">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-133">This is an optional field</span></span>  
  
    -   <span data-ttu-id="7a041-134">如**GS7**，從下拉式清單中選取負責單位的值。</span><span class="sxs-lookup"><span data-stu-id="7a041-134">For **GS7**, select a value for the responsible agency from the drop-down list.</span></span> <span data-ttu-id="7a041-135">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-135">This is an optional field.</span></span>  
  
    -   <span data-ttu-id="7a041-136">如**GS8**，輸入最少一個字元，最多 12 個字元的識別文件的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="7a041-136">For **GS8**, enter an alphanumeric value for the document identified with a minimum of one character and a maximum of 12 characters.</span></span> <span data-ttu-id="7a041-137">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="7a041-137">This is an optional field.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7a041-138">這些會是 BizTalk Server 將在它本身正在建置如果交換的 GS 欄位中輸入的值**交易類型**，**版本/版次**，和**目標命名空間**相同的資料列中的項目都符合與交換關聯。</span><span class="sxs-lookup"><span data-stu-id="7a041-138">These will be the values that BizTalk Server will enter in the GS fields of the interchange it is building if the **Transaction Type**, **Version/Release**, and **Target namespace** elements in the same row are a match for those associated with the interchange.</span></span>  
  
5.  <span data-ttu-id="7a041-139">重複步驟 3 和 4 方格中輸入額外的資料列。</span><span class="sxs-lookup"><span data-stu-id="7a041-139">Repeat steps 3 and 4 to enter additional rows into the grid.</span></span>  
  
6.  <span data-ttu-id="7a041-140">在方格中的一個資料列，按一下 **預設**將它指定為預設資料列。</span><span class="sxs-lookup"><span data-stu-id="7a041-140">For one row in the grid, click **Default** to designate it as the default row.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a041-141">如果訊息沒有相符項目與**交易類型**，**版本/版次**，和**目標命名空間**任何資料列，BizTalk Server 中的項目將會填入訊息值與**GS1**， **GS2**， **GS3**， **GS5**， **GS7**，和**GS8**預設列中的項目。</span><span class="sxs-lookup"><span data-stu-id="7a041-141">If a message does not have a match with the **Transaction Type**, **Version/Release**, and **Target namespace** elements in any row, BizTalk Server will populate the message with the values for the **GS1**, **GS2**, **GS3**, **GS5**, **GS7**, and **GS8** elements in the default row.</span></span> <span data-ttu-id="7a041-142">即使訊息沒有具有相符項目，就會使用這些值**交易類型**，**版本/版次**，和**目標命名空間**與預設列的項目。</span><span class="sxs-lookup"><span data-stu-id="7a041-142">These values will be used even if the message does not have a match with the **Transaction Type**, **Version/Release**, and **Target namespace** elements of the default row.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a041-143">如果沒有預設值是已選取，內送文件不符合**交易類型**，**版本/版次**，和**目標命名空間**的任何資料列的項目將會遭到擱置.</span><span class="sxs-lookup"><span data-stu-id="7a041-143">If no default is selected, incoming documents that do not match the **Transaction Type**, **Version/Release**, and **Target namespace** elements of any rows will be suspended.</span></span>  
  
7.  <span data-ttu-id="7a041-144">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a041-144">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a041-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a041-145">See Also</span></span>  
 [<span data-ttu-id="7a041-146">設定交易集設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="7a041-146">Configuring Transaction Set Settings (X12)</span></span>](../core/configuring-transaction-set-settings-x12.md)