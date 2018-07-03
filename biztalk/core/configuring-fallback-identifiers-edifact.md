---
title: 設定後援識別碼 (EDIFACT) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2ce56c1-44f1-42dc-94e8-36e5ba664f53
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7db7e20f8ccb4db8da53483e7c33285f4b75afb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991983"
---
# <a name="configuring-fallback-identifiers-edifact"></a><span data-ttu-id="9570e-102">設定後援識別項 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="9570e-102">Configuring Fallback Identifiers (EDIFACT)</span></span>
<span data-ttu-id="9570e-103">在後援協議中，您必須設定收件者參考密碼，才可以確認交換的接收者不會是未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="9570e-103">In the fallback agreement, you must set the recipient reference password, in order to verify that the interchange is not being received by unauthorized recipients.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9570e-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="9570e-104">Prerequisites</span></span>  
 <span data-ttu-id="9570e-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="9570e-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-the-sender-recipient-recipient-password"></a><span data-ttu-id="9570e-106">若要設定傳送者、接收者、接收者密碼</span><span class="sxs-lookup"><span data-stu-id="9570e-106">To set the sender, recipient, recipient password</span></span>  
  
1. <span data-ttu-id="9570e-107">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="9570e-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2. <span data-ttu-id="9570e-108">在  **EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤之下**交換設定**區段中，按一下**識別碼**.</span><span class="sxs-lookup"><span data-stu-id="9570e-108">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Identifiers**.</span></span>  
  
3. <span data-ttu-id="9570e-109">在 **寄件者 (UNB2)** 區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9570e-109">In the **Sender (UNB2)** section, do the following:</span></span>  
  
   1.  <span data-ttu-id="9570e-110">針對**識別 (UNB2.1)**，輸入最少 1 個，最多 35 個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-110">For **Identification (UNB2.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35.</span></span> <span data-ttu-id="9570e-111">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-111">This is a required field.</span></span>  
  
   2.  <span data-ttu-id="9570e-112">針對**代碼辨識符號 (UNB2.2)**，從下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="9570e-112">For **Code qualifier (UNB2.2)**, select a value from the drop-down list.</span></span> <span data-ttu-id="9570e-113">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-113">This is an optional field.</span></span>  
  
   3.  <span data-ttu-id="9570e-114">針對**反向路由位址 (UNB2.3)**，輸入最少一個字元，最多 14 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-114">For **Reverse routing address (UNB2.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="9570e-115">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-115">This is an optional field.</span></span>  
  
   4.  <span data-ttu-id="9570e-116">針對**應用程式參考識別碼 (UNB7)**，輸入最少一個字元，最多 6 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-116">For **Application reference ID (UNB7)**, enter an alphanumeric value with a minimum of one character and a maximum of six characters.</span></span> <span data-ttu-id="9570e-117">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-117">This is a required field.</span></span>  
  
4. <span data-ttu-id="9570e-118">在 **收件者 (UNB3)** 區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9570e-118">In the **Recipient (UNB3)** section, do the following:</span></span>  
  
   1.  <span data-ttu-id="9570e-119">針對**識別 (UNB3.1)**，輸入最少 1 個，最多 35 個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-119">For **Identification (UNB3.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35.</span></span> <span data-ttu-id="9570e-120">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-120">This is a required field.</span></span>  
  
   2.  <span data-ttu-id="9570e-121">針對**代碼辨識符號 (UNB3.2)**，從下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="9570e-121">For **Code qualifier (UNB3.2)**, select a value from the drop-down list.</span></span> <span data-ttu-id="9570e-122">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-122">This is an optional field.</span></span>  
  
   3.  <span data-ttu-id="9570e-123">針對**反向路由位址 (UNB3.3)(&AMP;S)**，輸入最少一個字元，最多 14 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-123">For **Reverse routing address (UNB3.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="9570e-124">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-124">This is an optional field.</span></span>  
  
   4.  <span data-ttu-id="9570e-125">如有需要，在**收件者參考密碼 (UNB6)** 區段中，輸入收件者參考密碼的值。</span><span class="sxs-lookup"><span data-stu-id="9570e-125">If required, in the **Recipient reference password (UNB6)** section, enter values for the recipient reference password.</span></span> <span data-ttu-id="9570e-126">針對**值 (UNB6.1)**，輸入最少 1 個，最多 14 個的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-126">For **Value (UNB6.1)**, enter an alphanumeric value with a minimum of one and a maximum of 14.</span></span> <span data-ttu-id="9570e-127">針對**辨識符號 (UNB6.2)**，輸入最少一個字元，最多 2 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="9570e-127">For **Qualifier (UNB6.2)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters.</span></span> <span data-ttu-id="9570e-128">這些是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-128">These are optional fields.</span></span> <span data-ttu-id="9570e-129">如果這些值與所接收交換中的 UNB6.1 和 UNB6.2 欄位值不相符，BizTalk Server 將會擱置該項交換。</span><span class="sxs-lookup"><span data-stu-id="9570e-129">If these values do not match the UNB6.1 and UNB6.2 fields in a received interchange, BizTalk Server will suspend the interchange.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="9570e-130">組合**UNB6.1**並**UNB6.2**必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9570e-130">The combination of **UNB6.1** and **UNB6.2** must be unique.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="9570e-131">如果同時輸入 UNB6.1 及 UNB6.2 的值並套用變更，然後又清空 UNB6.1，則也會刪除 UNB6.2 中的值，並且停用該欄位。</span><span class="sxs-lookup"><span data-stu-id="9570e-131">If you enter values for both UNB6.1 and UNB6.2, apply the changes and then blank out UNB6.1, the value in UNB6.2 will also be deleted and the field will be disabled.</span></span>  
  
5. <span data-ttu-id="9570e-132">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9570e-132">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9570e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9570e-133">See Also</span></span>  
 [<span data-ttu-id="9570e-134">設定交換處理的 EDIFACT 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="9570e-134">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)