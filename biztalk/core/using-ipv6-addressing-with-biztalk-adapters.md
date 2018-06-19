---
title: BizTalk 配接器搭配使用 IPv6 定址 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93cd2ead-5e87-47ac-8f78-d56b80afd34e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5726d5b05c548fd728228fcad39e56ce535fbb5
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710621"
---
# <a name="using-ipv6-addressing-with-biztalk-adapters"></a><span data-ttu-id="84a22-102">BizTalk 配接器搭配使用 IPv6 定址</span><span class="sxs-lookup"><span data-stu-id="84a22-102">Using IPv6 Addressing with BizTalk Adapters</span></span>
<span data-ttu-id="84a22-103">BizTalk Server 配接器支援使用 IPv6 定址。</span><span class="sxs-lookup"><span data-stu-id="84a22-103">BizTalk Server adapters support the use of IPv6 addressing.</span></span> <span data-ttu-id="84a22-104">本主題說明指定 UNC 路徑的 IPv6 位址時應該使用的術語表、指定常值 IPv6 位址時必須使用的術語表，以及與 HTTP 和 SOAP 配接器搭配使用 IPv6 範圍識別項。</span><span class="sxs-lookup"><span data-stu-id="84a22-104">This topic describes the nomenclature that should be used to specify an IPv6 address for a UNC path, the nomenclature for specifying a literal IPv6 address, and the use of IPv6 scope identifiers with the HTTP and SOAP adapters.</span></span>  
  
## <a name="ipv6-address-nomenclature-used-for-a-unc-path"></a><span data-ttu-id="84a22-105">UNC 路徑所用的 IPv6 位址術語表</span><span class="sxs-lookup"><span data-stu-id="84a22-105">IPv6 Address Nomenclature Used for a UNC Path</span></span>  
 <span data-ttu-id="84a22-106">指定 UNC 路徑中的常值 IPv6 位址時，請遵循這些步驟：</span><span class="sxs-lookup"><span data-stu-id="84a22-106">Follow these steps when specifying a literal IPv6 address in a UNC path:</span></span>  
  
1.  <span data-ttu-id="84a22-107">取代任何冒號":"取代任何冒號"-"字元。</span><span class="sxs-lookup"><span data-stu-id="84a22-107">Replace any colon ":" characters with a dash "-" character.</span></span>  
  
2.  <span data-ttu-id="84a22-108">將文字附加"**.ipv6-literal.net**」 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="84a22-108">Append the text "**.ipv6-literal.net**" to the IP address.</span></span>  
  
 <span data-ttu-id="84a22-109">例如，URI 若指向 IPv6 位址為 2001:DB8:2a:1005:230:48ff:fe73:989d 之電腦的檔案共用，其術語表為：</span><span class="sxs-lookup"><span data-stu-id="84a22-109">For example, the nomenclature for a URI that points to a file share on a computer with the IPv6 address 2001:DB8:2a:1005:230:48ff:fe73:989d would be:</span></span>  
  
```  
\\2001-DB8-2a-1005-230-48ff-fe73-989d.ipv6-literal.net\<sharename\>  
```  
  
 <span data-ttu-id="84a22-110">其中\< *sharename* \>是目標電腦上的檔案共用的名稱。</span><span class="sxs-lookup"><span data-stu-id="84a22-110">Where \<*sharename*\> is the name of the file share on the target computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84a22-111">執行 File 傳送和接收處理常式之主控件執行個體的使用者帳戶，一定要有檔案共用的適當權限。</span><span class="sxs-lookup"><span data-stu-id="84a22-111">Ensure that the user accounts for the host instances that the File send and receive handlers are running in have appropriate permissions to the file share.</span></span> <span data-ttu-id="84a22-112">如需 File 配接器接收檔案的資料夾權限的詳細資訊請參閱[設定 File 接收處理常式](../core/configure-the-file-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="84a22-112">For more information about the folder permissions required to receive files with the File adapter see [Configure a File Receive Handler](../core/configure-the-file-adapter.md).</span></span> <span data-ttu-id="84a22-113">如需有關傳送 File 配接器的檔案時所需的資料夾權限，請參閱[File 配接器的已知問題](../core/known-issues-with-the-file-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="84a22-113">For more information about the folder permissions required when sending files with the File adapter see [Known Issues with the File Adapter](../core/known-issues-with-the-file-adapter.md).</span></span> <span data-ttu-id="84a22-114">支援使用 File 配接器的檔案系統的相關資訊，請參閱 [http://support.microsoft.com/kb/815070](http://support.microsoft.com/kb/815070)。</span><span class="sxs-lookup"><span data-stu-id="84a22-114">For information about the file systems that are supported for use with the File adapter, see [http://support.microsoft.com/kb/815070](http://support.microsoft.com/kb/815070).</span></span>  
  
## <a name="using-ipv6-scope-identifiers-with-the-http-adapter-and-the-soap-send-adapter"></a><span data-ttu-id="84a22-115">與 HTTP 配接器和 SOAP 傳送配接器搭配使用 IPv6 範圍識別項</span><span class="sxs-lookup"><span data-stu-id="84a22-115">Using IPv6 Scope Identifiers with the HTTP Adapter and the SOAP Send Adapter</span></span>  
 <span data-ttu-id="84a22-116">HTTP 傳送和接收配接器和 SOAP 傳送配接器需要，如果使用 IPv6 位址範圍識別項時，範圍識別項必須使用逸出的逸出程式碼 **%25**。</span><span class="sxs-lookup"><span data-stu-id="84a22-116">The HTTP send and receive adapter and the SOAP send adapter require that if a scope identifier is used in an IPv6 address, the scope identifier must be escaped with the escape code **%25**.</span></span> <span data-ttu-id="84a22-117">例如， **fe80::550c:489f:e65e:aef3 %8** 是有效的 IPv6 位址包含範圍識別項 (%8)。</span><span class="sxs-lookup"><span data-stu-id="84a22-117">For example, **fe80::550c:489f:e65e:aef3%8** is a valid IPv6 address containing a scope identifier (%8).</span></span> <span data-ttu-id="84a22-118">若要將此 IPv6 位址搭配使用 HTTP 傳送和接收配接器或 SOAP 傳送配接器，範圍識別項必須跳過，如下所示：</span><span class="sxs-lookup"><span data-stu-id="84a22-118">To use this IPv6 address with the HTTP send and receive adapters or the SOAP send adapter, the scope identifier must be escaped as follows:</span></span>  
  
```  
fe80::550c:489f:e65e:aef3%258  
```  
  
## <a name="adapter-uri-nomenclature-used-for-a-literal-ipv6-address"></a><span data-ttu-id="84a22-119">常值 IPv6 位址所用的配接器 URI 術語表</span><span class="sxs-lookup"><span data-stu-id="84a22-119">Adapter URI Nomenclature Used for a Literal IPv6 Address</span></span>  
  
-   <span data-ttu-id="84a22-120">配接器 URI 若要使用常值 IPv6 位址，必須使用方括號 "[" 和 "]" 括住 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="84a22-120">To use a literal IPv6 address for an adapter URI, enclose the IP address in square brackets "[", "]".</span></span> <span data-ttu-id="84a22-121">例如，URI 含 IPv6 位址 2001:DB8:2a:1005:230:48ff:fe73:989d 的術語表為：</span><span class="sxs-lookup"><span data-stu-id="84a22-121">For example, the nomenclature for a URI with the IPv6 address 2001:DB8:2a:1005:230:48ff:fe73:989d would be:</span></span>  
  
    ```  
    [2001:DB8:2a:1005:230:48ff:fe73:989d]  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="84a22-122">使用常值 IPv6 位址會遵循配接器 Uri 中所建立的指導方針 [RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375)。</span><span class="sxs-lookup"><span data-stu-id="84a22-122">The use of literal IPv6 addresses for adapter URIs follows the guidelines established in [RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375).</span></span>  
  
-   <span data-ttu-id="84a22-123">指定常值 IPv6 位址做為 POP3 接收配接器、SMTP 傳送配接器，或 SQL 傳送和接收配接器的伺服器名稱時，不應使用方括號括住 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="84a22-123">When specifying a literal IPv6 address as the server name for the POP3 receive adapter, the SMTP send adapter, or the SQL send and receive adapters, the IPv6 address should not be enclosed in square brackets.</span></span>  
  
## <a name="summary-of-considerations-when-using-literal-ipv6-addressing-with-biztalk-adapters"></a><span data-ttu-id="84a22-124">常值 IPv6 定址與 BizTalk 配接器搭配使用時之考量的摘要</span><span class="sxs-lookup"><span data-stu-id="84a22-124">Summary of Considerations When Using Literal IPv6 Addressing with BizTalk Adapters</span></span>  
 <span data-ttu-id="84a22-125">下表摘要說明，使用常值 IPv6 位址何時需要以方括號 "[" 和 "]" 括住 IP 位址，以及何時必須跳過用於 IPv6 位址中的範圍識別項：</span><span class="sxs-lookup"><span data-stu-id="84a22-125">The table below summarizes when the use of a literal IPv6 address requires that the IP address is enclosed in square brackets "[", "]" and when a scope identifier that is used in an IPv6 address must be escaped:</span></span>  
  
|<span data-ttu-id="84a22-126">配接器</span><span class="sxs-lookup"><span data-stu-id="84a22-126">Adapter</span></span>|<span data-ttu-id="84a22-127">常值 IPv6 位址必須以方括號括住嗎？</span><span class="sxs-lookup"><span data-stu-id="84a22-127">Requires that literal IPv6 address is enclosed in square brackets?</span></span>|<span data-ttu-id="84a22-128">範圍識別項必須跳過嗎？</span><span class="sxs-lookup"><span data-stu-id="84a22-128">Requires that scope identifier is escaped?</span></span>|  
|---|---|---|  
|<span data-ttu-id="84a22-129">POP3 接收</span><span class="sxs-lookup"><span data-stu-id="84a22-129">POP3 receive</span></span>|<span data-ttu-id="84a22-130">否</span><span class="sxs-lookup"><span data-stu-id="84a22-130">No</span></span>|<span data-ttu-id="84a22-131">否</span><span class="sxs-lookup"><span data-stu-id="84a22-131">No</span></span>|  
|<span data-ttu-id="84a22-132">SMTP 傳送</span><span class="sxs-lookup"><span data-stu-id="84a22-132">SMTP send</span></span>|<span data-ttu-id="84a22-133">否</span><span class="sxs-lookup"><span data-stu-id="84a22-133">No</span></span>|<span data-ttu-id="84a22-134">否</span><span class="sxs-lookup"><span data-stu-id="84a22-134">No</span></span>|  
|<span data-ttu-id="84a22-135">SQL 傳送和接收</span><span class="sxs-lookup"><span data-stu-id="84a22-135">SQL send and receive</span></span>|<span data-ttu-id="84a22-136">否</span><span class="sxs-lookup"><span data-stu-id="84a22-136">No</span></span>|<span data-ttu-id="84a22-137">否</span><span class="sxs-lookup"><span data-stu-id="84a22-137">No</span></span>|  
|<span data-ttu-id="84a22-138">File 傳送和接收</span><span class="sxs-lookup"><span data-stu-id="84a22-138">File send and receive</span></span>|<span data-ttu-id="84a22-139">否 (請參見 **IPv6 位址術語表用於 UNC 路徑**)</span><span class="sxs-lookup"><span data-stu-id="84a22-139">No (see section **IPv6 Address Nomenclature Used for a UNC Path**)</span></span>|<span data-ttu-id="84a22-140">否</span><span class="sxs-lookup"><span data-stu-id="84a22-140">No</span></span>|  
|<span data-ttu-id="84a22-141">HTTP 傳送和接收</span><span class="sxs-lookup"><span data-stu-id="84a22-141">HTTP send and receive</span></span>|<span data-ttu-id="84a22-142">是</span><span class="sxs-lookup"><span data-stu-id="84a22-142">Yes</span></span>|<span data-ttu-id="84a22-143">是</span><span class="sxs-lookup"><span data-stu-id="84a22-143">Yes</span></span>|  
|<span data-ttu-id="84a22-144">MQSeries 傳送和接收</span><span class="sxs-lookup"><span data-stu-id="84a22-144">MQSeries send and receive</span></span>|<span data-ttu-id="84a22-145">是</span><span class="sxs-lookup"><span data-stu-id="84a22-145">Yes</span></span>|<span data-ttu-id="84a22-146">否</span><span class="sxs-lookup"><span data-stu-id="84a22-146">No</span></span>|  
|<span data-ttu-id="84a22-147">MSMQ 傳送和接收</span><span class="sxs-lookup"><span data-stu-id="84a22-147">MSMQ send and receive</span></span>|<span data-ttu-id="84a22-148">是</span><span class="sxs-lookup"><span data-stu-id="84a22-148">Yes</span></span>|<span data-ttu-id="84a22-149">否</span><span class="sxs-lookup"><span data-stu-id="84a22-149">No</span></span>|  
|<span data-ttu-id="84a22-150">SOAP 傳送</span><span class="sxs-lookup"><span data-stu-id="84a22-150">SOAP send</span></span>|<span data-ttu-id="84a22-151">是</span><span class="sxs-lookup"><span data-stu-id="84a22-151">Yes</span></span>|<span data-ttu-id="84a22-152">是</span><span class="sxs-lookup"><span data-stu-id="84a22-152">Yes</span></span>|  
|<span data-ttu-id="84a22-153">SOAP 接收</span><span class="sxs-lookup"><span data-stu-id="84a22-153">SOAP receive</span></span>|<span data-ttu-id="84a22-154">是</span><span class="sxs-lookup"><span data-stu-id="84a22-154">Yes</span></span>|<span data-ttu-id="84a22-155">否</span><span class="sxs-lookup"><span data-stu-id="84a22-155">No</span></span>|  
|<span data-ttu-id="84a22-156">WCF 傳送和接收</span><span class="sxs-lookup"><span data-stu-id="84a22-156">WCF send and receive</span></span>|<span data-ttu-id="84a22-157">是</span><span class="sxs-lookup"><span data-stu-id="84a22-157">Yes</span></span>|<span data-ttu-id="84a22-158">否</span><span class="sxs-lookup"><span data-stu-id="84a22-158">No</span></span>|