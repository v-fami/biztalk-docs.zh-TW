---
title: 設定後援字元集與分隔符號屬性 (X12) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477f4952-6a4e-4e98-a37f-f6e1fe7db3d3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633ea22c611eb0fab994fd62250b9cb9ff8a0f2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233838"
---
# <a name="configuring-fallback-charset-and-separator-properties-x12"></a><span data-ttu-id="42b5e-102">設定後援字元集與分隔符號屬性 (X12)</span><span class="sxs-lookup"><span data-stu-id="42b5e-102">Configuring Fallback Charset and Separator Properties (X12)</span></span>
<span data-ttu-id="42b5e-103">在後援協議中，您可以指定建立 X12 外寄訊息的信封時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來驗證合作對象屬性的字元集。</span><span class="sxs-lookup"><span data-stu-id="42b5e-103">In the fallback agreement, you can specify the character set that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing X12 message.</span></span> <span data-ttu-id="42b5e-104">您也可以指定要在交換的區段中使用的分隔字元與結束字元。</span><span class="sxs-lookup"><span data-stu-id="42b5e-104">You can also specify what separators and terminators will be used for the segments in the interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42b5e-105">此處所說明的設定也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="42b5e-105">The settings described here also apply to HIPAA interchanges.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="42b5e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="42b5e-106">Prerequisites</span></span>  
 <span data-ttu-id="42b5e-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="42b5e-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-character-set-and-separators"></a><span data-ttu-id="42b5e-108">若要設定字元集和分隔符號</span><span class="sxs-lookup"><span data-stu-id="42b5e-108">To configure the character set and separators</span></span>  
  
1.  <span data-ttu-id="42b5e-109">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="42b5e-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="42b5e-110">在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交換設定**區段中，按一下**字元集與分隔符號**.</span><span class="sxs-lookup"><span data-stu-id="42b5e-110">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Charset and Separators**.</span></span>  
  
3.  <span data-ttu-id="42b5e-111">從**要使用的字元集**下拉式清單中，選取 X12 字元集用來驗證您輸入協議屬性。</span><span class="sxs-lookup"><span data-stu-id="42b5e-111">From the **Character set to be used** drop-down list, select the X12 character set to be used to validate the properties that you enter for the agreement.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="42b5e-112"> 只會使用這個設定來驗證相關協議屬性的輸入值。</span><span class="sxs-lookup"><span data-stu-id="42b5e-112"> only uses this setting to validate the values entered for the related agreement properties.</span></span> <span data-ttu-id="42b5e-113">當接收管線或傳送管線進行執行階段處理時，將會忽略此字元集屬性。</span><span class="sxs-lookup"><span data-stu-id="42b5e-113">The receive pipeline or send pipeline will ignore this character-set property when performing run-time processing.</span></span>  
  
4.  <span data-ttu-id="42b5e-114">如**資料項目**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用以分隔複合資料元素包含兩個或多個簡單資料元素，以及不屬於複合元素的簡單資料元素。</span><span class="sxs-lookup"><span data-stu-id="42b5e-114">For **Data element**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate composite data elements consisting of two or more simple data elements, and simple data elements that are not part of a composite element.</span></span> <span data-ttu-id="42b5e-115">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="42b5e-115">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="42b5e-116">當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="42b5e-116">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
5.  <span data-ttu-id="42b5e-117">如**元件元素分隔符號 (ISA16)**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用以分隔複合資料元素中的簡單資料元素。</span><span class="sxs-lookup"><span data-stu-id="42b5e-117">For **Component element separator (ISA16)**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate simple data elements within composite data elements.</span></span> <span data-ttu-id="42b5e-118">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="42b5e-118">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="42b5e-119">當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="42b5e-119">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
6.  <span data-ttu-id="42b5e-120">如**區段結束字元**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]要用來表示 EDI 區段結束。</span><span class="sxs-lookup"><span data-stu-id="42b5e-120">For **Segment terminator**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to indicate the end of an EDI segment.</span></span> <span data-ttu-id="42b5e-121">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="42b5e-121">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="42b5e-122">當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="42b5e-122">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
7.  <span data-ttu-id="42b5e-123">如**尾碼**，選取的字元，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將是搭配區段識別項中，使用**無**， **CR** （歸位字元）、 **LF**（換行字元），或**CR LF** （歸位字元/換）。</span><span class="sxs-lookup"><span data-stu-id="42b5e-123">For **Suffix**, select the character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use with the Segment identifier, either **None**, **CR** (carriage return), **LF** (line feed), or **CR LF** (carriage return/line feed).</span></span> <span data-ttu-id="42b5e-124">如果您指定尾碼，區段結束字元資料元素即可為空白。</span><span class="sxs-lookup"><span data-stu-id="42b5e-124">If you designate a suffix, the segment terminator data element can be empty.</span></span> <span data-ttu-id="42b5e-125">如果區段結束字元留白，您就必須指定尾碼。</span><span class="sxs-lookup"><span data-stu-id="42b5e-125">If the segment terminator is left empty, you must designate a suffix.</span></span> <span data-ttu-id="42b5e-126">區段結束字元和尾碼的組合可以是下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="42b5e-126">The combination of the segment terminator and suffix can be any of the following:</span></span>  
  
    -   <span data-ttu-id="42b5e-127">區段結束字元</span><span class="sxs-lookup"><span data-stu-id="42b5e-127">Segment terminator</span></span>  
  
    -   <span data-ttu-id="42b5e-128">區域結束字元 + 歸位字元</span><span class="sxs-lookup"><span data-stu-id="42b5e-128">Segment terminator + carriage return</span></span>  
  
    -   <span data-ttu-id="42b5e-129">區域結束字元 + 歸位字元/換行字元</span><span class="sxs-lookup"><span data-stu-id="42b5e-129">Segment terminator + carriage return/line feed</span></span>  
  
    -   <span data-ttu-id="42b5e-130">歸位字元</span><span class="sxs-lookup"><span data-stu-id="42b5e-130">Carriage return</span></span>  
  
    -   <span data-ttu-id="42b5e-131">換行字元</span><span class="sxs-lookup"><span data-stu-id="42b5e-131">Line feed</span></span>  
  
    -   <span data-ttu-id="42b5e-132">歸位字元/換行字元</span><span class="sxs-lookup"><span data-stu-id="42b5e-132">Carriage return/line feed</span></span>  
  
8.  <span data-ttu-id="42b5e-133">如果裝載資料含有也用來當做資料、 區段或元件分隔字元，請檢查**取代內容中的分隔符號**並指定取代字元。</span><span class="sxs-lookup"><span data-stu-id="42b5e-133">If the payload data contains characters that are also used as data, segment, or component separators, check **Replace separators in payload with** and specify a replacement character.</span></span> <span data-ttu-id="42b5e-134">產生 X12 外寄訊息時，內容資料中的所有分隔符號字元都將被取代為指定的字元。</span><span class="sxs-lookup"><span data-stu-id="42b5e-134">When generating the outbound X12 message, all instances of separator characters in the payload data will be replaced with the specified character.</span></span> <span data-ttu-id="42b5e-135">選取**Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="42b5e-135">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="42b5e-136">當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="42b5e-136">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
9. <span data-ttu-id="42b5e-137">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="42b5e-137">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b5e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42b5e-138">See Also</span></span>  
 [<span data-ttu-id="42b5e-139">設定 X12 後援協議屬性的交換處理</span><span class="sxs-lookup"><span data-stu-id="42b5e-139">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)