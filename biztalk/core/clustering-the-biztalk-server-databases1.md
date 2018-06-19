---
title: 叢集 BizTalk Server Databases1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clustering, how to
- clustering, SQL Servers
- SQL Server, clustering
- BizTalk Server Configuration Wizard
- high availability, databases
- clustering, BizTalk Server Configuration Wizard
- clustering, databases
- clustering, prerequisites
ms.assetid: 9a1ed843-483b-4a56-961b-bc6801a07b64
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 983023ceb88618a540d922481c4cb185a076ae3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232430"
---
# <a name="clustering-the-biztalk-server-databases"></a><span data-ttu-id="f2ad6-102">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="f2ad6-102">Clustering the BizTalk Server Databases</span></span>
<span data-ttu-id="f2ad6-103">本節提供部署具有高可用性之 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案的指導方針。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-103">This section provides guidelines for deploying a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution with high availability.</span></span> <span data-ttu-id="f2ad6-104">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會變成無法使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境將無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-104">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases become unavailable, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment will not function correctly.</span></span> <span data-ttu-id="f2ad6-105">若要提供高可用性，您可以建立的 Microsoft SQL Server 叢集中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-105">To provide high availability, you can create a Microsoft SQL Server cluster for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="f2ad6-106">![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span><span class="sxs-lookup"><span data-stu-id="f2ad6-106">![BizTalk Server Database Tier](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span></span>  
  
 <span data-ttu-id="f2ad6-107">若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您必須擁有至少兩部電腦正在執行 SQL Server 和共用的磁碟陣列，以便使用的 Windows Server 容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-107">To provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must have at least two computers that are running SQL Server and a shared disk array for use by a  Windows Server Failover Cluster.</span></span>  
  
## <a name="procedures-for-clustering-the-databases"></a><span data-ttu-id="f2ad6-108">叢集資料庫的程序</span><span class="sxs-lookup"><span data-stu-id="f2ad6-108">Procedures for Clustering the Databases</span></span>  
  
#### <a name="before-you-start"></a><span data-ttu-id="f2ad6-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="f2ad6-109">Before you start</span></span>  
  
1.  <span data-ttu-id="f2ad6-110">當您建立網域群組的 BizTalk Server 環境時，您必須建立 Active Directory 網域全域群組。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-110">When you create the domain groups for your BizTalk Server environment, you must create Active Directory domain global groups.</span></span>  
  
2.  <span data-ttu-id="f2ad6-111">安裝及設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前，請先設定 SQL Server 叢集。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-111">Configure the SQL Server cluster before you install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f2ad6-112">如需叢集 SQL Server 的詳細資訊，請參閱[Alwayson 容錯移轉叢集執行個體](https://technet.microsoft.com/library/ms189134.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-112">For more information about clustering SQL Server, see [Always On Failover Cluster Instances](https://technet.microsoft.com/library/ms189134.aspx).</span></span>  
  
3.  <span data-ttu-id="f2ad6-113">若您也要叢集主要密碼伺服器，請先設定該伺服器。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-113">If you are also clustering the master secret server, configure that server first.</span></span> <span data-ttu-id="f2ad6-114">如需高可用性的企業單一登入，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-114">For more information about high availability for Enterprise Single Sign-On, see [High Availability for Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).</span></span>  
  
#### <a name="to-run-the-biztalk-server-configuration-wizard"></a><span data-ttu-id="f2ad6-115">若要執行 BizTalk Server 組態精靈</span><span class="sxs-lookup"><span data-stu-id="f2ad6-115">To run the BizTalk Server Configuration Wizard</span></span>  
  
1.  <span data-ttu-id="f2ad6-116">在執行階段伺服器上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-116">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a runtime server.</span></span>  
  
2.  <span data-ttu-id="f2ad6-117">啟動 「 BizTalk 組態 」 程式。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-117">Launch the BizTalk Configuration Program.</span></span> <span data-ttu-id="f2ad6-118">按一下**啟動**，指向 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-118">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
3.  <span data-ttu-id="f2ad6-119">請依照[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)套用自訂組態。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-119">Follow the steps in [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md) to apply a custom configuration.</span></span> <span data-ttu-id="f2ad6-120">若要指定 BizTalk 資料庫的 SQL Server 叢集，請輸入中的 SQL Server 叢集名稱**資料庫**對話方塊中所述的組態程式**編輯資料庫**區段本主題中。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-120">To specify the SQL Server cluster for the BizTalk databases, enter the name of the SQL Server cluster in the **Databases** dialog of the configuration program as described in the **Editing Databases** section of this topic.</span></span>  
  
4.  <span data-ttu-id="f2ad6-121">中的指示，完成 BizTalk Server 組態[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ad6-121">Complete the BizTalk Server configuration by following the instructions in [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ad6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2ad6-122">See Also</span></span>  
 [<span data-ttu-id="f2ad6-123">建立高可用性的 BizTalk Server 環境</span><span class="sxs-lookup"><span data-stu-id="f2ad6-123">Creating a Highly Available BizTalk Server Environment</span></span>](../core/creating-a-highly-available-biztalk-server-environment.md)