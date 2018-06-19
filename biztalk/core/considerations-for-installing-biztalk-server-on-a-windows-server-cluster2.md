---
title: Windows Server Cluster2 上安裝 BizTalk Server 的考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Configure Your Server Wizard
- installing, Windows Server cluster
- BizTalk Server Configuration Wizard
- Windows Server cluster, warnings
- high availability, Windows Server cluster
- clustering, Windows Server cluster
- domain groups
- Windows Server cluster, Configure Your Server Wizard
- Network DTC access
- MSDTC
ms.assetid: 4daea7c6-7d26-440c-a2a0-fa018a25b2b3
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38bd34862efb0cd73e66a2c694abd26b823766db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237934"
---
# <a name="considerations-for-installing-biztalk-server-on-a-windows-server-cluster"></a><span data-ttu-id="ddbd6-102">在 Windows 伺服器叢集上安裝 BizTalk Server 的考量</span><span class="sxs-lookup"><span data-stu-id="ddbd6-102">Considerations for Installing BizTalk Server on a Windows Server Cluster</span></span>
<span data-ttu-id="ddbd6-103">在 Windows 伺服器叢集上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時必須有一些特殊考量。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-103">Special considerations must be made when installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a Windows Server cluster.</span></span> <span data-ttu-id="ddbd6-104">本主題將列出這些考量。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-104">This topic lists these considerations.</span></span>  
  
## <a name="a-non-clustered-biztalk-host-instance-should-not-be-run-on-a-windows-server-cluster-where-the-enterprise-sso-service-is-clustered"></a><span data-ttu-id="ddbd6-105">非叢集 BizTalk 主控件執行個體不應該在「企業單一登入」服務已叢集化的 Windows 伺服器叢集上執行</span><span class="sxs-lookup"><span data-stu-id="ddbd6-105">A non-clustered BizTalk host instance should not be run on a Windows Server cluster where the Enterprise SSO service is clustered</span></span>  
 <span data-ttu-id="ddbd6-106">建議的做法是在主動/被動組態中叢集化「企業單一登入主要密碼伺服器」，為主要密碼伺服器提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-106">It is a recommended practice to cluster the Enterprise Single Sign-On Master Secret Server in an active/passive configuration to provide high availability for the master secret server.</span></span> <span data-ttu-id="ddbd6-107">如果非叢集 BizTalk 主控件執行個體與「企業單一登入」服務的叢集執行個體在相同的叢集節點上執行，則一旦叢集「企業單一登入」服務移至叢集中的其他節點，BizTalk 主控件執行個體就會失效。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-107">If a non-clustered BizTalk host instance and a clustered instance of the Enterprise SSO service are running on the same cluster node, the BizTalk host instance will fail if the clustered Enterprise SSO service is moved to a different node in the cluster.</span></span> <span data-ttu-id="ddbd6-108">BizTalk 主控件與本機執行的「企業單一登入」服務執行個體保持相依。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-108">BizTalk Hosts maintain a dependency on a locally running instance of the Enterprise SSO service.</span></span> <span data-ttu-id="ddbd6-109">因此如果 「 企業單一登入 」 服務設定為叢集資源，然後在叢集節點上執行所有 BizTalk 主控件必須都設定為相同的叢集群組中叢集資源。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-109">Therefore if the Enterprise SSO service is configured as a clustered resource, then any BizTalk Hosts running on the cluster nodes must be configured as a clustered resource in the same cluster group.</span></span>  
  
## <a name="configure-the-microsoft-distributed-transaction-coordinator-msdtc-as-a-clustered-resource-before-installing-biztalk-server-on-a-cluster"></a><span data-ttu-id="ddbd6-110">在叢集上安裝 BizTalk Server 前，必須先將 Microsoft 分散式交易協調器 (MSDTC) 設定為叢集資源</span><span class="sxs-lookup"><span data-stu-id="ddbd6-110">Configure the Microsoft Distributed Transaction Coordinator (MSDTC) as a clustered resource before installing BizTalk Server on a cluster</span></span>  
 <span data-ttu-id="ddbd6-111">如果您打算在 Windows 伺服器叢集上安裝 BizTalk Server，必須先將 Microsoft 分散式交易協調器叢集化。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-111">If you plan to install BizTalk Server on a Windows Server cluster, you must cluster the Microsoft Distributed Transaction Coordinator first.</span></span>  
  
 <span data-ttu-id="ddbd6-112">若要在 Windows Server 2008 容錯移轉叢集上叢集 MSDTC，請遵循中概述的步驟[檢查清單： Windows Server 2008 容錯移轉叢集中建立 MS DTC 資源](http://go.microsoft.com/fwlink/?LinkID=129677)</span><span class="sxs-lookup"><span data-stu-id="ddbd6-112">To cluster MSDTC on a Windows Server 2008 failover cluster, follow the steps outlined in [Checklist: Creating an MS DTC Resource in a Windows Server 2008 Failover Cluster](http://go.microsoft.com/fwlink/?LinkID=129677)</span></span>  
  
## <a name="network-dtc-access-must-be-enabled-on-all-biztalk-servers-and-on-the-sql-server-before-installing-or-configuring-biztalk-server"></a><span data-ttu-id="ddbd6-113">所有 BizTalk Server 和 SQL Server，才能安裝或設定 BizTalk Server 上必須啟用網路 DTC 存取</span><span class="sxs-lookup"><span data-stu-id="ddbd6-113">Network DTC access must be enabled on all BizTalk Servers and on the SQL Server before installing or configuring BizTalk Server</span></span>  
 <span data-ttu-id="ddbd6-114">若要啟用網路 DTC 存取 SQL Server 將裝載 BizTalk Server 資料庫以及每個叢集節點上，請依照下列所述的步驟[如何啟用網頁伺服器上的 MSDTC](http://go.microsoft.com/fwlink/?LinkId=189701) (http://go.microsoft.com/fwlink/?LinkId=189701)。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-114">To enable network DTC access on each cluster node as well as on the SQL Server that will host the BizTalk Server databases, follow the steps outlined in [How to Enable MSDTC on a Web Server](http://go.microsoft.com/fwlink/?LinkId=189701) (http://go.microsoft.com/fwlink/?LinkId=189701).</span></span> <span data-ttu-id="ddbd6-115">必須啟用網路 DTC 存取，才能配合 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的交易支援。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-115">Network DTC access must be enabled to accommodate transactional support for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="ddbd6-116">建議您在完成該份知識庫文章中說明的步驟後重新啟動每一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-116">We recommend that you restart each server after completing the steps in this Knowledge Base article.</span></span>  
  
## <a name="you-must-manually-create-domain-groups-in-active-directory-before-you-configure-biztalk-server"></a><span data-ttu-id="ddbd6-117">您必須先在 Active Directory 中手動建立網域群組，然後再設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ddbd6-117">You must manually create domain groups in Active Directory before you configure BizTalk Server</span></span>  
 <span data-ttu-id="ddbd6-118">如果您安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]多部電腦，您必須指定網域群組和使用者帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態精靈。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-118">If you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on multiple computers, you must specify domain groups and user accounts in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard.</span></span> <span data-ttu-id="ddbd6-119">如果您使用網域群組您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態中，您必須手動建立群組之後再設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ddbd6-119">If you use domain groups for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration, you must manually create the groups before you configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>