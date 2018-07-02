---
title: 設定後援驗證屬性 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a64431d-373a-4d63-9b83-cbb323620152
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f9dca1416b106e951b32efe79d18260201dc48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973927"
---
# <a name="configuring-fallback-validation-properties-x12"></a><span data-ttu-id="c4154-102">設定後援驗證屬性 (X12)</span><span class="sxs-lookup"><span data-stu-id="c4154-102">Configuring Fallback Validation Properties (X12)</span></span>
<span data-ttu-id="c4154-103">X12 交換驗證產生後援設定定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何在收到的交換中檢查重複的控制編號。</span><span class="sxs-lookup"><span data-stu-id="c4154-103">X12 interchange validation generation fallback settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] checks for duplicate control numbers in the received interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4154-104">此處所說明的設定也適用於 HIPAA 交換驗證。</span><span class="sxs-lookup"><span data-stu-id="c4154-104">The settings described here also apply to HIPAA interchange validation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c4154-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="c4154-105">Prerequisites</span></span>  
 <span data-ttu-id="c4154-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="c4154-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-validation"></a><span data-ttu-id="c4154-107">若要設定驗證</span><span class="sxs-lookup"><span data-stu-id="c4154-107">To configure validation</span></span>  
  
1. <span data-ttu-id="c4154-108">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="c4154-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2. <span data-ttu-id="c4154-109">在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交換設定**區段中，按一下**驗證**.</span><span class="sxs-lookup"><span data-stu-id="c4154-109">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Validation**.</span></span>  
  
3. <span data-ttu-id="c4154-110">選取 **交換控制編號**核取方塊以啟用接收管線封鎖重複的交換。</span><span class="sxs-lookup"><span data-stu-id="c4154-110">Select the **Interchange Control Number** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="c4154-111">若選取上述核取方塊，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會檢查該交換控制編號，確定所接收交換的交換控制編號 (ISA13) 與該交換控制編號不相符。</span><span class="sxs-lookup"><span data-stu-id="c4154-111">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number (ISA13) for the received interchange does not match the interchange control number.</span></span> <span data-ttu-id="c4154-112">如果偵測到相符項目時，接收管線不會處理交換。</span><span class="sxs-lookup"><span data-stu-id="c4154-112">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4. <span data-ttu-id="c4154-113">如果**交換控制編號**已選取，在**檢查是否有重複的 ISA13 內**欄位中，輸入將使用特定執行檢查重複交換的天數交換控制編號。</span><span class="sxs-lookup"><span data-stu-id="c4154-113">If **Interchange Control Number** is selected, in the **Check for duplicate ISA13 within** field, enter the number of days that a check for a duplicate interchange will be performed using a specific interchange control number.</span></span>  
  
5. <span data-ttu-id="c4154-114">選取 **群組控制編號**，避免接收管線處理具有重複群組控制編號 (GS6) 的交換。</span><span class="sxs-lookup"><span data-stu-id="c4154-114">Select **Group Control Number** to prevent the receive pipeline from processing interchanges with duplicate group control numbers (GS6).</span></span>  
  
6. <span data-ttu-id="c4154-115">選取 **交易集控制編號**，避免接收管線處理具有重複交易集控制編號 (ST2) 的交換。</span><span class="sxs-lookup"><span data-stu-id="c4154-115">Select **Transaction Set Control Number** to prevent the receive pipeline from processing interchanges with duplicate transaction set control numbers (ST2).</span></span>  
  
7. <span data-ttu-id="c4154-116">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c4154-116">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4154-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4154-117">See Also</span></span>  
 [<span data-ttu-id="c4154-118">設定交換處理的 X12 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="c4154-118">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)