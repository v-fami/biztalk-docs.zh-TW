---
title: MQSeries 配接器的元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, BizTalk component
- MQSeries adapters, components
- MQSeries components, MQSeries adapters
- BizTalk components
- MQSeries adapters, MQSeries component
ms.assetid: 923974cb-371d-47dc-99a7-2f7b93f60ada
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afeac0dda1d42c244eeeac124632ed68aa2e90d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990327"
---
# <a name="components-of-the-mqseries-adapter"></a><span data-ttu-id="59389-102">MQSeries 配接器的元件</span><span class="sxs-lookup"><span data-stu-id="59389-102">Components of the MQSeries Adapter</span></span>
<span data-ttu-id="59389-103">MQSeries 配接器會使用兩個元件，協助 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 MQSeries Server for Windows 之間的文件轉換。</span><span class="sxs-lookup"><span data-stu-id="59389-103">The MQSeries adapter uses two components to facilitate document transfer between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and MQSeries Server for Windows.</span></span>  
  
- <span data-ttu-id="59389-104">**BizTalk 元件。**</span><span class="sxs-lookup"><span data-stu-id="59389-104">**BizTalk component.**</span></span> <span data-ttu-id="59389-105">Microsoft 的同一部電腦上安裝此元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="59389-105">Install this component on the same computer as Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="59389-106">此元件會與 BizTalk Server 通訊。</span><span class="sxs-lookup"><span data-stu-id="59389-106">This component communicates with BizTalk Server.</span></span>  
  
- <span data-ttu-id="59389-107">**MQSeries 元件。**</span><span class="sxs-lookup"><span data-stu-id="59389-107">**MQSeries component.**</span></span> <span data-ttu-id="59389-108">在 MQSeries Server for Windows 上安裝此元件。</span><span class="sxs-lookup"><span data-stu-id="59389-108">Install this component on the MQSeries Server for Windows.</span></span> <span data-ttu-id="59389-109">在上執行的 MQSeries Server for Windows[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="59389-109">MQSeries Server for Windows runs on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span></span> <span data-ttu-id="59389-110">此元件 (稱為 MQSAgent) 會與 IBM MQSeries Server 通訊。</span><span class="sxs-lookup"><span data-stu-id="59389-110">This component (referred to as MQSAgent) communicates with IBM MQSeries Server.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="59389-111">MQSeries 配接器的 MQSAgent 元件支援在 Windows 上，根據 MQSeries Server 5.3、CSD10 或更新版，以及 WebSphere MQSeries Server 6.0 來執行。</span><span class="sxs-lookup"><span data-stu-id="59389-111">The MQSAgent component of the MQSeries Adapter is supported running against MQSeries Server 5.3, CSD10 or above, and WebSphere MQSeries Server 6.0 on Windows.</span></span>  
  
  <span data-ttu-id="59389-112">下圖概述配接器的一般用法。</span><span class="sxs-lookup"><span data-stu-id="59389-112">The following figure outlines a typical use of the adapter.</span></span>  
  
  <span data-ttu-id="59389-113">![文件的 MQSeries Server 與 BizTalk 之間的流量](../core/media/bts-dev-mqadapterflow.gif "BTS_Dev_MQAdapterFlow")</span><span class="sxs-lookup"><span data-stu-id="59389-113">![Document flow between MQSeries Server and BizTalk](../core/media/bts-dev-mqadapterflow.gif "BTS_Dev_MQAdapterFlow")</span></span>  
  
  <span data-ttu-id="59389-114">MQSeries 配接器是一種連線解決方案，可讓您在企業中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及 MQSeries 作為選擇的傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="59389-114">The MQSeries adapter is a connectivity solution that lets you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in an enterprise with MQSeries as the chosen messaging standard.</span></span> <span data-ttu-id="59389-115">開發此解決方案的動機有部分是來自下列問題：</span><span class="sxs-lookup"><span data-stu-id="59389-115">Developing this solution was motivated, in part, by the following issues:</span></span>  
  
- <span data-ttu-id="59389-116">配合客戶對於簡單安裝和組態及 MQSeries 連線解決方案的要求。</span><span class="sxs-lookup"><span data-stu-id="59389-116">Accommodating customer requests for simple installation and configuration, and an MQSeries connectivity solution</span></span>  
  
- <span data-ttu-id="59389-117">支援最大可達 100 MB 大小的訊息</span><span class="sxs-lookup"><span data-stu-id="59389-117">Supporting message sizes up to 100 MB</span></span>  
  
- <span data-ttu-id="59389-118">提供 MQSeries 支援</span><span class="sxs-lookup"><span data-stu-id="59389-118">Providing MQSeries support</span></span>  
  
- <span data-ttu-id="59389-119">為傳送到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 MQSeries 訊息提供隨插即用的連線解決方案</span><span class="sxs-lookup"><span data-stu-id="59389-119">Providing a Plug and Play connectivity solution for MQSeries messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
  <span data-ttu-id="59389-120">MQSeries 配接器是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組合軟體之接收服務的主要新增功能，它為各種通訊協定標準提供一組待命程式。</span><span class="sxs-lookup"><span data-stu-id="59389-120">The MQSeries adapter is a key addition to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suite of receive services that provide a set of listeners for various communication protocol standards.</span></span> <span data-ttu-id="59389-121">待命程式會將通訊協定 (例如 HTTP、FTP 或 MQSeries) 連接到企業應用程式整合 (EAI)、B2B，或是應用程式對應用程式整合的交易關係。</span><span class="sxs-lookup"><span data-stu-id="59389-121">The listeners attach a protocol, for example HTTP, FTP, or MQSeries, to an enterprise application integration (EAI), business-to-business, or application-to-application integration trading relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59389-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59389-122">See Also</span></span>  
 <span data-ttu-id="59389-123">[MQSeries 配接器架構](../core/mqseries-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="59389-123">[MQSeries Adapter Architecture](../core/mqseries-adapter-architecture.md) </span></span>  
 [<span data-ttu-id="59389-124">何謂 MQSeries 配接器？</span><span class="sxs-lookup"><span data-stu-id="59389-124">What Is the MQSeries Adapter?</span></span>](../core/what-is-the-mqseries-adapter.md)