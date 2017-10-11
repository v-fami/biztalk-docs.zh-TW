---
title: "步驟 2： 建立 Fabrikam 交易夥伴組織 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trading partners
- double action tutorial, creating partner organizations
- trading partners, partner organization
ms.assetid: 4d2ddc4c-2275-4faf-9a36-8a912cc06527
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3133f5e2ae7b3a234bef276af67afda391c1f7cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-the-fabrikam-partner-organization"></a><span data-ttu-id="7c615-102">步驟 2： 建立 Fabrikam 交易夥伴組織</span><span class="sxs-lookup"><span data-stu-id="7c615-102">Step 2: Creating the Fabrikam Partner Organization</span></span>
<span data-ttu-id="7c615-103">在這個步驟中，您會使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台來建立新的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="7c615-103">In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create a new trading partner.</span></span> <span data-ttu-id="7c615-104">這個教學課程中的交易夥伴是 Fabrikam 組織。</span><span class="sxs-lookup"><span data-stu-id="7c615-104">The trading partner for this tutorial is the Fabrikam organization.</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="7c615-105">若要啟動 BTARN 管理主控台</span><span class="sxs-lookup"><span data-stu-id="7c615-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="7c615-106">在 Contoso 電腦上，按一下 **啟動**，指向**所有程式**，指向**Microsoft BizTalk\<版本 > Accelerator for RosettaNet**，然後按一下按一下 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="7c615-106">On the Contoso computer, click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-fabrikam-as-a-trading-partner"></a><span data-ttu-id="7c615-107">若要建立 Fabrikam 為交易夥伴</span><span class="sxs-lookup"><span data-stu-id="7c615-107">To create Fabrikam as a trading partner</span></span>  
  
1.  <span data-ttu-id="7c615-108">在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**夥伴**，指向 **新增**，然後按一下**夥伴**.</span><span class="sxs-lookup"><span data-stu-id="7c615-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Partners**, point to **New**, and then click **Partner**.</span></span>  
  
2.  <span data-ttu-id="7c615-109">在 [新交易夥伴屬性] 對話方塊上**一般**索引標籤上，執行下列動作**:**</span><span class="sxs-lookup"><span data-stu-id="7c615-109">In the New Partner Properties dialog box, on the **General** tab, do the following**:**</span></span>  
  
    |<span data-ttu-id="7c615-110">使用</span><span class="sxs-lookup"><span data-stu-id="7c615-110">Use this</span></span>|<span data-ttu-id="7c615-111">動作</span><span class="sxs-lookup"><span data-stu-id="7c615-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7c615-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7c615-112">**Name**</span></span>|<span data-ttu-id="7c615-113">型別**FABRIKAM**。</span><span class="sxs-lookup"><span data-stu-id="7c615-113">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="7c615-114">**GBI**</span><span class="sxs-lookup"><span data-stu-id="7c615-114">**GBI**</span></span>|<span data-ttu-id="7c615-115">型別**987654321**。</span><span class="sxs-lookup"><span data-stu-id="7c615-115">Type **987654321**.</span></span> <span data-ttu-id="7c615-116">**注意：**如果您在同一部電腦上執行回送教學課程，您必須輸入"987654321"以外的 GBI 值。</span><span class="sxs-lookup"><span data-stu-id="7c615-116">**Note:**  If you have run the Loopback tutorial on the same computer, you will have to enter a value for GBI that is different than "987654321".</span></span>|  
    |<span data-ttu-id="7c615-117">**夥伴分類**</span><span class="sxs-lookup"><span data-stu-id="7c615-117">**Partner Classification**</span></span>|<span data-ttu-id="7c615-118">選取**購物者**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="7c615-118">Select **Shopper** from the drop-down list.</span></span>|  
    |<span data-ttu-id="7c615-119">**簽章憑證**</span><span class="sxs-lookup"><span data-stu-id="7c615-119">**Signature Certificate**</span></span>|<span data-ttu-id="7c615-120">選取**Fabrikam Signature [憑證指紋]**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="7c615-120">Select **Fabrikam Signature [Thumbprint]** from the drop-down list.</span></span>|  
    |<span data-ttu-id="7c615-121">**加密憑證**</span><span class="sxs-lookup"><span data-stu-id="7c615-121">**Encryption Certificate**</span></span>|<span data-ttu-id="7c615-122">選取**Fabrikam Encryption [憑證指紋]**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="7c615-122">Select **Fabrikam Encryption [Thumbprint]** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="7c615-123">按一下**連絡人屬性**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7c615-123">Click the **Contact Properties** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="7c615-124">使用</span><span class="sxs-lookup"><span data-stu-id="7c615-124">Use this</span></span>|<span data-ttu-id="7c615-125">動作</span><span class="sxs-lookup"><span data-stu-id="7c615-125">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7c615-126">**連絡人名稱**</span><span class="sxs-lookup"><span data-stu-id="7c615-126">**Contact Name**</span></span>|<span data-ttu-id="7c615-127">型別**Jane Doe**。</span><span class="sxs-lookup"><span data-stu-id="7c615-127">Type **Jane Doe**.</span></span>|  
    |<span data-ttu-id="7c615-128">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="7c615-128">**E-mail Address**</span></span>|<span data-ttu-id="7c615-129">型別 **jdoe@fabrikam.com** 。</span><span class="sxs-lookup"><span data-stu-id="7c615-129">Type **jdoe@fabrikam.com**.</span></span>|  
    |<span data-ttu-id="7c615-130">**電話號碼**</span><span class="sxs-lookup"><span data-stu-id="7c615-130">**Telephone Number**</span></span>|<span data-ttu-id="7c615-131">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="7c615-131">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="7c615-132">**傳真號碼**</span><span class="sxs-lookup"><span data-stu-id="7c615-132">**Fax Number**</span></span>|<span data-ttu-id="7c615-133">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="7c615-133">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="7c615-134">**供應鏈代碼**</span><span class="sxs-lookup"><span data-stu-id="7c615-134">**Supply chain code**</span></span>|<span data-ttu-id="7c615-135">型別**Electronic Components**。</span><span class="sxs-lookup"><span data-stu-id="7c615-135">Type **Electronic Components**.</span></span>|  
  
4.  <span data-ttu-id="7c615-136">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7c615-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c615-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c615-137">See Also</span></span>  
 [<span data-ttu-id="7c615-138">步驟 3： 建立 Contoso 0 C 2 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="7c615-138">Step 3: Creating the Contoso 0C2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-contoso-0c2-trading-partner-agreement.md)