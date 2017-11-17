---
title: "設定 A4SWIFT 使用者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, user accounts
- creating, user accounts
- user accounts, creating
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79c3b63cd77bb34545f4c4093796310aa7720563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a4swift-users"></a><span data-ttu-id="ce944-102">設定 A4SWIFT 使用者</span><span class="sxs-lookup"><span data-stu-id="ce944-102">Configuring A4SWIFT Users</span></span>
<span data-ttu-id="ce944-103">在安裝期間[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]，A4SWIFT 組態程式會建立預設交易夥伴設定檔和協議，並註冊 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="ce944-103">During installation of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], the A4SWIFT configuration program creates default trading partner profiles and agreements, and registers the BizTalk Server.</span></span> <span data-ttu-id="ce944-104">A4SWIFT 也會建立 Message Repair 和 New Submission 元件所使用的文件庫。</span><span class="sxs-lookup"><span data-stu-id="ce944-104">A4SWIFT also creates document libraries used by the Message Repair and New Submission component.</span></span>  
  
 <span data-ttu-id="ce944-105">A4SWIFT 安裝期間建立的下列文件資料夾：</span><span class="sxs-lookup"><span data-stu-id="ce944-105">A4SWIFT creates the following document folders during installation:</span></span>  
  
-   <span data-ttu-id="ce944-106">寄件匣文件庫</span><span class="sxs-lookup"><span data-stu-id="ce944-106">Outbox document library</span></span>  
  
-   <span data-ttu-id="ce944-107">範本文件庫</span><span class="sxs-lookup"><span data-stu-id="ce944-107">Templates document library</span></span>  
  
-   <span data-ttu-id="ce944-108">未剖析的文件庫</span><span class="sxs-lookup"><span data-stu-id="ce944-108">Unparsed document library</span></span>  
  
-   <span data-ttu-id="ce944-109">新的 SWIFT MT 訊息文件庫</span><span class="sxs-lookup"><span data-stu-id="ce944-109">New SWIFT MT Message document library</span></span>  
  
-   <span data-ttu-id="ce944-110">新的 SWIFT MX 訊息文件庫</span><span class="sxs-lookup"><span data-stu-id="ce944-110">New SWIFT MX Messages document library</span></span>  
  
 <span data-ttu-id="ce944-111">建立每個部門，A4SWIFT 系統管理員必須手動設定網站的相對應的部門的群組和 A4SWIFT 定義角色。</span><span class="sxs-lookup"><span data-stu-id="ce944-111">For each department created, the A4SWIFT Administrator must manually set up site groups for the corresponding departments and A4SWIFT defined roles.</span></span> <span data-ttu-id="ce944-112">每個部門/角色有自動建立設定檔 Web Client(PWC) 收件匣。</span><span class="sxs-lookup"><span data-stu-id="ce944-112">Each department/role has an inbox created automatically by the Profile Web Client(PWC).</span></span>  
  
 <span data-ttu-id="ce944-113">A4SWIFT 安裝組態程式完成之後，A4SWIFT 系統管理員會設定工作流程中每個部門的組織中。</span><span class="sxs-lookup"><span data-stu-id="ce944-113">After the A4SWIFT setup configuration program is completed, the A4SWIFT Administrator configures workflows for each department in the organization.</span></span> <span data-ttu-id="ce944-114">訊息修復和新送出在設定期間，設定檔的 Web 用戶端，透過對應的收件匣會建立每個部門/角色組合。</span><span class="sxs-lookup"><span data-stu-id="ce944-114">During Message Repair and New Submission configuration, through the Profile Web Client, corresponding inboxes are created for each department/role combination.</span></span> <span data-ttu-id="ce944-115">比方說，PWC 組態期間 A4SWIFT 系統管理員會建立名為付款的部門，並再將建立者、 Repairers 和核准者的角色指派給呼叫付款的部門。</span><span class="sxs-lookup"><span data-stu-id="ce944-115">For example, during PWC configuration an A4SWIFT Administrator creates a department named Payments and then assigns the roles of Creators, Repairers, and Approvers to a department called Payments.</span></span> <span data-ttu-id="ce944-116">MRSR 站台上的文件庫會使用名稱來建立收件匣中的範例下表, 所示：</span><span class="sxs-lookup"><span data-stu-id="ce944-116">Document libraries on the MRSR site are created with the inbox names as shown in the examples in the following table:</span></span>  
  
|<span data-ttu-id="ce944-117">部門名稱</span><span class="sxs-lookup"><span data-stu-id="ce944-117">Department name</span></span>|<span data-ttu-id="ce944-118">角色名稱</span><span class="sxs-lookup"><span data-stu-id="ce944-118">Role name</span></span>|<span data-ttu-id="ce944-119">收件匣名稱</span><span class="sxs-lookup"><span data-stu-id="ce944-119">Inbox name</span></span>|  
|---------------------|---------------|----------------|  
|<span data-ttu-id="ce944-120">付款</span><span class="sxs-lookup"><span data-stu-id="ce944-120">Payments</span></span>|<span data-ttu-id="ce944-121">建立者</span><span class="sxs-lookup"><span data-stu-id="ce944-121">Creators</span></span>|<span data-ttu-id="ce944-122">Payments_Creator</span><span class="sxs-lookup"><span data-stu-id="ce944-122">Payments_Creator</span></span>|  
|<span data-ttu-id="ce944-123">付款</span><span class="sxs-lookup"><span data-stu-id="ce944-123">Payments</span></span>|<span data-ttu-id="ce944-124">Repairers</span><span class="sxs-lookup"><span data-stu-id="ce944-124">Repairers</span></span>|<span data-ttu-id="ce944-125">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="ce944-125">Payments_Repairers</span></span>|  
|<span data-ttu-id="ce944-126">付款</span><span class="sxs-lookup"><span data-stu-id="ce944-126">Payments</span></span>|<span data-ttu-id="ce944-127">核准者</span><span class="sxs-lookup"><span data-stu-id="ce944-127">Approvers</span></span>|<span data-ttu-id="ce944-128">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="ce944-128">Payments_Approvers</span></span>|