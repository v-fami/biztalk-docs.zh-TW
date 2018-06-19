---
title: 向外延展傳送主控件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hosts, sending
- FTP adapters, high availability
- EDI adapters, high availability
- hosts, high availability
- hosts, availability
- Windows SharePoint Services adapters, high availability
- scaling, hosts
- hosts, clustering
- scaling, adapters
- high availability, hosts
- clustering, hosts
- MSMQ adapters, high availability
- hosts, planning
- hosts, scaling
- adapters, scaling
ms.assetid: a3d79e0b-8c1e-471c-88e2-623600dfd81a
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50659e267731caafe4bad6dabe89944cb16c0c98
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007743"
---
# <a name="scaled-out-sending-hosts"></a><span data-ttu-id="d7b48-102">向外擴充的傳送主控件</span><span class="sxs-lookup"><span data-stu-id="d7b48-102">Scaled-Out Sending Hosts</span></span>
<span data-ttu-id="d7b48-103">向外擴充的傳送主控件可確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的傳送功能為高度可用。</span><span class="sxs-lookup"><span data-stu-id="d7b48-103">A scaled-out sending host makes sure that the sending functionality in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is highly available.</span></span> <span data-ttu-id="d7b48-104">若您將多部電腦新增至傳送訊息的主控件，則可執行多個傳送主控件執行個體以獲得備援與高可用性。</span><span class="sxs-lookup"><span data-stu-id="d7b48-104">If you add multiple computers to a host for sending messages, you can run multiple sending host instances for redundancy and high availability.</span></span>  
  
 <span data-ttu-id="d7b48-105">下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的部署，它有兩部執行傳送主控件執行個體的電腦，可為傳送主控件提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="d7b48-105">The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability for the sending host by having two computers that are running instances of the sending host.</span></span> <span data-ttu-id="d7b48-106">請注意，在此圖中接收和處理主控件不是高度可用。</span><span class="sxs-lookup"><span data-stu-id="d7b48-106">Note that in this figure the receiving and processing hosts are not highly available.</span></span>  
  
 <span data-ttu-id="d7b48-107">![調整 &#45; Out 傳送主機](../core/media/tdi-ha-scalesend.gif "TDI_HA_ScaleSend")</span><span class="sxs-lookup"><span data-stu-id="d7b48-107">![Scaled&#45;Out Sending Host](../core/media/tdi-ha-scalesend.gif "TDI_HA_ScaleSend")</span></span>  
  
## <a name="high-availability-for-sending-hosts"></a><span data-ttu-id="d7b48-108">傳送主控件的高可用性</span><span class="sxs-lookup"><span data-stu-id="d7b48-108">High Availability for Sending Hosts</span></span>  
 <span data-ttu-id="d7b48-109">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的傳送功能與處理功能相似，因為這些活動都不需要主控件與資料之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="d7b48-109">Sending functionality in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is similar to processing functionality in the sense that neither of these activities requires any association between host and data.</span></span> <span data-ttu-id="d7b48-110">就如同任何處理主控件執行個體都可以從 MessageBox 資料庫擷取訊息並處理它們，任何傳送主控件執行個體也可以從 MessageBox 資料庫擷取訊息並傳送它們。</span><span class="sxs-lookup"><span data-stu-id="d7b48-110">Just as any processing host instance can retrieve messages from the MessageBox database and process them, any sending host instance can retrieve messages from the MessageBox database and send them.</span></span> <span data-ttu-id="d7b48-111">因此，為傳送主控件提供高可用性表示您可以使用相同的技術為處理主控件提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="d7b48-111">Therefore, providing high availability for the sending hosts means that you use the same techniques as for providing high availability for the processing hosts.</span></span>  
  
## <a name="scaling-the-biztalk-server-send-adapters"></a><span data-ttu-id="d7b48-112">擴充 BizTalk Server 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="d7b48-112">Scaling the BizTalk Server Send Adapters</span></span>  
  
### <a name="high-availability-for-the-msmq-send-adapter"></a><span data-ttu-id="d7b48-113">MSMQ 傳送配接器的高可用性</span><span class="sxs-lookup"><span data-stu-id="d7b48-113">High Availability for the MSMQ Send Adapter</span></span>  
 <span data-ttu-id="d7b48-114">若要為 MSMQ 傳送配接器提供高可用性，您應該叢集 MSMQ 服務、在與叢集 MSMQ 服務相同群組中叢集 BizTalk 主控件，並設定 MSMQ 傳送處理常式以便在此叢集 BizTalk 主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="d7b48-114">To provide high availability for the MSMQ send adapter you should cluster the MSMQ service, cluster a BizTalk host in the same group as the clustered MSMQ service, and configure the MSMQ send handler to run in this clustered BizTalk host.</span></span> <span data-ttu-id="d7b48-115">您應執行這些動作以確保 MSMQ 配接器所初始化的交易傳送的一致性。</span><span class="sxs-lookup"><span data-stu-id="d7b48-115">This should be done to ensure the consistency of transactional sends initiated by the MSMQ adapter.</span></span> <span data-ttu-id="d7b48-116">如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b48-116">For more information see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
### <a name="high-availability-for-the-windows-sharepoint-services-send-adapter"></a><span data-ttu-id="d7b48-117">Windows SharePoint Services 傳送配接器的高可用性</span><span class="sxs-lookup"><span data-stu-id="d7b48-117">High Availability for the Windows SharePoint Services Send Adapter</span></span>  
 <span data-ttu-id="d7b48-118">若要為 Windows SharePoint Services 傳送配接器提供高可用性，請將多部電腦新增至傳送主控件，並讓其中每部主控件電腦都參考相同的文件庫。</span><span class="sxs-lookup"><span data-stu-id="d7b48-118">To provide high availability for the Windows SharePoint Services send adapter, add multiple computers to the send host with the send port on each host computer referencing the same document library.</span></span> <span data-ttu-id="d7b48-119">Windows SharePoint Services 配接器會藉由 SharePoint 電腦上的 BizTalk 所安裝的 Windows SharePoint Services web 服務呼叫，將訊息傳送至 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="d7b48-119">The Windows SharePoint Services adapter sends messages to SharePoint by calling into the Windows SharePoint Services web service installed by BizTalk on the SharePoint machine.</span></span> <span data-ttu-id="d7b48-120">此為 SharePoint 傳送配接器讓您將訊息推送到相同 HTTP URL 指向 SharePoint NLB 安裝的多個主控件執行個體上執行相同的傳送埠，BizTalk Server 會提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="d7b48-120">BizTalk Server provides high availability for the SharePoint send adapter by letting you run the same send ports on multiple host instances that push messages to the same HTTP URL pointing to a SharePoint NLB installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b48-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b48-121">See Also</span></span>  
 <span data-ttu-id="d7b48-122">[為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="d7b48-122">[Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md) </span></span>  
 [<span data-ttu-id="d7b48-123">在叢集主控件中執行配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="d7b48-123">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)