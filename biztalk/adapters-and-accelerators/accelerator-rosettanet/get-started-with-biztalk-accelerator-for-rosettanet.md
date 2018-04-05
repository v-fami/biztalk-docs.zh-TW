---
title: 開始使用 BizTalk Accelerator for RosettaNet |Microsoft 文件
description: 請參閱提供的教學課程可協助了解並開始使用 BizTalk Server 中的 RosettaNet 加速器 (BTARN)
caps.latest.revision: 7
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btarn.configuration.introduction
ms.assetid: 28a8942c-b461-4b2f-bc1f-1fc22cd08882
ms.author: mandia
ms.openlocfilehash: 156153010a4ee9caa5cb02535d516e05e49a21fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-biztalk-accelerator-for-rosettanet"></a><span data-ttu-id="e3166-103">開始使用 BizTalk Accelerator for RosettaNet</span><span class="sxs-lookup"><span data-stu-id="e3166-103">Get started with BizTalk Accelerator for RosettaNet</span></span>
<span data-ttu-id="e3166-104">Microsoft BizTalk Accelerator for RosettaNet (BTARN) 來簡化開發和部署的 RosettaNet 標準架構整合解決方案。</span><span class="sxs-lookup"><span data-stu-id="e3166-104">The Microsoft BizTalk Accelerator for RosettaNet (BTARN) streamlines the development and deployment of RosettaNet standards-based integration solutions.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="e3166-105">支援 RosettaNet 實作架構 (RNIF) 1.1 和 2.0.01 版。</span><span class="sxs-lookup"><span data-stu-id="e3166-105"> supports the RosettaNet Implementation Framework (RNIF) versions 1.1 and 2.0.01.</span></span> <span data-ttu-id="e3166-106">RNIF 是開放型的網路應用程式架構，可讓商務夥伴協同執行 RosettaNet 夥伴介面程序 (PIP)。</span><span class="sxs-lookup"><span data-stu-id="e3166-106">RNIF is an open network application framework that enables business partners to collaboratively run RosettaNet Partner Interface Processes (PIPs).</span></span> <span data-ttu-id="e3166-107">請參閱[GS1 美國](http://go.microsoft.com/fwlink/?LinkID=33859)如需有關 RosettaNet 標準。</span><span class="sxs-lookup"><span data-stu-id="e3166-107">See [GS1 US](http://go.microsoft.com/fwlink/?LinkID=33859) for more information about RosettaNet standard.</span></span>
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="e3166-108"> 同時支援化學資料交換 (CIDX) 電子化標準的交換作業。</span><span class="sxs-lookup"><span data-stu-id="e3166-108"> also supports the exchange of Chemical Data Exchange (CIDX) Chem eStandards.</span></span>  
  
<span data-ttu-id="e3166-109">本節提供有關如何使用 BizTalk Server 與 RosettaNet 加速器在公司內企業應用程式整合 (EAI)，以及在商務夥伴將自動化企業對企業採購角色專屬資訊解決方案。</span><span class="sxs-lookup"><span data-stu-id="e3166-109">This section provides role-specific information about how you can use BizTalk Server and the RosettaNet accelerator in your company for enterprise application integration (EAI), and among business partners to automate business-to-business procurement solutions.</span></span>  

## <a name="loopback-tutorial"></a><span data-ttu-id="e3166-110">回送教學課程</span><span class="sxs-lookup"><span data-stu-id="e3166-110">Loopback tutorial</span></span>

<span data-ttu-id="e3166-111">包含描述如何使用模擬單一電腦上的主要及交易夥伴組織之間的程序實作 RosettaNet 加速器的詳細的步驟。</span><span class="sxs-lookup"><span data-stu-id="e3166-111">Includes detailed steps that describe how to use the RosettaNet accelerator to simulate a process implementation between the home and partner organization on a single computer.</span></span>

<span data-ttu-id="e3166-112">在此教學課程中，您將建立主要組織、交易夥伴組織、交易協議、使用回送公用程式建立鏡像協議，並且執行範例程序以確認回送實例。</span><span class="sxs-lookup"><span data-stu-id="e3166-112">In this tutorial, you create a home organization, a partner organization, a trade agreement, use the Loopback utility to create a mirror agreement, and then run a sample process to verify the loop-back scenario.</span></span>

<span data-ttu-id="e3166-113">移至[回送教學課程](loopback-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e3166-113">Go to [Loopback tutorial](loopback-tutorial.md).</span></span> 

## <a name="double-action-tutorial"></a><span data-ttu-id="e3166-114">雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="e3166-114">Double action tutorial</span></span>

<span data-ttu-id="e3166-115">使用 RosettaNet 加速器的端對端解決方案。</span><span class="sxs-lookup"><span data-stu-id="e3166-115">An end-to-end solution using the RosettaNet accelerator.</span></span> <span data-ttu-id="e3166-116">本教學課程詳細說明的步驟，以建立交易夥伴實例兩家虛構公司之間實作 RosettaNet 相容解決方案： Contoso，供應商的組織和與買方組織 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="e3166-116">The tutorial details the steps to implement a RosettaNet-compliant solution by creating a trading partner scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>

<span data-ttu-id="e3166-117">其中包括使用 BTARN 管理主控台中，建立特定業務 (LOB) 應用程式，以及建立自訂協調流程。</span><span class="sxs-lookup"><span data-stu-id="e3166-117">It includes working with the BTARN Management Console, creating line-of-business (LOB) applications, and creating custom orchestrations.</span></span>

<span data-ttu-id="e3166-118">移至[雙向動作教學課程](double-action-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e3166-118">Go to [Double action tutorial](double-action-tutorial.md).</span></span> 


## <a name="private-process-tutorial"></a><span data-ttu-id="e3166-119">私用程序教學課程</span><span class="sxs-lookup"><span data-stu-id="e3166-119">Private process tutorial</span></span>
<span data-ttu-id="e3166-120">使用 RosettaNet 加速器的端對端解決方案。</span><span class="sxs-lookup"><span data-stu-id="e3166-120">An end-to-end solution using the RosettaNet accelerator.</span></span> <span data-ttu-id="e3166-121">本教學課程詳細說明的步驟，以建立交易實例兩家虛構公司之間實作 RosettaNet 相容解決方案： Contoso，供應商的組織和與買方組織 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="e3166-121">The tutorial details the steps to implement a RosettaNet-compliant solution by creating a trading scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>

<span data-ttu-id="e3166-122">其中摘列建立 RosettaNet 架構解決方案的各種不同層面，包括整合 ERP、強制執行商務原則、自訂私用程序及升級安全通訊。</span><span class="sxs-lookup"><span data-stu-id="e3166-122">It outlines various aspects of creating a RosettaNet-based solution, including ERP integration, business policy enforcement, private process customization, and promoting secure communication.</span></span>

<span data-ttu-id="e3166-123">移至[私用程序教學課程](private-process-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="e3166-123">Go to [Private process tutorial](private-process-tutorial.md)</span></span>


## <a name="tutorial-links"></a><span data-ttu-id="e3166-124">教學課程的連結</span><span class="sxs-lookup"><span data-stu-id="e3166-124">Tutorial Links</span></span>
[<span data-ttu-id="e3166-125">回送教學課程</span><span class="sxs-lookup"><span data-stu-id="e3166-125">Loopback tutorial</span></span>](loopback-tutorial.md)  
[<span data-ttu-id="e3166-126">雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="e3166-126">Double action tutorial</span></span>](double-action-tutorial.md)  
[<span data-ttu-id="e3166-127">私用程序教學課程</span><span class="sxs-lookup"><span data-stu-id="e3166-127">Private process tutorial</span></span>](private-process-tutorial.md)

## <a name="see-also"></a><span data-ttu-id="e3166-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3166-128">See also</span></span>
[<span data-ttu-id="e3166-129">殘障人士的協助工具</span><span class="sxs-lookup"><span data-stu-id="e3166-129">Accessibility for People with Disabilities</span></span>](accessibility-for-people-with-disabilities3.md)