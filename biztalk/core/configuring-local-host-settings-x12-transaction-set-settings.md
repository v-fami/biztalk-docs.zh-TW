---
title: "設定本機主機設定 （X12-交易集設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31b41c3-49fc-46ef-ab69-889e30dfc58e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fcc099535e6a7b96c5c4bbdd29112da46af3522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-x12-transaction-set-settings"></a><span data-ttu-id="a52ef-102">設定本機主機設定 (X12 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="a52ef-102">Configuring Local Host Settings (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="a52ef-103">為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a52ef-103">To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange.</span></span> <span data-ttu-id="a52ef-104">這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a52ef-104">This consists of determining the target namespace associated with the schema, and determining the schema to be used.</span></span> <span data-ttu-id="a52ef-105">您要在這頁合作對象協議中，輸入要用來判斷上述目標命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="a52ef-105">In this page of the party agreement, you enter the properties to be used in determining the target namespace.</span></span> <span data-ttu-id="a52ef-106">如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]判斷結構描述所述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="a52ef-106">How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a52ef-107">這個主題也適用於 HIPAA 相關設定。</span><span class="sxs-lookup"><span data-stu-id="a52ef-107">This topic applies also to HIPAA-related settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a52ef-108">任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="a52ef-108">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a52ef-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="a52ef-109">Prerequisites</span></span>  
 <span data-ttu-id="a52ef-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="a52ef-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="determining-the-target-namespace"></a><span data-ttu-id="a52ef-111">判斷目標命名空間</span><span class="sxs-lookup"><span data-stu-id="a52ef-111">Determining the Target Namespace</span></span>  
 <span data-ttu-id="a52ef-112">在**自訂目標命名空間**方格中，您可以將目標命名空間設其中一個命名空間的標準結構描述隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a52ef-112">In the **Customize Target namespace** grid, you can set the target namespaces to one of the namespaces for the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="a52ef-113">在方格中，您將建立關聯的值**目標命名空間**項目的值應用程式傳送者 (**GS2**) 和交易集識別項代碼 (**ST1**)。</span><span class="sxs-lookup"><span data-stu-id="a52ef-113">In the grid, you associate a value of the **Target Namespace** element with values of the application sender (**GS2**) and transaction set identifier code (**ST1**).</span></span> <span data-ttu-id="a52ef-114">當 BizTalk 收到之訊息的**GS2**和**ST1**資料項目符合方格的資料列中，BizTalk 會使用對應的命名空間來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="a52ef-114">When BizTalk receives a message whose **GS2** and **ST1** data elements match those in a row of the grid, BizTalk will use the corresponding namespace to process the message.</span></span> <span data-ttu-id="a52ef-115">您輸入的項目值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a52ef-115">The values of the elements that you enter must be unique.</span></span>  
  
 <span data-ttu-id="a52ef-116">如果訊息沒有相符項目與**GS2**和**ST1**資料方格中，BizTalk Server 的任何資料列中的項目會處理訊息的資料列中使用命名空間的**預設**會檢查資料行。</span><span class="sxs-lookup"><span data-stu-id="a52ef-116">If a message does not have a match with the **GS2** and **ST1** data elements in any row of the grid, BizTalk Server will process the message using the namespace in the row for which the **Default** column is checked.</span></span> <span data-ttu-id="a52ef-117">該命名空間即會做為預設的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="a52ef-117">That serves as the default target namespace.</span></span> <span data-ttu-id="a52ef-118">如果找不到任何命名空間，BizTalk Server 就會使用 `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006` 的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="a52ef-118">If no namespace is identified, BizTalk Server will use the default namespace of `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a52ef-119">如果您為格線中的任何欄位輸入設定，然後又要刪除該設定，那麼就必須刪除一整列，否則該頁面將不會讓您通過驗證。</span><span class="sxs-lookup"><span data-stu-id="a52ef-119">If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a52ef-120">如需這個方格的使用示範，請完整執行 EDI 介面開發人員教學課程，並特別注意設定要交換接收來源的合作對象。</span><span class="sxs-lookup"><span data-stu-id="a52ef-120">For an illustration of using this grid, run through the EDI Interface Developer tutorial, specifically setting up a party to receive an interchange from.</span></span> <span data-ttu-id="a52ef-121">如需詳細資訊，請參閱[步驟 4： 為您的交易夥伴設定合作對象與商務設定檔](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)。</span><span class="sxs-lookup"><span data-stu-id="a52ef-121">For more information, see [Step 4: Configure a Party and Business Profile for Your Trading Partner](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md).</span></span>  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a><span data-ttu-id="a52ef-122">若要設定交易集的本機主機設定</span><span class="sxs-lookup"><span data-stu-id="a52ef-122">To configure local host settings for transaction sets</span></span>  
  
1.  <span data-ttu-id="a52ef-123">建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="a52ef-123">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="a52ef-124">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a52ef-124">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a52ef-125">在單向協議索引標籤底下**交易集設定**區段中，按一下**本機主機設定**。</span><span class="sxs-lookup"><span data-stu-id="a52ef-125">On a one-way agreement tab, under **Transaction Set Settings** section, click **Local Host Settings**.</span></span>  
  
3.  <span data-ttu-id="a52ef-126">選取**轉換隱含的小數格式 Nn 10 進制數值**来轉換成 BizTalk Server 中的中繼 XML 中的基底 10 數值將格式 Nn 指定的 EDI 數字。</span><span class="sxs-lookup"><span data-stu-id="a52ef-126">Select **Convert implied decimal format Nn to base 10 numeric value** to convert an EDI number that is specified with the format Nn into a base-10 numeric value in the intermediate XML in BizTalk Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a52ef-127">轉換後，中繼 XML 可能會在長度驗證時失敗。</span><span class="sxs-lookup"><span data-stu-id="a52ef-127">After this conversion, the intermediate XML may fail length validation.</span></span> <span data-ttu-id="a52ef-128">這是因為以 10 為基底的數值格式包含小數點，這使得它的長度比 Nn 格式數字大一。</span><span class="sxs-lookup"><span data-stu-id="a52ef-128">This occurs because the number in the base-10 numeric format includes a decimal, making its length one greater than the number in Nn format.</span></span> <span data-ttu-id="a52ef-129">您可以藉由新增的值來解決這個問題**1**最小/最大長度值。</span><span class="sxs-lookup"><span data-stu-id="a52ef-129">You can resolve this issue by adding a value of **1** to the minimum/maximum length value.</span></span>  
  
4.  <span data-ttu-id="a52ef-130">當交易的一部分設定驗證設定，如果您設定**尾端分隔符號原則**至**選擇性**或**強制**，您可以選取**建立空白針對尾端分隔符號的 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="a52ef-130">As part of the transaction set validation settings, if you set **Trailing Separator Policy** to **Optional** or **Mandatory**, you can select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.</span></span>  
  
5.  <span data-ttu-id="a52ef-131">在**自訂目標命名空間**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a52ef-131">In the **Customize Target Namespace** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="a52ef-132">選取**預設**包含您想要定義的預設目標命名空間的資料列的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a52ef-132">Select the **Default** check box for the row that contains the default target namespace that you want to define.</span></span>  
  
    2.  <span data-ttu-id="a52ef-133">在**針對 ST1**資料行中，選取一個值的交易集識別項代碼，從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a52ef-133">In the **For ST1** column, select a value for the Transaction set identifier code from the drop-down list.</span></span>  
  
    3.  <span data-ttu-id="a52ef-134">在**GS2**資料行中，輸入應用程式傳送者最少 2 個字元，最多 15 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="a52ef-134">In the **GS2** column, enter an alphanumeric value for the Application sender with a minimum of two characters and a maximum of 15 characters.</span></span> <span data-ttu-id="a52ef-135">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="a52ef-135">This is a required field.</span></span>  
  
    4.  <span data-ttu-id="a52ef-136">在**目標命名空間**資料行，從下拉式清單中選取或輸入要在格線的任何資料列中的資料項目與交換中的欄位之間不相符時用於交換的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="a52ef-136">In the **Target Namespace** column, select from the drop-down list or enter the target namespace to be used for an interchange when no match is found between the data elements in any row of the grid and the fields in the interchange.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a52ef-137">這些將是 BizTalk Server 用來與所接收交換之相關值進行比較的值。</span><span class="sxs-lookup"><span data-stu-id="a52ef-137">These will be the values that BizTalk Server will compare with the values associated with the interchange it received.</span></span>  
  
    5.  <span data-ttu-id="a52ef-138">針對其他任何要使用的目標命名空間 重複這些步驟 。</span><span class="sxs-lookup"><span data-stu-id="a52ef-138">Repeat these steps for any other target namespaces to be used.</span></span>  
  
    6.  <span data-ttu-id="a52ef-139">若要從清單中移除目標命名空間，請在選取的資料列，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="a52ef-139">To remove a target namespace from the list, select the row and click **Delete**.</span></span>  
  
6.  <span data-ttu-id="a52ef-140">按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a52ef-140">Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a52ef-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a52ef-141">See Also</span></span>  
 [<span data-ttu-id="a52ef-142">設定交易集設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="a52ef-142">Configuring Transaction Set Settings (X12)</span></span>](../core/configuring-transaction-set-settings-x12.md)