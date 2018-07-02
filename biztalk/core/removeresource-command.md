---
title: RemoveResource 命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e2c6046-43d4-4ac1-a1b1-3795b4e44038
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c95b636083542bb1291cd10881bd74ca9d41c15b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976991"
---
# <a name="removeresource-command"></a><span data-ttu-id="2149f-102">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="2149f-102">RemoveResource Command</span></span>
<span data-ttu-id="2149f-103">從 BizTalk 管理資料庫移除 (刪除) 成品。</span><span class="sxs-lookup"><span data-stu-id="2149f-103">Removes (deletes) an artifact from the BizTalk Management database.</span></span> <span data-ttu-id="2149f-104">執行此命令並不會將全域組件快取 (GAC)、檔案系統、憑證存放區、Internet Information Services 或 Windows 登錄等位置上已有的成品移除。</span><span class="sxs-lookup"><span data-stu-id="2149f-104">Running this command does not remove the artifact from the global assembly cache (GAC), file system, certificate store, Internet Information Services, or the Windows registry, if it exists in any of these locations.</span></span> <span data-ttu-id="2149f-105">此命令既不會從 BAM 主要匯入資料庫移除 BAM 定義，也不會從規則引擎資料庫移除原則。</span><span class="sxs-lookup"><span data-stu-id="2149f-105">It does not remove a BAM definition from the BAM Primary Import database nor does it remove policies from the Rule Engine database.</span></span> <span data-ttu-id="2149f-106">若您執行此命令以移除繫結檔案，繫結仍將原封不動；此舉只會移除繫結檔案而已。</span><span class="sxs-lookup"><span data-stu-id="2149f-106">If you run this command to remove a binding file, the bindings remain unchanged – only the binding file is removed.</span></span>  
  
 <span data-ttu-id="2149f-107">您可以使用此命令移除下列成品類型：</span><span class="sxs-lookup"><span data-stu-id="2149f-107">You can use this command to remove the following artifact types:</span></span>  
  
- <span data-ttu-id="2149f-108">.NET 組件 (System.BizTalk:Assembly)</span><span class="sxs-lookup"><span data-stu-id="2149f-108">.NET assembly (System.BizTalk:Assembly)</span></span>  
  
- <span data-ttu-id="2149f-109">BAM 定義 (System.BizTalk:Bam)</span><span class="sxs-lookup"><span data-stu-id="2149f-109">BAM definition (System.BizTalk:Bam)</span></span>  
  
- <span data-ttu-id="2149f-110">BizTalk 組件 (System.BizTalk:BizTalkAssembly)</span><span class="sxs-lookup"><span data-stu-id="2149f-110">BizTalk assembly (System.BizTalk:BizTalkAssembly</span></span>  
  
- <span data-ttu-id="2149f-111">BizTalk 繫結檔案 (System.BizTalk:BizTalkBinding)</span><span class="sxs-lookup"><span data-stu-id="2149f-111">BizTalk binding file (System.BizTalk:BizTalkBinding)</span></span>  
  
- <span data-ttu-id="2149f-112">安全性憑證 (System.BizTalk:Certificate)</span><span class="sxs-lookup"><span data-stu-id="2149f-112">Security certificate (System.BizTalk:Certificate)</span></span>  
  
- <span data-ttu-id="2149f-113">COM 元件 (System.BizTalk:Com)</span><span class="sxs-lookup"><span data-stu-id="2149f-113">COM component (System.BizTalk:Com)</span></span>  
  
- <span data-ttu-id="2149f-114">臨機操作檔案 (System.BizTalk:File)</span><span class="sxs-lookup"><span data-stu-id="2149f-114">Ad hoc file (System.BizTalk:File)</span></span>  
  
- <span data-ttu-id="2149f-115">後置處理指令碼 (System.BizTalk:PostProcessingScript)</span><span class="sxs-lookup"><span data-stu-id="2149f-115">Postprocessing script (System.BizTalk:PostProcessingScript)</span></span>  
  
- <span data-ttu-id="2149f-116">前置處理指令碼 (System.BizTalk:PreProcessingScript)</span><span class="sxs-lookup"><span data-stu-id="2149f-116">Preprocessing script (System.BizTalk:PreProcessingScript)</span></span>  
  
- <span data-ttu-id="2149f-117">原則或規則 (System.BizTalk:Rules)</span><span class="sxs-lookup"><span data-stu-id="2149f-117">Policy or rule (System.BizTalk:Rules)</span></span>  
  
- <span data-ttu-id="2149f-118">虛擬目錄 (System.BizTalk:WebDirectory)</span><span class="sxs-lookup"><span data-stu-id="2149f-118">Virtual directory (System.BizTalk:WebDirectory)</span></span>  
  
  <span data-ttu-id="2149f-119">在下列情況中，移除作業將會失敗：</span><span class="sxs-lookup"><span data-stu-id="2149f-119">The remove operation will fail in the following cases:</span></span>  
  
- <span data-ttu-id="2149f-120">試圖移除的 BizTalk 組件正由其他組件所參考。</span><span class="sxs-lookup"><span data-stu-id="2149f-120">You attempt to remove a BizTalk assembly to which another assembly has a reference.</span></span>  
  
- <span data-ttu-id="2149f-121">試圖移除的 BizTalk 組件中含有傳送埠或接收埠正在使用的管線。</span><span class="sxs-lookup"><span data-stu-id="2149f-121">You attempt to remove a BizTalk assembly that includes a pipeline that is used by a send or receive port.</span></span>  
  
- <span data-ttu-id="2149f-122">試圖移除的 BizTalk 組件中含有傳送埠正在使用的對應。</span><span class="sxs-lookup"><span data-stu-id="2149f-122">You attempt to remove a BizTalk assembly that includes a map used by a send port.</span></span>  
  
- <span data-ttu-id="2149f-123">試圖移除的 BizTalk 組件中含有不在取消登錄狀態，或其執行個體擱置的協調流程。</span><span class="sxs-lookup"><span data-stu-id="2149f-123">You attempt to remove a BizTalk assembly that includes an orchestration that is not in an unenlisted state or that has a suspended instance.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="2149f-124">使用方式</span><span class="sxs-lookup"><span data-stu-id="2149f-124">Usage</span></span>  
 <span data-ttu-id="2149f-125">**BTSTask RemoveResource /ApplicationName:** *值* **/Luid:** *值*[**/Server:**<em>值</em>] [**/Database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="2149f-125">**BTSTask RemoveResource /ApplicationName:** *value* **/Luid:** *value* [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="2149f-126">參數</span><span class="sxs-lookup"><span data-stu-id="2149f-126">Parameters</span></span>  
  
|<span data-ttu-id="2149f-127">參數</span><span class="sxs-lookup"><span data-stu-id="2149f-127">Parameter</span></span>|<span data-ttu-id="2149f-128">必要項</span><span class="sxs-lookup"><span data-stu-id="2149f-128">Required</span></span>|<span data-ttu-id="2149f-129">描述</span><span class="sxs-lookup"><span data-stu-id="2149f-129">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="2149f-130">**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="2149f-130">**/ApplicationName** (or **/A**, see Remarks)</span></span>|<span data-ttu-id="2149f-131">是</span><span class="sxs-lookup"><span data-stu-id="2149f-131">Yes</span></span>|<span data-ttu-id="2149f-132">含有所要刪除之資源成品的 BizTalk 應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="2149f-132">Name of the BizTalk application containing the resource artifact to delete.</span></span> <span data-ttu-id="2149f-133">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="2149f-133">If the name includes spaces, you must enclose it with double quotation marks (").</span></span>|  
|<span data-ttu-id="2149f-134">**/ Luid** (或 **/L**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="2149f-134">**/Luid** (or **/L**, see Remarks)</span></span>|<span data-ttu-id="2149f-135">是</span><span class="sxs-lookup"><span data-stu-id="2149f-135">Yes</span></span>|<span data-ttu-id="2149f-136">成品的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="2149f-136">Locally unique identifier (LUID) of the artifact.</span></span> <span data-ttu-id="2149f-137">您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="2149f-137">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
|<span data-ttu-id="2149f-138">**/Server** (或 **/S**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="2149f-138">**/Server** (or **/S**, see Remarks)</span></span>|<span data-ttu-id="2149f-139">否</span><span class="sxs-lookup"><span data-stu-id="2149f-139">No</span></span>|<span data-ttu-id="2149f-140">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="2149f-140">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="2149f-141">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="2149f-141">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="2149f-142">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="2149f-142">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="2149f-143">範例:</span><span class="sxs-lookup"><span data-stu-id="2149f-143">Examples:</span></span><br /><br /> <span data-ttu-id="2149f-144">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="2149f-144">Server=MyServer</span></span><br /><br /> <span data-ttu-id="2149f-145">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="2149f-145">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="2149f-146">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="2149f-146">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
|<span data-ttu-id="2149f-147">**/ 資料庫**(或 **/D**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="2149f-147">**/Database** (or **/D**, see Remarks)</span></span>|<span data-ttu-id="2149f-148">否</span><span class="sxs-lookup"><span data-stu-id="2149f-148">No</span></span>|<span data-ttu-id="2149f-149">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2149f-149">Name of the BizTalk Management database.</span></span> <span data-ttu-id="2149f-150">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="2149f-150">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="2149f-151">範例</span><span class="sxs-lookup"><span data-stu-id="2149f-151">Sample</span></span>  
 <span data-ttu-id="2149f-152">**BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0、 文化特性 = 中性，PublicKeyToken = 0123456789ABCDEF"**</span><span class="sxs-lookup"><span data-stu-id="2149f-152">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2149f-153">備註</span><span class="sxs-lookup"><span data-stu-id="2149f-153">Remarks</span></span>  
 <span data-ttu-id="2149f-154">參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2149f-154">Parameters are not case-sensitive.</span></span> <span data-ttu-id="2149f-155">您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。</span><span class="sxs-lookup"><span data-stu-id="2149f-155">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2149f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2149f-156">See Also</span></span>  
 <span data-ttu-id="2149f-157">[BTSTask 命令列參考](../core/btstask-command-line-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2149f-157">[BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) </span></span>  
 [<span data-ttu-id="2149f-158">如何從應用程式移除成品</span><span class="sxs-lookup"><span data-stu-id="2149f-158">How to Remove an Artifact from an Application</span></span>](../core/how-to-remove-an-artifact-from-an-application.md)