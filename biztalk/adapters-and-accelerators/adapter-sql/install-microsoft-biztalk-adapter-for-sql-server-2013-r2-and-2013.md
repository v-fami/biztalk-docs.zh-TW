---
title: 安裝 Microsoft BizTalk Adapter for SQL Server-2013 R2 和 2013年 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56c31d0d-783b-41ee-8265-56c9547e9dca
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f248e1db8bc57e928e85e908e679d4ded1ec38aa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969639"
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2013-r2-and-2013"></a><span data-ttu-id="4caa7-102">安裝 Microsoft BizTalk Adapter for SQL Server-2013 R2 和 2013</span><span class="sxs-lookup"><span data-stu-id="4caa7-102">Install Microsoft BizTalk Adapter for SQL Server - 2013 R2 and 2013</span></span>
<span data-ttu-id="4caa7-103">安裝[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]隨附[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]，或隨附[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]2013年。</span><span class="sxs-lookup"><span data-stu-id="4caa7-103">Install the [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] included with [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)], or included with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 2013.</span></span>

 <span data-ttu-id="4caa7-104">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於：</span><span class="sxs-lookup"><span data-stu-id="4caa7-104">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used with:</span></span>  

- <span data-ttu-id="4caa7-105">.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="4caa7-105">A .NET application</span></span>  

- <span data-ttu-id="4caa7-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4caa7-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span></span>  

  <span data-ttu-id="4caa7-107">根據您如何使用介面卡，所需的軟體而異。</span><span class="sxs-lookup"><span data-stu-id="4caa7-107">Based on how you use the adapters, the required software varies.</span></span>  

<a name="BKMK_Prereqs_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a><span data-ttu-id="4caa7-108">使用.NET 應用程式中的配接器時的必要條件</span><span class="sxs-lookup"><span data-stu-id="4caa7-108">Prerequisites when using the adapter with a .NET Application</span></span>  
<span data-ttu-id="4caa7-109">您要在其中撰寫取用的.NET 應用程式的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-109">Install the following software on the computer where you are writing .NET applications that consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="4caa7-110">所列，請在順序中安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="4caa7-110">Install the software in the order as listed.</span></span>  


|                                 <span data-ttu-id="4caa7-111">2013 R2</span><span class="sxs-lookup"><span data-stu-id="4caa7-111">2013 R2</span></span>                                 |                                  <span data-ttu-id="4caa7-112">2013</span><span class="sxs-lookup"><span data-stu-id="4caa7-112">2013</span></span>                                   |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------|
|          [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]          |      <span data-ttu-id="4caa7-113">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4caa7-113">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span></span>      |
|                           <span data-ttu-id="4caa7-114">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="4caa7-114">Visual Studio 2013</span></span>                            |                           <span data-ttu-id="4caa7-115">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="4caa7-115">Visual Studio 2012</span></span>                            |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] |
|                   <span data-ttu-id="4caa7-116">SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="4caa7-116">The SQL Server client libraries.</span></span> <span data-ttu-id="4caa7-117">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="4caa7-117">.</span></span>                    |                    <span data-ttu-id="4caa7-118">SQL Server 用戶端程式庫...</span><span class="sxs-lookup"><span data-stu-id="4caa7-118">The SQL Server client libraries..</span></span>                    |

<a name="BKMK_Prereqs_BTS"></a>    
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a><span data-ttu-id="4caa7-119">使用 BizTalk Server 中的配接器時的必要條件</span><span class="sxs-lookup"><span data-stu-id="4caa7-119">Prerequisites when using the adapter with BizTalk Server</span></span>  
<span data-ttu-id="4caa7-120">會使用您的電腦上安裝下列軟體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-120">Install the following software on the computer where you will be using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="4caa7-121">我們建議您安裝軟體的相同順序，如此處所列。</span><span class="sxs-lookup"><span data-stu-id="4caa7-121">We recommend installing the software in the same order as listed here.</span></span>  


|                                                                                                                                                                                                                                                               <span data-ttu-id="4caa7-122">2013 R2</span><span class="sxs-lookup"><span data-stu-id="4caa7-122">2013 R2</span></span>                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                <span data-ttu-id="4caa7-123">2013</span><span class="sxs-lookup"><span data-stu-id="4caa7-123">2013</span></span>                                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                                                                                        [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                    <span data-ttu-id="4caa7-124">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4caa7-124">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span></span>                                                                                                                                                                                                                                    |
|                                                                                                                                                                                                                                                         <span data-ttu-id="4caa7-125">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="4caa7-125">Visual Studio 2013</span></span>                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                         <span data-ttu-id="4caa7-126">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="4caa7-126">Visual Studio 2012</span></span>                                                                                                                                                                                                                                                          |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="4caa7-127">安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]for[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-127">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="4caa7-128">若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-128">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="4caa7-129">安裝[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]for[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-129">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="4caa7-130">若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-130">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> |
|                                                                                                                                                                                                                                                       <span data-ttu-id="4caa7-131">BizTalk Server 2013 R2</span><span class="sxs-lookup"><span data-stu-id="4caa7-131">BizTalk Server 2013 R2</span></span>                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                         <span data-ttu-id="4caa7-132">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="4caa7-132">BizTalk Server 2013</span></span>                                                                                                                                                                                                                                                         |
|                                                                                                                                                                                                                                                  <span data-ttu-id="4caa7-133">SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="4caa7-133">The SQL Server client libraries.</span></span>                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                  <span data-ttu-id="4caa7-134">SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="4caa7-134">The SQL Server client libraries.</span></span>                                                                                                                                                                                                                                                   |

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a><span data-ttu-id="4caa7-135">支援的 SQL Server 版本和用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="4caa7-135">Supported SQL Server versions and client libraries</span></span>  
 <span data-ttu-id="4caa7-136">下列章節提供支援的 SQL Server 版本和用戶端所需的程式庫[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-136">The following section presents the supported SQL Server versions and the client libraries required by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

- <span data-ttu-id="4caa7-137">**支援的伺服器版本**: SQL Server 2005，SQL Server 2008 SP1 中，SQL Server 2008 R2，SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="4caa7-137">**Supported server versions**: SQL Server 2005, SQL Server 2008 SP1, SQL Server 2008 R2, SQL Server 2012</span></span>  

- <span data-ttu-id="4caa7-138">**支援的用戶端版本**: Microsoft[!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]連接到 SQL Server 所需的用戶端 Dll 的套件組合。</span><span class="sxs-lookup"><span data-stu-id="4caa7-138">**Supported client versions**: Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] bundles the client DLLs required to connect to SQL Server.</span></span> <span data-ttu-id="4caa7-139">您不需要明確地在您的電腦上安裝任何用戶端 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-139">You do not need to explicitly install any client DLLs on your computer.</span></span>  

- <span data-ttu-id="4caa7-140">**必要驅動程式**:</span><span class="sxs-lookup"><span data-stu-id="4caa7-140">**Required drivers**:</span></span>  

  - <span data-ttu-id="4caa7-141">如果您使用的 Udt 隨附的 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4caa7-141">If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server.</span></span> <span data-ttu-id="4caa7-142">例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業時，這些 Dll 必須存在於執行 BizTalk Server 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4caa7-142">For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.</span></span>  

    - <span data-ttu-id="4caa7-143">請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="4caa7-143">Make sure Microsoft.SqlServer.Types.dll is added to the GAC.</span></span>  

    - <span data-ttu-id="4caa7-144">請確定 SqlServerSpatial.dll 位於 System32 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4caa7-144">Make sure SqlServerSpatial.dll is available in the System32 folder.</span></span>  

      <span data-ttu-id="4caa7-145">您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，然後選取**管理工具-基本**並**管理工具-完整**在**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="4caa7-145">You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.</span></span>  

  - <span data-ttu-id="4caa7-146">如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定您已安裝的 SQL 用戶端連接性 SDK。</span><span class="sxs-lookup"><span data-stu-id="4caa7-146">If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="4caa7-147">您可以安裝 SQL 用戶端連接性 SDK，以執行 SQL Server 安裝程式，然後選取**SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="4caa7-147">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="4caa7-148">配接器會使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。</span><span class="sxs-lookup"><span data-stu-id="4caa7-148">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  

  - <span data-ttu-id="4caa7-149">如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。</span><span class="sxs-lookup"><span data-stu-id="4caa7-149">If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.</span></span>  

<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a><span data-ttu-id="4caa7-150">64 位元支援</span><span class="sxs-lookup"><span data-stu-id="4caa7-150">64-bit support</span></span> 

<span data-ttu-id="4caa7-151">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以在 32 位元或 64 位元的主控件執行個體中執行。</span><span class="sxs-lookup"><span data-stu-id="4caa7-151">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can run in a 32-bit or 64-bit host instance.</span></span>

 <span data-ttu-id="4caa7-152">如需有關支援的安裝案例，32 位元和 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-152">For more information about the supported installation scenarios for the 32-bit and 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)],.</span></span> 

<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a><span data-ttu-id="4caa7-153">安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="4caa7-153">Install the SQL Adapter</span></span>  
 <span data-ttu-id="4caa7-154">請確定您已安裝，才能安裝的必要條件[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-154">Make sure you have the prerequisites installed before installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

 <span data-ttu-id="4caa7-155">您可以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="4caa7-155">You can install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  

- <span data-ttu-id="4caa7-156">**在互動模式中**使用安裝精靈</span><span class="sxs-lookup"><span data-stu-id="4caa7-156">**In interactive mode** using the setup wizard</span></span>  

- <span data-ttu-id="4caa7-157">**以無訊息模式**命令中使用 msiexec 連結</span><span class="sxs-lookup"><span data-stu-id="4caa7-157">**In silent mode** using msiexec in the command lin</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="4caa7-158">您必須安裝在電腦上擁有系統管理權限[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，不論您要安裝使用精靈或命令列。</span><span class="sxs-lookup"><span data-stu-id="4caa7-158">You must have administrative privileges on the computer where you will install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], irrespective of whether you are installing by using the wizard or the command line.</span></span>  

<a name="BKMK_Install_Scenarios"></a>   
### <a name="32-bit-and-64-bit-install-scenarios"></a><span data-ttu-id="4caa7-159">32 位元和 64 位元安裝案例</span><span class="sxs-lookup"><span data-stu-id="4caa7-159">32-bit and 64-bit install scenarios</span></span>
 <span data-ttu-id="4caa7-160">具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]適用於：</span><span class="sxs-lookup"><span data-stu-id="4caa7-160">With [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used for:</span></span>  

- [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="4caa7-161"> 設計階段 （當產生作業的中繼資料）。</span><span class="sxs-lookup"><span data-stu-id="4caa7-161"> design time (when generating metadata for operations).</span></span>  

- <span data-ttu-id="4caa7-162">BizTalk Server 管理主控台 （用於建立實體連接埠） 的設計階段。</span><span class="sxs-lookup"><span data-stu-id="4caa7-162">BizTalk Server Administration console design time (for creating physical ports).</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="4caa7-163">BizTalk Server 管理主控台會以 32 位元的 Microsoft Management Console (MMC) 應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="4caa7-163">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  

- <span data-ttu-id="4caa7-164">BizTalk 執行階段 （當傳送和接收來自 LOB 應用程式的訊息）。</span><span class="sxs-lookup"><span data-stu-id="4caa7-164">BizTalk run time (when sending and receiving messages from LOB applications).</span></span>  

  <span data-ttu-id="4caa7-165">您可以安裝在同一部電腦或不同的電腦執行所有這些工作地方。</span><span class="sxs-lookup"><span data-stu-id="4caa7-165">You can have an installation where you perform all these tasks on the same computer or different computers.</span></span> <span data-ttu-id="4caa7-166">因為這兩[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]BizTalk MMC 和 32 位元處理序，您必須安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]您要執行設計階段工作的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4caa7-166">Because both [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on the computer where you want to perform the design-time tasks.</span></span> <span data-ttu-id="4caa7-167">安裝支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元和 64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="4caa7-167">The following scenarios are supported for installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on 32-bit and 64-bit platforms.</span></span>  

#### <a name="install-scenarios-on-a-32-bit-platform"></a><span data-ttu-id="4caa7-168">在 32 位元平台上安裝案例</span><span class="sxs-lookup"><span data-stu-id="4caa7-168">Install scenarios on a 32-bit platform</span></span>  
 <span data-ttu-id="4caa7-169">安裝時支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]32 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="4caa7-169">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 32-bit platform.</span></span>  


|                                                                                                               <span data-ttu-id="4caa7-170">Visual Studio 設計階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-170">Visual Studio design time</span></span>                                                                                                                |                                                                                                                <span data-ttu-id="4caa7-171">BizTalk MMC 設計階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-171">BizTalk MMC design time</span></span>                                                                                                                 |                                                                                                                    <span data-ttu-id="4caa7-172">BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-172">BizTalk run time</span></span>                                                                                                                    |                                                                                      <span data-ttu-id="4caa7-173">Visual Studio 設計階段及/或 BizTalk MMC 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-173">Visual Studio design time and/or  BizTalk MMC design time + BizTalk run time</span></span>                                                                                      |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4caa7-174">-安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-174">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-175">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-175">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-176">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-176">- Install 32-bit client and other required DLLs.</span></span> | <span data-ttu-id="4caa7-177">-安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-177">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-178">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-178">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-179">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-179">- Install 32-bit client and other required DLLs.</span></span> | <span data-ttu-id="4caa7-180">-安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-180">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-181">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-181">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-182">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-182">- Install 32-bit client and other required DLLs.</span></span> | <span data-ttu-id="4caa7-183">-安裝 32 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-183">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-184">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-184">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-185">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-185">- Install 32-bit client and other required DLLs.</span></span> |

#### <a name="install-scenarios-on-a-64-bit-platform"></a><span data-ttu-id="4caa7-186">在 64 位元平台上安裝案例</span><span class="sxs-lookup"><span data-stu-id="4caa7-186">Install scenarios on a 64-bit platform</span></span>  
 <span data-ttu-id="4caa7-187">安裝時支援下列案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="4caa7-187">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 64-bit platform.</span></span>  

> [!NOTE]
>  <span data-ttu-id="4caa7-188">在您要執行設計階段工作使用的任何電腦上[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-188">On any computer where you want to perform design-time tasks using either [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

|                                                                                                               <span data-ttu-id="4caa7-189">Visual Studio 設計階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-189">Visual Studio design time</span></span>                                                                                                                |                                                                                                                <span data-ttu-id="4caa7-190">BizTalk MMC 設計階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-190">BizTalk MMC design time</span></span>                                                                                                                 |                                                                                                                                                                                                                                                                                                   <span data-ttu-id="4caa7-191">BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-191">BizTalk run time</span></span>                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                    <span data-ttu-id="4caa7-192">Visual Studio 設計階段及/或 BizTalk MMC 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="4caa7-192">Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>                                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4caa7-193">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-193">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-194">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-194">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-195">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-195">- Install 32-bit client and other required DLLs.</span></span> | <span data-ttu-id="4caa7-196">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-196">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-197">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-197">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-198">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-198">- Install 32-bit client and other required DLLs.</span></span> | <span data-ttu-id="4caa7-199">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="4caa7-199">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="4caa7-200">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-200">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-201">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-201">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-202">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-202">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="4caa7-203">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="4caa7-203">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="4caa7-204">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-204">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-205">安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-205">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-206">-安裝 64 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-206">- Install 64-bit client and other required DLLs.</span></span> | <span data-ttu-id="4caa7-207">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="4caa7-207">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="4caa7-208">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-208">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-209">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-209">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-210">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-210">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="4caa7-211">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="4caa7-211">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="4caa7-212">安裝 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-212">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-213">安裝 64 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-213">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-214">-安裝 64 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-214">- Install 64-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="4caa7-215">-安裝 32 位元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-215">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="4caa7-216">-安裝 32 位元用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="4caa7-216">- Install 32-bit client and other required DLLs.</span></span> |

<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-sql-adapter-in-interactive-mode"></a><span data-ttu-id="4caa7-217">在互動模式中安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="4caa7-217">Install the SQL Adapter in interactive mode</span></span>  

1. <span data-ttu-id="4caa7-218">執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="4caa7-218">Run the installer.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="4caa7-219">如果您要安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]虛擬機器上，安裝精靈可能會繼續進行對話方塊，通知的安裝程式正在檢查可用磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="4caa7-219">If you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space.</span></span> <span data-ttu-id="4caa7-220">在此情況下，我們建議您使用無訊息安裝選項。</span><span class="sxs-lookup"><span data-stu-id="4caa7-220">In such cases, we recommend that you use the silent installation option.</span></span>   

2. <span data-ttu-id="4caa7-221">閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-221">Read the information on the Welcome screen, and then click **Next**.</span></span>  

3. <span data-ttu-id="4caa7-222">閱讀並接受使用者授權合約 (EULA)，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-222">Read and accept the end-user license agreement (EULA), and then click **Next**.</span></span>  

4. <span data-ttu-id="4caa7-223">在 **目的地資料夾**對話方塊方塊中，指定您要安裝的位置[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，按一下**下一步]**，然後按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-223">In the **Destination Folder** dialog box, specify the location where you want to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], click **Next**, and then click **Install**.</span></span>  

5. <span data-ttu-id="4caa7-224">在 **客戶經驗改進計畫**對話方塊方塊中，指定您想要註冊的客戶經驗改進計畫 (CEIP)。</span><span class="sxs-lookup"><span data-stu-id="4caa7-224">In the **Customer Experience Improvement Program** dialog box, specify whether you would like to enroll for the Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="4caa7-225">一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您會將分享 Microsoft 中的下列資料：</span><span class="sxs-lookup"><span data-stu-id="4caa7-225">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  

   - <span data-ttu-id="4caa7-226">您安裝所在的電腦硬體的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-226">Data related to the computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

   - <span data-ttu-id="4caa7-227">您用來連接使用的 SQL Server 版本的相關資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-227">Data related to the SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

     <span data-ttu-id="4caa7-228">指定您選擇，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-228">Specify your choice and click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="4caa7-229">您可以隨時變更您的喜好設定有關在修復模式下執行安裝程式，從 控制台註冊 ceip。</span><span class="sxs-lookup"><span data-stu-id="4caa7-229">You can always change your preference regarding enrolling for CEIP by running the Setup in Repair mode from the Control Panel.</span></span>  

6. <span data-ttu-id="4caa7-230">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-230">Click **Finish**.</span></span>  

<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a><span data-ttu-id="4caa7-231">以無訊息模式安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="4caa7-231">Install the SQL adapter in Silent mode</span></span>  
 <span data-ttu-id="4caa7-232">下列程序示範如何執行無訊息安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用`msiexec`命令。</span><span class="sxs-lookup"><span data-stu-id="4caa7-232">The following procedure demonstrates how to perform a silent installation of [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the `msiexec` command.</span></span>  

1. <span data-ttu-id="4caa7-233">開啟命令提示字元並瀏覽至您已安裝程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4caa7-233">Open a command prompt, and navigate to the folder where you have the installer.</span></span>  

2. <span data-ttu-id="4caa7-234">執行下列命令以安裝[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="4caa7-234">Run the following command to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="4caa7-235">若要執行無訊息安裝在 x64 架構的平台，在下列命令中，取代 SqlAdapterSetup64.msi SqlAdapterSetup.msi。</span><span class="sxs-lookup"><span data-stu-id="4caa7-235">To perform silent installation on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn  
   ```  

    <span data-ttu-id="4caa7-236">您也可以選擇加入 ceip 的無訊息安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="4caa7-236">You can also choose to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="4caa7-237">一部分的 CEIP [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您會將分享 Microsoft 中的下列資料：</span><span class="sxs-lookup"><span data-stu-id="4caa7-237">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  

   - <span data-ttu-id="4caa7-238">您安裝所在的電腦硬體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-238">The computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

   - <span data-ttu-id="4caa7-239">您用來連接使用的 SQL Server 版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-239">The SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

     <span data-ttu-id="4caa7-240">若要註冊 ceip，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="4caa7-240">To enroll for CEIP, run the following command:</span></span>  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
   ```  

    <span data-ttu-id="4caa7-241">根據預設，此選項為 false。</span><span class="sxs-lookup"><span data-stu-id="4caa7-241">By default, the option is false.</span></span>  

    <span data-ttu-id="4caa7-242">如需詳細資訊`msiexec`命令中，輸入`msiexec`上的命令列和按下`ENTER`，或參閱[ https://support.microsoft.com/kb/230781 ](https://support.microsoft.com/kb/230781)。</span><span class="sxs-lookup"><span data-stu-id="4caa7-242">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  

<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a><span data-ttu-id="4caa7-243">後續安裝工作</span><span class="sxs-lookup"><span data-stu-id="4caa7-243">Post-installation tasks</span></span>  

<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a><span data-ttu-id="4caa7-244">註冊繫結</span><span class="sxs-lookup"><span data-stu-id="4caa7-244">Register the Bindings</span></span>  
<span data-ttu-id="4caa7-245">完成這些步驟*只*如果 machine.config 檔案中註冊的配接器繫結失敗的安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="4caa7-245">Complete these steps *only* if the setup wizard fails to register the adapter bindings in the machine.config file.</span></span>  

1. <span data-ttu-id="4caa7-246">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4caa7-246">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="4caa7-247">例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="4caa7-247">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  

   - <span data-ttu-id="4caa7-248">Microsoft.NET framework 3.5 SP1 \<*版本*\>是.NET framework 版本 v2.0.50727。</span><span class="sxs-lookup"><span data-stu-id="4caa7-248">For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.</span></span>  

   - <span data-ttu-id="4caa7-249">Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。</span><span class="sxs-lookup"><span data-stu-id="4caa7-249">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.</span></span>  

2. <span data-ttu-id="4caa7-250">開啟使用文字編輯器的檔案。</span><span class="sxs-lookup"><span data-stu-id="4caa7-250">Open the file using a text editor.</span></span>  

3. <span data-ttu-id="4caa7-251">若要註冊配接器繫結：</span><span class="sxs-lookup"><span data-stu-id="4caa7-251">To register the adapter bindings:</span></span>  

   1. <span data-ttu-id="4caa7-252">搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="4caa7-252">Search for the element "system.serviceModel" and add the following under it:</span></span>  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
      ```  

   2. <span data-ttu-id="4caa7-253">搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="4caa7-253">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  

   3. <span data-ttu-id="4caa7-254">新增"bindingElementExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="4caa7-254">Add the following section under the "bindingElementExtensions" node.</span></span>  

       <span data-ttu-id="4caa7-255">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="4caa7-255">For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. <span data-ttu-id="4caa7-256">搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="4caa7-256">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  

   5. <span data-ttu-id="4caa7-257">新增"bindingExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="4caa7-257">Add the following section under the "bindingExtensions" node.</span></span>  

       <span data-ttu-id="4caa7-258">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="4caa7-258">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  



4. <span data-ttu-id="4caa7-259">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4caa7-259">Save and close the machine.config file.</span></span>  

<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a><span data-ttu-id="4caa7-260">判斷的公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="4caa7-260">Determining the Public Key and Version</span></span>  
<span data-ttu-id="4caa7-261">完成下列步驟來判斷的公開金鑰和版本[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-261">Complete the following steps to determine the public key and version for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

1. <span data-ttu-id="4caa7-262">瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="4caa7-262">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  

2. <span data-ttu-id="4caa7-263">以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-263">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="4caa7-264">下表列出的 Dll 名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-264">The following table lists the name of the DLLs for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  


   |                              <span data-ttu-id="4caa7-265">配接器</span><span class="sxs-lookup"><span data-stu-id="4caa7-265">Adapter</span></span>                              |      <span data-ttu-id="4caa7-266">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="4caa7-266">Name of the DLL</span></span>       |
   |-------------------------------------------------------------------|----------------------------|
   | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] | <span data-ttu-id="4caa7-267">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="4caa7-267">Microsoft.Adapters.Sql.dll</span></span> |


3. <span data-ttu-id="4caa7-268">在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4caa7-268">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="4caa7-269">同樣地，根據的值才**版本**標籤都會指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4caa7-269">Similarly, the value against the **Version** label specifies the version number for the DLL.</span></span>  

4. <span data-ttu-id="4caa7-270">複製公開金鑰，然後再按**取消**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-270">Copy the public key, and then click **Cancel**.</span></span>  

<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a><span data-ttu-id="4caa7-271">更新或變更 SQL 配接器安裝</span><span class="sxs-lookup"><span data-stu-id="4caa7-271">Update or change the SQL adapter installation</span></span>  
 <span data-ttu-id="4caa7-272">執行下列步驟，以修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="4caa7-272">Perform the following steps to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span> <span data-ttu-id="4caa7-273">請確定您已[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝在執行安裝精靈來修改之前[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="4caa7-273">Make sure you have the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span>  

 <span data-ttu-id="4caa7-274">您可以修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式安裝：</span><span class="sxs-lookup"><span data-stu-id="4caa7-274">You can modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the following two ways:</span></span>  

-   <span data-ttu-id="4caa7-275">**在互動模式中**執行安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="4caa7-275">**In interactive mode** by running the setup wizard.</span></span>  

-   <span data-ttu-id="4caa7-276">**以無訊息模式**使用命令列。</span><span class="sxs-lookup"><span data-stu-id="4caa7-276">**In silent mode** by using the command line.</span></span>  

#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a><span data-ttu-id="4caa7-277">更新 SQL 配接器安裝在互動模式中</span><span class="sxs-lookup"><span data-stu-id="4caa7-277">Update the SQL Adapter installation in interactive mode</span></span>  

1.  <span data-ttu-id="4caa7-278">按一下 **開始**，然後按一下**控制台**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-278">Click **Start**, and then click **Control Panel**.</span></span>  

2.  <span data-ttu-id="4caa7-279">在控制台中，按兩下**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-279">In Control Panel, double-click **Programs and Features**.</span></span>  

3.  <span data-ttu-id="4caa7-280">在 **程式和功能**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下**變更**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-280">In the **Programs and Features** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Change**.</span></span>  

4.  <span data-ttu-id="4caa7-281">閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-281">Read the information on the Welcome screen, and then click **Next**.</span></span>  

5.  <span data-ttu-id="4caa7-282">在 [**變更、 修復或移除安裝**] 對話方塊中，按一下**修復**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-282">In the **Change, repair, or remove installation** dialog box, click **Repair**.</span></span>  

6.  <span data-ttu-id="4caa7-283">在 [**準備好修復 Microsoft BizTalk Adapter for SQL Server** ] 對話方塊中，按一下**修復**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-283">In the **Ready to repair Microsoft BizTalk Adapter for SQL Server** dialog box, click **Repair**.</span></span>  

7.  <span data-ttu-id="4caa7-284">如有需要，變更您的喜好設定有關選擇加入 ceip，，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-284">If required, change your preferences regarding opting for CEIP, and then click **OK**.</span></span>  

8.  <span data-ttu-id="4caa7-285">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-285">Click **Finish**.</span></span>  

#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a><span data-ttu-id="4caa7-286">SQL 配接器安裝，以無訊息模式更新</span><span class="sxs-lookup"><span data-stu-id="4caa7-286">Update the SQL Adapter installation in silent mode</span></span>  

1. <span data-ttu-id="4caa7-287">開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="4caa7-287">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  

2. <span data-ttu-id="4caa7-288">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="4caa7-288">Run the following command:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="4caa7-289">若要修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以無訊息模式的 x64 型的平台，在下列命令中，在安裝取代 SqlAdapterSetup64.msi SqlAdapterSetup.msi。</span><span class="sxs-lookup"><span data-stu-id="4caa7-289">To modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn /f  
   ```  

   > [!IMPORTANT]
   >  <span data-ttu-id="4caa7-290">同時修改[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇參與或退出 CEIP。</span><span class="sxs-lookup"><span data-stu-id="4caa7-290">While modifying the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="4caa7-291">喜好設定會維持不變您指定在安裝時，即使您明確地設定 CEIP_OPTIN 為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="4caa7-291">The preferences will remain the same as you specified during the installation, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  

    <span data-ttu-id="4caa7-292">如需詳細資訊`msiexec`命令中，輸入`msiexec`上的命令列和按下`ENTER`，或參閱[ https://support.microsoft.com/kb/230781 ](https://support.microsoft.com/kb/230781)。</span><span class="sxs-lookup"><span data-stu-id="4caa7-292">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>   

<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a><span data-ttu-id="4caa7-293">解除安裝或移除 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="4caa7-293">Uninstall or remove the SQL Adapter</span></span>  
 <span data-ttu-id="4caa7-294">執行下列步驟來移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="4caa7-294">Perform the following steps to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from your computer.</span></span> <span data-ttu-id="4caa7-295">請確定您已[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝在執行安裝精靈來移除之前[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-295">Make sure you have the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

 <span data-ttu-id="4caa7-296">您可以移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="4caa7-296">You can remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  

-   <span data-ttu-id="4caa7-297">**在互動模式中**執行安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="4caa7-297">**In interactive mode** by running the setup wizard.</span></span>  

-   <span data-ttu-id="4caa7-298">**以無訊息模式**使用命令列。</span><span class="sxs-lookup"><span data-stu-id="4caa7-298">**In silent mode** by using the command line.</span></span>  

#### <a name="uninstall-in-interactive-mode"></a><span data-ttu-id="4caa7-299">在互動模式中解除安裝</span><span class="sxs-lookup"><span data-stu-id="4caa7-299">Uninstall in interactive mode</span></span>  

1.  <span data-ttu-id="4caa7-300">按一下 **開始**，然後按一下**控制台**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-300">Click **Start**, and then click **Control Panel**.</span></span>  

2.  <span data-ttu-id="4caa7-301">在控制台中，按兩下**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-301">In Control Panel, double-click  **Programs and Features**.</span></span>  

3.  <span data-ttu-id="4caa7-302">在 **新增或移除程式**視窗中，選取**Microsoft BizTalk Adapter for SQL Server**，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-302">In the **Add or Remove Programs** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Remove**.</span></span>  

4.  <span data-ttu-id="4caa7-303">在對話方塊中，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="4caa7-303">In the dialog box, click **Yes**.</span></span>  

#### <a name="uninstall-in-silent-mode"></a><span data-ttu-id="4caa7-304">解除安裝以無訊息模式</span><span class="sxs-lookup"><span data-stu-id="4caa7-304">Uninstall in silent mode</span></span>  

1. <span data-ttu-id="4caa7-305">開啟命令提示字元，並瀏覽至根目錄的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="4caa7-305">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  

2. <span data-ttu-id="4caa7-306">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="4caa7-306">Run the following command:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="4caa7-307">若要移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在無訊息模式的 x64 型的平台，在下列命令中，取代 SqlAdapterSetup.msi SqlAdapterSetup64.msi。</span><span class="sxs-lookup"><span data-stu-id="4caa7-307">To remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  

   ```  
   msiexec /x SqlAdapterSetup.msi /qn  
   ```  

    <span data-ttu-id="4caa7-308">此命令會移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從電腦。</span><span class="sxs-lookup"><span data-stu-id="4caa7-308">This command removes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from the computer.</span></span>  

    <span data-ttu-id="4caa7-309">如需詳細資訊`msiexec`命令中，輸入`msiexec`上的命令列和按下`ENTER`，或參閱[ https://support.microsoft.com/kb/230781 ](https://support.microsoft.com/kb/230781)。</span><span class="sxs-lookup"><span data-stu-id="4caa7-309">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  

<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a><span data-ttu-id="4caa7-310">解除安裝後工作</span><span class="sxs-lookup"><span data-stu-id="4caa7-310">Post-uninstall task</span></span>  
 <span data-ttu-id="4caa7-311">如果[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式無法移除配接器繫結同時移除[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須手動移除它們。</span><span class="sxs-lookup"><span data-stu-id="4caa7-311">If the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] setup fails to remove the adapter bindings while removing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must remove them manually.</span></span> <span data-ttu-id="4caa7-312">下節描述如何手動移除的繫結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4caa7-312">The following section describes how to manually remove the bindings for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

<a name="BKMK_Remove_Binding"></a>   
#### <a name="manually-remove-the-bindings"></a><span data-ttu-id="4caa7-313">以手動方式移除繫結</span><span class="sxs-lookup"><span data-stu-id="4caa7-313">Manually remove the bindings</span></span>  
 <span data-ttu-id="4caa7-314">執行這些步驟*只*如果安裝精靈 無法移除 machine.config 檔案中的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="4caa7-314">Perform these steps *only* if the setup wizard fails to remove the adapter bindings from the machine.config file.</span></span>  

1. <span data-ttu-id="4caa7-315">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4caa7-315">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="4caa7-316">例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="4caa7-316">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  

   - <span data-ttu-id="4caa7-317">Microsoft.NET framework 3.5 SP1 \<*版本*\>是.NET framework 版本 v2.0.50727。</span><span class="sxs-lookup"><span data-stu-id="4caa7-317">For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.</span></span>  

   - <span data-ttu-id="4caa7-318">Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)]， \<*版本*\>是.NET framework 版本 v4.0.30319。</span><span class="sxs-lookup"><span data-stu-id="4caa7-318">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.</span></span>  

2. <span data-ttu-id="4caa7-319">開啟使用文字編輯器的檔案。</span><span class="sxs-lookup"><span data-stu-id="4caa7-319">Open the file using a text editor.</span></span>  

3. <span data-ttu-id="4caa7-320">若要移除介面卡繫結註冊：</span><span class="sxs-lookup"><span data-stu-id="4caa7-320">To remove the adapter binding registration:</span></span>  

   1. <span data-ttu-id="4caa7-321">搜尋 [system.serviceModel] 的項目，並移除下列項目底下：</span><span class="sxs-lookup"><span data-stu-id="4caa7-321">Search for the element "system.serviceModel" and remove the following from under the element:</span></span>  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  

      ```  

   2. <span data-ttu-id="4caa7-322">搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="4caa7-322">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  

   3. <span data-ttu-id="4caa7-323">移除 「 bindingElementExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="4caa7-323">Remove the following section under the "bindingElementExtensions" node.</span></span>  

       <span data-ttu-id="4caa7-324">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="4caa7-324">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. <span data-ttu-id="4caa7-325">搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="4caa7-325">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  

   5. <span data-ttu-id="4caa7-326">移除 「 bindingExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="4caa7-326">Remove the following section under the "bindingExtensions" node.</span></span>  

       <span data-ttu-id="4caa7-327">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="4caa7-327">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

4. <span data-ttu-id="4caa7-328">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4caa7-328">Save and close the machine.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4caa7-329">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4caa7-329">See also</span></span>
[<span data-ttu-id="4caa7-330">安裝 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="4caa7-330">Install the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[<span data-ttu-id="4caa7-331">了解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="4caa7-331">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)