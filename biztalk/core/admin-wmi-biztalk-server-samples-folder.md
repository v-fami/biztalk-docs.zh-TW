---
title: "管理 WMI （BizTalk Server 範例資料夾） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administering, WMI
- examples, Windows Management Instrumentation (WMI)
- Windows Management Instrumentation (WMI), administering
- Windows Management Instrumentation (WMI), examples
- examples, administering
- administering, examples
ms.assetid: 39e2a6fe-2781-4be2-a152-f5e9960a0faa
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19a8698bbe916d86909005ff77c9b1eeea11604f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="admin-wmi-biztalk-server-samples-folder"></a><span data-ttu-id="f3e91-102">管理 WMI （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="f3e91-102">Admin-WMI (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="f3e91-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的軟體開發套件 (SDK) 中包含數個 Microsoft Windows Management Instrumentation (WMI) 管理範例。</span><span class="sxs-lookup"><span data-stu-id="f3e91-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several Microsoft Windows Management Instrumentation (WMI) administration samples in its software development kit (SDK).</span></span> <span data-ttu-id="f3e91-104">本節提供每個 WMI 管理範例所示範功能的詳細資訊、用來建置和執行範例的指示，以及您可以預期的結果。</span><span class="sxs-lookup"><span data-stu-id="f3e91-104">This section provides detailed information about the functionality demonstrated by each WMI administration sample, instructions for building and running the sample, and the results you can expect.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f3e91-105">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="f3e91-105">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="f3e91-106">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="f3e91-106">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3e91-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f3e91-107">In This Section</span></span>  
  
-   <span data-ttu-id="f3e91-108">[啟用接收位置 （BizTalk Server 範例）](../core/enable-receive-location-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-108">[Enable Receive Location (BizTalk Server Sample)](../core/enable-receive-location-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-109">示範如何啟用接收位置及設定該接收位置的輸入傳輸 URL。</span><span class="sxs-lookup"><span data-stu-id="f3e91-109">Demonstrates how to enable a receive location and set the Inbound Transport URL for that receive location.</span></span>  
  
-   <span data-ttu-id="f3e91-110">[登錄協調流程 （BizTalk Server 範例）](../core/enlist-orchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-110">[Enlist Orchestration (BizTalk Server Sample)](../core/enlist-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-111">示範如何將 BizTalk Server 協調流程登錄到主控件。</span><span class="sxs-lookup"><span data-stu-id="f3e91-111">Demonstrates how to enlist a BizTalk Server orchestration to a host.</span></span>  
  
-   <span data-ttu-id="f3e91-112">[列舉接收位置 （BizTalk Server 範例）](../core/enumerate-receive-locations-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-112">[Enumerate Receive Locations (BizTalk Server Sample)](../core/enumerate-receive-locations-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-113">示範如何擷取一或多個接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f3e91-113">Demonstrates how to retrieve details about one or more receive locations.</span></span>  
  
-   <span data-ttu-id="f3e91-114">[移除接收埠 （BizTalk Server 範例）](../core/remove-receive-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-114">[Remove Receive Port (BizTalk Server Sample)](../core/remove-receive-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-115">示範如何移除一或多個接收埠。</span><span class="sxs-lookup"><span data-stu-id="f3e91-115">Demonstrates how to remove one or more receive ports.</span></span>  
  
-   <span data-ttu-id="f3e91-116">[移除傳送埠 （BizTalk Server 範例）](../core/remove-send-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-116">[Remove Send Port (BizTalk Server Sample)](../core/remove-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-117">示範如何取消登錄一或多個傳送埠，並且將其移除。</span><span class="sxs-lookup"><span data-stu-id="f3e91-117">Demonstrates how to unenlist and remove one or more send ports.</span></span>  
  
-   <span data-ttu-id="f3e91-118">[設定 Send Handler 屬性 （BizTalk Server 範例）](../core/set-send-handler-property-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-118">[Set Send Handler Property (BizTalk Server Sample)](../core/set-send-handler-property-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-119">示範如何設定 Simple Mail Transfer Protocol (SMTP) 傳送處理常式的 XML 組態資訊。</span><span class="sxs-lookup"><span data-stu-id="f3e91-119">Demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.</span></span>  
  
-   <span data-ttu-id="f3e91-120">[啟動傳送埠 （BizTalk Server 範例）](../core/start-send-port-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-120">[Start Send Port (BizTalk Server Sample)](../core/start-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-121">示範如何在使用 FILE 配接器時啟動傳送埠及設定主要傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="f3e91-121">Demonstrates how to start a send port and set the Primary Transport Address when using the FILE adapter.</span></span>  
  
-   <span data-ttu-id="f3e91-122">[停止協調流程 （BizTalk Server 範例）](../core/stop-orchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e91-122">[Stop Orchestration (BizTalk Server Sample)](../core/stop-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="f3e91-123">示範如何停止 BizTalk Server 協調流程，以及選擇性地將它取消登錄。</span><span class="sxs-lookup"><span data-stu-id="f3e91-123">Demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.</span></span>