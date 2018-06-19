---
title: 配接器群組和群組配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e0a9423-99dd-4474-afa1-fd8e1d074cd1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcf10f50857026893245cc567783b649f614c4f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225374"
---
# <a name="adapter-groups-and-group-adapters"></a><span data-ttu-id="301e3-102">配接器群組和群組配接器</span><span class="sxs-lookup"><span data-stu-id="301e3-102">Adapter Groups and Group Adapters</span></span>
<span data-ttu-id="301e3-103">*配接器群組*是一種管理機制，您可以使用它來收集和組織的介面卡集合。</span><span class="sxs-lookup"><span data-stu-id="301e3-103">An *adapter group* is an administration mechanism that you can use to collect and organize a set of adapters.</span></span> <span data-ttu-id="301e3-104">相反地，*群組配接器*是服務配接器群組中的所有配接器的元件。</span><span class="sxs-lookup"><span data-stu-id="301e3-104">In contrast, a *group adapter* is a component that services all adapters in an adapter group.</span></span> <span data-ttu-id="301e3-105">例如，您可以撰寫一組配接器，讓它們都使用相同的 COM 元件，透過 TCP/IP 來傳輸密碼同步。</span><span class="sxs-lookup"><span data-stu-id="301e3-105">For example, you might write a set of adapters that all use the same COM component to transmit password synchronizations over TCP/IP.</span></span> <span data-ttu-id="301e3-106">這一組配接器即稱為配接器群組，而用來服務這些配接器的元件，就稱為群組配接器。</span><span class="sxs-lookup"><span data-stu-id="301e3-106">Your set of adapters is called the adapter group, whereas the component that services them all is called a group adapter.</span></span> <span data-ttu-id="301e3-107">配接器群組在組態存放區中加以描述。</span><span class="sxs-lookup"><span data-stu-id="301e3-107">Adapter groups are described in the configuration store.</span></span> <span data-ttu-id="301e3-108">您可以使用 `ISSOPSAdapter.ReceiveNotification` 擷取有關配接器群組的資訊和更新。</span><span class="sxs-lookup"><span data-stu-id="301e3-108">You can retrieve information and updates on an adapter group by using `ISSOPSAdapter.ReceiveNotification`.</span></span>  
  
 <span data-ttu-id="301e3-109">群組配接器的名稱和配接器群組的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="301e3-109">A group adapter has the same name as the adapter group.</span></span> <span data-ttu-id="301e3-110">除了命名限制不同之外，群組配接器其實就是一般的配接器。</span><span class="sxs-lookup"><span data-stu-id="301e3-110">Other than the naming restriction, a group adapter is otherwise identical to a normal adapter.</span></span> <span data-ttu-id="301e3-111">例如，群組配接器可以擁有獨立存取群組和組態屬性，正如其組態檔案所述。</span><span class="sxs-lookup"><span data-stu-id="301e3-111">For example, a group adapter can have independent access groups and configuration properties, as described by its configuration file.</span></span> <span data-ttu-id="301e3-112">群組配接器大多和配接器群組中的配接器位於同一台電腦上。</span><span class="sxs-lookup"><span data-stu-id="301e3-112">A group adapter is most likely on the same computer as any adapters in the adapter group.</span></span> <span data-ttu-id="301e3-113">然而，目前並不強制一定要如此做。</span><span class="sxs-lookup"><span data-stu-id="301e3-113">However, this is not currently enforced.</span></span> <span data-ttu-id="301e3-114">同樣地，相同配接器群組中的所有配接器最好都能在同一台電腦上。</span><span class="sxs-lookup"><span data-stu-id="301e3-114">Likewise, all adapters in the same adapter group can be expected to be on the same computer.</span></span>  
  
 <span data-ttu-id="301e3-115">您可以使用 `ISSOPSAdapter.InitializeAdapter`，在啟動時存取和初始化群組配接器。</span><span class="sxs-lookup"><span data-stu-id="301e3-115">By using `ISSOPSAdapter.InitializeAdapter`, you can access and initialize a group adapter during startup.</span></span> <span data-ttu-id="301e3-116">當您初始化群組配接器時，系統會告知群組配接器，目前系統中有哪些配接器存在於配接器群組中。</span><span class="sxs-lookup"><span data-stu-id="301e3-116">When you initialize a group adapter, the system informs the group adapter of all adapters in the adapter group on the current system.</span></span> <span data-ttu-id="301e3-117">此外，每當在配接器群組中新增、刪除、啟用或停用配接器時，系統將會傳送通知給群組配接器。</span><span class="sxs-lookup"><span data-stu-id="301e3-117">In addition, the system sends notifications to the group adapter any time an adapter is added, deleted, enabled, or disabled in the adapter group.</span></span> <span data-ttu-id="301e3-118">然而，群組配接器不會收到任何密碼變更通知。</span><span class="sxs-lookup"><span data-stu-id="301e3-118">However, the group adapter does not receive any password change notifications.</span></span>  
  
 <span data-ttu-id="301e3-119">配接器群組和群組配接器會選擇性使用管理工具。</span><span class="sxs-lookup"><span data-stu-id="301e3-119">Adapter groups and group adapters are optional using the Administration tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301e3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="301e3-120">See Also</span></span>  
 [<span data-ttu-id="301e3-121">密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="301e3-121">Password Sync Adapters</span></span>](../core/password-sync-adapters.md)