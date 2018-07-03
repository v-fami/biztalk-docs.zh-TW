---
title: Admin （BizTalk Server 範例資料夾） |Microsoft Docs
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
ms.openlocfilehash: 5b2075ffdf3a9e7750717cef34c222e0f871eb2c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018748"
---
# <a name="admin-biztalk-server-samples-folder"></a><span data-ttu-id="eb5bf-102">Admin （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="eb5bf-102">Admin (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="eb5bf-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的軟體開發套件 (SDK) 中包含數個管理範例。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several administration samples in its software development kit (SDK).</span></span> <span data-ttu-id="eb5bf-104">本節提供每個管理範例所示範之功能的詳細資訊、用來建置和執行範例的指示，以及您可以預期的結果。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-104">This section provides detailed information about the functionality demonstrated by each administration sample, instructions for building and running the sample, and the results you can expect.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="eb5bf-105">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-105">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="eb5bf-106">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-106">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb5bf-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="eb5bf-107">In This Section</span></span>  
  
- <span data-ttu-id="eb5bf-108">[Admin-explorerom （BizTalk Server Samples 資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-108">[Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md).</span></span>  
  
  - <span data-ttu-id="eb5bf-109">[ApplicationManager （BizTalk Server 範例）](../core/applicationmanager-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-109">[ApplicationManager (BizTalk Server Sample)](../core/applicationmanager-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-110">示範如何啟動或停止 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-110">Demonstrates how to start or stop a BizTalk application.</span></span>  
  
  - <span data-ttu-id="eb5bf-111">[BrowsingArtifacts （BizTalk Server 範例）](../core/browsingartifacts-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-111">[BrowsingArtifacts (BizTalk Server Sample)](../core/browsingartifacts-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-112">示範如何列舉 BizTalk 成品和屬性。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-112">Demonstrates how to enumerate BizTalk artifacts and attributes.</span></span>  
  
  - <span data-ttu-id="eb5bf-113">[CBR （BizTalk Server 範例）](../core/cbr-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-113">[CBR (BizTalk Server Sample)](../core/cbr-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-114">示範如何新增和設定新傳送埠的 BizTalk 訊息內容型路由。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-114">Demonstrates adding and configuring new send ports for content based routing of BizTalk messages.</span></span>  
  
  - <span data-ttu-id="eb5bf-115">[DeleteParty （BizTalk Server 範例）](../core/deleteparty-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-115">[DeleteParty (BizTalk Server Sample)](../core/deleteparty-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-116">示範如何刪除指定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-116">Demonstrates how to delete a specified party.</span></span>  
  
  - <span data-ttu-id="eb5bf-117">[OrchestrationBinding （BizTalk Server 範例）](../core/orchestrationbinding-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-117">[OrchestrationBinding (BizTalk Server Sample)](../core/orchestrationbinding-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-118">示範如何管理和設定協調流程。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-118">Demonstrates how to manage and configure orchestrations.</span></span>  
  
  - <span data-ttu-id="eb5bf-119">[PartnerManagement （BizTalk Server 範例）](../core/partnermanagement-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-119">[PartnerManagement (BizTalk Server Sample)](../core/partnermanagement-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-120">示範如何建立和刪除合作對象。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-120">Demonstrates creating and deleting parties.</span></span> <span data-ttu-id="eb5bf-121">也會示範與角色登錄及取消登錄合作對象。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-121">Also demonstrates enlisting and unenlisting parties with roles.</span></span>  
  
  - <span data-ttu-id="eb5bf-122">[ReceiveLocations （BizTalk Server 範例）](../core/receivelocations-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-122">[ReceiveLocations (BizTalk Server Sample)](../core/receivelocations-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-123">示範如何建立和管理接收埠的接收位置。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-123">Demonstrates how to create and manage receive locations for receive ports.</span></span>  
  
  - <span data-ttu-id="eb5bf-124">[ReceivePorts （BizTalk Server 範例）](../core/receiveports-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-124">[ReceivePorts (BizTalk Server Sample)](../core/receiveports-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-125">示範如何建立、 列舉和刪除接收埠。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-125">Demonstrates creating, enumerating and deleting receive ports.</span></span>  
  
  - <span data-ttu-id="eb5bf-126">[SendPortGroups （BizTalk Server 範例）](../core/sendportgroups-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-126">[SendPortGroups (BizTalk Server Sample)](../core/sendportgroups-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-127">示範如何列舉和管理傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-127">Demonstrates how to enumerate and manage send port groups.</span></span>  
  
  - <span data-ttu-id="eb5bf-128">[SendPorts （BizTalk Server 範例）](../core/sendports-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-128">[SendPorts (BizTalk Server Sample)](../core/sendports-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-129">示範如何列舉和管理傳送埠。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-129">Demonstrates how to enumerate and manage send ports.</span></span>  
  
  - <span data-ttu-id="eb5bf-130">[UnenlistParties （BizTalk Server 範例）](../core/unenlistparties-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-130">[UnenlistParties (BizTalk Server Sample)](../core/unenlistparties-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-131">示範如何取消登錄與已部署 BizTalk 組件關聯的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-131">Demonstrates how to unenlist all of the parties associated with a deployed BizTalk assembly.</span></span>  
  
  - <span data-ttu-id="eb5bf-132">[Sysprep 對 BizTalk Server VHD （BizTalk Server 範例）](../core/sysprep-a-biztalk-server-vhd-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-132">[Sysprep a BizTalk Server VHD (BizTalk Server Sample)](../core/sysprep-a-biztalk-server-vhd-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-133">Sysprep 會有的虛擬機器的快照集的建立會示範[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]快速部署其他虛擬機器上安裝。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-133">Demonstrates how Sysprep creates a snapshot of a virtual machine with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed for quick deployment on other virtual machines.</span></span>  
  
- [<span data-ttu-id="eb5bf-134">Admin-OperationsOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="eb5bf-134">Admin-OperationsOM (BizTalk Server Samples Folder)</span></span>](../core/admin-operationsom-biztalk-server-samples-folder.md)  
  
  -   [<span data-ttu-id="eb5bf-135">OperationsSamples (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="eb5bf-135">OperationsSamples (BizTalk Server Sample)</span></span>](../core/operationssamples-biztalk-server-sample.md)  
  
- [<span data-ttu-id="eb5bf-136">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="eb5bf-136">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)  
  
  -   <span data-ttu-id="eb5bf-137">[啟用接收位置 （BizTalk Server 範例）](../core/enable-receive-location-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-137">[Enable Receive Location (BizTalk Server Sample)](../core/enable-receive-location-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-138">示範如何啟用接收位置及設定該接收位置的輸入傳輸 URL。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-138">Demonstrates how to enable a receive location and set the Inbound Transport URL for that receive location.</span></span>  
  
  -   <span data-ttu-id="eb5bf-139">[登錄協調流程 （BizTalk Server 範例）](../core/enlist-orchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-139">[Enlist Orchestration (BizTalk Server Sample)](../core/enlist-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-140">示範如何將 BizTalk Server 協調流程登錄到主控件。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-140">Demonstrates how to enlist a BizTalk Server orchestration to a host.</span></span>  
  
  -   <span data-ttu-id="eb5bf-141">[列舉接收位置 （BizTalk Server 範例）](../core/enumerate-receive-locations-biztalk-server-sample.md)範例。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-141">[Enumerate Receive Locations (BizTalk Server Sample)](../core/enumerate-receive-locations-biztalk-server-sample.md) Sample.</span></span> <span data-ttu-id="eb5bf-142">示範如何擷取一或多個接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-142">Demonstrates how to retrieve details about one or more receive locations.</span></span>  
  
  -   <span data-ttu-id="eb5bf-143">[移除接收埠 （BizTalk Server 範例）](../core/remove-receive-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-143">[Remove Receive Port (BizTalk Server Sample)](../core/remove-receive-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-144">示範如何移除一或多個接收埠。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-144">Demonstrates how to remove one or more receive ports.</span></span>  
  
  -   <span data-ttu-id="eb5bf-145">[移除傳送埠 （BizTalk Server 範例）](../core/remove-send-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-145">[Remove Send Port (BizTalk Server Sample)](../core/remove-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-146">示範如何取消登錄一或多個傳送埠，並且將其移除。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-146">Demonstrates how to unenlist and remove one or more send ports.</span></span>  
  
  -   <span data-ttu-id="eb5bf-147">[設定 Send Handler 屬性 （BizTalk Server 範例）](../core/set-send-handler-property-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-147">[Set Send Handler Property (BizTalk Server Sample)](../core/set-send-handler-property-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-148">示範如何設定 Simple Mail Transfer Protocol (SMTP) 傳送處理常式的 XML 組態資訊。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-148">Demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.</span></span>  
  
  -   <span data-ttu-id="eb5bf-149">[啟動傳送埠 （BizTalk Server 範例）](../core/start-send-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-149">[Start Send Port (BizTalk Server Sample)](../core/start-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-150">示範如何在使用 FILE 配接器時啟動傳送埠及設定主要傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-150">Demonstrates how to start a send port and set the Primary Transport Address when using the FILE adapter.</span></span>  
  
  -   <span data-ttu-id="eb5bf-151">[停止協調流程 （BizTalk Server 範例）](../core/stop-orchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-151">[Stop Orchestration (BizTalk Server Sample)](../core/stop-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="eb5bf-152">示範如何停止 BizTalk Server 協調流程，以及選擇性地將它取消登錄。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-152">Demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.</span></span>