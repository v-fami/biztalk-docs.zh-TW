---
title: "角色連結和服務連結角色 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, orchestrations
- service link roles
- role links
- roles, orchestrations
- roles
- roles, about roles
- service link roles, about service link roles
- orchestrations, roles
- role links, about role links
- orchestrations, deleting
ms.assetid: 23b4ca34-a1a5-44d4-a50d-661277681c72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6630b1ad22ba86f3efe8a19409f3b731880c8a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="role-links-and-service-link-roles"></a><span data-ttu-id="44d5f-102">角色連結和服務連結角色</span><span class="sxs-lookup"><span data-stu-id="44d5f-102">Role Links and Service Link Roles</span></span>
<span data-ttu-id="44d5f-103">A*角色*是使用服務或實作服務的連接埠類型的集合。</span><span class="sxs-lookup"><span data-stu-id="44d5f-103">A *role* is a collection of port types that either uses a service or implements a service.</span></span> <span data-ttu-id="44d5f-104">角色代表合作對象可擁有一或多個協調流程的互動類型。</span><span class="sxs-lookup"><span data-stu-id="44d5f-104">A role represents the type of interaction that a party can have with one or many orchestrations.</span></span> <span data-ttu-id="44d5f-105">當合作對象的數目增加時，角色提供彈性與簡易管理。</span><span class="sxs-lookup"><span data-stu-id="44d5f-105">Roles provide flexibility and ease of management as the number of parties increase.</span></span> <span data-ttu-id="44d5f-106">例如，協調流程可能使用託運商的角色。</span><span class="sxs-lookup"><span data-stu-id="44d5f-106">For example, an orchestration might use the role of a Shipper.</span></span> <span data-ttu-id="44d5f-107">託運商可能有一或多個合作對象與它關聯。</span><span class="sxs-lookup"><span data-stu-id="44d5f-107">The Shipper would have one or two parties associated with it.</span></span> <span data-ttu-id="44d5f-108">協調流程決定要僱用哪家託運公司運送項目時，它會比較託運商角色中合作對象的價格。</span><span class="sxs-lookup"><span data-stu-id="44d5f-108">When the orchestration decides which shipping company to use to ship an item, it compares the prices of the parties in the Shipper role.</span></span>  
  
 <span data-ttu-id="44d5f-109">A*角色連結類型*是確定兩個服務或協調流程之間關係特徵的屬性。</span><span class="sxs-lookup"><span data-stu-id="44d5f-109">A *role link type* is a property that characterizes the relationship between two services or orchestrations.</span></span> <span data-ttu-id="44d5f-110">它定義了關係中每個服務所扮演的部分，並指定每個角色提供的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="44d5f-110">It defines the part played by each of the services in the relationship and specifies the port types provided by each role.</span></span>  
  
 <span data-ttu-id="44d5f-111">合作對象或組織單位代表 BizTalk Server 外部與協調流程互動的實體。</span><span class="sxs-lookup"><span data-stu-id="44d5f-111">A party, or organizational unit, represents an entity outside of BizTalk Server that interacts with an orchestration.</span></span> <span data-ttu-id="44d5f-112">在 BizTalk Server 中，與您交換訊息的每個組織都以合作對象來表示。</span><span class="sxs-lookup"><span data-stu-id="44d5f-112">In BizTalk Server, each organization with which you exchange messages is represented by a party.</span></span> <span data-ttu-id="44d5f-113">藉由在角色中登錄，您可以定義合作對象互動的方式。</span><span class="sxs-lookup"><span data-stu-id="44d5f-113">You can define how the party interacts by enlisting it in a role.</span></span>  
  
 <span data-ttu-id="44d5f-114">角色連結類型與協調流程關聯時，可以部署或移除該角色連結類型。</span><span class="sxs-lookup"><span data-stu-id="44d5f-114">You can deploy or remove a role link type when it is associated with an orchestration.</span></span>  
  
## <a name="orchestrations-and-roles"></a><span data-ttu-id="44d5f-115">協調流程和角色</span><span class="sxs-lookup"><span data-stu-id="44d5f-115">Orchestrations and Roles</span></span>  
 <span data-ttu-id="44d5f-116">部署使用角色連結類型的協調流程時，「組態」資料庫會儲存角色。</span><span class="sxs-lookup"><span data-stu-id="44d5f-116">When you deploy an orchestration that uses a role link type, the Configuration database saves the role.</span></span> <span data-ttu-id="44d5f-117">因為角色可以由一個以上的協調流程使用，所以「管理」資料庫僅會儲存一個角色連結類型複本。</span><span class="sxs-lookup"><span data-stu-id="44d5f-117">Because a role can be used by more than one orchestration, the Management database saves only one copy of the role link type.</span></span>  
  
 <span data-ttu-id="44d5f-118">若您的 BizTalk 專案在名稱及命名空間相同的不同協調流程 (.odx) 檔案中包含兩個角色連結類型，則該 BizTalk 專案不會編譯。</span><span class="sxs-lookup"><span data-stu-id="44d5f-118">If your BizTalk project contains two role link types in separate orchestration (.odx) files that have the same name and namespace, your BizTalk project does not compile.</span></span>  
  
### <a name="orchestration-removals-that-use-roles"></a><span data-ttu-id="44d5f-119">移除使用角色的協調流程</span><span class="sxs-lookup"><span data-stu-id="44d5f-119">Orchestration Removals that use Roles</span></span>  
 <span data-ttu-id="44d5f-120">由於角色連結類型可供多個協調流程使用，因此解除部署包含使用角色之協調流程的組件時，只有在沒有其他協調流程使用角色時，「管理」資料庫才能移除角色。</span><span class="sxs-lookup"><span data-stu-id="44d5f-120">Because a role link type can be used by more than one orchestration, when you undeploy an assembly that contains an orchestration that uses a role, the Management database removes the role only if no other orchestrations are using the role.</span></span>  
  
 <span data-ttu-id="44d5f-121">此外，若是沒有合作對象在角色中登錄，「管理」資料庫也會移除角色。</span><span class="sxs-lookup"><span data-stu-id="44d5f-121">Additionally, the Management database removes a role only if there are no parties enlisted with it.</span></span> <span data-ttu-id="44d5f-122">就好像您無法覆寫有登錄合作對象的角色，也不能移除有登錄合作對象的角色。</span><span class="sxs-lookup"><span data-stu-id="44d5f-122">Just as you cannot overwrite a role that has parties enlisted with it, you cannot remove a role that has parties enlisted with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d5f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44d5f-123">See Also</span></span>  
 <span data-ttu-id="44d5f-124">[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="44d5f-124">[Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="44d5f-125">成品</span><span class="sxs-lookup"><span data-stu-id="44d5f-125">Artifacts</span></span>](../core/artifacts.md)