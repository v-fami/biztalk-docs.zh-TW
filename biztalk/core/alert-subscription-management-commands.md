---
title: "警示訂閱管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd6ad27-6217-466a-b616-4b26fb31b0af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914d5cd9ac19e160c1f26df3f762f81fb89345d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="alert-subscription-management-commands"></a><span data-ttu-id="f6bdc-102">警示訂閱管理命令</span><span class="sxs-lookup"><span data-stu-id="f6bdc-102">Alert Subscription Management Commands</span></span>
<span data-ttu-id="f6bdc-103">BAM 管理公用程式訂閱管理命令可讓您使用警示訂閱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-103">The BAM management utility subscription management commands allow you to work with alert subscriptions.</span></span>  
  
-   <span data-ttu-id="f6bdc-104">取得訂用帳戶： 取得警示的訂閱者的清單。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-104">get-subscription: Gets a list of subscribers to an alert.</span></span>  
  
-   <span data-ttu-id="f6bdc-105">新增訂閱： 訂閱者加入警示。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-105">add-subscription: Adds a subscriber to an alert.</span></span>  
  
-   <span data-ttu-id="f6bdc-106">移除訂用帳戶： 從警示移除訂閱者。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-106">remove-subscription: Removes a subscriber from an alert.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6bdc-107">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-107">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="f6bdc-108">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-108">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="f6bdc-109">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-109">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6bdc-110">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-110">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-subscription-command"></a><span data-ttu-id="f6bdc-111">get-subscription 命令</span><span class="sxs-lookup"><span data-stu-id="f6bdc-111">get-subscription Command</span></span>  
 <span data-ttu-id="f6bdc-112">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-112">**Usage**</span></span>  
  
 <span data-ttu-id="f6bdc-113">**bm.exe get 訂閱-檢視：\<檢視名稱 >-警示：\<警示名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-113">**bm.exe get-subscriptions -View:\<view name> -Alert:\<alert name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="f6bdc-114">**參數**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-114">**Parameters**</span></span>  
  
|<span data-ttu-id="f6bdc-115">參數</span><span class="sxs-lookup"><span data-stu-id="f6bdc-115">Parameter</span></span>|<span data-ttu-id="f6bdc-116">Description</span><span class="sxs-lookup"><span data-stu-id="f6bdc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6bdc-117">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-117">View:\<view name></span></span>|<span data-ttu-id="f6bdc-118">指定的警示所在檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-118">The name of the view on which the alert is to be specified.</span></span>|  
|<span data-ttu-id="f6bdc-119">警示：\<警示名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-119">Alert:\<alert name></span></span>|<span data-ttu-id="f6bdc-120">要取得其訂閱的警示名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-120">The name of the alert from which to get the subscription.</span></span>|  
|<span data-ttu-id="f6bdc-121">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-121">Server:\<server></span></span>|<span data-ttu-id="f6bdc-122">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-122">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="f6bdc-123">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-123">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="f6bdc-124">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-124">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="f6bdc-125">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-125">Database:\<database></span></span>|<span data-ttu-id="f6bdc-126">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-126">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="f6bdc-127">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-127">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="f6bdc-128">列出指定之警示的所有訂閱者。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-128">Lists all the subscribers to the specified alert.</span></span>  
  
 <span data-ttu-id="f6bdc-129">**範例**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-129">**Examples**</span></span>  
  
```  
bm.exe get-subscriptions -View:SalesManagerView -Alert:SalesTooLow  
bm.exe get-subscriptions -View:Shipments -Alert:SlowShipment -Server:Ship1  
```  
  
## <a name="add-subscription-command"></a><span data-ttu-id="f6bdc-130">add-subscription 命令</span><span class="sxs-lookup"><span data-stu-id="f6bdc-130">add-subscription Command</span></span>  
 <span data-ttu-id="f6bdc-131">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-131">**Usage**</span></span>  
  
 <span data-ttu-id="f6bdc-132">**bm.exe 加入訂閱的檢視：\<檢視名稱 >-警示：\<警示名稱 >-AccountName:\<帳戶名稱 >-類型: [檔案 &#124;電子郵件] [-電子郵件：\<電子郵件地址 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-132">**bm.exe add-subscription -View:\<view name> -Alert:\<alert name> -AccountName:\<account name> -Type: [ File &#124; Email ][ -Email:\<e-mail address> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="f6bdc-133">**參數**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-133">**Parameters**</span></span>  
  
|<span data-ttu-id="f6bdc-134">參數</span><span class="sxs-lookup"><span data-stu-id="f6bdc-134">Parameter</span></span>|<span data-ttu-id="f6bdc-135">Description</span><span class="sxs-lookup"><span data-stu-id="f6bdc-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6bdc-136">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-136">View:\<view name></span></span>|<span data-ttu-id="f6bdc-137">指定警示所在檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-137">The name of the view on which the alert is specified.</span></span>|  
|<span data-ttu-id="f6bdc-138">警示：\<警示名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-138">Alert:\<alert name></span></span>|<span data-ttu-id="f6bdc-139">要訂閱的警示名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-139">The name of the alert to which to subscribe.</span></span>|  
|<span data-ttu-id="f6bdc-140">AccountName:\<帳戶名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-140">AccountName:\<account name></span></span>|<span data-ttu-id="f6bdc-141">訂閱警示的帳戶，格式為「網域\使用者」。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-141">The account, in domain\user format, to subscribe to the alert.</span></span>|  
|<span data-ttu-id="f6bdc-142">類型: [檔案 &#124;電子郵件]</span><span class="sxs-lookup"><span data-stu-id="f6bdc-142">Type: [ File &#124; Email ]</span></span>|<span data-ttu-id="f6bdc-143">警示的傳遞類型。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-143">The delivery type of the alert.</span></span> <span data-ttu-id="f6bdc-144">如果您指定電子郵件的傳遞類型，則必須在命令列上包含電子郵件參數。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-144">If you specify a delivery type of e-mail, you must include the e-mail parameter on the command line.</span></span>|  
|<span data-ttu-id="f6bdc-145">電子郵件：\<電子郵件地址 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-145">Email:\<e-mail address></span></span>|<span data-ttu-id="f6bdc-146">選擇性： 將會傳遞警示通知電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-146">Optional: The email address to which the alert notification will be delivered.</span></span>|  
|<span data-ttu-id="f6bdc-147">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-147">Server:\<server></span></span>|<span data-ttu-id="f6bdc-148">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-148">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="f6bdc-149">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-149">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="f6bdc-150">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-150">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="f6bdc-151">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-151">Database:\<database></span></span>|<span data-ttu-id="f6bdc-152">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-152">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="f6bdc-153">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-153">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="f6bdc-154">為指定的帳戶新增訂閱至只訂的警示。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-154">Adds a subscription for the specified account to the specified alert.</span></span>  
  
 <span data-ttu-id="f6bdc-155">**範例**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-155">**Examples**</span></span>  
  
```  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:File  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:Email -Email:useremail@domain.com  
```  
  
## <a name="remove-subscription-command"></a><span data-ttu-id="f6bdc-156">remove-subscription 命令</span><span class="sxs-lookup"><span data-stu-id="f6bdc-156">remove-subscription Command</span></span>  
 <span data-ttu-id="f6bdc-157">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-157">**Usage**</span></span>  
  
 <span data-ttu-id="f6bdc-158">**bm.exe 移除訂用帳戶-檢視：\<檢視名稱 >-警示：\<警示名稱 >-AccountName:\<帳戶名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-158">**bm.exe remove-subscription -View:\<view name> -Alert:\<alert name> -AccountName:\<account name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="f6bdc-159">**參數**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-159">**Parameters**</span></span>  
  
|<span data-ttu-id="f6bdc-160">參數</span><span class="sxs-lookup"><span data-stu-id="f6bdc-160">Parameter</span></span>|<span data-ttu-id="f6bdc-161">Description</span><span class="sxs-lookup"><span data-stu-id="f6bdc-161">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6bdc-162">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-162">View:\<view name></span></span>|<span data-ttu-id="f6bdc-163">指定警示所在檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-163">The name of the view on which the alert is specified.</span></span>|  
|<span data-ttu-id="f6bdc-164">警示：\<警示名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-164">Alert:\<alert name></span></span>|<span data-ttu-id="f6bdc-165">警示的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-165">The name of the alert.</span></span>|  
|<span data-ttu-id="f6bdc-166">AccountName:\<帳戶名稱 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-166">AccountName:\<account name></span></span>|<span data-ttu-id="f6bdc-167">要從警示移除的帳戶，格式為「網域\使用者」。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-167">The account, in domain\user format, to remove from the alert.</span></span>|  
|<span data-ttu-id="f6bdc-168">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-168">Server:\<server></span></span>|<span data-ttu-id="f6bdc-169">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-169">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="f6bdc-170">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-170">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="f6bdc-171">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-171">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="f6bdc-172">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="f6bdc-172">Database:\<database></span></span>|<span data-ttu-id="f6bdc-173">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-173">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="f6bdc-174">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-174">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="f6bdc-175">從指定的警示移除指定之帳戶的訂閱。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-175">Removes the subscription of the specified account from the specified alert.</span></span> <span data-ttu-id="f6bdc-176">指定之帳戶的所有訂閱都將移除。</span><span class="sxs-lookup"><span data-stu-id="f6bdc-176">All subscriptions for the specified account are removed.</span></span>  
  
 <span data-ttu-id="f6bdc-177">**範例**</span><span class="sxs-lookup"><span data-stu-id="f6bdc-177">**Examples**</span></span>  
  
```  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:domain\user  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:user -Server:s1  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6bdc-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6bdc-178">See Also</span></span>  
 [<span data-ttu-id="f6bdc-179">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="f6bdc-179">BAM Management Utility</span></span>](../core/bam-management-utility.md)