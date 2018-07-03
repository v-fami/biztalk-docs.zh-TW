---
title: 步驟 7： 設定 BizTalk HTTP 前端伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, HTTP servers
- HTTP server, configuring
ms.assetid: 6b7e0b48-bb20-42f4-84a5-092ff3a02741
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b6429ba6c753bac16874fd6fa81e13e91927b58
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989183"
---
# <a name="step-7-configuring-the-biztalk-http-front-end-servers"></a><span data-ttu-id="ab180-102">步驟 7： 設定 BizTalk HTTP 前端伺服器</span><span class="sxs-lookup"><span data-stu-id="ab180-102">Step 7: Configuring the BizTalk HTTP Front-End Servers</span></span>
<span data-ttu-id="ab180-103">本節提供有關設定中的 Web 伺服器的指導方針您[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]部署。</span><span class="sxs-lookup"><span data-stu-id="ab180-103">This section provides guidelines on configuring the Web servers in your [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab180-104">在單一電腦部署中，此電腦是一個可進行傳訊和處理的同一部電腦。</span><span class="sxs-lookup"><span data-stu-id="ab180-104">In the single-computer deployment, this computer is the same computer as the one that does the messaging and processing.</span></span>  
  
### <a name="to-configure-the-biztalk-http-front-end-servers"></a><span data-ttu-id="ab180-105">若要設定 BizTalk HTTP 前端伺服器</span><span class="sxs-lookup"><span data-stu-id="ab180-105">To configure the BizTalk HTTP front-end servers</span></span>  
  
1. <span data-ttu-id="ab180-106">安裝 Internet Information Services (IIS) 和 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="ab180-106">Install Internet Information Services (IIS) and ASP.NET.</span></span>  
  
2. <span data-ttu-id="ab180-107">開啟 IIS 管理員並選取**網頁服務延伸**。</span><span class="sxs-lookup"><span data-stu-id="ab180-107">Open IIS Manager and select **Web Service Extensions**.</span></span> <span data-ttu-id="ab180-108">請確定 ASP.NET v1.1 和 ASP.NET v2.0 設定為**允許**。</span><span class="sxs-lookup"><span data-stu-id="ab180-108">Ensure that ASP.NET v1.1 and ASP.NET v2.0 are set to **Allowed**.</span></span>  
  
3. <span data-ttu-id="ab180-109">請確認**Message Queuing**服務 (MSMQ) 與**路由支援**從 新增/移除安裝[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]下應用程式伺服器/訊息佇列的元件。</span><span class="sxs-lookup"><span data-stu-id="ab180-109">Ensure that the **Message Queuing** service (MSMQ) with **Routing Support** is installed from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under Application Server/Message Queuing.</span></span>  
  
4. <span data-ttu-id="ab180-110">確定已啟用網路 DTC 存取在 [新增/移除[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。</span><span class="sxs-lookup"><span data-stu-id="ab180-110">Ensure that Network DTC access is enabled in the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="ab180-111">上已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]先前步驟中的電腦。</span><span class="sxs-lookup"><span data-stu-id="ab180-111">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span>  
  
5. <span data-ttu-id="ab180-112">在您部署中，實作安全通訊端層 (SSL) 通訊協定，如中所述[支援 Secure Sockets Layer (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)。</span><span class="sxs-lookup"><span data-stu-id="ab180-112">Implement the Secure Sockets Layer (SSL) protocol in your deployment, as described in [Supporting Secure Sockets Layer (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md).</span></span>  
  
6. <span data-ttu-id="ab180-113">安裝和設定 Windows SharePoint Services 3.0 SP1。</span><span class="sxs-lookup"><span data-stu-id="ab180-113">Install and configure Windows SharePoint Services 3.0 SP1.</span></span>  
  
7. <span data-ttu-id="ab180-114">安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="ab180-114">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in [Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md).</span></span>  
  
   <span data-ttu-id="ab180-115">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="ab180-115">This section contains:</span></span>  
  
-   [<span data-ttu-id="ab180-116">支援安全通訊端層 (SSL)</span><span class="sxs-lookup"><span data-stu-id="ab180-116">Supporting Secure Sockets Layer (SSL)</span></span>](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)  
  
-   [<span data-ttu-id="ab180-117">安裝和設定 BizTalk HTTP 前端伺服器</span><span class="sxs-lookup"><span data-stu-id="ab180-117">Installing and Configuring BizTalk HTTP Front-End Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)  
  
-   [<span data-ttu-id="ab180-118">在 HTTP 前端伺服器上安裝和設定 BizTalk Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="ab180-118">Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-http-front-end-servers.md)