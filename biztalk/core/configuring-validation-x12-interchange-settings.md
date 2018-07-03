---
title: 設定驗證 （X12 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdad7016-1d66-4d11-b620-c28368f00133
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eba4a7cbeffe342e37c366c3ce391018beec748
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988695"
---
# <a name="configuring-validation-x12-interchange-settings"></a><span data-ttu-id="6afba-102">設定驗證 (X12 交換設定)</span><span class="sxs-lookup"><span data-stu-id="6afba-102">Configuring Validation (X12-Interchange Settings)</span></span>
<span data-ttu-id="6afba-103">X12 交換驗證產生設定會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何在收到的交換中檢查重複的交換控制編號。</span><span class="sxs-lookup"><span data-stu-id="6afba-103">X12 interchange validation generation settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] checks for duplicate control numbers in the received interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6afba-104">此處所說明的設定也適用於 HIPAA 交換驗證。</span><span class="sxs-lookup"><span data-stu-id="6afba-104">The settings described here also apply to HIPAA interchange validation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6afba-105">沒有屬性會停用此頁面上即使您清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="6afba-105">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6afba-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="6afba-106">Prerequisites</span></span>  
 <span data-ttu-id="6afba-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="6afba-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-validation"></a><span data-ttu-id="6afba-108">若要設定驗證</span><span class="sxs-lookup"><span data-stu-id="6afba-108">To configure validation</span></span>  
  
1. <span data-ttu-id="6afba-109">建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="6afba-109">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="6afba-110">若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6afba-110">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2. <span data-ttu-id="6afba-111">在單向協議索引標籤底下**交換設定**區段中，按一下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="6afba-111">On a one-way agreement tab, under **Interchange Settings** section, click **Validation**.</span></span>  
  
3. <span data-ttu-id="6afba-112">選取 **交換控制編號**核取方塊以啟用接收管線封鎖重複的交換。</span><span class="sxs-lookup"><span data-stu-id="6afba-112">Select the **Interchange Control Number** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="6afba-113">若選取上述核取方塊，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會檢查該交換控制編號，確定所接收交換的交換控制編號 (ISA13) 與該交換控制編號不相符。</span><span class="sxs-lookup"><span data-stu-id="6afba-113">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number (ISA13) for the received interchange does not match the interchange control number.</span></span> <span data-ttu-id="6afba-114">如果偵測到相符項目時，接收管線不會處理交換。</span><span class="sxs-lookup"><span data-stu-id="6afba-114">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4. <span data-ttu-id="6afba-115">如果**交換控制編號**已選取，在**檢查是否有重複的 ISA13 內**欄位中，輸入將使用特定執行檢查重複交換的天數交換控制編號。</span><span class="sxs-lookup"><span data-stu-id="6afba-115">If **Interchange Control Number** is selected, in the **Check for duplicate ISA13 within** field, enter the number of days that a check for a duplicate interchange will be performed using a specific interchange control number.</span></span>  
  
5. <span data-ttu-id="6afba-116">選取 **群組控制編號**，避免接收管線處理具有重複群組控制編號 (GS6) 的交換。</span><span class="sxs-lookup"><span data-stu-id="6afba-116">Select **Group Control Number** to prevent the receive pipeline from processing interchanges with duplicate group control numbers (GS6).</span></span>  
  
6. <span data-ttu-id="6afba-117">選取 **交易集控制編號**，避免接收管線處理具有重複交易集控制編號 (ST2) 的交換。</span><span class="sxs-lookup"><span data-stu-id="6afba-117">Select **Transaction Set Control Number** to prevent the receive pipeline from processing interchanges with duplicate transaction set control numbers (ST2).</span></span>  
  
7. <span data-ttu-id="6afba-118">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6afba-118">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afba-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6afba-119">See Also</span></span>  
 [<span data-ttu-id="6afba-120">設定交換設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="6afba-120">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)