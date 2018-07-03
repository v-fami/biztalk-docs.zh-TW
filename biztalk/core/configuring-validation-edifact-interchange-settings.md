---
title: 設定驗證 （EDIFACT 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55820ebc-fe21-48a3-8985-1bf4184176ac
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a700282aee9651b8f259c931a460a774f900a4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999727"
---
# <a name="configuring-validation-edifact-interchange-settings"></a><span data-ttu-id="6d93b-102">設定驗證 (EDIFACT-Interchange 設定)</span><span class="sxs-lookup"><span data-stu-id="6d93b-102">Configuring Validation (EDIFACT-Interchange Settings)</span></span>
<span data-ttu-id="6d93b-103">本節提供如何避免重複處理控制編號的指示。</span><span class="sxs-lookup"><span data-stu-id="6d93b-103">This section provides instructions on how to prevent duplicate control numbers from being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d93b-104">沒有屬性會停用此頁面上即使您清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="6d93b-104">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6d93b-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="6d93b-105">Prerequisites</span></span>  
 <span data-ttu-id="6d93b-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="6d93b-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-duplicate-validation"></a><span data-ttu-id="6d93b-107">設定重複項驗證</span><span class="sxs-lookup"><span data-stu-id="6d93b-107">To configure duplicate validation</span></span>  
  
1. <span data-ttu-id="6d93b-108">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="6d93b-108">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="6d93b-109">若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6d93b-109">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2. <span data-ttu-id="6d93b-110">在單向協議索引標籤底下**交換設定**區段中，按一下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="6d93b-110">On a one-way agreement tab, under **Interchange Settings** section, click **Validation**.</span></span>  
  
3. <span data-ttu-id="6d93b-111">選取 **交換控制編號 (UNB5)** 核取方塊以啟用接收管線封鎖重複的交換。</span><span class="sxs-lookup"><span data-stu-id="6d93b-111">Select the **Interchange control number (UNB5)** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="6d93b-112">如果選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會檢查所接收交換的交換控制編號，是否與其他所接收交換的交換控制編號相符。</span><span class="sxs-lookup"><span data-stu-id="6d93b-112">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number for the received interchange does not match the interchange control number of another received interchange.</span></span> <span data-ttu-id="6d93b-113">如果偵測到相符項目時，接收管線不會處理交換。</span><span class="sxs-lookup"><span data-stu-id="6d93b-113">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4. <span data-ttu-id="6d93b-114">如果**交換控制編號 (UNB5)** 已選取，在**檢查是否有重複的 UNB5 內**欄位中，輸入檢查重複交換的天數。</span><span class="sxs-lookup"><span data-stu-id="6d93b-114">If **Interchange control number (UNB5)** is selected, in the **Check for duplicate UNB5 within** field, enter the number of days to check for a duplicate interchange.</span></span>  
  
5. <span data-ttu-id="6d93b-115">選取 **交換中的群組控制編號 (UNG5)** ，避免接收管線處理重複的群組。</span><span class="sxs-lookup"><span data-stu-id="6d93b-115">Select **Group control number (UNG5) in interchange** to prevent the receive pipeline from processing duplicate groups.</span></span>  
  
6. <span data-ttu-id="6d93b-116">選取 [**交易集控制編號 (UNH1)] 群組中**，避免接收管線處理重複的交易設定。</span><span class="sxs-lookup"><span data-stu-id="6d93b-116">Select **Transaction Set Control Number (UNH1) in group** to prevent the receive pipeline from processing duplicate transaction sets.</span></span>  
  
7. <span data-ttu-id="6d93b-117">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6d93b-117">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d93b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d93b-118">See Also</span></span>  
 [<span data-ttu-id="6d93b-119">設定交換設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="6d93b-119">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)