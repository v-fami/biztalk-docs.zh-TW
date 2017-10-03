---
title: "設定交易集清單 (X12) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f277318-90e9-4ad3-843a-e6128837fa2b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b11ea09c7c3156aea18b95d758228e55994901
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-transaction-set-list-x12"></a><span data-ttu-id="04b2f-102">設定交易集清單 (X12)</span><span class="sxs-lookup"><span data-stu-id="04b2f-102">Configuring Transaction Set List (X12)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="04b2f-103"> 可讓您定義在處理 EDI 交換時要一律包括或排除的交易集清單。</span><span class="sxs-lookup"><span data-stu-id="04b2f-103"> enables you to define a list of transaction sets that must always be included or excluded while processing an EDI interchange.</span></span> <span data-ttu-id="04b2f-104">本節提供如何建立交易集清單的指示。</span><span class="sxs-lookup"><span data-stu-id="04b2f-104">This section provides instructions on how to create the transaction set list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b2f-105">此處所說明的設定也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="04b2f-105">The settings described here also apply to HIPAA interchanges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04b2f-106">任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="04b2f-106">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="04b2f-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="04b2f-107">Prerequisites</span></span>  
 <span data-ttu-id="04b2f-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="04b2f-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-a-transaction-set-list"></a><span data-ttu-id="04b2f-109">若要設定交易集清單</span><span class="sxs-lookup"><span data-stu-id="04b2f-109">To configure a transaction set list</span></span>  
  
1.  <span data-ttu-id="04b2f-110">建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="04b2f-110">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="04b2f-111">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="04b2f-111">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="04b2f-112">在單向協議索引標籤底下**交易集設定**區段中，按一下**交易集清單**。</span><span class="sxs-lookup"><span data-stu-id="04b2f-112">On a one-way agreement tab, under **Transaction Set Settings** section, click **Transaction Set List**.</span></span>  
  
3.  <span data-ttu-id="04b2f-113">選取**支援從清單中的交易集**選項，如果您想要建立必須一律先處理的交易集的清單。</span><span class="sxs-lookup"><span data-stu-id="04b2f-113">Select **Support Transaction Sets from the List** option if you want to create a list of transaction sets that must always be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04b2f-114">如果您所收到的通常是特定交易類型 (例如 850) 的交換，則應使用此選項。</span><span class="sxs-lookup"><span data-stu-id="04b2f-114">You would use this option if you typically receive interchanges with specific transaction types, say 850.</span></span> <span data-ttu-id="04b2f-115">在此情況下，您應將該交易類型新增至清單中，而使其他類型的交易集完全不會受到處理。</span><span class="sxs-lookup"><span data-stu-id="04b2f-115">In that case, you add that transaction type to the list so that the transaction sets of other types are not processed at all.</span></span>  
  
4.  <span data-ttu-id="04b2f-116">選取**排除交易集從清單**選項，如果您想要建立絕不處理的交易集的清單。</span><span class="sxs-lookup"><span data-stu-id="04b2f-116">Select **Exclude Transaction Sets from the List** option if you want to create a list of transaction sets that must not be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04b2f-117">如果您所收到的通常是各種不同的交易類型，則應使用此選項。</span><span class="sxs-lookup"><span data-stu-id="04b2f-117">You would use this option if you typically receive interchanges with varied transaction types.</span></span> <span data-ttu-id="04b2f-118">在此情況下，您應將這些交易類型新增至您不會為其取得任何交易集的清單。</span><span class="sxs-lookup"><span data-stu-id="04b2f-118">In that case, you add those transaction type to the list for which you do not get any transaction sets.</span></span>  
  
5.  <span data-ttu-id="04b2f-119">按一下空白儲存格**ST01**資料行然後從下拉式清單中選取的交易集您想要排除的型別。</span><span class="sxs-lookup"><span data-stu-id="04b2f-119">Click the empty cell in the **ST01** column and from the drop-down select the transaction set type you want to support on exclude.</span></span>  
  
6.  <span data-ttu-id="04b2f-120">若要從清單中刪除交易類型，選取交易類型的資料列，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="04b2f-120">To delete a transaction type from the list, select the row for the transaction type, and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="04b2f-121">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="04b2f-121">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b2f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04b2f-122">See Also</span></span>  
 [<span data-ttu-id="04b2f-123">設定交易集設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="04b2f-123">Configuring Transaction Set Settings (X12)</span></span>](../core/configuring-transaction-set-settings-x12.md)