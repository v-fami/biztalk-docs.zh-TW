---
title: 步驟 4： 建立交易協議 |Microsoft Docs
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
ms.openlocfilehash: bbe74e1b214d733615bbc46deaea9f8a7e6c5134
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994631"
---
# <a name="step-4-create-a-trade-agreement"></a><span data-ttu-id="cdef6-102">步驟 4： 建立交易協議</span><span class="sxs-lookup"><span data-stu-id="cdef6-102">Step 4: Create a Trade Agreement</span></span>
<span data-ttu-id="cdef6-103">在此步驟中，您會建立交易協議使用 Microsoft® 在主要和夥伴組織之間[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="cdef6-103">In this step, you create a trade agreement between the home and partner organization using the Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span>  

### <a name="to-create-a-trade-agreement"></a><span data-ttu-id="cdef6-104">若要建立交易協議</span><span class="sxs-lookup"><span data-stu-id="cdef6-104">To create a trade agreement</span></span>  

1. <span data-ttu-id="cdef6-105">在  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開**BizTalk\<版本\>Accelerator for RosettaNet**，以滑鼠右鍵按一下**協議**，按一下**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="cdef6-105">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, right-click **Agreements**, click **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="cdef6-106">在 **新協議屬性**對話方塊的 **一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cdef6-106">In the **New Agreement Properties** dialog box, on the **General** tab, do the following:</span></span>  


   |         <span data-ttu-id="cdef6-107">使用</span><span class="sxs-lookup"><span data-stu-id="cdef6-107">Use this</span></span>          |                     <span data-ttu-id="cdef6-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cdef6-108">To do this</span></span>                     |
   |---------------------------|----------------------------------------------------|
   |         <span data-ttu-id="cdef6-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cdef6-109">**Name**</span></span>          |             <span data-ttu-id="cdef6-110">型別**交易協議**。</span><span class="sxs-lookup"><span data-stu-id="cdef6-110">Type **Trade Agreement**.</span></span>              |
   | <span data-ttu-id="cdef6-111">**程序組態**</span><span class="sxs-lookup"><span data-stu-id="cdef6-111">**Process Configuration**</span></span> | <span data-ttu-id="cdef6-112">選取  **STD_0C1_R01.02**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cdef6-112">Select **STD_0C1_R01.02** from the drop-down list.</span></span> |
   |    <span data-ttu-id="cdef6-113">**我的組織**</span><span class="sxs-lookup"><span data-stu-id="cdef6-113">**My organization**</span></span>    |      <span data-ttu-id="cdef6-114">選取 **首頁**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cdef6-114">Select **HOME** from the drop-down list.</span></span>      |
   | <span data-ttu-id="cdef6-115">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="cdef6-115">**Partner organization**</span></span>  |    <span data-ttu-id="cdef6-116">選取 **夥伴**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cdef6-116">Select **PARTNER** from the drop-down list.</span></span>     |
   |       <span data-ttu-id="cdef6-117">**主要角色**</span><span class="sxs-lookup"><span data-stu-id="cdef6-117">**Home role**</span></span>       |   <span data-ttu-id="cdef6-118">選取 **啟動器**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cdef6-118">Select **Initiator** from the drop-down list.</span></span>    |


3. <span data-ttu-id="cdef6-119">在 **新協議屬性**對話方塊的 **連接埠**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cdef6-119">In the **New Agreement Properties** dialog box, on the **Ports** tab, do the following:</span></span>  


   |    <span data-ttu-id="cdef6-120">使用</span><span class="sxs-lookup"><span data-stu-id="cdef6-120">Use this</span></span>    |                                         <span data-ttu-id="cdef6-121">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cdef6-121">To do this</span></span>                                         |
   |----------------|--------------------------------------------------------------------------------------------|
   | <span data-ttu-id="cdef6-122">**動作 URL**</span><span class="sxs-lookup"><span data-stu-id="cdef6-122">**Action URL**</span></span> |                   <span data-ttu-id="cdef6-123">型別**<http://localhost/BTARNApp/RNIFReceive.aspx>**。</span><span class="sxs-lookup"><span data-stu-id="cdef6-123">Type **<http://localhost/BTARNApp/RNIFReceive.aspx>**.</span></span>                   |
   | <span data-ttu-id="cdef6-124">**信號 URL**</span><span class="sxs-lookup"><span data-stu-id="cdef6-124">**Signal URL**</span></span> |                   <span data-ttu-id="cdef6-125">型別**<http://localhost/BTARNApp/RNIFReceive.aspx>**。</span><span class="sxs-lookup"><span data-stu-id="cdef6-125">Type **<http://localhost/BTARNApp/RNIFReceive.aspx>**.</span></span>                   |
   |  <span data-ttu-id="cdef6-126">**同步 URL**</span><span class="sxs-lookup"><span data-stu-id="cdef6-126">**Sync URL**</span></span>  | <span data-ttu-id="cdef6-127">保留空白。</span><span class="sxs-lookup"><span data-stu-id="cdef6-127">Leave blank.</span></span> <span data-ttu-id="cdef6-128">同步化交易夥伴介面程序 (PIP) 不需要「同步 URL」。</span><span class="sxs-lookup"><span data-stu-id="cdef6-128">Sync URL is not required for the synchronous Partner Interface Process (PIP).</span></span> |


4. <span data-ttu-id="cdef6-129">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cdef6-129">Click **Apply**, and then click **OK**.</span></span>  

   <span data-ttu-id="cdef6-130">建立交易協議之後，必須加以啟動。</span><span class="sxs-lookup"><span data-stu-id="cdef6-130">After you create the trade agreement, you must activate it.</span></span>  

### <a name="to-activate-the-trade-agreement"></a><span data-ttu-id="cdef6-131">啟動交易協議</span><span class="sxs-lookup"><span data-stu-id="cdef6-131">To activate the trade agreement</span></span>  

- <span data-ttu-id="cdef6-132">在 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，按一下**協議**，以滑鼠右鍵按一下**交易協議**在結果窗格中，然後按一下**啟動**.</span><span class="sxs-lookup"><span data-stu-id="cdef6-132">In the [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], click **Agreements**, right-click **Trade Agreement** in the results pane, and then click **Activate**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="cdef6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdef6-133">See Also</span></span>  
 [<span data-ttu-id="cdef6-134">步驟 5：建立鏡像協議</span><span class="sxs-lookup"><span data-stu-id="cdef6-134">Step 5: Create a Mirror Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)