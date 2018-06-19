---
title: 步驟 4： 建立交易協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, trade agreeements
- loopback tutorial, creating trade agreements
- agreements, creating
ms.assetid: 9bcb80b1-fefc-4f1c-ae03-fb736cdfd524
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4e49efd8a2fd195c0b5fa912ced3773fa85153e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964261"
---
# <a name="step-4-create-a-trade-agreement"></a><span data-ttu-id="6b4a9-102">步驟 4： 建立交易協議</span><span class="sxs-lookup"><span data-stu-id="6b4a9-102">Step 4: Create a Trade Agreement</span></span>
<span data-ttu-id="6b4a9-103">在此步驟中，您將使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台，建立主要組織和夥伴組織之間的交易協議。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-103">In this step, you create a trade agreement between the home and partner organization using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span>  
  
### <a name="to-create-a-trade-agreement"></a><span data-ttu-id="6b4a9-104">若要建立交易協議</span><span class="sxs-lookup"><span data-stu-id="6b4a9-104">To create a trade agreement</span></span>  
  
1.  <span data-ttu-id="6b4a9-105">在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開 **BizTalk\<版本\>Accelerator for RosettaNet**，以滑鼠右鍵按一下**協議**，按一下 **新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-105">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, right-click **Agreements**, click **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="6b4a9-106">在**新協議屬性**對話方塊**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6b4a9-106">In the **New Agreement Properties** dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="6b4a9-107">使用</span><span class="sxs-lookup"><span data-stu-id="6b4a9-107">Use this</span></span>|<span data-ttu-id="6b4a9-108">動作</span><span class="sxs-lookup"><span data-stu-id="6b4a9-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6b4a9-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-109">**Name**</span></span>|<span data-ttu-id="6b4a9-110">型別**交易協議**。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-110">Type **Trade Agreement**.</span></span>|  
    |<span data-ttu-id="6b4a9-111">**程序組態**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-111">**Process Configuration**</span></span>|<span data-ttu-id="6b4a9-112">選取**STD_0C1_R01.02**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-112">Select **STD_0C1_R01.02** from the drop-down list.</span></span>|  
    |<span data-ttu-id="6b4a9-113">**我的組織**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-113">**My organization**</span></span>|<span data-ttu-id="6b4a9-114">選取**首頁**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-114">Select **HOME** from the drop-down list.</span></span>|  
    |<span data-ttu-id="6b4a9-115">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-115">**Partner organization**</span></span>|<span data-ttu-id="6b4a9-116">選取**夥伴**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-116">Select **PARTNER** from the drop-down list.</span></span>|  
    |<span data-ttu-id="6b4a9-117">**主要角色**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-117">**Home role**</span></span>|<span data-ttu-id="6b4a9-118">選取**啟動器**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-118">Select **Initiator** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="6b4a9-119">在**新協議屬性**對話方塊**連接埠**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6b4a9-119">In the **New Agreement Properties** dialog box, on the **Ports** tab, do the following:</span></span>  
  
    |<span data-ttu-id="6b4a9-120">使用</span><span class="sxs-lookup"><span data-stu-id="6b4a9-120">Use this</span></span>|<span data-ttu-id="6b4a9-121">動作</span><span class="sxs-lookup"><span data-stu-id="6b4a9-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6b4a9-122">**動作 URL**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-122">**Action URL**</span></span>|<span data-ttu-id="6b4a9-123">型別**http://localhost/BTARNApp/RNIFReceive.aspx**。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-123">Type **http://localhost/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="6b4a9-124">**信號 URL**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-124">**Signal URL**</span></span>|<span data-ttu-id="6b4a9-125">型別**http://localhost/BTARNApp/RNIFReceive.aspx**。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-125">Type **http://localhost/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="6b4a9-126">**同步 URL**</span><span class="sxs-lookup"><span data-stu-id="6b4a9-126">**Sync URL**</span></span>|<span data-ttu-id="6b4a9-127">保留空白。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-127">Leave blank.</span></span> <span data-ttu-id="6b4a9-128">同步化交易夥伴介面程序 (PIP) 不需要「同步 URL」。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-128">Sync URL is not required for the synchronous Partner Interface Process (PIP).</span></span>|  
  
4.  <span data-ttu-id="6b4a9-129">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-129">Click **Apply**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="6b4a9-130">建立交易協議之後，必須加以啟動。</span><span class="sxs-lookup"><span data-stu-id="6b4a9-130">After you create the trade agreement, you must activate it.</span></span>  
  
### <a name="to-activate-the-trade-agreement"></a><span data-ttu-id="6b4a9-131">啟動交易協議</span><span class="sxs-lookup"><span data-stu-id="6b4a9-131">To activate the trade agreement</span></span>  
  
-   <span data-ttu-id="6b4a9-132">在[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，按一下 **協議**，以滑鼠右鍵按一下**交易協議**在結果窗格中，然後按一下**Activate**.</span><span class="sxs-lookup"><span data-stu-id="6b4a9-132">In the [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], click **Agreements**, right-click **Trade Agreement** in the results pane, and then click **Activate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4a9-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b4a9-133">See Also</span></span>  
 [<span data-ttu-id="6b4a9-134">步驟 5：建立鏡像協議</span><span class="sxs-lookup"><span data-stu-id="6b4a9-134">Step 5: Create a Mirror Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)