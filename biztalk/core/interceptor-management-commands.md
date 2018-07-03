---
title: 攔截器管理命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2be6460-1f81-4bc3-a831-34ff24d65d34
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aefeefc7010c4cefca323782dac5a1349479a07d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023164"
---
# <a name="interceptor-management-commands"></a><span data-ttu-id="4d251-102">攔截器管理命令</span><span class="sxs-lookup"><span data-stu-id="4d251-102">Interceptor Management Commands</span></span>
<span data-ttu-id="4d251-103">為了支援新的 BAM 攔截器功能，BAM 管理公用程式中已加入四個新的命令。</span><span class="sxs-lookup"><span data-stu-id="4d251-103">To support the new BAM interceptor functionality, four new commands have been added to the BAM Management utility.</span></span>  
  
 <span data-ttu-id="4d251-104">這些命令支援攔截器的部署、擷取和移除。</span><span class="sxs-lookup"><span data-stu-id="4d251-104">These commands support the deployment, retrieval, and removal of interceptors.</span></span> <span data-ttu-id="4d251-105">也有提供一個命令給設定的攔截器清單。</span><span class="sxs-lookup"><span data-stu-id="4d251-105">A command is also provided to list the configured interceptors.</span></span>  
  
-   <span data-ttu-id="4d251-106">部署攔截器： 部署攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-106">deploy-interceptor: Deploys an interceptor configuration.</span></span>  
  
-   <span data-ttu-id="4d251-107">取得 interceptorlist： 取得部署攔截的活動清單。</span><span class="sxs-lookup"><span data-stu-id="4d251-107">get-interceptorlist: Gets a list of activities on which interception is deployed.</span></span>  
  
-   <span data-ttu-id="4d251-108">取得攔截器： 取得攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-108">get-interceptor: Gets the interceptor configuration.</span></span>  
  
-   <span data-ttu-id="4d251-109">移除攔截器： 移除攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-109">remove-interceptor: Removes an interceptor configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d251-110">您可以藉由啟用任何 BM 公用程式命令的追蹤 **-追蹤： 在&#124;關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="4d251-110">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="4d251-111">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="4d251-111">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="4d251-112">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="4d251-112">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d251-113">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="4d251-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="deploy-interceptor-command"></a><span data-ttu-id="4d251-114">deploy-interceptor 命令</span><span class="sxs-lookup"><span data-stu-id="4d251-114">deploy-interceptor Command</span></span>  
 <span data-ttu-id="4d251-115">**Usage**</span><span class="sxs-lookup"><span data-stu-id="4d251-115">**Usage**</span></span>  
  
 <span data-ttu-id="4d251-116">**bm.exe 部署攔截器檔案名稱：\<組態 XML 檔名\>[-Force: True] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="4d251-116">**bm.exe deploy-interceptor -FileName:\<Configuration XML Filename\> [-Force:True ] [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="4d251-117">**參數**</span><span class="sxs-lookup"><span data-stu-id="4d251-117">**Parameters**</span></span>  
  
|<span data-ttu-id="4d251-118">參數</span><span class="sxs-lookup"><span data-stu-id="4d251-118">Parameter</span></span>|<span data-ttu-id="4d251-119">描述</span><span class="sxs-lookup"><span data-stu-id="4d251-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d251-120">檔案名稱：\<組態 XML 檔案名稱\></span><span class="sxs-lookup"><span data-stu-id="4d251-120">FileName:\<Configuration XML Filename\></span></span>|<span data-ttu-id="4d251-121">包含攔截器組態的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-121">The name of the XML file containing the interceptor configuration.</span></span>|  
|<span data-ttu-id="4d251-122">Force:True</span><span class="sxs-lookup"><span data-stu-id="4d251-122">Force:True</span></span>|<span data-ttu-id="4d251-123">選擇性： 偵測到事件來源名稱衝突時，會強制部署攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-123">Optional: Forces deployment of the interceptor configuration when event source name collisions are detected.</span></span>|  
|<span data-ttu-id="4d251-124">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="4d251-124">Server:\<server\></span></span>|<span data-ttu-id="4d251-125">選擇性： 要部署攔截器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-125">Optional: The name of the server on which to deploy the interceptor.</span></span> <span data-ttu-id="4d251-126">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4d251-126">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4d251-127">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="4d251-127">Database:\<database\></span></span>|<span data-ttu-id="4d251-128">選擇性： 要設定攔截器的 BAM 主要匯入資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-128">Optional: The name of the BAM Primary Import database on which to configure the interceptor.</span></span>|  
  
 <span data-ttu-id="4d251-129">這個命令會將攔截器組態部署到指定的伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d251-129">This command deploys the interceptor configuration to the specified server and database.</span></span> <span data-ttu-id="4d251-130">在部署期間，BAM 管理公用程式會執行下列驗證：</span><span class="sxs-lookup"><span data-stu-id="4d251-130">During deployment, the BAM Management utility performs the following validations:</span></span>  
  
- <span data-ttu-id="4d251-131">XSD 驗證： 針對一般攔截器組態結構描述驗證的攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-131">XSD validation: The interceptor configuration is validated against the common interceptor configuration schema.</span></span>  
  
- <span data-ttu-id="4d251-132">此活動存在 (在主要匯入資料庫中部署) 且檢查點有效 (存在而且有相符的資料類型) 的驗證。</span><span class="sxs-lookup"><span data-stu-id="4d251-132">Validation that the activity exists (is deployed in the Primary Import database) and that checkpoints are valid (exist and have a matching data type).</span></span>  
  
  <span data-ttu-id="4d251-133">如果在事件來源名稱中偵測到衝突，會擲回一則警告來描述此衝突。</span><span class="sxs-lookup"><span data-stu-id="4d251-133">If a collision is detected in the event source name, a warning is thrown describing the collision.</span></span> <span data-ttu-id="4d251-134">如果發生衝突，部署會失敗，除非 **– Force: True**使用參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="4d251-134">In the case of a collision, the deployment will fail unless the **–Force:True** parameter flag is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d251-135">**– Force: True**參數可能會移除參考具有相同名稱的事件來源的攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-135">The **–Force:True** parameter potentially removes interceptor configurations that reference event sources with the same name.</span></span> <span data-ttu-id="4d251-136">您應該使用**取得攔截器**命令來建立現有攔截器組態的備份，再使用 **– Force: True**參數。</span><span class="sxs-lookup"><span data-stu-id="4d251-136">You should use the **get-interceptor** command to create a backup of existing interceptor configurations before using the **–Force:True** parameter.</span></span>  
  
 <span data-ttu-id="4d251-137">**範例**</span><span class="sxs-lookup"><span data-stu-id="4d251-137">**Examples**</span></span>  
  
```  
bm.exe deploy-interceptor  -FileName:myInceptor.xml  
bm.exe deploy-interceptor  -FileName:myInceptor.xml -Force:True  
```  
  
## <a name="get-interceptorlist-command"></a><span data-ttu-id="4d251-138">get-interceptorlist 命令</span><span class="sxs-lookup"><span data-stu-id="4d251-138">get-interceptorlist Command</span></span>  
 <span data-ttu-id="4d251-139">**Usage**</span><span class="sxs-lookup"><span data-stu-id="4d251-139">**Usage**</span></span>  
  
 <span data-ttu-id="4d251-140">**bm.exe get interceptorlist [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="4d251-140">**bm.exe get-interceptorlist [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="4d251-141">**參數**</span><span class="sxs-lookup"><span data-stu-id="4d251-141">**Parameters**</span></span>  
  
|<span data-ttu-id="4d251-142">參數</span><span class="sxs-lookup"><span data-stu-id="4d251-142">Parameter</span></span>|<span data-ttu-id="4d251-143">描述</span><span class="sxs-lookup"><span data-stu-id="4d251-143">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d251-144">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="4d251-144">Server:\<server\></span></span>|<span data-ttu-id="4d251-145">選擇性： 要從中傳回一份已部署攔截器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-145">Optional: The name of the server from which to return a list of deployed interceptors.</span></span> <span data-ttu-id="4d251-146">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4d251-146">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4d251-147">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="4d251-147">Database:\<database\></span></span>|<span data-ttu-id="4d251-148">選擇性： 要從中擷取已部署攔截器的 BAM 主要匯入資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-148">Optional: The name of the BAM Primary Import database from which to retrieve the deployed interceptors.</span></span>|  
  
 <span data-ttu-id="4d251-149">這個命令會傳回已啟用攔截之活動和其相關事件來源的清單。</span><span class="sxs-lookup"><span data-stu-id="4d251-149">This command returns a list of the activities, and their associated event sources, for which interception is enabled.</span></span>  
  
 <span data-ttu-id="4d251-150">**範例**</span><span class="sxs-lookup"><span data-stu-id="4d251-150">**Example**</span></span>  
  
```  
bm.exe get-interceptorlist   
```  
  
## <a name="get-interceptor-command"></a><span data-ttu-id="4d251-151">get-interceptor 命令</span><span class="sxs-lookup"><span data-stu-id="4d251-151">get-interceptor Command</span></span>  
 <span data-ttu-id="4d251-152">**Usage**</span><span class="sxs-lookup"><span data-stu-id="4d251-152">**Usage**</span></span>  
  
 <span data-ttu-id="4d251-153">**bm.exe 取得攔截器 [-Server:\<伺服器\>] [-Database:\<資料庫\>]-FileName:\<組態 XML 檔案名稱\>[-活動：\<活動名稱\>][-EventSource:\<事件來源名稱\>]**</span><span class="sxs-lookup"><span data-stu-id="4d251-153">**bm.exe get-interceptor [-Server:\<server\>] [-Database:\<database\>] -FileName: \<Configuration XML Filename\> [ -Activity: \<Activity Name\>] [-EventSource: \<Event Source Name\>]**</span></span>  
  
 <span data-ttu-id="4d251-154">**參數**</span><span class="sxs-lookup"><span data-stu-id="4d251-154">**Parameters**</span></span>  
  
|<span data-ttu-id="4d251-155">參數</span><span class="sxs-lookup"><span data-stu-id="4d251-155">Parameter</span></span>|<span data-ttu-id="4d251-156">描述</span><span class="sxs-lookup"><span data-stu-id="4d251-156">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d251-157">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="4d251-157">Server:\<server\></span></span>|<span data-ttu-id="4d251-158">選擇性： 要從中擷取已部署之攔截器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-158">Optional: The name of the server from which to retrieve the deployed interceptor.</span></span> <span data-ttu-id="4d251-159">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4d251-159">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4d251-160">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="4d251-160">Database:\<database\></span></span>|<span data-ttu-id="4d251-161">選擇性： 要從中擷取已部署之攔截器的 BAM 主要匯入資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-161">Optional: The name of the BAM Primary Import database from which to retrieve deployed interceptor.</span></span>|  
|<span data-ttu-id="4d251-162">檔案名稱：\<組態 XML 檔案名稱\></span><span class="sxs-lookup"><span data-stu-id="4d251-162">FileName:\<Configuration XML Filename\></span></span>|<span data-ttu-id="4d251-163">寫入攔截器組態的目標 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-163">The name of the XML file to which to write the interceptor configuration.</span></span>|  
|<span data-ttu-id="4d251-164">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="4d251-164">Activity:\<Activity Name\></span></span>|<span data-ttu-id="4d251-165">選擇性︰ 指定要傳回設定之攔截器的活動。</span><span class="sxs-lookup"><span data-stu-id="4d251-165">Optional: Specifies the activity for which to return the configured interceptor.</span></span> <span data-ttu-id="4d251-166">可以用於搭配**EventSource**參數來進一步指定要傳回的組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-166">Can be used in conjunction with the **EventSource** parameter to further specify the configuration to return.</span></span>|  
|<span data-ttu-id="4d251-167">EventSource:\<事件來源名稱\></span><span class="sxs-lookup"><span data-stu-id="4d251-167">EventSource:\<Event Source Name\></span></span>|<span data-ttu-id="4d251-168">選擇性︰ 指定要傳回設定之攔截器的事件來源。</span><span class="sxs-lookup"><span data-stu-id="4d251-168">Optional: Specifies the event source for which to return the configured interceptor.</span></span> <span data-ttu-id="4d251-169">可以用於搭配**活動**參數來進一步指定要傳回的組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-169">Can be used in conjunction with the **Activity** parameter to further specify the configuration to return.</span></span>|  
  
 <span data-ttu-id="4d251-170">如果未提供任何活動名稱或事件來源名稱，此命令會傳回有效的組態檔，其中包含所有事件來源和活動的攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-170">If no activity name or event source name is provided, the command returns a valid configuration file containing the interceptor configurations for all event sources and activities.</span></span>  
  
 <span data-ttu-id="4d251-171">如果只有提供活動名稱，此命令會針對該活動的所有事件來源傳回有效的攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="4d251-171">If only an activity name is provided, the command returns a valid interceptor configuration file for all event sources for that activity.</span></span>  
  
 <span data-ttu-id="4d251-172">如果只有提供事件來源名稱，此命令會針對所有活動中的該事件來源傳回有效的攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="4d251-172">If only an event source name is provided, the command returns a valid interceptor configuration file for that event source across all activities.</span></span>  
  
 <span data-ttu-id="4d251-173">如果活動名稱和事件來源名稱都有提供，此命令會針對該活動的該事件來源傳回有效的攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="4d251-173">If both an activity name and an event source name are provided, then the command returns a valid interceptor configuration file for that event source for that activity.</span></span>  
  
 <span data-ttu-id="4d251-174">**範例**</span><span class="sxs-lookup"><span data-stu-id="4d251-174">**Examples**</span></span>  
  
```  
bm.exe get-interceptor   
bm.exe get-interceptor  -Activity:ShippingPO  
```  
  
## <a name="remove-interceptor-command"></a><span data-ttu-id="4d251-175">remove-interceptor 命令</span><span class="sxs-lookup"><span data-stu-id="4d251-175">remove-interceptor Command</span></span>  
 <span data-ttu-id="4d251-176">**Usage**</span><span class="sxs-lookup"><span data-stu-id="4d251-176">**Usage**</span></span>  
  
 <span data-ttu-id="4d251-177">**bm.exe 移除攔截器 [-Server:\<伺服器\>] [-Database:\<資料庫\>] [-活動：\<活動名稱\>] [-EventSource: \<的事件來源名稱\>]**</span><span class="sxs-lookup"><span data-stu-id="4d251-177">**bm.exe remove-interceptor [-Server:\<server\>] [-Database:\<database\>] [ -Activity: \<Activity Name\>][-EventSource: \<Event Source Name\>]**</span></span>  
  
 <span data-ttu-id="4d251-178">**參數**</span><span class="sxs-lookup"><span data-stu-id="4d251-178">**Parameters**</span></span>  
  
|<span data-ttu-id="4d251-179">參數</span><span class="sxs-lookup"><span data-stu-id="4d251-179">Parameter</span></span>|<span data-ttu-id="4d251-180">描述</span><span class="sxs-lookup"><span data-stu-id="4d251-180">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d251-181">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="4d251-181">Server:\<server\></span></span>|<span data-ttu-id="4d251-182">選擇性： 要設定攔截器所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-182">Optional: The name of the server on which the interceptor is configured.</span></span> <span data-ttu-id="4d251-183">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4d251-183">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4d251-184">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="4d251-184">Database:\<database\></span></span>|<span data-ttu-id="4d251-185">選擇性： 要設定攔截器所在之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d251-185">Optional: The name of the database on which the interceptor is configured.</span></span>|  
|<span data-ttu-id="4d251-186">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="4d251-186">Activity: \<Activity Name\></span></span>|<span data-ttu-id="4d251-187">選擇性︰ 指定要移除指定之攔截器的活動。</span><span class="sxs-lookup"><span data-stu-id="4d251-187">Optional: Specifies the activity for which to remove the specified interceptor.</span></span> <span data-ttu-id="4d251-188">可以用於搭配**EventSource**參數來進一步指定要傳回的組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-188">Can be used in conjunction with the **EventSource** parameter to further specify the configuration to return.</span></span>|  
|<span data-ttu-id="4d251-189">EventSource:\<事件來源名稱\></span><span class="sxs-lookup"><span data-stu-id="4d251-189">EventSource: \<Event Source Name\></span></span>|<span data-ttu-id="4d251-190">選擇性︰ 指定要移除指定之攔截器的事件來源。</span><span class="sxs-lookup"><span data-stu-id="4d251-190">Optional: Specifies the event source for which to remove the specified interceptor.</span></span> <span data-ttu-id="4d251-191">可以用於搭配**活動**參數來進一步指定要傳回的組態。</span><span class="sxs-lookup"><span data-stu-id="4d251-191">Can be used in conjunction with the **Activity** parameter to further specify the configuration to return.</span></span>|  
  
 <span data-ttu-id="4d251-192">如果只有提供活動名稱，此命令會針對該活動的所有事件來源移除攔截器。</span><span class="sxs-lookup"><span data-stu-id="4d251-192">If only an activity name is provided, the command removes the interceptor for all event sources for that activity.</span></span>  
  
 <span data-ttu-id="4d251-193">如果只有提供事件來源名稱，此命令只會移除所有活動的該事件來源部分。</span><span class="sxs-lookup"><span data-stu-id="4d251-193">If only an event source name is provided, the command removes only that event source portion for all activities.</span></span>  
  
 <span data-ttu-id="4d251-194">**範例**</span><span class="sxs-lookup"><span data-stu-id="4d251-194">**Example**</span></span>  
  
```  
bm.exe remove-interceptor   
```  
  
## <a name="see-also"></a><span data-ttu-id="4d251-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d251-195">See Also</span></span>  
 [<span data-ttu-id="4d251-196">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="4d251-196">BAM Management Utility</span></span>](../core/bam-management-utility.md)