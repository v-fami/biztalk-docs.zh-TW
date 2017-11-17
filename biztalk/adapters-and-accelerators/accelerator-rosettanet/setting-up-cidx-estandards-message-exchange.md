---
title: "設定 CIDX eStandards 訊息交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CIDX, configuring message exchange
ms.assetid: 90468459-cef7-436b-8c0b-3a7455a091c3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c4606dfc4b912d884a997bb65acb26cb4352448
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-cidx-estandards-message-exchange"></a><span data-ttu-id="d873e-102">設定 CIDX eStandards 訊息交換</span><span class="sxs-lookup"><span data-stu-id="d873e-102">Setting Up CIDX eStandards Message Exchange</span></span>
<span data-ttu-id="d873e-103">本主題描述如何設定 CIDX (化學資料交換) eStandards 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="d873e-103">This topic describes how to set up Chemical Data Exchange (CIDX) eStandards message exchange.</span></span> <span data-ttu-id="d873e-104">CIDX 要求設定下列三項屬性：</span><span class="sxs-lookup"><span data-stu-id="d873e-104">CIDX requires that you set the following three properties:</span></span>  
  
-   <span data-ttu-id="d873e-105">`Standard`屬性中的程序組態設定來**CIDX**</span><span class="sxs-lookup"><span data-stu-id="d873e-105">`Standard` property in the process configuration settings to **CIDX**</span></span>  
  
-   <span data-ttu-id="d873e-106">在程序組態設定中設定為 `True` 的 `Is Single Action` 屬性</span><span class="sxs-lookup"><span data-stu-id="d873e-106">`Is Single Action` property in the process configuration settings to `True`</span></span>  
  
-   <span data-ttu-id="d873e-107">`0A1 agreement`中以交易夥伴協議屬性**No 0A1**</span><span class="sxs-lookup"><span data-stu-id="d873e-107">`0A1 agreement` property in the trading partner agreement to **No 0A1**</span></span>  
  
 <span data-ttu-id="d873e-108">CIDX 與 RosettaNet 之間差異的詳細資訊，請參閱[CIDX 支援](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)。</span><span class="sxs-lookup"><span data-stu-id="d873e-108">For information about the differences between CIDX and RosettaNet, see [CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md).</span></span>  
  
### <a name="to-set-up-cidx-message-exchange"></a><span data-ttu-id="d873e-109">設定 CIDX 訊息交換</span><span class="sxs-lookup"><span data-stu-id="d873e-109">To set up CIDX message exchange</span></span>  
  
1.  <span data-ttu-id="d873e-110">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.</span><span class="sxs-lookup"><span data-stu-id="d873e-110">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="d873e-111">在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。</span><span class="sxs-lookup"><span data-stu-id="d873e-111">In the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].</span></span>  
  
3.  <span data-ttu-id="d873e-112">以滑鼠右鍵按一下**程序組態設定**，指向 **新增**，然後按一下 **程序組態**。</span><span class="sxs-lookup"><span data-stu-id="d873e-112">Right-click **Process Configuration Settings**, point to **New**, and then click **Process Configuration**.</span></span>  
  
4.  <span data-ttu-id="d873e-113">在 [新程序組態屬性] 對話方塊上**一般**索引標籤上，針對**標準**屬性選取**CIDX**。</span><span class="sxs-lookup"><span data-stu-id="d873e-113">In the New Process Configuration Properties dialog box, on the **General** tab, for the **Standard** property, select **CIDX**.</span></span>  
  
5.  <span data-ttu-id="d873e-114">上**活動**索引標籤上，針對**單向動作**屬性選取**True**。</span><span class="sxs-lookup"><span data-stu-id="d873e-114">On the **Activity** tab, for the **Is Single Action** property, select **True**.</span></span>  
  
6.  <span data-ttu-id="d873e-115">視需要，輸入其他程序組態設定。</span><span class="sxs-lookup"><span data-stu-id="d873e-115">Enter other process configuration settings as needed.</span></span> <span data-ttu-id="d873e-116">這些設定的相關資訊，請參閱中的資料表[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="d873e-116">For information about these settings, see the table in [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
7.  <span data-ttu-id="d873e-117">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d873e-117">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="d873e-118">以滑鼠右鍵按一下**協議**，指向 **新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="d873e-118">Right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
9. <span data-ttu-id="d873e-119">在**一般**，**連接埠**，**通訊協定**，和**Custom Properties**索引標籤上，輸入各種設定的值。</span><span class="sxs-lookup"><span data-stu-id="d873e-119">On the **General**, **Ports**, **Protocol**, and **Custom Properties** tabs, enter the values for the various settings.</span></span> <span data-ttu-id="d873e-120">這些設定的相關資訊，請參閱中的資料表[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="d873e-120">For information about these settings, see the table in [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
10. <span data-ttu-id="d873e-121">在 [新協議屬性] 對話方塊上**一般**索引標籤上，針對**0A1 協議**屬性選取**No 0A1**。</span><span class="sxs-lookup"><span data-stu-id="d873e-121">In the New Agreement Properties dialog box, on the **General** tab, for the **0A1 agreement** property, select **No 0A1**.</span></span>  
  
11. <span data-ttu-id="d873e-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d873e-122">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d873e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d873e-123">See Also</span></span>  
 <span data-ttu-id="d873e-124">[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d873e-124">[How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md) </span></span>  
 <span data-ttu-id="d873e-125">[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="d873e-125">[Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span></span>  
 <span data-ttu-id="d873e-126">[建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md) </span><span class="sxs-lookup"><span data-stu-id="d873e-126">[Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md) </span></span>  
 [<span data-ttu-id="d873e-127">建立或編輯夥伴</span><span class="sxs-lookup"><span data-stu-id="d873e-127">Creating or Editing a Partner</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)