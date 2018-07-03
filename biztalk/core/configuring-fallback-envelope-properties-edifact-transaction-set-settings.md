---
title: 設定後援信封屬性 （EDIFACT 交易集設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b56a5a93-35ac-4293-b00e-28dcd89dfa2a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f060b37004346ae5b7419acbe9f1fcf1d128179
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020258"
---
# <a name="configuring-fallback-envelope-properties-edifact-transaction-set-settings"></a><span data-ttu-id="52c71-102">設定後援信封屬性 (EDIFACT 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="52c71-102">Configuring Fallback Envelope Properties (EDIFACT-Transaction Set Settings)</span></span>
<span data-ttu-id="52c71-103">在 [**信封**頁面**交易集設定**] 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象的 EDIFACT 編碼交換的 UNG 區段。</span><span class="sxs-lookup"><span data-stu-id="52c71-103">In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the UNG segments for an EDIFACT-encoded interchange that it sends to the party.</span></span>  
  
 <span data-ttu-id="52c71-104">UNG 區段是識別和指定 EDIFACT 編碼交換之功能群組的標頭。</span><span class="sxs-lookup"><span data-stu-id="52c71-104">The UNG segment is the header that identifies and specifies a functional group of an EDIFACT-encoded interchange.</span></span> <span data-ttu-id="52c71-105">其中包含準備功能群組的日期與時間資訊，以及功能群組中文件的類型與版本資訊。</span><span class="sxs-lookup"><span data-stu-id="52c71-105">It contains information about the date and time that the functional group was prepared, together with the type and version of the document in the functional group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="52c71-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="52c71-106">Prerequisites</span></span>  
 <span data-ttu-id="52c71-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="52c71-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-ung-segments"></a><span data-ttu-id="52c71-108">若要定義 UNG 區段</span><span class="sxs-lookup"><span data-stu-id="52c71-108">To define the UNG segments</span></span>  
  
1. <span data-ttu-id="52c71-109">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="52c71-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2. <span data-ttu-id="52c71-110">在  **EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤之下**交易集設定**區段中，按一下**信封**.</span><span class="sxs-lookup"><span data-stu-id="52c71-110">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3. <span data-ttu-id="52c71-111">針對**功能群組識別碼 (UNG1)**，輸入最少一個字元，最多 6 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-111">For **Functional group ID (UNG1)**, enter an alphanumeric value with a minimum of one character and a maximum of six characters.</span></span> <span data-ttu-id="52c71-112">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-112">This is a required field.</span></span>  
  
4. <span data-ttu-id="52c71-113">輸入值，以找出**應用程式傳送者 (UNG2)**。</span><span class="sxs-lookup"><span data-stu-id="52c71-113">Enter values to identify **Application sender (UNG2)**.</span></span>  
  
   -   <span data-ttu-id="52c71-114">針對**識別 (UNG2.1)**，輸入最少一個字元，最多 35 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-114">For **Identification (UNG2.1)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="52c71-115">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-115">This is a required field.</span></span>  
  
   -   <span data-ttu-id="52c71-116">針對**代碼辨識符號 (UNG2.2)**，輸入最少一個字元，最多四個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-116">For **Code qualifier (UNG2.2)**, enter an alphanumeric value with a minimum of one character and a maximum of four characters.</span></span> <span data-ttu-id="52c71-117">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-117">This is an optional field.</span></span>  
  
5. <span data-ttu-id="52c71-118">輸入值，以找出**應用程式收件者 (UNG3)**。</span><span class="sxs-lookup"><span data-stu-id="52c71-118">Enter values to identify **Application recipient (UNG3)**.</span></span>  
  
   -   <span data-ttu-id="52c71-119">針對**識別 (UNG3.1)**，輸入最少一個字元，最多 35 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-119">For **Identification (UNG3.1)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="52c71-120">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-120">This is a required field.</span></span>  
  
   -   <span data-ttu-id="52c71-121">針對**代碼辨識符號 (UNG3.2)**，輸入最少一個字元，最多四個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-121">For **Code qualifier (UNG3.2)**, enter an alphanumeric value with a minimum of one character and a maximum of four characters.</span></span> <span data-ttu-id="52c71-122">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-122">This is an optional field.</span></span>  
  
6. <span data-ttu-id="52c71-123">針對**控管單位 (UNG6)**，輸入最少一個字元，最多 2 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-123">For **Controlling agency (UNG6)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters.</span></span> <span data-ttu-id="52c71-124">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-124">This is a required field.</span></span>  
  
7. <span data-ttu-id="52c71-125">輸入值，以找出**訊息版本 (UNG7)**。</span><span class="sxs-lookup"><span data-stu-id="52c71-125">Enter values to identify **Message version (UNG7)**.</span></span>  
  
   -   <span data-ttu-id="52c71-126">針對**版本 (UNG7.1)**，輸入最少一個字元，最多 3 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-126">For **Version (UNG7.1)**, enter an alphanumeric value with a minimum of one character and a maximum of three characters.</span></span> <span data-ttu-id="52c71-127">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-127">This is a required field.</span></span>  
  
   -   <span data-ttu-id="52c71-128">針對**版次 (UNG7.2)**，輸入最少一個字元，最多 3 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-128">For **Release (UNG7.2)**, enter an alphanumeric value with a minimum of one character and a maximum of three characters.</span></span> <span data-ttu-id="52c71-129">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-129">This is a required field.</span></span>  
  
   -   <span data-ttu-id="52c71-130">針對**關聯指定代碼 (UNG7.3)**，輸入最少 1 個字元，最多 6 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-130">For **Association assigned code (UNG7.3)**, enter an alphanumeric value with a minimum of 1 character and a maximum of 6 characters.</span></span> <span data-ttu-id="52c71-131">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-131">This is an optional field.</span></span>  
  
8. <span data-ttu-id="52c71-132">針對**應用程式密碼 (UNG8)**，輸入最少一個字元，最多 14 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="52c71-132">For **Application password (UNG8)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="52c71-133">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="52c71-133">This is a required field.</span></span>  
  
9. <span data-ttu-id="52c71-134">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52c71-134">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c71-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52c71-135">See Also</span></span>  
 [<span data-ttu-id="52c71-136">設定交易集設定的 EDIFACT 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="52c71-136">Configuring EDIFACT Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)