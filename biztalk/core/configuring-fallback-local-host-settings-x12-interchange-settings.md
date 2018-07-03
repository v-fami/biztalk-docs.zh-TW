---
title: 設定後援本機主機設定 （X12 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b552fa2b-1154-491f-9bcf-aaba3b8f343f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57763ad613025f475ae141a884bd9994a8e8a209
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012559"
---
# <a name="configuring-fallback-local-host-settings-x12-interchange-settings"></a><span data-ttu-id="b9289-102">設定後援本機主機設定 (X12-交換設定)</span><span class="sxs-lookup"><span data-stu-id="b9289-102">Configuring Fallback Local Host Settings (X12-Interchange Settings)</span></span>
<span data-ttu-id="b9289-103">本機主機設定控制了處理 EDI 交換的方式。</span><span class="sxs-lookup"><span data-stu-id="b9289-103">The local host settings govern how the EDI interchanges are processed.</span></span> <span data-ttu-id="b9289-104">此頁面上的設定可分成兩個類別 - 接收者的設定 (用於內送交換) 與傳送者的設定 (用於外寄交換)。</span><span class="sxs-lookup"><span data-stu-id="b9289-104">The settings on this page can be divided into two categories – receiver’s settings (for incoming interchanges) and sender’s settings (for outgoing interchanges).</span></span> <span data-ttu-id="b9289-105">在接收者的設定中，您可以指定 ST02 (通知控制編號) 的產生方式。</span><span class="sxs-lookup"><span data-stu-id="b9289-105">As part of the receiver’s settings, you can specify how the ST02 will be generated, the acknowledgement control number.</span></span> <span data-ttu-id="b9289-106">在傳送者的設定中，您可以指定為外寄訊息產生控制編號的方式。</span><span class="sxs-lookup"><span data-stu-id="b9289-106">As part of the sender’s settings, you can specify how the control numbers are generated for outgoing messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9289-107">此處所說明的設定也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="b9289-107">The settings described here also apply to HIPAA interchanges.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b9289-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="b9289-108">Prerequisites</span></span>  
 <span data-ttu-id="b9289-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="b9289-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-local-host--receivers-settings"></a><span data-ttu-id="b9289-110">若要設定本機主機 - 接收者的設定</span><span class="sxs-lookup"><span data-stu-id="b9289-110">To configure local host – receiver’s settings</span></span>  
  
1. <span data-ttu-id="b9289-111">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="b9289-111">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2. <span data-ttu-id="b9289-112">在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交換設定**區段中，按一下**本機主機設定**.</span><span class="sxs-lookup"><span data-stu-id="b9289-112">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Local Host Settings**.</span></span>  
  
3. <span data-ttu-id="b9289-113">若要指定通知中使用的交易集控制編號範圍，請輸入中的值**ACK 控制編號 (ST02)** 欄位。</span><span class="sxs-lookup"><span data-stu-id="b9289-113">To designate the range of transaction set control numbers used in an acknowledgment, enter values in the **ACK Control number (ST02)** fields.</span></span> <span data-ttu-id="b9289-114">在中間兩個欄位中輸入數值，並在必要時於前置詞和尾碼欄位中輸入英數字元值。</span><span class="sxs-lookup"><span data-stu-id="b9289-114">Enter a numeric value for the middle two fields, and an alphanumeric value (if desired) for the prefix and suffix fields.</span></span> <span data-ttu-id="b9289-115">中間幾個欄位是必要欄位，其中包含控制編號的最小值與最大值；前置詞和尾碼則是選用欄位。</span><span class="sxs-lookup"><span data-stu-id="b9289-115">The middle fields are required and contain the minimum and maximum values for the control number; the prefix and suffix are optional.</span></span> <span data-ttu-id="b9289-116">這三個欄位的最大長度都是 9 個字元。</span><span class="sxs-lookup"><span data-stu-id="b9289-116">The maximum length for all three fields is nine characters.</span></span>  
  
    <span data-ttu-id="b9289-117">若要重設目前的交易集控制編號的最小值，請按一下**重設**。</span><span class="sxs-lookup"><span data-stu-id="b9289-117">To reset the current transaction set control number to the minimum value, click **Reset**.</span></span> <span data-ttu-id="b9289-118">請檢查**重設為較低的限制，超出範圍時**重設下限的控制編號，一旦已超過最大值。</span><span class="sxs-lookup"><span data-stu-id="b9289-118">Check **Reset to lower limit when out of bound** to reset the control number to the lower limit once the maximum value has been exceeded.</span></span>  
  
### <a name="to-configure-local-host--senders-settings"></a><span data-ttu-id="b9289-119">若要設定本機主機 - 傳送者的設定</span><span class="sxs-lookup"><span data-stu-id="b9289-119">To configure local host – sender’s settings</span></span>  
  
1.  <span data-ttu-id="b9289-120">針對**交換控制編號 (ISA13)**，輸入數字以供 BizTalk Server 產生外寄交換的交換控制編號值範圍。</span><span class="sxs-lookup"><span data-stu-id="b9289-120">For **Interchange control number (ISA13)**, enter a range of values for the interchange control number to be used by BizTalk Server in generating an outgoing interchange.</span></span> <span data-ttu-id="b9289-121">輸入最小為 1，最大為 999999999 的數值。</span><span class="sxs-lookup"><span data-stu-id="b9289-121">Enter a numeric value with a minimum of 1 and a maximum of 999999999.</span></span> <span data-ttu-id="b9289-122">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="b9289-122">This is a mandatory field.</span></span>  
  
     <span data-ttu-id="b9289-123">若要重設控制編號，指定的最小值，請按一下**重設** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9289-123">To reset the control number to the minimum value specified, click the **Reset** button.</span></span> <span data-ttu-id="b9289-124">請檢查**重設為較低的限制，超出範圍時**自動重設為最小值 如果超過最大值。</span><span class="sxs-lookup"><span data-stu-id="b9289-124">Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.</span></span>  
  
2.  <span data-ttu-id="b9289-125">針對**群組控制編號 (GS06)**，輸入 BizTalk Server 應該用於群組控制編號的數字的範圍。</span><span class="sxs-lookup"><span data-stu-id="b9289-125">For **Group control number (GS06)**, enter the range of numbers that BizTalk Server should use for the group control number.</span></span> <span data-ttu-id="b9289-126">輸入最少 1 個字元，最多 9 個字元的數字值。</span><span class="sxs-lookup"><span data-stu-id="b9289-126">Enter a numeric value with a minimum of one character and a maximum of nine characters.</span></span> <span data-ttu-id="b9289-127">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="b9289-127">This is a required field.</span></span>  
  
     <span data-ttu-id="b9289-128">若要重設的群組控制編號，指定的最小值，請按一下**重設** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9289-128">To reset the group control number to the minimum value specified, click the **Reset** button.</span></span> <span data-ttu-id="b9289-129">請檢查**重設為較低的限制，超出範圍時**自動重設為最小值 如果超過最大值。</span><span class="sxs-lookup"><span data-stu-id="b9289-129">Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.</span></span>  
  
3.  <span data-ttu-id="b9289-130">針對**交易集控制編號 (ST02)**，按一下**套用新識別碼**，然後輸入選擇性的前置詞和後置詞的一系列的數字的值為必要的中間欄位及英數字元值。</span><span class="sxs-lookup"><span data-stu-id="b9289-130">For **Transaction Set Control number (ST02)**, click **Apply new ID**, and then enter a range of numeric values for the required middle fields, and alphanumeric values for the optional prefix and suffix.</span></span> <span data-ttu-id="b9289-131">這四個欄位的最大長度都是 9 個字元。</span><span class="sxs-lookup"><span data-stu-id="b9289-131">The maximum length of all four fields is nine characters.</span></span>  
  
     <span data-ttu-id="b9289-132">若要重設目前的交易集控制編號的最小值，請按一下**重設**。</span><span class="sxs-lookup"><span data-stu-id="b9289-132">To reset the current transaction set control number to the minimum value, click **Reset**.</span></span> <span data-ttu-id="b9289-133">選取 **重設為較低的限制，超出範圍時**的最小值重設控制編號，如果已超過最大值。</span><span class="sxs-lookup"><span data-stu-id="b9289-133">Select **Reset to lower limit when out of bound** to reset the control number to the minimum value if the maximum value has been exceeded.</span></span>  
  
4.  <span data-ttu-id="b9289-134">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9289-134">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9289-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9289-135">See Also</span></span>  
 [<span data-ttu-id="b9289-136">設定交換處理的 X12 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="b9289-136">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)