---
title: "設定本機主機設定 （EDIFACT 交易集設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f7c9cb9-7b4b-41de-a3f3-c0519b18673c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 912af3a047f77f077bf9de58a25802f3c658e6b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-edifact-transaction-set-settings"></a><span data-ttu-id="a652c-102">設定本機主機設定 (EDIFACT 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="a652c-102">Configuring Local Host Settings (EDIFACT-Transaction Set Settings)</span></span>
<span data-ttu-id="a652c-103">為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a652c-103">To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange.</span></span> <span data-ttu-id="a652c-104">這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a652c-104">This consists of determining the target namespace associated with the schema, and determining the schema to be used.</span></span> <span data-ttu-id="a652c-105">您要在這頁合作對象協議中，輸入要用來判斷上述目標命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="a652c-105">In this page of the party agreement, you enter the properties to be used in determining the target namespace.</span></span> <span data-ttu-id="a652c-106">BizTalk Server 如何判斷結構描述中描述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="a652c-106">How BizTalk Server determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a652c-107">任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="a652c-107">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a652c-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="a652c-108">Prerequisites</span></span>  
 <span data-ttu-id="a652c-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="a652c-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="determining-the-target-namespace"></a><span data-ttu-id="a652c-110">判斷目標命名空間</span><span class="sxs-lookup"><span data-stu-id="a652c-110">Determining the Target Namespace</span></span>  
 <span data-ttu-id="a652c-111">在**自訂目標命名空間**方格中，您可以設定目標命名空間為其中一個隨附於 Microsoft 的標準結構描述命名空間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a652c-111">In the **Customize Target Namespace** grid, you can set the target namespace to one of the namespaces for the standard schemas shipped with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="a652c-112">在方格中，您將建立關聯的值**目標命名空間**項目的值**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**， **UNG2.1**，和**UNG2.2**項目。</span><span class="sxs-lookup"><span data-stu-id="a652c-112">In the grid, you associate a value of the **Target Namespace** element with values of the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, and **UNG2.2** elements.</span></span> <span data-ttu-id="a652c-113">當 BizTalk 收到之訊息的**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**， **UNG2.1**，和**UNG2.2**項目符合格線的某列中，BizTalk 會使用對應的命名空間，以判斷它會使用它來處理訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a652c-113">When BizTalk receives a message whose **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, and **UNG2.2** elements match those in a row of the grid, BizTalk will use the corresponding namespace to determine the schema that it will use to process the message.</span></span> <span data-ttu-id="a652c-114">您輸入的項目值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a652c-114">The values of the elements that you enter must be unique.</span></span>  
  
 <span data-ttu-id="a652c-115">如果訊息沒有相符項目與**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**， **UNG2.1**，和**UNG2.2**方格中，BizTalk Server 的任何資料列中的項目會處理訊息的資料列中使用命名空間的**預設**會檢查資料行。</span><span class="sxs-lookup"><span data-stu-id="a652c-115">If a message does not have a match with the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, and **UNG2.2** elements in any row of the grid, BizTalk Server will process the message using the namespace in the row for which the **Default** column is checked.</span></span> <span data-ttu-id="a652c-116">該命名空間即會做為預設的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="a652c-116">That serves as the default target namespace.</span></span> <span data-ttu-id="a652c-117">如果找不到任何命名空間，BizTalk 就會使用 `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006` 的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="a652c-117">If no namespace is identified, BizTalk will use the default namespace of `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a652c-118">如果您為格線中的任何欄位輸入設定，然後又要刪除該設定，那麼就必須刪除一整列，否則該頁面將不會讓您通過驗證。</span><span class="sxs-lookup"><span data-stu-id="a652c-118">If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.</span></span>  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a><span data-ttu-id="a652c-119">若要設定交易集的本機主機設定</span><span class="sxs-lookup"><span data-stu-id="a652c-119">To configure local host settings for transaction sets</span></span>  
  
1.  <span data-ttu-id="a652c-120">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="a652c-120">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="a652c-121">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a652c-121">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a652c-122">在單向協議索引標籤底下**交易集設定**區段中，按一下**本機主機設定**。</span><span class="sxs-lookup"><span data-stu-id="a652c-122">On a one-way agreement tab, under **Transaction Set Settings** section, click **Local Host Settings**.</span></span>  
  
3.  <span data-ttu-id="a652c-123">當交易的一部分設定驗證設定，如果您設定**尾端分隔符號原則**至**選擇性**或**強制**，您可以選取**建立空白針對尾端分隔符號的 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="a652c-123">As part of the transaction set validation settings, if you set **Trailing Separator Policy** to **Optional** or **Mandatory**, you can select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.</span></span>  
  
4.  <span data-ttu-id="a652c-124">選取**使用點 （.） 做為小數分隔符號**BizTalk Server 以啟用含小數的交換建立 XML 訊息中包含點 （.）。</span><span class="sxs-lookup"><span data-stu-id="a652c-124">Select **Use Dot (.) as decimal separator** to enable BizTalk Server include a dot (.) in the XML message created out of an interchange that contains a decimal number.</span></span>  
  
5.  <span data-ttu-id="a652c-125">在**自訂目標命名空間**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a652c-125">In the **Customize Target Namespace** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="a652c-126">選取**預設**包含您想要定義的預設目標命名空間的資料列的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a652c-126">Select the **Default** check box for the row that contains the default target namespace that you want to define.</span></span>  
  
    2.  <span data-ttu-id="a652c-127">在**UNH2.1**資料行中，指定訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a652c-127">In the **UNH2.1** column, specify the message type.</span></span> <span data-ttu-id="a652c-128">(最多 6 個字元)。</span><span class="sxs-lookup"><span data-stu-id="a652c-128">(maximum, six characters).</span></span>  
  
    3.  <span data-ttu-id="a652c-129">在**UNH2.2**資料行中，指定訊息版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a652c-129">In the **UNH2.2**  column, specify the message version number.</span></span> <span data-ttu-id="a652c-130">(最少 1 個字元，最多 3 個字元)。</span><span class="sxs-lookup"><span data-stu-id="a652c-130">(minimum, one character; maximum, three characters).</span></span>  
  
    4.  <span data-ttu-id="a652c-131">在**UNH2.3**資料行中，指定訊息版次號碼。</span><span class="sxs-lookup"><span data-stu-id="a652c-131">In the **UNH2.3** column, specify the message release number.</span></span> <span data-ttu-id="a652c-132">(最少 1 個字元，最多 3 個字元)。</span><span class="sxs-lookup"><span data-stu-id="a652c-132">(minimum, one character; maximum, three characters).</span></span>  
  
    5.  <span data-ttu-id="a652c-133">在**UNH2.5**資料行中，指定指派的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a652c-133">In the **UNH2.5** column, specify the assigned code.</span></span> <span data-ttu-id="a652c-134">(最多 6 個字元，</span><span class="sxs-lookup"><span data-stu-id="a652c-134">(maximum, six characters.</span></span> <span data-ttu-id="a652c-135">必須是英數字元)。</span><span class="sxs-lookup"><span data-stu-id="a652c-135">Must be alphanumeric).</span></span>  
  
    6.  <span data-ttu-id="a652c-136">在**UNG2.1**資料行中，輸入應用程式傳送者識別最少一個字元和最多 35 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="a652c-136">In the **UNG2.1** column, enter an alphanumeric value for the application sender identification with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="a652c-137">這是必要欄位。</span><span class="sxs-lookup"><span data-stu-id="a652c-137">This field is required.</span></span>  
  
    7.  <span data-ttu-id="a652c-138">在**UNG2.2**資料行中，輸入最少一個字元，最多四個字元的應用程式傳送者代碼辨識符號的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="a652c-138">In the **UNG2.2** column, enter an alphanumeric value for the application sender code qualifier with a minimum of one character and a maximum of four characters.</span></span> <span data-ttu-id="a652c-139">此為選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="a652c-139">This field is optional.</span></span>  
  
    8.  <span data-ttu-id="a652c-140">在**目標命名空間**資料行，從下拉式清單中選取或輸入要在格線的任何資料列中的資料項目與交換中的欄位之間不相符時用於交換的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="a652c-140">In the **Target Namespace** column, select from the drop-down list or enter the target namespace to be used for an interchange when no match is found between the data elements in any row of the grid and the fields in the interchange.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a652c-141">這些將是 BizTalk Server 用來與所接收交換之相關值進行比較的值。</span><span class="sxs-lookup"><span data-stu-id="a652c-141">These will be the values that BizTalk Server will compare with the values associated with the interchange it received.</span></span>  
  
    9. <span data-ttu-id="a652c-142">針對其他任何要使用的目標命名空間 重複這些步驟 。</span><span class="sxs-lookup"><span data-stu-id="a652c-142">Repeat these steps for any other target namespaces to be used.</span></span>  
  
    10. <span data-ttu-id="a652c-143">若要從清單中移除目標命名空間，請在選取的資料列，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="a652c-143">To remove a target namespace from the list, select the row and click **Delete**.</span></span>  
  
6.  <span data-ttu-id="a652c-144">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a652c-144">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a652c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a652c-145">See Also</span></span>  
 [<span data-ttu-id="a652c-146">設定交易集設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="a652c-146">Configuring Transaction Set Settings (EDIFACT)</span></span>](../core/configuring-transaction-set-settings-edifact.md)