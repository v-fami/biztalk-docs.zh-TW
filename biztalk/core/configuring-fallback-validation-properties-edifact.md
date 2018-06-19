---
title: 設定後援驗證屬性 (EDIFACT) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b925d063-e24b-4cfb-acbd-dcadb511011d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0e103eb2e20bb64973cd207ed2a55c2f91e58d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233198"
---
# <a name="configuring-fallback-validation-properties-edifact"></a><span data-ttu-id="a8c3f-102">設定後援驗證屬性 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="a8c3f-102">Configuring Fallback Validation Properties (EDIFACT)</span></span>
<span data-ttu-id="a8c3f-103">本節提供如何避免重複處理控制編號的指示。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-103">This section provides instructions on how to prevent duplicate control numbers from being processed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8c3f-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="a8c3f-104">Prerequisites</span></span>  
 <span data-ttu-id="a8c3f-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-duplicate-validation"></a><span data-ttu-id="a8c3f-106">設定重複項驗證</span><span class="sxs-lookup"><span data-stu-id="a8c3f-106">To configure duplicate validation</span></span>  
  
1.  <span data-ttu-id="a8c3f-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="a8c3f-108">在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**驗證**.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-108">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Validation**.</span></span>  
  
3.  <span data-ttu-id="a8c3f-109">選取**交換控制編號 (UNB5)** 核取方塊以啟用接收管線封鎖重複的交換。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-109">Select the **Interchange control number (UNB5)** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="a8c3f-110">如果選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會檢查所接收交換的交換控制編號，是否與其他所接收交換的交換控制編號相符。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-110">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number for the received interchange does not match the interchange control number of another received interchange.</span></span> <span data-ttu-id="a8c3f-111">如果偵測到相符項目時，接收管線不會處理交換。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-111">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4.  <span data-ttu-id="a8c3f-112">如果**交換控制編號 (UNB5)** 選取時，在**檢查重複的 unb5 內**欄位中，輸入檢查重複交換的天數。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-112">If **Interchange control number (UNB5)** is selected, in the **Check for duplicate UNB5 within** field, enter the number of days to check for a duplicate interchange.</span></span>  
  
5.  <span data-ttu-id="a8c3f-113">選取**交換中的群組控制編號 (UNG5)** ，避免接收管線處理重複的群組。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-113">Select **Group control number (UNG5) in interchange** to prevent the receive pipeline from processing duplicate groups.</span></span>  
  
6.  <span data-ttu-id="a8c3f-114">選取**交易集控制編號 (UNH1) 中群組**，避免接收管線處理重複的交易設定。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-114">Select **Transaction Set Control Number (UNH1) in group** to prevent the receive pipeline from processing duplicate transaction sets.</span></span>  
  
7.  <span data-ttu-id="a8c3f-115">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a8c3f-115">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c3f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8c3f-116">See Also</span></span>  
 [<span data-ttu-id="a8c3f-117">設定 EDIFACT 後援協議屬性的交換處理</span><span class="sxs-lookup"><span data-stu-id="a8c3f-117">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)