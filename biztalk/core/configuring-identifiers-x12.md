---
title: 設定識別項 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 665698d1-c46c-4149-9715-381b4966dd92
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc9b4b5a6b2632c797ff655899b118536dbdde4e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003079"
---
# <a name="configuring-identifiers-x12"></a><span data-ttu-id="3c0c3-102">設定識別項 (X12)</span><span class="sxs-lookup"><span data-stu-id="3c0c3-102">Configuring Identifiers (X12)</span></span>
<span data-ttu-id="3c0c3-103">在夥伴協議中，您必須設定 X12 驗證和安全性等屬性，才可以確認該交換的接收者不會是未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-103">In the partner agreement, you must set the X12 authorization and security properties in order to verify that the interchange is not being received by unauthorized recipients.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c0c3-104">此處所述的交換處理屬性也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-104">The interchange processing properties described here apply also to HIPAA interchanges.</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="3c0c3-105">下列屬性會停用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-105">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
> 
> - <span data-ttu-id="3c0c3-106">**DestinationPartyName**底下**額外的協議解析程式**一節。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-106">**DestinationPartyName** under **Additional Agreement Resolvers** section.</span></span>  
> 
>   <span data-ttu-id="3c0c3-107">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-107">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="3c0c3-108">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-108">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3c0c3-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="3c0c3-109">Prerequisites</span></span>  
 <span data-ttu-id="3c0c3-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-sender-receiver-and-security-properties"></a><span data-ttu-id="3c0c3-111">設定傳送者、接收者和安全性等屬性</span><span class="sxs-lookup"><span data-stu-id="3c0c3-111">To set sender, receiver, and security properties</span></span>  
  
1. <span data-ttu-id="3c0c3-112">建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-112">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="3c0c3-113">若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-113">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2. <span data-ttu-id="3c0c3-114">在單向協議索引標籤底下**交換設定**區段中，按一下**識別碼**。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-114">On a one-way agreement tab, under **Interchange Settings** section, click **Identifiers**.</span></span>  
  
3. <span data-ttu-id="3c0c3-115">輸入的值**ISA1 2 （授權辨識符號和資訊）**。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-115">Enter values for the **ISA1-2 (Authorization qualifier and information)**.</span></span> <span data-ttu-id="3c0c3-116">選取的值**授權辨識符號 (ISA1)** 從相關聯的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-116">Select the value for the **Authorization qualifier (ISA1)** from the associated drop-down list.</span></span> <span data-ttu-id="3c0c3-117">如果此值不是**00**，如**值 (ISA2)** 文字中，輸入最少一個英數字元，最多 10 個。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-117">If this value is other than **00**, for the **Value (ISA2)** text box, enter a minimum of one alphanumeric character and a maximum of 10.</span></span> <span data-ttu-id="3c0c3-118">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-118">This is an optional field.</span></span> <span data-ttu-id="3c0c3-119">如果您指定這些值，請確定它們和已接收交換中的 ISA1 與 ISA2 欄位相符，否則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會擱置交換。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-119">If you do specify these values, make sure they match the ISA1 and ISA2 fields in a received interchange otherwise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.</span></span>  
  
4. <span data-ttu-id="3c0c3-120">輸入的值**ISA3 4 （安全性辨識符號和資訊）**。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-120">Enter values for the **ISA3-4 (Security qualifier and information)**.</span></span> <span data-ttu-id="3c0c3-121">選取的值**安全性辨識符號 (ISA3)** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-121">Select the value for the **Security qualifier (ISA3)** from the drop-down list.</span></span> <span data-ttu-id="3c0c3-122">如果此值不是**00**，如**值 (ISA4)** 文字中，輸入最少一個英數值，最多 10 個。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-122">If this value is other than **00**, for the **Value (ISA4)** text box, enter a minimum of one alphanumeric value and a maximum of 10.</span></span> <span data-ttu-id="3c0c3-123">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-123">This is an optional field.</span></span> <span data-ttu-id="3c0c3-124">如果這些值與所接收交換中的 ISA3 和 ISA4 欄位值不相符，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會擱置交換。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-124">If these values do not match the ISA3 and ISA4 fields in a received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="3c0c3-125">該值**03-密碼 （用於回溯相容性）**，為了提供回溯相容性[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]，將在未來版本中移除。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-125">The value **03 – Password (for backward compatibility)**, is included for backward compatibility with [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and will be removed in future versions.</span></span>  
  
5. <span data-ttu-id="3c0c3-126">輸入的值**ISA5 6 （傳送者辨識符號和識別項）**。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-126">Enter the values for **ISA5-6 (Sender qualifier and identifier)**.</span></span> <span data-ttu-id="3c0c3-127">選取的值從限定詞**寄件者識別碼辨識符號 (ISA5)** 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-127">Select a value for the qualifier from the **Sender Id Qualifier (ISA5)** drop-down list.</span></span> <span data-ttu-id="3c0c3-128">針對該識別碼，在**值 (ISA6)** 文字中，輸入最少一個英數字元，最多 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-128">For the identifier, in the **Value (ISA6)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.</span></span>  
  
6. <span data-ttu-id="3c0c3-129">輸入的值**ISA7 8 （接收者辨識符號和識別項）**。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-129">Enter the values for **ISA7-8 (Receiver qualifier and identifier)**.</span></span> <span data-ttu-id="3c0c3-130">選取的值從限定詞**寄件者識別碼辨識符號 (ISA7)** 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-130">Select a value for the qualifier from the **Sender Id Qualifier (ISA7)** drop-down list.</span></span> <span data-ttu-id="3c0c3-131">針對該識別碼，在**值 (ISA8)** 文字中，輸入最少一個英數字元，最多 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-131">For the identifier, in the **Value (ISA8)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.</span></span>  
  
7. <span data-ttu-id="3c0c3-132">在**其他的協議解析程式**區段中，如**DestinationPartyName**屬性，指定目的合作對象的值。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-132">In the **Additional Agreement Resolvers** section, for **DestinationPartyName** property, specify a value for the destination party.</span></span> <span data-ttu-id="3c0c3-133">此值也用來將外寄訊息解析為協議。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-133">This value is also used to resolve outbound messages to an agreement.</span></span> <span data-ttu-id="3c0c3-134">如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-134">For more information see, [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="3c0c3-135">您通常不需要設定**DestinationPartyName**屬性。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-135">You typically do not need to set the **DestinationPartyName** property.</span></span> <span data-ttu-id="3c0c3-136">此屬性是協議屬性的一部分，用來支援升級案例。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-136">This property is available as part of the agreement properties to support upgrade scenarios.</span></span> <span data-ttu-id="3c0c3-137">從 BizTalk Server 2006 R2 或 BizTalk Server 2009 中，升級**DestinationPartyName**屬性設定為在 BizTalk Server 2006 R2 或 BizTalk Server 2009 中的合作對象的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-137">When upgrading from BizTalk Server 2006 R2 or BizTalk Server 2009, the **DestinationPartyName** property is set to the name of the party in BizTalk Server 2006 R2 or BizTalk Server 2009.</span></span>  
  
8. <span data-ttu-id="3c0c3-138">按一下 **套用**以接受變更，或按一下**確定**輸入並驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-138">Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="3c0c3-139">如果您按一下 **[確定]** 或是**套用**在這個階段，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-139">If you click **OK** or **Apply** at this stage, you will get an error.</span></span> <span data-ttu-id="3c0c3-140">這是因為您仍然需要提供 ISA5 到 ISA8 的值**識別碼**其他單向協議索引標籤的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3c0c3-140">That is because you still need to provide ISA5 to ISA8 values on the **Identifiers** tab for the other one-way agreement tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0c3-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c0c3-141">See Also</span></span>  
 [<span data-ttu-id="3c0c3-142">設定交換設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="3c0c3-142">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)