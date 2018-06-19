---
title: 設定信封 （Edifact-interchange 設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501ccc5f-e21c-4c36-9509-217d5b3ba21f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 531b559e690fae5369298a90cd372edcae79db57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233518"
---
# <a name="configuring-envelopes-edifact-interchange-settings"></a><span data-ttu-id="f8cbd-102">設定信封 (EDIFACT-Interchange 設定)</span><span class="sxs-lookup"><span data-stu-id="f8cbd-102">Configuring Envelopes (EDIFACT-Interchange Settings)</span></span>
<span data-ttu-id="f8cbd-103">本節提供如何設定外寄 EDIFACT 訊息之信封的指示。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-103">This section provides instructions on how to configure the envelope for outgoing EDIFACT messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f8cbd-104">所有屬性會停都用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-104">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="f8cbd-105">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-105">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="f8cbd-106">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-106">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8cbd-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="f8cbd-107">Prerequisites</span></span>  
 <span data-ttu-id="f8cbd-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-interchange-envelope"></a><span data-ttu-id="f8cbd-109">若要設定交換信封</span><span class="sxs-lookup"><span data-stu-id="f8cbd-109">To configure the interchange envelope</span></span>  
  
1.  <span data-ttu-id="f8cbd-110">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-110">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="f8cbd-111">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-111">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f8cbd-112">在單向協議索引標籤底下**交換設定**區段中，按一下**信封**。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-112">On a one-way agreement tab, under **Interchange Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="f8cbd-113">如**處理優先順序代碼 (UNB8)**，輸入最少一個字元，最多 1 個字元的字母值。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-113">For **Processing priority code (UNB8)**, enter an alphabetical value with a minimum of one character and a maximum of one character.</span></span> <span data-ttu-id="f8cbd-114">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-114">This is an optional field.</span></span>  
  
4.  <span data-ttu-id="f8cbd-115">如**通訊協議 (UNB10)**，輸入最少一個字元，最多 35 個字元的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-115">For **Communication agreement (UNB10)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="f8cbd-116">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-116">This is an optional field</span></span>  
  
5.  <span data-ttu-id="f8cbd-117">選取**測試指示符號 (UNB11)** 表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是測試資料。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-117">Select **Test indicator (UNB11)** to indicate that the interchange generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is test data.</span></span>  
  
6.  <span data-ttu-id="f8cbd-118">選取**套用 UNA 區段 （字串服務建議）** 產生要傳送交換的 UNA 區段。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-118">Select **Apply UNA segment (String service advice)** to generate a UNA segment for the interchange to be sent.</span></span> <span data-ttu-id="f8cbd-119">如果已核取此選項，然後**UNA6**不可為空白和**UNA 6 尾碼**不可**無**。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-119">If this option is checked, then **UNA6** cannot be empty and **UNA 6 Suffix** cannot be **None**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8cbd-120">您指定**UNA6**和**UNA6 尾碼**中**字元集和分隔符號**頁面中所述[設定字元集和分隔符號 (EDIFACT)](../core/configuring-charset-and-separators-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="f8cbd-120">You specify **UNA6** and **UNA6 Suffix** in the **Charset and Separators** page as described in [Configuring Charset and Separators (EDIFACT)](../core/configuring-charset-and-separators-edifact.md).</span></span>  
  
7.  <span data-ttu-id="f8cbd-121">選取**套用 UNG 區段 （功能群組標頭）** 功能群組標頭外寄訊息中建立群組區段。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-121">Select **Apply UNG segments (Functional group header)** to create grouping segments in the functional group header in outgoing messages.</span></span>  
  
8.  <span data-ttu-id="f8cbd-122">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f8cbd-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cbd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8cbd-123">See Also</span></span>  
 [<span data-ttu-id="f8cbd-124">設定交換設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="f8cbd-124">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)