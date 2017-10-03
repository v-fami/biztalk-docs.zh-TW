---
title: "如何使用角色連結精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- links [roles]
- Role Link Wizard [Orchestration Designer]
- roles, links
- Orchestration Designer, Role Link Wizard
- role links, Role Link Wizard [Orchestration Designer]
- links [roles], about links
ms.assetid: ddc33d87-c08d-4193-9483-4644ef302853
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d31abcc8fcc2bfaf1ebd641e1e52ad08d1c9c9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-role-link-wizard"></a><span data-ttu-id="0317f-102">如何使用角色連結精靈</span><span class="sxs-lookup"><span data-stu-id="0317f-102">How to Use the Role Link Wizard</span></span>
<span data-ttu-id="0317f-103">[角色連結精靈] 可以讓您建立新角色連結或修改現有的角色連結。</span><span class="sxs-lookup"><span data-stu-id="0317f-103">The Role Link Wizard enables you to create a new role link or modify an existing one.</span></span> <span data-ttu-id="0317f-104">您可以使用它來設定或檢視角色連結的名稱、類型與存取限制，以及構成角色連結類型的實作角色與使用角色。</span><span class="sxs-lookup"><span data-stu-id="0317f-104">You can use it to set or view the name, type, and access restriction of the role link, as well as the implements role and the uses role that compose the role link type.</span></span> <span data-ttu-id="0317f-105">若要了解角色連結運作，請參閱[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="0317f-105">To understand how role links work, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="0317f-106">**角色連結名稱**： 為您填入角色連結名稱，和為目前名稱的現有角色連結，您要設定或自動產生的名稱，如果您要建立新的角色連結。</span><span class="sxs-lookup"><span data-stu-id="0317f-106">**Role link name**: The role link name is filled in for you and is either the current name of an existing role link that you are configuring, or an automatically generated name if you are creating a new role link.</span></span> <span data-ttu-id="0317f-107">不論是哪一種，您都可以修改名稱。</span><span class="sxs-lookup"><span data-stu-id="0317f-107">In either case you can modify the name.</span></span>  
  
 <span data-ttu-id="0317f-108">**角色連結類型**： 您可以選取現有的角色連結類型，或另外新建一個。</span><span class="sxs-lookup"><span data-stu-id="0317f-108">**Role link type**: You can select an existing role link type, or create a new one.</span></span> <span data-ttu-id="0317f-109">不論您是設定新的或現有的角色連結類型，都可以指定協調流程參與服務的方式。</span><span class="sxs-lookup"><span data-stu-id="0317f-109">Whether you are configuring a new or existing role link type, you can specify how your orchestration participates in the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0317f-110">建議您最好在建立角色連結之前先建立角色連結類型及關聯的連接埠類型，好讓您可以使用現有的角色連結類型來定義角色連結。</span><span class="sxs-lookup"><span data-stu-id="0317f-110">We recommend that you create the role link type and associated port type prior to create the role link so that you can use an existing role link type for defining your role link.</span></span> <span data-ttu-id="0317f-111">如需詳細資訊，請參閱[如何在協調流程中建立角色連結](../core/how-to-create-role-links-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="0317f-111">For more information, see [How to Create Role Links in Orchestrations](../core/how-to-create-role-links-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="0317f-112">**角色連結使用方式**： 如果您建立新的角色連結類型，這兩種實作和使用角色為您自動建立。</span><span class="sxs-lookup"><span data-stu-id="0317f-112">**Role link usage**: If you create a new role link type, both the implements and uses roles are automatically created for you.</span></span> <span data-ttu-id="0317f-113">您可以選取反映協調流程參與服務的方式之角色。</span><span class="sxs-lookup"><span data-stu-id="0317f-113">You can select the role that reflects how your orchestration participates in the service.</span></span> <span data-ttu-id="0317f-114">在您完成精靈中的步驟之後，可以重新命名角色識別項或移除角色，以更符合您的實作。</span><span class="sxs-lookup"><span data-stu-id="0317f-114">After you have completed the steps in the wizard, you can rename the role identifiers or remove a role to better match your implementation.</span></span> <span data-ttu-id="0317f-115">角色連結類型必須包含這兩種角色類型中的一種或每種角色類型各一。</span><span class="sxs-lookup"><span data-stu-id="0317f-115">A role link type must contain one of either role type or one of each role type.</span></span> <span data-ttu-id="0317f-116">當您按一下**確定**，未設定的角色會建立對應至每個名稱。</span><span class="sxs-lookup"><span data-stu-id="0317f-116">When you click **OK**, unconfigured roles are created corresponding to each name.</span></span> <span data-ttu-id="0317f-117">您也可以在 [類型] 視窗中選取角色的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="0317f-117">You can also select port types for the roles in the Types window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0317f-118">若您叫用 [連接埠組態精靈] 來為角色連結類型建立連接埠類型，並且想要選取先前已定義的連接埠類型，請確定連接埠類型的存取限制未與角色連結類型的存取限制衝突。</span><span class="sxs-lookup"><span data-stu-id="0317f-118">If you invoke the Port Configuration Wizard to create a port type for your role link type, and want to select a previously defined port type, ensure that the access restrictions of the port type do not conflict with the access restrictions of the role link type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0317f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0317f-119">See Also</span></span>  
 [<span data-ttu-id="0317f-120">協調流程中使用角色連結</span><span class="sxs-lookup"><span data-stu-id="0317f-120">Using Role Links in Orchestrations</span></span>](../core/using-role-links-in-orchestrations.md)