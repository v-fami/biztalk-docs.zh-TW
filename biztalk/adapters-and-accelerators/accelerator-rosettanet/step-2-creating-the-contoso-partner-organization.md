---
title: 步驟 2： 建立 Contoso 交易夥伴組織 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating partner organizations
ms.assetid: ebb3b166-3781-40b9-89d4-2ca0c83d05f3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5d3f29a2a369f37589f3356da1a1183d8cb91b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-creating-the-contoso-partner-organization"></a><span data-ttu-id="3c75b-102">步驟 2： 建立 Contoso 交易夥伴組織</span><span class="sxs-lookup"><span data-stu-id="3c75b-102">Step 2: Creating the Contoso Partner Organization</span></span>
<span data-ttu-id="3c75b-103">在這個步驟中，您會使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台來建立新的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="3c75b-103">In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create a new trading partner.</span></span> <span data-ttu-id="3c75b-104">這個教學課程中的交易夥伴是 Contoso 組織。</span><span class="sxs-lookup"><span data-stu-id="3c75b-104">The trading partner for this tutorial is the Contoso organization.</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="3c75b-105">若要啟動 BTARN 管理主控台</span><span class="sxs-lookup"><span data-stu-id="3c75b-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="3c75b-106">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="3c75b-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-fabrikam-as-a-trading-partner"></a><span data-ttu-id="3c75b-107">若要建立 Fabrikam 為交易夥伴</span><span class="sxs-lookup"><span data-stu-id="3c75b-107">To create Fabrikam as a trading partner</span></span>  
  
1.  <span data-ttu-id="3c75b-108">在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**夥伴**，指向 **新增**，然後按一下**夥伴**.</span><span class="sxs-lookup"><span data-stu-id="3c75b-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Partners**, point to **New**, and then click **Partner**.</span></span>  
  
2.  <span data-ttu-id="3c75b-109">在 [新交易夥伴屬性] 對話方塊上**一般**索引標籤上，執行下列動作**:**</span><span class="sxs-lookup"><span data-stu-id="3c75b-109">In the New Partner Properties dialog box, on the **General** tab, do the following**:**</span></span>  
  
    |<span data-ttu-id="3c75b-110">使用</span><span class="sxs-lookup"><span data-stu-id="3c75b-110">Use this</span></span>|<span data-ttu-id="3c75b-111">動作</span><span class="sxs-lookup"><span data-stu-id="3c75b-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3c75b-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="3c75b-112">**Name**</span></span>|<span data-ttu-id="3c75b-113">型別**CONTOSO**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-113">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="3c75b-114">**GBI**</span><span class="sxs-lookup"><span data-stu-id="3c75b-114">**GBI**</span></span>|<span data-ttu-id="3c75b-115">型別**123456789**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-115">Type **123456789**.</span></span>|  
    |<span data-ttu-id="3c75b-116">**夥伴分類**</span><span class="sxs-lookup"><span data-stu-id="3c75b-116">**Partner Classification**</span></span>|<span data-ttu-id="3c75b-117">選取**製造商**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c75b-117">Select **Manufacturer** from the drop-down list.</span></span>|  
    |<span data-ttu-id="3c75b-118">**簽章憑證**</span><span class="sxs-lookup"><span data-stu-id="3c75b-118">**Signature Certificate**</span></span>|<span data-ttu-id="3c75b-119">選取**Contoso Signature [憑證指紋]**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c75b-119">Select **Contoso Signature [Thumbprint]** from the drop-down list.</span></span>|  
    |<span data-ttu-id="3c75b-120">**加密憑證**</span><span class="sxs-lookup"><span data-stu-id="3c75b-120">**Encryption Certificate**</span></span>|<span data-ttu-id="3c75b-121">選取**Contoso Encryption [憑證指紋]**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3c75b-121">Select **Contoso Encryption [Thumbprint]** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="3c75b-122">按一下**連絡人屬性**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3c75b-122">Click the **Contact Properties** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="3c75b-123">使用</span><span class="sxs-lookup"><span data-stu-id="3c75b-123">Use this</span></span>|<span data-ttu-id="3c75b-124">動作</span><span class="sxs-lookup"><span data-stu-id="3c75b-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3c75b-125">**連絡人名稱**</span><span class="sxs-lookup"><span data-stu-id="3c75b-125">**Contact Name**</span></span>|<span data-ttu-id="3c75b-126">型別**John Doe**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-126">Type **John Doe**.</span></span>|  
    |<span data-ttu-id="3c75b-127">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="3c75b-127">**E-mail Address**</span></span>|<span data-ttu-id="3c75b-128">型別 **jdoe@contoso.com** 。</span><span class="sxs-lookup"><span data-stu-id="3c75b-128">Type **jdoe@contoso.com**.</span></span>|  
    |<span data-ttu-id="3c75b-129">**電話號碼**</span><span class="sxs-lookup"><span data-stu-id="3c75b-129">**Telephone Number**</span></span>|<span data-ttu-id="3c75b-130">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-130">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="3c75b-131">**傳真號碼**</span><span class="sxs-lookup"><span data-stu-id="3c75b-131">**Fax Number**</span></span>|<span data-ttu-id="3c75b-132">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-132">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="3c75b-133">**供應鏈代碼**</span><span class="sxs-lookup"><span data-stu-id="3c75b-133">**Supply chain code**</span></span>|<span data-ttu-id="3c75b-134">型別**Electronic Components**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-134">Type **Electronic Components**.</span></span>|  
  
4.  <span data-ttu-id="3c75b-135">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3c75b-135">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c75b-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c75b-136">See Also</span></span>  
 [<span data-ttu-id="3c75b-137">步驟 3：建立 Fabrikam 0C2 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="3c75b-137">Step 3: Creating the Fabrikam 0C2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-fabrikam-0c2-trading-partner-agreement.md)