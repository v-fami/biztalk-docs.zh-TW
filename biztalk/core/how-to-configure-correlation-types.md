---
title: 如何設定相互關聯類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, correlation types
- correlation types, configuring
- correlation types, deleting
- configuring, correlation types
ms.assetid: cfae4d2e-ec79-45c8-93b3-799dc5e0576e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 646ac7dafd5207a2558e45252077efe2d9616a70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248566"
---
# <a name="how-to-configure-correlation-types"></a><span data-ttu-id="5e5c9-102">如何設定相互關聯類型</span><span class="sxs-lookup"><span data-stu-id="5e5c9-102">How to Configure Correlation Types</span></span>
<span data-ttu-id="5e5c9-103">您使用**相互關聯屬性**對話方塊來加入或移除的相互關聯類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-103">You use the **Correlation Properties** dialog box to add or remove properties from a correlation type.</span></span> <span data-ttu-id="5e5c9-104">相互關聯類型會列出相互關聯集中的屬性；在執行階段中，傳送和接收活動會使用這些屬性，確定內送訊息是否與協調流程之正確執行個體相關。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-104">The correlation type lists the properties in a correlation set which are used by Send and Receive activities to make sure that incoming messages are properly correlated with the right instances of an orchestration at run time.</span></span>  
  
 <span data-ttu-id="5e5c9-105">此對話方塊中有兩個窗格，分別包含一份屬性清單。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-105">There are two panes in the dialog box, each containing a list of properties.</span></span> <span data-ttu-id="5e5c9-106">左窗格為 [可用屬性] 窗格，內含您的專案所定義或參考之所有屬性的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-106">The left pane, "Available Properties", contains a tree view of all of the properties that are defined in your project or referenced by it.</span></span> <span data-ttu-id="5e5c9-107">顯示的屬性預設為 BizTalk Server 定義的系統屬性，但是您也可以在屬性結構描述中定義自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-107">The properties that appear by default are system properties, defined by BizTalk Server, but you can also define your own properties in a property schema.</span></span> <span data-ttu-id="5e5c9-108">如需有關如何建立屬性結構描述的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-108">For more information about creating property schemas, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e5c9-109">結構描述屬性必須先升級，然後才能在相互關聯類型中使用。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-109">Schema properties must be promoted before they can be used in a correlation type.</span></span> <span data-ttu-id="5e5c9-110">如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-110">For more information, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
### <a name="to-add-and-configure-a-correlation-type"></a><span data-ttu-id="5e5c9-111">若要新增及設定相互關聯類型</span><span class="sxs-lookup"><span data-stu-id="5e5c9-111">To add and configure a correlation type</span></span>  
  
-   <span data-ttu-id="5e5c9-112">在協調流程檢視] 視窗中，以滑鼠右鍵按一下**相互關聯類型**，然後按一下 [**新相互關聯類型**。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-112">In the Orchestration View window, right-click **Correlation Types** and then click **New Correlation Type**.</span></span>  
  
     <span data-ttu-id="5e5c9-113">**相互關聯屬性**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-113">The **Correlation Properties** dialog box comes up.</span></span> <span data-ttu-id="5e5c9-114">新增您要包含在相互關聯類型內的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-114">Add properties that you want to include in your correlation type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e5c9-115">如果您存取**相互關聯屬性**對話方塊直接從相互關聯集，如果不存在，則會建立相互關聯類型的相互關聯集。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-115">If you access the **Correlation Properties** dialog box directly from a correlation set, a correlation type for the correlation set is created if one does not already exist.</span></span> <span data-ttu-id="5e5c9-116">您的變更將會儲存在新的相互關聯類型中，而且會將相互關聯集設定為使用新的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-116">Your changes will be saved to the new correlation type, and the correlation set will be configured to use the new correlation type.</span></span> <span data-ttu-id="5e5c9-117">如果相互關聯集已有相互關聯類型，在您進行變更後，系統將會修改該相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-117">If a correlation type already existed for the correlation set and you make changes, the correlation type will be modified.</span></span>  
  
### <a name="to-remove-a-correlation-type"></a><span data-ttu-id="5e5c9-118">若要移除相互關聯類型</span><span class="sxs-lookup"><span data-stu-id="5e5c9-118">To remove a correlation type</span></span>  
  
-   <span data-ttu-id="5e5c9-119">在協調流程檢視] 視窗中，以滑鼠右鍵按一下您想要移除，然後按一下 [相互關聯類型**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5e5c9-119">In the Orchestration View window, right-click the correlation type you want to remove and then click **Delete**.</span></span>