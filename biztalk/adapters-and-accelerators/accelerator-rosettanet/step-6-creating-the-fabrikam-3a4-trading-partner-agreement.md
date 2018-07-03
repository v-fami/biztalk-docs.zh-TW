---
title: 步驟 6： 建立 Fabrikam 3A4 交易夥伴協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating agreements
ms.assetid: 6ccd2414-a1d4-460e-9529-65b2d30cfca6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a533f00835b8f2200c539baa0e27fbe51ad2c5f6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009543"
---
# <a name="step-6-creating-the-fabrikam-3a4-trading-partner-agreement"></a><span data-ttu-id="12f4e-102">步驟 6： 建立 Fabrikam 3A4 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="12f4e-102">Step 6: Creating the Fabrikam 3A4 Trading Partner Agreement</span></span>
<span data-ttu-id="12f4e-103">在此步驟中，您會建立 Contoso 與 Fabrikam 使用 Microsoft® 之間的交易夥伴協議[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="12f4e-103">In this step, you create a trading partner agreement between Contoso and Fabrikam using the Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span> <span data-ttu-id="12f4e-104">您將為 3A4 交易夥伴介面程序 (PIP) 建立新的交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="12f4e-104">You create a new trading partner agreement for the 3A4 Partner Interface Process (PIP).</span></span>  

### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="12f4e-105">若要啟動 BTARN 管理主控台</span><span class="sxs-lookup"><span data-stu-id="12f4e-105">To start the BTARN Management Console</span></span>  

- <span data-ttu-id="12f4e-106">按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="12f4e-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  

### <a name="to-create-the-3a4-trading-partner-agreement"></a><span data-ttu-id="12f4e-107">若要建立 3A4 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="12f4e-107">To create the 3A4 trading partner agreement</span></span>  

1. <span data-ttu-id="12f4e-108">在**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**協議**，指向 **新增**，然後按一下 **協議**.</span><span class="sxs-lookup"><span data-stu-id="12f4e-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="12f4e-109">在 **新協議屬性**對話方塊的 **一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="12f4e-109">In the **New Agreement Properties** dialog box, on the **General** tab, do the following:</span></span>  


   |         <span data-ttu-id="12f4e-110">使用</span><span class="sxs-lookup"><span data-stu-id="12f4e-110">Use this</span></span>          |                      <span data-ttu-id="12f4e-111">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="12f4e-111">To do this</span></span>                       |
   |---------------------------|-------------------------------------------------------|
   |         <span data-ttu-id="12f4e-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="12f4e-112">**Name**</span></span>          |           <span data-ttu-id="12f4e-113">型別**Fabrikam_To_Contoso_3A4**。</span><span class="sxs-lookup"><span data-stu-id="12f4e-113">Type **Fabrikam_To_Contoso_3A4**.</span></span>           |
   | <span data-ttu-id="12f4e-114">**程序組態**</span><span class="sxs-lookup"><span data-stu-id="12f4e-114">**Process Configuration**</span></span> |  <span data-ttu-id="12f4e-115">選取  **STD_3A4_V02.02**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="12f4e-115">Select **STD_3A4_V02.02** from the drop-down list.</span></span>   |
   |    <span data-ttu-id="12f4e-116">**我的組織**</span><span class="sxs-lookup"><span data-stu-id="12f4e-116">**My Organization**</span></span>    |     <span data-ttu-id="12f4e-117">選取  **Fabrikam**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="12f4e-117">Select **Fabrikam** from the drop-down list.</span></span>      |
   | <span data-ttu-id="12f4e-118">**夥伴組織**</span><span class="sxs-lookup"><span data-stu-id="12f4e-118">**Partner Organization**</span></span>  |      <span data-ttu-id="12f4e-119">選取  **Contoso**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="12f4e-119">Select **Contoso** from the drop-down list.</span></span>      |
   |     <span data-ttu-id="12f4e-120">**RNIF 版本**</span><span class="sxs-lookup"><span data-stu-id="12f4e-120">**RNIF Version**</span></span>      |     <span data-ttu-id="12f4e-121">選取  **V02.00.01**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="12f4e-121">Select **V02.00.01** from the drop-down list.</span></span>     |
   |       <span data-ttu-id="12f4e-122">**主要角色**</span><span class="sxs-lookup"><span data-stu-id="12f4e-122">**Home Role**</span></span>       | <span data-ttu-id="12f4e-123">選取 **買方 （啟動者）** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="12f4e-123">Select **Buyer (Initiator)** from the drop-down list.</span></span> |
   |         <span data-ttu-id="12f4e-124">**Usage**</span><span class="sxs-lookup"><span data-stu-id="12f4e-124">**Usage**</span></span>         |       <span data-ttu-id="12f4e-125">選取 **測試**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="12f4e-125">Select **Test** from the drop-down list.</span></span>        |


3. <span data-ttu-id="12f4e-126">在 **連接埠**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="12f4e-126">On the **Ports** tab, do the following:</span></span>  


   |    <span data-ttu-id="12f4e-127">使用</span><span class="sxs-lookup"><span data-stu-id="12f4e-127">Use this</span></span>    |                          <span data-ttu-id="12f4e-128">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="12f4e-128">To do this</span></span>                           |
   |----------------|---------------------------------------------------------------|
   | <span data-ttu-id="12f4e-129">**動作 URL**</span><span class="sxs-lookup"><span data-stu-id="12f4e-129">**Action URL**</span></span> | <span data-ttu-id="12f4e-130">型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。</span><span class="sxs-lookup"><span data-stu-id="12f4e-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span> |
   | <span data-ttu-id="12f4e-131">**信號 URL**</span><span class="sxs-lookup"><span data-stu-id="12f4e-131">**Signal URL**</span></span> | <span data-ttu-id="12f4e-132">型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。</span><span class="sxs-lookup"><span data-stu-id="12f4e-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span> |
   |  <span data-ttu-id="12f4e-133">**同步 URL**</span><span class="sxs-lookup"><span data-stu-id="12f4e-133">**Sync URL**</span></span>  | <span data-ttu-id="12f4e-134">型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。</span><span class="sxs-lookup"><span data-stu-id="12f4e-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span> |


4. <span data-ttu-id="12f4e-135">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="12f4e-135">Click **OK**.</span></span>  

5. <span data-ttu-id="12f4e-136">以滑鼠右鍵按一下**Fabrikam_To_Contoso_3A4**協議，然後按一下**Activate**。</span><span class="sxs-lookup"><span data-stu-id="12f4e-136">Right-click the **Fabrikam_To_Contoso_3A4** agreement and then click **Activate**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="12f4e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12f4e-137">See Also</span></span>  
 [<span data-ttu-id="12f4e-138">步驟 7：建置與部署 LOBWebApplication SDK 範例</span><span class="sxs-lookup"><span data-stu-id="12f4e-138">Step 7: Building and Deploying the LOBWebApplication SDK Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-building-and-deploying-the-lobwebapplication-sdk-sample.md)