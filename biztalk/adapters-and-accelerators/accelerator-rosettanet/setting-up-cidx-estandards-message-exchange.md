---
title: 設定 CIDX eStandards 訊息交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, configuring message exchange
ms.assetid: 90468459-cef7-436b-8c0b-3a7455a091c3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2aef1c49ca4bb87ef2e9388b9cdfcc86d2f35f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988863"
---
# <a name="setting-up-cidx-estandards-message-exchange"></a><span data-ttu-id="803b9-102">設定 CIDX eStandards 訊息交換</span><span class="sxs-lookup"><span data-stu-id="803b9-102">Setting Up CIDX eStandards Message Exchange</span></span>
<span data-ttu-id="803b9-103">本主題描述如何設定 CIDX (化學資料交換) eStandards 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="803b9-103">This topic describes how to set up Chemical Data Exchange (CIDX) eStandards message exchange.</span></span> <span data-ttu-id="803b9-104">CIDX 要求設定下列三項屬性：</span><span class="sxs-lookup"><span data-stu-id="803b9-104">CIDX requires that you set the following three properties:</span></span>  
  
- <span data-ttu-id="803b9-105">`Standard` 中的程序組態設定的屬性**CIDX**</span><span class="sxs-lookup"><span data-stu-id="803b9-105">`Standard` property in the process configuration settings to **CIDX**</span></span>  
  
- <span data-ttu-id="803b9-106">在程序組態設定中設定為 `True` 的 `Is Single Action` 屬性</span><span class="sxs-lookup"><span data-stu-id="803b9-106">`Is Single Action` property in the process configuration settings to `True`</span></span>  
  
- <span data-ttu-id="803b9-107">`0A1 agreement` 在交易夥伴協議屬性**無 0A1**</span><span class="sxs-lookup"><span data-stu-id="803b9-107">`0A1 agreement` property in the trading partner agreement to **No 0A1**</span></span>  
  
  <span data-ttu-id="803b9-108">CIDX 與 RosettaNet 之間差異的詳細資訊，請參閱[CIDX 支援](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)。</span><span class="sxs-lookup"><span data-stu-id="803b9-108">For information about the differences between CIDX and RosettaNet, see [CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md).</span></span>  
  
### <a name="to-set-up-cidx-message-exchange"></a><span data-ttu-id="803b9-109">設定 CIDX 訊息交換</span><span class="sxs-lookup"><span data-stu-id="803b9-109">To set up CIDX message exchange</span></span>  
  
1. <span data-ttu-id="803b9-110">按一下 **開始**，指向**所有程式**，指向**Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span><span class="sxs-lookup"><span data-stu-id="803b9-110">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2. <span data-ttu-id="803b9-111">在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。</span><span class="sxs-lookup"><span data-stu-id="803b9-111">In the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].</span></span>  
  
3. <span data-ttu-id="803b9-112">以滑鼠右鍵按一下**程序組態設定**，指向**新增**，然後按一下**程序組態**。</span><span class="sxs-lookup"><span data-stu-id="803b9-112">Right-click **Process Configuration Settings**, point to **New**, and then click **Process Configuration**.</span></span>  
  
4. <span data-ttu-id="803b9-113">在新的程序組態屬性 對話方塊中，在**一般**索引標籤上，如**標準**屬性中，選取**CIDX**。</span><span class="sxs-lookup"><span data-stu-id="803b9-113">In the New Process Configuration Properties dialog box, on the **General** tab, for the **Standard** property, select **CIDX**.</span></span>  
  
5. <span data-ttu-id="803b9-114">上**活動**索引標籤上，如**單向動作**屬性中，選取**True**。</span><span class="sxs-lookup"><span data-stu-id="803b9-114">On the **Activity** tab, for the **Is Single Action** property, select **True**.</span></span>  
  
6. <span data-ttu-id="803b9-115">視需要，輸入其他程序組態設定。</span><span class="sxs-lookup"><span data-stu-id="803b9-115">Enter other process configuration settings as needed.</span></span> <span data-ttu-id="803b9-116">如需這些設定的詳細資訊，請參閱中的資料表[如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="803b9-116">For information about these settings, see the table in [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
7. <span data-ttu-id="803b9-117">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="803b9-117">Click **OK**.</span></span>  
  
8. <span data-ttu-id="803b9-118">以滑鼠右鍵按一下**協議**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="803b9-118">Right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
9. <span data-ttu-id="803b9-119">在上**一般**，**連接埠**，**通訊協定**，以及**自訂屬性**索引標籤上，輸入各種設定的值。</span><span class="sxs-lookup"><span data-stu-id="803b9-119">On the **General**, **Ports**, **Protocol**, and **Custom Properties** tabs, enter the values for the various settings.</span></span> <span data-ttu-id="803b9-120">如需這些設定的詳細資訊，請參閱中的資料表[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="803b9-120">For information about these settings, see the table in [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
10. <span data-ttu-id="803b9-121">在 [新協議屬性] 對話方塊中，在**一般**索引標籤上，如**0A1 協議**屬性中，選取**No 0A1**。</span><span class="sxs-lookup"><span data-stu-id="803b9-121">In the New Agreement Properties dialog box, on the **General** tab, for the **0A1 agreement** property, select **No 0A1**.</span></span>  
  
11. <span data-ttu-id="803b9-122">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="803b9-122">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="803b9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="803b9-123">See Also</span></span>  
 <span data-ttu-id="803b9-124">[如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="803b9-124">[How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md) </span></span>  
 <span data-ttu-id="803b9-125">[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="803b9-125">[Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span></span>  
 <span data-ttu-id="803b9-126">[建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md) </span><span class="sxs-lookup"><span data-stu-id="803b9-126">[Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md) </span></span>  
 [<span data-ttu-id="803b9-127">建立或編輯夥伴</span><span class="sxs-lookup"><span data-stu-id="803b9-127">Creating or Editing a Partner</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)