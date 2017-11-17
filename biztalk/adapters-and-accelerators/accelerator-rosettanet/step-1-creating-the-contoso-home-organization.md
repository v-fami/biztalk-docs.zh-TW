---
title: "步驟 1： 建立 Contoso 主要組織 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating home organizations
- creating, home organizations
- home organizations, creating
ms.assetid: 0e7a53b9-ae59-4cd1-88bd-0ada7e65acba
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21e6afcc3aca274d968b15f2bbe93c2226e54a48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-the-contoso-home-organization"></a><span data-ttu-id="d9ad5-102">步驟 1： 建立 Contoso 主要組織</span><span class="sxs-lookup"><span data-stu-id="d9ad5-102">Step 1: Creating the Contoso Home Organization</span></span>
<span data-ttu-id="d9ad5-103">在這個步驟中，您會使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台來建立 Contoso 主要組織。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-103">In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create the Contoso home organization.</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="d9ad5-104">若要啟動 BTARN 管理主控台</span><span class="sxs-lookup"><span data-stu-id="d9ad5-104">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="d9ad5-105">在 Contoso 電腦上，按一下 **啟動**，指向 **所有程式**，指向**Microsoft BizTalk\<版本 > Accelerator for RosettaNet**然後按一下 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-105">On the Contoso computer, click **Start**, point to **All Programs**, point to **Microsoft  BizTalk \<version> Accelerator for RosettaNet** and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-home-organization"></a><span data-ttu-id="d9ad5-106">若要建立主要組織</span><span class="sxs-lookup"><span data-stu-id="d9ad5-106">To create the home organization</span></span>  
  
1.  <span data-ttu-id="d9ad5-107">在[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**主要組織**，指向 **新增**，然後按一下 **主要組織**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-107">In the [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Home Organizations**, point to **New**, and then click **Home Organization**.</span></span>  
  
2.  <span data-ttu-id="d9ad5-108">在 [新主要組織屬性] 對話方塊上**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d9ad5-108">In the New Home Organization Properties dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="d9ad5-109">使用</span><span class="sxs-lookup"><span data-stu-id="d9ad5-109">Use this</span></span>|<span data-ttu-id="d9ad5-110">動作</span><span class="sxs-lookup"><span data-stu-id="d9ad5-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d9ad5-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-111">**Name**</span></span>|<span data-ttu-id="d9ad5-112">型別**CONTOSO**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-112">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="d9ad5-113">**GBI**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-113">**GBI**</span></span>|<span data-ttu-id="d9ad5-114">型別**123456789**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-114">Type **123456789**.</span></span> <span data-ttu-id="d9ad5-115">**注意：**如果您在同一部電腦上執行回送教學課程，您必須輸入"123456789"以外的 GBI 值。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-115">**Note:**  If you have run the Loopback tutorial on the same computer, you will have to enter a value for GBI that is different than "123456789".</span></span>|  
    |<span data-ttu-id="d9ad5-116">**主要組織分類**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-116">**Home Organization Classification**</span></span>|<span data-ttu-id="d9ad5-117">選取**製造商**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-117">Select **Manufacturer** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="d9ad5-118">按一下**連絡人屬性**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d9ad5-118">Click the **Contact Properties** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="d9ad5-119">使用</span><span class="sxs-lookup"><span data-stu-id="d9ad5-119">Use this</span></span>|<span data-ttu-id="d9ad5-120">動作</span><span class="sxs-lookup"><span data-stu-id="d9ad5-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d9ad5-121">**連絡人名稱**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-121">**Contact Name**</span></span>|<span data-ttu-id="d9ad5-122">型別**John Doe**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-122">Type **John Doe**.</span></span>|  
    |<span data-ttu-id="d9ad5-123">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-123">**E-mail Address**</span></span>|<span data-ttu-id="d9ad5-124">型別 **jdoe@contoso.com** 。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-124">Type **jdoe@contoso.com**.</span></span>|  
    |<span data-ttu-id="d9ad5-125">**電話號碼**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-125">**Telephone Number**</span></span>|<span data-ttu-id="d9ad5-126">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-126">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="d9ad5-127">**傳真號碼**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-127">**Fax Number**</span></span>|<span data-ttu-id="d9ad5-128">型別**555-555-5555**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-128">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="d9ad5-129">**供應鏈代碼**</span><span class="sxs-lookup"><span data-stu-id="d9ad5-129">**Supply Chain Code**</span></span>|<span data-ttu-id="d9ad5-130">型別**Electronic Components**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-130">Type **Electronic Components**.</span></span>|  
  
4.  <span data-ttu-id="d9ad5-131">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d9ad5-131">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ad5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9ad5-132">See Also</span></span>  
 [<span data-ttu-id="d9ad5-133">步驟 2： 建立 Fabrikam 交易夥伴組織</span><span class="sxs-lookup"><span data-stu-id="d9ad5-133">Step 2: Creating the Fabrikam Partner Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-the-fabrikam-partner-organization.md)