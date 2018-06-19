---
title: HTTP 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AffiliateApplicationName property [HTTP adapters]
- Certificate property [HTTP adapters]
- Password property [HTTP adapters]
- HTTP adapters, properties
- InboundHttpHeaders property [HTTP adapters]
- UseHandlerProxySettings property [HTTP adapters]
- configuring [HTTP adapters], properties
- schemas, HTTP adapters
- RequestTimeout property [HTTP adapters]
- ProxyPassword property [HTTP adapters]
- UseSSO property [HTTP adapters]
- HTTP adapters, schemas
- AuthenticationScheme property [HTTP adapters]
- ProxyName property [HTTP adapters]
- ProxyPort property [HTTP adapters]
- UseProxy property [HTTP adapters]
- configuring [HTTP adapters], schemas
- ContentType property [HTTP adapters]
- MaxRedirects property [HTTP adapters]
- ProxyUsername property [HTTP adapters]
- UserName property, HTTP adapters
ms.assetid: c9b50a82-8cb1-4521-9cf3-5fd77a3531e1
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 416ad39e804a4907dc39c7cef941e9a1bb57d3dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257422"
---
# <a name="http-adapter-property-schema-and-properties"></a><span data-ttu-id="b874e-102">HTTP 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="b874e-102">HTTP Adapter Property Schema and Properties</span></span>
<span data-ttu-id="b874e-103">下表列出 HTTP 配接器屬性結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="b874e-103">The following table lists the properties in the HTTP adapter property schema.</span></span>  
  
 <span data-ttu-id="b874e-104">**命名空間：** http://schemas.microsoft.com/BizTalk/2003/http-properties</span><span class="sxs-lookup"><span data-stu-id="b874e-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/http-properties</span></span>  
  
|<span data-ttu-id="b874e-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b874e-105">Name</span></span>|<span data-ttu-id="b874e-106">型別</span><span class="sxs-lookup"><span data-stu-id="b874e-106">Type</span></span>|<span data-ttu-id="b874e-107">Description</span><span class="sxs-lookup"><span data-stu-id="b874e-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="b874e-108">**ProxyName**</span><span class="sxs-lookup"><span data-stu-id="b874e-108">**ProxyName**</span></span>|<span data-ttu-id="b874e-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-109">xs:string</span></span>|<span data-ttu-id="b874e-110">指定 Proxy 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b874e-110">Specifies the proxy server name.</span></span>|  
|<span data-ttu-id="b874e-111">**ProxyPort**</span><span class="sxs-lookup"><span data-stu-id="b874e-111">**ProxyPort**</span></span>|<span data-ttu-id="b874e-112">xs:int</span><span class="sxs-lookup"><span data-stu-id="b874e-112">xs:int</span></span>|<span data-ttu-id="b874e-113">指定 Proxy 伺服器連接埠。</span><span class="sxs-lookup"><span data-stu-id="b874e-113">Specifies the proxy server port.</span></span>|  
|<span data-ttu-id="b874e-114">**UseHandlerProxySettings**</span><span class="sxs-lookup"><span data-stu-id="b874e-114">**UseHandlerProxySettings**</span></span>|<span data-ttu-id="b874e-115">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="b874e-115">xs:boolean</span></span>|<span data-ttu-id="b874e-116">指定 HTTP 傳送埠是否要對處理常式使用 Proxy 組態。</span><span class="sxs-lookup"><span data-stu-id="b874e-116">Specifies whether the HTTP send port uses the proxy configuration for the handler.</span></span>|  
|<span data-ttu-id="b874e-117">**UseProxy**</span><span class="sxs-lookup"><span data-stu-id="b874e-117">**UseProxy**</span></span>|<span data-ttu-id="b874e-118">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="b874e-118">xs:boolean</span></span>|<span data-ttu-id="b874e-119">指定 HTTP 配接器是否使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b874e-119">Specifies whether HTTP adapter uses the proxy server.</span></span>|  
|<span data-ttu-id="b874e-120">**RequestTimeout**</span><span class="sxs-lookup"><span data-stu-id="b874e-120">**RequestTimeout**</span></span>|<span data-ttu-id="b874e-121">xs:int</span><span class="sxs-lookup"><span data-stu-id="b874e-121">xs:int</span></span>|<span data-ttu-id="b874e-122">等待伺服器回應的逾時期間。</span><span class="sxs-lookup"><span data-stu-id="b874e-122">Time-out period of waiting for a response from the server.</span></span> <span data-ttu-id="b874e-123">若此屬性設定為零 (0)，則系統會根據要求訊息的大小來計算逾時。</span><span class="sxs-lookup"><span data-stu-id="b874e-123">If this property is set to zero (0), the system calculates the time-out on the request message size.</span></span>|  
|<span data-ttu-id="b874e-124">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="b874e-124">**Username**</span></span>|<span data-ttu-id="b874e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-125">xs:string</span></span>|<span data-ttu-id="b874e-126">要提供給伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b874e-126">The user name to use for authentication with the server.</span></span>|  
|<span data-ttu-id="b874e-127">**密碼**</span><span class="sxs-lookup"><span data-stu-id="b874e-127">**Password**</span></span>|<span data-ttu-id="b874e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-128">xs:string</span></span>|<span data-ttu-id="b874e-129">要提供給伺服器驗證的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="b874e-129">The user password to use for authentication with the server.</span></span>|  
|<span data-ttu-id="b874e-130">**ProxyUsername**</span><span class="sxs-lookup"><span data-stu-id="b874e-130">**ProxyUsername**</span></span>|<span data-ttu-id="b874e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-131">xs:string</span></span>|<span data-ttu-id="b874e-132">指定要用於 Proxy 伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b874e-132">Specifies the user name for authentication with the proxy server.</span></span>|  
|<span data-ttu-id="b874e-133">**ProxyPassword**</span><span class="sxs-lookup"><span data-stu-id="b874e-133">**ProxyPassword**</span></span>|<span data-ttu-id="b874e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-134">xs:string</span></span>|<span data-ttu-id="b874e-135">指定要用於 Proxy 伺服器驗證的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="b874e-135">Specifies the user password for authentication with the proxy server.</span></span>|  
|<span data-ttu-id="b874e-136">**MaxRedirects**</span><span class="sxs-lookup"><span data-stu-id="b874e-136">**MaxRedirects**</span></span>|<span data-ttu-id="b874e-137">xs:int</span><span class="sxs-lookup"><span data-stu-id="b874e-137">xs:int</span></span>|<span data-ttu-id="b874e-138">HTTP 配接器重新導向要求的次數上限。</span><span class="sxs-lookup"><span data-stu-id="b874e-138">The maximum number of times that the HTTP adapter will redirect the request.</span></span>|  
|<span data-ttu-id="b874e-139">**ContentType**</span><span class="sxs-lookup"><span data-stu-id="b874e-139">**ContentType**</span></span>|<span data-ttu-id="b874e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-140">xs:string</span></span>|<span data-ttu-id="b874e-141">要求訊息的內容類型。</span><span class="sxs-lookup"><span data-stu-id="b874e-141">Content type of the request messages.</span></span>|  
|<span data-ttu-id="b874e-142">**AuthenticationScheme**</span><span class="sxs-lookup"><span data-stu-id="b874e-142">**AuthenticationScheme**</span></span>|<span data-ttu-id="b874e-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-143">xs:string</span></span>|<span data-ttu-id="b874e-144">與目的地伺服器搭配使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b874e-144">Type of authentication to use with the destination server.</span></span>|  
|<span data-ttu-id="b874e-145">**[MSSQLSERVER 的通訊協定內容]**</span><span class="sxs-lookup"><span data-stu-id="b874e-145">**Certificate**</span></span>|<span data-ttu-id="b874e-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-146">xs:string</span></span>|<span data-ttu-id="b874e-147">用戶端 SSL 憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="b874e-147">Thumbprint of client SSL certificate.</span></span>|  
|<span data-ttu-id="b874e-148">**UseSSO**</span><span class="sxs-lookup"><span data-stu-id="b874e-148">**UseSSO**</span></span>|<span data-ttu-id="b874e-149">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="b874e-149">xs:boolean</span></span>|<span data-ttu-id="b874e-150">指定 HTTP 傳送埠是否要使用 SSO。</span><span class="sxs-lookup"><span data-stu-id="b874e-150">Specifies whether the HTTP send port will use SSO.</span></span>|  
|<span data-ttu-id="b874e-151">**AffiliateApplicationName**</span><span class="sxs-lookup"><span data-stu-id="b874e-151">**AffiliateApplicationName**</span></span>|<span data-ttu-id="b874e-152">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-152">xs:string</span></span>|<span data-ttu-id="b874e-153">SSO 使用之分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b874e-153">Name of affiliate application to use for SSO.</span></span>|  
|<span data-ttu-id="b874e-154">**InboundHttpHeaders**</span><span class="sxs-lookup"><span data-stu-id="b874e-154">**InboundHttpHeaders**</span></span>|<span data-ttu-id="b874e-155">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-155">xs:string</span></span>|<span data-ttu-id="b874e-156">包含來自輸入 HTTP 要求的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="b874e-156">Contains the HTTP headers from the inbound HTTP request.</span></span>|  
|<span data-ttu-id="b874e-157">**SubmissionHandle**</span><span class="sxs-lookup"><span data-stu-id="b874e-157">**SubmissionHandle**</span></span>|<span data-ttu-id="b874e-158">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-158">xs:string</span></span>|<span data-ttu-id="b874e-159">包含要求訊息的 BizTalk Server 相互關聯 Token (GUID)。</span><span class="sxs-lookup"><span data-stu-id="b874e-159">Contains the BizTalk Server correlation token (GUID) for the request message.</span></span>|  
|<span data-ttu-id="b874e-160">**EnableChunkedEncoding**</span><span class="sxs-lookup"><span data-stu-id="b874e-160">**EnableChunkedEncoding**</span></span>|<span data-ttu-id="b874e-161">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="b874e-161">xs:boolean</span></span>|<span data-ttu-id="b874e-162">指定 HTTP 配接器是否會使用區塊編碼。</span><span class="sxs-lookup"><span data-stu-id="b874e-162">Specifies whether or not chunked encoding is used by the HTTP adapter.</span></span>|  
|<span data-ttu-id="b874e-163">**UserHttpHeaders**</span><span class="sxs-lookup"><span data-stu-id="b874e-163">**UserHttpHeaders**</span></span>|<span data-ttu-id="b874e-164">xs:string</span><span class="sxs-lookup"><span data-stu-id="b874e-164">xs:string</span></span>|<span data-ttu-id="b874e-165">包含 HTTP 要求或回應訊息中內含的自訂標頭</span><span class="sxs-lookup"><span data-stu-id="b874e-165">Contains the customized headers contained in the HTTP request or response message</span></span><br /><br /> <span data-ttu-id="b874e-166">值**UserHttpHeaders**屬性必須具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="b874e-166">The value of the **UserHttpHeaders** property must have the following format:</span></span><br /><br /> `Header1: value\r\nHeader2: value\r\n`<br /><br /> <span data-ttu-id="b874e-167">**請注意**放置冒號 （:） 和標頭的值之間的空格字元 （）。</span><span class="sxs-lookup"><span data-stu-id="b874e-167">**Note** Put a colon (:) and a SPACE character ( ) between the header and the value.</span></span> <span data-ttu-id="b874e-168">空白標頭將會篩除項目。可以使用空值。</span><span class="sxs-lookup"><span data-stu-id="b874e-168">An empty header will cause the entry to be filtered out. An empty value is okay.</span></span><br /><br /> <span data-ttu-id="b874e-169">您可以修改下列五個標準 HTTP 標頭使用**UserHttpHeaders**屬性：</span><span class="sxs-lookup"><span data-stu-id="b874e-169">You can modify the following five standard HTTP headers by using the **UserHttpHeaders** property:</span></span><br /><br /> <span data-ttu-id="b874e-170">接受</span><span class="sxs-lookup"><span data-stu-id="b874e-170">- Accept</span></span><br /><br /> <span data-ttu-id="b874e-171">-查閱者</span><span class="sxs-lookup"><span data-stu-id="b874e-171">- Referrer</span></span><br /><br /> <span data-ttu-id="b874e-172">-預期</span><span class="sxs-lookup"><span data-stu-id="b874e-172">- Expect</span></span><br /><br /> <span data-ttu-id="b874e-173">-如果-修改-自</span><span class="sxs-lookup"><span data-stu-id="b874e-173">- If-Modified-Since</span></span><br /><br /> <span data-ttu-id="b874e-174">-使用者代理程式</span><span class="sxs-lookup"><span data-stu-id="b874e-174">- User-Agent</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b874e-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b874e-175">See Also</span></span>  
 [<span data-ttu-id="b874e-176">設定 HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="b874e-176">Configuring the HTTP Adapter</span></span>](../core/configuring-the-http-adapter.md)