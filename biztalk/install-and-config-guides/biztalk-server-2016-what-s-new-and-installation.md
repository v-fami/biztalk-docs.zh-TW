---
title: "BizTalk Server 2016： 什麼是新的與安裝 |Microsoft 文件"
description: "什麼是新的並安裝與升級至 BizTalk Server 2016 的簡介"
ms.custom: 
ms.prod: biztalk-server
ms.date: 08/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229043b3-b1a4-47e9-9c0e-1fba5ec5b417
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 212eee411c78bacd3d46ca66762fc8fc0f25fa05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-2016-whats-new-and-installation"></a><span data-ttu-id="09f2d-103">BizTalk Server 2016：新功能與安裝</span><span class="sxs-lookup"><span data-stu-id="09f2d-103">BizTalk Server 2016: What's New, and Installation</span></span>

## <a name="get-started-with-biztalk-server-2016"></a><span data-ttu-id="09f2d-104">開始使用 BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="09f2d-104">Get started with BizTalk Server 2016</span></span>

[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]<span data-ttu-id="09f2d-105"> 是最新的內部部署版本。</span><span class="sxs-lookup"><span data-stu-id="09f2d-105"> is the latest on-premises release.</span></span> <span data-ttu-id="09f2d-106">這個新的版本可讓您使用新的 Logic Apps 配接器更緊密地整合 Azure，並使用 FILE 配接器和 WCF-SQL 配接器連接 Azure 資源。</span><span class="sxs-lookup"><span data-stu-id="09f2d-106">With this new version, you can expect closer integration with Azure using the new Logic Apps adapter, and connect to Azure resources using the File and WCF-SQL adapters.</span></span> 

<span data-ttu-id="09f2d-107">其中一個最大的變更是針對 SQL Server 2016 AlwaysOn 可用性群組 (AG) 的支援。</span><span class="sxs-lookup"><span data-stu-id="09f2d-107">One of the biggest changes is support for SQL Server 2016 AlwaysOn Availability Groups (AG).</span></span> <span data-ttu-id="09f2d-108">此支援涵蓋以內部部署方式使用 BizTalk Server，以及使用 BizTalk Server 的 Azure 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="09f2d-108">This support covers using BizTalk Server on-premises, and using BizTalk Server Azure virtual machines.</span></span> <span data-ttu-id="09f2d-109">您現在可以搭配使用 AlwaysOn 與 Azure 虛擬機器，來獲得高可用性的解決方案。</span><span class="sxs-lookup"><span data-stu-id="09f2d-109">With AlwaysOn, you can now have a highly-available solution using Azure virtual machines.</span></span>

<span data-ttu-id="09f2d-110">此外，還有 SHA-2 支援、匯入和匯出合作對象的繫結選項、管理主控台的改良功能等許多更新。</span><span class="sxs-lookup"><span data-stu-id="09f2d-110">There have also been updates to SHA-2 support, import and export binding options for parties, Administration console improvements, and much much more.</span></span> 

<span data-ttu-id="09f2d-111">在這組 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 主題中，我們著重在 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 的特定文件，包括變更項目及安裝的相關內容。</span><span class="sxs-lookup"><span data-stu-id="09f2d-111">In this [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] set of topics, we focus on the specific documentation for [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], including what's changed, and the installation.</span></span> <span data-ttu-id="09f2d-112">因此，如果您想要閱讀高可用性、監視 BIzTalk 環境等相關資訊，請參閱 [BizTalk Server 核心文件](../core/biztalk-server-core-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="09f2d-112">So, if you want to read about high availability, monitoring your BIzTalk environment, and more, then go to the [BizTalk Server core documentation](../core/biztalk-server-core-documentation.md).</span></span> <span data-ttu-id="09f2d-113">如果您想要設定 BizTalk Server，可參閱[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="09f2d-113">If you want to configure BizTalk Server, then go [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span> <span data-ttu-id="09f2d-114">如果您想要了解新功能並安裝 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，請使用下列入門連結：</span><span class="sxs-lookup"><span data-stu-id="09f2d-114">If you want to read about what's new, and install [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], then get started with the following links:</span></span>  

* [<span data-ttu-id="09f2d-115">新功能</span><span class="sxs-lookup"><span data-stu-id="09f2d-115">What's New</span></span>](../install-and-config-guides/what-s-new-in-biztalk-server-2016.md)  
* [<span data-ttu-id="09f2d-116">硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="09f2d-116">Hardware and Software Requirements</span></span>](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
* [<span data-ttu-id="09f2d-117">設定及安裝必要元件</span><span class="sxs-lookup"><span data-stu-id="09f2d-117">Set up and install prerequisites</span></span>](../install-and-config-guides/set-up-and-install-prerequisites-for-biztalk-server-2016.md)  
* [<span data-ttu-id="09f2d-118">安裝 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09f2d-118">Install BizTalk Server</span></span>](../install-and-config-guides/install-biztalk-server-2016.md)
* [<span data-ttu-id="09f2d-119">升級 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09f2d-119">Upgrade BizTalk Server</span></span>](../install-and-config-guides/upgrade-to-biztalk-server-2016.md)
  
## <a name="more-good-stuff"></a><span data-ttu-id="09f2d-120">更多實用功能</span><span class="sxs-lookup"><span data-stu-id="09f2d-120">More good stuff</span></span>
[<span data-ttu-id="09f2d-121">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09f2d-121">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)

[<span data-ttu-id="09f2d-122">設定叢集中的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09f2d-122">Configure BizTalk Server in a Cluster</span></span>](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)

[<span data-ttu-id="09f2d-123">環境最佳化的後續設定步驟</span><span class="sxs-lookup"><span data-stu-id="09f2d-123">Post-configuration steps to optimize your environment</span></span>](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)

[<span data-ttu-id="09f2d-124">匯入和匯出 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="09f2d-124">Import and Export BizTalk Server Configuration</span></span>](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)

[<span data-ttu-id="09f2d-125">合併 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="09f2d-125">Consolidate the BizTalk Server Databases</span></span>](../install-and-config-guides/consolidate-the-biztalk-server-databases2.md)

[<span data-ttu-id="09f2d-126">處理組態架構</span><span class="sxs-lookup"><span data-stu-id="09f2d-126">Working with the Configuration Framework</span></span>](../install-and-config-guides/working-with-the-configuration-framework.md)

[<span data-ttu-id="09f2d-127">保護 BizTalk Server 的部署安全</span><span class="sxs-lookup"><span data-stu-id="09f2d-127">Securing Your BizTalk Server Deployment</span></span>](../install-and-config-guides/securing-your-biztalk-server-deployment.md)

[<span data-ttu-id="09f2d-128">解除安裝並取消設定 BizTalk Server 以將其移除</span><span class="sxs-lookup"><span data-stu-id="09f2d-128">Uninstall and unconfigure BizTalk Server to remove it</span></span>](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)