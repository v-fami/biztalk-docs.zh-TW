---
title: 系統管理員 （BizTalk Server 範例資料夾） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SDK examples
- examples, administering
- administering, examples
ms.assetid: 178d0ee2-d437-4945-a35d-1a8be524aff1
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d50da9489338ff9b3bf00dd829d7001b12d1b93c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230990"
---
# <a name="admin-biztalk-server-samples-folder"></a><span data-ttu-id="63eee-102">系統管理員 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="63eee-102">Admin (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="63eee-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的軟體開發套件 (SDK) 中包含數個管理範例。</span><span class="sxs-lookup"><span data-stu-id="63eee-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several administration samples in its software development kit (SDK).</span></span> <span data-ttu-id="63eee-104">本節提供每個管理範例所示範之功能的詳細資訊、用來建置和執行範例的指示，以及您可以預期的結果。</span><span class="sxs-lookup"><span data-stu-id="63eee-104">This section provides detailed information about the functionality demonstrated by each administration sample, instructions for building and running the sample, and the results you can expect.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="63eee-105">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="63eee-105">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="63eee-106">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="63eee-106">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63eee-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="63eee-107">In This Section</span></span>  
  
-   <span data-ttu-id="63eee-108">[系統管理員 ExplorerOM （BizTalk Server 範例資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-108">[Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md).</span></span>  
  
    -   <span data-ttu-id="63eee-109">[（BizTalk Server 範例） ApplicationManager](../core/applicationmanager-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-109">[ApplicationManager (BizTalk Server Sample)](../core/applicationmanager-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-110">示範如何啟動或停止 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="63eee-110">Demonstrates how to start or stop a BizTalk application.</span></span>  
  
    -   <span data-ttu-id="63eee-111">[（BizTalk Server 範例） BrowsingArtifacts](../core/browsingartifacts-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-111">[BrowsingArtifacts (BizTalk Server Sample)](../core/browsingartifacts-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-112">示範如何列舉 BizTalk 成品和屬性。</span><span class="sxs-lookup"><span data-stu-id="63eee-112">Demonstrates how to enumerate BizTalk artifacts and attributes.</span></span>  
  
    -   <span data-ttu-id="63eee-113">[CBR （BizTalk Server 範例）](../core/cbr-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-113">[CBR (BizTalk Server Sample)](../core/cbr-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-114">示範如何加入和設定新的內容為基礎的路由的 BizTalk 訊息的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="63eee-114">Demonstrates adding and configuring new send ports for content based routing of BizTalk messages.</span></span>  
  
    -   <span data-ttu-id="63eee-115">[DeleteParty （BizTalk Server 範例）](../core/deleteparty-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-115">[DeleteParty (BizTalk Server Sample)](../core/deleteparty-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-116">示範如何刪除指定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="63eee-116">Demonstrates how to delete a specified party.</span></span>  
  
    -   <span data-ttu-id="63eee-117">[OrchestrationBinding （BizTalk Server 範例）](../core/orchestrationbinding-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-117">[OrchestrationBinding (BizTalk Server Sample)](../core/orchestrationbinding-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-118">示範如何管理及設定協調流程。</span><span class="sxs-lookup"><span data-stu-id="63eee-118">Demonstrates how to manage and configure orchestrations.</span></span>  
  
    -   <span data-ttu-id="63eee-119">[（BizTalk Server 範例） PartnerManagement](../core/partnermanagement-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-119">[PartnerManagement (BizTalk Server Sample)](../core/partnermanagement-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-120">示範如何建立和刪除合作對象。</span><span class="sxs-lookup"><span data-stu-id="63eee-120">Demonstrates creating and deleting parties.</span></span> <span data-ttu-id="63eee-121">也會示範與角色登錄和取消登錄合作對象。</span><span class="sxs-lookup"><span data-stu-id="63eee-121">Also demonstrates enlisting and unenlisting parties with roles.</span></span>  
  
    -   <span data-ttu-id="63eee-122">[ReceiveLocations （BizTalk Server 範例）](../core/receivelocations-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-122">[ReceiveLocations (BizTalk Server Sample)](../core/receivelocations-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-123">示範如何建立和管理接收埠的接收位置。</span><span class="sxs-lookup"><span data-stu-id="63eee-123">Demonstrates how to create and manage receive locations for receive ports.</span></span>  
  
    -   <span data-ttu-id="63eee-124">[接收埠 （BizTalk Server 範例）](../core/receiveports-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-124">[ReceivePorts (BizTalk Server Sample)](../core/receiveports-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-125">示範建立、 列舉和刪除接收埠。</span><span class="sxs-lookup"><span data-stu-id="63eee-125">Demonstrates creating, enumerating and deleting receive ports.</span></span>  
  
    -   <span data-ttu-id="63eee-126">[傳送埠群組 （BizTalk Server 範例）](../core/sendportgroups-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-126">[SendPortGroups (BizTalk Server Sample)](../core/sendportgroups-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-127">示範如何列舉和管理傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="63eee-127">Demonstrates how to enumerate and manage send port groups.</span></span>  
  
    -   <span data-ttu-id="63eee-128">[SendPorts （BizTalk Server 範例）](../core/sendports-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-128">[SendPorts (BizTalk Server Sample)](../core/sendports-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-129">示範如何列舉和管理傳送埠。</span><span class="sxs-lookup"><span data-stu-id="63eee-129">Demonstrates how to enumerate and manage send ports.</span></span>  
  
    -   <span data-ttu-id="63eee-130">[UnenlistParties （BizTalk Server 範例）](../core/unenlistparties-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-130">[UnenlistParties (BizTalk Server Sample)](../core/unenlistparties-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-131">示範如何取消登錄與已部署 BizTalk 組件關聯的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="63eee-131">Demonstrates how to unenlist all of the parties associated with a deployed BizTalk assembly.</span></span>  
  
    -   <span data-ttu-id="63eee-132">[BizTalk Server VHD （BizTalk Server 範例） Sysprep](../core/sysprep-a-biztalk-server-vhd-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-132">[Sysprep a BizTalk Server VHD (BizTalk Server Sample)](../core/sysprep-a-biztalk-server-vhd-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-133">示範如何 Sysprep 會建立與虛擬機器的快照集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]快速部署其他虛擬機器上安裝。</span><span class="sxs-lookup"><span data-stu-id="63eee-133">Demonstrates how Sysprep creates a snapshot of a virtual machine with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed for quick deployment on other virtual machines.</span></span>  
  
-   [<span data-ttu-id="63eee-134">系統管理員 OperationsOM （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="63eee-134">Admin-OperationsOM (BizTalk Server Samples Folder)</span></span>](../core/admin-operationsom-biztalk-server-samples-folder.md)  
  
    -   [<span data-ttu-id="63eee-135">OperationsSamples （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="63eee-135">OperationsSamples (BizTalk Server Sample)</span></span>](../core/operationssamples-biztalk-server-sample.md)  
  
-   [<span data-ttu-id="63eee-136">管理 WMI （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="63eee-136">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)  
  
    -   <span data-ttu-id="63eee-137">[啟用接收位置 （BizTalk Server 範例）](../core/enable-receive-location-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-137">[Enable Receive Location (BizTalk Server Sample)](../core/enable-receive-location-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-138">示範如何啟用接收位置及設定該接收位置的輸入傳輸 URL。</span><span class="sxs-lookup"><span data-stu-id="63eee-138">Demonstrates how to enable a receive location and set the Inbound Transport URL for that receive location.</span></span>  
  
    -   <span data-ttu-id="63eee-139">[登錄協調流程 （BizTalk Server 範例）](../core/enlist-orchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-139">[Enlist Orchestration (BizTalk Server Sample)](../core/enlist-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-140">示範如何將 BizTalk Server 協調流程登錄到主控件。</span><span class="sxs-lookup"><span data-stu-id="63eee-140">Demonstrates how to enlist a BizTalk Server orchestration to a host.</span></span>  
  
    -   <span data-ttu-id="63eee-141">[列舉接收位置 （BizTalk Server 範例）](../core/enumerate-receive-locations-biztalk-server-sample.md)範例。</span><span class="sxs-lookup"><span data-stu-id="63eee-141">[Enumerate Receive Locations (BizTalk Server Sample)](../core/enumerate-receive-locations-biztalk-server-sample.md) Sample.</span></span> <span data-ttu-id="63eee-142">示範如何擷取一或多個接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="63eee-142">Demonstrates how to retrieve details about one or more receive locations.</span></span>  
  
    -   <span data-ttu-id="63eee-143">[移除接收埠 （BizTalk Server 範例）](../core/remove-receive-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-143">[Remove Receive Port (BizTalk Server Sample)](../core/remove-receive-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-144">示範如何移除一或多個接收埠。</span><span class="sxs-lookup"><span data-stu-id="63eee-144">Demonstrates how to remove one or more receive ports.</span></span>  
  
    -   <span data-ttu-id="63eee-145">[移除傳送埠 （BizTalk Server 範例）](../core/remove-send-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-145">[Remove Send Port (BizTalk Server Sample)](../core/remove-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-146">示範如何取消登錄一或多個傳送埠，並且將其移除。</span><span class="sxs-lookup"><span data-stu-id="63eee-146">Demonstrates how to unenlist and remove one or more send ports.</span></span>  
  
    -   <span data-ttu-id="63eee-147">[設定 Send Handler 屬性 （BizTalk Server 範例）](../core/set-send-handler-property-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-147">[Set Send Handler Property (BizTalk Server Sample)](../core/set-send-handler-property-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-148">示範如何設定 Simple Mail Transfer Protocol (SMTP) 傳送處理常式的 XML 組態資訊。</span><span class="sxs-lookup"><span data-stu-id="63eee-148">Demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.</span></span>  
  
    -   <span data-ttu-id="63eee-149">[啟動傳送埠 （BizTalk Server 範例）](../core/start-send-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-149">[Start Send Port (BizTalk Server Sample)](../core/start-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-150">示範如何在使用 FILE 配接器時啟動傳送埠及設定主要傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="63eee-150">Demonstrates how to start a send port and set the Primary Transport Address when using the FILE adapter.</span></span>  
  
    -   <span data-ttu-id="63eee-151">[停止協調流程 （BizTalk Server 範例）](../core/stop-orchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63eee-151">[Stop Orchestration (BizTalk Server Sample)](../core/stop-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="63eee-152">示範如何停止 BizTalk Server 協調流程，以及選擇性地將它取消登錄。</span><span class="sxs-lookup"><span data-stu-id="63eee-152">Demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.</span></span>