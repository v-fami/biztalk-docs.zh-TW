---
title: 安裝 FileAct 和互動配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf387d59-373b-4151-9dfd-30c511978862
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a3beccd6179bcb4526ba41f4f41a7923f5f966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224166"
---
# <a name="install-the-fileact-and-interact-adapter"></a><span data-ttu-id="74e4a-102">安裝 FileAct 和互動配接器</span><span class="sxs-lookup"><span data-stu-id="74e4a-102">Install the FileAct and InterAct Adapter</span></span>
<span data-ttu-id="74e4a-103">本節提供安裝指示[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]– for SWIFT。</span><span class="sxs-lookup"><span data-stu-id="74e4a-103">This section provides instructions to install [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] – for SWIFT.</span></span> <span data-ttu-id="74e4a-104">安裝配接器之前，您必須安裝先決條件軟體。</span><span class="sxs-lookup"><span data-stu-id="74e4a-104">Before you install the adapters, you must install the prerequisite software.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="74e4a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="74e4a-105">Prerequisites</span></span>  

* <span data-ttu-id="74e4a-106">使用屬於本機 administrators 群組的成員，以及 BizTalk Server 系統管理員群組的成員帳戶登入</span><span class="sxs-lookup"><span data-stu-id="74e4a-106">Sign in with an account that is member of the local administrators group, and a member of the BizTalk Server Administrators group</span></span>
  
## <a name="step-1-install-biztalk-server-and-configure-bam"></a><span data-ttu-id="74e4a-107">步驟 1： 安裝 BizTalk Server 及設定 BAM</span><span class="sxs-lookup"><span data-stu-id="74e4a-107">Step 1: Install BizTalk Server and configure BAM</span></span>

1. <span data-ttu-id="74e4a-108">安裝[BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md)，或[BizTalk Server 2013 R2 / 2013年](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)，並安裝商務活動監控 (BAM)。</span><span class="sxs-lookup"><span data-stu-id="74e4a-108">Install [BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md), or [BizTalk Server 2013 R2 / 2013](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md), and install Business Activity Monitoring (BAM).</span></span>

2. <span data-ttu-id="74e4a-109">設定[BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md)，並設定商務活動監控 (BAM)。</span><span class="sxs-lookup"><span data-stu-id="74e4a-109">Configure [BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md), and configure Business Activity Monitoring (BAM).</span></span>
  
3. <span data-ttu-id="74e4a-110">請確定您有足夠的安全性權限可以存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="74e4a-110">Make sure you have enough security privileges to access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="74e4a-111">[BizTalk Server 的最小安全性權限](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)是絕佳的資源。</span><span class="sxs-lookup"><span data-stu-id="74e4a-111">[Minimum Security Rights for BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) is a great resource.</span></span>
  
## <a name="step-2-install-biztalk-accelerator-for-swift-a4swift"></a><span data-ttu-id="74e4a-112">步驟 2： 安裝 BizTalk Accelerator for SWIFT (A4SWIFT)</span><span class="sxs-lookup"><span data-stu-id="74e4a-112">Step 2: Install BizTalk Accelerator for SWIFT (A4SWIFT)</span></span>  

<span data-ttu-id="74e4a-113">安裝和設定[BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md)。</span><span class="sxs-lookup"><span data-stu-id="74e4a-113">Install and configure the [BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md).</span></span>

  
## <a name="step-3-install-swiftalliance-gateway-sag"></a><span data-ttu-id="74e4a-114">步驟 3： 安裝 SWIFTAlliance 閘道 (SAG)</span><span class="sxs-lookup"><span data-stu-id="74e4a-114">Step 3: Install SWIFTAlliance Gateway (SAG)</span></span>  
 <span data-ttu-id="74e4a-115">安裝 FileAct 和 InterAct 配接器之前，請建立 SAG 訊息夥伴、 結束點和路由規則，並測試安裝 FileAct 和 InterAct 配接器的電腦上的 SAG 連線能力。</span><span class="sxs-lookup"><span data-stu-id="74e4a-115">Before you install the FileAct and InterAct adapters, create the SAG Message Partners, End Points, and Routing Rules, and test the SAG connectivity on the computer where you install the FileAct and InterAct adapters.</span></span>

<span data-ttu-id="74e4a-116">請參閱[https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway)如 SWIFTAlliance 閘道上的特定詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="74e4a-116">See [https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway) for specific details on the SWIFTAlliance Gateway.</span></span>  

## <a name="step-4-install-the-biztalk-fileact-and-interact-adapters"></a><span data-ttu-id="74e4a-117">步驟 4： 安裝 BizTalk FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="74e4a-117">Step 4: Install the BizTalk FileAct and InterAct adapters</span></span>  
  
1. <span data-ttu-id="74e4a-118">執行**Setup.exe**以系統管理員身分來啟動安裝。</span><span class="sxs-lookup"><span data-stu-id="74e4a-118">Run the **Setup.exe** as administrator to start the installation.</span></span>  
  
2.  <span data-ttu-id="74e4a-119">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="74e4a-119">Select **Install**.</span></span>  
  
3.  <span data-ttu-id="74e4a-120">輸入您的使用者名稱和組織名稱，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="74e4a-120">Enter your user name and organization name, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="74e4a-121">**接受**授權合約。</span><span class="sxs-lookup"><span data-stu-id="74e4a-121">**Accept** the license agreement.</span></span>
  
5.  <span data-ttu-id="74e4a-122">在**安裝選項**頁面上，執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="74e4a-122">On the **Installation Options** page, do one of the following:</span></span>  
  
    -   <span data-ttu-id="74e4a-123">選取**完成**選項來安裝所有元件的 FileAct 和 InterAct adapters。</span><span class="sxs-lookup"><span data-stu-id="74e4a-123">Select the **Complete** option to install all components of the FileAct and InterAct adapters.</span></span>  
  
    -   <span data-ttu-id="74e4a-124">選取**自訂**選項以選擇要安裝哪些元件。</span><span class="sxs-lookup"><span data-stu-id="74e4a-124">Select the **Custom** option to choose which components to install.</span></span>  
  
     <span data-ttu-id="74e4a-125">確認安裝位置，或選取**瀏覽**以選取不同的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="74e4a-125">Verify the installation location, or select **Browse** to select a different installation location.</span></span> <span data-ttu-id="74e4a-126">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="74e4a-126">Select **Next**.</span></span>  
  
6.  <span data-ttu-id="74e4a-127">在**摘要**頁面上，選取**安裝**安裝列出的元件。</span><span class="sxs-lookup"><span data-stu-id="74e4a-127">On the **Summary** page, select **Install** to install the listed components.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="74e4a-128">當**執行組態精靈**是選取 （預設值）， **Microsoft BizTalk FileAct 與互動的介面卡設定**精靈會自動執行時您所選取**完成**.</span><span class="sxs-lookup"><span data-stu-id="74e4a-128">When **Run Configuration Wizard** is selected (the default), the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard runs automatically when you select **Finish**.</span></span>  
  
7. <span data-ttu-id="74e4a-129">當安裝完成時，選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="74e4a-129">When the installation completes, select **Finish**.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="74e4a-130">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="74e4a-130">Next steps</span></span>

[<span data-ttu-id="74e4a-131">設定 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="74e4a-131">Configure the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/configure-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="74e4a-132">範例互動和 FileAct 訊息</span><span class="sxs-lookup"><span data-stu-id="74e4a-132">Sample InterAct and FileAct messages</span></span>](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)  
[<span data-ttu-id="74e4a-133">解除安裝或修復 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="74e4a-133">Uninstall or repair the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="74e4a-134">請閱讀的已知問題的安裝</span><span class="sxs-lookup"><span data-stu-id="74e4a-134">Read the installation known issues</span></span>](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
  
## <a name="see-also"></a><span data-ttu-id="74e4a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74e4a-135">See Also</span></span>  
[<span data-ttu-id="74e4a-136">FileAct 和 InterAct 配接器使用者入門</span><span class="sxs-lookup"><span data-stu-id="74e4a-136">Getting started with the FileAct and InterAct adapters</span></span>](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)  
[<span data-ttu-id="74e4a-137">了解 FileAct 和 InterAct 配接器架構</span><span class="sxs-lookup"><span data-stu-id="74e4a-137">Understanding FileAct and InterAct adapter architecture</span></span>](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)