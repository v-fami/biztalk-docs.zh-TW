---
title: "安裝 Microsoft BizTalk Adapter for SQL Server-2013 R2 和 2013年 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c31d0d-783b-41ee-8265-56c9547e9dca
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af91ae787d5800738865980609bb86f96a73bfb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2013-r2-and-2013"></a><span data-ttu-id="f76bf-102">安裝 Microsoft BizTalk Adapter for SQL Server-2013 R2 和 2013</span><span class="sxs-lookup"><span data-stu-id="f76bf-102">Install Microsoft BizTalk Adapter for SQL Server - 2013 R2 and 2013</span></span>
<span data-ttu-id="f76bf-103">安裝[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]隨附[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]，或隨附[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]2013年。</span><span class="sxs-lookup"><span data-stu-id="f76bf-103">Install the [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] included with [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)], or included with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 2013.</span></span>

 <span data-ttu-id="f76bf-104">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以搭配使用：</span><span class="sxs-lookup"><span data-stu-id="f76bf-104">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used with:</span></span>  
  
-   <span data-ttu-id="f76bf-105">.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="f76bf-105">A .NET application</span></span>  
  
-   <span data-ttu-id="f76bf-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f76bf-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
 <span data-ttu-id="f76bf-107">根據您如何使用配接器，所需的軟體而異。</span><span class="sxs-lookup"><span data-stu-id="f76bf-107">Based on how you use the adapters, the required software varies.</span></span>  
 
<a name="BKMK_Prereqs_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a><span data-ttu-id="f76bf-108">當配接器使用.NET 應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="f76bf-108">Prerequisites when using the adapter with a .NET Application</span></span>  
<span data-ttu-id="f76bf-109">您要在其中撰寫可取用的.NET 應用程式的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-109">Install the following software on the computer where you are writing .NET applications that consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="f76bf-110">安裝軟體的順序，如下所列。</span><span class="sxs-lookup"><span data-stu-id="f76bf-110">Install the software in the order as listed.</span></span>  

|<span data-ttu-id="f76bf-111">2013 R2</span><span class="sxs-lookup"><span data-stu-id="f76bf-111">2013 R2</span></span>|<span data-ttu-id="f76bf-112">2013</span><span class="sxs-lookup"><span data-stu-id="f76bf-112">2013</span></span>|  
|---|---|  
|[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]|<span data-ttu-id="f76bf-113">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f76bf-113">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="f76bf-114">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="f76bf-114">Visual Studio 2013</span></span>|<span data-ttu-id="f76bf-115">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="f76bf-115">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|  
|<span data-ttu-id="f76bf-116">SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="f76bf-116">The SQL Server client libraries.</span></span> <span data-ttu-id="f76bf-117">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="f76bf-117">.</span></span>|<span data-ttu-id="f76bf-118">SQL Server 用戶端程式庫...</span><span class="sxs-lookup"><span data-stu-id="f76bf-118">The SQL Server client libraries..</span></span>|  

<a name="BKMK_Prereqs_BTS"></a>    
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a><span data-ttu-id="f76bf-119">搭配 BizTalk Server 使用配接器時的必要條件</span><span class="sxs-lookup"><span data-stu-id="f76bf-119">Prerequisites when using the adapter with BizTalk Server</span></span>  
<span data-ttu-id="f76bf-120">會使用您的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-120">Install the following software on the computer where you will be using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f76bf-121">我們建議您以相同的順序安裝軟體，如這裡所列。</span><span class="sxs-lookup"><span data-stu-id="f76bf-121">We recommend installing the software in the same order as listed here.</span></span>  
 
 |<span data-ttu-id="f76bf-122">2013 R2</span><span class="sxs-lookup"><span data-stu-id="f76bf-122">2013 R2</span></span>|<span data-ttu-id="f76bf-123">2013</span><span class="sxs-lookup"><span data-stu-id="f76bf-123">2013</span></span>|  
|---|---|  
|[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]|<span data-ttu-id="f76bf-124">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f76bf-124">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="f76bf-125">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="f76bf-125">Visual Studio 2013</span></span>|<span data-ttu-id="f76bf-126">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="f76bf-126">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="f76bf-127">安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-127">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="f76bf-128">若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-128">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="f76bf-129">安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-129">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="f76bf-130">若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-130">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>|  
|<span data-ttu-id="f76bf-131">BizTalk Server 2013 R2</span><span class="sxs-lookup"><span data-stu-id="f76bf-131">BizTalk Server 2013 R2</span></span>|<span data-ttu-id="f76bf-132">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="f76bf-132">BizTalk Server 2013</span></span>|  
|<span data-ttu-id="f76bf-133">SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="f76bf-133">The SQL Server client libraries.</span></span> |<span data-ttu-id="f76bf-134">SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="f76bf-134">The SQL Server client libraries.</span></span> |  

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a><span data-ttu-id="f76bf-135">支援的 SQL Server 版本與用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="f76bf-135">Supported SQL Server versions and client libraries</span></span>  
 <span data-ttu-id="f76bf-136">下列章節提供支援的 SQL Server 版本與用戶端所需的程式庫[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-136">The following section presents the supported SQL Server versions and the client libraries required by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="f76bf-137">**支援的伺服器版本**: SQL Server 2005、 SQL Server 2008 SP1、 SQL Server 2008 R2、 SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="f76bf-137">**Supported server versions**: SQL Server 2005, SQL Server 2008 SP1, SQL Server 2008 R2, SQL Server 2012</span></span>  
  
-   <span data-ttu-id="f76bf-138">**支援的用戶端版本**: Microsoft[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]連接到 SQL Server 所需的用戶端 Dll 的組合。</span><span class="sxs-lookup"><span data-stu-id="f76bf-138">**Supported client versions**: Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] bundles the client DLLs required to connect to SQL Server.</span></span> <span data-ttu-id="f76bf-139">您不需要明確安裝在電腦上的任何用戶端 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-139">You do not need to explicitly install any client DLLs on your computer.</span></span>  
  
-   <span data-ttu-id="f76bf-140">**必要驅動程式**:</span><span class="sxs-lookup"><span data-stu-id="f76bf-140">**Required drivers**:</span></span>  
  
    -   <span data-ttu-id="f76bf-141">如果您使用 Udt 隨附於 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f76bf-141">If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server.</span></span> <span data-ttu-id="f76bf-142">例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業，這些 Dll 必須存在於執行 BizTalk Server 電腦上。</span><span class="sxs-lookup"><span data-stu-id="f76bf-142">For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.</span></span>  
  
        -   <span data-ttu-id="f76bf-143">請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="f76bf-143">Make sure Microsoft.SqlServer.Types.dll is added to the GAC.</span></span>  
  
        -   <span data-ttu-id="f76bf-144">請確定 SqlServerSpatial.dll System32 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f76bf-144">Make sure SqlServerSpatial.dll is available in the System32 folder.</span></span>  
  
         <span data-ttu-id="f76bf-145">您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，並選取**管理工具 – 基本**和**管理工具-完整**中**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="f76bf-145">You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.</span></span>  
  
    -   <span data-ttu-id="f76bf-146">如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定已安裝 SQL 用戶端連接性 SDK。</span><span class="sxs-lookup"><span data-stu-id="f76bf-146">If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="f76bf-147">您可以在執行 SQL Server 安裝程式並選取安裝 SQL 用戶端連接性 SDK **SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="f76bf-147">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="f76bf-148">配接器使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。</span><span class="sxs-lookup"><span data-stu-id="f76bf-148">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  
  
    -   <span data-ttu-id="f76bf-149">如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。</span><span class="sxs-lookup"><span data-stu-id="f76bf-149">If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.</span></span>  
  
<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a><span data-ttu-id="f76bf-150">64 位元支援</span><span class="sxs-lookup"><span data-stu-id="f76bf-150">64-bit support</span></span> 

<span data-ttu-id="f76bf-151">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以在 32 位元或 64 位元的主控件執行個體中執行。</span><span class="sxs-lookup"><span data-stu-id="f76bf-151">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can run in a 32-bit or 64-bit host instance.</span></span>

 <span data-ttu-id="f76bf-152">如需有關支援的安裝案例，32 位元和 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-152">For more information about the supported installation scenarios for the 32-bit and 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)],.</span></span> 
  
<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a><span data-ttu-id="f76bf-153">安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="f76bf-153">Install the SQL Adapter</span></span>  
 <span data-ttu-id="f76bf-154">請確定您已安裝之前安裝的必要條件[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-154">Make sure you have the prerequisites installed before installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="f76bf-155">您可以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="f76bf-155">You can install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="f76bf-156">**以互動模式**使用安裝精靈</span><span class="sxs-lookup"><span data-stu-id="f76bf-156">**In interactive mode** using the setup wizard</span></span>  
  
-   <span data-ttu-id="f76bf-157">**以無訊息模式**命令中使用 msiexec 連結</span><span class="sxs-lookup"><span data-stu-id="f76bf-157">**In silent mode** using msiexec in the command lin</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f76bf-158">您必須安裝在電腦上擁有系統管理權限[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，不論是否使用精靈或命令列安裝。</span><span class="sxs-lookup"><span data-stu-id="f76bf-158">You must have administrative privileges on the computer where you will install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], irrespective of whether you are installing by using the wizard or the command line.</span></span>  
  
<a name="BKMK_Install_Scenarios"></a>   
### <a name="32-bit-and-64-bit-install-scenarios"></a><span data-ttu-id="f76bf-159">32 位元和 64 位元安裝案例</span><span class="sxs-lookup"><span data-stu-id="f76bf-159">32-bit and 64-bit install scenarios</span></span>
 <span data-ttu-id="f76bf-160">與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於：</span><span class="sxs-lookup"><span data-stu-id="f76bf-160">With [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used for:</span></span>  
  
-   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="f76bf-161">設計階段 （當產生作業的中繼資料）。</span><span class="sxs-lookup"><span data-stu-id="f76bf-161"> design time (when generating metadata for operations).</span></span>  
  
-   <span data-ttu-id="f76bf-162">BizTalk Server 管理主控台 （用於建立實體連接埠） 的設計階段。</span><span class="sxs-lookup"><span data-stu-id="f76bf-162">BizTalk Server Administration console design time (for creating physical ports).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f76bf-163">BizTalk Server 管理主控台會以 32 位元 Microsoft Management Console (MMC) 應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="f76bf-163">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  
  
-   <span data-ttu-id="f76bf-164">BizTalk 執行階段 （傳送和接收訊息時從 LOB 應用程式）。</span><span class="sxs-lookup"><span data-stu-id="f76bf-164">BizTalk run time (when sending and receiving messages from LOB applications).</span></span>  
  
 <span data-ttu-id="f76bf-165">您可以安裝在同一部電腦或不同的電腦執行所有這些工作地方。</span><span class="sxs-lookup"><span data-stu-id="f76bf-165">You can have an installation where you perform all these tasks on the same computer or different computers.</span></span> <span data-ttu-id="f76bf-166">因為同時[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和 BizTalk MMC 是 32 位元處理程序，您必須安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]您要執行設計階段工作的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f76bf-166">Because both [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on the computer where you want to perform the design-time tasks.</span></span> <span data-ttu-id="f76bf-167">支援下列案例安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元和 64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="f76bf-167">The following scenarios are supported for installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on 32-bit and 64-bit platforms.</span></span>  
  
#### <a name="install-scenarios-on-a-32-bit-platform"></a><span data-ttu-id="f76bf-168">在 32 位元平台上安裝案例</span><span class="sxs-lookup"><span data-stu-id="f76bf-168">Install scenarios on a 32-bit platform</span></span>  
 <span data-ttu-id="f76bf-169">當安裝支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="f76bf-169">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 32-bit platform.</span></span>  
  
|<span data-ttu-id="f76bf-170">Visual Studio 設計階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-170">Visual Studio design time</span></span>|<span data-ttu-id="f76bf-171">BizTalk MMC 設計階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-171">BizTalk MMC design time</span></span>|<span data-ttu-id="f76bf-172">BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-172">BizTalk run time</span></span>|<span data-ttu-id="f76bf-173">Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-173">Visual Studio design time and/or  BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="f76bf-174">安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-174">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-175">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-175">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-176">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-176">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="f76bf-177">安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-177">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-178">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-178">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-179">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-179">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="f76bf-180">安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-180">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-181">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-181">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-182">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-182">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="f76bf-183">安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-183">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-184">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-184">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-185">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-185">- Install 32-bit client and other required DLLs.</span></span>|  
  
#### <a name="install-scenarios-on-a-64-bit-platform"></a><span data-ttu-id="f76bf-186">在 64 位元平台上安裝案例</span><span class="sxs-lookup"><span data-stu-id="f76bf-186">Install scenarios on a 64-bit platform</span></span>  
 <span data-ttu-id="f76bf-187">當安裝支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="f76bf-187">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 64-bit platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f76bf-188">在您要執行設計階段工作使用的任何電腦上[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-188">On any computer where you want to perform design-time tasks using either [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
|<span data-ttu-id="f76bf-189">Visual Studio 設計階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-189">Visual Studio design time</span></span>|<span data-ttu-id="f76bf-190">BizTalk MMC 設計階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-190">BizTalk MMC design time</span></span>|<span data-ttu-id="f76bf-191">BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-191">BizTalk run time</span></span>|<span data-ttu-id="f76bf-192">Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="f76bf-192">Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="f76bf-193">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-193">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-194">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-194">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-195">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-195">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="f76bf-196">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-196">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-197">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-197">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-198">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-198">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="f76bf-199">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="f76bf-199">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="f76bf-200">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-200">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-201">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-201">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-202">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-202">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="f76bf-203">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="f76bf-203">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="f76bf-204">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-204">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-205">安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-205">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-206">-安裝 64 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-206">- Install 64-bit client and other required DLLs.</span></span>|<span data-ttu-id="f76bf-207">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="f76bf-207">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="f76bf-208">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-208">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-209">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-209">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-210">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-210">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="f76bf-211">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="f76bf-211">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="f76bf-212">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-212">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-213">安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-213">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-214">-安裝 64 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-214">- Install 64-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="f76bf-215">安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-215">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="f76bf-216">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="f76bf-216">- Install 32-bit client and other required DLLs.</span></span>|  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-sql-adapter-in-interactive-mode"></a><span data-ttu-id="f76bf-217">在互動模式中安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="f76bf-217">Install the SQL Adapter in interactive mode</span></span>  
 
1.  <span data-ttu-id="f76bf-218">執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f76bf-218">Run the installer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f76bf-219">如果您要安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]上為虛擬機器，安裝精靈可能會繼續進行通知的安裝程式正在檢查可用磁碟空間的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f76bf-219">If you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space.</span></span> <span data-ttu-id="f76bf-220">在這種情況下，我們建議您使用無訊息安裝選項。</span><span class="sxs-lookup"><span data-stu-id="f76bf-220">In such cases, we recommend that you use the silent installation option.</span></span>   
  
2.  <span data-ttu-id="f76bf-221">閱讀 [歡迎] 畫面上的資訊，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-221">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="f76bf-222">閱讀並接受使用者授權合約 (EULA)，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-222">Read and accept the end-user license agreement (EULA), and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="f76bf-223">在**目的地資料夾**對話方塊方塊中，指定您要安裝的位置[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，按一下 **下一步**，然後按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-223">In the **Destination Folder** dialog box, specify the location where you want to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], click **Next**, and then click **Install**.</span></span>  
  
5.  <span data-ttu-id="f76bf-224">在**客戶經驗改進計畫**對話方塊方塊中，指定您想要註冊的客戶經驗改進計畫 (CEIP)。</span><span class="sxs-lookup"><span data-stu-id="f76bf-224">In the **Customer Experience Improvement Program** dialog box, specify whether you would like to enroll for the Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="f76bf-225">一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，將會與 Microsoft 共用的下列資料：</span><span class="sxs-lookup"><span data-stu-id="f76bf-225">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="f76bf-226">您要安裝的電腦硬體的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-226">Data related to the computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    -   <span data-ttu-id="f76bf-227">您用來連接使用的 SQL Server 版本的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-227">Data related to the SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="f76bf-228">指定您的選擇，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-228">Specify your choice and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f76bf-229">您可以隨時變更您的喜好設定有關在修復模式中執行安裝程式，從 控制台註冊 CEIP。</span><span class="sxs-lookup"><span data-stu-id="f76bf-229">You can always change your preference regarding enrolling for CEIP by running the Setup in Repair mode from the Control Panel.</span></span>  
  
6.  <span data-ttu-id="f76bf-230">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-230">Click **Finish**.</span></span>  
  
<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a><span data-ttu-id="f76bf-231">以無訊息模式安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="f76bf-231">Install the SQL adapter in Silent mode</span></span>  
 <span data-ttu-id="f76bf-232">下列程序示範如何執行的無訊息安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用`msiexec`命令。</span><span class="sxs-lookup"><span data-stu-id="f76bf-232">The following procedure demonstrates how to perform a silent installation of [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the `msiexec` command.</span></span>  
  
1.  <span data-ttu-id="f76bf-233">開啟命令提示字元並瀏覽至您用來讓安裝程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f76bf-233">Open a command prompt, and navigate to the folder where you have the installer.</span></span>  
  
2.  <span data-ttu-id="f76bf-234">執行下列命令以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f76bf-234">Run the following command to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f76bf-235">若要執行無訊息安裝在 x64 架構的平台，在下列命令，取代 SqlAdapterSetup64.msi 為 SqlAdapterSetup.msi。</span><span class="sxs-lookup"><span data-stu-id="f76bf-235">To perform silent installation on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn  
    ```  
  
     <span data-ttu-id="f76bf-236">您也可以選擇的 CEIP 註冊為無訊息安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="f76bf-236">You can also choose to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="f76bf-237">一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，將會與 Microsoft 共用的下列資料：</span><span class="sxs-lookup"><span data-stu-id="f76bf-237">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="f76bf-238">您要安裝的電腦硬體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-238">The computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    -   <span data-ttu-id="f76bf-239">您用來連接使用的 SQL Server 版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-239">The SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="f76bf-240">若要註冊 ceip，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="f76bf-240">To enroll for CEIP, run the following command:</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
    ```  
  
     <span data-ttu-id="f76bf-241">根據預設，此選項為 false。</span><span class="sxs-lookup"><span data-stu-id="f76bf-241">By default, the option is false.</span></span>  
  
     <span data-ttu-id="f76bf-242">如需有關`msiexec`命令中，輸入`msiexec`命令列，然後按上`ENTER`，或參閱[https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781)。</span><span class="sxs-lookup"><span data-stu-id="f76bf-242">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a><span data-ttu-id="f76bf-243">後續安裝工作</span><span class="sxs-lookup"><span data-stu-id="f76bf-243">Post-installation tasks</span></span>  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a><span data-ttu-id="f76bf-244">註冊繫結</span><span class="sxs-lookup"><span data-stu-id="f76bf-244">Register the Bindings</span></span>  
<span data-ttu-id="f76bf-245">完成這些步驟*只*如果安裝精靈無法註冊在 machine.config 檔案中的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="f76bf-245">Complete these steps *only* if the setup wizard fails to register the adapter bindings in the machine.config file.</span></span>  
  
1.  <span data-ttu-id="f76bf-246">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="f76bf-246">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="f76bf-247">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="f76bf-247">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    -   <span data-ttu-id="f76bf-248">Microsoft.NET framework 3.5 SP1、 \<*版本*\>是.NET framework 版本 v2.0.50727。</span><span class="sxs-lookup"><span data-stu-id="f76bf-248">For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="f76bf-249">Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。</span><span class="sxs-lookup"><span data-stu-id="f76bf-249">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="f76bf-250">開啟檔案，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="f76bf-250">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="f76bf-251">若要註冊配接器繫結：</span><span class="sxs-lookup"><span data-stu-id="f76bf-251">To register the adapter bindings:</span></span>  
  
    1.  <span data-ttu-id="f76bf-252">搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="f76bf-252">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="f76bf-253">搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="f76bf-253">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="f76bf-254">新增下列區段，"bindingElementExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="f76bf-254">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="f76bf-255">如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="f76bf-255">For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="f76bf-256">搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="f76bf-256">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="f76bf-257">新增下列區段，"bindingExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="f76bf-257">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="f76bf-258">如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="f76bf-258">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
      
  
4.  <span data-ttu-id="f76bf-259">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="f76bf-259">Save and close the machine.config file.</span></span>  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a><span data-ttu-id="f76bf-260">判斷公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="f76bf-260">Determining the Public Key and Version</span></span>  
<span data-ttu-id="f76bf-261">完成下列步驟來判斷公開金鑰和版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-261">Complete the following steps to determine the public key and version for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="f76bf-262">瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="f76bf-262">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="f76bf-263">以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-263">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="f76bf-264">下表列出的 Dll 名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-264">The following table lists the name of the DLLs for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    |<span data-ttu-id="f76bf-265">配接器</span><span class="sxs-lookup"><span data-stu-id="f76bf-265">Adapter</span></span>|<span data-ttu-id="f76bf-266">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="f76bf-266">Name of the DLL</span></span>|  
    |---|---|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|<span data-ttu-id="f76bf-267">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="f76bf-267">Microsoft.Adapters.Sql.dll</span></span>|  
  
3.  <span data-ttu-id="f76bf-268">在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f76bf-268">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="f76bf-269">同樣地，根據值**版本**標籤指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f76bf-269">Similarly, the value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="f76bf-270">複製的公開金鑰，然後按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-270">Copy the public key, and then click **Cancel**.</span></span>  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a><span data-ttu-id="f76bf-271">更新或變更 SQL 配接器安裝</span><span class="sxs-lookup"><span data-stu-id="f76bf-271">Update or change the SQL adapter installation</span></span>  
 <span data-ttu-id="f76bf-272">執行下列步驟來修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="f76bf-272">Perform the following steps to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span> <span data-ttu-id="f76bf-273">請確定您有[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝您執行安裝精靈來修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="f76bf-273">Make sure you have the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span>  
  
 <span data-ttu-id="f76bf-274">您可以修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式安裝：</span><span class="sxs-lookup"><span data-stu-id="f76bf-274">You can modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the following two ways:</span></span>  
  
-   <span data-ttu-id="f76bf-275">**以互動模式**執行安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="f76bf-275">**In interactive mode** by running the setup wizard.</span></span>  
  
-   <span data-ttu-id="f76bf-276">**以無訊息模式**使用命令列。</span><span class="sxs-lookup"><span data-stu-id="f76bf-276">**In silent mode** by using the command line.</span></span>  
  
#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a><span data-ttu-id="f76bf-277">更新 SQL 配接器安裝在互動模式中</span><span class="sxs-lookup"><span data-stu-id="f76bf-277">Update the SQL Adapter installation in interactive mode</span></span>  
  
1.  <span data-ttu-id="f76bf-278">按一下**啟動**，然後按一下 **控制台**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-278">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="f76bf-279">在控制台中，按兩下**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-279">In Control Panel, double-click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="f76bf-280">在**程式和功能**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下 **變更**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-280">In the **Programs and Features** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Change**.</span></span>  
  
4.  <span data-ttu-id="f76bf-281">閱讀 [歡迎] 畫面上的資訊，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-281">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="f76bf-282">在**變更、 修復或移除安裝**對話方塊中，按一下 **修復**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-282">In the **Change, repair, or remove installation** dialog box, click **Repair**.</span></span>  
  
6.  <span data-ttu-id="f76bf-283">在**準備好修復 Microsoft BizTalk Adapter for SQL Server**對話方塊中，按一下 **修復**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-283">In the **Ready to repair Microsoft BizTalk Adapter for SQL Server** dialog box, click **Repair**.</span></span>  
  
7.  <span data-ttu-id="f76bf-284">若有需要，變更您的喜好設定有關選擇加入 ceip，，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-284">If required, change your preferences regarding opting for CEIP, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f76bf-285">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-285">Click **Finish**.</span></span>  
  
#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a><span data-ttu-id="f76bf-286">SQL 配接器安裝，以無訊息模式更新</span><span class="sxs-lookup"><span data-stu-id="f76bf-286">Update the SQL Adapter installation in silent mode</span></span>  
  
1.  <span data-ttu-id="f76bf-287">開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f76bf-287">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="f76bf-288">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="f76bf-288">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f76bf-289">若要修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]x64 平台上，下列命令，在無訊息模式中的安裝取代 SqlAdapterSetup64.msi SqlAdapterSetup.msi。</span><span class="sxs-lookup"><span data-stu-id="f76bf-289">To modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn /f  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f76bf-290">修改時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇加入或退出 CEIP。</span><span class="sxs-lookup"><span data-stu-id="f76bf-290">While modifying the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="f76bf-291">喜好設定會維持您指定在安裝時，即使您明確地設定 CEIP_OPTIN 為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="f76bf-291">The preferences will remain the same as you specified during the installation, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  
  
     <span data-ttu-id="f76bf-292">如需有關`msiexec`命令中，輸入`msiexec`命令列，然後按上`ENTER`，或參閱[https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781)。</span><span class="sxs-lookup"><span data-stu-id="f76bf-292">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>   
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a><span data-ttu-id="f76bf-293">解除安裝或移除 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="f76bf-293">Uninstall or remove the SQL Adapter</span></span>  
 <span data-ttu-id="f76bf-294">執行下列步驟來移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="f76bf-294">Perform the following steps to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from your computer.</span></span> <span data-ttu-id="f76bf-295">請確定您有[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝在執行安裝程式精靈，以移除之前[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-295">Make sure you have the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="f76bf-296">您可以移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="f76bf-296">You can remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="f76bf-297">**以互動模式**執行安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="f76bf-297">**In interactive mode** by running the setup wizard.</span></span>  
  
-   <span data-ttu-id="f76bf-298">**以無訊息模式**使用命令列。</span><span class="sxs-lookup"><span data-stu-id="f76bf-298">**In silent mode** by using the command line.</span></span>  
  
#### <a name="uninstall-in-interactive-mode"></a><span data-ttu-id="f76bf-299">在互動模式中解除安裝</span><span class="sxs-lookup"><span data-stu-id="f76bf-299">Uninstall in interactive mode</span></span>  
  
1.  <span data-ttu-id="f76bf-300">按一下**啟動**，然後按一下 **控制台**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-300">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="f76bf-301">在控制台中，按兩下**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-301">In Control Panel, double-click  **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="f76bf-302">在**新增或移除程式**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下 **移除**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-302">In the **Add or Remove Programs** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Remove**.</span></span>  
  
4.  <span data-ttu-id="f76bf-303">在對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="f76bf-303">In the dialog box, click **Yes**.</span></span>  
  
#### <a name="uninstall-in-silent-mode"></a><span data-ttu-id="f76bf-304">在無訊息模式中解除安裝</span><span class="sxs-lookup"><span data-stu-id="f76bf-304">Uninstall in silent mode</span></span>  
  
1.  <span data-ttu-id="f76bf-305">開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f76bf-305">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="f76bf-306">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="f76bf-306">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f76bf-307">若要移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在 x64 平台上，下列命令，在無訊息模式取代 SqlAdapterSetup.msi SqlAdapterSetup64.msi。</span><span class="sxs-lookup"><span data-stu-id="f76bf-307">To remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /x SqlAdapterSetup.msi /qn  
    ```  
  
     <span data-ttu-id="f76bf-308">此命令會移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從電腦。</span><span class="sxs-lookup"><span data-stu-id="f76bf-308">This command removes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from the computer.</span></span>  
  
     <span data-ttu-id="f76bf-309">如需有關`msiexec`命令中，輸入`msiexec`命令列，然後按上`ENTER`，或參閱[https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781)。</span><span class="sxs-lookup"><span data-stu-id="f76bf-309">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a><span data-ttu-id="f76bf-310">解除安裝後工作</span><span class="sxs-lookup"><span data-stu-id="f76bf-310">Post-uninstall task</span></span>  
 <span data-ttu-id="f76bf-311">如果[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式無法移除配接器繫結同時移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須手動移除它們。</span><span class="sxs-lookup"><span data-stu-id="f76bf-311">If the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] setup fails to remove the adapter bindings while removing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must remove them manually.</span></span> <span data-ttu-id="f76bf-312">下列章節描述如何手動移除的繫結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f76bf-312">The following section describes how to manually remove the bindings for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
<a name="BKMK_Remove_Binding"></a>   
#### <a name="manually-remove-the-bindings"></a><span data-ttu-id="f76bf-313">手動移除繫結</span><span class="sxs-lookup"><span data-stu-id="f76bf-313">Manually remove the bindings</span></span>  
 <span data-ttu-id="f76bf-314">執行這些步驟*只*如果安裝精靈無法移除 machine.config 檔案中的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="f76bf-314">Perform these steps *only* if the setup wizard fails to remove the adapter bindings from the machine.config file.</span></span>  
  
1.  <span data-ttu-id="f76bf-315">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="f76bf-315">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="f76bf-316">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="f76bf-316">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    -   <span data-ttu-id="f76bf-317">Microsoft.NET framework 3.5 SP1、 \<*版本*\>是.NET framework 版本 v2.0.50727。</span><span class="sxs-lookup"><span data-stu-id="f76bf-317">For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="f76bf-318">Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。</span><span class="sxs-lookup"><span data-stu-id="f76bf-318">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="f76bf-319">開啟檔案，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="f76bf-319">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="f76bf-320">若要移除介面卡繫結註冊：</span><span class="sxs-lookup"><span data-stu-id="f76bf-320">To remove the adapter binding registration:</span></span>  
  
    1.  <span data-ttu-id="f76bf-321">搜尋 「 system.serviceModel 的項目，並移除下列項目底下：</span><span class="sxs-lookup"><span data-stu-id="f76bf-321">Search for the element "system.serviceModel" and remove the following from under the element:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  <span data-ttu-id="f76bf-322">搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="f76bf-322">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="f76bf-323">移除 「 bindingElementExtensions 」 節點下的下一節。</span><span class="sxs-lookup"><span data-stu-id="f76bf-323">Remove the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="f76bf-324">如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="f76bf-324">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="f76bf-325">搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="f76bf-325">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="f76bf-326">移除 「 bindingExtensions 」 節點下的下一節。</span><span class="sxs-lookup"><span data-stu-id="f76bf-326">Remove the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="f76bf-327">如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="f76bf-327">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  <span data-ttu-id="f76bf-328">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="f76bf-328">Save and close the machine.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76bf-329">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f76bf-329">See also</span></span>
[<span data-ttu-id="f76bf-330">安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="f76bf-330">Install the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[<span data-ttu-id="f76bf-331">了解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="f76bf-331">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)