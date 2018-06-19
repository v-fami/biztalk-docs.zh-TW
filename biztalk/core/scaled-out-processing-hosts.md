---
title: 向外延展處理主控件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability
- hosts, processing
- hosts, high availability
- scaling, hosts
- hosts, planning
- hosts, scaling
- clustering
ms.assetid: c72ce8fc-7593-4700-8398-23d1a20515c3
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01ee36777a5c64713fd31e86fe6ef2a1886b3348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269326"
---
# <a name="scaled-out-processing-hosts"></a><span data-ttu-id="50a76-102">向外擴充的處理主控件</span><span class="sxs-lookup"><span data-stu-id="50a76-102">Scaled-Out Processing Hosts</span></span>
<span data-ttu-id="50a76-103">向外擴充的處理主控件藉由隔離協調流程功能在兩部或以上不同的主控件電腦上，以改善效能和提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="50a76-103">A scaled-out processing host improves performance and provides high availability by isolating orchestration functionality onto two or more separate host computers.</span></span> <span data-ttu-id="50a76-104">此隔離可讓您新增多部電腦至處理主控件，以獲得備援。</span><span class="sxs-lookup"><span data-stu-id="50a76-104">This isolation lets you add multiple computers to a processing host for redundancy.</span></span> <span data-ttu-id="50a76-105">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的處理主控件會執行一或多個主控件執行個體，以協調各種商務程序並為協調流程建立程式物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="50a76-105">A processing host in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runs one or more host instances that coordinate various business processes and creates an instance of programmatic objects for orchestrations.</span></span>  
  
 <span data-ttu-id="50a76-106">下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署，此部署具有兩部執行執行處理主控件的電腦，可為處理主控件提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="50a76-106">The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability for the processing host by having two computers that are running instances of the processing host.</span></span> <span data-ttu-id="50a76-107">請注意，在此圖中接收和傳送主控件不是高度可用。</span><span class="sxs-lookup"><span data-stu-id="50a76-107">Note that in this figure the receiving and sending hosts are not highly available.</span></span>  
  
 <span data-ttu-id="50a76-108">![向外延展處理主控件](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")</span><span class="sxs-lookup"><span data-stu-id="50a76-108">![Scaled Out Processing Host](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")</span></span>  
  
 <span data-ttu-id="50a76-109">在此組態中，處理協調流程的工作可在兩部具有處理主控件執行個體且可獨立執行的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦之間平衡負載。</span><span class="sxs-lookup"><span data-stu-id="50a76-109">In this configuration, the work for processing orchestrations is load balanced between two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers that have instances of the processing host and run independently of each other.</span></span> <span data-ttu-id="50a76-110">若其中一部電腦發生錯誤或失敗，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動使用另一部電腦上的主控件執行個體來處理其餘的協調流程。</span><span class="sxs-lookup"><span data-stu-id="50a76-110">If one computer encounters errors or fails, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically uses the host instance on the other computer to process remaining orchestrations.</span></span>  
  
## <a name="maintaining-orchestration-state"></a><span data-ttu-id="50a76-111">維護協調流程狀態</span><span class="sxs-lookup"><span data-stu-id="50a76-111">Maintaining Orchestration State</span></span>  
 <span data-ttu-id="50a76-112">BizTalk Server 是在 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 中集中維護協調流程狀態，而不是在每一部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上以本機方式來維護。</span><span class="sxs-lookup"><span data-stu-id="50a76-112">BizTalk Server maintains orchestration state centrally in Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and not locally on each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span> <span data-ttu-id="50a76-113">藉由將狀態保存在 MessageBox 資料庫中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 克服了依賴單一處理主控件執行個體處理協調流程的限制，而且讓任何處理主控件執行個體都可以處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="50a76-113">By persisting the state in the MessageBox database, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] overcomes the limitation of relying on a single processing host instance to process the orchestration, and lets any processing host instance process the orchestration.</span></span> <span data-ttu-id="50a76-114">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在處理協調流程時發生錯誤，另一個相同的處理主控件執行個體將可從上次保存的狀態完成協調流程。</span><span class="sxs-lookup"><span data-stu-id="50a76-114">If an error occurs while [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes an orchestration, another instance of the same processing host can complete the orchestration from the last persisted state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a76-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50a76-115">See Also</span></span>  
 [<span data-ttu-id="50a76-116">為 BizTalk 主控件提供高可用性</span><span class="sxs-lookup"><span data-stu-id="50a76-116">Providing High Availability for BizTalk Hosts</span></span>](../core/providing-high-availability-for-biztalk-hosts.md)