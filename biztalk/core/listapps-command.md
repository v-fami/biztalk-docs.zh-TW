---
title: ListApps 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a5eb0af-e153-4639-a6c0-56c951827c7c
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 785d98655cbe1ef32c00120dc1e54227717ebcae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262158"
---
# <a name="listapps-command"></a><span data-ttu-id="4ecd2-102">ListApps 命令</span><span class="sxs-lookup"><span data-stu-id="4ecd2-102">ListApps Command</span></span>
<span data-ttu-id="4ecd2-103">將指定的 BizTalk 管理資料庫中所有 BizTalk 應用程式的名稱和描述列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-103">Prints to the console the name and description of all of the BizTalk applications in the specified BizTalk Management database.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="4ecd2-104">使用方式</span><span class="sxs-lookup"><span data-stu-id="4ecd2-104">Usage</span></span>  
 <span data-ttu-id="4ecd2-105">**BTSTask ListApps** [**/Server:***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="4ecd2-105">**BTSTask ListApps** [**/Server:***value*] [**/Database:***value*]</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="4ecd2-106">參數</span><span class="sxs-lookup"><span data-stu-id="4ecd2-106">Parameters</span></span>  
  
|<span data-ttu-id="4ecd2-107">參數</span><span class="sxs-lookup"><span data-stu-id="4ecd2-107">Parameter</span></span>|<span data-ttu-id="4ecd2-108">Required</span><span class="sxs-lookup"><span data-stu-id="4ecd2-108">Required</span></span>|<span data-ttu-id="4ecd2-109">Description</span><span class="sxs-lookup"><span data-stu-id="4ecd2-109">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="4ecd2-110">**/ 伺服器**(或 **/S**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="4ecd2-110">**/Server** (or **/S**, see Remarks)</span></span>|<span data-ttu-id="4ecd2-111">否</span><span class="sxs-lookup"><span data-stu-id="4ecd2-111">No</span></span>|<span data-ttu-id="4ecd2-112">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-112">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="4ecd2-113">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-113">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="4ecd2-114">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-114">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="4ecd2-115">範例:</span><span class="sxs-lookup"><span data-stu-id="4ecd2-115">Examples:</span></span><br /><br /> <span data-ttu-id="4ecd2-116">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="4ecd2-116">Server=MyServer</span></span><br /><br /> <span data-ttu-id="4ecd2-117">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="4ecd2-117">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="4ecd2-118">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-118">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
|<span data-ttu-id="4ecd2-119">**/ 資料庫**(或 **/D**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="4ecd2-119">**/Database** (or **/D**, see Remarks)</span></span>|<span data-ttu-id="4ecd2-120">否</span><span class="sxs-lookup"><span data-stu-id="4ecd2-120">No</span></span>|<span data-ttu-id="4ecd2-121">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-121">Name of the BizTalk Management database.</span></span> <span data-ttu-id="4ecd2-122">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-122">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="4ecd2-123">範例</span><span class="sxs-lookup"><span data-stu-id="4ecd2-123">Sample</span></span>  
 <span data-ttu-id="4ecd2-124">**BTSTask ListApps**</span><span class="sxs-lookup"><span data-stu-id="4ecd2-124">**BTSTask ListApps**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ecd2-125">備註</span><span class="sxs-lookup"><span data-stu-id="4ecd2-125">Remarks</span></span>  
 <span data-ttu-id="4ecd2-126">參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-126">Parameters are not case-sensitive.</span></span> <span data-ttu-id="4ecd2-127">您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。</span><span class="sxs-lookup"><span data-stu-id="4ecd2-127">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ecd2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ecd2-128">See Also</span></span>  
 [<span data-ttu-id="4ecd2-129">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="4ecd2-129">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)