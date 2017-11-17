---
title: "協調流程中使用角色連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role links
- roles, links
- roles
- roles, about roles
- role links, about role links
- role links, properties
- role links, initializing
ms.assetid: 0cf85544-12c9-4541-8925-61a6e946cce0
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e3c4e4a4c3a99fb6e1962299d440717eaa8d51b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-role-links-in-orchestrations"></a><span data-ttu-id="60cd2-102">在協調流程中使用角色連結</span><span class="sxs-lookup"><span data-stu-id="60cd2-102">Using Role Links in Orchestrations</span></span>
<span data-ttu-id="60cd2-103">角色連結是協調流程與交易夥伴之間互動的抽象形式。</span><span class="sxs-lookup"><span data-stu-id="60cd2-103">Role links are a form of abstraction for the interactions between your orchestration and your trading partners.</span></span> <span data-ttu-id="60cd2-104">角色連結可讓您根據交易夥伴解析、訊息內容或資料庫尋查結果，動態選擇要與之互動的交易夥伴，而您的整體商務程序仍然能保持完整。</span><span class="sxs-lookup"><span data-stu-id="60cd2-104">Role links enable you to dynamically choose which trading partner to interact with based on trading partner resolution, message content, or the results of a database lookup while maintaining your overall business process intact.</span></span>  
  
 <span data-ttu-id="60cd2-105">例如，在 B2B 實例中，有多個買方、一個供應商以及供應商的多個託運商。</span><span class="sxs-lookup"><span data-stu-id="60cd2-105">For example, in a business-to-business scenario, there are multiple buyers, a single supplier, and multiple shipping agencies for the supplier.</span></span> <span data-ttu-id="60cd2-106">當買方傳送訂單給供應商時，供應商透過合作對象解析知道是哪個買方傳送了這份訂單，並且可以套用適當的折扣。</span><span class="sxs-lookup"><span data-stu-id="60cd2-106">When a buyer sends a purchase order to the supplier, the supplier knows through party resolution which buyer is sending the purchase order and can apply the appropriate discount.</span></span> <span data-ttu-id="60cd2-107">此外，根據訂購的貨物，供應商還可以在執行階段決定將由哪個託運商負責運送。</span><span class="sxs-lookup"><span data-stu-id="60cd2-107">Moreover, based on the goods ordered, the supplier determines at run time which shipping agency will be in charge of the delivery.</span></span> <span data-ttu-id="60cd2-108">雖然每個託運商各有自己的傳輸通訊協定，但供應商仍然可在執行階段使用相同的商務程序來處理所有託運商，並決定與哪個代理商進行互動。</span><span class="sxs-lookup"><span data-stu-id="60cd2-108">Although each shipping agency may have its own transport protocol, the supplier can use the same business process at run time to handle all the shipping agencies and determine which agency to interact with.</span></span> <span data-ttu-id="60cd2-109">在後續階段中，如果託運商更新其傳輸通訊協定 — 例如，從 FTP 變更為 HTTP — 供應商只需要使用 BizTalk 總管或 BizTalk Server 管理主控台來更新該特定託運商相關聯的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="60cd2-109">At a later stage, if a shipping agency updates its transport protocol—for example, from FTP to HTTP—the supplier only needs to use BizTalk Explorer or the BizTalk Server Administration console to update the send port associated with that particular shipping agency.</span></span> <span data-ttu-id="60cd2-110">供應商則不需要變更其位於協調流程中的商務程序。</span><span class="sxs-lookup"><span data-stu-id="60cd2-110">The supplier does not need to change its business process, which resides in the orchestration.</span></span>  
  
## <a name="roles"></a><span data-ttu-id="60cd2-111">角色</span><span class="sxs-lookup"><span data-stu-id="60cd2-111">Roles</span></span>  
 <span data-ttu-id="60cd2-112">在協調流程中有兩個角色：</span><span class="sxs-lookup"><span data-stu-id="60cd2-112">There are two roles in an orchestration:</span></span>  
  
-   <span data-ttu-id="60cd2-113">接收和處理訊息的「實作」角色。</span><span class="sxs-lookup"><span data-stu-id="60cd2-113">An "implements" role to receive and process messages.</span></span> <span data-ttu-id="60cd2-114">這個角色也稱為提供者。</span><span class="sxs-lookup"><span data-stu-id="60cd2-114">This role is also known as the provider.</span></span>  
  
-   <span data-ttu-id="60cd2-115">傳送訊息的「使用」角色。</span><span class="sxs-lookup"><span data-stu-id="60cd2-115">A "uses" role to send messages.</span></span> <span data-ttu-id="60cd2-116">這個角色也稱為取用者。</span><span class="sxs-lookup"><span data-stu-id="60cd2-116">This role is also known as the consumer.</span></span>  
  
## <a name="role-links"></a><span data-ttu-id="60cd2-117">角色連結</span><span class="sxs-lookup"><span data-stu-id="60cd2-117">Role Links</span></span>  
 <span data-ttu-id="60cd2-118">角色連結可以包含取用者或提供者角色，或各有其一。</span><span class="sxs-lookup"><span data-stu-id="60cd2-118">A role link can include either a consumer or a provider role, or one of each.</span></span> <span data-ttu-id="60cd2-119">取用者角色會取用提供者角色提供的服務。</span><span class="sxs-lookup"><span data-stu-id="60cd2-119">A consumer role consumes the services provided by the provider role.</span></span> <span data-ttu-id="60cd2-120">當您使用這兩個角色其中一個或兩者來定義角色連結時，它會假定互補角色是由您正在連結的夥伴擔任。</span><span class="sxs-lookup"><span data-stu-id="60cd2-120">When you define a role link with one or both of these roles, it is assumed that the complementary role is being fulfilled by the partner with whom you are linking.</span></span>  
  
 <span data-ttu-id="60cd2-121">角色連結具有**SourceParty**屬性， **DestinationParty**屬性，以及初始角色。</span><span class="sxs-lookup"><span data-stu-id="60cd2-121">A role link has a **SourceParty** property, a **DestinationParty** property, and an initiating role.</span></span> <span data-ttu-id="60cd2-122">初始角色是先進行通訊，以及因此啟始角色連結的值設定角色**DestinationParty**屬性。</span><span class="sxs-lookup"><span data-stu-id="60cd2-122">An initiating role is the role on which the first communication occurs, and which therefore initiates the role link by setting the value of the **DestinationParty** property.</span></span>  
  
 <span data-ttu-id="60cd2-123">如果初始角色是傳送訊息的取用者，則明確設定**DestinationParty**協調流程中的屬性 （一次，一次）。</span><span class="sxs-lookup"><span data-stu-id="60cd2-123">If the initiating role is a consumer for sending messages, you explicitly set the **DestinationParty** property (once and only once) in your orchestration.</span></span> <span data-ttu-id="60cd2-124">若要這樣做，您可以設定的值**DestinationParty**中**運算式**圖形，如下列範例，其中 ConfirmOrder 是角色連結名稱，而 PartnerName 和 organizationname 則是合作對象的參數：</span><span class="sxs-lookup"><span data-stu-id="60cd2-124">To do so, you set the value of the **DestinationParty** in the **Expression** shape, as in the following example, where ConfirmOrder is the name of a role link, and PartnerName and OrganizationName are parameters of a party:</span></span>  
  
```  
ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");  
```  
  
 <span data-ttu-id="60cd2-125">如果初始角色是提供者接收訊息， **DestinationParty**屬性會自動初始化收件者。</span><span class="sxs-lookup"><span data-stu-id="60cd2-125">If the initiating role is a provider for receiving messages, the **DestinationParty** property is initialized automatically by the receiver.</span></span> <span data-ttu-id="60cd2-126">**DestinationParty**設為提供者本身。</span><span class="sxs-lookup"><span data-stu-id="60cd2-126">The **DestinationParty** is set to the provider itself.</span></span> <span data-ttu-id="60cd2-127">**SourceParty**屬性是唯讀的而且提供透過受信任的管線元件來解析合作對象名稱為基礎的安全性識別碼 (SID) 寄件者或合作對象相關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="60cd2-127">The **SourceParty** property is read-only, and is supplied through a trusted pipeline component to resolve the party name based on the security identifier (SID) of the sender or on a certificate associated with the party.</span></span> <span data-ttu-id="60cd2-128">執行管線元件的主控件必須標示為**信任的驗證**。</span><span class="sxs-lookup"><span data-stu-id="60cd2-128">The host running the pipeline component must be marked as **Authentication Trusted**.</span></span> <span data-ttu-id="60cd2-129">您可以取得的值**SourceParty**中**運算式**圖形，方法是使用下列範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="60cd2-129">You can get the value of the **SourceParty** in the **Expression** shape by using the following sample code:</span></span>  
  
 `PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);`  
  
## <a name="role-link-types"></a><span data-ttu-id="60cd2-130">角色連結類型</span><span class="sxs-lookup"><span data-stu-id="60cd2-130">Role Link Types</span></span>  
 <span data-ttu-id="60cd2-131">角色連結是角色連結類型的執行個體，它是由一或兩個角色所組成。</span><span class="sxs-lookup"><span data-stu-id="60cd2-131">A role link is an instance of a role link type, which consists of either one or two roles.</span></span> <span data-ttu-id="60cd2-132">使用角色連結類型時，請考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="60cd2-132">When working with a role link type, consider the following:</span></span>  
  
-   <span data-ttu-id="60cd2-133">您只能在單一角色連結類型中，參考任何指定的連接埠類型一次。</span><span class="sxs-lookup"><span data-stu-id="60cd2-133">You can refer only once to any given port type within a single role link type.</span></span>  
  
-   <span data-ttu-id="60cd2-134">因為角色連結類型定義包含連接埠類型，所以連接埠類型的範圍必須包含會使用它的任何角色連結類型的範圍。</span><span class="sxs-lookup"><span data-stu-id="60cd2-134">Because a role link type definition includes port types, the scope of a port type must encompass that of any role link type that uses it.</span></span>  
  
-   <span data-ttu-id="60cd2-135">使用「商務活動服務」(BAS) 時，必須在與相關角色連結類型相同的 BizTalk 組件中定義結構化參數結構描述。</span><span class="sxs-lookup"><span data-stu-id="60cd2-135">When working with Business Activity Services (BAS), the structured parameter schema must be defined in the same BizTalk assembly as the role link type it is associated with.</span></span> <span data-ttu-id="60cd2-136">因為與結構描述有關聯的是角色連結類型，而非構成該角色連結類型的個別角色，如果兩個扮演不同角色的合作對象共用包含角色連結類型的組件，則雙方都會看見相同的結構化參數結構描述。</span><span class="sxs-lookup"><span data-stu-id="60cd2-136">Because the schema is associated with the role link type and not with the individual roles that make up that role link type, if the parties that play the different roles share the assembly containing the role link type, both parties will see the same structured parameter schemas.</span></span> <span data-ttu-id="60cd2-137">如果兩個合作對象都使用相同的角色連結類型，但是必須有不同的參數結構描述，則應該為每個合作對象建立不同的組件。</span><span class="sxs-lookup"><span data-stu-id="60cd2-137">If the two parties use the same role link type but must have different parameter schemas, a different assembly should be created for each party.</span></span> <span data-ttu-id="60cd2-138">在每個組件中，角色連結類型則必須重複。</span><span class="sxs-lookup"><span data-stu-id="60cd2-138">The role link type should be duplicated in each assembly.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60cd2-139">本節內容</span><span class="sxs-lookup"><span data-stu-id="60cd2-139">In This Section</span></span>  
  
-   [<span data-ttu-id="60cd2-140">如何在協調流程中建立角色連結</span><span class="sxs-lookup"><span data-stu-id="60cd2-140">How to Create Role Links in Orchestrations</span></span>](../core/how-to-create-role-links-in-orchestrations.md)  
  
-   [<span data-ttu-id="60cd2-141">如何使用角色連結圖形</span><span class="sxs-lookup"><span data-stu-id="60cd2-141">How to Use the Role Link Shape</span></span>](../core/how-to-use-the-role-link-shape.md)  
  
-   [<span data-ttu-id="60cd2-142">如何使用角色連結精靈</span><span class="sxs-lookup"><span data-stu-id="60cd2-142">How to Use the Role Link Wizard</span></span>](../core/how-to-use-the-role-link-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="60cd2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60cd2-143">See Also</span></span>  
 <span data-ttu-id="60cd2-144">[如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="60cd2-144">[How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md) </span></span>  
 [<span data-ttu-id="60cd2-145">協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="60cd2-145">Using Ports in Orchestrations</span></span>](../core/using-ports-in-orchestrations.md)