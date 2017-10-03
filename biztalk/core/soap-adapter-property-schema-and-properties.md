---
title: "SOAP 配接器屬性結構描述和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ProxyUsername property [SOAP adapters]
- ClientConnectionTimeout property [SOAP adapters]
- SOAP adapters, properties
- ProxyAddress property [SOAP adapters]
- UserDefined property [SOAP adapters]
- AssemblyName property [SOAP adapters]
- ClientCertificate property [SOAP adapters]
- AffiliateApplicationName property [SOAP adapters]
- schemas, SOAP adapters
- AuthenticationScheme property [SOAP adapters]
- UserName property, SOAP adapters
- UseProxy property [SOAP adapters]
- Password property [SOAP adapters]
- configuring [SOAP adapters], schemas
- UnknownHeaders property [SOAP adapters]
- configuring [SOAP adapters], properties
- UseSoap12 property [SOAP adapters]
- UseHandlerSetting property [SOAP adapters]
- SOAP adapters, schemas
- ProxyPassword property [SOAP adapters]
- UseSSO property [SOAP adapters]
- MethodName property [SOAP adapters]
- ProxyPort property [SOAP adapters]
ms.assetid: b471cf4b-2d87-4aa2-ae4a-f48517fd4c94
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a24a9ccfc3a07abe925761fe2d6886646981be9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-property-schema-and-properties"></a><span data-ttu-id="ffb27-102">SOAP 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="ffb27-102">SOAP Adapter Property Schema and Properties</span></span>
<span data-ttu-id="ffb27-103">下表列出 SOAP 配接器屬性結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="ffb27-103">The following table lists the properties in the SOAP adapter property schema.</span></span>  
  
 <span data-ttu-id="ffb27-104">**命名空間：** http://schemas.microsoft.com/BizTalk/2003/soap-properties</span><span class="sxs-lookup"><span data-stu-id="ffb27-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/soap-properties</span></span>  
  
|<span data-ttu-id="ffb27-105">名稱</span><span class="sxs-lookup"><span data-stu-id="ffb27-105">Name</span></span>|<span data-ttu-id="ffb27-106">型別</span><span class="sxs-lookup"><span data-stu-id="ffb27-106">Type</span></span>|<span data-ttu-id="ffb27-107">Description</span><span class="sxs-lookup"><span data-stu-id="ffb27-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="ffb27-108">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="ffb27-108">**AssemblyName**</span></span>|<span data-ttu-id="ffb27-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-109">xs:string</span></span>|<span data-ttu-id="ffb27-110">識別要載入和執行的 .NET 類型與組件。</span><span class="sxs-lookup"><span data-stu-id="ffb27-110">Identifies the .NET type and assembly to be loaded and executed.</span></span>|  
|<span data-ttu-id="ffb27-111">**MethodName**</span><span class="sxs-lookup"><span data-stu-id="ffb27-111">**MethodName**</span></span>|<span data-ttu-id="ffb27-112">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-112">xs:string</span></span>|<span data-ttu-id="ffb27-113">識別在 .NET 組件上要叫用的目標方法。</span><span class="sxs-lookup"><span data-stu-id="ffb27-113">Identifies the target method on the .NET assembly that is to be invoked.</span></span>|  
|<span data-ttu-id="ffb27-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="ffb27-114">**Username**</span></span>|<span data-ttu-id="ffb27-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-115">xs:string</span></span>|<span data-ttu-id="ffb27-116">要提供給伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="ffb27-116">User name to use for authentication with the server.</span></span>|  
|<span data-ttu-id="ffb27-117">**密碼**</span><span class="sxs-lookup"><span data-stu-id="ffb27-117">**Password**</span></span>|<span data-ttu-id="ffb27-118">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-118">xs:string</span></span>|<span data-ttu-id="ffb27-119">要提供給伺服器驗證的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="ffb27-119">User password to use for authentication with the server.</span></span>|  
|<span data-ttu-id="ffb27-120">**ClientCertificate**</span><span class="sxs-lookup"><span data-stu-id="ffb27-120">**ClientCertificate**</span></span>|<span data-ttu-id="ffb27-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-121">xs:string</span></span>|<span data-ttu-id="ffb27-122">用戶端 SSL 憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="ffb27-122">Thumbprint of the client SSL certificate.</span></span>|  
|<span data-ttu-id="ffb27-123">**UseProxy**</span><span class="sxs-lookup"><span data-stu-id="ffb27-123">**UseProxy**</span></span>|<span data-ttu-id="ffb27-124">xs:Boolean</span><span class="sxs-lookup"><span data-stu-id="ffb27-124">xs:Boolean</span></span>|<span data-ttu-id="ffb27-125">指定 SOAP 配接器是否要使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ffb27-125">Specifies whether the SOAP adapter uses a proxy server.</span></span>|  
|<span data-ttu-id="ffb27-126">**ProxyAddress**</span><span class="sxs-lookup"><span data-stu-id="ffb27-126">**ProxyAddress**</span></span>|<span data-ttu-id="ffb27-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-127">xs:string</span></span>|<span data-ttu-id="ffb27-128">指定 Proxy 伺服器位址。</span><span class="sxs-lookup"><span data-stu-id="ffb27-128">Specifies the proxy server address.</span></span>|  
|<span data-ttu-id="ffb27-129">**ProxyPort**</span><span class="sxs-lookup"><span data-stu-id="ffb27-129">**ProxyPort**</span></span>|<span data-ttu-id="ffb27-130">xs:int</span><span class="sxs-lookup"><span data-stu-id="ffb27-130">xs:int</span></span>|<span data-ttu-id="ffb27-131">指定 Proxy 伺服器連接埠。</span><span class="sxs-lookup"><span data-stu-id="ffb27-131">Specifies the proxy server port.</span></span>|  
|<span data-ttu-id="ffb27-132">**ProxyUsername**</span><span class="sxs-lookup"><span data-stu-id="ffb27-132">**ProxyUsername**</span></span>|<span data-ttu-id="ffb27-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-133">xs:string</span></span>|<span data-ttu-id="ffb27-134">指定要用於 Proxy 伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="ffb27-134">Specifies the user name for authentication with the proxy server.</span></span>|  
|<span data-ttu-id="ffb27-135">**ProxyPassword**</span><span class="sxs-lookup"><span data-stu-id="ffb27-135">**ProxyPassword**</span></span>|<span data-ttu-id="ffb27-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-136">xs:string</span></span>|<span data-ttu-id="ffb27-137">指定要用於 Proxy 伺服器驗證的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="ffb27-137">Specifies the user password for authentication with the proxy server.</span></span>|  
|<span data-ttu-id="ffb27-138">**UnknownHeaders**</span><span class="sxs-lookup"><span data-stu-id="ffb27-138">**UnknownHeaders**</span></span>|<span data-ttu-id="ffb27-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-139">xs:string</span></span>|<span data-ttu-id="ffb27-140">指定未知 SOAP 標頭的序列化清單。</span><span class="sxs-lookup"><span data-stu-id="ffb27-140">Specifies the serialized list of unknown SOAP headers.</span></span>|  
|<span data-ttu-id="ffb27-141">**AffiliateApplicationName**</span><span class="sxs-lookup"><span data-stu-id="ffb27-141">**AffiliateApplicationName**</span></span>|<span data-ttu-id="ffb27-142">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-142">xs:string</span></span>|<span data-ttu-id="ffb27-143">定義 SSO 使用之分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffb27-143">Defines the name of the affiliate application to use for SSO.</span></span>|  
|<span data-ttu-id="ffb27-144">**AuthenticationScheme**</span><span class="sxs-lookup"><span data-stu-id="ffb27-144">**AuthenticationScheme**</span></span>|<span data-ttu-id="ffb27-145">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-145">xs:string</span></span>|<span data-ttu-id="ffb27-146">指定要提供給目的地伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ffb27-146">Specifies the type of authentication to use with the destination server.</span></span>|  
|<span data-ttu-id="ffb27-147">**UseSSO**</span><span class="sxs-lookup"><span data-stu-id="ffb27-147">**UseSSO**</span></span>|<span data-ttu-id="ffb27-148">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="ffb27-148">xs:boolean</span></span>|<span data-ttu-id="ffb27-149">指定 SOAP 配接器是否對傳送埠使用 SSO。</span><span class="sxs-lookup"><span data-stu-id="ffb27-149">Specifies whether the SOAP adapter uses SSO for the send port.</span></span>|  
|<span data-ttu-id="ffb27-150">**UseHandlerSetting**</span><span class="sxs-lookup"><span data-stu-id="ffb27-150">**UseHandlerSetting**</span></span>|<span data-ttu-id="ffb27-151">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="ffb27-151">xs:boolean</span></span>|<span data-ttu-id="ffb27-152">指定 SOAP 傳送埠是否要對處理常式使用 Proxy 組態。</span><span class="sxs-lookup"><span data-stu-id="ffb27-152">Specifies whether the SOAP send port uses the proxy configuration for the handler.</span></span>|  
|<span data-ttu-id="ffb27-153">**ClientConnectionTimeout**</span><span class="sxs-lookup"><span data-stu-id="ffb27-153">**ClientConnectionTimeout**</span></span>|<span data-ttu-id="ffb27-154">xs:int</span><span class="sxs-lookup"><span data-stu-id="ffb27-154">xs:int</span></span>|<span data-ttu-id="ffb27-155">指定等待伺服器回應的逾時期間。</span><span class="sxs-lookup"><span data-stu-id="ffb27-155">Specifies the time-out period of waiting for a response from the server.</span></span> <span data-ttu-id="ffb27-156">若設定為零 (0)，則系統會根據要求訊息的大小來計算逾時。</span><span class="sxs-lookup"><span data-stu-id="ffb27-156">If set to zero (0), the system will calculate the time-out based on the request message size.</span></span>|  
|<span data-ttu-id="ffb27-157">**UserDefined**</span><span class="sxs-lookup"><span data-stu-id="ffb27-157">**UserDefined**</span></span>|<span data-ttu-id="ffb27-158">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffb27-158">xs:string</span></span>|<span data-ttu-id="ffb27-159">定義使用者定義類別。</span><span class="sxs-lookup"><span data-stu-id="ffb27-159">Defines user-defined classes.</span></span>|  
|<span data-ttu-id="ffb27-160">**UseSoap12**</span><span class="sxs-lookup"><span data-stu-id="ffb27-160">**UseSoap12**</span></span>|<span data-ttu-id="ffb27-161">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="ffb27-161">xs:boolean</span></span>|<span data-ttu-id="ffb27-162">指定是否產生支援 SOAP 1.2 通訊協定的 Proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ffb27-162">Specifies whether to generate proxy code that supports the SOAP 1.2 protocol.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffb27-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffb27-163">See Also</span></span>  
 [<span data-ttu-id="ffb27-164">設定 SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="ffb27-164">Configuring the SOAP Adapter</span></span>](../core/configuring-the-soap-adapter.md)