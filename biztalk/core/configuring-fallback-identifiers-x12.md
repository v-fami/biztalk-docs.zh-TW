---
title: 設定後援識別碼 (X12) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cb5b32c-96ec-4192-9a10-6668a2cb1195
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58909783b30a0bce855fc56316f687aa9dbc918c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233526"
---
# <a name="configuring-fallback-identifiers-x12"></a><span data-ttu-id="81a97-102">設定後援識別碼 (X12)</span><span class="sxs-lookup"><span data-stu-id="81a97-102">Configuring Fallback Identifiers (X12)</span></span>
<span data-ttu-id="81a97-103">在此後援協議中，您必須設定 X12 授權和安全性等屬性，才可以確認該交換的接收者不會是未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="81a97-103">In the fallback agreement, you must set the X12 authorization and security properties in order to verify that the interchange is not being received by unauthorized recipients.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81a97-104">此處所述的交換處理屬性也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="81a97-104">The interchange processing properties described here apply also to HIPAA interchanges.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="81a97-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="81a97-105">Prerequisites</span></span>  
 <span data-ttu-id="81a97-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="81a97-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-sender-receiver-and-security-properties"></a><span data-ttu-id="81a97-107">設定傳送者、接收者和安全性等屬性</span><span class="sxs-lookup"><span data-stu-id="81a97-107">To set sender, receiver, and security properties</span></span>  
  
1.  <span data-ttu-id="81a97-108">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="81a97-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="81a97-109">在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交換設定**區段中，按一下**的識別項**.</span><span class="sxs-lookup"><span data-stu-id="81a97-109">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Identifiers**.</span></span>  
  
3.  <span data-ttu-id="81a97-110">輸入的值**ISA1-2 （授權辨識符號和資訊）**。</span><span class="sxs-lookup"><span data-stu-id="81a97-110">Enter values for the **ISA1-2 (Authorization qualifier and information)**.</span></span> <span data-ttu-id="81a97-111">選取的值**授權辨識符號 (ISA1)** 從相關聯的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="81a97-111">Select the value for the **Authorization qualifier (ISA1)** from the associated drop-down list.</span></span> <span data-ttu-id="81a97-112">如果此值不是**00**，如**值 (ISA2)** 文字方塊中，輸入最少一個英數字元，最多 10 個。</span><span class="sxs-lookup"><span data-stu-id="81a97-112">If this value is other than **00**, for the **Value (ISA2)** text box, enter a minimum of one alphanumeric character and a maximum of 10.</span></span> <span data-ttu-id="81a97-113">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="81a97-113">This is an optional field.</span></span> <span data-ttu-id="81a97-114">如果您指定這些值，請確定它們和已接收交換中的 ISA1 與 ISA2 欄位相符，否則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會擱置交換。</span><span class="sxs-lookup"><span data-stu-id="81a97-114">If you do specify these values, make sure they match the ISA1 and ISA2 fields in a received interchange otherwise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.</span></span>  
  
4.  <span data-ttu-id="81a97-115">輸入的值**ISA3-4 （安全性辨識符號和資訊）**。</span><span class="sxs-lookup"><span data-stu-id="81a97-115">Enter values for the **ISA3-4 (Security qualifier and information)**.</span></span> <span data-ttu-id="81a97-116">選取的值**安全性辨識符號 (ISA3)** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="81a97-116">Select the value for the **Security qualifier (ISA3)** from the drop-down list.</span></span> <span data-ttu-id="81a97-117">如果此值不是**00**，如**值 (ISA4)** 文字方塊中，輸入最少一個英數值，最多 10 個。</span><span class="sxs-lookup"><span data-stu-id="81a97-117">If this value is other than **00**, for the **Value (ISA4)** text box, enter a minimum of one alphanumeric value and a maximum of 10.</span></span> <span data-ttu-id="81a97-118">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="81a97-118">This is an optional field.</span></span> <span data-ttu-id="81a97-119">如果這些值與所接收交換中的 ISA3 和 ISA4 欄位值不相符，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會擱置交換。</span><span class="sxs-lookup"><span data-stu-id="81a97-119">If these values do not match the ISA3 and ISA4 fields in a received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81a97-120">值**03-密碼 （用於回溯相容性）**，是為了回溯相容性的[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]將在未來版本中移除。</span><span class="sxs-lookup"><span data-stu-id="81a97-120">The value **03 – Password (for backward compatibility)**, is included for backward compatibility with [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and will be removed in future versions.</span></span>  
  
5.  <span data-ttu-id="81a97-121">輸入的值**ISA5-6 （傳送者辨識符號和識別項）**。</span><span class="sxs-lookup"><span data-stu-id="81a97-121">Enter the values for **ISA5-6 (Sender qualifier and identifier)**.</span></span> <span data-ttu-id="81a97-122">選取從辨識符號的值**寄件者識別碼辨識符號 (ISA5)** 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="81a97-122">Select a value for the qualifier from the **Sender Id Qualifier (ISA5)** drop-down list.</span></span> <span data-ttu-id="81a97-123">針對該識別碼，在**值 (ISA6)** 文字方塊中，輸入最少一個英數字元，最多 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="81a97-123">For the identifier, in the **Value (ISA6)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.</span></span>  
  
6.  <span data-ttu-id="81a97-124">輸入的值**ISA7-8 （接收者辨識符號和識別項）**。</span><span class="sxs-lookup"><span data-stu-id="81a97-124">Enter the values for **ISA7-8 (Receiver qualifier and identifier)**.</span></span> <span data-ttu-id="81a97-125">選取從辨識符號的值**接收者識別碼辨識符號 (ISA7)** 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="81a97-125">Select a value for the qualifier from the **Receiver Id Qualifier (ISA7)** drop-down list.</span></span> <span data-ttu-id="81a97-126">針對該識別碼，在**值 (ISA8)** 文字方塊中，輸入最少一個英數字元，最多 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="81a97-126">For the identifier, in the **Value (ISA8)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.</span></span>  
  
7.  <span data-ttu-id="81a97-127">按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="81a97-127">Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a97-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81a97-128">See Also</span></span>  
 [<span data-ttu-id="81a97-129">設定 X12 後援協議屬性的交換處理</span><span class="sxs-lookup"><span data-stu-id="81a97-129">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)