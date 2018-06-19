---
title: AddApp 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 445784f1-505b-4259-a3f4-6f0d61578b1c
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6b91faa406181db3e4195bf57baeb086a0b69e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229998"
---
# <a name="addapp-command"></a><span data-ttu-id="9ccd0-102">AddApp 命令</span><span class="sxs-lookup"><span data-stu-id="9ccd0-102">AddApp Command</span></span>
<span data-ttu-id="9ccd0-103">在 BizTalk 管理資料庫中建立新的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-103">Creates a new BizTalk application in the BizTalk Management database.</span></span> <span data-ttu-id="9ccd0-104">您可以在 BizTalk Server 管理主控台的 [應用程式] 節點下檢視應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-104">You can view the application in the Applications node of the BizTalk Server Administration console.</span></span> <span data-ttu-id="9ccd0-105">您可以將成品新增至應用程式使用 AddResource 命令中所述[AddResource 命令](../core/addresource-command.md)。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-105">You can add artifacts to the application by using the AddResource command, as described in [AddResource Command](../core/addresource-command.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="9ccd0-106">使用方式</span><span class="sxs-lookup"><span data-stu-id="9ccd0-106">Usage</span></span>  
 <span data-ttu-id="9ccd0-107">**BTSTask AddApp /ApplicationName:** *值*[**/Description:***值*] [**/預設**] [**/伺服器：***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="9ccd0-107">**BTSTask AddApp /ApplicationName:** *value* [**/Description:***value*] [**/Default**] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="9ccd0-108">參數</span><span class="sxs-lookup"><span data-stu-id="9ccd0-108">Parameters</span></span>  
  
|<span data-ttu-id="9ccd0-109">參數</span><span class="sxs-lookup"><span data-stu-id="9ccd0-109">Parameter</span></span>|<span data-ttu-id="9ccd0-110">Required</span><span class="sxs-lookup"><span data-stu-id="9ccd0-110">Required</span></span>|<span data-ttu-id="9ccd0-111">值</span><span class="sxs-lookup"><span data-stu-id="9ccd0-111">Value</span></span>|  
|---------------|--------------|-----------|  
|<span data-ttu-id="9ccd0-112">**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="9ccd0-112">**/ApplicationName** (or **/A**, see Remarks)</span></span>|<span data-ttu-id="9ccd0-113">是</span><span class="sxs-lookup"><span data-stu-id="9ccd0-113">Yes</span></span>|<span data-ttu-id="9ccd0-114">若要加入的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-114">Name of the BizTalk application to add.</span></span> <span data-ttu-id="9ccd0-115">如果應用程式名稱包含空格，則它必須括在雙引號 （"）。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-115">If the application name includes spaces, it must be enclosed in double quotation marks (").</span></span>|  
|<span data-ttu-id="9ccd0-116">**/ 預設**(或 **/Def**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="9ccd0-116">**/Default** (or **/Def**, see Remarks)</span></span>|<span data-ttu-id="9ccd0-117">否</span><span class="sxs-lookup"><span data-stu-id="9ccd0-117">No</span></span>|<span data-ttu-id="9ccd0-118">如果有指定，新應用程式將成為 BizTalk 群組預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-118">When specified, makes the new application the default application for the BizTalk group.</span></span>|  
|<span data-ttu-id="9ccd0-119">**/ 描述**(或 **/Des**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="9ccd0-119">**/Description** (or **/Des**, see Remarks)</span></span>|<span data-ttu-id="9ccd0-120">否</span><span class="sxs-lookup"><span data-stu-id="9ccd0-120">No</span></span>|<span data-ttu-id="9ccd0-121">應用程式的說明。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-121">Description of the application.</span></span> <span data-ttu-id="9ccd0-122">必須括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-122">Must be enclosed in double quotation marks (").</span></span>|  
|<span data-ttu-id="9ccd0-123">**/ 伺服器**(或 **/S**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="9ccd0-123">**/Server** (or **/S**, see Remarks)</span></span>|<span data-ttu-id="9ccd0-124">否</span><span class="sxs-lookup"><span data-stu-id="9ccd0-124">No</span></span>|<span data-ttu-id="9ccd0-125">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-125">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="9ccd0-126">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-126">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="9ccd0-127">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-127">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="9ccd0-128">範例:</span><span class="sxs-lookup"><span data-stu-id="9ccd0-128">Examples:</span></span><br /><br /> <span data-ttu-id="9ccd0-129">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="9ccd0-129">Server=MyServer</span></span><br /><br /> <span data-ttu-id="9ccd0-130">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="9ccd0-130">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="9ccd0-131">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-131">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
|<span data-ttu-id="9ccd0-132">**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="9ccd0-132">**/Database** (or **/Da**, see Remarks)</span></span>|<span data-ttu-id="9ccd0-133">否</span><span class="sxs-lookup"><span data-stu-id="9ccd0-133">No</span></span>|<span data-ttu-id="9ccd0-134">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-134">Name of the BizTalk Management database.</span></span> <span data-ttu-id="9ccd0-135">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-135">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="9ccd0-136">範例</span><span class="sxs-lookup"><span data-stu-id="9ccd0-136">Sample</span></span>  
 <span data-ttu-id="9ccd0-137">**AddApp /applicationname: myapplication /Description: 「 我的 BizTalk 應用程式 」**</span><span class="sxs-lookup"><span data-stu-id="9ccd0-137">**AddApp /ApplicationName:MyApplication /Description:"My BizTalk application"**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ccd0-138">備註</span><span class="sxs-lookup"><span data-stu-id="9ccd0-138">Remarks</span></span>  
 <span data-ttu-id="9ccd0-139">參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-139">Parameters are not case-sensitive.</span></span> <span data-ttu-id="9ccd0-140">您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。</span><span class="sxs-lookup"><span data-stu-id="9ccd0-140">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccd0-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ccd0-141">See Also</span></span>  
 <span data-ttu-id="9ccd0-142">[BTSTask 命令列參考](../core/btstask-command-line-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9ccd0-142">[BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) </span></span>  
 [<span data-ttu-id="9ccd0-143">如何建立應用程式</span><span class="sxs-lookup"><span data-stu-id="9ccd0-143">How to Create an Application</span></span>](../core/how-to-create-an-application.md)