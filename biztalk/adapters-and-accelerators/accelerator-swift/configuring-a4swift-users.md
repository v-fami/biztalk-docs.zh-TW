---
title: 設定 A4SWIFT 使用者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, user accounts
- creating, user accounts
- user accounts, creating
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b75a3e95c836f8a577543b43319e6abe49a96c42
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005255"
---
# <a name="configuring-a4swift-users"></a><span data-ttu-id="fc7d9-102">設定 A4SWIFT 使用者</span><span class="sxs-lookup"><span data-stu-id="fc7d9-102">Configuring A4SWIFT Users</span></span>
<span data-ttu-id="fc7d9-103">在安裝期間[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]，A4SWIFT 組態程式會建立預設交易夥伴設定檔和協議，並註冊 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-103">During installation of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], the A4SWIFT configuration program creates default trading partner profiles and agreements, and registers the BizTalk Server.</span></span> <span data-ttu-id="fc7d9-104">A4SWIFT 也會建立 Message Repair 和 New Submission 元件所使用的文件庫。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-104">A4SWIFT also creates document libraries used by the Message Repair and New Submission component.</span></span>  
  
 <span data-ttu-id="fc7d9-105">A4SWIFT 安裝期間建立下列的文件資料夾：</span><span class="sxs-lookup"><span data-stu-id="fc7d9-105">A4SWIFT creates the following document folders during installation:</span></span>  
  
- <span data-ttu-id="fc7d9-106">寄件匣文件庫</span><span class="sxs-lookup"><span data-stu-id="fc7d9-106">Outbox document library</span></span>  
  
- <span data-ttu-id="fc7d9-107">範本文件庫</span><span class="sxs-lookup"><span data-stu-id="fc7d9-107">Templates document library</span></span>  
  
- <span data-ttu-id="fc7d9-108">未剖析的文件庫</span><span class="sxs-lookup"><span data-stu-id="fc7d9-108">Unparsed document library</span></span>  
  
- <span data-ttu-id="fc7d9-109">新增 SWIFT MT 訊息文件庫</span><span class="sxs-lookup"><span data-stu-id="fc7d9-109">New SWIFT MT Message document library</span></span>  
  
- <span data-ttu-id="fc7d9-110">新增 SWIFT MX 訊息文件庫</span><span class="sxs-lookup"><span data-stu-id="fc7d9-110">New SWIFT MX Messages document library</span></span>  
  
  <span data-ttu-id="fc7d9-111">每個部門建立，A4SWIFT 系統管理員必須手動設定網站群組對應的部門，和 A4SWIFT 定義的角色。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-111">For each department created, the A4SWIFT Administrator must manually set up site groups for the corresponding departments and A4SWIFT defined roles.</span></span> <span data-ttu-id="fc7d9-112">每個部門/角色有自動建立設定檔 Web Client(PWC) 收件匣。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-112">Each department/role has an inbox created automatically by the Profile Web Client(PWC).</span></span>  
  
  <span data-ttu-id="fc7d9-113">A4SWIFT 安裝組態程式完成之後，A4SWIFT 系統管理員會設定在組織中的每個部門的工作流程。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-113">After the A4SWIFT setup configuration program is completed, the A4SWIFT Administrator configures workflows for each department in the organization.</span></span> <span data-ttu-id="fc7d9-114">Message Repair 和 New Submission 在設定期間，透過設定檔的 Web 用戶端，相對應的收件匣會針對每個部門/角色組合。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-114">During Message Repair and New Submission configuration, through the Profile Web Client, corresponding inboxes are created for each department/role combination.</span></span> <span data-ttu-id="fc7d9-115">比方說，PWC 組態期間 A4SWIFT 系統管理員會建立名為付款的部門使用，然後將 Creators Repairers 及核准者的角色指派給稱為付款的部門。</span><span class="sxs-lookup"><span data-stu-id="fc7d9-115">For example, during PWC configuration an A4SWIFT Administrator creates a department named Payments and then assigns the roles of Creators, Repairers, and Approvers to a department called Payments.</span></span> <span data-ttu-id="fc7d9-116">下表中的範例所示，MRSR 網站上的文件庫會建立與收件匣名稱：</span><span class="sxs-lookup"><span data-stu-id="fc7d9-116">Document libraries on the MRSR site are created with the inbox names as shown in the examples in the following table:</span></span>  
  
|<span data-ttu-id="fc7d9-117">部門名稱</span><span class="sxs-lookup"><span data-stu-id="fc7d9-117">Department name</span></span>|<span data-ttu-id="fc7d9-118">角色名稱</span><span class="sxs-lookup"><span data-stu-id="fc7d9-118">Role name</span></span>|<span data-ttu-id="fc7d9-119">收件匣名稱</span><span class="sxs-lookup"><span data-stu-id="fc7d9-119">Inbox name</span></span>|  
|---------------------|---------------|----------------|  
|<span data-ttu-id="fc7d9-120">付款</span><span class="sxs-lookup"><span data-stu-id="fc7d9-120">Payments</span></span>|<span data-ttu-id="fc7d9-121">建立者</span><span class="sxs-lookup"><span data-stu-id="fc7d9-121">Creators</span></span>|<span data-ttu-id="fc7d9-122">Payments_Creator</span><span class="sxs-lookup"><span data-stu-id="fc7d9-122">Payments_Creator</span></span>|  
|<span data-ttu-id="fc7d9-123">付款</span><span class="sxs-lookup"><span data-stu-id="fc7d9-123">Payments</span></span>|<span data-ttu-id="fc7d9-124">Repairers</span><span class="sxs-lookup"><span data-stu-id="fc7d9-124">Repairers</span></span>|<span data-ttu-id="fc7d9-125">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="fc7d9-125">Payments_Repairers</span></span>|  
|<span data-ttu-id="fc7d9-126">付款</span><span class="sxs-lookup"><span data-stu-id="fc7d9-126">Payments</span></span>|<span data-ttu-id="fc7d9-127">核准者</span><span class="sxs-lookup"><span data-stu-id="fc7d9-127">Approvers</span></span>|<span data-ttu-id="fc7d9-128">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="fc7d9-128">Payments_Approvers</span></span>|