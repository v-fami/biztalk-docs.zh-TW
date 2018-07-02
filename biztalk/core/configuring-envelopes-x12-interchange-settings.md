---
title: 設定信封 （X12 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4fade73-14cf-475c-81b5-6102c75db991
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab420ed868ccd84240f53fc900106bbd56ab15ed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971351"
---
# <a name="configuring-envelopes-x12-interchange-settings"></a><span data-ttu-id="db264-102">設定信封 (X12 交換設定)</span><span class="sxs-lookup"><span data-stu-id="db264-102">Configuring Envelopes (X12-Interchange Settings)</span></span>
<span data-ttu-id="db264-103">產生 X12 交換信封設定會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何產生傳送至接收合作對象的 X12 編碼交換信封。</span><span class="sxs-lookup"><span data-stu-id="db264-103">X12 interchange envelope generation settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates the envelope of an X12-encoded interchange to be sent to the receiving party.</span></span> <span data-ttu-id="db264-104">在本節中，您會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 針對其傳送至合作對象的 X12 編碼交換來產生 ISA 區段的方式。</span><span class="sxs-lookup"><span data-stu-id="db264-104">In this section, you define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates the ISA segment for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="db264-105">ISA 區段則是 X12 編碼交換的交換控制標頭。</span><span class="sxs-lookup"><span data-stu-id="db264-105">An ISA segment is the interchange control header for an X12-encoded interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db264-106">對於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段而言，英數 ISA 欄位的長度是固定的。</span><span class="sxs-lookup"><span data-stu-id="db264-106">For the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime, the length of alphanumeric ISA fields is fixed.</span></span> <span data-ttu-id="db264-107">不過，如果是 [!INCLUDE[TPM](../includes/tpm-md.md)] 使用者介面，則您可以針對英數 ISA 欄位輸入單一字元。</span><span class="sxs-lookup"><span data-stu-id="db264-107">However, for the [!INCLUDE[TPM](../includes/tpm-md.md)] user interface, you may enter a single character for an alphanumeric ISA field.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="db264-108"> 會使用尾端的空格字元來填補這些欄位，確保符合標準的需求。</span><span class="sxs-lookup"><span data-stu-id="db264-108"> will pad these fields with trailing space characters to ensure compliance with standards requirements.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="db264-109">此處所述設定同樣適用於 HIPAA 交換信封產生作業。</span><span class="sxs-lookup"><span data-stu-id="db264-109">The settings described here also apply to HIPAA interchange envelope generation.</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="db264-110">所有屬性會停都用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="db264-110">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
> 
>  <span data-ttu-id="db264-111">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="db264-111">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="db264-112">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="db264-112">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="db264-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="db264-113">Prerequisites</span></span>  
 <span data-ttu-id="db264-114">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="db264-114">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-envelope"></a><span data-ttu-id="db264-115">若要定義信封</span><span class="sxs-lookup"><span data-stu-id="db264-115">To define the envelope</span></span>  
  
1. <span data-ttu-id="db264-116">建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="db264-116">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="db264-117">若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="db264-117">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2. <span data-ttu-id="db264-118">在單向協議索引標籤底下**交換設定**區段中，按一下**信封**。</span><span class="sxs-lookup"><span data-stu-id="db264-118">On a one-way agreement tab, under **Interchange Settings** section, click **Envelopes**.</span></span>  
  
3. <span data-ttu-id="db264-119">底下**ISA11 使用狀況**，保留**標準識別項**選取以指定標準的識別項，而非重複分隔符號，然後從下拉式清單中選取 標準識別項的值。</span><span class="sxs-lookup"><span data-stu-id="db264-119">Under **ISA11 usage**, keep **Standard identifier** selected to specify a standard identifier instead of a repetition separator, and then select a value for the standard identifier from the drop-down list.</span></span> <span data-ttu-id="db264-120">選取 **重複分隔符號**指定重複分隔符號而非標準的識別項，並然後輸入單一字元做為重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="db264-120">Select **Repetition separator** to specify a repetition separator instead of a standard identifier, and then enter a single character for the repetition separator.</span></span> <span data-ttu-id="db264-121">用來區隔交易集合中重複之區段的重複分隔符號，僅限使用 ASCII 字元集中的值。</span><span class="sxs-lookup"><span data-stu-id="db264-121">The repetition separator, which is used to separate segments that repeat within a transaction set, is limited to the values in the ASCII character set.</span></span>  
  
4. <span data-ttu-id="db264-122">針對**控制版本號碼 (ISA12)**，選取的 x12 標準所使用的版本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來產生外寄交換。</span><span class="sxs-lookup"><span data-stu-id="db264-122">For **Control version number (ISA12)**, select the version of the X12 standard to be used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for generating an outgoing interchange.</span></span>  
  
5. <span data-ttu-id="db264-123">針對**使用狀況指示符號 (ISA15)**，選取以表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是資訊、 生產資料還是測試資料。</span><span class="sxs-lookup"><span data-stu-id="db264-123">For **Usage indicator (ISA15)**, select to indicate whether an interchange generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is information, production data, or test data.</span></span>  
  
6. <span data-ttu-id="db264-124">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db264-124">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db264-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db264-125">See Also</span></span>  
 [<span data-ttu-id="db264-126">設定交換設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="db264-126">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)