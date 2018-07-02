---
title: 關於.NET Framework Data Provider for mySAP Business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS
- EXEC query
- SELECT query
- SAPDiscoveredObjects.xml
- SQL Server Integration Services
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- custom RFC
- Visual Studio DDEX plug-in
ms.assetid: 4832f789-c1d8-4c5d-a49d-b1da6b7d4bd4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ee712f6b818b94ca731d94165cd345a3249a61d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978911"
---
# <a name="about-the-net-framework-data-provider-for-mysap-business-suite"></a><span data-ttu-id="a86c1-102">關於.NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="a86c1-102">About the .NET Framework Data Provider for mySAP Business Suite</span></span>
<span data-ttu-id="a86c1-103">本節提供有關資訊[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) 和它的功能。</span><span class="sxs-lookup"><span data-stu-id="a86c1-103">This section provides information about the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) and its features.</span></span> <span data-ttu-id="a86c1-104">如需有關如何使用指示[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱 <<c2> [ 使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="a86c1-104">For instructions about how to use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a86c1-105">即使您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]的一部分[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，您[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]是仍未完成，直到您安裝的自訂 RFC，SAP 系統中。</span><span class="sxs-lookup"><span data-stu-id="a86c1-105">Even if you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, your [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] is still incomplete until you install a custom RFC in the SAP system.</span></span> <span data-ttu-id="a86c1-106">如需有關如何安裝自訂 RFC 的指示，請參閱 <<c0> [ 安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="a86c1-106">For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
 <span data-ttu-id="a86c1-107">您可以使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]如下：</span><span class="sxs-lookup"><span data-stu-id="a86c1-107">You can use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] in the following ways:</span></span>  
  
- <span data-ttu-id="a86c1-108">要寫入的 ADO.NET 用戶端連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="a86c1-108">To write an ADO.NET client to connect to the SAP system.</span></span> <span data-ttu-id="a86c1-109">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]公開特定類別，可讓您與提供者介面。</span><span class="sxs-lookup"><span data-stu-id="a86c1-109">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] exposes certain classes that enable you to interface with the provider.</span></span>  
  
- <span data-ttu-id="a86c1-110">若要在 SAP 系統上執行 SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="a86c1-110">To execute a SELECT query on the SAP system.</span></span> <span data-ttu-id="a86c1-111">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]這項功能會使用自訂的 RFC。</span><span class="sxs-lookup"><span data-stu-id="a86c1-111">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses the custom RFC for this feature.</span></span>  
  
- <span data-ttu-id="a86c1-112">若要執行 SAP 系統上的執行作業。</span><span class="sxs-lookup"><span data-stu-id="a86c1-112">To execute an EXEC operation on the SAP system.</span></span> <span data-ttu-id="a86c1-113">SAP 系統上執行查詢，您可以使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="a86c1-113">You can use this operation to perform queries on the SAP system.</span></span>  
  
- <span data-ttu-id="a86c1-114">若要執行 SAP 系統上的 EXECQUERY 作業。</span><span class="sxs-lookup"><span data-stu-id="a86c1-114">To execute an EXECQUERY operation on the SAP system.</span></span> <span data-ttu-id="a86c1-115">您可以使用這項作業來執行 SAP 系統中已定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="a86c1-115">You can use this operation to execute queries that are already defined in the SAP system.</span></span>  
  
- <span data-ttu-id="a86c1-116">接著，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]DDEX 外掛程式，以便在介面資料表和函式模組從 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="a86c1-116">To, in turn, use the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in to surface tables and function modules from the SAP system.</span></span> <span data-ttu-id="a86c1-117">從 SAP 系統探索到的物件名稱會寫入至組態檔，SAPDiscoveredObjects.xml。</span><span class="sxs-lookup"><span data-stu-id="a86c1-117">The names of the objects discovered from the SAP system are written to a configuration file, SAPDiscoveredObjects.xml.</span></span>  
  
- <span data-ttu-id="a86c1-118">若要使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]與 SQL Server Integration Services (SSIS)。</span><span class="sxs-lookup"><span data-stu-id="a86c1-118">To use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Integration Services (SSIS).</span></span>  
  
- <span data-ttu-id="a86c1-119">若要使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]與 SQL Server Reporting Services (SSRS)。</span><span class="sxs-lookup"><span data-stu-id="a86c1-119">To use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Reporting Services (SSRS).</span></span>  
  
  <span data-ttu-id="a86c1-120">如需有關如何執行這些工作的詳細資訊，請參閱 <<c0> [ 使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="a86c1-120">For more information about performing these tasks, see [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).</span></span> <span data-ttu-id="a86c1-121">如需有關自訂 RFC、 SAPDiscoveredObjects.xml 組態檔和相關聯的限制[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="a86c1-121">For more information about the custom RFC, the SAPDiscoveredObjects.xml configuration file, and the limitations associated with the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see the following links.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a86c1-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="a86c1-122">In This Section</span></span>  
  
-   [<span data-ttu-id="a86c1-123">在 SAP 中的提供者所使用的自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="a86c1-123">Custom RFCs Used by the Provider in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/custom-rfcs-used-by-the-provider-in-sap.md)  
  
-   [<span data-ttu-id="a86c1-124">關於 SAPDiscoveredObjects.xml 檔案，在 SAP 中</span><span class="sxs-lookup"><span data-stu-id="a86c1-124">About the SAPDiscoveredObjects.xml File in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)  
  
-   [<span data-ttu-id="a86c1-125">.NET Framework Data Provider for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="a86c1-125">Limitations of the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/limitations-of-the-net-framework-data-provider-for-mysap-business-suite.md)