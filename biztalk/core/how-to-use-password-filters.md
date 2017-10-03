---
title: "如何使用密碼篩選器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb429f8b-c301-45a3-8a4f-bbe6f2c566a3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ad35e2c3bec5b2ece69911b8de8c7fd13c9b790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-password-filters"></a><span data-ttu-id="fb948-102">如何使用密碼篩選條件</span><span class="sxs-lookup"><span data-stu-id="fb948-102">How to Use Password Filters</span></span>
<span data-ttu-id="fb948-103">「ENTSSO 密碼同步處理」功能，可以同步處理 Microsoft Windows Active Directory 和非 Windows 系統之間的密碼。</span><span class="sxs-lookup"><span data-stu-id="fb948-103">The ENTSSO Password Synchronization feature synchronizes passwords between Microsoft Windows Active Directory and non-Windows systems.</span></span> <span data-ttu-id="fb948-104">然而，許多外部系統都有不同於 Active Directory 的密碼原則需求</span><span class="sxs-lookup"><span data-stu-id="fb948-104">However, many external systems have password policy requirements which differ from those in Active Directory.</span></span> <span data-ttu-id="fb948-105">(例如，某個 IBM 系統可能會要求密碼都為大寫，而且僅限於 8 個字元)。這樣便會強制 ENTSSO 在兩個系統之間使用「最低公分母」來限制密碼安全性。</span><span class="sxs-lookup"><span data-stu-id="fb948-105">(For example, an IBM system may require a password to be upper case and limited to 8 characters.) This forces ENTSSO to use the “lowest common denominator” between the two systems, limiting password security.</span></span>  
  
 <span data-ttu-id="fb948-106">「ENTSSO 密碼篩選」功能可解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="fb948-106">The ENTSSO Password Filter feature addresses this limitation.</span></span> <span data-ttu-id="fb948-107">其實「密碼篩選」只是定義了額外屬性的「密碼同步配接器」。</span><span class="sxs-lookup"><span data-stu-id="fb948-107">A Password Filter is merely a Password Sync Adapter with additional properties defined.</span></span> <span data-ttu-id="fb948-108">這些其他屬性 (例如最大或最小長度、大小寫，以及字元限制) 會用來篩選密碼，以確保密碼符合外部系統的條件。</span><span class="sxs-lookup"><span data-stu-id="fb948-108">These additional properties (such as maximum or minimum length, case, and character restrictions) serve to filter the passwords so that they meet the criteria of the external system.</span></span>  
  
 <span data-ttu-id="fb948-109">請注意，當您建立「密碼篩選」時，指定的系統管理員群組會自動當做「SSO 系統管理員帳戶」。</span><span class="sxs-lookup"><span data-stu-id="fb948-109">Note that when you create a Password Filter, the Administrator group specified is automatically used as the SSO Administrators account.</span></span> <span data-ttu-id="fb948-110">如果您變更 SSO 系統管理員群組，您必須確定密碼篩選器也會更新與新的 SSO 系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb948-110">If you change the SSO Administrator group, you will need to make sure the Password Filter is also updated with the new SSO Administrators account.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb948-111">就像 ENTSSO 系統中的所有項目，「密碼篩選」包含高度機密資訊，因此應盡可能地只讓最少數的人員知道。</span><span class="sxs-lookup"><span data-stu-id="fb948-111">As with all elements of the ENTSSO system, Password Filters contain highly sensitive information and should be exposed to the minimum number of people possible.</span></span>  
  
### <a name="to-create-a-password-filter"></a><span data-ttu-id="fb948-112">若要建立密碼篩選</span><span class="sxs-lookup"><span data-stu-id="fb948-112">To Create a Password Filter</span></span>  
  
1.  <span data-ttu-id="fb948-113">在**SSO 管理 主控台**，以滑鼠右鍵按一下**密碼管理**節點，然後再按一下**建立篩選**。</span><span class="sxs-lookup"><span data-stu-id="fb948-113">In the **SSO Management Console**, right-click the **Password Management** node, and then click **Create Filter**.</span></span>  
  
     <span data-ttu-id="fb948-114">**密碼篩選精靈**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fb948-114">The **Password Filter Wizard** appears.</span></span>  
  
2.  <span data-ttu-id="fb948-115">請依照精靈的指示來建立密碼篩選。</span><span class="sxs-lookup"><span data-stu-id="fb948-115">Follow the directions on the Wizard to create the Password Filter.</span></span>  
  
### <a name="to-assign-an-affiliate-application-to-a-password-filter"></a><span data-ttu-id="fb948-116">若要將分支機構應用程式指派至密碼篩選</span><span class="sxs-lookup"><span data-stu-id="fb948-116">To Assign an Affiliate Application to a Password Filter</span></span>  
  
1.  <span data-ttu-id="fb948-117">以滑鼠右鍵按一下適當的篩選器，然後按一下**指派**...</span><span class="sxs-lookup"><span data-stu-id="fb948-117">Right-click the appropriate filter, and then click **Assign**….</span></span>  
  
2.  <span data-ttu-id="fb948-118">選取適當**分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fb948-118">Select the appropriate **Affiliate Application**.</span></span>