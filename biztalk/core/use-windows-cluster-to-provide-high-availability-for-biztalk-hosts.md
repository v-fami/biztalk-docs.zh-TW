---
title: 使用 Windows Server 叢集為 BizTalk Server Hosts2 提供高可用性 |Microsoft Docs
ms.custom: ''
ms.date: 2016-01-04
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Passive configuration [Master Secret server]
- Active configuration [Master Secret server]
- clustering, about clustering
- high availability
- Windows Server cluster, warnings
- installation, high availibility planning
- Master Secret server
- installation, configuring
- Master Secret server, configuring
- installation, Windows Server cluster
- clustering
ms.assetid: 4d7f0842-561e-49e0-ab08-504256b9294f
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8893bcd043ca046c310ee52276eb28476be4ea9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001175"
---
# <a name="using-windows-server-cluster-to-provide-high-availability-for-biztalk-server-hosts2"></a><span data-ttu-id="b4eee-102">使用 Windows Server 叢集為 BizTalk Server Hosts2 提供高可用性</span><span class="sxs-lookup"><span data-stu-id="b4eee-102">Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b4eee-103"> 提供可讓您設定 BizTalk 主控件做為 Windows Server 容錯移轉叢集群組中叢集資源的功能。</span><span class="sxs-lookup"><span data-stu-id="b4eee-103"> provides functionality that allows you to configure a BizTalk host as a clustered resource within a  Windows Server failover cluster group.</span></span> <span data-ttu-id="b4eee-104">主控件叢集支援可為不能在多個主控件執行個體中同時執行的整合式 BizTalk 配接器支援高可用性，例如 FTP 接收處理常式，或 POP3 接收處理常式 (在特定情況下)。</span><span class="sxs-lookup"><span data-stu-id="b4eee-104">Host cluster support is provided to support high availability for integrated BizTalk adapters that should not be run in multiple host instances simultaneously, such as the FTP receive handler or, under certain circumstances, the POP3 receive handler.</span></span> <span data-ttu-id="b4eee-105">在需要叢集 MSMQ 服務的實例中，主控件叢集支援也可確保 MSMQ 配接器所傳送或所接收訊息的交易一致性。</span><span class="sxs-lookup"><span data-stu-id="b4eee-105">Host cluster support is also provided to ensure transactional consistency for messages sent or received by the MSMQ adapter in scenarios that require that the MSMQ service is clustered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4eee-106">主控件叢集只能搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 企業版使用。</span><span class="sxs-lookup"><span data-stu-id="b4eee-106">Host clustering is only available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise Edition.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="b4eee-107">您可以叢集化 BizTalk 主控件之前，您必須設定至少兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組與 Windows Server 容錯移轉叢集的成員。</span><span class="sxs-lookup"><span data-stu-id="b4eee-107">Before you can cluster a BizTalk host, you must have configured at least two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group as members of a Windows Server Failover cluster.</span></span> <span data-ttu-id="b4eee-108">如需有關如何設定 Windows Server 容錯移轉叢集的詳細資訊，請參閱 Windows Server 線上說明。</span><span class="sxs-lookup"><span data-stu-id="b4eee-108">For more information about configuring a Windows Server Failover cluster, please see the Windows Server online help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4eee-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4eee-109">In This Section</span></span>  
  
-   [<span data-ttu-id="b4eee-110">在 Windows Server 叢集上安裝 BizTalk Server 的考量</span><span class="sxs-lookup"><span data-stu-id="b4eee-110">Considerations for Installing BizTalk Server on a Windows Server Cluster</span></span>](../core/considerations-for-installing-biztalk-server-on-a-windows-server-cluster2.md)  
  
-   [<span data-ttu-id="b4eee-111">如何將 BizTalk 主控件設定為叢集資源</span><span class="sxs-lookup"><span data-stu-id="b4eee-111">How to Configure a BizTalk Host as a Cluster Resource</span></span>](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md)  
  
-   [<span data-ttu-id="b4eee-112">在叢集主控件中執行配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="b4eee-112">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)