---
title: 步驟 1： 安裝基底平台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- platforms
- installing, base platform
- base platform
ms.assetid: 27da386f-90c7-414f-a4e3-e909f0c18371
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6eaae10965aa240af86ee381a3504a4ec64c8fc2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986951"
---
# <a name="step-1-installing-the-base-platform"></a><span data-ttu-id="537d3-102">步驟 1： 安裝基底平台</span><span class="sxs-lookup"><span data-stu-id="537d3-102">Step 1: Installing the Base Platform</span></span>
<span data-ttu-id="537d3-103">基底平台，請先安裝 Microsoft[!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)]和[!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)]使用預設安裝選項的每部伺服器上的 Service Pack 2。</span><span class="sxs-lookup"><span data-stu-id="537d3-103">For the base platform, install Microsoft [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] Service Pack 2 on each server using the default installation options.</span></span> <span data-ttu-id="537d3-104">請遵循下列建議：</span><span class="sxs-lookup"><span data-stu-id="537d3-104">Follow these recommendations:</span></span>  
  
## <a name="pre-installation"></a><span data-ttu-id="537d3-105">預先安裝</span><span class="sxs-lookup"><span data-stu-id="537d3-105">Pre-Installation</span></span>  
  
- <span data-ttu-id="537d3-106">在安裝軟體時，停用所有防毒軟體。</span><span class="sxs-lookup"><span data-stu-id="537d3-106">Disable all antivirus software during software installation.</span></span> <span data-ttu-id="537d3-107">某些防毒軟體程式可能會阻止正確安裝必要的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="537d3-107">Some antivirus software programs might prevent required software components from installing properly.</span></span>  
  
- <span data-ttu-id="537d3-108">請確定您輸入適當的授權資訊 （您已購買每一部伺服器的連線的數目上限）。</span><span class="sxs-lookup"><span data-stu-id="537d3-108">Make sure that you enter the appropriate licensing information (maximum number of connections you have purchased per server).</span></span> <span data-ttu-id="537d3-109">系統效能可能會受到可用的連線數目。</span><span class="sxs-lookup"><span data-stu-id="537d3-109">System performance can be affected by the number of available connections.</span></span>  
  
- <span data-ttu-id="537d3-110">請確定您已安裝 BizTalk Server 安裝所需的所有軟體必要條件。</span><span class="sxs-lookup"><span data-stu-id="537d3-110">Make sure that you have installed all the software prerequisites required for a BizTalk Server installation.</span></span> <span data-ttu-id="537d3-111">如需詳細資訊，請參閱 BizTalk Server 的安裝指示，在[ http://go.microsoft.com/fwlink/?LinkId=81041 ](http://go.microsoft.com/fwlink/?LinkId=81041)。</span><span class="sxs-lookup"><span data-stu-id="537d3-111">For more information, see the BizTalk Server Installation Instructions at [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).</span></span> <span data-ttu-id="537d3-112">[BizTalk 2013 R2 accelerator for SWIFT 的安裝指南](http://msdn.microsoft.com/library/d2b4a9f3-baeb-4fbc-9fda-5e4178832cd1)。</span><span class="sxs-lookup"><span data-stu-id="537d3-112">[Installation Guide for BizTalk 2013 R2 Accelerator for SWIFT](http://msdn.microsoft.com/library/d2b4a9f3-baeb-4fbc-9fda-5e4178832cd1).</span></span>  
  
- <span data-ttu-id="537d3-113">在離線環境中測試所有重大更新，然後再安裝在您的生產伺服器上。</span><span class="sxs-lookup"><span data-stu-id="537d3-113">Test all critical updates in an offline environment before installing them on your production servers.</span></span>  
  
- <span data-ttu-id="537d3-114">請確定您已安裝所有適用的 hotfix，您將安裝為部署一部分的所有產品。</span><span class="sxs-lookup"><span data-stu-id="537d3-114">Make sure that you install all the applicable hotfixes for all the products that you install as part of your deployment.</span></span> <span data-ttu-id="537d3-115">如需詳細資訊，請參閱下列來源：</span><span class="sxs-lookup"><span data-stu-id="537d3-115">For more information, see the following sources:</span></span>  
  
  - <span data-ttu-id="537d3-116">Microsoft BizTalk Server 線上說明</span><span class="sxs-lookup"><span data-stu-id="537d3-116">Microsoft BizTalk Server Online Help</span></span>  
  
  - <span data-ttu-id="537d3-117">在 BizTalk Server 安裝指示[ http://go.microsoft.com/fwlink/?LinkId=81041 ](http://go.microsoft.com/fwlink/?LinkId=81041)。</span><span class="sxs-lookup"><span data-stu-id="537d3-117">BizTalk Server Installation Instructions at [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).</span></span>  
  
  - <span data-ttu-id="537d3-118">Microsoft[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]網站，網址[ http://go.microsoft.com/fwlink/?linkid=48685 ](http://go.microsoft.com/fwlink/?linkid=48685)。</span><span class="sxs-lookup"><span data-stu-id="537d3-118">Microsoft [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Web site at [http://go.microsoft.com/fwlink/?linkid=48685](http://go.microsoft.com/fwlink/?linkid=48685).</span></span>  
  
  - <span data-ttu-id="537d3-119">Microsoft 下載中心網站位於[ http://go.microsoft.com/fwlink/?linkid=48686 ](http://go.microsoft.com/fwlink/?linkid=48686)。</span><span class="sxs-lookup"><span data-stu-id="537d3-119">Microsoft Download Center Web site at [http://go.microsoft.com/fwlink/?linkid=48686](http://go.microsoft.com/fwlink/?linkid=48686).</span></span>  
  
  - [!INCLUDE[btsWinUpdate](../../includes/btswinupdate-md.md)]<span data-ttu-id="537d3-120"> 網站，網址[ http://go.microsoft.com/fwlink/?linkid=48687 ](http://go.microsoft.com/fwlink/?linkid=48687)。</span><span class="sxs-lookup"><span data-stu-id="537d3-120"> Web site at [http://go.microsoft.com/fwlink/?linkid=48687](http://go.microsoft.com/fwlink/?linkid=48687).</span></span>  
  
- <span data-ttu-id="537d3-121">若要避免病毒的攻擊，從 CD 安裝的平台，並透過拔除任何纜線，並停用任何網路介面卡中斷網際網路連線的每一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="537d3-121">To avoid virus attacks, install the platform from a CD and disconnect each server from the Internet by unplugging any cables and disabling any network adapters.</span></span>  
  
- <span data-ttu-id="537d3-122">全新的磁碟分割，使用格式[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]NTFS 檔案系統。</span><span class="sxs-lookup"><span data-stu-id="537d3-122">Format a clean partition using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] NTFS file system.</span></span>  
  
## <a name="active-directory"></a><span data-ttu-id="537d3-123">Active Directory</span><span class="sxs-lookup"><span data-stu-id="537d3-123">Active Directory</span></span>  
  
-   <span data-ttu-id="537d3-124">建立的網域使用者身分**系統管理員**並將它新增至本機**系統管理員**群組部署中的每一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="537d3-124">Create a domain user called **Admin** and add it to the local **Administrators** group on every computer in your deployment.</span></span> <span data-ttu-id="537d3-125">在安裝期間，登入使用此網域帳戶的部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="537d3-125">At installation time, log on to the deployment servers using this domain account.</span></span>  
  
-   <span data-ttu-id="537d3-126">請勿設定任何網路介面卡，或在此時加入任何網域。</span><span class="sxs-lookup"><span data-stu-id="537d3-126">Do not configure any network adapters or join any domains at this time.</span></span> <span data-ttu-id="537d3-127">本指南說明如何在開始部署程序時，稍後再設定這些設定。</span><span class="sxs-lookup"><span data-stu-id="537d3-127">This guide describes how to configure these settings later when you begin the deployment process.</span></span>  
  
## <a name="internal-web-servers-mrsr-site"></a><span data-ttu-id="537d3-128">內部網頁伺服器 （MRSR 站台）</span><span class="sxs-lookup"><span data-stu-id="537d3-128">Internal Web Servers (MRSR site)</span></span>  
  
-   <span data-ttu-id="537d3-129">請確定只在 MRSR 站台伺服器上已安裝 Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="537d3-129">Make sure that Internet Information Services (IIS) is installed only on the MRSR site Servers.</span></span>  
  
-   <span data-ttu-id="537d3-130">請確定 Internet Security and Acceleration (ISA) Server 上未安裝，Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="537d3-130">Make sure that Internet Information Services (IIS) is not installed on the Internet Security and Acceleration (ISA) Server.</span></span>  
  
-   <span data-ttu-id="537d3-131">請確定只在 MRSR 站台伺服器上已安裝 Message Queuing (MSMQ) 服務。</span><span class="sxs-lookup"><span data-stu-id="537d3-131">Make sure that the Message Queuing (MSMQ) service is installed only on the MRSR site Servers.</span></span> <span data-ttu-id="537d3-132">如果 BizTalk 傳訊的伺服器也會當做 MRSR 站台伺服器，請勿在這些伺服器上安裝 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="537d3-132">If the BizTalk Messaging servers will also be used as the MRSR site Servers, do not install MSMQ on those servers.</span></span>