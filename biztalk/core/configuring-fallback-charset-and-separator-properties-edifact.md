---
title: "設定後援字元集與分隔符號屬性 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eadc9c1-ebec-42f5-a9ca-06cb28bebcdf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b517a98130f2d245d68083dc16c65865950800c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-charset-and-separator-properties-edifact"></a><span data-ttu-id="3bef5-102">設定後援字集和分隔符號屬性 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="3bef5-102">Configuring Fallback Charset and Separator Properties (EDIFACT)</span></span>
<span data-ttu-id="3bef5-103">在後援協議中，您可以指定在建立 EDIFACT 外寄訊息的信封時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會用來驗證合作對象屬性的字元集 (UNA)。</span><span class="sxs-lookup"><span data-stu-id="3bef5-103">In the fallback agreement, you can specify the character set (UNA) that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing EDIFACT message.</span></span> <span data-ttu-id="3bef5-104">您也可以指定要對交換中的區段使用的分隔符號和結束字元 (UNB)。</span><span class="sxs-lookup"><span data-stu-id="3bef5-104">You can also specify what separators and terminators (UNB) will be used for the segments in the interchange.</span></span>  
  
 <span data-ttu-id="3bef5-105">在 UNA 區段中，您可以定義 BizTalk Server 如何針對產生傳送至合作對象的 EDIFACT 編碼交換來產生 UNA 區段。</span><span class="sxs-lookup"><span data-stu-id="3bef5-105">In the UNA segment, you define how BizTalk Server generates the UNA segment for an EDIFACT-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="3bef5-106">UNA 區段會定義在 EDIFACT 編碼的交換中，用來當做分隔符號和指標的字元。</span><span class="sxs-lookup"><span data-stu-id="3bef5-106">The UNA segment defines the characters that will be used as separators and indicators for an EDIFACT-encoded interchange.</span></span> <span data-ttu-id="3bef5-107">只有當此交換包含非標準的分隔符號字元時，才能使用這個區段。</span><span class="sxs-lookup"><span data-stu-id="3bef5-107">Use this segment only if the interchange contains non-standard separator characters.</span></span>  
  
 <span data-ttu-id="3bef5-108">在 UNB 區段中，您可以定義要使用的 EDIFACT 字元集。</span><span class="sxs-lookup"><span data-stu-id="3bef5-108">In the UNB segment, you define the EDIFACT character set to be used.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3bef5-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="3bef5-109">Prerequisites</span></span>  
 <span data-ttu-id="3bef5-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="3bef5-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-character-set-and-separators"></a><span data-ttu-id="3bef5-111">若要設定字元集和分隔符號</span><span class="sxs-lookup"><span data-stu-id="3bef5-111">To configure the character set and separators</span></span>  
  
1.  <span data-ttu-id="3bef5-112">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="3bef5-112">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="3bef5-113">在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**字元集和分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="3bef5-113">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Charset and Separators**.</span></span>  
  
3.  <span data-ttu-id="3bef5-114">在**語法 (UNB1)**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3bef5-114">In the **Syntax (UNB1)** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="3bef5-115">如**識別項 (UNB1.1)**，輸入要套用到外寄交換的 EDIFACT 字元集。</span><span class="sxs-lookup"><span data-stu-id="3bef5-115">For **Identifier (UNB1.1)**, enter the EDIFACT character set to be applied on the outgoing interchange.</span></span> <span data-ttu-id="3bef5-116">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="3bef5-116">This is a required field.</span></span>  
  
    2.  <span data-ttu-id="3bef5-117">如**版本 (UNB1.2)**，選取一個介於**1**和**4**。</span><span class="sxs-lookup"><span data-stu-id="3bef5-117">For **Version (UNB1.2)**, select a value between **1** and **4**.</span></span> <span data-ttu-id="3bef5-118">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="3bef5-118">This is an optional field.</span></span>  
  
4.  <span data-ttu-id="3bef5-119">在**分隔符號**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3bef5-119">In the **Separators** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="3bef5-120">如**元件資料元素分隔符號 (UNA1)**，輸入元件資料元素分隔符號分隔複合資料元素內的簡單資料元素的值。</span><span class="sxs-lookup"><span data-stu-id="3bef5-120">For **Component data element separator (UNA1)**, enter a value for the component data element separator that separates simple data elements within composite data elements.</span></span> <span data-ttu-id="3bef5-121">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="3bef5-121">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="3bef5-122">如果您變更字元的格式，輸入的字元就會自動變更。</span><span class="sxs-lookup"><span data-stu-id="3bef5-122">The character you entered will automatically change if you change its format.</span></span>  
  
    2.  <span data-ttu-id="3bef5-123">如**資料元素分隔符號 (UNA2)**，輸入資料元素分隔符號分隔的兩個或多個簡單資料元素或不屬於複合的簡單資料元素所組成的複合資料元素的值。</span><span class="sxs-lookup"><span data-stu-id="3bef5-123">For **Data element separator (UNA2)**, enter a value for the data element separator that separates composite data elements consisting of two or more simple data elements or simple data elements that are not part of a composite.</span></span> <span data-ttu-id="3bef5-124">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="3bef5-124">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="3bef5-125">如果您變更字元的格式，輸入的字元就會自動變更。</span><span class="sxs-lookup"><span data-stu-id="3bef5-125">The character you entered will automatically change if you change its format.</span></span>  
  
    3.  <span data-ttu-id="3bef5-126">如**小數點標記 (UNA3)**，選取要在外寄交換中使用的小數點標記。</span><span class="sxs-lookup"><span data-stu-id="3bef5-126">For **Decimal notation (UNA3)**, select the decimal notation to be used in the outgoing interchange.</span></span>  
  
    4.  <span data-ttu-id="3bef5-127">如**釋放指示符號 (UNA4)**，輸入釋放指示符號，指出接的字元不是語法分隔符號、 結束字元或釋放字元，而是原始資料的一部分的值。</span><span class="sxs-lookup"><span data-stu-id="3bef5-127">For **Release indicator (UNA4)**, enter a value for the release indicator that indicates that the following character is not a syntax separator, terminator, or release character, but is part of the original data.</span></span> <span data-ttu-id="3bef5-128">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="3bef5-128">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="3bef5-129">如果您變更字元的格式，輸入的字元就會自動變更。</span><span class="sxs-lookup"><span data-stu-id="3bef5-129">The character you entered will automatically change if you change its format.</span></span>  
  
    5.  <span data-ttu-id="3bef5-130">如**重複分隔符號 (UNA5)**，為交易集內重複的區段用來分隔為重複分隔符號輸入值。</span><span class="sxs-lookup"><span data-stu-id="3bef5-130">For **Repetition separator (UNA5)**, enter a value for the repetition separator that is used to separate segments that repeat within a transaction set.</span></span> <span data-ttu-id="3bef5-131">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="3bef5-131">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="3bef5-132">如果您變更字元的格式，輸入的字元就會自動變更。</span><span class="sxs-lookup"><span data-stu-id="3bef5-132">The character you entered will automatically change if you change its format.</span></span>  
  
    6.  <span data-ttu-id="3bef5-133">如**區段結束字元 (UNA6)**，表示 EDI 區段結尾的區段結束字元輸入的值。</span><span class="sxs-lookup"><span data-stu-id="3bef5-133">For **Segment terminator (UNA6)**, enter a value for the segment terminator that indicates the end of an EDI segment.</span></span>  
  
    7.  <span data-ttu-id="3bef5-134">如**UNA6 尾碼**，選取 BizTalk Server 將搭配使用區段識別碼可以是字元**無**， **CR** （歸位字元）、 **LF**（換行字元），或**CR LF** （歸位字元/換）。</span><span class="sxs-lookup"><span data-stu-id="3bef5-134">For **UNA6 Suffix**, select the character that BizTalk Server will use with the Segment identifier, either **None**, **CR** (carriage return), **LF** (line feed), or **CR LF** (carriage return/line feed).</span></span> <span data-ttu-id="3bef5-135">如果您指定尾碼，區段結束字元資料元素即可為空白。</span><span class="sxs-lookup"><span data-stu-id="3bef5-135">If you designate a suffix, the segment terminator data element can be empty.</span></span> <span data-ttu-id="3bef5-136">如果區段結束字元留白，您就必須指定尾碼。</span><span class="sxs-lookup"><span data-stu-id="3bef5-136">If the segment terminator is left empty, you must designate a suffix.</span></span> <span data-ttu-id="3bef5-137">區段結束字元和尾碼的組合可以是下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="3bef5-137">The combination of the segment terminator and suffix can be any of the following:</span></span>  
  
        -   <span data-ttu-id="3bef5-138">區段結束字元</span><span class="sxs-lookup"><span data-stu-id="3bef5-138">Segment terminator</span></span>  
  
        -   <span data-ttu-id="3bef5-139">區域結束字元 + 歸位字元</span><span class="sxs-lookup"><span data-stu-id="3bef5-139">Segment terminator + carriage return</span></span>  
  
        -   <span data-ttu-id="3bef5-140">區域結束字元 + 歸位字元/換行字元</span><span class="sxs-lookup"><span data-stu-id="3bef5-140">Segment terminator + carriage return/line feed</span></span>  
  
        -   <span data-ttu-id="3bef5-141">歸位字元</span><span class="sxs-lookup"><span data-stu-id="3bef5-141">Carriage return</span></span>  
  
        -   <span data-ttu-id="3bef5-142">換行字元</span><span class="sxs-lookup"><span data-stu-id="3bef5-142">Line feed</span></span>  
  
        -   <span data-ttu-id="3bef5-143">歸位字元/換行字元</span><span class="sxs-lookup"><span data-stu-id="3bef5-143">Carriage return/line feed</span></span>  
  
5.  <span data-ttu-id="3bef5-144">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證並接受變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3bef5-144">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate and accept the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bef5-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bef5-145">See Also</span></span>  
 [<span data-ttu-id="3bef5-146">設定 EDIFACT 後援協議屬性的交換處理</span><span class="sxs-lookup"><span data-stu-id="3bef5-146">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)