---
title: 步驟 2： 建立 Contoso 交易夥伴組織 |Microsoft Docs
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
ms.openlocfilehash: 97e811493c1347bc016671469da8a0dc18483e85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969775"
---
# <a name="step-2-creating-the-contoso-partner-organization"></a><span data-ttu-id="bb104-102">步驟 2： 建立 Contoso 交易夥伴組織</span><span class="sxs-lookup"><span data-stu-id="bb104-102">Step 2: Creating the Contoso Partner Organization</span></span>
<span data-ttu-id="bb104-103">在此步驟中，您可以使用 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]管理主控台來建立新的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="bb104-103">In this step, you use the Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create a new trading partner.</span></span> <span data-ttu-id="bb104-104">這個教學課程中的交易夥伴是 Contoso 組織。</span><span class="sxs-lookup"><span data-stu-id="bb104-104">The trading partner for this tutorial is the Contoso organization.</span></span>  

### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="bb104-105">若要啟動 BTARN 管理主控台</span><span class="sxs-lookup"><span data-stu-id="bb104-105">To start the BTARN Management Console</span></span>  

- <span data-ttu-id="bb104-106">按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="bb104-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  

### <a name="to-create-fabrikam-as-a-trading-partner"></a><span data-ttu-id="bb104-107">若要建立 Fabrikam 為交易夥伴</span><span class="sxs-lookup"><span data-stu-id="bb104-107">To create Fabrikam as a trading partner</span></span>  

1. <span data-ttu-id="bb104-108">在**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**夥伴**，指向 **新增**，然後按一下**夥伴**.</span><span class="sxs-lookup"><span data-stu-id="bb104-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Partners**, point to **New**, and then click **Partner**.</span></span>  

2. <span data-ttu-id="bb104-109">在 [新交易夥伴屬性] 對話方塊中，在**一般**索引標籤上，執行下列<strong>:</strong></span><span class="sxs-lookup"><span data-stu-id="bb104-109">In the New Partner Properties dialog box, on the **General** tab, do the following<strong>:</strong></span></span>  


   |          <span data-ttu-id="bb104-110">使用</span><span class="sxs-lookup"><span data-stu-id="bb104-110">Use this</span></span>          |                             <span data-ttu-id="bb104-111">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="bb104-111">To do this</span></span>                              |
   |----------------------------|---------------------------------------------------------------------|
   |          <span data-ttu-id="bb104-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="bb104-112">**Name**</span></span>          |                          <span data-ttu-id="bb104-113">型別**CONTOSO**。</span><span class="sxs-lookup"><span data-stu-id="bb104-113">Type **CONTOSO**.</span></span>                          |
   |          <span data-ttu-id="bb104-114">**GBI**</span><span class="sxs-lookup"><span data-stu-id="bb104-114">**GBI**</span></span>           |                         <span data-ttu-id="bb104-115">型別**123456789**。</span><span class="sxs-lookup"><span data-stu-id="bb104-115">Type **123456789**.</span></span>                         |
   | <span data-ttu-id="bb104-116">**夥伴分類**</span><span class="sxs-lookup"><span data-stu-id="bb104-116">**Partner Classification**</span></span> |          <span data-ttu-id="bb104-117">選取 **製造商**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="bb104-117">Select **Manufacturer** from the drop-down list.</span></span>           |
   | <span data-ttu-id="bb104-118">**簽章憑證**</span><span class="sxs-lookup"><span data-stu-id="bb104-118">**Signature Certificate**</span></span>  | <span data-ttu-id="bb104-119">選取  **Contoso Signature [憑證指紋]** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="bb104-119">Select **Contoso Signature [Thumbprint]** from the drop-down list.</span></span>  |
   | <span data-ttu-id="bb104-120">**加密憑證**</span><span class="sxs-lookup"><span data-stu-id="bb104-120">**Encryption Certificate**</span></span> | <span data-ttu-id="bb104-121">選取  **Contoso Encryption [憑證指紋]** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="bb104-121">Select **Contoso Encryption [Thumbprint]** from the drop-down list.</span></span> |


3. <span data-ttu-id="bb104-122">按一下 **連絡人屬性**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bb104-122">Click the **Contact Properties** tab, and then do the following:</span></span>  


   |       <span data-ttu-id="bb104-123">使用</span><span class="sxs-lookup"><span data-stu-id="bb104-123">Use this</span></span>        |               <span data-ttu-id="bb104-124">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="bb104-124">To do this</span></span>                |
   |-----------------------|-----------------------------------------|
   |   <span data-ttu-id="bb104-125">**連絡人名稱**</span><span class="sxs-lookup"><span data-stu-id="bb104-125">**Contact Name**</span></span>    |           <span data-ttu-id="bb104-126">型別**John Doe**。</span><span class="sxs-lookup"><span data-stu-id="bb104-126">Type **John Doe**.</span></span>            |
   |  <span data-ttu-id="bb104-127">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="bb104-127">**E-mail Address**</span></span>   | <span data-ttu-id="bb104-128">型別<strong>jdoe@contoso.com</strong>。</span><span class="sxs-lookup"><span data-stu-id="bb104-128">Type <strong>jdoe@contoso.com</strong>.</span></span> |
   | <span data-ttu-id="bb104-129">**電話號碼**</span><span class="sxs-lookup"><span data-stu-id="bb104-129">**Telephone Number**</span></span>  |         <span data-ttu-id="bb104-130">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="bb104-130">Type **555-555-5555**.</span></span>          |
   |    <span data-ttu-id="bb104-131">**傳真號碼**</span><span class="sxs-lookup"><span data-stu-id="bb104-131">**Fax Number**</span></span>     |         <span data-ttu-id="bb104-132">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="bb104-132">Type **555-555-5555**.</span></span>          |
   | <span data-ttu-id="bb104-133">**供應鏈代碼**</span><span class="sxs-lookup"><span data-stu-id="bb104-133">**Supply chain code**</span></span> |     <span data-ttu-id="bb104-134">型別**Electronic Components**。</span><span class="sxs-lookup"><span data-stu-id="bb104-134">Type **Electronic Components**.</span></span>     |


4. <span data-ttu-id="bb104-135">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="bb104-135">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="bb104-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb104-136">See Also</span></span>  
 [<span data-ttu-id="bb104-137">步驟 3：建立 Fabrikam 0C2 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="bb104-137">Step 3: Creating the Fabrikam 0C2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-fabrikam-0c2-trading-partner-agreement.md)