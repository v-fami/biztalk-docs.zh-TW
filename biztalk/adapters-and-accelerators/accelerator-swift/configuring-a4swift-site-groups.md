---
title: 設定 A4SWIFT 網站群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- site groups, creating
- creating, site groups
- security, user accounts
- user accounts, site groups
- site groups, user accounts
ms.assetid: ec2f3efe-439a-4018-ad94-5ab0fb2808ee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0070f10819ebbde18cdeab9c3bd534ca74bfbcd9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209006"
---
# <a name="configuring-a4swift-site-groups"></a><span data-ttu-id="be343-102">設定 A4SWIFT 網站群組</span><span class="sxs-lookup"><span data-stu-id="be343-102">Configuring A4SWIFT Site Groups</span></span>
<span data-ttu-id="be343-103">您需要建立對應的網站群組鎖定 Message Repair 和 New Submission 設定期間建立的文件庫上的權限。</span><span class="sxs-lookup"><span data-stu-id="be343-103">You need to create the corresponding site groups to lock down the permissions on the document libraries created during Message Repair and New Submission configuration.</span></span> <span data-ttu-id="be343-104">若要執行此動作與上一節中的範例，會移至 MRSR 站台 A4SWIFT 系統管理員，並將其設定下列網站群組中：</span><span class="sxs-lookup"><span data-stu-id="be343-104">To do so with the example in the preceding section, an A4SWIFT Administrator would go to the MRSR site and set up the following site groups:</span></span>  
  
-   <span data-ttu-id="be343-105">Payments_Creators</span><span class="sxs-lookup"><span data-stu-id="be343-105">Payments_Creators</span></span>  
  
-   <span data-ttu-id="be343-106">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="be343-106">Payments_Repairers</span></span>  
  
-   <span data-ttu-id="be343-107">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="be343-107">Payments_Approvers</span></span>  
  
 <span data-ttu-id="be343-108">針對每個網站群組應該套用下列權限：</span><span class="sxs-lookup"><span data-stu-id="be343-108">For each of these site groups the following permissions should be applied:</span></span>  
  
-   <span data-ttu-id="be343-109">**檢視項目。**</span><span class="sxs-lookup"><span data-stu-id="be343-109">**View Items.**</span></span> <span data-ttu-id="be343-110">檢視項目在清單中，文件庫中的文件、 檢視網頁討論區註解，以及設定電子郵件警示的清單。</span><span class="sxs-lookup"><span data-stu-id="be343-110">View items in lists, documents in document libraries, view Web discussion comments, and set up e-mail alerts for lists.</span></span>  
  
-   <span data-ttu-id="be343-111">**檢視頁面。**</span><span class="sxs-lookup"><span data-stu-id="be343-111">**View Pages.**</span></span> <span data-ttu-id="be343-112">在網站上檢視頁面。</span><span class="sxs-lookup"><span data-stu-id="be343-112">View pages in a Web site.</span></span>  
  
 <span data-ttu-id="be343-113">每個使用者參與付款部門的角色，您需要建立新的站台使用者，並將該使用者指派給對應至網站群組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MMC 設定期間建立的角色。</span><span class="sxs-lookup"><span data-stu-id="be343-113">For each user who participates in the roles for the Payments department, you need to create a new site user and assign that user to the site group that corresponds to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] roles created during MMC configuration.</span></span>