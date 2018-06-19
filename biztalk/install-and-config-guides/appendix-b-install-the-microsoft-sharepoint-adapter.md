---
title: 附錄 b： 安裝 SharePoint 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f44c6e0a-dcce-4444-8cac-bd403c81a233
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0766eabdad71546090b703e41a00f496629d83
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710833"
---
# <a name="appendix-b-install-the-microsoft-sharepoint-adapter"></a><span data-ttu-id="fea95-102">附錄 B：安裝 Microsoft SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="fea95-102">Appendix B: Install the Microsoft SharePoint Adapter</span></span>
<span data-ttu-id="fea95-103">BizTalk Server 會包含 SharePoint 配接器可以接收訊息，或將訊息傳送至 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="fea95-103">BizTalk Server includes a SharePoint adapter that can receive messages or send messages to SharePoint.</span></span> 

<span data-ttu-id="fea95-104">[BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) 和 [BizTalk Server 2013 R2/2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) 的軟體需求會列出支援的 SharePoint 版本。</span><span class="sxs-lookup"><span data-stu-id="fea95-104">The software requirements for [BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) and [BizTalk Server 2013 R2 / 2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) list the supported SharePoint versions.</span></span>

## <a name="sharepoint-adapter-in-biztalk-server-2016"></a><span data-ttu-id="fea95-105">BizTalk Server 2016 中的 SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="fea95-105">SharePoint adapter in BizTalk Server 2016</span></span>

<span data-ttu-id="fea95-106">BizTalk Server 安裝程式會自動安裝 CSOM 可轉散發套件，就像 File 配接器、FTP 配接器以及其他非預設配接器一樣。</span><span class="sxs-lookup"><span data-stu-id="fea95-106">The BizTalk Server setup automatically installs the CSOM redistributable package, just like the File adapter, FTP adapter, and other out-of-the-box adapters.</span></span> 

<span data-ttu-id="fea95-107">SSOM 選項會予以移除，而且無法使用。</span><span class="sxs-lookup"><span data-stu-id="fea95-107">The SSOM option is removed, and is not available.</span></span>


## <a name="sharepoint-adapter-in-biztalk-server-2013-and-r2"></a><span data-ttu-id="fea95-108">BizTalk Server 2013 和 R2 中的 SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="fea95-108">SharePoint adapter in BizTalk Server 2013 and R2</span></span>
<span data-ttu-id="fea95-109">在 BizTalk Server 2013 R2 和 BizTalk Server 2013 中，有兩個 SharePoint 配接器的選項。</span><span class="sxs-lookup"><span data-stu-id="fea95-109">In BizTalk Server 2013 R2 and BizTalk Server 2013, there are two options for the SharePoint adapter.</span></span>

|<span data-ttu-id="fea95-110">SharePoint 物件模型</span><span class="sxs-lookup"><span data-stu-id="fea95-110">SharePoint object model</span></span>|<span data-ttu-id="fea95-111">Description</span><span class="sxs-lookup"><span data-stu-id="fea95-111">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="fea95-112">CSOM-SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="fea95-112">CSOM - SharePoint Adapter</span></span>|<span data-ttu-id="fea95-113">**建議**。</span><span class="sxs-lookup"><span data-stu-id="fea95-113">**Recommended**.</span></span> <span data-ttu-id="fea95-114">BizTalk Server 安裝程式會自動安裝 CSOM 可轉散發套件，就像 File 配接器、FTP 配接器以及其他非預設配接器一樣。</span><span class="sxs-lookup"><span data-stu-id="fea95-114">The BizTalk Server setup automatically installs the CSOM redistributable package, just like the File adapter, FTP adapter, and other out-of-the-box adapters.</span></span> <br/><br/><span data-ttu-id="fea95-115">沒有 SharePoint 電腦的安裝需求。</span><span class="sxs-lookup"><span data-stu-id="fea95-115">There are no installation requirements on the SharePoint computer.</span></span>|  
|<span data-ttu-id="fea95-116">SSOM - SharePoint Web Service</span><span class="sxs-lookup"><span data-stu-id="fea95-116">SSOM - SharePoint Web Service</span></span>|<span data-ttu-id="fea95-117">**已取代**。</span><span class="sxs-lookup"><span data-stu-id="fea95-117">**Deprecated**.</span></span> <span data-ttu-id="fea95-118">SharePoint 電腦上，執行 BizTalk Server 安裝程式和**只**選取 SharePoint 配接器。</span><span class="sxs-lookup"><span data-stu-id="fea95-118">On the SharePoint computer, run the BizTalk Server setup, and **only** select the SharePoint Adapter.</span></span> <span data-ttu-id="fea95-119">這個安裝程式會安裝 IIS Web 服務，以處理與 BizTalk Server 上 SharePoint 配接器的通訊。</span><span class="sxs-lookup"><span data-stu-id="fea95-119">This setup installs an IIS web service that handles the communication to the SharePoint adapter on BizTalk Server.</span></span> <br/><br/><span data-ttu-id="fea95-120">在大部分的環境中，BizTalk Server 和 SharePoint 是在不同電腦上。</span><span class="sxs-lookup"><span data-stu-id="fea95-120">In most environments, BizTalk Server and SharePoint are on separate computers.</span></span>|  

##  <a name="BKMK_Before"></a> <span data-ttu-id="fea95-121">安裝之前</span><span class="sxs-lookup"><span data-stu-id="fea95-121">Before You Install</span></span>  

*  <span data-ttu-id="fea95-122">SharePoint SSOM 和 CSOM 元件可以安裝 BizTalk Server 2013 R2 或 2013年和 SharePoint 安裝在同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="fea95-122">The SharePoint SSOM and CSOM components can both be installed if BizTalk Server 2013 R2 or 2013 and SharePoint are installed on the same computer.</span></span>  
  
* <span data-ttu-id="fea95-123">BAM 入口網站只能在 32 位元模式中執行。</span><span class="sxs-lookup"><span data-stu-id="fea95-123">The BAM Portal only runs in 32-bit mode.</span></span> <span data-ttu-id="fea95-124">如果 BAM 入口網站安裝在 64 位元電腦上，請確定已啟用 ASP.NET 2.0 32 位元，而且 IIS 應用程式集區處於 32 位元模式。</span><span class="sxs-lookup"><span data-stu-id="fea95-124">If the BAM Portal is installed on a 64-bit machine, ensure that ASP.NET 2.0 32-bit is enabled and the IIS application pool is in 32-bit mode.</span></span> <span data-ttu-id="fea95-125">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="fea95-125">To do this:</span></span>  
  
    -   <span data-ttu-id="fea95-126">**ASP.NET**︰開啟 IIS 管理員中，並按一下 [BAM 入口網站] 網站，然後按兩下 [處理常式對應]。</span><span class="sxs-lookup"><span data-stu-id="fea95-126">**ASP.NET**: Open IIS Manager, click the **BAM Portal** web site, and then double-click **Handler Mappings**.</span></span> <span data-ttu-id="fea95-127">在 [已啟用] 清單中，確認列出 [PageHandlerFactory-ISAPI-2.0]。</span><span class="sxs-lookup"><span data-stu-id="fea95-127">In the **Enabled** list, confirm **PageHandlerFactory-ISAPI-2.0** is listed.</span></span>  
  
    -   <span data-ttu-id="fea95-128">**應用程式集區**：開啟 IIS 管理員，並依序按一下 [應用程式集區]、[BAMAppPool] 和 [進階設定]。</span><span class="sxs-lookup"><span data-stu-id="fea95-128">**Application Pool**: Open IIS Manager, click **Application Pools**, click the **BAMAppPool**, and then click **Advanced Settings**.</span></span> <span data-ttu-id="fea95-129">在 **啟用 32 位元應用程式**, ，請選取 **True**。</span><span class="sxs-lookup"><span data-stu-id="fea95-129">In **Enable 32-bit applications**, select **True**.</span></span>  
  
* <span data-ttu-id="fea95-130">安裝 SharePoint 時，按一下**伺服器陣列**選項，即使當您建立單一伺服器的 BizTalk Server 和 SharePoint 安裝。</span><span class="sxs-lookup"><span data-stu-id="fea95-130">When installing SharePoint, click the **Server Farm** option, even when you are creating a single-server BizTalk Server and SharePoint installation.</span></span> <span data-ttu-id="fea95-131">A**伺服器陣列**安裝可讓您設定 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fea95-131">A **Server Farm** installation allows you to configure the SharePoint databases.</span></span>  
* <span data-ttu-id="fea95-132">[CSOM: SharePoint Services 配接器](../core/csom-sharepoint-services-adapter.md)提供設定 SharePoint 接收位置和傳送埠的資訊。</span><span class="sxs-lookup"><span data-stu-id="fea95-132">[CSOM: SharePoint Services Adapter](../core/csom-sharepoint-services-adapter.md) provides information on configuring a SharePoint receive location and send port.</span></span>  
* <span data-ttu-id="fea95-133">BizTalk Server 2010 和舊版使用伺服器端物件模型 (SSOM) 連線到 SharePoint 2010。</span><span class="sxs-lookup"><span data-stu-id="fea95-133">BizTalk Server 2010 and previous versions use the Server Side Object Model (SSOM) to connect to SharePoint 2010.</span></span> 

## <a name="csom-and-ssom-supported-versions"></a><span data-ttu-id="fea95-134">CSOM 和 SSOM 支援的版本</span><span class="sxs-lookup"><span data-stu-id="fea95-134">CSOM and SSOM supported versions</span></span>  
<span data-ttu-id="fea95-135">SharePoint 支援下表中列出：</span><span class="sxs-lookup"><span data-stu-id="fea95-135">SharePoint support is listed in the following table:</span></span>  
  
||<span data-ttu-id="fea95-136">支援 CSOM</span><span class="sxs-lookup"><span data-stu-id="fea95-136">Supports CSOM</span></span>|<span data-ttu-id="fea95-137">支援 SSOM</span><span class="sxs-lookup"><span data-stu-id="fea95-137">Supports SSOM</span></span>|  
|---|---|---|  
|<span data-ttu-id="fea95-138">SharePoint 2016</span><span class="sxs-lookup"><span data-stu-id="fea95-138">SharePoint 2016</span></span>|<span data-ttu-id="fea95-139">是</span><span class="sxs-lookup"><span data-stu-id="fea95-139">Yes</span></span>|<span data-ttu-id="fea95-140">否</span><span class="sxs-lookup"><span data-stu-id="fea95-140">No</span></span>|  
|<span data-ttu-id="fea95-141">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fea95-141">SharePoint 2013</span></span>|<span data-ttu-id="fea95-142">是</span><span class="sxs-lookup"><span data-stu-id="fea95-142">Yes</span></span>|<span data-ttu-id="fea95-143">否</span><span class="sxs-lookup"><span data-stu-id="fea95-143">No</span></span>|  
|<span data-ttu-id="fea95-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fea95-144">SharePoint Online</span></span>|<span data-ttu-id="fea95-145">是</span><span class="sxs-lookup"><span data-stu-id="fea95-145">Yes</span></span>|<span data-ttu-id="fea95-146">否</span><span class="sxs-lookup"><span data-stu-id="fea95-146">No</span></span>|  
|<span data-ttu-id="fea95-147">SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="fea95-147">SharePoint 2010</span></span>|<span data-ttu-id="fea95-148">是</span><span class="sxs-lookup"><span data-stu-id="fea95-148">Yes</span></span>|<span data-ttu-id="fea95-149">是</span><span class="sxs-lookup"><span data-stu-id="fea95-149">Yes</span></span>|  
|<span data-ttu-id="fea95-150">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="fea95-150">SharePoint 2007</span></span> |<span data-ttu-id="fea95-151">否</span><span class="sxs-lookup"><span data-stu-id="fea95-151">No</span></span>|<span data-ttu-id="fea95-152">是</span><span class="sxs-lookup"><span data-stu-id="fea95-152">Yes</span></span>|  
  
##  <a name="BKMK_CSOM"></a> <span data-ttu-id="fea95-153">安裝 CSOM SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="fea95-153">Install the CSOM SharePoint adapter</span></span>  
  
1.  <span data-ttu-id="fea95-154">根據下列需求來使用 SharePoint 電腦︰</span><span class="sxs-lookup"><span data-stu-id="fea95-154">Use a SharePoint computer based on the following requirements:</span></span>  
  
    ||<span data-ttu-id="fea95-155">CSOM 支援</span><span class="sxs-lookup"><span data-stu-id="fea95-155">CSOM Support</span></span>|  
    |---|---|  
    |<span data-ttu-id="fea95-156">SharePoint 2016</span><span class="sxs-lookup"><span data-stu-id="fea95-156">SharePoint 2016</span></span><br /><br /> <span data-ttu-id="fea95-157">[安裝 SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)</span><span class="sxs-lookup"><span data-stu-id="fea95-157">[Install SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)</span></span>|<span data-ttu-id="fea95-158">是</span><span class="sxs-lookup"><span data-stu-id="fea95-158">Yes</span></span>|  
    |<span data-ttu-id="fea95-159">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fea95-159">SharePoint 2013</span></span><br /><br /> [<span data-ttu-id="fea95-160">安裝 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fea95-160">Install SharePoint 2013</span></span>](https://technet.microsoft.com/library/cc262957.aspx)|<span data-ttu-id="fea95-161">是</span><span class="sxs-lookup"><span data-stu-id="fea95-161">Yes</span></span>|  
    |<span data-ttu-id="fea95-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fea95-162">SharePoint Online</span></span><br /><br /> [<span data-ttu-id="fea95-163">SharePoint Online 管理</span><span class="sxs-lookup"><span data-stu-id="fea95-163">SharePoint Online administration</span></span>](https://technet.microsoft.com/library/gg132908.aspx)|<span data-ttu-id="fea95-164">是</span><span class="sxs-lookup"><span data-stu-id="fea95-164">Yes</span></span>|  
    |<span data-ttu-id="fea95-165">SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="fea95-165">SharePoint 2010</span></span><br /><br /> <span data-ttu-id="fea95-166">[SharePoint Server 2010 的安裝和部署](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)</span><span class="sxs-lookup"><span data-stu-id="fea95-166">[Installation and Deployment for SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)</span></span>|<span data-ttu-id="fea95-167">是</span><span class="sxs-lookup"><span data-stu-id="fea95-167">Yes</span></span>|  
    |<span data-ttu-id="fea95-168">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="fea95-168">SharePoint 2007</span></span> |<span data-ttu-id="fea95-169">否</span><span class="sxs-lookup"><span data-stu-id="fea95-169">No</span></span>|  
  
2.  <span data-ttu-id="fea95-170">在 BizTalk 伺服器上，安裝 Windows Identity Foundation:</span><span class="sxs-lookup"><span data-stu-id="fea95-170">On the BizTalk Server, install Windows Identity Foundation:</span></span>  
  
    | <span data-ttu-id="fea95-171">作業系統</span><span class="sxs-lookup"><span data-stu-id="fea95-171">Operating System</span></span> | <span data-ttu-id="fea95-172">資訊</span><span class="sxs-lookup"><span data-stu-id="fea95-172">Info</span></span> |  
    |---|---|  
    |<span data-ttu-id="fea95-173">Windows 10、 Windows 8.1、 Windows Server 2016、 Windows Server 2012 和 Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fea95-173">Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012, and Windows Server 2012 R2</span></span>|<span data-ttu-id="fea95-174">Windows Identity Foundation 隨附於作業系統的 [開啟或關閉 Windows 功能] 功能之一。</span><span class="sxs-lookup"><span data-stu-id="fea95-174">Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.</span></span>|  
    |<span data-ttu-id="fea95-175">Windows Vista SP1</span><span class="sxs-lookup"><span data-stu-id="fea95-175">Windows Vista SP1</span></span>|<span data-ttu-id="fea95-176">可在 [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) 下載。</span><span class="sxs-lookup"><span data-stu-id="fea95-176">Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331).</span></span>|  
  
3.  <span data-ttu-id="fea95-177">安裝 BizTalk Server:</span><span class="sxs-lookup"><span data-stu-id="fea95-177">Install BizTalk Server:</span></span>

    | |  |  
    |---|---|  
     | <span data-ttu-id="fea95-178">BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="fea95-178">BizTalk Server 2016</span></span> | <span data-ttu-id="fea95-179">執行 BizTalk 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="fea95-179">Run BizTalk setup.</span></span> |
    | <span data-ttu-id="fea95-180">BizTalk Server 2013 R2</span><span class="sxs-lookup"><span data-stu-id="fea95-180">BizTalk Server 2013 R2</span></span> | <span data-ttu-id="fea95-181">執行 BizTalk 安裝程式，並**未**核取 [Windows SharePoint Services 配接器]。</span><span class="sxs-lookup"><span data-stu-id="fea95-181">Run BizTalk setup, and do **not** check **Windows SharePoint Services Adapter**.</span></span> |  
    | <span data-ttu-id="fea95-182">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="fea95-182">BizTalk Server 2013</span></span> | <span data-ttu-id="fea95-183">執行 BizTalk 安裝程式，並**未**核取 [Windows SharePoint Services 配接器]。</span><span class="sxs-lookup"><span data-stu-id="fea95-183">Run BizTalk setup, and do **not** check **Windows SharePoint Services Adapter**.</span></span> |
  
##  <a name="BKMK_SSOM"></a> <span data-ttu-id="fea95-184">安裝 SSOM SharePoint 配接器 (已取代)</span><span class="sxs-lookup"><span data-stu-id="fea95-184">Install the SSOM SharePoint adapter (deprecated)</span></span>  
  
1.  <span data-ttu-id="fea95-185">使用下列 SSOM 需求為基礎的 SharePoint 電腦：</span><span class="sxs-lookup"><span data-stu-id="fea95-185">Use a SharePoint computer based on the following SSOM requirements:</span></span>  
  
    ||<span data-ttu-id="fea95-186">SSOM 支援</span><span class="sxs-lookup"><span data-stu-id="fea95-186">SSOM Support</span></span>|  
    |---|---|  
    |<span data-ttu-id="fea95-187">SharePoint 2016</span><span class="sxs-lookup"><span data-stu-id="fea95-187">SharePoint 2016</span></span><br /><br /> <span data-ttu-id="fea95-188">[安裝 SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)</span><span class="sxs-lookup"><span data-stu-id="fea95-188">[Install SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)</span></span>|<span data-ttu-id="fea95-189">否</span><span class="sxs-lookup"><span data-stu-id="fea95-189">No</span></span>| 
    |<span data-ttu-id="fea95-190">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fea95-190">SharePoint 2013</span></span><br /><br /> [<span data-ttu-id="fea95-191">安裝 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fea95-191">Install SharePoint 2013</span></span>](http://technet.microsoft.com/library/cc303424.aspx)|<span data-ttu-id="fea95-192">否</span><span class="sxs-lookup"><span data-stu-id="fea95-192">No</span></span>|  
    |<span data-ttu-id="fea95-193">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fea95-193">SharePoint Online</span></span><br /><br /> [<span data-ttu-id="fea95-194">SharePoint Online 管理</span><span class="sxs-lookup"><span data-stu-id="fea95-194">SharePoint Online administration</span></span>](https://technet.microsoft.com/library/gg132908.aspx)|<span data-ttu-id="fea95-195">否</span><span class="sxs-lookup"><span data-stu-id="fea95-195">No</span></span>|  
    |<span data-ttu-id="fea95-196">SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="fea95-196">SharePoint 2010</span></span><br /><br /> <span data-ttu-id="fea95-197">[SharePoint Server 2010 的安裝和部署](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)</span><span class="sxs-lookup"><span data-stu-id="fea95-197">[Installation and Deployment for SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)</span></span>|<span data-ttu-id="fea95-198">是</span><span class="sxs-lookup"><span data-stu-id="fea95-198">Yes</span></span>|  
    |<span data-ttu-id="fea95-199">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="fea95-199">SharePoint 2007</span></span><br /><br /> <span data-ttu-id="fea95-200">[SharePoint Server 2007 的安裝](https://technet.microsoft.com/library/cc262957(v=office.12).aspx)</span><span class="sxs-lookup"><span data-stu-id="fea95-200">[Installation for SharePoint Server 2007](https://technet.microsoft.com/library/cc262957(v=office.12).aspx)</span></span> |<span data-ttu-id="fea95-201">是</span><span class="sxs-lookup"><span data-stu-id="fea95-201">Yes</span></span>|  
  
2.  <span data-ttu-id="fea95-202">SharePoint 電腦上，設定 SharePoint，及擴充預設的網站。</span><span class="sxs-lookup"><span data-stu-id="fea95-202">On the SharePoint computer, configure SharePoint, and extend the Default Web Site.</span></span> <span data-ttu-id="fea95-203">當您擴充網站時，會建立包含相同內容的個別 IIS 網站，同時提供一個唯一 URL 和驗證類型。</span><span class="sxs-lookup"><span data-stu-id="fea95-203">When you extend the web site, a separate IIS web site is created that contains the same content but also provides a unique URL and authentication type.</span></span>  
  
     <span data-ttu-id="fea95-204">請參閱 [SharePoint 2010：擴充 Web 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=259124)。</span><span class="sxs-lookup"><span data-stu-id="fea95-204">See [SharePoint 2010: Extend a Web Application](http://go.microsoft.com/fwlink/p/?LinkId=259124).</span></span>  
  
3.  <span data-ttu-id="fea95-205">SharePoint 電腦上，執行 BizTalk Server 安裝和**只**檢查**Windows SharePoint Services 配接器**。</span><span class="sxs-lookup"><span data-stu-id="fea95-205">On the SharePoint computer, run the BizTalk Server installation and **only** check **Windows SharePoint Services Adapter**.</span></span> <span data-ttu-id="fea95-206">這會安裝 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fea95-206">This installs the web service.</span></span> <span data-ttu-id="fea95-207">**請不要執行 BizTalk 組態**。</span><span class="sxs-lookup"><span data-stu-id="fea95-207">**Do not run the BizTalk configuration**.</span></span>  
  
4.  <span data-ttu-id="fea95-208">在 BizTalk 伺服器上，安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="fea95-208">On the BizTalk Server, install BizTalk Server.</span></span> <span data-ttu-id="fea95-209">請**不**要核取 [Windows SharePoint Services 配接器]。</span><span class="sxs-lookup"><span data-stu-id="fea95-209">Do **not** check **Windows SharePoint Services Adapter**.</span></span>  
  
5.  <span data-ttu-id="fea95-210">SharePoint Web 服務 (SSOM) 只會在 64 位元模式下執行。</span><span class="sxs-lookup"><span data-stu-id="fea95-210">The SharePoint Web Service (SSOM) only runs in 64-bit mode.</span></span> <span data-ttu-id="fea95-211">SharePoint 電腦上的 ASP.NET 和 IIS 應用程式集區必須處於 64 位元模式，才能安裝 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="fea95-211">ASP.NET and the IIS application pool must be in 64-bit mode on the SharePoint computer before installing SharePoint.</span></span> <span data-ttu-id="fea95-212">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="fea95-212">To do this:</span></span>  
  
    -   <span data-ttu-id="fea95-213">**ASP.NET**︰開啟 IIS 管理員中，並按一下網站，然後按兩下 [處理常式對應]。</span><span class="sxs-lookup"><span data-stu-id="fea95-213">**ASP.NET**: Open IIS Manager, click the web site, and then double-click **Handler Mappings**.</span></span> <span data-ttu-id="fea95-214">在 [已啟用] 清單中，確認列出 [PageHandlerFactory-ISAPI-2.0-64]。</span><span class="sxs-lookup"><span data-stu-id="fea95-214">In the **Enabled** list, confirm **PageHandlerFactory-ISAPI-2.0-64** is listed.</span></span>  
  
    -   <span data-ttu-id="fea95-215">**應用程式集區**：開啟 IIS 管理員，並按一下 [應用程式集區]，再選取應用程式集區，然後按一下 [進階設定]。</span><span class="sxs-lookup"><span data-stu-id="fea95-215">**Application Pool**: Open IIS Manager, click **Application Pools**, select the application pool, and then click **Advanced Settings**.</span></span> <span data-ttu-id="fea95-216">在 [啟用 32 位元應用程式] 中，選取 [False]。</span><span class="sxs-lookup"><span data-stu-id="fea95-216">In **Enable 32-bit applications**, select **False**.</span></span>  

