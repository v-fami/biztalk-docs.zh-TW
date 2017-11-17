---
title: "設定交易集清單 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b03ace75-70bf-47c9-9a94-df813d7cab1e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f6b4d9a5aae6c8758d3a6d4f46d18f9a820fabd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-transaction-set-list-edifact"></a><span data-ttu-id="0bbc5-102">設定交易集清單 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-102">Configuring Transaction Set List (EDIFACT)</span></span>
[!INCLUDE[prague](../includes/prague-md.md)]<span data-ttu-id="0bbc5-103"> 可讓您定義在處理 EDI 交換時要一律包括或排除的交易集清單。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-103"> enables you to define a list of transaction sets that must always be included or excluded while processing an EDI interchange.</span></span> <span data-ttu-id="0bbc5-104">本節提供如何建立交易集清單的指示。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-104">This section provides instructions on how to create the transaction set list.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0bbc5-105">任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-105">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0bbc5-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="0bbc5-106">Prerequisites</span></span>  
 <span data-ttu-id="0bbc5-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-a-transaction-set-list"></a><span data-ttu-id="0bbc5-108">若要設定交易集清單</span><span class="sxs-lookup"><span data-stu-id="0bbc5-108">To configure a transaction set list</span></span>  
  
1.  <span data-ttu-id="0bbc5-109">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-109">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="0bbc5-110">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-110">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0bbc5-111">在單向協議索引標籤底下**交易集設定**區段中，按一下**交易集清單**。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-111">On a one-way agreement tab, under **Transaction Set Settings** section, click **Transaction Set List**.</span></span>  
  
3.  <span data-ttu-id="0bbc5-112">選取**支援從清單中的交易集**選項，如果您想要建立必須一律先處理的交易集的清單。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-112">Select **Support Transaction Sets from the List** option if you want to create a list of transaction sets that must always be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bbc5-113">如果您所收到的通常是特定交易類型 (例如 APERAK) 的交換，則應使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-113">You would use this option if you typically receive interchanges with specific transaction types, say APERAK.</span></span> <span data-ttu-id="0bbc5-114">在此情況下，您應將該交易類型新增至清單中，而使其他類型的交易集完全不會受到處理。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-114">In that case, you add that transaction type to the list so that the transaction sets of other types are not processed at all.</span></span>  
  
4.  <span data-ttu-id="0bbc5-115">選取**排除交易集從清單**選項，如果您想要建立絕不處理的交易集的清單。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-115">Select **Exclude Transaction Sets from the List** option if you want to create a list of transaction sets that must not be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bbc5-116">如果您所收到的通常是各種不同的交易類型，則應使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-116">You would use this option if you typically receive interchanges with varied transaction types.</span></span> <span data-ttu-id="0bbc5-117">在此情況下，您應將這些交易類型新增至您不會為其取得任何交易集的清單。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-117">In that case, you add those transaction type to the list for which you do not get any transaction sets.</span></span>  
  
5.  <span data-ttu-id="0bbc5-118">按一下空白儲存格**UNH2.1**資料行然後從下拉式清單中選取的交易集您想要排除的型別。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-118">Click the empty cell in the **UNH2.1** column and from the drop-down select the transaction set type you want to support on exclude.</span></span>  
  
6.  <span data-ttu-id="0bbc5-119">若要從清單中刪除交易類型，選取交易類型的資料列，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-119">To delete a transaction type from the list, select the row for the transaction type, and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="0bbc5-120">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-120">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbc5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bbc5-121">See Also</span></span>  
 [<span data-ttu-id="0bbc5-122">設定交易集設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-122">Configuring Transaction Set Settings (EDIFACT)</span></span>](../core/configuring-transaction-set-settings-edifact.md)