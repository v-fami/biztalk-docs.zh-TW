---
title: 如何變更單一登入介面的行為 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4a4946a-e345-4c7e-835d-a3f7f72ebaca
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29f8adf1be531b5d439200dd2a10667ecf72bfbf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000815"
---
# <a name="how-to-change-the-behavior-of-a-single-sign-on-interface"></a><span data-ttu-id="194dc-102">如何變更單一登入介面的行為</span><span class="sxs-lookup"><span data-stu-id="194dc-102">How to Change the Behavior of a Single Sign-On Interface</span></span>
<span data-ttu-id="194dc-103">「企業單一登入」(SSO) 物件模型中的許多物件都會公開 IPropertyBag 介面，此介面可讓您修改指定物件的行為。</span><span class="sxs-lookup"><span data-stu-id="194dc-103">Many of the objects in the Enterprise Single Sign-On (SSO) object model expose the IPropertyBag interface, which allows you to modify the behavior of the specified object.</span></span> <span data-ttu-id="194dc-104">如果在 SSO 物件上呼叫 QueryInterface，則可以擷取 IPropertyBag 介面，並將其用來變更目前物件的行為。</span><span class="sxs-lookup"><span data-stu-id="194dc-104">If you call QueryInterface on an SSO object, you can retrieve the IPropertyBag interface and use it to change the behavior of your current object.</span></span>  

### <a name="to-change-the-behavior-for-a-specified-sso-interface"></a><span data-ttu-id="194dc-105">變更指定 SSO 介面的行為</span><span class="sxs-lookup"><span data-stu-id="194dc-105">To change the behavior for a specified SSO interface</span></span>  

1.  <span data-ttu-id="194dc-106">在指定的介面上使用 QueryInterface 來擷取 IPropertyBag 執行個體。</span><span class="sxs-lookup"><span data-stu-id="194dc-106">Use QueryInterface on the specified interface to retrieve an IPropertyBag instance.</span></span>  

2.  <span data-ttu-id="194dc-107">使用 IPropertyBag.Write 來設定介面的屬性、類型及值。</span><span class="sxs-lookup"><span data-stu-id="194dc-107">Use IPropertyBag.Write to set the property, type, and value for the interface.</span></span>  

     <span data-ttu-id="194dc-108">下表說明 IPropertyBag propName 和 ptrVar 參數的有效值。</span><span class="sxs-lookup"><span data-stu-id="194dc-108">The following table describes the valid values for the IPropertyBag propName and ptrVar parameters.</span></span>  

|<span data-ttu-id="194dc-109">propName</span><span class="sxs-lookup"><span data-stu-id="194dc-109">propName</span></span>|<span data-ttu-id="194dc-110">類型</span><span class="sxs-lookup"><span data-stu-id="194dc-110">Type</span></span>|<span data-ttu-id="194dc-111">ptrValue</span><span class="sxs-lookup"><span data-stu-id="194dc-111">ptrValue</span></span>|<span data-ttu-id="194dc-112">可用於</span><span class="sxs-lookup"><span data-stu-id="194dc-112">Usable On</span></span>|  
|--------------|----------|--------------|---------------|  
|<span data-ttu-id="194dc-113">CurrentSSOServer</span><span class="sxs-lookup"><span data-stu-id="194dc-113">CurrentSSOServer</span></span>|<span data-ttu-id="194dc-114">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="194dc-114">VT_BSTR</span></span>|<span data-ttu-id="194dc-115">要將資訊傳送至的伺服器的名稱</span><span class="sxs-lookup"><span data-stu-id="194dc-115">Name of the server to send the information to</span></span>|<span data-ttu-id="194dc-116">All</span><span class="sxs-lookup"><span data-stu-id="194dc-116">All</span></span>|  
|<span data-ttu-id="194dc-117">Transaction</span><span class="sxs-lookup"><span data-stu-id="194dc-117">Transaction</span></span>|<span data-ttu-id="194dc-118">VT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="194dc-118">VT_UNKNOWN</span></span><br /><br /> <span data-ttu-id="194dc-119">VT_EMPTY</span><span class="sxs-lookup"><span data-stu-id="194dc-119">VT_EMPTY</span></span>|<span data-ttu-id="194dc-120">DTC ITransaction 指標，或 NULL 以清除範圍。</span><span class="sxs-lookup"><span data-stu-id="194dc-120">A DTC ITransaction pointer, or NULL to clear the scope.</span></span>|<span data-ttu-id="194dc-121">ISSOConfigStore::SetConfigInfo</span><span class="sxs-lookup"><span data-stu-id="194dc-121">ISSOConfigStore::SetConfigInfo</span></span><br /><span data-ttu-id="194dc-122">ISSOConfigStore::GetConfigInfo</span><span class="sxs-lookup"><span data-stu-id="194dc-122">ISSOConfigStore::GetConfigInfo</span></span> <br /><span data-ttu-id="194dc-123">ISSOConfigStore::DeleteConfigInfo</span><span class="sxs-lookup"><span data-stu-id="194dc-123">ISSOConfigStore::DeleteConfigInfo</span></span><br /><br /> <span data-ttu-id="194dc-124">ISSOAdmin::CreateApplication</span><span class="sxs-lookup"><span data-stu-id="194dc-124">ISSOAdmin::CreateApplication</span></span><br /><span data-ttu-id="194dc-125">ISSOAdmin::DeleteApplication</span><span class="sxs-lookup"><span data-stu-id="194dc-125">ISSOAdmin::DeleteApplication</span></span> <br /><span data-ttu-id="194dc-126">ISSOAdmin::UpdateApplication</span><span class="sxs-lookup"><span data-stu-id="194dc-126">ISSOAdmin::UpdateApplication</span></span><br /><span data-ttu-id="194dc-127">ISSOAdmin::CreateFieldInfo</span><span class="sxs-lookup"><span data-stu-id="194dc-127">ISSOAdmin::CreateFieldInfo</span></span><br /><br /> <span data-ttu-id="194dc-128">ISSOMapper::GetFieldInfo</span><span class="sxs-lookup"><span data-stu-id="194dc-128">ISSOMapper::GetFieldInfo</span></span>|  
|<span data-ttu-id="194dc-129">AppFilterFlags</span><span class="sxs-lookup"><span data-stu-id="194dc-129">AppFilterFlags</span></span>|<span data-ttu-id="194dc-130">VT_I4</span><span class="sxs-lookup"><span data-stu-id="194dc-130">VT_I4</span></span><br /><br /> <span data-ttu-id="194dc-131">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="194dc-131">VT_UI4</span></span>|<span data-ttu-id="194dc-132">控制要篩選之應用程式的旗標。</span><span class="sxs-lookup"><span data-stu-id="194dc-132">Flags to control what application to filter.</span></span>|<span data-ttu-id="194dc-133">ISSOMapper::GetApplications</span><span class="sxs-lookup"><span data-stu-id="194dc-133">ISSOMapper::GetApplications</span></span><br /><br /> <span data-ttu-id="194dc-134">ISSOMapper2::GetApplications2</span><span class="sxs-lookup"><span data-stu-id="194dc-134">ISSOMapper2::GetApplications2</span></span>|  
|<span data-ttu-id="194dc-135">AppFilterFlagsMask</span><span class="sxs-lookup"><span data-stu-id="194dc-135">AppFilterFlagsMask</span></span>|<span data-ttu-id="194dc-136">VT_I4</span><span class="sxs-lookup"><span data-stu-id="194dc-136">VT_I4</span></span><br /><br /> <span data-ttu-id="194dc-137">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="194dc-137">VT_UI4</span></span>|<span data-ttu-id="194dc-138">控制要篩選之應用程式的旗標遮罩。</span><span class="sxs-lookup"><span data-stu-id="194dc-138">Flag mask to control what application to filter.</span></span>|<span data-ttu-id="194dc-139">ISSOMapper::GetApplications</span><span class="sxs-lookup"><span data-stu-id="194dc-139">ISSOMapper::GetApplications</span></span><br /><br /> <span data-ttu-id="194dc-140">ISSOMapper2::GetApplications2</span><span class="sxs-lookup"><span data-stu-id="194dc-140">ISSOMapper2::GetApplications2</span></span>|  
|<span data-ttu-id="194dc-141">AsyncCall</span><span class="sxs-lookup"><span data-stu-id="194dc-141">AsyncCall</span></span>|<span data-ttu-id="194dc-142">VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="194dc-142">VT_BOOL</span></span>|<span data-ttu-id="194dc-143">若為 True，則使用非同步 RPC 進行呼叫；若為 False，則使用同步 RPC。</span><span class="sxs-lookup"><span data-stu-id="194dc-143">True to call using an async RPC; false to use a synchronous RPC.</span></span>|<span data-ttu-id="194dc-144">ISSOConfigOM::GetServerStatus</span><span class="sxs-lookup"><span data-stu-id="194dc-144">ISSOConfigOM::GetServerStatus</span></span><br /><br /> <span data-ttu-id="194dc-145">ISSOAdmin::GetGlobalInfo</span><span class="sxs-lookup"><span data-stu-id="194dc-145">ISSOAdmin::GetGlobalInfo</span></span>|  

- <span data-ttu-id="194dc-146">**CurrentSSOServer**： 標準的行為，判斷哪個 SSO 將資訊傳送至伺服器，如下所示：</span><span class="sxs-lookup"><span data-stu-id="194dc-146">**CurrentSSOServer**: the standard behavior for determining which server to send SSO information to is as follows:</span></span>  

  1. <span data-ttu-id="194dc-147">在目前使用者的登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="194dc-147">Look in the registry for the current user.</span></span> <span data-ttu-id="194dc-148">可以使用命令列工具或 GUI，為目前的使用者設定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="194dc-148">The server name can be set for the current user using the command line tools or GUI.</span></span>  

  2. <span data-ttu-id="194dc-149">在所有使用者的登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="194dc-149">Look in the registry for all users.</span></span> <span data-ttu-id="194dc-150">可以使用命令列工具或 GUI，為所有的使用者設定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="194dc-150">The server name can be set for all users using the command line tools or GUI.</span></span>  

  3. <span data-ttu-id="194dc-151">如果在登錄中找不到 SSO 伺服器名稱，則使用目前的電腦。</span><span class="sxs-lookup"><span data-stu-id="194dc-151">If no SSO server name is found in the registry then use the current computer.</span></span>  

     <span data-ttu-id="194dc-152">將 CurrentSSOServer 設定為指定的伺服器會覆寫前述的指定介面程序。</span><span class="sxs-lookup"><span data-stu-id="194dc-152">Setting CurrentSSOServer to a specified server overrides the previous process for the specified interface.</span></span> <span data-ttu-id="194dc-153">一旦設定 CurrentSSOServer 之後，所有後續在該介面上的方法呼叫都會傳送到指定的伺服器。</span><span class="sxs-lookup"><span data-stu-id="194dc-153">Once you set CurrentSSOServer, all subsequent method calls on the interface will be sent to the specified server.</span></span>  

- <span data-ttu-id="194dc-154">**交易**： 指定 DTC 交易的範圍內執行的作業由 SSO 物件模型。</span><span class="sxs-lookup"><span data-stu-id="194dc-154">**Transaction**: specifies a DTC transaction that to scope the operations performed by the SSO object model.</span></span> <span data-ttu-id="194dc-155">您必須在 `ptrValue` 中傳遞 DTC ITransaction 指標，或 "null" 以清除目前的交易範圍。</span><span class="sxs-lookup"><span data-stu-id="194dc-155">You must pass a DTC ITransaction pointer in `ptrValue`, or "null" to clear the current transaction scope.</span></span>  

- <span data-ttu-id="194dc-156">**AppFilterFlags/AppFilterMask**： 控制項類型的應用程式將會從 ISSOMapper.GetApplications 和 ISSOMapper2.GetApplications 所傳回。</span><span class="sxs-lookup"><span data-stu-id="194dc-156">**AppFilterFlags/AppFilterMask**: controls what types of applications will be returned from ISSOMapper.GetApplications and ISSOMapper2.GetApplications.</span></span> <span data-ttu-id="194dc-157">如果應用程式旗標符合篩選器旗標和篩選器旗標遮罩所指定的旗標，它們就會傳回。</span><span class="sxs-lookup"><span data-stu-id="194dc-157">If the application flags match the flags specified by the filter flags and the filter flag mask they will be returned.</span></span> <span data-ttu-id="194dc-158">一種執行應用程式篩選的方式，是將 AppFilterFlagsMask 設定為 SSO_FLAG_APP_FILTER_BY_TYPE，然後再將 AppFilterFlags 設定為下列的一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="194dc-158">One way to perform application filtering is to set AppFilterFlagsMask to SSO_FLAG_APP_FILTER_BY_TYPE and to then set AppFilterFlags to one or more of the following:</span></span>  

   <span data-ttu-id="194dc-159">SSO_APP_TYPE_INDIVIDUAL</span><span class="sxs-lookup"><span data-stu-id="194dc-159">SSO_APP_TYPE_INDIVIDUAL</span></span>  

   <span data-ttu-id="194dc-160">SSO_APP_TYPE_GROUP</span><span class="sxs-lookup"><span data-stu-id="194dc-160">SSO_APP_TYPE_GROUP</span></span>  

   <span data-ttu-id="194dc-161">SSO_APP_TYPE_CONFIG_STORE</span><span class="sxs-lookup"><span data-stu-id="194dc-161">SSO_APP_TYPE_CONFIG_STORE</span></span>  

   <span data-ttu-id="194dc-162">SSO_APP_TYPE_HOST_GROUP</span><span class="sxs-lookup"><span data-stu-id="194dc-162">SSO_APP_TYPE_HOST_GROUP</span></span>  

   <span data-ttu-id="194dc-163">SSO_APP_TYPE_PS_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="194dc-163">SSO_APP_TYPE_PS_ADAPTER</span></span>  

   <span data-ttu-id="194dc-164">SSO_APP_TYPE_PS_GROUP_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="194dc-164">SSO_APP_TYPE_PS_GROUP_ADAPTER</span></span>  

- <span data-ttu-id="194dc-165">**AsyncCall**： 如果為 true，則 SSO 會執行，方法是使用非同步遠端程序呼叫 (RPC)。</span><span class="sxs-lookup"><span data-stu-id="194dc-165">**AsyncCall**: if true, then SSO will perform the method using an asynchronous remote procedure call (RPC).</span></span> <span data-ttu-id="194dc-166">此方法在進行時會傳回 E_PENDING。</span><span class="sxs-lookup"><span data-stu-id="194dc-166">The method will return E_PENDING while in progress.</span></span> <span data-ttu-id="194dc-167">任何其他的傳回值都代表方法已完成。</span><span class="sxs-lookup"><span data-stu-id="194dc-167">Any other return value indicates that the method is completed.</span></span> <span data-ttu-id="194dc-168">AsyncCall 也可讓您輪詢完成的方法。</span><span class="sxs-lookup"><span data-stu-id="194dc-168">AsyncCall also allows you to poll the method for completion.</span></span>
