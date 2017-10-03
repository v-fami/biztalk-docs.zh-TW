---
title: "FTP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FTP adapters
ms.assetid: 878dc0b0-d1d8-405a-a697-654dd18ba08e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffc72b5166f8971392b41f275338bde593d325af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ftp-adapter"></a><span data-ttu-id="e2459-102">FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="e2459-102">FTP Adapter</span></span>
<span data-ttu-id="e2459-103">FTP 配接器可在 FTP 伺服器與 Microsoft BizTalk Server 之間交換資料，並能整合各種平台上商業實務應用程式中儲存的重要資料。</span><span class="sxs-lookup"><span data-stu-id="e2459-103">The FTP adapter exchanges data between an FTP server and Microsoft BizTalk Server, and allows for the integration of vital data stored on a variety of platforms with line-of-business applications.</span></span> <span data-ttu-id="e2459-104">配接器可以連接到 FTP 伺服器透過 SOCKS4 或 SOCKS5 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e2459-104">The adapter can connect to the FTP server via SOCKS4 or SOCKS5 proxy server.</span></span>  
  
 <span data-ttu-id="e2459-105">FTP 配接器可以將大量檔案從 FTP 伺服器傳輸到 BizTalk Server；</span><span class="sxs-lookup"><span data-stu-id="e2459-105">The FTP adapter can transfer a large number of files from an FTP server to BizTalk Server.</span></span> <span data-ttu-id="e2459-106">也可以將檔案當作協調流程的一部分來傳輸。</span><span class="sxs-lookup"><span data-stu-id="e2459-106">It can also transfer files as part of an orchestration.</span></span>  
  
 <span data-ttu-id="e2459-107">FTP 配接器是由兩個配接器所組成 — 接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="e2459-107">The FTP adapter consists of two adapters — a receive adapter and a send adapter.</span></span>  

<span data-ttu-id="e2459-108">本節將描述 FTP 接收與傳送配接器，以及安全性和最佳作法資訊。</span><span class="sxs-lookup"><span data-stu-id="e2459-108">This section describes the FTP receive and send adapters, as well as security and best-practice information.</span></span>  
  
 ## <a name="receive-adapter"></a><span data-ttu-id="e2459-109">接收配接器</span><span class="sxs-lookup"><span data-stu-id="e2459-109">Receive adapter</span></span>  
  
 <span data-ttu-id="e2459-110">FTP 接收配接器可讓您將資料從 FTP 伺服器，以移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e2459-110">The FTP receive adapter enables you to move data from an FTP server to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e2459-111">主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="e2459-111">Key features include:</span></span>  
  
-   <span data-ttu-id="e2459-112">視需要從 FTP 伺服器提取檔案</span><span class="sxs-lookup"><span data-stu-id="e2459-112">Pulling files from the FTP server on demand</span></span>  
  
-   <span data-ttu-id="e2459-113">根據可以設定的排程執行輪詢</span><span class="sxs-lookup"><span data-stu-id="e2459-113">Running polls based on a configurable schedule</span></span>  
  
-   <span data-ttu-id="e2459-114">輪詢 FTP 伺服器，及直接傳送資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2459-114">Polling the FTP server and sending data directly to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="e2459-115">指定 FTP 伺服器為 IP 位址、連接埠、密碼和主控件名稱</span><span class="sxs-lookup"><span data-stu-id="e2459-115">Specifying the FTP server as an IP address, port, password, and host name</span></span>  
  
-   <span data-ttu-id="e2459-116">保證檔案傳遞</span><span class="sxs-lookup"><span data-stu-id="e2459-116">Guaranteed file delivery</span></span>  
  
     <span data-ttu-id="e2459-117">FTP 接收配接器也可搭配[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 」 和 「 BizTalk 總管 中設定及管理每個接收函式，是由下列組態項目所組成：</span><span class="sxs-lookup"><span data-stu-id="e2459-117">The FTP receive adapter also works with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and BizTalk Explorer to configure and administer each receive function, which is composed of the following configuration items:</span></span>  
  
-   <span data-ttu-id="e2459-118">執行 FTP 命令的輪詢間隔 (例如，60 分鐘)</span><span class="sxs-lookup"><span data-stu-id="e2459-118">Poll interval to run an FTP command (for example, 60 minutes)</span></span>  
  
-   <span data-ttu-id="e2459-119">路由傳送文件以指定 BizTalk 傳送埠或接受位置的資料</span><span class="sxs-lookup"><span data-stu-id="e2459-119">Information with which to route the document to a specific BizTalk send port or receive location</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2459-120">FTP 接收配接器不支援接收來自分割資料集的檔案。</span><span class="sxs-lookup"><span data-stu-id="e2459-120">The FTP receive adapter does not support receiving files from a partitioned data set.</span></span>  
  
## <a name="send-adapter"></a><span data-ttu-id="e2459-121">傳送配接器</span><span class="sxs-lookup"><span data-stu-id="e2459-121">Send adapter</span></span>  
  
 <span data-ttu-id="e2459-122">FTP 傳送配接器可讓您將資料從移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 FTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e2459-122">The FTP send adapter enables you to move data from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to an FTP server.</span></span> <span data-ttu-id="e2459-123">主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="e2459-123">Key features include:</span></span>  
  
-   <span data-ttu-id="e2459-124">視需要執行傳送的功能</span><span class="sxs-lookup"><span data-stu-id="e2459-124">Ability to run sends on demand</span></span>  
  
-   <span data-ttu-id="e2459-125">保證傳遞</span><span class="sxs-lookup"><span data-stu-id="e2459-125">Guaranteed delivery</span></span>  
  
## <a name="supported-platforms"></a><span data-ttu-id="e2459-126">支援的平台</span><span class="sxs-lookup"><span data-stu-id="e2459-126">Supported platforms</span></span>  
<span data-ttu-id="e2459-127">存取儲存在 FTP 伺服器上任何下列平台的資訊：</span><span class="sxs-lookup"><span data-stu-id="e2459-127">Access information stored in an FTP server on any of the following platforms:</span></span>  

- [!INCLUDE[btsWinSvrNoVersion_md](../includes/btswinsvrnoversion-md.md)]<span data-ttu-id="e2459-128"> 2016</span><span class="sxs-lookup"><span data-stu-id="e2459-128"> 2016</span></span>

- [!INCLUDE[btsWinSrv2k12_md](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="e2459-129"> R2</span><span class="sxs-lookup"><span data-stu-id="e2459-129"> R2</span></span>
  
-   [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]  
  
-   [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]<span data-ttu-id="e2459-130"> 2008</span><span class="sxs-lookup"><span data-stu-id="e2459-130"> 2008</span></span>  
  
-   [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]<span data-ttu-id="e2459-131">2000 Service Pack 3 (SP3) 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e2459-131"> 2000 Service Pack 3 (SP3) and later</span></span>  
  
-   <span data-ttu-id="e2459-132">Sun Solaris 9.0</span><span class="sxs-lookup"><span data-stu-id="e2459-132">Sun Solaris 9.0</span></span>  
  
-   <span data-ttu-id="e2459-133">HP-UX</span><span class="sxs-lookup"><span data-stu-id="e2459-133">HP-UX</span></span>  
  
-   <span data-ttu-id="e2459-134">LINUX (Redhat 7.x)</span><span class="sxs-lookup"><span data-stu-id="e2459-134">LINUX (Redhat 7.x)</span></span>  
  
-   <span data-ttu-id="e2459-135">IBM z/OS v1.9 (MVS)</span><span class="sxs-lookup"><span data-stu-id="e2459-135">IBM z/OS v1.9 (MVS)</span></span>  
  
-   <span data-ttu-id="e2459-136">執行 MVS 的 IBM o/S 390</span><span class="sxs-lookup"><span data-stu-id="e2459-136">IBM O/S 390 running MVS</span></span>  
  
-   <span data-ttu-id="e2459-137">AS / 400 OS/400 V5R1</span><span class="sxs-lookup"><span data-stu-id="e2459-137">AS/400 OS/400 V5R1</span></span>  
  
-   <span data-ttu-id="e2459-138">i5/OS V5R4 (AS400)</span><span class="sxs-lookup"><span data-stu-id="e2459-138">i5/OS V5R4 (AS400)</span></span>  
  
-   <span data-ttu-id="e2459-139">i5/OS V6R1 (AS400)</span><span class="sxs-lookup"><span data-stu-id="e2459-139">i5/OS V6R1 (AS400)</span></span>  
  
-   <span data-ttu-id="e2459-140">GXS ICS</span><span class="sxs-lookup"><span data-stu-id="e2459-140">GXS ICS</span></span>  
  
-   <span data-ttu-id="e2459-141">AIX</span><span class="sxs-lookup"><span data-stu-id="e2459-141">AIX</span></span>  
  
 <span data-ttu-id="e2459-142">支援所有的服務組件，除非已特別列出 service pack。</span><span class="sxs-lookup"><span data-stu-id="e2459-142">All services packs are supported, unless the service pack is specifically listed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2459-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="e2459-143">In This Section</span></span>  
  
[<span data-ttu-id="e2459-144">最佳做法和建議，FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="e2459-144">Best practices and recommendations for the FTP Adapter</span></span>](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[<span data-ttu-id="e2459-145">設定 FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="e2459-145">Configuring the FTP adapter</span></span>](../core/configuring-the-ftp-adapter.md)  

[<span data-ttu-id="e2459-146">FTP 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="e2459-146">FTP Adapter Property Schema and Properties</span></span>](../core/ftp-adapter-property-schema-and-properties.md)