---
title: 設定字元集和分隔符號 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6249f2e1-70b0-4960-bbc4-0c3fefd26faa
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9615e3cdcf46872ff2d07ecdff4ea7288f09f94f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976687"
---
# <a name="configuring-charset-and-separators-x12"></a><span data-ttu-id="a30fb-102">設定字元集與分隔符號 (X12)</span><span class="sxs-lookup"><span data-stu-id="a30fb-102">Configuring Charset and Separators (X12)</span></span>
<span data-ttu-id="a30fb-103">在夥伴協議中，您可以指定建立 X12 外寄訊息的信封時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來驗證合作對象屬性的字元集。</span><span class="sxs-lookup"><span data-stu-id="a30fb-103">In the partner agreement, you can specify the character set that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing X12 message.</span></span> <span data-ttu-id="a30fb-104">您也可以指定要在交換的區段中使用的分隔字元與結束字元。</span><span class="sxs-lookup"><span data-stu-id="a30fb-104">You can also specify what separators and terminators will be used for the segments in the interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a30fb-105">此處所說明的設定也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="a30fb-105">The settings described here also apply to HIPAA interchanges.</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="a30fb-106">下列屬性會停用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="a30fb-106">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
> 
> - <span data-ttu-id="a30fb-107">**資料元素**</span><span class="sxs-lookup"><span data-stu-id="a30fb-107">**Data element**</span></span>  
>   -   <span data-ttu-id="a30fb-108">**元件元素分隔符號 (ISA16)**</span><span class="sxs-lookup"><span data-stu-id="a30fb-108">**Component element separator (ISA16)**</span></span>  
>   -   <span data-ttu-id="a30fb-109">**區段結束字元**</span><span class="sxs-lookup"><span data-stu-id="a30fb-109">**Segment terminator**</span></span>  
>   -   <span data-ttu-id="a30fb-110">**後置詞**</span><span class="sxs-lookup"><span data-stu-id="a30fb-110">**Suffix**</span></span>  
>   -   <span data-ttu-id="a30fb-111">**取代內容中的分隔符號**</span><span class="sxs-lookup"><span data-stu-id="a30fb-111">**Replace separators in payload with**</span></span>  
> 
>   <span data-ttu-id="a30fb-112">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="a30fb-112">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="a30fb-113">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a30fb-113">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a30fb-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="a30fb-114">Prerequisites</span></span>  
 <span data-ttu-id="a30fb-115">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="a30fb-115">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-character-set-and-separators"></a><span data-ttu-id="a30fb-116">若要設定字元集和分隔符號</span><span class="sxs-lookup"><span data-stu-id="a30fb-116">To configure the character set and separators</span></span>  
  
1. <span data-ttu-id="a30fb-117">建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="a30fb-117">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="a30fb-118">若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a30fb-118">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2. <span data-ttu-id="a30fb-119">在單向協議索引標籤底下**交換設定**區段中，按一下**字元集和分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="a30fb-119">On a one-way agreement tab, under **Interchange Settings** section, click **Charset and Separators**.</span></span>  
  
3. <span data-ttu-id="a30fb-120">從**要使用的字元集**下拉式清單中，選取 X12 字元集來驗證您輸入協議屬性。</span><span class="sxs-lookup"><span data-stu-id="a30fb-120">From the **Character set to be used** drop-down list, select the X12 character set to be used to validate the properties that you enter for the agreement.</span></span>  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a30fb-121"> 只會使用這個設定來驗證相關協議屬性的輸入值。</span><span class="sxs-lookup"><span data-stu-id="a30fb-121"> only uses this setting to validate the values entered for the related agreement properties.</span></span> <span data-ttu-id="a30fb-122">當接收管線或傳送管線進行執行階段處理時，將會忽略此字元集屬性。</span><span class="sxs-lookup"><span data-stu-id="a30fb-122">The receive pipeline or send pipeline will ignore this character-set property when performing run-time processing.</span></span>  
  
4. <span data-ttu-id="a30fb-123">針對**資料項目**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將用以分隔複合資料元素，其中包含兩個或多個簡單資料元素和不屬於複合元素的簡單資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-123">For **Data element**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate composite data elements consisting of two or more simple data elements, and simple data elements that are not part of a composite element.</span></span> <span data-ttu-id="a30fb-124">選取  **Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-124">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="a30fb-125">當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a30fb-125">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
5. <span data-ttu-id="a30fb-126">針對**元件元素分隔符號 (ISA16)**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用來分隔複合資料元素內的簡單資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-126">For **Component element separator (ISA16)**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate simple data elements within composite data elements.</span></span> <span data-ttu-id="a30fb-127">選取  **Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-127">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="a30fb-128">當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a30fb-128">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
6. <span data-ttu-id="a30fb-129">針對**區段結束字元**，請輸入單一字元，用以指出 EDI 區段的結尾。</span><span class="sxs-lookup"><span data-stu-id="a30fb-129">For **Segment terminator**, enter a single character to indicate the end of an EDI segment.</span></span> <span data-ttu-id="a30fb-130">選取  **Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-130">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span>  
  
    <span data-ttu-id="a30fb-131">如果類型是**Char**，預設值是**~**。</span><span class="sxs-lookup"><span data-stu-id="a30fb-131">If the type is **Char**, the default value is **~**.</span></span>  
  
    <span data-ttu-id="a30fb-132">如果類型是**Hex**，預設值是**7E**。</span><span class="sxs-lookup"><span data-stu-id="a30fb-132">If the type is **Hex**, the default value is **7E**.</span></span>  
  
    <span data-ttu-id="a30fb-133">這是必要的資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-133">This data element is required.</span></span>  
  
    <span data-ttu-id="a30fb-134">這個項目限制為 ASCII 字元集中的值。</span><span class="sxs-lookup"><span data-stu-id="a30fb-134">This element is limited to the values in the ASCII character set.</span></span> <span data-ttu-id="a30fb-135">這個屬性不會根據 [一般] 頁面中定義的 X12 字元集進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a30fb-135">This property is not validated against the X12 character set defined in the General page.</span></span>  
  
    <span data-ttu-id="a30fb-136">當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a30fb-136">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
7. <span data-ttu-id="a30fb-137">針對**後置詞**，選取要使用的字元**使用**區段結束字元值。</span><span class="sxs-lookup"><span data-stu-id="a30fb-137">For **Suffix**, select the character to use **with** the Segment Terminator value.</span></span> <span data-ttu-id="a30fb-138">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="a30fb-138">Options include:</span></span>  
  
   - <span data-ttu-id="a30fb-139">**無**: Default</span><span class="sxs-lookup"><span data-stu-id="a30fb-139">**None**: Default</span></span>  
  
   - <span data-ttu-id="a30fb-140">**CR**： 歸位字元</span><span class="sxs-lookup"><span data-stu-id="a30fb-140">**CR**: Carriage Return</span></span>  
  
   - <span data-ttu-id="a30fb-141">**LF**： 換行字元</span><span class="sxs-lookup"><span data-stu-id="a30fb-141">**LF**: Line Feed</span></span>  
  
   - <span data-ttu-id="a30fb-142">**CR LF**： 歸位/換</span><span class="sxs-lookup"><span data-stu-id="a30fb-142">**CR LF**: Carriage Return/Line Feed</span></span>  
  
     <span data-ttu-id="a30fb-143">區段結束字元和尾碼的組合可包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="a30fb-143">The Segment Terminator and Suffix combinations include the following:</span></span>  
  
   - <span data-ttu-id="a30fb-144">**任何**區段結束字元 +**無**後置詞</span><span class="sxs-lookup"><span data-stu-id="a30fb-144">**Any** Segment Terminator + **None** Suffix</span></span>  
  
   - <span data-ttu-id="a30fb-145">**任何**區段結束字元 + **CR**後置詞</span><span class="sxs-lookup"><span data-stu-id="a30fb-145">**Any** Segment Terminator + **CR** Suffix</span></span>  
  
   - <span data-ttu-id="a30fb-146">**任何**區段結束字元 + **CR LF**後置詞</span><span class="sxs-lookup"><span data-stu-id="a30fb-146">**Any** Segment Terminator + **CR LF** Suffix</span></span>  
  
   - <span data-ttu-id="a30fb-147">**D （十六進位）** 區段結束字元 +**無**尾碼： 這個組合就如同區段結束字元空白且尾碼設定為 CR。</span><span class="sxs-lookup"><span data-stu-id="a30fb-147">**D (Hex)** Segment Terminator + **None** Suffix: This combination behaves as if Segment Terminator is blank and Suffix is set to CR.</span></span>  
  
   - <span data-ttu-id="a30fb-148">（十六進位） 區段結束字元 +**無**尾碼： 這個組合就如同區段結束字元空白且尾碼設定為 LF。</span><span class="sxs-lookup"><span data-stu-id="a30fb-148">A (Hex) Segment Terminator + **None** Suffix: This combination behaves as if Segment Terminator is blank and Suffix is set to LF.</span></span>  
  
   - <span data-ttu-id="a30fb-149">**D （十六進位）** 區段結束字元 + **LF**尾碼： 這個組合就如同區段結束字元為 CR 且尾碼設定為 LF。</span><span class="sxs-lookup"><span data-stu-id="a30fb-149">**D (Hex)** Segment Terminator + **LF** Suffix: This combination behaves as if Segment Terminator is CR and Suffix is set to LF.</span></span>  
  
8. <span data-ttu-id="a30fb-150">如果裝載資料含有也可以當作資料、 區段或元件分隔符號的字元，請檢查**取代內容中的分隔符號**並指定取代字元。</span><span class="sxs-lookup"><span data-stu-id="a30fb-150">If the payload data contains characters that are also used as data, segment, or component separators, check **Replace separators in payload with** and specify a replacement character.</span></span> <span data-ttu-id="a30fb-151">產生 X12 外寄訊息時，內容資料中的所有分隔符號字元都將被取代為指定的字元。</span><span class="sxs-lookup"><span data-stu-id="a30fb-151">When generating the outbound X12 message, all instances of separator characters in the payload data will be replaced with the specified character.</span></span> <span data-ttu-id="a30fb-152">選取  **Char**字元資料元素或**Hex**十六進位資料元素。</span><span class="sxs-lookup"><span data-stu-id="a30fb-152">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="a30fb-153">當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a30fb-153">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
9. <span data-ttu-id="a30fb-154">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a30fb-154">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30fb-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a30fb-155">See Also</span></span>  
 [<span data-ttu-id="a30fb-156">設定交換設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="a30fb-156">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)