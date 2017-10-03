---
title: "如何使用 Internet Explorer 測試已發佈的 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, receive locations
- Web services, Internet Explorer
- testing, Web services
- receive locations, modifying
- Web services, modifying
- modifying, Web.config file
- Web.config file
- Web services, Web.config file
- HTTP-GET
- Web services, testing
- Web services, HTTP-GET
- modifying, Web services
ms.assetid: 4dc2171d-4abe-43db-b4bc-e484048c6430
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 687078a14d8cb2163c9795c68f65171e7b82467c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-internet-explorer-to-test-a-published-web-service"></a><span data-ttu-id="57bb4-102">如何使用 Internet Explorer 測試已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="57bb4-102">How to Use Internet Explorer to Test a Published Web Service</span></span>
<span data-ttu-id="57bb4-103">您不需要撰寫 Web 用戶端應用程式，就可以測試已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="57bb4-103">You can test your published Web service without writing a Web client application.</span></span> <span data-ttu-id="57bb4-104">您可以使用如 Internet Explorer 這類 Web 瀏覽器來測試已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="57bb4-104">You can use a Web browser, such as Internet Explorer, to test your published Web service.</span></span> <span data-ttu-id="57bb4-105">雖然您可以使用 Web 瀏覽器來存取任何已發佈的 Web 服務，但只能測試擁有包含簡單型別參數之 Web 方法的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="57bb4-105">Although you can access any published Web service using a Web browser, you can only test Web services with Web methods that contain simple type parameters.</span></span> <span data-ttu-id="57bb4-106">若要在 Web 瀏覽器測試 Web 方法，用於接收埠的要求和回應訊息的訊息部分只能是簡單型別，例如**System.String**或**System.Int32**。</span><span class="sxs-lookup"><span data-stu-id="57bb4-106">To test your Web method in a Web browser, your message parts for the request and response messages that are used in the receive port can only be a simple type, such as **System.String** or **System.Int32**.</span></span> <span data-ttu-id="57bb4-107">如果任何訊息部分使用結構描述做為訊息類型，就不能使用瀏覽器測試 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="57bb4-107">If any message part uses a schema as a message type, you cannot test the Web method with a browser.</span></span>  
  
 <span data-ttu-id="57bb4-108">如果您要使用 HTTP-GET 或 HTTP-POST 測試已發佈的 Web 服務，則必須設定 SOAP 配接器的 BizTalk 接收位置，並修改已發佈之 Web 服務的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="57bb4-108">If you want to test your published Web services using HTTP-GET or HTTP-POST, you must configure your BizTalk receive location for the SOAP adapter and modify the Web.config file for your published Web service.</span></span>  
  
 <span data-ttu-id="57bb4-109">**修改接收位置**</span><span class="sxs-lookup"><span data-stu-id="57bb4-109">**Modifying the Receive Locations**</span></span>  
  
 <span data-ttu-id="57bb4-110">當 SOAP 配接器設定接收位置時，SOAP 配接器一般會指定虛擬目錄和 Web 服務的 .asmx 檔案名稱，來設定接收位置的 URI：</span><span class="sxs-lookup"><span data-stu-id="57bb4-110">When the SOAP adapter configures receive locations, the SOAP adapter normally sets the URI of the receive location by giving the virtual directory and the Web service .asmx file name:</span></span>  
  
```  
/PurchaseOrder/POOrchestration.asmx  
```  
  
 <span data-ttu-id="57bb4-111">這可讓 SOAP 配接器使用 HTTP-SOAP 通訊協定接收 Web 服務要求。</span><span class="sxs-lookup"><span data-stu-id="57bb4-111">This allows the SOAP adapter to receive Web service requests using the HTTP-SOAP protocol.</span></span> <span data-ttu-id="57bb4-112">若要設定接收位置使用 HTTP-GET 或 HTTP-POST 通訊協定，您必須將方法名稱附加到 URI：</span><span class="sxs-lookup"><span data-stu-id="57bb4-112">To configure the receive location to use the HTTP-GET or HTTP-POST protocol, you must append the method name to the URI:</span></span>  
  
```  
/PurchaseOrder/POOrchestration.asmx/Operation_1  
```  
  
 <span data-ttu-id="57bb4-113">方法名稱與協調流程中的連接埠作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="57bb4-113">The method name is the same as the port operation name in the orchestration.</span></span>  
  
 <span data-ttu-id="57bb4-114">**修改 Web.config 檔案**</span><span class="sxs-lookup"><span data-stu-id="57bb4-114">**Modifying the Web.config file**</span></span>  
  
 <span data-ttu-id="57bb4-115">根據預設，精靈會設定 Web 服務使用 HTTP-SOAP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="57bb4-115">By default, the wizard configures the Web services to use the HTTP-SOAP protocol.</span></span> <span data-ttu-id="57bb4-116">HTTP-GET 和 HTTP-POST 則會明確停用。</span><span class="sxs-lookup"><span data-stu-id="57bb4-116">HTTP-GET and HTTP-POST are explicitly disabled.</span></span> <span data-ttu-id="57bb4-117">若要使用 Web 瀏覽器測試 Web 服務，您必須啟用 HTTP-GET。</span><span class="sxs-lookup"><span data-stu-id="57bb4-117">To test a Web service with a Web browser, you must enable HTTP-GET.</span></span>  
  
### <a name="to-modify-the-webconfig-file-for-the-published-web-service"></a><span data-ttu-id="57bb4-118">若要修改已發佈之 Web 服務的 Web.config 檔案</span><span class="sxs-lookup"><span data-stu-id="57bb4-118">To modify the Web.config file for the published Web service</span></span>  
  
1.  <span data-ttu-id="57bb4-119">開啟已發佈之 Web 服務的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="57bb4-119">Open the Web.config file for the published Web service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57bb4-120">您可以在設成 IIS 虛擬根目錄來包含 Web 服務的目錄中找到 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="57bb4-120">You can find the Web.config file in the directory that you configured for the IIS virtual root that contains the Web service.</span></span>  
  
2.  <span data-ttu-id="57bb4-121">尋找\<通訊協定 > 一節：</span><span class="sxs-lookup"><span data-stu-id="57bb4-121">Find the \<protocols> section:</span></span>  
  
    ```  
    <webServices>  
       <protocols>  
         <remove name="HttpPost" />  
         <remove name="HttpGet" />  
         <remove name="HttpPostLocalhost" />  
       </protocols>  
  
    </webServices>  
    ```  
  
3.  <span data-ttu-id="57bb4-122">測試 HTTP-GET、 HTTP-POST 或從本機電腦的 HTTP-POST 移除對應的行，從\<通訊協定 > 一節。</span><span class="sxs-lookup"><span data-stu-id="57bb4-122">For testing HTTP-GET, HTTP-POST, or HTTP-POST from the local computer, remove the corresponding line from the \<protocols> section.</span></span>  
  
 <span data-ttu-id="57bb4-123">如需有關組態選項的詳細資訊，請參閱"組態選項的 Web 服務使用 ASP.NET 建立 XML 」 中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]協助處[http://go.microsoft.com/fwlink/?LinkId=62264](http://go.microsoft.com/fwlink/?LinkId=62264)。</span><span class="sxs-lookup"><span data-stu-id="57bb4-123">For more information about the configuration options, see "Configuration Options for XML Web Services Created Using ASP.NET" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62264](http://go.microsoft.com/fwlink/?LinkId=62264).</span></span>  
  
#### <a name="to-access-a-web-service-with-internet-explorer"></a><span data-ttu-id="57bb4-124">若要使用 Internet Explorer 存取 Web 服務</span><span class="sxs-lookup"><span data-stu-id="57bb4-124">To access a Web service with Internet Explorer</span></span>  
  
-   <span data-ttu-id="57bb4-125">在 Internet Explorer 中**位址**方塊中，輸入使用的格式為 Web 服務 URL  **http://*servername*/*apppath*/ *webservicename*.asmx * *。</span><span class="sxs-lookup"><span data-stu-id="57bb4-125">In Internet Explorer, in the **Address** box, type the URL for the Web service using the format **http://*servername*/*apppath*/*webservicename*.asmx**.</span></span>  
  
    |<span data-ttu-id="57bb4-126">參數</span><span class="sxs-lookup"><span data-stu-id="57bb4-126">Parameter</span></span>|<span data-ttu-id="57bb4-127">值</span><span class="sxs-lookup"><span data-stu-id="57bb4-127">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="57bb4-128">***伺服器名稱***</span><span class="sxs-lookup"><span data-stu-id="57bb4-128">***servername***</span></span>|<span data-ttu-id="57bb4-129">您已部署 XML Web Service 之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="57bb4-129">The name of the server that you have deployed your XML Web service.</span></span>|  
    |<span data-ttu-id="57bb4-130">***Apppath***</span><span class="sxs-lookup"><span data-stu-id="57bb4-130">***Apppath***</span></span>|<span data-ttu-id="57bb4-131">虛擬目錄的名稱和 Web 應用程式路徑。</span><span class="sxs-lookup"><span data-stu-id="57bb4-131">The name of your virtual directory and the Web application path.</span></span>|  
    |<span data-ttu-id="57bb4-132">***webservicename.asmx***</span><span class="sxs-lookup"><span data-stu-id="57bb4-132">***webservicename.asmx***</span></span>|<span data-ttu-id="57bb4-133">XML Web Service .asmx 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="57bb4-133">The name of the XML Web service .asmx file.</span></span>|  
  
 <span data-ttu-id="57bb4-134">Web 服務的描述會顯示該特定 Web 服務支援的所有 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="57bb4-134">The description for the Web service shows you all the Web service methods that the particular Web service supports.</span></span> <span data-ttu-id="57bb4-135">Web 服務描述頁面包含每個可用的 Web 方法和 Web 服務的服務描述的連結。</span><span class="sxs-lookup"><span data-stu-id="57bb4-135">The Web service description page contains links for each available Web method and the service description of the Web service.</span></span>  
  
#### <a name="to-test-a-web-service-with-internet-explorer-using-http-get"></a><span data-ttu-id="57bb4-136">若要使用 Internet Explorer 和 HTTP-GET 測試 Web 服務</span><span class="sxs-lookup"><span data-stu-id="57bb4-136">To test a Web service with Internet Explorer using HTTP-GET</span></span>  
  
1.  <span data-ttu-id="57bb4-137">存取 Web 服務描述頁面之後，按一下 Web 服務描述頁面中所列的其中一個 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="57bb4-137">After accessing the Web service description page, click one of the Web methods listed in the Web service description page.</span></span>  
  
2.  <span data-ttu-id="57bb4-138">輸入 Web 方法，針對必要的參數，然後按一下**Invoke**。</span><span class="sxs-lookup"><span data-stu-id="57bb4-138">Type the necessary parameters for the Web method, and then click **Invoke**.</span></span>  
  
3.  <span data-ttu-id="57bb4-139">伺服器會將 XML 回應傳回瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="57bb4-139">The server returns an XML response in the browser.</span></span> <span data-ttu-id="57bb4-140">如果 Web 服務的傳回資料型別是雙精度浮點數，結果可能看起來如下：</span><span class="sxs-lookup"><span data-stu-id="57bb4-140">If the return data type for the Web service is a double-precision floating-point number, the result might look like the following:</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <double>74.5</double>  
    ```  
  
#### <a name="to-test-a-web-service-with-internet-explorer-using-http-get-alternate-method"></a><span data-ttu-id="57bb4-141">若要使用 Internet Explorer 和 HTTP-GET (替代方法) 測試 Web 服務</span><span class="sxs-lookup"><span data-stu-id="57bb4-141">To test a Web service with Internet Explorer using HTTP-GET (alternate method)</span></span>  
  
1.  <span data-ttu-id="57bb4-142">在 Internet Explorer 中**位址**方塊中，輸入使用的格式為 Web 服務 URL ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***。</span><span class="sxs-lookup"><span data-stu-id="57bb4-142">In Internet Explorer, in the **Address** box, type the URL for the Web service using the format ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***.</span></span>  
  
    |<span data-ttu-id="57bb4-143">參數</span><span class="sxs-lookup"><span data-stu-id="57bb4-143">Parameter</span></span>|<span data-ttu-id="57bb4-144">值</span><span class="sxs-lookup"><span data-stu-id="57bb4-144">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="57bb4-145">***伺服器名稱***</span><span class="sxs-lookup"><span data-stu-id="57bb4-145">***servername***</span></span>|<span data-ttu-id="57bb4-146">您已部署 XML Web Service 之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="57bb4-146">The name of the server that you have deployed your XML Web service.</span></span>|  
    |<span data-ttu-id="57bb4-147">***Apppath***</span><span class="sxs-lookup"><span data-stu-id="57bb4-147">***Apppath***</span></span>|<span data-ttu-id="57bb4-148">虛擬目錄的名稱和 Web 應用程式路徑。</span><span class="sxs-lookup"><span data-stu-id="57bb4-148">The name of your virtual directory and the Web application path.</span></span>|  
    |<span data-ttu-id="57bb4-149">***webservicename.asmx***</span><span class="sxs-lookup"><span data-stu-id="57bb4-149">***webservicename.asmx***</span></span>|<span data-ttu-id="57bb4-150">XML Web Service .asmx 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="57bb4-150">The name of the XML Web service .asmx file.</span></span>|  
    |<span data-ttu-id="57bb4-151">***方法名稱***</span><span class="sxs-lookup"><span data-stu-id="57bb4-151">***Methodname***</span></span>|<span data-ttu-id="57bb4-152">XML Web Service 公開的公用方法名稱。</span><span class="sxs-lookup"><span data-stu-id="57bb4-152">The name of a public method that the XML Web service exposes.</span></span> <span data-ttu-id="57bb4-153">若將它留白，XML Web Service 的描述頁面將會出現，並列出 .asmx 檔案中可用的每個公用方法</span><span class="sxs-lookup"><span data-stu-id="57bb4-153">If left blank, the description page for the XML Web service appears, listing each public method available in the .asmx file.</span></span> <span data-ttu-id="57bb4-154">(選擇性)</span><span class="sxs-lookup"><span data-stu-id="57bb4-154">(Optional)</span></span>|  
    |<span data-ttu-id="57bb4-155">***參數***</span><span class="sxs-lookup"><span data-stu-id="57bb4-155">***parameter***</span></span>|<span data-ttu-id="57bb4-156">您的方法所需之任何參數的適當參數名稱和值。</span><span class="sxs-lookup"><span data-stu-id="57bb4-156">The appropriate parameter name and value for any parameters required by your method.</span></span> <span data-ttu-id="57bb4-157">若將它留白，XML Web Service 的描述頁面將會出現，並列出 .asmx 檔案中可用的每個公用方法</span><span class="sxs-lookup"><span data-stu-id="57bb4-157">If left blank, the description page for the XML Web service appears, listing each public method available in the .asmx file.</span></span> <span data-ttu-id="57bb4-158">(選擇性)</span><span class="sxs-lookup"><span data-stu-id="57bb4-158">(Optional)</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="57bb4-159">此語法中的 XML Web Service 方法名稱區分大小寫，但伺服器、專案和 XML Web Service 名稱則不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="57bb4-159">The XML Web service method name in this syntax is case sensitive, but the server, project, and XML Web service names are not.</span></span>  
  
2.  <span data-ttu-id="57bb4-160">按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="57bb4-160">Press Enter.</span></span> <span data-ttu-id="57bb4-161">Web 瀏覽器會顯示伺服器傳回的 XML 回應。</span><span class="sxs-lookup"><span data-stu-id="57bb4-161">The Web browser displays an XML response from the server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57bb4-162">您也可以使用 HTTP-POST 來呼叫 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="57bb4-162">You can also use HTTP-POST to call the Web service.</span></span> <span data-ttu-id="57bb4-163">如資訊和有關從網頁瀏覽器呼叫 XML Web 服務的範例，請參閱 「 如何以:: 存取 XML Web 服務從瀏覽器 」 中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]協助處[http://go.microsoft.com/fwlink/?LinkId=62265](http://go.microsoft.com/fwlink/?LinkId=62265)。</span><span class="sxs-lookup"><span data-stu-id="57bb4-163">For information and samples about calling XML Web services from a Web browser, see "How to: Access XML Web Services from a Browser" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62265](http://go.microsoft.com/fwlink/?LinkId=62265).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bb4-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57bb4-164">See Also</span></span>  
 [<span data-ttu-id="57bb4-165">測試已發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="57bb4-165">Testing Published Web Services</span></span>](../core/testing-published-web-services.md)