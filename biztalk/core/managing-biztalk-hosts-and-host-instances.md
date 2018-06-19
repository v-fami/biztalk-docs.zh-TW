---
title: 管理 BizTalk 主控件和主控件執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [hosts]
- hosts, managing
- managing [hosts], about managing hosts
ms.assetid: 7f329804-ca44-4799-8a5d-38b3146d8e5e
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e60981f69bc3ff71bdd8581659f9cdd20f87467
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262582"
---
# <a name="managing-biztalk-hosts-and-host-instances"></a><span data-ttu-id="6c111-102">管理 BizTalk 主控件和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6c111-102">Managing BizTalk Hosts and Host Instances</span></span>
<span data-ttu-id="6c111-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件是一組零個以上 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段程序的邏輯集，您可以在其中部署如配接器處理常式、接收位置 (包括管線)，以及協調流程等項目。</span><span class="sxs-lookup"><span data-stu-id="6c111-103">A [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host is a logical set of zero or more [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time processes in which you deploy items such as adapter handlers, receive locations (including pipelines), and orchestrations.</span></span> <span data-ttu-id="6c111-104">如需主控件的詳細資訊，請參閱[主機](../core/hosts.md)。</span><span class="sxs-lookup"><span data-stu-id="6c111-104">For more information about hosts, see [Hosts](../core/hosts.md).</span></span>  
  
 <span data-ttu-id="6c111-105">主控件執行個體是處理、接收和傳輸訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="6c111-105">A host instance is the process where the message processing, receiving, and transmitting occurs.</span></span> <span data-ttu-id="6c111-106">您可以在每部執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、而且具有一或多個主控件與之對應的伺服器上安裝主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c111-106">You install a host instance on each server running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that has one or more hosts mapped to that server.</span></span> <span data-ttu-id="6c111-107">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="6c111-107">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="6c111-108">主控件具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="6c111-108">Hosts have the following characteristics:</span></span>  
  
-   <span data-ttu-id="6c111-109">主控件是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 物件的邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="6c111-109">Hosts are the logical containers of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="6c111-110">每部伺服器上僅能存在一個特定主控件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c111-110">Only one instance of a specific host can exist on each server.</span></span>  
  
-   <span data-ttu-id="6c111-111">您可以將一個主控件對應到多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="6c111-111">You can map one host to multiple servers.</span></span>  
  
 <span data-ttu-id="6c111-112">主控件執行個體具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="6c111-112">Host instances have the following characteristics:</span></span>  
  
-   <span data-ttu-id="6c111-113">主控件執行個體是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 物件的實體容器。</span><span class="sxs-lookup"><span data-stu-id="6c111-113">Host instances are the physical containers of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="6c111-114">當您將伺服器對應到主控件時，需建立主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c111-114">You create a host instance when you map a server to a host.</span></span>  
  
-   <span data-ttu-id="6c111-115">當負載平衡或是針對容錯移轉時，一部伺服器上可以有多個主控件執行個體 (屬於不同主控件)。</span><span class="sxs-lookup"><span data-stu-id="6c111-115">Multiple host instances (of different hosts) can exist on a server when load balancing or for failover.</span></span>  
  
 <span data-ttu-id="6c111-116">下圖顯示伺服器、主控件與主控件執行個體之間的關係。</span><span class="sxs-lookup"><span data-stu-id="6c111-116">The following figure shows the relationship between servers, hosts, and host instances.</span></span>  
  
 <span data-ttu-id="6c111-117">![主控件、 主控件執行個體和伺服器關係](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span><span class="sxs-lookup"><span data-stu-id="6c111-117">![Hosts, host instances, and server relationships](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span></span>  
<span data-ttu-id="6c111-118">主控件、主控件執行個體與伺服器之間的關係</span><span class="sxs-lookup"><span data-stu-id="6c111-118">Relationship between hosts, host instances, and servers</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c111-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="6c111-119">In This Section</span></span>  
  
-   [<span data-ttu-id="6c111-120">如何建立 BizTalk Server 主控件環境</span><span class="sxs-lookup"><span data-stu-id="6c111-120">How to Create a BizTalk Server Hosting Environment</span></span>](../core/how-to-create-a-biztalk-server-hosting-environment.md)  
  
-   [<span data-ttu-id="6c111-121">如何建立新的主機</span><span class="sxs-lookup"><span data-stu-id="6c111-121">How to Create a New Host</span></span>](../core/how-to-create-a-new-host.md)  
  
-   [<span data-ttu-id="6c111-122">如何修改主控件屬性</span><span class="sxs-lookup"><span data-stu-id="6c111-122">How to Modify Host Properties</span></span>](../core/how-to-modify-host-properties.md)  
  
-   [<span data-ttu-id="6c111-123">如何刪除主控件</span><span class="sxs-lookup"><span data-stu-id="6c111-123">How to Delete a Host</span></span>](../core/how-to-delete-a-host.md)  
  
-   [<span data-ttu-id="6c111-124">如何新增主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6c111-124">How to Add a Host Instance</span></span>](../core/how-to-add-a-host-instance.md)  
  
-   [<span data-ttu-id="6c111-125">如何啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6c111-125">How to Start a Host Instance</span></span>](../core/how-to-start-a-host-instance.md)  
  
-   [<span data-ttu-id="6c111-126">如何停止主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6c111-126">How to Stop a Host Instance</span></span>](../core/how-to-stop-a-host-instance.md)  
  
-   [<span data-ttu-id="6c111-127">如何刪除主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6c111-127">How to Delete a Host Instance</span></span>](../core/how-to-delete-a-host-instance.md)  
  
-   [<span data-ttu-id="6c111-128">如何修改主控件執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="6c111-128">How to Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)