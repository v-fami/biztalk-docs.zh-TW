---
title: 設定後援信封屬性 （X12 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e9b05ea-2a0f-42d6-adc2-c1f1f2b7a993
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72fa2217b04b118160853b8c229a7d514a6583c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010671"
---
# <a name="configuring-fallback-envelope-properties-x12-interchange-settings"></a><span data-ttu-id="07e65-102">設定後援信封屬性 (X12 交換的設定)</span><span class="sxs-lookup"><span data-stu-id="07e65-102">Configuring Fallback Envelope Properties (X12-Interchange Settings)</span></span>
<span data-ttu-id="07e65-103">產生 X12 交換信封設定會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何產生傳送至接收合作對象的 X12 編碼交換信封。</span><span class="sxs-lookup"><span data-stu-id="07e65-103">X12 interchange envelope generation settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates the envelope of an X12-encoded interchange to be sent to the receiving party.</span></span> <span data-ttu-id="07e65-104">在此後援協議中，您會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 針對其傳送至合作對象的 X12 編碼交換來產生 ISA 區段的方式。</span><span class="sxs-lookup"><span data-stu-id="07e65-104">In this fallback agreement, you define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates the ISA segment for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="07e65-105">ISA 區段則是 X12 編碼交換的交換控制標頭。</span><span class="sxs-lookup"><span data-stu-id="07e65-105">An ISA segment is the interchange control header for an X12-encoded interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07e65-106">對於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段而言，英數 ISA 欄位的長度是固定的。</span><span class="sxs-lookup"><span data-stu-id="07e65-106">For the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime, the length of alphanumeric ISA fields is fixed.</span></span> <span data-ttu-id="07e65-107">不過，如果是 [!INCLUDE[TPM](../includes/tpm-md.md)] 使用者介面，則您可以針對英數 ISA 欄位輸入單一字元。</span><span class="sxs-lookup"><span data-stu-id="07e65-107">However, for the [!INCLUDE[TPM](../includes/tpm-md.md)] user interface, you may enter a single character for an alphanumeric ISA field.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="07e65-108"> 會使用尾端的空格字元來填補這些欄位，確保符合標準的需求。</span><span class="sxs-lookup"><span data-stu-id="07e65-108"> will pad these fields with trailing space characters to ensure compliance with standards requirements.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="07e65-109">此處所述設定同樣適用於 HIPAA 交換信封產生作業。</span><span class="sxs-lookup"><span data-stu-id="07e65-109">The settings described here also apply to HIPAA interchange envelope generation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="07e65-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="07e65-110">Prerequisites</span></span>  
 <span data-ttu-id="07e65-111">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="07e65-111">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-envelope"></a><span data-ttu-id="07e65-112">若要定義信封</span><span class="sxs-lookup"><span data-stu-id="07e65-112">To define the envelope</span></span>  
  
1. <span data-ttu-id="07e65-113">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="07e65-113">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2. <span data-ttu-id="07e65-114">在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交換設定**區段中，按一下**信封**.</span><span class="sxs-lookup"><span data-stu-id="07e65-114">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Envelopes**.</span></span>  
  
3. <span data-ttu-id="07e65-115">底下**ISA11 使用狀況**，保留**標準識別項**選取以指定標準的識別項，而非重複分隔符號，然後從下拉式清單中選取 標準識別項的值。</span><span class="sxs-lookup"><span data-stu-id="07e65-115">Under **ISA11 usage**, keep **Standard identifier** selected to specify a standard identifier instead of a repetition separator, and then select a value for the standard identifier from the drop-down list.</span></span> <span data-ttu-id="07e65-116">選取 **重複分隔符號**指定重複分隔符號而非標準的識別項，並然後輸入單一字元做為重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="07e65-116">Select **Repetition separator** to specify a repetition separator instead of a standard identifier, and then enter a single character for the repetition separator.</span></span> <span data-ttu-id="07e65-117">用來區隔交易集合中重複之區段的重複分隔符號，僅限使用 ASCII 字元集中的值。</span><span class="sxs-lookup"><span data-stu-id="07e65-117">The repetition separator, which is used to separate segments that repeat within a transaction set, is limited to the values in the ASCII character set.</span></span>  
  
4. <span data-ttu-id="07e65-118">針對**控制版本號碼 (ISA12)**，選取的 x12 標準所使用的版本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來產生外寄交換。</span><span class="sxs-lookup"><span data-stu-id="07e65-118">For **Control version number (ISA12)**, select the version of the X12 standard to be used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for generating an outgoing interchange.</span></span>  
  
5. <span data-ttu-id="07e65-119">針對**使用狀況指示符號 (ISA15)**，選取以表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是資訊、 生產資料還是測試資料。</span><span class="sxs-lookup"><span data-stu-id="07e65-119">For **Usage indicator (ISA15)**, select to indicate whether an interchange generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is information, production data, or test data.</span></span>  
  
6. <span data-ttu-id="07e65-120">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="07e65-120">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e65-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07e65-121">See Also</span></span>  
 [<span data-ttu-id="07e65-122">設定交換處理的 X12 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="07e65-122">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)