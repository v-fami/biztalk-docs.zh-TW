---
title: "安裝 BizTalk Accelerator for RosettaNet (BTARN) 在 BizTalk Server 上 |Microsoft 文件"
description: "請參閱硬體和軟體需求、 安裝的步驟和 BTARN BizTalk Server 中的組態步驟"
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a40eca3ccd2092cc3024e0ad69d3737bad869180
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-accelerator-for-rosettanet"></a><span data-ttu-id="8e501-103">安裝 BizTalk Accelerator for RosettaNet</span><span class="sxs-lookup"><span data-stu-id="8e501-103">Install BizTalk Accelerator for RosettaNet</span></span>

## <a name="overview"></a><span data-ttu-id="8e501-104">概觀</span><span class="sxs-lookup"><span data-stu-id="8e501-104">Overview</span></span>
<span data-ttu-id="8e501-105">安裝 Microsoft BizTalk Accelerator for RosettaNet (BTARN)。</span><span class="sxs-lookup"><span data-stu-id="8e501-105">Install the Microsoft BizTalk Accelerator for RosettaNet (BTARN).</span></span>
  
> [!NOTE]
>  <span data-ttu-id="8e501-106">Enterprise Edition 的 BizTalk Server 上，您可以安裝只有 Enterprise 版的 BizTalk Accelerator for RosettaNet (BTARN)。</span><span class="sxs-lookup"><span data-stu-id="8e501-106">On the Enterprise Edition of BizTalk Server, you can install only the Enterprise Edition of BizTalk Accelerator for RosettaNet (BTARN).</span></span> <span data-ttu-id="8e501-107">在標準版本的 BizTalk 伺服器上，您可以安裝僅標準版的 BizTalk Accelerator for RosettaNet (BTARN)。</span><span class="sxs-lookup"><span data-stu-id="8e501-107">On the Standard Edition of BizTalk Server, you can install only the Standard Edition of BizTalk Accelerator for RosettaNet (BTARN).</span></span>  
  
 <span data-ttu-id="8e501-108">BTARN 安裝包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="8e501-108">The BTARN installation includes the following:</span></span>  
  
-   <span data-ttu-id="8e501-109">管理 BTARN</span><span class="sxs-lookup"><span data-stu-id="8e501-109">BTARN Administration</span></span>  
  
-   <span data-ttu-id="8e501-110">BizTalk 協調流程設計師 XLANG 排程 (「交易夥伴介面程序」 模式)</span><span class="sxs-lookup"><span data-stu-id="8e501-110">BizTalk Orchestration Designer XLANG schedules (Partner Interface Process patterns)</span></span>  
  
-   <span data-ttu-id="8e501-111">RosettaNet 實作架構 (RNIF)</span><span class="sxs-lookup"><span data-stu-id="8e501-111">RosettaNet Implementation Framework (RNIF)</span></span>  
  
-   <span data-ttu-id="8e501-112">BTARN 資料庫</span><span class="sxs-lookup"><span data-stu-id="8e501-112">BTARN database</span></span>  
  
-   <span data-ttu-id="8e501-113">HTTP 前端 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8e501-113">HTTP front end Web applications</span></span>  
  
## <a name="hardware-and-software-requirements"></a><span data-ttu-id="8e501-114">硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="8e501-114">Hardware and software requirements</span></span>

<span data-ttu-id="8e501-115">最低硬體和軟體需求會與 BizTalk Server 相同。</span><span class="sxs-lookup"><span data-stu-id="8e501-115">The minimum hardware and software requirements are the same as BizTalk Server.</span></span>

|  |<span data-ttu-id="8e501-116">BizTalk 需求</span><span class="sxs-lookup"><span data-stu-id="8e501-116">BizTalk requirements</span></span>  |<span data-ttu-id="8e501-117">SQL 和作業系統需求</span><span class="sxs-lookup"><span data-stu-id="8e501-117">SQL and OS requirements</span></span> |  
|---------|---------|--------- | 
| [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [<span data-ttu-id="8e501-118">BizTalk Server 2016 的硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="8e501-118">Hardware and Software Requirements for BizTalk Server 2016</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) | <span data-ttu-id="8e501-119">**SQL Server 硬體和軟體需求**:</span><span class="sxs-lookup"><span data-stu-id="8e501-119">**SQL Server hardware and software requirements**:</span></span> <br/><span data-ttu-id="8e501-120">[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e501-120">[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)</span></span><br/><span data-ttu-id="8e501-121">[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e501-121">[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)</span></span><br/><br/><span data-ttu-id="8e501-122">**Windows Server 硬體需求**:</span><span class="sxs-lookup"><span data-stu-id="8e501-122">**Windows Server hardware requirements**:</span></span> <br/>[<span data-ttu-id="8e501-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8e501-123">Windows Server 2016</span></span>](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[<span data-ttu-id="8e501-124">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8e501-124">Windows Server 2012</span></span>](https://technet.microsoft.com/library/jj134246.aspx) |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> <span data-ttu-id="8e501-125">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="8e501-125">BizTalk Server 2013</span></span> | [<span data-ttu-id="8e501-126">硬體和軟體需求適用於 BizTalk Server 2013 和 2013 R2</span><span class="sxs-lookup"><span data-stu-id="8e501-126">Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) |<span data-ttu-id="8e501-127">**SQL Server 硬體和軟體需求**:</span><span class="sxs-lookup"><span data-stu-id="8e501-127">**SQL Server hardware and software requirements**:</span></span> <br/><span data-ttu-id="8e501-128">[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e501-128">[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)</span></span><br/><span data-ttu-id="8e501-129">[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e501-129">[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)</span></span><br/><span data-ttu-id="8e501-130">[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e501-130">[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)</span></span><br/><br/><span data-ttu-id="8e501-131">**Windows Server 硬體需求**:</span><span class="sxs-lookup"><span data-stu-id="8e501-131">**Windows Server hardware requirements**:</span></span> <br/>[<span data-ttu-id="8e501-132">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8e501-132">Windows Server 2012</span></span>](https://technet.microsoft.com/library/jj134246.aspx)<br/><span data-ttu-id="8e501-133">[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e501-133">[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)</span></span>  |

> [!TIP] 
> <span data-ttu-id="8e501-134">列出的硬體需求是最小需求。</span><span class="sxs-lookup"><span data-stu-id="8e501-134">The hardware requirements listed are the minimum.</span></span> <span data-ttu-id="8e501-135">每個環境都不同，但您的環境極有可能需要更多需求。</span><span class="sxs-lookup"><span data-stu-id="8e501-135">Every environment is different and there's a very good chance that your environment may need more.</span></span> <span data-ttu-id="8e501-136">請參閱 [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx) (安裝、調整大小、部署和維護 BizTalk Server 解決方案的建議)。</span><span class="sxs-lookup"><span data-stu-id="8e501-136">See [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx).</span></span> 

## <a name="install-and-configure"></a><span data-ttu-id="8e501-137">安裝和設定</span><span class="sxs-lookup"><span data-stu-id="8e501-137">Install and configure</span></span>

### <a name="before-you-begin"></a><span data-ttu-id="8e501-138">開始之前</span><span class="sxs-lookup"><span data-stu-id="8e501-138">Before you begin</span></span>

* <span data-ttu-id="8e501-139">BTARN 資料庫中，BTARN 只會設定 SQL Server 的電腦名稱和資料庫名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="8e501-139">For the BTARN database, BTARN only configures the SQL Server computer name and database name properties.</span></span> <span data-ttu-id="8e501-140">關於這些屬性的資訊儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="8e501-140">Information about these properties is stored in the registry.</span></span>
* <span data-ttu-id="8e501-141">使用成員的帳戶登入 BizTalk Server 系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="8e501-141">Sign in using an account that is a member of the the BizTalk Server Administrators group.</span></span> 
* <span data-ttu-id="8e501-142">在您的 BizTalk Server 下載 BTARN 安裝程式是在`\BizTalk Accelerators`資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e501-142">In your BizTalk Server download, the BTARN setup is in the `\BizTalk Accelerators` folder.</span></span>
* <span data-ttu-id="8e501-143">BizTalk Server，必須先安裝，且必須執行 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8e501-143">BizTalk Server must be installed, and SQL Server must be running.</span></span>
* <span data-ttu-id="8e501-144">BTARN 和 BizTalk Server 需要 Microsoft.NET Framework 軟體必要元件。</span><span class="sxs-lookup"><span data-stu-id="8e501-144">Both BTARN and BizTalk Server require Microsoft .NET Framework as software prerequisite.</span></span> <span data-ttu-id="8e501-145">如果您有多個版本的電腦上安裝的.NET Framework，請確定 BtarnAPP Web 應用程式參考傳統.NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="8e501-145">If you have multiple versions of .NET Framework installed on your computer, make sure that the BtarnAPP Web application is referencing .NET Framework 4.0 classic.</span></span> <span data-ttu-id="8e501-146">您可使用 Internet Information Services (IIS) 管理員設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="8e501-146">You can configure this by using the Internet Information Services (IIS) Manager.</span></span>  
* <span data-ttu-id="8e501-147">BizTalk 主控件執行個體帳戶和 BizTalk 外掛式主控件執行個體帳戶應該要相同。</span><span class="sxs-lookup"><span data-stu-id="8e501-147">The BizTalk Host Instance Account and the BizTalk Isolated Host Instance Account should be the same.</span></span> <span data-ttu-id="8e501-148">否則，BTARN 無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="8e501-148">Otherwise, BTARN does not function correctly.</span></span>  
* <span data-ttu-id="8e501-149">BTARN 可讓您將只能個別的服務帳戶並不是群組新增至 BizTalk Server 系統管理員群組或 BizTalk 應用程式使用者群組。</span><span class="sxs-lookup"><span data-stu-id="8e501-149">BTARN allows you to add only individual service accounts, and not groups, to the BizTalk Server Administrators group or the BizTalk Application Users group.</span></span>  
* <span data-ttu-id="8e501-150">您必須建立 BTSHTTPReceive.dll 的 WebService 延伸模組，設定 IIS 隔離模式。</span><span class="sxs-lookup"><span data-stu-id="8e501-150">You need to create a WebService extension for BTSHTTPReceive.dll, configuring the IIS isolation mode.</span></span> <span data-ttu-id="8e501-151">如需詳細資訊，請參閱 「 疑難排解： 問題與解決方式 」 主題，網址的 「 404 找不到錯誤時，傳送 HTTP 要求 「 項[http://go.microsoft.com/fwlink/?LinkId=188560](http://go.microsoft.com/fwlink/?LinkId=188560)。</span><span class="sxs-lookup"><span data-stu-id="8e501-151">For more information, see the "404 Not found error when sending a HTTP request" entry in the "Troubleshooting: Issues and Resolutions" topic at [http://go.microsoft.com/fwlink/?LinkId=188560](http://go.microsoft.com/fwlink/?LinkId=188560).</span></span> <span data-ttu-id="8e501-152">此外，請參閱[如何設定 HTTP 接收位置的 IIS](../../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="8e501-152">Also, see [How to Configure IIS for an HTTP Receive Location](../../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
* <span data-ttu-id="8e501-153">加入您的伺服器 (http:// <*伺服器名稱*>) 至 Internet Explorer 安全性選項的本機網際網路區域。</span><span class="sxs-lookup"><span data-stu-id="8e501-153">Add your server (http://<*server name*>) to the Local Internet zone in the Internet Explorer security options.</span></span>  
*  <span data-ttu-id="8e501-154">如果用來設定 BTARN 的遠端 SQL 執行個體使用非預設連接埠，則 SQL Server 用戶端工具必須安裝在本機。</span><span class="sxs-lookup"><span data-stu-id="8e501-154">If a remote SQL instance using non default port is used for configuring BTARN, then the SQL Server Client Tools must be installed locally.</span></span> <span data-ttu-id="8e501-155">如需詳細資訊，請參閱[多重電腦環境中的 BizTalk Server 安裝指南 》](../../install-and-config-guides/install-biztalk-server-in-a-multi-computer-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="8e501-155">For details, see [BizTalk Server Installation Guide for multicomputer environment](../../install-and-config-guides/install-biztalk-server-in-a-multi-computer-environment.md).</span></span>
*  <span data-ttu-id="8e501-156">不同的群組必須用於 BizTalk Server 的組態期間，角色-BizTalk 系統管理員、 BizTalk 主控件使用者 」 和 BizTalk 外掛式主控件使用者。</span><span class="sxs-lookup"><span data-stu-id="8e501-156">A separate group must be used for role - BizTalk Administrator, BizTalk Host Users, and BizTalk Isolated Host Users during the configuration of BizTalk Server.</span></span>  
*  <span data-ttu-id="8e501-157">BTARN 不支援設定 BTARN 資料庫的 SQL 執行個體別名的使用。</span><span class="sxs-lookup"><span data-stu-id="8e501-157">BTARN does not support the use of alias created for SQL instance to configure the BTARN database.</span></span>  

### <a name="install-btarn"></a><span data-ttu-id="8e501-158">安裝 BTARN</span><span class="sxs-lookup"><span data-stu-id="8e501-158">Install BTARN</span></span>

1.  <span data-ttu-id="8e501-159">執行 BTARN **setup.exe**以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="8e501-159">Run the BTARN **setup.exe** as Administrator.</span></span>
  
2.  <span data-ttu-id="8e501-160">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="8e501-160">Select **Install**.</span></span>  
  
3.  <span data-ttu-id="8e501-161">在**客戶資訊**頁面上，輸入您的使用者名稱、 組織及產品金鑰，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8e501-161">On the **Customer Information** page, type your user name, organization, and the product key, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8e501-162">在**合約**頁面上，閱讀使用者授權合約，然後按**接受**。</span><span class="sxs-lookup"><span data-stu-id="8e501-162">On the **License Agreement** page, read the End User License Agreement, and then click **Accept**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e501-163">如果您不接受授權合約，您不能繼續安裝。</span><span class="sxs-lookup"><span data-stu-id="8e501-163">If you do not accept the license agreement, you cannot continue with the installation.</span></span>  
  
5.  <span data-ttu-id="8e501-164">在**安裝選項**頁面上，選取**完成**完整安裝或**自訂**進行部分安裝。</span><span class="sxs-lookup"><span data-stu-id="8e501-164">On the **Installation Options** page, select **Complete** for a full installation or **Custom** for a partial installation.</span></span> <span data-ttu-id="8e501-165">請確定安裝路徑是正確的，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="8e501-165">Ensure the installation path is correct, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e501-166">如果您選取**自訂**，選取要從安裝的元件**自訂安裝**頁面。</span><span class="sxs-lookup"><span data-stu-id="8e501-166">If you select **Custom**, select the components to install from the **Custom Installation** page.</span></span> <span data-ttu-id="8e501-167">如果您選擇安裝 SDK 或文件集元件，您必須再執行安裝程式安裝.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="8e501-167">If you select to install SDK or Documentation components only, you must have .NET Framework installed before running the setup program.</span></span>  
  
6.  <span data-ttu-id="8e501-168">在**摘要**頁面上，檢閱您要安裝，然後再按一下元件**安裝**。</span><span class="sxs-lookup"><span data-stu-id="8e501-168">On the **Summary** page, review the components you are installing, and then click **Install**.</span></span> <span data-ttu-id="8e501-169">**安裝進度**螢幕顯示的安裝程序的進度。</span><span class="sxs-lookup"><span data-stu-id="8e501-169">The **Installation Progress** screen displays the progress of the installation procedure.</span></span>  
  
7.  <span data-ttu-id="8e501-170">在**安裝完成**頁面上，確定**執行組態精靈**中已選取，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="8e501-170">On the **Installation Completed** page, ensure the **Run Configuration Wizard** box is selected, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="8e501-171">[BTARN 組態精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="8e501-171">The BTARN Configuration Wizard opens.</span></span> <span data-ttu-id="8e501-172">接下來，您會設定 BTARN。</span><span class="sxs-lookup"><span data-stu-id="8e501-172">Next, you configure BTARN.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8e501-173">如果您執行只安裝 BTARN HTTP 前端功能的自訂安裝，BTARN 組態可能會失敗之後安裝程式已完成，顯示 「 無法建立功能的物件： WebApp 」 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e501-173">If you perform a custom installation to install only the BTARN HTTP Front End feature, BTARN configuration may fail after setup is complete, displaying the "Failed to create object for feature: WebApp" error.</span></span> <span data-ttu-id="8e501-174">如果發生這種情況，將兩個檔案複製 (**Microsoft.VC80.ATL.manifest**和**atl80.dll**) 從 BizTalk Server 的電腦上安裝，若要安裝 BTARN HTTP 前端功能的電腦。</span><span class="sxs-lookup"><span data-stu-id="8e501-174">If this occurs, copy two files (**Microsoft.VC80.ATL.manifest** and **atl80.dll**) from a computer with BizTalk Server installed on it, to the computer where you installed the BTARN HTTP Front End feature.</span></span>  
    >   
    >  <span data-ttu-id="8e501-175">如果與 BizTalk Server 在相同電腦上安裝 Visual Studio，兩個檔案的來源資料夾是*< 磁碟機\>*: \Program Files\Microsoft Visual Studio 11.0\VC\redist\x86\Microsoft.VC100.ATL。</span><span class="sxs-lookup"><span data-stu-id="8e501-175">If Visual Studio is installed on the same computer as BizTalk Server, the source folder for the two files is *<drive\>*:\Program Files\Microsoft Visual Studio 11.0\VC\redist\x86\Microsoft.VC100.ATL.</span></span> <span data-ttu-id="8e501-176">如果 BizTalk server 上未安裝 Visual Studio，BizTalk server 上的兩個檔案的來源資料夾是資料夾之下的*< 磁碟機\>*: \WINDOWS\WinSxS。</span><span class="sxs-lookup"><span data-stu-id="8e501-176">If Visual Studio is not installed on the BizTalk server, the source folder for the two files on the BizTalk server is a folder under *<drive\>*:\WINDOWS\WinSxS.</span></span> <span data-ttu-id="8e501-177">檔案版本應為 8.0.50727.42。</span><span class="sxs-lookup"><span data-stu-id="8e501-177">The version of the files should be 8.0.50727.42.</span></span> <span data-ttu-id="8e501-178">在已安裝 HTTP 前端功能的電腦上目的地資料夾是 BTARN 安裝目錄 (根據預設， *< 磁碟機\>*: \Program Files\Microsoft BTARN)。</span><span class="sxs-lookup"><span data-stu-id="8e501-178">The destination folder on the computer where you have installed the HTTP Front End feature is the BTARN installation directory (by default, *<drive\>*:\Program Files\Microsoft BTARN).</span></span>  
    >   
    >  <span data-ttu-id="8e501-179">您將這些檔案複製到電腦已安裝 HTTP 前端功能之後，重新執行**Configuration.exe**。</span><span class="sxs-lookup"><span data-stu-id="8e501-179">After you have copied these files to the computer with the HTTP Front End feature installed, rerun **Configuration.exe**.</span></span>  
  
### <a name="configure-btarn"></a><span data-ttu-id="8e501-180">設定 BTARN</span><span class="sxs-lookup"><span data-stu-id="8e501-180">Configure BTARN</span></span>  

> [!TIP]
 >  <span data-ttu-id="8e501-181">之前設定 BTARN，請確定您將對應的.NET Framework 在 IIS 中的處理常式對應底下。</span><span class="sxs-lookup"><span data-stu-id="8e501-181">Before configuring BTARN, make sure you map .NET Framework under Handler Mappings in IIS.</span></span> <span data-ttu-id="8e501-182">此外，當設定 BTARN，您可能需要手動建立 IIS_WPG 群組。</span><span class="sxs-lookup"><span data-stu-id="8e501-182">Also, when configuring BTARN, you may need to create the IIS_WPG group manually.</span></span>  
   
1.  <span data-ttu-id="8e501-183">在**Microsoft BTARN 組態精靈**頁面上，選取**基本組態**設定伺服器預設設定，或**自訂組態**至設定伺服器使用進階的組態選項。</span><span class="sxs-lookup"><span data-stu-id="8e501-183">On the **Microsoft BTARN Configuration Wizard** page, select **Basic configuration** to configure the server with default settings, or **Custom configuration** to configure the server using advanced configuration options.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e501-184">如果您想要設定 BTARN 使用本機系統管理員帳戶，請輸入帳戶做為*< 機器名稱\>\\< 系統管理員名稱\>*中**使用者識別碼**欄位**服務認證**區域。</span><span class="sxs-lookup"><span data-stu-id="8e501-184">If you want to configure BTARN using a local administrator account, enter the account as *<machine name\>\\<administrator name\>* in the **User ID** field of the **Service Credential** area.</span></span>  
  
2.  <span data-ttu-id="8e501-185">在**資料庫伺服器名稱**文字方塊中，確認顯示的伺服器名稱正確無誤。</span><span class="sxs-lookup"><span data-stu-id="8e501-185">In the **Database server name** text box, verify that the server name displayed is correct.</span></span> <span data-ttu-id="8e501-186">在**服務認證**區域中，輸入執行服務的帳戶 （及網域） 的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8e501-186">In the **Service credential** area, enter the user name (with domain) and password for the account that the services will run under.</span></span> <span data-ttu-id="8e501-187">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8e501-187">Click **Configure**.</span></span>  
  
3.  <span data-ttu-id="8e501-188">如果您的帳戶具有系統管理權限，請按一下**是**以便進行設定。</span><span class="sxs-lookup"><span data-stu-id="8e501-188">If your account has administrative privileges, click **Yes** to proceed with the configuration.</span></span>  
  
4.  <span data-ttu-id="8e501-189">如果您選取**基本組態**在步驟 1 中，確認要在中設定的元件清單**摘要**對話方塊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8e501-189">If you selected **Basic configuration** in step 1, verify the list of components to be configured in the **Summary** dialog box, and then click **Next**.</span></span> <span data-ttu-id="8e501-190">移至步驟 10。</span><span class="sxs-lookup"><span data-stu-id="8e501-190">Go to step 10.</span></span>  
  
5.  <span data-ttu-id="8e501-191">如果您選取**自訂組態**在步驟 1 中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8e501-191">If you selected **Custom configuration** in step 1, perform the following steps:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e501-192">如果您在任何 BTARN 資料庫的名稱中使用特殊字元，BTARN 組態將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8e501-192">BTARN configuration will fail if you use a special character in the name of any of the BTARN databases.</span></span>  
  
6.  <span data-ttu-id="8e501-193">在 設定執行階段， **Microsoft BTRAN 組態**對話方塊中，按一下 **執行階段**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="8e501-193">To configure the runtime, in the **Microsoft BTRAN Configuration** dialog box, click **Runtime** in the left pane.</span></span> <span data-ttu-id="8e501-194">在右邊**執行階段**] 窗格中，按一下 [**啟用這部電腦上的執行階段功能**。</span><span class="sxs-lookup"><span data-stu-id="8e501-194">In the right **Runtime** pane, click **Enable the Runtime feature on this computer**.</span></span> <span data-ttu-id="8e501-195">若要加入現有的資料庫群組，請清除**您想要建立新的資料庫群組**。</span><span class="sxs-lookup"><span data-stu-id="8e501-195">To join an existing database group, clear **Do you want to create a new database group**.</span></span> <span data-ttu-id="8e501-196">請選取適當的 Web 伺服器名稱、連接埠編號、資料存放區、應用程式集區服務帳戶以及 BizTalk HTTP 接收虛擬資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e501-196">Select the appropriate Web server name, port number, data stores, Application Pool service account, and BizTalk HTTP Receive virtual folder.</span></span>  
  
7.  <span data-ttu-id="8e501-197">若要設定 WebApps 功能，在**Microsoft BTRAN 組態**對話方塊中，按一下  **WebApps**在左的窗格中，然後按一下**啟用這部電腦上的執行階段功能**.</span><span class="sxs-lookup"><span data-stu-id="8e501-197">To configure the WebApps feature, in the **Microsoft BTRAN Configuration** dialog box, click **WebApps** in the left pane, and then click **Enable the Runtime feature on this computer**.</span></span> <span data-ttu-id="8e501-198">輸入適當的 BizTalk Server 名稱和連接埠號碼，或選取的預設值。</span><span class="sxs-lookup"><span data-stu-id="8e501-198">Enter the appropriate BizTalk Server name and port number, or select the defaults.</span></span> <span data-ttu-id="8e501-199">選取適當的 Web 應用程式虛擬資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e501-199">Select the appropriate Web application virtual folder.</span></span>  
  
8.  <span data-ttu-id="8e501-200">按一下 [套用組態]。</span><span class="sxs-lookup"><span data-stu-id="8e501-200">Click **Apply Configuration**.</span></span>  
  
9. <span data-ttu-id="8e501-201">在**摘要**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8e501-201">On the **Summary** page, click **Next**.</span></span>  
  
10. <span data-ttu-id="8e501-202">在**完成設定**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="8e501-202">On the **Configuration Completed** page, click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e501-203">在您安裝 BTARN 之後，您的系統管理員必須將使用者加入至 BAS「商務使用者」、「商務經理人」和「商務管理員」群組。</span><span class="sxs-lookup"><span data-stu-id="8e501-203">After you install BTARN, your system administrator must add users to the BAS Business User, Business Manager, and Business Administrator groups.</span></span> <span data-ttu-id="8e501-204">如果您是系統管理員，則需要填入這些群組並登出，然後登入，以將您自己新增至群組。</span><span class="sxs-lookup"><span data-stu-id="8e501-204">If you are a system administrator, you will have to populate these groups and log off, and then log in adding yourself to the groups.</span></span>
  
    > [!WARNING]
    >  <span data-ttu-id="8e501-205">BizTalk 系統管理員、 BizTalk 主控件使用者 」 和 BizTalk 外掛式主控件使用者設定 BizTalk Server 時，必須使用三個不同的群組。</span><span class="sxs-lookup"><span data-stu-id="8e501-205">Three different groups must be used while configuring BizTalk Server for BizTalk Administrator, BizTalk Host Users, and BizTalk Isolated Host Users.</span></span>  

## <a name="start-the-artifacts"></a><span data-ttu-id="8e501-206">啟動成品</span><span class="sxs-lookup"><span data-stu-id="8e501-206">Start the artifacts</span></span>
<span data-ttu-id="8e501-207">BTARN 協調流程傳送埠和接收位置不會自動啟動設定 BTARN 之後。</span><span class="sxs-lookup"><span data-stu-id="8e501-207">The BTARN orchestrations, send ports, and receive locations are not automatically started after you configure BTARN.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="8e501-208">您必須先啟動 PrivateInitiator_To_LOB 傳送埠和 PrivateResponder_To_LOB 傳送埠，然後才能啟動 PrivateInitiatorProcess 和 PrivateResponderProcess 協調流程。</span><span class="sxs-lookup"><span data-stu-id="8e501-208">Start the PrivateInitiator_To_LOB and PrivateResponder_To_LOB send ports before you can start the PrivateInitiatorProcess and PrivateResponderProcess orchestrations.</span></span>  
  
-   <span data-ttu-id="8e501-209">在已將 Internet Information Services (IIS) 虛擬伺服器設定為使用安全通訊端層 (SSL) 的電腦中，您必須將虛擬伺服器設定為可接受用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="8e501-209">On computers where you have configured an Internet Information Services (IIS) virtual server with Secure Sockets Layer (SSL), you must configure the virtual server to accept the client certificate.</span></span> <span data-ttu-id="8e501-210">請參閱[步驟 4： 啟用安全通訊端在 IIS 中的層](step-4-enabling-secure-sockets-layer-in-iis.md)中[按兩下動作 」 教學課程](double-action-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="8e501-210">See [Step 4: Enabling Secure Sockets Layer in IIS](step-4-enabling-secure-sockets-layer-in-iis.md) in the [Double Action Tutorial](double-action-tutorial.md).</span></span>
  
 
1.  <span data-ttu-id="8e501-211">開啟**BizTalk Server 管理**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="8e501-211">Open **BizTalk Server Administration** as an administrator.</span></span>  
  
2.  <span data-ttu-id="8e501-212">展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="8e501-212">Expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="8e501-213">按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8e501-213">Click **Send Ports**.</span></span> <span data-ttu-id="8e501-214">在右窗格中，每一個未啟動的傳送埠，以滑鼠右鍵按一下，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="8e501-214">In the right pane, for each send port that is not started, right-click and then click **Start**.</span></span>  
  
4.  <span data-ttu-id="8e501-215">按一下**接收埠**和**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="8e501-215">Click **Receive Ports** and **Receive Locations**.</span></span> <span data-ttu-id="8e501-216">在右窗格中，為每個接收位置未啟動，以滑鼠右鍵按一下，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="8e501-216">In the right pane, for each receive location that is not started, right-click and then click **Start**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e501-217">您必須啟動 PrivateInitiator_To_LOB 傳送埠和 PrivateResponder_To_LOB 傳送埠，然後才能啟動 PrivateInitiatorProcess 和 PrivateResponderProcess 協調流程。</span><span class="sxs-lookup"><span data-stu-id="8e501-217">You must start the PrivateInitiator_To_LOB and PrivateResponder_To_LOB send ports before you can start the PrivateInitiatorProcess and PrivateResponderProcess orchestrations.</span></span>  
  
5.  <span data-ttu-id="8e501-218">按一下**協調流程**和**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="8e501-218">Click **Orchestrations** and **Receive Locations**.</span></span> <span data-ttu-id="8e501-219">在右窗格中，每個協調流程未啟動，以滑鼠右鍵按一下，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="8e501-219">In the right pane, for each orchestration that is not started, right-click and then click **Start**.</span></span>  
  
## <a name="restart-your-computer"></a><span data-ttu-id="8e501-220">重新啟動電腦</span><span class="sxs-lookup"><span data-stu-id="8e501-220">Restart your computer</span></span>  
  
<span data-ttu-id="8e501-221">重新啟動您的電腦，以套用對組態和權限進行的任何修改。</span><span class="sxs-lookup"><span data-stu-id="8e501-221">Restart your computer to apply any modifications made in configuration and permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e501-222">開發人員可以選擇在單一伺服器上安裝和設定 BTARN 以進行開發、執行或測試動作。</span><span class="sxs-lookup"><span data-stu-id="8e501-222">Developers may choose to install and configure BTARN on a single server for development, staging, or testing purposes.</span></span> <span data-ttu-id="8e501-223">開發人員使用這個伺服器在將其移動至生產線之前，寫入他們自訂的節點並加以測試。</span><span class="sxs-lookup"><span data-stu-id="8e501-223">Developers use this server to write their own custom code and test it before moving it to production.</span></span>  
  
 <span data-ttu-id="8e501-224">如需在單一伺服器上安裝 BTARN 的詳細資訊，請參閱[回送教學課程](loopback-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="8e501-224">For more information about installing BTARN on a single server, see the [Loopback Tutorial](loopback-tutorial.md).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="8e501-225">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="8e501-225">Next steps</span></span>  
  
* [<span data-ttu-id="8e501-226">升級 RosettaNet 加速器</span><span class="sxs-lookup"><span data-stu-id="8e501-226">Upgrade the RosettaNet accelerator</span></span>](upgrade-biztalk-accelerator-for-rosettanet.md)
* [<span data-ttu-id="8e501-227">解除安裝 RosettaNet 加速器</span><span class="sxs-lookup"><span data-stu-id="8e501-227">Uninstall the RosettaNet accelerator</span></span>](uninstall-biztalk-accelerator-for-rosettanet.md)
* [<span data-ttu-id="8e501-228">安裝的疑難排解，並查看已知的安裝問題</span><span class="sxs-lookup"><span data-stu-id="8e501-228">Troubleshoot the installation and see the known install issues</span></span>](troubleshoot-known-issues-installation.md)