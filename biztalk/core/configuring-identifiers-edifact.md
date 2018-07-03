---
title: 設定識別碼 (EDIFACT) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 097292f2-1aa5-42e4-aeee-c7d4cbdae17c
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c50743c237c66edcba1e6609dcd1ab9cb0081bc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997215"
---
# <a name="configuring-identifiers-edifact"></a><span data-ttu-id="fe3b5-102">設定識別項 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="fe3b5-102">Configuring Identifiers (EDIFACT)</span></span>
<span data-ttu-id="fe3b5-103">在此夥伴協議中，您必須設定收件者參考密碼，才可以確認該交換的接收者不會是未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-103">In the partner agreement, you must set the recipient reference password, in order to verify that the interchange is not being received by unauthorized recipients.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fe3b5-104">下列屬性會停用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-104">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
> 
> - <span data-ttu-id="fe3b5-105">**DestinationPartyName**底下**額外的協議解析程式**一節。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-105">**DestinationPartyName** under **Additional Agreement Resolvers** section.</span></span>  
> 
>   <span data-ttu-id="fe3b5-106">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-106">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="fe3b5-107">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-107">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe3b5-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="fe3b5-108">Prerequisites</span></span>  
 <span data-ttu-id="fe3b5-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-the-sender-recipient-and-recipient-password"></a><span data-ttu-id="fe3b5-110">若要設定傳送者、接收者和接收者密碼</span><span class="sxs-lookup"><span data-stu-id="fe3b5-110">To set the sender, recipient, and recipient password</span></span>  
  
1.  <span data-ttu-id="fe3b5-111">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-111">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="fe3b5-112">若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-112">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="fe3b5-113">在單向協議索引標籤底下**交換設定**區段中，按一下**識別碼**。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-113">On a one-way agreement tab, under **Interchange Settings** section, click **Identifiers**.</span></span>  
  
3.  <span data-ttu-id="fe3b5-114">在 **寄件者 (UNB2)** 區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fe3b5-114">In the **Sender (UNB2)** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="fe3b5-115">針對**識別 (UNB2.1)**，輸入最少 1 個，最多 35 個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-115">For **Identification (UNB2.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35.</span></span> <span data-ttu-id="fe3b5-116">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-116">This is a required field.</span></span>  
  
    2.  <span data-ttu-id="fe3b5-117">針對**代碼辨識符號 (UNB2.2)**，從下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-117">For **Code qualifier (UNB2.2)**, select a value from the drop-down list.</span></span> <span data-ttu-id="fe3b5-118">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-118">This is an optional field.</span></span>  
  
    3.  <span data-ttu-id="fe3b5-119">針對**反向路由位址 (UNB2.3)**，輸入最少一個字元，最多 14 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-119">For **Reverse routing address (UNB2.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="fe3b5-120">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-120">This is an optional field.</span></span>  
  
4.  <span data-ttu-id="fe3b5-121">在 **收件者 (UNB3)** 區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fe3b5-121">In the **Recipient (UNB3)** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="fe3b5-122">針對**識別 (UNB3.1)**，輸入最少 1 個，最多 35 個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-122">For **Identification (UNB3.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35.</span></span> <span data-ttu-id="fe3b5-123">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-123">This is a required field.</span></span>  
  
    2.  <span data-ttu-id="fe3b5-124">針對**代碼辨識符號 (UNB3.2)**，從下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-124">For **Code qualifier (UNB3.2)**, select a value from the drop-down list.</span></span> <span data-ttu-id="fe3b5-125">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-125">This is an optional field.</span></span>  
  
    3.  <span data-ttu-id="fe3b5-126">針對**反向路由位址 (UNB3.3)(&AMP;S)**，輸入最少一個字元，最多 14 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-126">For **Reverse routing address (UNB3.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="fe3b5-127">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-127">This is an optional field.</span></span>  
  
    4.  <span data-ttu-id="fe3b5-128">如有需要，在**收件者參考密碼 (UNB6)** 區段中，輸入收件者參考密碼的值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-128">If required, in the **Recipient reference password (UNB6)** section, enter values for the recipient reference password.</span></span> <span data-ttu-id="fe3b5-129">針對**值 (UNB6.1)**，輸入最少 1 個，最多 14 個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-129">For **Value (UNB6.1)**, enter an alphanumeric value with a minimum of one and a maximum of 14.</span></span> <span data-ttu-id="fe3b5-130">針對**辨識符號 (UNB6.2)**，輸入最少一個字元，最多 2 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-130">For **Qualifier (UNB6.2)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters.</span></span> <span data-ttu-id="fe3b5-131">這些是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-131">These are optional fields.</span></span> <span data-ttu-id="fe3b5-132">如果這些值與所接收交換中的 UNB6.1 和 UNB6.2 欄位值不相符，BizTalk Server 將會擱置該項交換。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-132">If these values do not match the UNB6.1 and UNB6.2 fields in a received interchange, BizTalk Server will suspend the interchange.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="fe3b5-133">組合**UNB6.1**並**UNB6.2**必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-133">The combination of **UNB6.1** and **UNB6.2** must be unique.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="fe3b5-134">如果同時輸入 UNB6.1 及 UNB6.2 的值並套用變更，然後又清空 UNB6.1，則也會刪除 UNB6.2 中的值，並且停用該欄位。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-134">If you enter values for both UNB6.1 and UNB6.2, apply the changes and then blank out UNB6.1, the value in UNB6.2 will also be deleted and the field will be disabled.</span></span>  
  
5.  <span data-ttu-id="fe3b5-135">在**其他的協議解析程式**區段中，如**DestinationPartyName**屬性，指定目的合作對象的值。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-135">In the **Additional Agreement Resolvers** section, for **DestinationPartyName** property, specify a value for the destination party.</span></span> <span data-ttu-id="fe3b5-136">此值也用來將外寄訊息解析為協議。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-136">This value is also used to resolve outbound messages to an agreement.</span></span> <span data-ttu-id="fe3b5-137">如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-137">For more information see, [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fe3b5-138">您通常不需要設定**DestinationPartyName**屬性。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-138">You typically do not need to set the **DestinationPartyName** property.</span></span> <span data-ttu-id="fe3b5-139">此屬性是協議屬性的一部分，用來支援升級案例。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-139">This property is available as part of the agreement properties to support upgrade scenarios.</span></span> <span data-ttu-id="fe3b5-140">從 BizTalk Server 2006 R2 或 BizTalk Server 2009 中，升級**DestinationPartyName**屬性設定為在 BizTalk Server 2006 R2 或 BizTalk Server 2009 中的合作對象的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-140">When upgrading from BizTalk Server 2006 R2 or BizTalk Server 2009, the **DestinationPartyName** property is set to the name of the party in BizTalk Server 2006 R2 or BizTalk Server 2009.</span></span>  
  
6.  <span data-ttu-id="fe3b5-141">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-141">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="fe3b5-142">如果您按一下 **[確定]** 或是**套用**在這個階段，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-142">If you click **OK** or **Apply** at this stage, you will get an error.</span></span> <span data-ttu-id="fe3b5-143">這是因為您仍然需要在上提供 UNB2 與 UNB3 值**識別碼**其他單向協議索引標籤的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fe3b5-143">That is because you still need to provide UNB2 and UNB3 values on the **Identifiers** tab for the other one-way agreement tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3b5-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe3b5-144">See Also</span></span>  
 [<span data-ttu-id="fe3b5-145">設定交換設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="fe3b5-145">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)