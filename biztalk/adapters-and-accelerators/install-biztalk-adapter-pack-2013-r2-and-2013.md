---
title: 安裝 BizTalk Adapter Pack 2013 R2 和 2013年 |Microsoft 文件
description: 必要條件和步驟以安裝 BAP 2013 R2 和 BizTalk Server 隨附的 BAP 2013
ms.custom: ''
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9980953a-8d38-476f-af38-4f4214ba61f2
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8bc1ebbdaf2973f4749da6c0832d49204588b6c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="install-biztalk-adapter-pack-2013-r2-and-2013"></a><span data-ttu-id="d702e-103">安裝 BizTalk Adapter Pack 2013 R2 和 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-103">Install BizTalk Adapter Pack 2013 R2 and 2013</span></span>
<span data-ttu-id="d702e-104">本文件列出的軟體需求，以及的步驟，安裝 Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] (BAP) 隨附於 BizTalk Server 2013 或[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-104">This document lists the software requirements, and the steps to install the Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] (BAP) included with BizTalk Server 2013 or [!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)].</span></span>  
  
## <a name="change-log"></a><span data-ttu-id="d702e-105">變更記錄</span><span class="sxs-lookup"><span data-stu-id="d702e-105">Change Log</span></span>  
  
|<span data-ttu-id="d702e-106">日期</span><span class="sxs-lookup"><span data-stu-id="d702e-106">Date</span></span>|<span data-ttu-id="d702e-107">變更</span><span class="sxs-lookup"><span data-stu-id="d702e-107">Change</span></span>|  
|---|---|  
|<span data-ttu-id="d702e-108">2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="d702e-108">March 2016</span></span>|<span data-ttu-id="d702e-109">在**之後安裝...**，加入步驟來設定 Oracle 資料庫配接器使用較新的 Oracle.DataAccess.dll 版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-109">In **After installing…**, added steps to configure Oracle Database adapter to use the newer Oracle.DataAccess.dll version.</span></span>|  
  
<a name="BKMK_Prereqs"></a>   
## <a name="software-prerequisites"></a><span data-ttu-id="d702e-110">軟體必要條件</span><span class="sxs-lookup"><span data-stu-id="d702e-110">Software prerequisites</span></span>  
 <span data-ttu-id="d702e-111">[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]可以取用從：</span><span class="sxs-lookup"><span data-stu-id="d702e-111">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be consumed from:</span></span>  
  
-   <span data-ttu-id="d702e-112">.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="d702e-112">A .NET application</span></span>  
  
-   <span data-ttu-id="d702e-113">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-113">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="d702e-114">ADO 介面</span><span class="sxs-lookup"><span data-stu-id="d702e-114">An ADO interface</span></span>  
  
-   <span data-ttu-id="d702e-115">Microsoft SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="d702e-115">A Microsoft SharePoint portal</span></span>  
  
 <span data-ttu-id="d702e-116">根據您如何使用配接器，所需的軟體而異。</span><span class="sxs-lookup"><span data-stu-id="d702e-116">Based on how you use the adapters, the required software varies.</span></span>  
  
### <a name="prerequisites-when-using-a-net-application"></a><span data-ttu-id="d702e-117">使用.NET 應用程式時的必要條件</span><span class="sxs-lookup"><span data-stu-id="d702e-117">Prerequisites when using a .NET application</span></span>  
<span data-ttu-id="d702e-118">當取用配接器使用.NET 應用程式，下列的軟體需要在開發電腦 （您要在其中建立.NET 應用程式的電腦）。</span><span class="sxs-lookup"><span data-stu-id="d702e-118">When using a .NET application to consume the adapters, the following software is required on your development computer (the computer where you're creating the .NET application).</span></span> <span data-ttu-id="d702e-119">列出的順序安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-119">Install the software in the order listed.</span></span>
  
|<span data-ttu-id="d702e-120">BizTalk Adapter Pack 2013 R2</span><span class="sxs-lookup"><span data-stu-id="d702e-120">BizTalk Adapter Pack 2013 R2</span></span>|<span data-ttu-id="d702e-121">BizTalk Adapter Pack 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-121">BizTalk Adapter Pack 2013</span></span>|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-122"> R2 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]，Windows 8.1、 Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-122"> R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1</span></span>|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-123">[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1、 Windows 8、 Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-123">, [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1</span></span>|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|<span data-ttu-id="d702e-124">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-124">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="d702e-125">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-125">Visual Studio 2013</span></span>|<span data-ttu-id="d702e-126">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="d702e-126">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|  
|<span data-ttu-id="d702e-127">企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-127">The enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-128">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-128">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>|<span data-ttu-id="d702e-129">企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-129">The enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-130">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-130">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>|  

### <a name="prerequisites-when-using-a-biztalk-server"></a><span data-ttu-id="d702e-131">當您使用 BizTalk Server 的必要條件</span><span class="sxs-lookup"><span data-stu-id="d702e-131">Prerequisites when using a BizTalk Server</span></span>  
<span data-ttu-id="d702e-132">當使用 BizTalk Server 使用配接器時，BizTalk Server 上需要下列軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-132">When using a BizTalk Server to consume the adapters, the following software is required on your BizTalk Server.</span></span> <span data-ttu-id="d702e-133">列出的順序安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-133">Install the software in the order listed.</span></span>
  
|<span data-ttu-id="d702e-134">BizTalk Adapter Pack 2013 R2</span><span class="sxs-lookup"><span data-stu-id="d702e-134">BizTalk Adapter Pack 2013 R2</span></span>|<span data-ttu-id="d702e-135">BizTalk Adapter Pack 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-135">BizTalk Adapter Pack 2013</span></span>|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-136"> R2 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]，Windows 8.1、 Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-136"> R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1</span></span>|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-137">[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1、 Windows 8、 Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-137">, [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1</span></span>|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|<span data-ttu-id="d702e-138">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-138">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="d702e-139">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-139">Visual Studio 2013</span></span>|<span data-ttu-id="d702e-140">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="d702e-140">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="d702e-141">安裝[!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-141">Install the [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="d702e-142">若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-142">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span>|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="d702e-143">安裝[!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)]如[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]隨附[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-143">Install the [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="d702e-144">若要安裝，請執行**自訂**(選取**BizTalk Server 增益集**) 或**完成**安裝[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-144">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span>|  
|<span data-ttu-id="d702e-145">BizTalk Server 2013 R2</span><span class="sxs-lookup"><span data-stu-id="d702e-145">BizTalk Server 2013 R2</span></span>|<span data-ttu-id="d702e-146">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-146">BizTalk Server 2013</span></span>|  
|<span data-ttu-id="d702e-147">企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-147">The enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-148">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-148">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>|<span data-ttu-id="d702e-149">企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-149">The enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-150">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-150">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>|  

### <a name="prerequisites-when-using-ado"></a><span data-ttu-id="d702e-151">使用 ADO 時的必要條件</span><span class="sxs-lookup"><span data-stu-id="d702e-151">Prerequisites when using ADO</span></span>  
 <span data-ttu-id="d702e-152">**[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]**和**[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]**包括 ADO 層 (*[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]*和*[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]*)。</span><span class="sxs-lookup"><span data-stu-id="d702e-152">The **[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]** and **[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]** include an ADO layer (*[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]* and *[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]*).</span></span> <span data-ttu-id="d702e-153">這個 ADO 層可用來撰寫 ADO.NET 用戶端連接至 SAP 系統或 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="d702e-153">This ADO layer can be used to write an ADO.NET client to connect to an SAP system or Siebel system.</span></span> <span data-ttu-id="d702e-154">您也可以使用 ADO 圖層與 SQL Server Integration Services (SSIS) 匯入和匯出資料從 LOB 應用程式和 SQL Server Reporting Services (SSRS) 來產生報表呈現資料從 LOB 系統。</span><span class="sxs-lookup"><span data-stu-id="d702e-154">You can also use the ADO layer with SQL Server Integration Services (SSIS) to import and export data from the LOB application, and SQL Server Reporting Services (SSRS) to generate reports to present data from the LOB systems.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d702e-155">僅適用於支援搭配使用 ADO 提供者與 SSRS *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]*。</span><span class="sxs-lookup"><span data-stu-id="d702e-155">Using the ADO Provider with SSRS is supported only for the *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]*.</span></span>  
  
<span data-ttu-id="d702e-156">使用的電腦上需要下列軟體[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]ADO 介面。</span><span class="sxs-lookup"><span data-stu-id="d702e-156">The following software is required on the computer that uses the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] with an ADO interface.</span></span> <span data-ttu-id="d702e-157">列出的順序安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-157">Install the software in the order listed.</span></span>
  
|<span data-ttu-id="d702e-158">BizTalk Adapter Pack 2013 R2</span><span class="sxs-lookup"><span data-stu-id="d702e-158">BizTalk Adapter Pack 2013 R2</span></span>|<span data-ttu-id="d702e-159">BizTalk Adapter Pack 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-159">BizTalk Adapter Pack 2013</span></span>|  
|---|---|  
|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-160"> R2 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]，Windows 8.1、 Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-160"> R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1</span></span>|[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-161">[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1、 Windows 8、 Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-161">, [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1</span></span>|  
|[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]|<span data-ttu-id="d702e-162">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-162">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="d702e-163">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-163">Visual Studio 2013</span></span>|<span data-ttu-id="d702e-164">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="d702e-164">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]|  
|[!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)]<span data-ttu-id="d702e-165">, [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-165">, [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]</span></span>|[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]<span data-ttu-id="d702e-166">, [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-166">, [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]</span></span>|  
|<span data-ttu-id="d702e-167">企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-167">The enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-168">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-168">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>|<span data-ttu-id="d702e-169">企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-169">The enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-170">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-170">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>|  

### <a name="prerequisites-when-using-microsoft-sharepoint"></a><span data-ttu-id="d702e-171">使用 Microsoft SharePoint 時的必要條件</span><span class="sxs-lookup"><span data-stu-id="d702e-171">Prerequisites when using Microsoft SharePoint</span></span>  
 <span data-ttu-id="d702e-172">使用 Microsoft SharePoint 配接器的目標是為 SharePoint 入口網站上顯示資料的 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d702e-172">The goal of using the adapters with Microsoft SharePoint is to show data from an LOB application on a SharePoint portal.</span></span>  
  
<span data-ttu-id="d702e-173">典型的安裝過程中，使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]SharePoint 可以在單一電腦或針對不同工作使用不同的電腦。</span><span class="sxs-lookup"><span data-stu-id="d702e-173">A typical setup with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] and SharePoint can be a single computer or use different computers for different tasks.</span></span> <span data-ttu-id="d702e-174">下表摘要說明每一部電腦的軟體必要條件。</span><span class="sxs-lookup"><span data-stu-id="d702e-174">The following table summarizes the software prerequisites for each computer.</span></span> <span data-ttu-id="d702e-175">如果您使用單一電腦，該電腦上需要的所有軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-175">If you are using a single computer, all the software is required on that computer.</span></span> <span data-ttu-id="d702e-176">列出的順序安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-176">Install the software in the order listed.</span></span>  
  
|<span data-ttu-id="d702e-177">您用來執行 WCF 配接器服務開發精靈的電腦</span><span class="sxs-lookup"><span data-stu-id="d702e-177">Computer where you run the WCF Adapter Service Development Wizard</span></span>|<span data-ttu-id="d702e-178">您用來裝載 WCF 服務的電腦</span><span class="sxs-lookup"><span data-stu-id="d702e-178">Computer where you host the WCF service</span></span>|<span data-ttu-id="d702e-179">您可以在其中定義外部內容類型使用 SharePoint Designer 的電腦</span><span class="sxs-lookup"><span data-stu-id="d702e-179">Computer where you can use the SharePoint Designer to define your External Content Types</span></span>|<span data-ttu-id="d702e-180">您使用 SharePoint 來呈現的資訊從 LOB 應用程式的電腦</span><span class="sxs-lookup"><span data-stu-id="d702e-180">Computer where you use SharePoint to present the information from an LOB application</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="d702e-181">**BAP 2013 R2**:</span><span class="sxs-lookup"><span data-stu-id="d702e-181">**BAP 2013 R2**:</span></span><ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-182"> R2</span><span class="sxs-lookup"><span data-stu-id="d702e-182"> R2</span></span><br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/><span data-ttu-id="d702e-183">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d702e-183">Windows 8.1</span></span><br/><span data-ttu-id="d702e-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-184">Windows 7 SP1</span></span></li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li> <span data-ttu-id="d702e-185">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="d702e-185">Visual Studio 2013</span></span></li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li><span data-ttu-id="d702e-186">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-186">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span></span></li><li><span data-ttu-id="d702e-187">個別的企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-187">Respective enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-188">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-188">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span></li></ul> <span data-ttu-id="d702e-189">**BAP 2013**:</span><span class="sxs-lookup"><span data-stu-id="d702e-189">**BAP 2013**:</span></span><ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]<span data-ttu-id="d702e-190"> SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-190"> SP1</span></span><br/><span data-ttu-id="d702e-191">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d702e-191">Windows 8</span></span><br/><span data-ttu-id="d702e-192">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-192">Windows 7 SP1</span></span></li><li><span data-ttu-id="d702e-193">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-193">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span></span></li><li><span data-ttu-id="d702e-194">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="d702e-194">Visual Studio 2012</span></span></li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li><span data-ttu-id="d702e-195">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-195">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span></span></li><li><span data-ttu-id="d702e-196">個別的企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-196">Respective enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-197">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-197">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span></li></ul>|<span data-ttu-id="d702e-198">**BAP 2013 R2**:</span><span class="sxs-lookup"><span data-stu-id="d702e-198">**BAP 2013 R2**:</span></span><ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="d702e-199"> R2</span><span class="sxs-lookup"><span data-stu-id="d702e-199"> R2</span></span><br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/><span data-ttu-id="d702e-200">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d702e-200">Windows 8.1</span></span><br/><span data-ttu-id="d702e-201">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-201">Windows 7 SP1</span></span></li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li><span data-ttu-id="d702e-202">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-202">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span></span></li><li><span data-ttu-id="d702e-203">個別的企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-203">Respective enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-204">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-204">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span></li><li><span data-ttu-id="d702e-205">隨附於作業系統的網際網路資訊服務 (IIS) 版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-205">Internet Information Services (IIS) version that comes with the operating system.</span></span> <span data-ttu-id="d702e-206">KB 224609 列出的版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-206">KB 224609 lists the versions.</span></span></li></ul><span data-ttu-id="d702e-207">**BAP 2013**:</span><span class="sxs-lookup"><span data-stu-id="d702e-207">**BAP 2013**:</span></span><ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]<span data-ttu-id="d702e-208"> SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-208"> SP1</span></span><br/><span data-ttu-id="d702e-209">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d702e-209">Windows 8</span></span><br/><span data-ttu-id="d702e-210">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d702e-210">Windows 7 SP1</span></span></li><li><span data-ttu-id="d702e-211">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-211">Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</span></span></li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li><span data-ttu-id="d702e-212">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-212">Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</span></span></li><li><span data-ttu-id="d702e-213">個別的企業應用程式用戶端和相關聯的軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-213">Respective enterprise application clients and associated software.</span></span> <span data-ttu-id="d702e-214">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-214">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span></li><li><span data-ttu-id="d702e-215">隨附於作業系統的網際網路資訊服務 (IIS) 版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-215">Internet Information Services (IIS) version that comes with the operating system.</span></span> <span data-ttu-id="d702e-216">KB 224609 列出的版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-216">KB 224609 lists the versions.</span></span></li></ul>|<span data-ttu-id="d702e-217">Microsoft Office SharePoint Server 軟體開發套件 (SDK)</span><span class="sxs-lookup"><span data-stu-id="d702e-217">Microsoft Office SharePoint Server Software Development Kit (SDK)</span></span>|<span data-ttu-id="d702e-218">Microsoft Office 伺服器基礎結構已更新。</span><span class="sxs-lookup"><span data-stu-id="d702e-218">Microsoft Office Servers Infrastructure Update.</span></span> <span data-ttu-id="d702e-219">從下列網址下載[ http://go.microsoft.com/fwlink/?LinkId=128344 ](http://go.microsoft.com/fwlink/?LinkId=128344)。</span><span class="sxs-lookup"><span data-stu-id="d702e-219">Download at [http://go.microsoft.com/fwlink/?LinkId=128344](http://go.microsoft.com/fwlink/?LinkId=128344).</span></span>|  
  
<a name="BKMK_SuppLOB"></a>   
## <a name="supported-enterprise-application-versions"></a><span data-ttu-id="d702e-220">支援的企業應用程式版本</span><span class="sxs-lookup"><span data-stu-id="d702e-220">Supported enterprise application versions</span></span>  

<span data-ttu-id="d702e-221">若要查看特定的 LOB 系統版本所支援的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱**[支援的特定業務 (LOB) 系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**。</span><span class="sxs-lookup"><span data-stu-id="d702e-221">To see the specific LOB system versions that are supported by the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see **[Supported Line-of-Business (LOB) systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**.</span></span> 

<span data-ttu-id="d702e-222">此區段會列出每張介面卡，任何額外的資訊，例如 Dll 的任何用戶端所需的每個介面卡。</span><span class="sxs-lookup"><span data-stu-id="d702e-222">This section lists any extra info for each adapter, such as any client DLLs required for each adapter.</span></span>  
  
### <a name="oracle-database-adapter"></a><span data-ttu-id="d702e-223">Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="d702e-223">Oracle Database adapter</span></span>  
  
-   <span data-ttu-id="d702e-224">選擇性： 如果您使用分散式的交易與 Oracle 資料庫時，安裝**Oracle Services for Microsoft Transaction Server** （Oracle 用戶端安裝的一部分） 的電腦上執行配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="d702e-224">Optional: If you use distributed transactions with the Oracle database, install **Oracle Services for Microsoft Transaction Server** (part of the Oracle client installation) on the computer running the adapter client.</span></span>  
  
-   <span data-ttu-id="d702e-225">若要使用最新版 ODP.NET 應用程式，安裝**原則 Dll**並在 GAC 中註冊 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-225">For your application to work with the most recent version of ODP.NET, install the **policy DLLs** and register the DLLs in the GAC.</span></span> <span data-ttu-id="d702e-226">請參閱[Oracle Data Provider for.NET 常見問題集](http://www.oracle.com/technetwork/database/windows/faq-093106.html)。</span><span class="sxs-lookup"><span data-stu-id="d702e-226">See [Oracle Data Provider for .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).</span></span>  

### <a name="oracle-e-business-adapter"></a><span data-ttu-id="d702e-227">Oracle E-Business 配接器</span><span class="sxs-lookup"><span data-stu-id="d702e-227">Oracle E-Business adapter</span></span>  
  
-   <span data-ttu-id="d702e-228">選擇性： 若要使用分散式的交易與 Oracle 資料庫，安裝**Oracle Services for Microsoft Transaction Server** （Oracle 用戶端安裝的一部分） 的電腦上執行配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="d702e-228">Optional: To use distributed transactions with the Oracle database, install **Oracle Services for Microsoft Transaction Server** (part of the Oracle client installation) on the computer running the adapter client.</span></span>  
  
-   <span data-ttu-id="d702e-229">若要使用最新版 ODP.NET 應用程式，安裝**原則 Dll**並在 GAC 中註冊 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-229">For your application to work with the most recent version of ODP.NET, install the **policy DLLs** and register the DLLs in the GAC.</span></span> <span data-ttu-id="d702e-230">請參閱[Oracle Data Provider for.NET 常見問題集](http://www.oracle.com/technetwork/database/windows/faq-093106.html)。</span><span class="sxs-lookup"><span data-stu-id="d702e-230">See [Oracle Data Provider for .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).</span></span>  
  
### <a name="sap-adapter"></a><span data-ttu-id="d702e-231">SAP adapter (SAP 配接器)</span><span class="sxs-lookup"><span data-stu-id="d702e-231">SAP adapter</span></span>  
  
-   <span data-ttu-id="d702e-232">[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]需要 RFC SDK，不論是否 SAP 系統是 Unicode 或非 Unicode 的 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-232">The [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] requires Unicode version of the RFC SDK irrespective of whether the SAP system is Unicode or non-Unicode.</span></span>  
  
-   <span data-ttu-id="d702e-233">**必要驅動程式**： 下表列出所需的 Dll[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]與 SAP 系統的介面。</span><span class="sxs-lookup"><span data-stu-id="d702e-233">**Required drivers**: The following table lists the DLLs required by the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] to interface with the SAP system.</span></span> <span data-ttu-id="d702e-234">大部分的包含這些 Dll 的套件，必須先下載 SAP 服務商場。</span><span class="sxs-lookup"><span data-stu-id="d702e-234">Most of the packages that contain these DLLs must be downloaded from the SAP Service Marketplace.</span></span> <span data-ttu-id="d702e-235">若要取得 SAP 服務商場的下載項目：</span><span class="sxs-lookup"><span data-stu-id="d702e-235">To get downloads from the SAP Service Marketplace:</span></span> 
  
    1.  <span data-ttu-id="d702e-236">安裝 SAP 服務商場的下載管理員使用。</span><span class="sxs-lookup"><span data-stu-id="d702e-236">Install the Download Manager available from the SAP Service Marketplace.</span></span>  
  
    2.  <span data-ttu-id="d702e-237">設定的下載管理員 SAP 服務 marketplace 使用您的認證。</span><span class="sxs-lookup"><span data-stu-id="d702e-237">Configure the Download Manager by using your credentials for the SAP Service Marketplace.</span></span>  
  
    3.  <span data-ttu-id="d702e-238">授權您組織中的 SAP 系統管理員從 SAP 服務網站下載軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-238">Be authorized by the SAP administrator in your organization to download software from the SAP service website.</span></span> <span data-ttu-id="d702e-239">這是必要的因為對 SAP 軟體發佈中心的存取權受到下載軟體的授權物件。</span><span class="sxs-lookup"><span data-stu-id="d702e-239">This is required because access to the SAP Software Distribution Center is restricted by a 'Download Software' authorization object.</span></span> <span data-ttu-id="d702e-240">這可確保由授權的使用者只會下載軟體。</span><span class="sxs-lookup"><span data-stu-id="d702e-240">This ensures that software is downloaded only by authorized users.</span></span>  
  
    4.  <span data-ttu-id="d702e-241">安裝 SAPCAR 程式才可從您下載 SAP 服務商場上的封裝解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="d702e-241">Install the SAPCAR program, which is required to extract the files from the packages that you download from the SAP Service Marketplace.</span></span> <span data-ttu-id="d702e-242">SAPCAR 也會提供 SAP 服務商場中。</span><span class="sxs-lookup"><span data-stu-id="d702e-242">SAPCAR is also available from the SAP Service Marketplace.</span></span>  
  
     <span data-ttu-id="d702e-243">32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，您必須擁有各自的 32 位元和 64 位元版本的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-243">For the 32-bit and 64-bit version of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], you must have the respective 32-bit and 64-bit versions of these DLLs.</span></span>  
  
    -   <span data-ttu-id="d702e-244">在 32 位元電腦上的 32 位元版本的 dll 必須加入 C:\Windows\System32 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d702e-244">On a 32-bit computer, the 32-bit version of the DLLs must be added to the C:\Windows\System32 folder.</span></span>  
  
    -   <span data-ttu-id="d702e-245">在 64 位元電腦上的 32 位元版本的 dll 必須加入 C:\Windows\SysWow64 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d702e-245">On a 64-bit computer, the 32-bit version of the DLLs must be added to the C:\Windows\SysWow64 folder.</span></span> <span data-ttu-id="d702e-246">64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d702e-246">The 64-bit version of the DLLs must be added to the C:\Windows\System32 folder.</span></span>  
  
    |<span data-ttu-id="d702e-247">SAP 用戶端版本</span><span class="sxs-lookup"><span data-stu-id="d702e-247">SAP client version</span></span>|<span data-ttu-id="d702e-248">必要的驅動程式</span><span class="sxs-lookup"><span data-stu-id="d702e-248">Required drivers</span></span>|  
    |------------------------|----------------------|  
    |<span data-ttu-id="d702e-249">6.4</span><span class="sxs-lookup"><span data-stu-id="d702e-249">6.4</span></span>|<span data-ttu-id="d702e-250">**BizTalk Adapter Pack 2013 只**</span><span class="sxs-lookup"><span data-stu-id="d702e-250">**BizTalk Adapter Pack 2013 Only**</span></span><br /><br /> <span data-ttu-id="d702e-251">- **SAP RFC SDK 6.40 UNICODE**。</span><span class="sxs-lookup"><span data-stu-id="d702e-251">- **SAP RFC SDK 6.40 UNICODE**.</span></span> <span data-ttu-id="d702e-252">使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[ http://go.microsoft.com/fwlink/?LinkId=94691 ](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，請將所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾都複製到前面這個資料表的相關位置所述。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d702e-252">This is available as part of SNOTE<sup>*</sup> 27517. The instructions to download the SDK are available at [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). After you have downloaded and extracted the SDK, copy all the DLLs from the \rfcsdk\bin and \rfcsdk\lib folders to the relevant location mentioned preceding this table.<br /><br /> - DLLs are available from SAP as part of **R3DLLINST.zip**. This contains Microsoft run-time DLLs and can be downloaded from the SAP site. See SNOTE<sup>*</sup> 684106 for more information.</span></span> <span data-ttu-id="d702e-253">您可以下載.zip 檔案，從[ http://go.microsoft.com/fwlink/?LinkId=94693 ](http://go.microsoft.com/fwlink/?LinkId=94693)。</span><span class="sxs-lookup"><span data-stu-id="d702e-253">You can download the .zip file from [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693).</span></span> <span data-ttu-id="d702e-254">此連結會有 「 附件 」 選項，從您可以在此下載封裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-254">This link has an “Attachments” option from where you can download the package.</span></span><br /><br /> <span data-ttu-id="d702e-255">-如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-255">- If you use SAP Secure Network Communications (SNC) to connect to an SAP system, you must also have the relevant DLLs from SAP.</span></span> <span data-ttu-id="d702e-256">這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> \* </sup> 352295。</span><span class="sxs-lookup"><span data-stu-id="d702e-256">These DLLs are different for 32-bit and 64-bit platforms and are available with SNOTE<sup>\*</sup> 352295.</span></span> <span data-ttu-id="d702e-257">您可以下載從 Dll [ http://go.microsoft.com/fwlink/?LinkId=104032 ](http://go.microsoft.com/fwlink/?LinkId=104032)。</span><span class="sxs-lookup"><span data-stu-id="d702e-257">You can download the DLLs from [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032).</span></span> <span data-ttu-id="d702e-258">此連結會有 「 附件 」 選項，從您可以在此下載封裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-258">This link has an “Attachments” option from where you can download the package.</span></span> <span data-ttu-id="d702e-259">Dll 的名稱為：</span><span class="sxs-lookup"><span data-stu-id="d702e-259">The names of the DLLs are:</span></span><br /><br /> <span data-ttu-id="d702e-260">- **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-260">- **For 32-bit**: gsskrb5.dll, gssntlm.dll</span></span><br /><br /> <span data-ttu-id="d702e-261">-  **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-261">-  **For 64-bit x86**: gx64krb5.dll, gx64ntlm.dll</span></span>|  
    |<span data-ttu-id="d702e-262">7.0</span><span class="sxs-lookup"><span data-stu-id="d702e-262">7.0</span></span>|<span data-ttu-id="d702e-263">- **SAP RFC SDK 7.00 UNICODE**。</span><span class="sxs-lookup"><span data-stu-id="d702e-263">- **SAP RFC SDK 7.00 UNICODE**.</span></span> <span data-ttu-id="d702e-264">使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[ http://go.microsoft.com/fwlink/?LinkId=94691 ](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，前面此資料表所述複製所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾和相關的位置。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d702e-264">This is available as part of SNOTE<sup>*</sup> 27517. The instructions to download the SDK are available at [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). After you have downloaded and extracted the SDK, copy all the DLLs from the \rfcsdk\bin and \rfcsdk\lib folders and to the relevant location mentioned preceding this table.<br /><br /> - DLLs are available from SAP as part of **R3DLLINST.zip**. This contains Microsoft run-time DLLs and can be downloaded from the SAP site. See SNOTE<sup>*</sup> 684106 for more information.</span></span> <span data-ttu-id="d702e-265">您可以下載.zip 檔案，從[ http://go.microsoft.com/fwlink/?LinkId=94693 ](http://go.microsoft.com/fwlink/?LinkId=94693)。</span><span class="sxs-lookup"><span data-stu-id="d702e-265">You can download the .zip file from [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693).</span></span> <span data-ttu-id="d702e-266">此連結會有 「 附件 」 選項，從您可以在此下載封裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-266">This link has an “Attachments” option from where you can download the package.</span></span><br /><br /> <span data-ttu-id="d702e-267">-如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-267">- If you use SAP Secure Network Communications (SNC) to connect to an SAP system, you must also have the relevant DLLs from SAP.</span></span> <span data-ttu-id="d702e-268">這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> \* </sup> 352295。</span><span class="sxs-lookup"><span data-stu-id="d702e-268">These DLLs are different for 32-bit and 64-bit platforms and are available with SNOTE<sup>\*</sup> 352295.</span></span> <span data-ttu-id="d702e-269">您可以下載從 Dll [ http://go.microsoft.com/fwlink/?LinkId=104032 ](http://go.microsoft.com/fwlink/?LinkId=104032)。</span><span class="sxs-lookup"><span data-stu-id="d702e-269">You can download the DLLs from [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032).</span></span> <span data-ttu-id="d702e-270">此連結會有 「 附件 」 選項，從您可以在此下載封裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-270">This link has an “Attachments” option from where you can download the package.</span></span> <span data-ttu-id="d702e-271">Dll 的名稱為：</span><span class="sxs-lookup"><span data-stu-id="d702e-271">The names of the DLLs are:</span></span><br /><br /> <span data-ttu-id="d702e-272">- **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-272">- **For 32-bit**: gsskrb5.dll, gssntlm.dll</span></span><br /><br /> <span data-ttu-id="d702e-273">- **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-273">- **For 64-bit x86**: gx64krb5.dll, gx64ntlm.dll</span></span>|  
    |<span data-ttu-id="d702e-274">7.1</span><span class="sxs-lookup"><span data-stu-id="d702e-274">7.1</span></span>|<span data-ttu-id="d702e-275">- **SAP RFC SDK 7.10 UNICODE**。</span><span class="sxs-lookup"><span data-stu-id="d702e-275">- **SAP RFC SDK 7.10 UNICODE**.</span></span> <span data-ttu-id="d702e-276">使用這個選項做為一部分 SNOTE<sup> * </sup> 27517。若要下載 SDK 的指示位於[ http://go.microsoft.com/fwlink/?LinkId=94691 ](http://go.microsoft.com/fwlink/?LinkId=94691)。您已經下載並解壓縮 SDK 之後，請將所有 Dll 從 \rfcsdk\bin 和 \rfcsdk\lib 資料夾都複製到前面這個資料表的相關位置所述。<br /> <br /> -一部分都有提供從 SAP Dll **R3DLLINST.zip**。它包含 Microsoft 執行階段 Dll，而且可以從 SAP 網站下載。請參閱 SNOTE<sup> * </sup> 684106 如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d702e-276">This is available as part of SNOTE<sup>*</sup> 27517. The instructions to download the SDK are available at [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). After you have downloaded and extracted the SDK, copy all the DLLs from the \rfcsdk\bin and \rfcsdk\lib folders to the relevant location mentioned preceding this table.<br /><br /> - DLLs are available from SAP as part of **R3DLLINST.zip**. This contains Microsoft run-time DLLs and can be downloaded from the SAP site. See SNOTE<sup>*</sup> 684106 for more information.</span></span> <span data-ttu-id="d702e-277">您可以下載.zip 檔案，從[ http://go.microsoft.com/fwlink/?LinkId=94693 ](http://go.microsoft.com/fwlink/?LinkId=94693)。</span><span class="sxs-lookup"><span data-stu-id="d702e-277">You can download the .zip file from [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693).</span></span> <span data-ttu-id="d702e-278">此連結會有 「 附件 」 選項，從您可以在此下載封裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-278">This link has an “Attachments” option from where you can download the package.</span></span><br /><br /> <span data-ttu-id="d702e-279">Microsoft Visual c + + 執行階段 Dll 所需的 SAP 7.1 用戶端可從下列連結：</span><span class="sxs-lookup"><span data-stu-id="d702e-279">- Microsoft Visual C++ run-time DLLs required for SAP 7.1 client are available from the following links:</span></span><br /><br /> <span data-ttu-id="d702e-280">- **32 位元 SAP 7.1 用戶端**： 從 Vcredist_x86.exe [ http://go.microsoft.com/fwlink/?LinkId=107086 ](http://go.microsoft.com/fwlink/?LinkId=107086)。</span><span class="sxs-lookup"><span data-stu-id="d702e-280">- **For 32-bit SAP 7.1 client**:  Vcredist_x86.exe from [http://go.microsoft.com/fwlink/?LinkId=107086](http://go.microsoft.com/fwlink/?LinkId=107086).</span></span><br /><br /> <span data-ttu-id="d702e-281">-                                 **64 位元 SAP 7.1 用戶端**： 從 Vcredist_x64.exe [ http://go.microsoft.com/fwlink/?LinkId=107087 ](http://go.microsoft.com/fwlink/?LinkId=107087)。</span><span class="sxs-lookup"><span data-stu-id="d702e-281">-                                 **For 64-bit SAP 7.1 client**: Vcredist_x64.exe from [http://go.microsoft.com/fwlink/?LinkId=107087](http://go.microsoft.com/fwlink/?LinkId=107087).</span></span><br /><br /> <span data-ttu-id="d702e-282">-如果您使用 SAP 安全網路通訊 (SNC) 來連接至 SAP 系統時，您也必須擁有從 SAP 相關的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-282">- If you use SAP Secure Network Communications (SNC) to connect to an SAP system, you must also have the relevant DLLs from SAP.</span></span> <span data-ttu-id="d702e-283">這些 Dll 不同 32 位元和 64 位元平台，可用之 SNOTE<sup> \* </sup> 352295。</span><span class="sxs-lookup"><span data-stu-id="d702e-283">These DLLs are different for 32-bit and 64-bit platforms and are available with SNOTE<sup>\*</sup> 352295.</span></span> <span data-ttu-id="d702e-284">您可以下載從 Dll [ http://go.microsoft.com/fwlink/?LinkId=104032 ](http://go.microsoft.com/fwlink/?LinkId=104032)。</span><span class="sxs-lookup"><span data-stu-id="d702e-284">You can download the DLLs from [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032).</span></span> <span data-ttu-id="d702e-285">此連結會有 「 附件 」 選項，從您可以在此下載封裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-285">This link has an “Attachments” option from where you can download the package.</span></span> <span data-ttu-id="d702e-286">Dll 的名稱為：</span><span class="sxs-lookup"><span data-stu-id="d702e-286">The names of the DLLs are:</span></span><br /><br /> <span data-ttu-id="d702e-287">- **適用於 32 位元**: gsskrb5.dll、 gssntlm.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-287">- **For 32-bit**: gsskrb5.dll, gssntlm.dll</span></span><br /><br /> <span data-ttu-id="d702e-288">- **適用於 64 位元 x86**: gx64krb5.dll、 gx64ntlm.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-288">- **For 64-bit x86**: gx64krb5.dll, gx64ntlm.dll</span></span>|  
  
     * <span data-ttu-id="d702e-289">SNOTEs 是隨附於修正由 SAP 發行的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="d702e-289">SNOTEs are release notes that accompany fixes released by SAP.</span></span>  

### <a name="siebel-adapter"></a><span data-ttu-id="d702e-290">Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="d702e-290">Siebel adapter</span></span>  
<span data-ttu-id="d702e-291">沒有額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="d702e-291">No extra steps.</span></span>
  
### <a name="sql-adapter"></a><span data-ttu-id="d702e-292">SQL adapter (SQL 配接器)</span><span class="sxs-lookup"><span data-stu-id="d702e-292">SQL adapter</span></span>  
  
<span data-ttu-id="d702e-293">**必要驅動程式**:</span><span class="sxs-lookup"><span data-stu-id="d702e-293">**Required drivers**:</span></span>  
  
-   <span data-ttu-id="d702e-294">**適用於 SQL Server 2005**： 如果您在 SQL Server 中建立使用者定義型別 (Udt)，請確定 Udt 的個別的組件加入 GAC。</span><span class="sxs-lookup"><span data-stu-id="d702e-294">**For SQL Server 2005**: If you create User Defined Types (UDTs) in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.</span></span>  
  
-   <span data-ttu-id="d702e-295">**適用於 SQL Server 2014、 SQL Server 2012、 SQL Server 2008 R2、 SQL Server 2008 SP1**:</span><span class="sxs-lookup"><span data-stu-id="d702e-295">**For SQL Server 2014, SQL Server 2012, SQL Server 2008 R2,SQL Server 2008 SP1**:</span></span>  
  
    -   <span data-ttu-id="d702e-296">如果您使用 Udt 隨附於 SQL Server 版本，例如地理位置，請確定下列 Dll 會出現在 SQL Server 上執行作業使用配接器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d702e-296">If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server.</span></span> <span data-ttu-id="d702e-297">例如，如果您建立 BizTalk 專案，在 SQL Server 上執行作業，這些 Dll 必須存在於執行 BizTalk Server 電腦上。</span><span class="sxs-lookup"><span data-stu-id="d702e-297">For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.</span></span>  
  
        -   <span data-ttu-id="d702e-298">請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="d702e-298">Make sure Microsoft.SqlServer.Types.dll is added to the GAC.</span></span>  
  
        -   <span data-ttu-id="d702e-299">請確定 SqlServerSpatial.dll System32 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d702e-299">Make sure SqlServerSpatial.dll is available in the System32 folder.</span></span>    
        
        <span data-ttu-id="d702e-300">您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，並選取**管理工具 – 基本**和**管理工具-完整**中**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="d702e-300">You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.</span></span>          
  
    -   <span data-ttu-id="d702e-301">如果您使用配接器在 FILESTREAM 資料類型的資料行上執行作業時，請確定已安裝 SQL 用戶端連接性 SDK。</span><span class="sxs-lookup"><span data-stu-id="d702e-301">If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="d702e-302">您可以在執行 SQL Server 安裝程式並選取安裝 SQL 用戶端連接性 SDK **SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="d702e-302">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="d702e-303">配接器使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。</span><span class="sxs-lookup"><span data-stu-id="d702e-303">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  

    -   <span data-ttu-id="d702e-304">如果您在 SQL Server 中建立您自己的 Udt，請確定 Udt 的個別的組件加入 GAC。</span><span class="sxs-lookup"><span data-stu-id="d702e-304">If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.</span></span>

## <a name="64-bit-support"></a><span data-ttu-id="d702e-305">64 位元支援</span><span class="sxs-lookup"><span data-stu-id="d702e-305">64-bit support</span></span>

<span data-ttu-id="d702e-306">Siebel 配接器支援的 32 位元主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="d702e-306">The Siebel adapter is supported in a 32-bit host instance.</span></span> <span data-ttu-id="d702e-307">它不支援在 64 位元主控件執行個體中執行 Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="d702e-307">It is not supported to run the Siebel adapter in a 64-bit host instance.</span></span> 

<span data-ttu-id="d702e-308">所有其他配接器可以在 32 位元或 64 位元的主控件執行個體執行。</span><span class="sxs-lookup"><span data-stu-id="d702e-308">All the other adapters can run in a 32-bit or 64-bit host instance.</span></span> 


  
 <span data-ttu-id="d702e-309">如需有關安裝 32 位元和 64 位元支援的安裝案例[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱[32 位元和 64 位元平台上安裝 BizTalk Adapter Pack 狀況](#BKMK_Install_Scenarios)。</span><span class="sxs-lookup"><span data-stu-id="d702e-309">For more information about the supported installation scenarios for installing the 32-bit and 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see [Scenarios for Installing the BizTalk Adapter Pack on 32-bit and 64-bit Platforms](#BKMK_Install_Scenarios).</span></span>  
  
<a name="BKMK_Install_Adap"></a>   
## <a name="installing-the-biztalk-adapter-pack"></a><span data-ttu-id="d702e-310">安裝 BizTalk Adapter Pack</span><span class="sxs-lookup"><span data-stu-id="d702e-310">Installing the BizTalk Adapter Pack</span></span>  
 <span data-ttu-id="d702e-311">請確定所有[軟體必要條件](#BKMK_Prereqs)會安裝，才能安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-311">Make sure all the [software prerequisites](#BKMK_Prereqs) are installed before installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-312">您可以安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="d702e-312">You can install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="d702e-313">**以互動模式**： 執行安裝精靈</span><span class="sxs-lookup"><span data-stu-id="d702e-313">**In interactive mode**: Run the setup wizard</span></span>  
  
-   <span data-ttu-id="d702e-314">**以無訊息模式**： 使用命令列</span><span class="sxs-lookup"><span data-stu-id="d702e-314">**In silent mode**: Use the command line</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d702e-315">您必須在您安裝的電腦上系統管理權限[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，不論您是否要安裝使用精靈或命令列。</span><span class="sxs-lookup"><span data-stu-id="d702e-315">You must have administrative privileges on the computer where you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], irrespective of whether you are installing using the wizard or the command line.</span></span>  

### <a name="typical-vs-custom-installation"></a><span data-ttu-id="d702e-316">一般與自訂安裝</span><span class="sxs-lookup"><span data-stu-id="d702e-316">Typical vs custom installation</span></span>  
<span data-ttu-id="d702e-317">此區段會列出的安裝類型，以及與每個選項一起安裝的功能：</span><span class="sxs-lookup"><span data-stu-id="d702e-317">This section lists the installation types, and the features that are installed with each option:</span></span>  
  
-   <span data-ttu-id="d702e-318">**一般**和**完成**選項會安裝為配接器，與相關聯的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-318">The **Typical** and **Complete** options install all the adapters, with the associated data providers.</span></span> <span data-ttu-id="d702e-319">您沒有選擇特定的配接器的安裝的選項。</span><span class="sxs-lookup"><span data-stu-id="d702e-319">You do not have the option of choosing a specific adapter to install.</span></span>  
  
-   <span data-ttu-id="d702e-320">**自訂**選項會與相關聯的資料提供者安裝一或多個介面卡。</span><span class="sxs-lookup"><span data-stu-id="d702e-320">The **Custom** option installs one or more adapters, with the associated data providers.</span></span> <span data-ttu-id="d702e-321">您可以選擇要安裝哪一個配接器。</span><span class="sxs-lookup"><span data-stu-id="d702e-321">You can choose which adapters to install.</span></span> <span data-ttu-id="d702e-322">如果您選擇安裝資料提供者，您也必須安裝對應的配接器。</span><span class="sxs-lookup"><span data-stu-id="d702e-322">If you choose to install a data provider, you must also install the corresponding adapter.</span></span> <span data-ttu-id="d702e-323">不過，您可以安裝配接器，而不需要安裝對應的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-323">However, you can install an adapter without installing the corresponding data provider.</span></span> <span data-ttu-id="d702e-324">這樣做展開**ADO 提供者**節點，然後再選取您不想要安裝的提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-324">Do this by expanding the **ADO Providers** node, and then selecting the providers that you don't want to install.</span></span> <span data-ttu-id="d702e-325">請參閱[以互動模式安裝 BizTalk Adapter Pack](#BKMK_Install_wizard)。</span><span class="sxs-lookup"><span data-stu-id="d702e-325">See [Installing the BizTalk Adapter Pack in Interactive Mode](#BKMK_Install_wizard).</span></span>  
  
     <span data-ttu-id="d702e-326">例如，如果您安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，您也必須安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-326">For example, if you install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], you must also install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="d702e-327">不過，您可以安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]而不需要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-327">However, you can install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] without installing the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span>  
  
<a name="BKMK_Install_Scenarios"></a>   
### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-32-bit-and-64-bit-platforms"></a><span data-ttu-id="d702e-328">在 32 位元和 64 位元平台上安裝 BizTalk Adapter Pack 狀況</span><span class="sxs-lookup"><span data-stu-id="d702e-328">Scenarios for installing the BizTalk Adapter Pack on 32-bit and 64-bit platforms</span></span>  
 <span data-ttu-id="d702e-329">與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]適用於：</span><span class="sxs-lookup"><span data-stu-id="d702e-329">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be used for:</span></span> 
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="d702e-330"> 設計階段 （當產生作業的 LOB 應用程式上的中繼資料）</span><span class="sxs-lookup"><span data-stu-id="d702e-330"> design time (when generating metadata for operations on LOB applications)</span></span>
  
-   <span data-ttu-id="d702e-331">BizTalk Server 管理主控台設計階段 （適用於建立實體連接埠）</span><span class="sxs-lookup"><span data-stu-id="d702e-331">BizTalk Server Administration console design time (for creating physical ports)</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-332">BizTalk Server 管理主控台會以 32 位元 Microsoft Management Console (MMC) 應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="d702e-332">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  
  
-   <span data-ttu-id="d702e-333">BizTalk 執行階段 （傳送和接收訊息時從 LOB 應用程式）</span><span class="sxs-lookup"><span data-stu-id="d702e-333">BizTalk run time (when sending and receiving messages from LOB applications)</span></span>

<span data-ttu-id="d702e-334">您可以使用單一電腦的所有這些 taks，或使用不同的電腦。</span><span class="sxs-lookup"><span data-stu-id="d702e-334">You can use a single computer for all these taks, or use different computers.</span></span> <span data-ttu-id="d702e-335">因為同時[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]和 BizTalk MMC 是 32 位元處理程序，您必須安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]您完成設計階段工作的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d702e-335">Because both [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on the computer where you complete the design-time tasks.</span></span> 

#### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-a-32-bit-platform"></a><span data-ttu-id="d702e-336">在 32 位元平台上安裝 BizTalk Adapter Pack 狀況</span><span class="sxs-lookup"><span data-stu-id="d702e-336">Scenarios for installing the BizTalk Adapter Pack on a 32-bit platform</span></span>  
 <span data-ttu-id="d702e-337">在 32 位元平台上支援的案例包括：</span><span class="sxs-lookup"><span data-stu-id="d702e-337">The supported scenarios on a 32-bit platform include:</span></span>  
  
|<span data-ttu-id="d702e-338">Visual Studio 設計階段的</span><span class="sxs-lookup"><span data-stu-id="d702e-338">For Visual Studio design time</span></span>|<span data-ttu-id="d702e-339">MMC 的 biztalk 設計階段</span><span class="sxs-lookup"><span data-stu-id="d702e-339">For BizTalk MMC design time</span></span>|<span data-ttu-id="d702e-340">Biztalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="d702e-340">For BizTalk run time</span></span>|<span data-ttu-id="d702e-341">Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="d702e-341">For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="d702e-342">安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-342">- Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-343">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-343">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-344">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-344">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="d702e-345">安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-345">- Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-346">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-346">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-347">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-347">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="d702e-348">安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-348">- Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-349">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-349">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-350">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-350">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="d702e-351">安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-351">- Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-352">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-352">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-353">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-353">- Install 32-bit LOB client and other required DLLs.</span></span>|  
  
#### <a name="scenarios-for-installing-the-biztalk-adapter-pack-on-a-64-bit-platform"></a><span data-ttu-id="d702e-354">在 64 位元平台上安裝 BizTalk Adapter Pack 狀況</span><span class="sxs-lookup"><span data-stu-id="d702e-354">Scenarios for installing the BizTalk Adapter Pack on a 64-bit platform</span></span>  
 <span data-ttu-id="d702e-355">在 64 位元平台上支援的案例包括：</span><span class="sxs-lookup"><span data-stu-id="d702e-355">The supported scenarios on a 64-bit platform include:</span></span>  
  
|<span data-ttu-id="d702e-356">Visual Studio 設計階段的</span><span class="sxs-lookup"><span data-stu-id="d702e-356">For Visual Studio design time</span></span>|<span data-ttu-id="d702e-357">MMC 的 biztalk 設計階段</span><span class="sxs-lookup"><span data-stu-id="d702e-357">For BizTalk MMC design time</span></span>|<span data-ttu-id="d702e-358">Biztalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="d702e-358">For BizTalk run time</span></span>|<span data-ttu-id="d702e-359">Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="d702e-359">For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="d702e-360">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-360">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-361">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-361">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-362">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-362">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="d702e-363">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-363">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-364">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-364">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-365">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-365">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="d702e-366">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="d702e-366">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="d702e-367">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-367">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-368">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-368">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-369">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-369">- Install 32-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="d702e-370">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="d702e-370">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="d702e-371">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-371">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-372">安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-372">- Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-373">-安裝 64 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-373">- Install 64-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="d702e-374">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="d702e-374">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="d702e-375">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-375">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-376">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-376">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-377">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-377">- Install 32-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="d702e-378">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="d702e-378">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="d702e-379">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-379">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-380">安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-380">- Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-381">-安裝 64 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-381">- Install 64-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="d702e-382">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-382">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d702e-383">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="d702e-383">- Install 32-bit LOB client and other required DLLs.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d702e-384">任何在電腦上您要執行設計階段工作，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-384">On any computer where you want to do design-time tasks, using either [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="installing-the-biztalk-adapter-pack-in-interactive-mode"></a><span data-ttu-id="d702e-385">以互動模式安裝 BizTalk Adapter Pack</span><span class="sxs-lookup"><span data-stu-id="d702e-385">Installing the BizTalk Adapter Pack in interactive mode</span></span>  
<span data-ttu-id="d702e-386">完成下列步驟來安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="d702e-386">Complete the following steps to install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the setup wizard.</span></span>  
  
1.  <span data-ttu-id="d702e-387">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝媒體上，執行**Setup.exe**。</span><span class="sxs-lookup"><span data-stu-id="d702e-387">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation media, run **Setup.exe**.</span></span>  
  
2.  <span data-ttu-id="d702e-388">選取**安裝 Microsoft BizTalk Adapter**。</span><span class="sxs-lookup"><span data-stu-id="d702e-388">Select **Install Microsoft BizTalk Adapters**.</span></span> <span data-ttu-id="d702e-389">在下一步 視窗中，選取**安裝 Microsoft BizTalk Adapter Pack**或**安裝 Microsoft BizTalk Adapter Pack (x64)**，視您的平台。</span><span class="sxs-lookup"><span data-stu-id="d702e-389">In the next window, select **Install Microsoft BizTalk Adapter Pack** or **Install Microsoft BizTalk Adapter Pack (x64)**, depending on your platform.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-390">如果您要安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]上為虛擬機器，安裝精靈可能會繼續進行通知的安裝程式正在檢查可用磁碟空間的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d702e-390">If you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space.</span></span> <span data-ttu-id="d702e-391">在這種情況下，我們建議您使用無訊息安裝選項。</span><span class="sxs-lookup"><span data-stu-id="d702e-391">In such cases, we recommend that you use the silent installation option.</span></span> <span data-ttu-id="d702e-392">請參閱[以無訊息模式安裝 BizTalk Adapter Pack](#BKMK_SilentInst) （在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="d702e-392">See [Installing the BizTalk Adapter Pack in Silent Mode](#BKMK_SilentInst) (in this topic).</span></span>  
  
3.  <span data-ttu-id="d702e-393">在 歡迎使用畫面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d702e-393">On the Welcome screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="d702e-394">接受使用者授權合約 (EULA)，然後再選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d702e-394">Accept the end-user license agreement (EULA), and then select **Next**.</span></span>  
  
5.  <span data-ttu-id="d702e-395">在**選擇安裝類型**:</span><span class="sxs-lookup"><span data-stu-id="d702e-395">In **Choose Setup Type**:</span></span>  
  
    -   <span data-ttu-id="d702e-396">若要安裝最常見的功能，請選取**一般**。</span><span class="sxs-lookup"><span data-stu-id="d702e-396">To install the most common features, select **Typical**.</span></span>  
  
    -   <span data-ttu-id="d702e-397">若要選取您想要安裝的配接器，請選取**自訂**，然後繼續進行下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="d702e-397">To select the adapters you want to install, select **Custom**, and then proceed to the next step.</span></span>  
  
    -   <span data-ttu-id="d702e-398">若要安裝所有功能，請選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="d702e-398">To install all the features, select **Complete**.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="d702e-399">若要安裝與您的企業應用程式互動，請選取您使用的介面卡**自訂**安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-399">To install only the adapter that you use to interface with your enterprise application, select the **Custom** installation.</span></span>  
  
6. <span data-ttu-id="d702e-400">**需要**只有當您選擇自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-400">**Required** only if you chose the Custom installation.</span></span> <span data-ttu-id="d702e-401">如果您選擇**一般**或**完成**安裝，然後略過此步驟中，並移至步驟 7。</span><span class="sxs-lookup"><span data-stu-id="d702e-401">If you chose the **Typical** or **Complete** installation, then skip this step, and go to step 7.</span></span>  
  
    1.  <span data-ttu-id="d702e-402">在**自訂安裝程式**，依序展開**基底介面卡**若要查看可用的介面卡。</span><span class="sxs-lookup"><span data-stu-id="d702e-402">In **Custom Setup**, expand **Base Adapters** to see the available adapters.</span></span>  
  
    2.  <span data-ttu-id="d702e-403">您不想為配接器，請選取介面卡旁的圖示，然後選取**整個功能將無法使用**。</span><span class="sxs-lookup"><span data-stu-id="d702e-403">For the adapters that you don't want, select the icon next to the adapter, and then select **Entire feature will be unavailable**.</span></span>  
  
    3.  <span data-ttu-id="d702e-404">展開**ADO 提供者**，然後選取您不想要安裝的提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-404">Expand **ADO Providers**, and then select the providers that you don't want to install.</span></span>  
  
    4.  <span data-ttu-id="d702e-405">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d702e-405">Select **Next**.</span></span>  
  
7.  <span data-ttu-id="d702e-406">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="d702e-406">Select **Install**.</span></span>  
  
8.  <span data-ttu-id="d702e-407">在**客戶經驗改進計畫**，您可以選擇註冊。</span><span class="sxs-lookup"><span data-stu-id="d702e-407">In **Customer Experience Improvement Program**, you can choose to enroll.</span></span> <span data-ttu-id="d702e-408">如果您註冊時，您可以與 Microsoft 共用的下列資料：</span><span class="sxs-lookup"><span data-stu-id="d702e-408">If you enroll, you can share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="d702e-409">您要安裝的電腦硬體的相關資料[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-409">Data related to the computer hardware on which you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="d702e-410">資料與企業應用程式版本，您正在使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-410">Data related to the enterprise application versions you are using with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
     <span data-ttu-id="d702e-411">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d702e-411">Select **OK**.</span></span> <span data-ttu-id="d702e-412">[CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699)提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d702e-412">[CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) provides more information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-413">您隨時可以變更此設定處於修復模式，從執行安裝程式**程式**。</span><span class="sxs-lookup"><span data-stu-id="d702e-413">You can always change this setting by running the Setup in Repair mode from **Programs**.</span></span>  
  
9. <span data-ttu-id="d702e-414">選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="d702e-414">Select **Finish**.</span></span>  
  
<a name="BKMK_SilentInst"></a>   
### <a name="installing-the-biztalk-adapter-pack-in-silent-mode"></a><span data-ttu-id="d702e-415">以無訊息模式安裝 BizTalk Adapter Pack</span><span class="sxs-lookup"><span data-stu-id="d702e-415">Installing the BizTalk Adapter Pack in silent mode</span></span>  
 <span data-ttu-id="d702e-416">使用**msiexec**命令來執行無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-416">Use the **msiexec** command to do a silent installation.</span></span> <span data-ttu-id="d702e-417">Msiexec 命令的一部分，請輸入您想要安裝的個別元件。</span><span class="sxs-lookup"><span data-stu-id="d702e-417">As part of the msiexec command, enter the individual components that you want to install.</span></span> <span data-ttu-id="d702e-418">下表列出每個元件中的值[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-418">The following table lists the values for each component in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-419">若要安裝 （移除） 特定元件使用這些值。</span><span class="sxs-lookup"><span data-stu-id="d702e-419">Use these values to install (or remove) specific components.</span></span> <span data-ttu-id="d702e-420">若要安裝 （移除） 多個元件，您可以使用以逗號分隔這些值的組合。</span><span class="sxs-lookup"><span data-stu-id="d702e-420">To install (or remove) more than one component, you can use a combination of these values separated by a comma.</span></span>  
  
|<span data-ttu-id="d702e-421">元件名稱</span><span class="sxs-lookup"><span data-stu-id="d702e-421">Component name</span></span>|<span data-ttu-id="d702e-422">命令列屬性的對應值</span><span class="sxs-lookup"><span data-stu-id="d702e-422">Corresponding value for command-line properties</span></span>|  
|---|---|  
|[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|<span data-ttu-id="d702e-423">DbFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-423">DbFeature</span></span>|  
|[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="d702e-424">OracleEBSFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-424">OracleEBSFeature</span></span>|  
|[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|<span data-ttu-id="d702e-425">SapBaseAdapterFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-425">SapBaseAdapterFeature</span></span>|  
|[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="d702e-426">SiebelBaseAdapterFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-426">SiebelBaseAdapterFeature</span></span>|  
|[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|<span data-ttu-id="d702e-427">SqlFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-427">SqlFeature</span></span>|  
|[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="d702e-428">SapAdoFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-428">SapAdoFeature</span></span><br /><br /> <span data-ttu-id="d702e-429">**請注意**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]也。</span><span class="sxs-lookup"><span data-stu-id="d702e-429">**Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] also.</span></span>|  
|[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="d702e-430">SiebelAdoFeature</span><span class="sxs-lookup"><span data-stu-id="d702e-430">SiebelAdoFeature</span></span><br /><br /> <span data-ttu-id="d702e-431">**請注意**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]也。</span><span class="sxs-lookup"><span data-stu-id="d702e-431">**Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] also.</span></span>|  
|<span data-ttu-id="d702e-432">所有元件</span><span class="sxs-lookup"><span data-stu-id="d702e-432">All components</span></span>|<span data-ttu-id="d702e-433">ALL</span><span class="sxs-lookup"><span data-stu-id="d702e-433">ALL</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="d702e-434">功能名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d702e-434">The feature names are case-sensitive.</span></span>  
  
 <span data-ttu-id="d702e-435">下列步驟說明如何完成的無訊息安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]為不同的元件。</span><span class="sxs-lookup"><span data-stu-id="d702e-435">The following steps show you how to complete a silent installation of [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] for different components.</span></span>  
  
##### <a name="install-in-silent-mode"></a><span data-ttu-id="d702e-436">以無訊息模式安裝</span><span class="sxs-lookup"><span data-stu-id="d702e-436">Install in silent mode</span></span>  
  
1.  <span data-ttu-id="d702e-437">開啟命令提示字元，並移至[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]根中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-437">Open a command prompt, and go to the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] root in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span>  
  
2.  <span data-ttu-id="d702e-438">執行下列命令，根據您想要安裝：</span><span class="sxs-lookup"><span data-stu-id="d702e-438">Run the following commands based on what you want to install:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-439">若要執行無訊息安裝在 x64 架構的平台上，取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`在下列命令。</span><span class="sxs-lookup"><span data-stu-id="d702e-439">To do silent installation on an x64-based platform, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi` in the following commands.</span></span>  
  
    -   <span data-ttu-id="d702e-440">若要執行完整安裝，安裝所有包括.NET Framework 資料提供者的介面卡，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d702e-440">To perform a complete installation, which installs all the adapters including the .NET Framework Data Providers, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
        ```  
  
    -   <span data-ttu-id="d702e-441">只安裝[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-441">To install only the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
        ```  
  
    -   <span data-ttu-id="d702e-442">只安裝[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-442">To install only the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
        ```  
  
    -   <span data-ttu-id="d702e-443">只安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-443">To install only the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="d702e-444">若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]連同[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-444">To install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] along with [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
        ```  
  
    -   <span data-ttu-id="d702e-445">只安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-445">To install only the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="d702e-446">若要安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]連同[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-446">To install the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] along with [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
        ```  
  
    -   <span data-ttu-id="d702e-447">只安裝[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-447">To install only the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
        ```  
  
    -   <span data-ttu-id="d702e-448">若要安裝的所有基底介面卡，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d702e-448">To install all the base adapters, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
        ```  
  
    -   <span data-ttu-id="d702e-449">若要安裝兩個.NET Framework 資料提供者，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d702e-449">To install the two .NET Framework Data Providers, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
        ```  
  
    -   <span data-ttu-id="d702e-450">以逗號分隔之元件的自訂安裝的任何類型。</span><span class="sxs-lookup"><span data-stu-id="d702e-450">Any type of custom installation by separating the components by a comma.</span></span> <span data-ttu-id="d702e-451">例如，若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]與[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，而[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-451">For example, to install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] with the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], and the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="d702e-452">您也可以選擇的 CEIP 註冊為無訊息安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="d702e-452">You can also opt to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="d702e-453">類型：</span><span class="sxs-lookup"><span data-stu-id="d702e-453">Type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
        ```  
  
         <span data-ttu-id="d702e-454">根據預設選項是 false。</span><span class="sxs-lookup"><span data-stu-id="d702e-454">By default the option is false.</span></span> 
  
        > [!IMPORTANT]
        >  <span data-ttu-id="d702e-455">在安裝時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式的評估版，CEIP 的預設選項為 true。</span><span class="sxs-lookup"><span data-stu-id="d702e-455">While installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Evaluation version in silent mode, the default option for CEIP is true.</span></span>  
  
     <span data-ttu-id="d702e-456">如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。</span><span class="sxs-lookup"><span data-stu-id="d702e-456">For more information about the msiexec command type `msiexec` on the command line and press `ENTER`.</span></span> <span data-ttu-id="d702e-457">或移至[ http://go.microsoft.com/fwlink/p/?LinkId=103199 ](http://go.microsoft.com/fwlink/p/?LinkId=103199)。</span><span class="sxs-lookup"><span data-stu-id="d702e-457">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>
  
<a name="BKMK_PostInst"></a>   
### <a name="after-installing-the-biztalk-adapter-pack"></a><span data-ttu-id="d702e-458">安裝 BizTalk Adapter Pack 之後</span><span class="sxs-lookup"><span data-stu-id="d702e-458">After installing the BizTalk Adapter Pack</span></span>  
 <span data-ttu-id="d702e-459">您可能需要在安裝之後，執行下列工作[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，根據您想要使用每張介面卡執行哪些作業：</span><span class="sxs-lookup"><span data-stu-id="d702e-459">You may need to do the following tasks after installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], based on what operations you want to do with each adapter:</span></span>  
  
-   <span data-ttu-id="d702e-460">[設定 Oracle 資料庫配接器使用較新版的 Oracle.DataAccess.dll](#BKMK_ConfigNewOracleDLL) OracleDB 組態檔中。</span><span class="sxs-lookup"><span data-stu-id="d702e-460">[Configure the Oracle Database adapter to use a newer Oracle.DataAccess.dll version](#BKMK_ConfigNewOracleDLL) in the OracleDB configuration file.</span></span>  
  
-   <span data-ttu-id="d702e-461">[建立 SQL Server 資料庫物件 （僅適用於 SAP 配接器）](#BKMK_CreateSQLServer) SAP 系統中叫用交易式 Rfc (tRFCs)。</span><span class="sxs-lookup"><span data-stu-id="d702e-461">[Create SQL Server Database Objects (Only for the SAP Adapter)](#BKMK_CreateSQLServer) to invoke transactional RFCs (tRFCs) in an SAP system.</span></span>  
  
-   <span data-ttu-id="d702e-462">[註冊配接器繫結](#BKMK_Register_Bindings)和.NET Framework 資料提供者安裝精靈時若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="d702e-462">[Register the adapter bindings](#BKMK_Register_Bindings) and the .NET Framework Data Providers if the setup wizard fails to do so.</span></span>  
  
-   <span data-ttu-id="d702e-463">[判斷公開金鑰和版本](#BKMK_PubKey)的不同配接器檔案。</span><span class="sxs-lookup"><span data-stu-id="d702e-463">[Determine the Public Key and Version](#BKMK_PubKey) of the different adapter files.</span></span>  
  
-   <span data-ttu-id="d702e-464">[安裝自訂 Rfc](#BKMK_InstallCustomRFC)如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-464">[Install the Custom RFCs](#BKMK_InstallCustomRFC) if you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span>  
  
<a name="BKMK_ConfigNewOracleDLL"></a>   
#### <a name="configure-the-oracle-database-adapter-to-use-a-newer-oracledataaccessdll-version"></a><span data-ttu-id="d702e-465">設定 Oracle 資料庫配接器使用較新版的 Oracle.DataAccess.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-465">Configure the Oracle Database adapter to use a newer Oracle.DataAccess.dll version</span></span>  
 <span data-ttu-id="d702e-466">當您設定要使用 Wcf-oracledb 配接器，或使用 Visual Studio 使用產生的配接器的連接埠時，會顯示訊息，配接器需要 Oracle.DataAccess.dll 2.111.7.0 版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-466">When you configure a port to use the WCF-OracleDB adapter or use Visual Studio to consume a generated adapter, a message displays that the adapter needs Oracle.DataAccess.dll version 2.111.7.0.</span></span> <span data-ttu-id="d702e-467">若要解決此訊息，請安裝支援的 Oracle.DataAccess.dll 版本 (請參閱[支援版本清單](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx))，然後更新`bindingRedirect`OracleDB 組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-467">To resolve this message, install a supported Oracle.DataAccess.dll version (see [supported version list](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), and then update the `bindingRedirect` element in the OracleDB configuration file.</span></span> <span data-ttu-id="d702e-468">步驟：</span><span class="sxs-lookup"><span data-stu-id="d702e-468">Steps:</span></span>  
  
1.  <span data-ttu-id="d702e-469">在 BizTalk 伺服器上，請移至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="d702e-469">On the BizTalk Server, go to the following folders:</span></span>  
  
     <span data-ttu-id="d702e-470">*磁碟機*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin</span><span class="sxs-lookup"><span data-stu-id="d702e-470">*drive*:\Program Files\Microsoft BizTalk Adapter Pack(x64)\bin</span></span>  
  
     <span data-ttu-id="d702e-471">*磁碟機*: \Program 檔案 (x86) \Microsoft BizTalk Adapter Pack\bin</span><span class="sxs-lookup"><span data-stu-id="d702e-471">*drive*:\Program Files (x86)\Microsoft BizTalk Adapter Pack\bin</span></span>  
  
2.  <span data-ttu-id="d702e-472">開啟 Microsoft.Adapters.OracleDB.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="d702e-472">Open the Microsoft.Adapters.OracleDB.config file.</span></span>  
  
3.  <span data-ttu-id="d702e-473">找不到下列區段，並複製/貼上下列：</span><span class="sxs-lookup"><span data-stu-id="d702e-473">Find the following section, and copy/paste the following:</span></span>  
  
    ```  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
              <dependentAssembly>  
                        <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />  
                        <bindingRedirect oldVersion="2.111.7.00" newVersion="2.112.1.00"/>  
              </dependentAssembly>  
    </assemblyBinding>  
  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-474">在此範例中，我們設定*newVersion* 2.112.1.00 至。</span><span class="sxs-lookup"><span data-stu-id="d702e-474">In this example, we set *newVersion* to 2.112.1.00.</span></span> <span data-ttu-id="d702e-475">此值設為已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-475">Set this value to the version you have installed.</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="d702e-476">如果此群組中有多個 BizTalk 伺服器，請在群組中的所有 BizTalk 伺服器上進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="d702e-476">If there are multiple BizTalk Servers in this group, make this change on all the BizTalk servers in the group.</span></span>  
> -   <span data-ttu-id="d702e-477">*NewVersion*值需要更新 Oracle.DataAccess.dll 檔案的電腦上安裝的版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="d702e-477">The *newVersion* value needs to be updated based on the version of the Oracle.DataAccess.dll file installed on the computer.</span></span>  <span data-ttu-id="d702e-478">Oracle.DataAccess.dll 隨附於您從 Oracle 安裝 Oracle 用戶端。</span><span class="sxs-lookup"><span data-stu-id="d702e-478">Oracle.DataAccess.dll is included with the Oracle Client you install from Oracle.</span></span>  <span data-ttu-id="d702e-479">您只必須安裝 Oracle 用戶端版本， [BizTalk 配接器組件支援](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d702e-479">You must only install an Oracle Client version that is [supported by the BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).</span></span>  
  
<a name="BKMK_CreateSQLServer"></a>   
#### <a name="create-sql-server-database-objects-only-for-the-sap-adapter"></a><span data-ttu-id="d702e-480">建立 SQL Server 資料庫物件 （僅適用於 SAP 配接器）</span><span class="sxs-lookup"><span data-stu-id="d702e-480">Create SQL Server Database objects (only for the SAP adapter)</span></span>  
 <span data-ttu-id="d702e-481">若要啟動 tRFCs SAP 系統中，執行*SapAdapter-DbScript-Install.sql* SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d702e-481">To invoke tRFCs in an SAP system, run the *SapAdapter-DbScript-Install.sql* SQL script.</span></span> <span data-ttu-id="d702e-482">此指令碼會隨[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，並在 SQL Server 中建立資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="d702e-482">This script is installed with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, and creates database objects in SQL Server.</span></span> <span data-ttu-id="d702e-483">指令碼通常會安裝在\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-483">The script is typically installed at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-484">只要您輸入該資料庫名稱來叫用 tRFCs 使用配接器時，您可以針對任何 SQL Server 資料庫，執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="d702e-484">You can run this script against any SQL Server database, as long as you enter that database name while using the adapter to invoke tRFCs.</span></span>  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-adapter-bindings"></a><span data-ttu-id="d702e-485">註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="d702e-485">Register the adapter bindings</span></span>  
 <span data-ttu-id="d702e-486">期間[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，安裝精靈可能無法註冊配接器繫結或.NET Framework Data Provider for mySAP Business Suite，但安裝程式才能繼續使用配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-486">During the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, the setup wizard may fail to register the adapter bindings or the .NET Framework Data Provider for mySAP Business Suite, but setup proceeds with the adapter installation.</span></span> <span data-ttu-id="d702e-487">這可能會造成問題的 Windows Communication Foundation (WCF) 安裝，因為[!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="d702e-487">This might result due to problems with Windows Communication Foundation (WCF) installation, [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span>  
  
<span data-ttu-id="d702e-488">完成這些步驟*只*如果安裝精靈無法註冊在 machine.config 檔案中的配接器繫結或.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-488">Complete these steps *only* if the setup wizard fails to register the adapter bindings or .NET Framework Data Providers in the machine.config file.</span></span>  
  
###### <a name="register-the-adapter-bindings-or-the-net-framework-data-providers"></a><span data-ttu-id="d702e-489">註冊配接器繫結或.NET Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="d702e-489">Register the adapter bindings or the .NET Framework data providers</span></span>  
  
1.  <span data-ttu-id="d702e-490">移至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="d702e-490">Go to the machine.config file on the computer.</span></span> <span data-ttu-id="d702e-491">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="d702e-491">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
2.  <span data-ttu-id="d702e-492">開啟檔案，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="d702e-492">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="d702e-493">註冊配接器繫結：</span><span class="sxs-lookup"><span data-stu-id="d702e-493">Register the adapter bindings:</span></span>  
  
    1.  <span data-ttu-id="d702e-494">搜尋`system.serviceModel`項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-494">Search for the `system.serviceModel` element, and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="d702e-495">搜尋`bindingElementExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-495">Search for the `bindingElementExtensions` element under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="d702e-496">尋找遺漏的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-496">Look for the missing adapter binding.</span></span> <span data-ttu-id="d702e-497">新增下列各節下的`bindingElementExtensions`節點，根據遺失的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-497">Add the following sections under the `bindingElementExtensions` node, depending on the missing adapter binding.</span></span> <span data-ttu-id="d702e-498">如果安裝精靈無法註冊任何，您必須註冊的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-498">You must register all the bindings if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="d702e-499">如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-499">For the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-500">如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-500">For the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-501">如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-501">For the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-502">如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-502">For the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-503">如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-503">For the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="d702e-504">搜尋`bindingExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-504">Search for the `bindingExtensions` element under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="d702e-505">尋找遺漏的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-505">Look for the missing adapter binding.</span></span> <span data-ttu-id="d702e-506">新增下列各節下的`bindingExtensions`節點，根據遺失的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-506">Add the following sections under the `bindingExtensions` node, depending on the missing adapter binding.</span></span> <span data-ttu-id="d702e-507">如果安裝精靈無法註冊任何，您必須註冊的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-507">You must register all the bindings if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="d702e-508">如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-508">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-509">如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-509">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-510">如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-510">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-511">如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-511">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS,Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-512">如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-512">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-513">如需如何判斷公開金鑰資訊，請參閱[判斷公開金鑰和版本](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="d702e-513">For information about how to determine the public key, see [Determine the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="d702e-514">註冊.NET Framework 資料提供者：</span><span class="sxs-lookup"><span data-stu-id="d702e-514">Register the .NET Framework data providers:</span></span>  
  
    1.  <span data-ttu-id="d702e-515">搜尋`DbProviderFactories`system.data 節點下的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-515">Search for the `DbProviderFactories` element under the system.data node.</span></span>  
  
    2.  <span data-ttu-id="d702e-516">尋找遺漏的.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-516">Look for the missing .NET Framework Data Providers.</span></span> <span data-ttu-id="d702e-517">新增下列各節下的`DbProviderFactories`節點，根據遺失的提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-517">Add the following sections under the `DbProviderFactories` node, depending on the missing provider.</span></span> <span data-ttu-id="d702e-518">如果安裝精靈無法註冊任何，您必須註冊所有提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-518">You must register all the providers if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="d702e-519">如[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-519">For the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-520">如[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="d702e-520">For the [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="d702e-521">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="d702e-521">Save and close the machine.config file.</span></span>  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determine-the-public-key-and-version"></a><span data-ttu-id="d702e-522">判斷公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="d702e-522">Determine the Public Key and Version</span></span>  
 <span data-ttu-id="d702e-523">完成下列步驟來判斷公開金鑰和配接器或.NET Framework Data Provider 的版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-523">Complete the following steps to determine the public key and version for an adapter or the .NET Framework Data Provider.</span></span>  
  
###### <a name="determine-the-public-key"></a><span data-ttu-id="d702e-524">判斷公開金鑰</span><span class="sxs-lookup"><span data-stu-id="d702e-524">Determine the public key</span></span>  
  
1.  <span data-ttu-id="d702e-525">移至 Windows 目錄，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="d702e-525">Go to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="d702e-526">以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d702e-526">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="d702e-527">下表列出每個配接器和提供者 Dll 的名稱：</span><span class="sxs-lookup"><span data-stu-id="d702e-527">The following table lists the name of the DLLs for each adapter and provider:</span></span>  
  
    |<span data-ttu-id="d702e-528">配接器/.NET Framework Data Provider</span><span class="sxs-lookup"><span data-stu-id="d702e-528">Adapter/.NET Framework Data Provider</span></span>|<span data-ttu-id="d702e-529">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="d702e-529">Name of the DLL</span></span>|  
    |---|---|  
    |[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|<span data-ttu-id="d702e-530">Microsoft.Adapters.SAP</span><span class="sxs-lookup"><span data-stu-id="d702e-530">Microsoft.Adapters.SAP</span></span>|  
    |[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="d702e-531">Microsoft.Adapters.Siebel</span><span class="sxs-lookup"><span data-stu-id="d702e-531">Microsoft.Adapters.Siebel</span></span>|  
    |[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|<span data-ttu-id="d702e-532">Microsoft.Adapters.OracleDB</span><span class="sxs-lookup"><span data-stu-id="d702e-532">Microsoft.Adapters.OracleDB</span></span>|  
    |[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="d702e-533">Microsoft.Adapters.OracleEBS</span><span class="sxs-lookup"><span data-stu-id="d702e-533">Microsoft.Adapters.OracleEBS</span></span>|  
    |[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|<span data-ttu-id="d702e-534">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="d702e-534">Microsoft.Adapters.Sql.dll</span></span>|  
    |[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="d702e-535">Microsoft.Data.SAPClient</span><span class="sxs-lookup"><span data-stu-id="d702e-535">Microsoft.Data.SAPClient</span></span>|  
    |[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="d702e-536">Microsoft.Data.SiebelClient</span><span class="sxs-lookup"><span data-stu-id="d702e-536">Microsoft.Data.SiebelClient</span></span>|  
  
3.  <span data-ttu-id="d702e-537">在**一般**索引標籤上，**公開金鑰語彙基元**值是 DLL 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="d702e-537">On the **General** tab, the **Public Key Token** values is the public key for the DLL.</span></span> <span data-ttu-id="d702e-538">**版本**值是 DLL 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d702e-538">The **Version** value is the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="d702e-539">複製的公開金鑰，然後選取**取消**。</span><span class="sxs-lookup"><span data-stu-id="d702e-539">Copy the public key, and then select **Cancel**.</span></span>  
  
<a name="BKMK_InstallCustomRFC"></a>   
#### <a name="install-the-custom-rfcs"></a><span data-ttu-id="d702e-540">安裝自訂的 Rfc</span><span class="sxs-lookup"><span data-stu-id="d702e-540">Install the custom RFCs</span></span>  
 <span data-ttu-id="d702e-541">您只需要執行這項工作，如果您想要使用[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-541">You only need to do this task if you want to use the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="d702e-542">如需安裝自訂 Rfc 的指示，請參閱[安裝自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)中[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="d702e-542">For instructions on installing custom RFCs, see [Install Custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) in the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="d702e-543">如果您使用較早版本所提供的自訂 Rfc 的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，則您必須將它們升級為此版本提供的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d702e-543">If you are using an earlier version of the custom RFCs provided with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], then you must upgrade them to the RFCs provided with this release.</span></span> <span data-ttu-id="d702e-544">藉由移除舊版的 Rfc，執行這項操作，然後安裝 Rfc 隨附於此版本。</span><span class="sxs-lookup"><span data-stu-id="d702e-544">Do this by removing the earlier RFCs, and then installing the RFCs shipped with this release.</span></span>  

## <a name="installing-the-enterprise-applications"></a><span data-ttu-id="d702e-545">安裝企業應用程式</span><span class="sxs-lookup"><span data-stu-id="d702e-545">Installing the Enterprise Applications</span></span>  
<span data-ttu-id="d702e-546">步驟和指示，以安裝不同的企業部署 LOB 系統，我們會引導您使用其特定安裝 recommendnd。</span><span class="sxs-lookup"><span data-stu-id="d702e-546">For the steps and guidance to install the different enterprise LOB systems, we recommendnd you use their specific installation guides.</span></span> <span data-ttu-id="d702e-547">如果有的話，也參照特定的組態變更，及其配接器文件。</span><span class="sxs-lookup"><span data-stu-id="d702e-547">Also refer to its adapter documentation for specific configuration changes, if any.</span></span>   

## <a name="installation-and-post-installation-checklist"></a><span data-ttu-id="d702e-548">安裝及安裝後的檢查清單</span><span class="sxs-lookup"><span data-stu-id="d702e-548">Installation and post-installation checklist</span></span>  
  
-   <span data-ttu-id="d702e-549">請確定您已安裝所有[軟體必要條件](#BKMK_Prereqs)使用正確的安裝選項。</span><span class="sxs-lookup"><span data-stu-id="d702e-549">Make sure you installed all the [software prerequisites](#BKMK_Prereqs) with the correct installation option.</span></span>
  
-   <span data-ttu-id="d702e-550">請確定您已安裝在電腦上安裝企業 LOB 應用程式的支援的版本[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-550">Make sure you have the supported version of the enterprise LOB applications installed on your computer where you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-551">請參閱[支援企業應用程式版本](#BKMK_SuppLOB)。</span><span class="sxs-lookup"><span data-stu-id="d702e-551">See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</span></span>  
  
-   <span data-ttu-id="d702e-552">若要安裝的企業 LOB 系統，您想要連接的介面卡，請確定您已安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用**自訂**安裝選項。</span><span class="sxs-lookup"><span data-stu-id="d702e-552">To install only the adapter for the enterprise LOB system you want to connect, make sure you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the **Custom** installation option.</span></span> <span data-ttu-id="d702e-553">請確定您並未安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用**完成**安裝選項。</span><span class="sxs-lookup"><span data-stu-id="d702e-553">Make sure you have not installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the **Complete** installation option.</span></span> <span data-ttu-id="d702e-554">請參閱[安裝 BizTalk Adapter Pack](#BKMK_Install_Adap)。</span><span class="sxs-lookup"><span data-stu-id="d702e-554">See [Installing the BizTalk Adapter Pack](#BKMK_Install_Adap).</span></span>  
  
-   <span data-ttu-id="d702e-555">如果您想要進行 tRFC 呼叫 SAP 系統使用[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，請確定您在 SQL Server 資料庫中建立必要的資料表。</span><span class="sxs-lookup"><span data-stu-id="d702e-555">If you want to make tRFC calls to the SAP system using the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], make sure you create the required tables in a SQL Server database.</span></span> <span data-ttu-id="d702e-556">請參閱[安裝 BizTalk Adapter Pack 之後](#BKMK_PostInst)。</span><span class="sxs-lookup"><span data-stu-id="d702e-556">See [After Installing the BizTalk Adapter Pack](#BKMK_PostInst).</span></span>
  
-   <span data-ttu-id="d702e-557">執行時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝精靈中，您可能會收到錯誤訊息，表示安裝程式無法註冊繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-557">While running the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup wizard, you may get an error message that states the setup failed to register the bindings.</span></span> <span data-ttu-id="d702e-558">如果是的話，手動註冊它們。</span><span class="sxs-lookup"><span data-stu-id="d702e-558">If so, register them manually.</span></span> <span data-ttu-id="d702e-559">請參閱[安裝 BizTalk Adapter Pack 之後](#BKMK_PostInst)。</span><span class="sxs-lookup"><span data-stu-id="d702e-559">See [After Installing the BizTalk Adapter Pack](#BKMK_PostInst).</span></span>  
  
-   <span data-ttu-id="d702e-560">如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]一部分[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，請確定您已安裝自訂 Rfc SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="d702e-560">If you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure you install the custom RFCs on the SAP system.</span></span> <span data-ttu-id="d702e-561">請參閱[安裝 BizTalk Adapter Pack 之後](#BKMK_PostInst)。</span><span class="sxs-lookup"><span data-stu-id="d702e-561">See [After Installing the BizTalk Adapter Pack](#BKMK_PostInst).</span></span>  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="change-the-biztalk-adapter-pack-installation"></a><span data-ttu-id="d702e-562">變更 BizTalk Adapter Pack 安裝</span><span class="sxs-lookup"><span data-stu-id="d702e-562">Change the BizTalk Adapter Pack installation</span></span>  
 <span data-ttu-id="d702e-563">完成下列步驟來變更[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-563">Complete the following steps to change the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span> <span data-ttu-id="d702e-564">請確定您有[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝您執行安裝精靈來修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-564">Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="d702e-565">您可以修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝在互動模式 （安裝精靈中），或以無訊息模式 （命令列）。</span><span class="sxs-lookup"><span data-stu-id="d702e-565">You can modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in interactive mode (the setup wizard), or in silent mode (the command line).</span></span>
  
#### <a name="change-the-bap-installation-in-interactive-mode"></a><span data-ttu-id="d702e-566">變更以互動模式 BAP 安裝</span><span class="sxs-lookup"><span data-stu-id="d702e-566">Change the BAP installation in interactive mode</span></span>  
  
1.  <span data-ttu-id="d702e-567">使用 BizTalk Server 系統管理員群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="d702e-567">Sign in using an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="d702e-568">在**程式和功能**，選取**解除安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="d702e-568">In **Programs and features**, select **Uninstall a program**.</span></span>  
  
3.  <span data-ttu-id="d702e-569">以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="d702e-569">Right-click **Microsoft BizTalk Adapter Pack**, and then select **Change**.</span></span>  
  
4.  <span data-ttu-id="d702e-570">在 歡迎使用畫面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d702e-570">On the Welcome screen, select **Next**.</span></span>  
  
5.  <span data-ttu-id="d702e-571">在**變更、 修復或移除安裝**:</span><span class="sxs-lookup"><span data-stu-id="d702e-571">In **Change, repair, or remove installation**:</span></span>  
  
    -   <span data-ttu-id="d702e-572">若要選取您想要安裝的元件，請選取**變更**並移至步驟 6。</span><span class="sxs-lookup"><span data-stu-id="d702e-572">To select the components you want to install, select **Change** and go to Step 6.</span></span>  
  
    -   <span data-ttu-id="d702e-573">若要修復最近安裝中的錯誤，請選取**修復**並移至步驟 7。</span><span class="sxs-lookup"><span data-stu-id="d702e-573">To repair errors in the most recent installation, select **Repair** and go to Step 7.</span></span>  
  
    -   <span data-ttu-id="d702e-574">若要移除 Microsoft[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從電腦中，選取**移除**然後移至步驟 10。</span><span class="sxs-lookup"><span data-stu-id="d702e-574">To remove Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from the computer, select **Remove** and then go to Step 10.</span></span>  
  
6.  <span data-ttu-id="d702e-575">如果您選擇修改安裝：</span><span class="sxs-lookup"><span data-stu-id="d702e-575">If you chose to modify the installation:</span></span>  
  
    -   <span data-ttu-id="d702e-576">展開**Microsoft BizTalk Adapter Pack**節點，選擇要安裝的基底介面卡、.NET Framework 資料提供者，或兩者。</span><span class="sxs-lookup"><span data-stu-id="d702e-576">Expand the **Microsoft BizTalk Adapter Pack** node to choose to install the base adapters, the .NET Framework Data Providers, or both.</span></span>  
  
    -   <span data-ttu-id="d702e-577">展開**基底介面卡**節點，選擇要安裝的所有介面卡或特定介面卡。</span><span class="sxs-lookup"><span data-stu-id="d702e-577">Expand the **Base Adapters** node to choose to install all the adapters or specific adapters.</span></span>  
  
    -   <span data-ttu-id="d702e-578">展開**ADO 提供者**節點，選擇要安裝所有的提供者或特定的提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-578">Expand the **ADO Providers** node to choose to install all the providers or specific providers.</span></span>  
  
    -   <span data-ttu-id="d702e-579">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d702e-579">Select **Next**.</span></span>  
  
    -   <span data-ttu-id="d702e-580">選取**變更**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="d702e-580">Select **Change**, and then select **Finish**.</span></span>  
  
7.  <span data-ttu-id="d702e-581">如果您選擇要在修復安裝，**準備好修復 Microsoft BizTalk Adapter Pack**對話方塊中，選取**修復**。</span><span class="sxs-lookup"><span data-stu-id="d702e-581">If you chose to repair the installation, in the **Ready to repair Microsoft BizTalk Adapter Pack** dialog box, select **Repair**.</span></span> <span data-ttu-id="d702e-582">精靈會啟動修復安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-582">The wizard starts repairing the installation.</span></span>  
  
8.  <span data-ttu-id="d702e-583">若有需要，變更您的喜好設定有關選擇加入 ceip，，然後選取 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d702e-583">If required, change your preferences regarding opting for CEIP, and then select **OK**.</span></span> 
  
9. <span data-ttu-id="d702e-584">選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="d702e-584">Select **Finish**.</span></span>  
  
10. <span data-ttu-id="d702e-585">如果您選擇要移除介面卡，在**準備好要移除 Microsoft BizTalk Adapter Pack**對話方塊中，選取**移除**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="d702e-585">If you chose to remove the adapters, in the **Ready to remove Microsoft BizTalk Adapter Pack** dialog box, select **Remove**, and then select **Finish**.</span></span>  
  
#### <a name="change-the-bap-installation-in-silent-mode"></a><span data-ttu-id="d702e-586">變更 BAP 安裝以無訊息模式</span><span class="sxs-lookup"><span data-stu-id="d702e-586">Change the BAP installation in silent mode</span></span>  
  
1.  <span data-ttu-id="d702e-587">開啟命令提示字元，並移至的根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d702e-587">Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="d702e-588">執行類似下列的命令：</span><span class="sxs-lookup"><span data-stu-id="d702e-588">Run a command similar to the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-589">若要修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]x64 平台上，在下列命令，以無訊息模式安裝取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`。</span><span class="sxs-lookup"><span data-stu-id="d702e-589">To modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in a silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.</span></span>  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
    ```  
  
     <span data-ttu-id="d702e-590">此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，並安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-590">This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], and installs the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span></span>  
  
     <span data-ttu-id="d702e-591">使用不同的值`REMOVE`和`ADDLOCAL`屬性，您可以新增或移除特定元件。</span><span class="sxs-lookup"><span data-stu-id="d702e-591">By using different values for the `REMOVE` and `ADDLOCAL` properties, you can add or remove specific components.</span></span> <span data-ttu-id="d702e-592">中的資料表是指[以無訊息模式安裝 BizTalk Adapter Pack](#BKMK_SilentInst) （在本主題） 有關您可以使用這些屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d702e-592">Refer to the table in [Installing the BizTalk Adapter Pack in Silent Mode](#BKMK_SilentInst) (in this topic) for information about the values that you can use for these properties.</span></span>  
  
     <span data-ttu-id="d702e-593">您也可以使用 /f 選項 msiexec 命令的一部分來執行無訊息的修復。</span><span class="sxs-lookup"><span data-stu-id="d702e-593">You can also do a silent repair by using the /f option as part of the msiexec command.</span></span> <span data-ttu-id="d702e-594">例如：</span><span class="sxs-lookup"><span data-stu-id="d702e-594">For example:</span></span>  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn /f  
    ```  
  
     <span data-ttu-id="d702e-595">您可以使用各種不同的組合使用 /f 選項。</span><span class="sxs-lookup"><span data-stu-id="d702e-595">You can use various different combinations with the /f option.</span></span> <span data-ttu-id="d702e-596">如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。</span><span class="sxs-lookup"><span data-stu-id="d702e-596">For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="d702e-597">或移至[ http://go.microsoft.com/fwlink/p/?LinkId=103199 ](http://go.microsoft.com/fwlink/p/?LinkId=103199)。</span><span class="sxs-lookup"><span data-stu-id="d702e-597">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d702e-598">修改時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇加入或退出 CEIP。</span><span class="sxs-lookup"><span data-stu-id="d702e-598">While modifying the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="d702e-599">即使您明確地設定為 true 或 false CEIP_OPTIN 安裝會保持在您選擇喜好設定。</span><span class="sxs-lookup"><span data-stu-id="d702e-599">The preferences you chose during the installation remains, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="removing-the-biztalk-adapter-pack"></a><span data-ttu-id="d702e-600">移除 BizTalk Adapter Pack</span><span class="sxs-lookup"><span data-stu-id="d702e-600">Removing the BizTalk Adapter Pack</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d702e-601">如果您使用的 tRFC 功能的 SQL Server 資料庫中建立資料表[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，您必須手動移除之後再移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-601">If you created tables in the SQL Server database to work with the tRFC feature of the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], you must manually remove them before removing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-602">[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝會複製 SapAdapter-DbScript-Uninstall.sql 檔案通常位於\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-602">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation copies a SapAdapter-DbScript-Uninstall.sql file typically at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-603">執行這個檔案來移除您所建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="d702e-603">Run this file to remove the tables you created.</span></span>  
  
<span data-ttu-id="d702e-604">完成下列步驟來移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="d702e-604">Complete the following steps to remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from your computer.</span></span> <span data-ttu-id="d702e-605">請確定您有[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝您執行安裝精靈來移除介面卡。</span><span class="sxs-lookup"><span data-stu-id="d702e-605">Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the adapters.</span></span>  
  
 <span data-ttu-id="d702e-606">您可以移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以互動模式 （安裝程式精靈），或以無訊息模式 （命令列）。</span><span class="sxs-lookup"><span data-stu-id="d702e-606">You can remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode (setup wizard), or in silent mode (command line).</span></span>
  
#### <a name="uninstall-the-biztalk-adapter-pack-in-interactive-mode"></a><span data-ttu-id="d702e-607">解除安裝 BizTalk Adapter Pack，以互動模式</span><span class="sxs-lookup"><span data-stu-id="d702e-607">Uninstall the BizTalk Adapter Pack in interactive mode</span></span>  
  
1.  <span data-ttu-id="d702e-608">在**程式和功能**，選取**解除安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="d702e-608">In **Programs and features**, select **Uninstall a program**.</span></span>  
  
2.  <span data-ttu-id="d702e-609">以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="d702e-609">Right-click **Microsoft BizTalk Adapter Pack**, and then select **Uninstall**.</span></span>  
  
#### <a name="uninstall-the-biztalk-adapter-pack-in-silent-mode"></a><span data-ttu-id="d702e-610">解除安裝 BizTalk Adapter Pack，以無訊息模式</span><span class="sxs-lookup"><span data-stu-id="d702e-610">Uninstall the BizTalk Adapter Pack in silent mode</span></span>  
  
1.  <span data-ttu-id="d702e-611">開啟命令提示字元，並移至的根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d702e-611">Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="d702e-612">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d702e-612">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d702e-613">若要移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在 x64 平台上，下列命令，在無訊息模式取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`。</span><span class="sxs-lookup"><span data-stu-id="d702e-613">To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.</span></span>  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
    ```  
  
     <span data-ttu-id="d702e-614">此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-614">This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span>  
  
     <span data-ttu-id="d702e-615">藉由提供不同的值`REMOVE`屬性，您可以移除特定元件從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="d702e-615">By providing different values for the `REMOVE` property, you can remove specific components from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span> <span data-ttu-id="d702e-616">中的資料表是指[以無訊息模式安裝 BizTalk Adapter Pack](#BKMK_SilentInst) （在本主題） 有關您可以使用這個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d702e-616">Refer to the table in [Installing the BizTalk Adapter Pack in Silent Mode](#BKMK_SilentInst) (in this topic) for information about the values that you can use for this property.</span></span>  
  
     <span data-ttu-id="d702e-617">若要完全移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d702e-617">To completely remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], execute the following command:</span></span>  
  
    ```  
    msiexec /x AdaptersSetup.msi /qn  
    ```  
  
     <span data-ttu-id="d702e-618">如需有關 msiexec 命令類型`msiexec`命令列，然後按上`ENTER`。</span><span class="sxs-lookup"><span data-stu-id="d702e-618">For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="d702e-619">或移至[ http://go.microsoft.com/fwlink/p/?LinkId=103199 ](http://go.microsoft.com/fwlink/p/?LinkId=103199)。</span><span class="sxs-lookup"><span data-stu-id="d702e-619">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>
  
<a name="BKMK_PostRemove"></a>   
### <a name="after-removing-the-biztalk-adapter-pack"></a><span data-ttu-id="d702e-620">移除 BizTalk Adapter Pack 之後</span><span class="sxs-lookup"><span data-stu-id="d702e-620">After removing the BizTalk Adapter Pack</span></span>  
 <span data-ttu-id="d702e-621">您可能需要執行下列步驟移除後[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d702e-621">You may need to perform the following steps after removing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="d702e-622">如果安裝精靈無法執行這項操作，移除配接器繫結或.NET Framework 資料提供者註冊，</span><span class="sxs-lookup"><span data-stu-id="d702e-622">Remove the adapter bindings or the .NET Framework Data Provider registration, if the setup wizard failed to do so</span></span>
  
-   <span data-ttu-id="d702e-623">移除自訂 Rfc，如果您選擇要安裝 [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d702e-623">Remove the custom RFCs, if you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]</span></span>
  
<a name="BKMK_Remove_Binding"></a>   
#### <a name="remove-the-bindings-or-the-net-framework-data-provider-registration"></a><span data-ttu-id="d702e-624">移除繫結或.NET Framework 資料提供者登錄</span><span class="sxs-lookup"><span data-stu-id="d702e-624">Remove the bindings or the .NET Framework Data Provider registration</span></span>  
 <span data-ttu-id="d702e-625">完成這些步驟*只*如果安裝精靈無法移除 machine.config 檔中的配接器繫結或.NET Framework 資料提供者註冊。</span><span class="sxs-lookup"><span data-stu-id="d702e-625">Complete these steps *only* if the setup wizard fails to remove the adapter bindings or .NET Framework Data Provider registration from the machine.config file.</span></span>  
  
###### <a name="remove-the-adapter-bindings-or-net-framework-data-provider-registration"></a><span data-ttu-id="d702e-626">移除配接器繫結或.NET Framework 資料提供者登錄</span><span class="sxs-lookup"><span data-stu-id="d702e-626">Remove the adapter bindings or .NET Framework Data Provider registration</span></span>  
  
1.  <span data-ttu-id="d702e-627">移至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="d702e-627">Go to the machine.config file on the computer.</span></span> <span data-ttu-id="d702e-628">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="d702e-628">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
2.  <span data-ttu-id="d702e-629">開啟檔案，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="d702e-629">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="d702e-630">移除配接器繫結註冊：</span><span class="sxs-lookup"><span data-stu-id="d702e-630">Remove the adapter binding registration:</span></span>  
  
    1.  <span data-ttu-id="d702e-631">搜尋`system.serviceModel`項目，並移除下列項目底下：</span><span class="sxs-lookup"><span data-stu-id="d702e-631">Search for the `system.serviceModel` element, and remove the following from under the element:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  <span data-ttu-id="d702e-632">搜尋`bindingElementExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-632">Search for the `bindingElementExtensions` element under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="d702e-633">移除下列各節下的`bindingElementExtensions`節點，根據可用的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-633">Remove the following sections under the `bindingElementExtensions` node, depending on the available adapter binding.</span></span> <span data-ttu-id="d702e-634">如果安裝精靈會移除任何失敗，您必須移除所有的繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-634">You must remove all the bindings if the setup wizard fails to remove any.</span></span>  
  
         <span data-ttu-id="d702e-635">如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-635">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-636">如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-636">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-637">如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-637">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-638">如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-638">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-639">如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-639">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="d702e-640">搜尋`bindingExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-640">Search for the `bindingExtensions` element under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="d702e-641">移除下列各節下的`bindingExtensions`節點，根據可用的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-641">Remove the following sections under the `bindingExtensions` node, depending on the available adapter binding.</span></span> <span data-ttu-id="d702e-642">如果安裝精靈會移除任何失敗，您必須移除所有的繫結。</span><span class="sxs-lookup"><span data-stu-id="d702e-642">You must remove all the bindings if the setup wizard fails to remove any.</span></span>  
  
         <span data-ttu-id="d702e-643">如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-643">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-644">如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-644">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-645">如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-645">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-646">如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-646">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-647">如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-647">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  <span data-ttu-id="d702e-648">移除.NET Framework 資料提供者的登錄：</span><span class="sxs-lookup"><span data-stu-id="d702e-648">Remove the .NET Framework Data Provider registration:</span></span>  
  
    -   <span data-ttu-id="d702e-649">搜尋`DbProviderFactories`system.data 節點下的項目。</span><span class="sxs-lookup"><span data-stu-id="d702e-649">Search for the `DbProviderFactories` element under the system.data node.</span></span>  
  
    -   <span data-ttu-id="d702e-650">尋找中仍登錄的.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-650">Look for the .NET Framework Data Providers that are still registered.</span></span> <span data-ttu-id="d702e-651">移除下列各節下的`DbProviderFactories`節點，根據現有的.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-651">Remove the following sections under the `DbProviderFactories` node, depending on the existing .NET Framework Data Providers.</span></span> <span data-ttu-id="d702e-652">如果有的話，您必須移除所有的提供者。</span><span class="sxs-lookup"><span data-stu-id="d702e-652">You must remove all the providers if they exist.</span></span>  
  
         <span data-ttu-id="d702e-653">如[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-653">For [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="d702e-654">如[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="d702e-654">For [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="d702e-655">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="d702e-655">Save and close the machine.config file.</span></span>  
  
<a name="BKMK_Remove_SAP_Pro"></a>   
#### <a name="remove-the-custom-rfcs"></a><span data-ttu-id="d702e-656">移除自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="d702e-656">Remove the custom RFCs</span></span>  
<span data-ttu-id="d702e-657">完成此步驟，移除您安裝在 SAP 系統的自訂 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d702e-657">Complete this step to remove the custom RFCs that you installed in the SAP system.</span></span> <span data-ttu-id="d702e-658">請參閱[安裝或移除自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="d702e-658">See [Install or remove custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
## <a name="troubleshoot-biztalk-adapter-pack-installation"></a><span data-ttu-id="d702e-659">BizTalk Adapter Pack 安裝問題疑難排解</span><span class="sxs-lookup"><span data-stu-id="d702e-659">Troubleshoot BizTalk Adapter Pack installation</span></span>  
 <span data-ttu-id="d702e-660">以下是安裝時，您可能會面臨一些問題[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d702e-660">Following are some issues that you might face when installing [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d702e-661">安裝相關問題的完整清單，請參閱**疑難排解**每個配接器的主題。</span><span class="sxs-lookup"><span data-stu-id="d702e-661">For a comprehensive list of installation-related issues, refer to **Troublehsooting** topics for each adapter.</span></span>  
  
-   <span data-ttu-id="d702e-662">**在 64 位元電腦上的執行安裝程式可能會擲回錯誤存取結構描述檔案時發生**</span><span class="sxs-lookup"><span data-stu-id="d702e-662">**Running setup on a 64-bit computer might throw an error while accessing schema file**</span></span>  
  
     <span data-ttu-id="d702e-663">[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝存取時擲回錯誤**Microsoft.Adapters。*\<AdapterName\>*_schema.xml**檔案，但配接器的安裝會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="d702e-663">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup throws an error while accessing the **Microsoft.Adapters.*\<AdapterName\>*_schema.xml** file, but proceeds with the adapter installation.</span></span>  
  
     <span data-ttu-id="d702e-664">**原因**</span><span class="sxs-lookup"><span data-stu-id="d702e-664">**Cause**</span></span>  
  
     <span data-ttu-id="d702e-665">如果 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]已安裝的相同電腦上，目標結構描述所用的檔案都相同。</span><span class="sxs-lookup"><span data-stu-id="d702e-665">If both 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] are installed on the same computer, the target schema file used by both is the same.</span></span> <span data-ttu-id="d702e-666">如此一來，檔案安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]64 位元安裝程式會嘗試存取權限時，可能是由 IIS 所使用。</span><span class="sxs-lookup"><span data-stu-id="d702e-666">As a result, the file installed by the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] might be in use by IIS when the 64-bit installer tries to access it.</span></span>  
  
     <span data-ttu-id="d702e-667">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d702e-667">**Resolution**</span></span>  
  
     <span data-ttu-id="d702e-668">手動複製**Microsoft.Adapters。*\<AdapterName\>*_schema.xml**檔案從`C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas`」 至`C:\Windows\System32\inetsrv\config\schema`。</span><span class="sxs-lookup"><span data-stu-id="d702e-668">Manually copy the **Microsoft.Adapters.*\<AdapterName\>*_schema.xml** file from `C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas`" to `C:\Windows\System32\inetsrv\config\schema`.</span></span>  