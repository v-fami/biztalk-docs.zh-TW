---
title: "安裝 BizTalk Adapter Pack 2016 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23c74470-6336-49be-95c3-32b5c279e0ab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fec17ce2da0183b9029839d3054261c5db3952a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-biztalk-adapter-pack-2016"></a><span data-ttu-id="4afd7-102">安裝 BizTalk Adapter Pack 2016</span><span class="sxs-lookup"><span data-stu-id="4afd7-102">Install the BizTalk Adapter Pack 2016</span></span>
## <a name="overview"></a><span data-ttu-id="4afd7-103">概觀</span><span class="sxs-lookup"><span data-stu-id="4afd7-103">Overview</span></span>

<span data-ttu-id="4afd7-104">[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] (BAP) 隨附於[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4afd7-104">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] (BAP) is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="4afd7-105">因此，當您下載[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，您也要將下載中的配接器[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4afd7-105">So when you download [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], you are also downloading the adapters in the [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)].</span></span> 

<span data-ttu-id="4afd7-106">[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)]使用[!INCLUDE[firstref_btsWinCommFoundation_md](../includes/firstref-btswincommfoundation-md.md)]與不同的企業的特定業務 (LOB) 系統進行通訊。</span><span class="sxs-lookup"><span data-stu-id="4afd7-106">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] uses the [!INCLUDE[firstref_btsWinCommFoundation_md](../includes/firstref-btswincommfoundation-md.md)] to communicate with different enterprise line-of-business (LOB) systems.</span></span> <span data-ttu-id="4afd7-107">[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)]都有它自己組需求，其本身的安裝經驗和它自己的安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="4afd7-107">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] has its own set of requirements, its own setup experience, and its own installation steps.</span></span> 

<span data-ttu-id="4afd7-108">[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)]為選擇性，而且如果您想要則只需要[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]傳送或接收任何下列企業 LOB 系統訊息：</span><span class="sxs-lookup"><span data-stu-id="4afd7-108">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] is optional, and is only needed if you want [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to send or receive messages to any of the following enterprise LOB systems:</span></span> 

* <span data-ttu-id="4afd7-109">Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="4afd7-109">Oracle Database</span></span>
* <span data-ttu-id="4afd7-110">Oracle E-business Suite (EBS)</span><span class="sxs-lookup"><span data-stu-id="4afd7-110">Oracle E-Business Suite (EBS)</span></span>
* <span data-ttu-id="4afd7-111">SAP</span><span class="sxs-lookup"><span data-stu-id="4afd7-111">SAP</span></span>
* <span data-ttu-id="4afd7-112">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4afd7-112">SQL Server</span></span>
* <span data-ttu-id="4afd7-113">Siebel</span><span class="sxs-lookup"><span data-stu-id="4afd7-113">Siebel</span></span>

<span data-ttu-id="4afd7-114">每個版本[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]包含它自己[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="4afd7-114">Every version of [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] includes its own [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] version.</span></span> <span data-ttu-id="4afd7-115">隨附的版本您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]支援版本。</span><span class="sxs-lookup"><span data-stu-id="4afd7-115">Only the version included with your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version is supported.</span></span> <span data-ttu-id="4afd7-116">它們不是與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="4afd7-116">They are not backward-compatible.</span></span>

<span data-ttu-id="4afd7-117">本文件列出的軟體需求，以及的步驟，安裝 Microsoft BizTalk 配接器組件 (BAP) 隨附[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4afd7-117">This document lists the software requirements, and the steps to install the Microsoft BizTalk Adapter Pack (BAP) included with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].</span></span> 

## <a name="get-started-here"></a><span data-ttu-id="4afd7-118">從這裡開始使用</span><span class="sxs-lookup"><span data-stu-id="4afd7-118">Get started here</span></span>
[<span data-ttu-id="4afd7-119">軟體必要條件</span><span class="sxs-lookup"><span data-stu-id="4afd7-119">Software prerequisites</span></span>](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="4afd7-120">安裝步驟</span><span class="sxs-lookup"><span data-stu-id="4afd7-120">Install steps</span></span>](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="4afd7-121">後續安裝步驟</span><span class="sxs-lookup"><span data-stu-id="4afd7-121">Post installation steps</span></span>](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="4afd7-122">更新或解除安裝</span><span class="sxs-lookup"><span data-stu-id="4afd7-122">Update or uninstall</span></span>](../adapters-and-accelerators/update-or-uninstall-the-biztalk-adapter-pack-2016.md)