---
title: 如何使用 Web 服務僅供傳訊實例中 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66873959-5b1b-4d9b-ad19-f083670420b8
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71d1e38305fd5b798a2fa8dd59fc6341dc806dfd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985447"
---
# <a name="how-to-consume-web-services-in-a-messaging-only-scenario"></a><span data-ttu-id="e803c-102">如何在僅供傳訊實例中使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="e803c-102">How to Consume Web Services in a Messaging Only Scenario</span></span>
<span data-ttu-id="e803c-103">SOAP 配接器的其中一項新增強功能，就是可以在僅供傳訊實例中使用根據訊息內容決定路由傳送埠來呼叫 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="e803c-103">One of the new enhancements for the SOAP adapter is ability to call Web services in a messaging only scenario by using content-based routing send ports.</span></span> <span data-ttu-id="e803c-104">這項功能可以讓配接器直接使用 Web 服務，而不用另外建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="e803c-104">This feature makes it possible to consume Web services without creating orchestrations.</span></span> <span data-ttu-id="e803c-105">這項功能也會使得 Web 服務使用效能更好，因為這時訊息並不用通過協調流程。</span><span class="sxs-lookup"><span data-stu-id="e803c-105">It also provides better performance to consume Web services because messages do not pass through orchestrations.</span></span>  
  
 <span data-ttu-id="e803c-106">若要在僅供傳訊實例中使用 Web 服務，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e803c-106">To consume Web services in a messaging only scenario, do the following:</span></span>  
  
-   <span data-ttu-id="e803c-107">建立 Proxy 程式庫和 XML 結構描述來叫用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="e803c-107">Create a proxy library and XML schemas for invoking Web services</span></span>  
  
-   <span data-ttu-id="e803c-108">設定傳送埠和接收位置來使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="e803c-108">Configure a send port and receive location for consuming a Web service</span></span>  
  
### <a name="to-create-a-proxy-library-and-xml-schemas-for-invoking-web-services"></a><span data-ttu-id="e803c-109">若要建立 Proxy 程式庫和 XML 結構描述來叫用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="e803c-109">To create a proxy library and XML schemas for invoking Web services</span></span>  
  
1. <span data-ttu-id="e803c-110">決定 Web 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="e803c-110">Determine the URL for the Web service.</span></span>  
  
2. <span data-ttu-id="e803c-111">開啟**空白 BizTalk Server 專案**在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="e803c-111">Open an **Empty BizTalk Server Project** in a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution.</span></span> <span data-ttu-id="e803c-112">如需如何建立 BizTalk Server 專案的詳細資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="e803c-112">For more information about how to create a BizTalk Server project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="e803c-113">這個逐步解說會應用 BizTalk Server 專案，產生 Web 服務所使用的 Proxy 程式庫和 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="e803c-113">This walkthrough uses a BizTalk Server project to generate proxy libraries and XML schemas that the Web service uses.</span></span> <span data-ttu-id="e803c-114">您也可以針對相同目的.NET Framework 4.0 SDK 中使用 Wsdl.exe 和 Xsd.exe。</span><span class="sxs-lookup"><span data-stu-id="e803c-114">You can also use the Wsdl.exe and Xsd.exe in the .NET Framework 4.0 SDK for the same purpose.</span></span>  
  
3. <span data-ttu-id="e803c-115">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk Server 專案名稱，然後**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="e803c-115">In Solution Explorer, right-click the BizTalk Server project name, and then click **Add Service Reference**.</span></span>  
  
4. <span data-ttu-id="e803c-116">在 [**加入服務參考**] 對話方塊中，按一下**進階**。</span><span class="sxs-lookup"><span data-stu-id="e803c-116">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
5. <span data-ttu-id="e803c-117">在 [**服務參考設定**] 對話方塊中，按一下**加入 Web 參考**中**相容性**一節。</span><span class="sxs-lookup"><span data-stu-id="e803c-117">In the **Service Reference Settings** dialog box, Click **Add Web Reference** in the **Compatibility** section.</span></span>  
  
6. <span data-ttu-id="e803c-118">在 **加入 Web 參考**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e803c-118">In the **Add Web Reference** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="e803c-119">在  **URL**欄位，輸入 Web 服務的 URL，然後按一下 **移**。</span><span class="sxs-lookup"><span data-stu-id="e803c-119">In the **URL** field, type a Web service URL, and then click **Go**.</span></span>  
  
   2.  <span data-ttu-id="e803c-120">在  **Web 參考名稱**欄位中，輸入命名空間的名稱，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="e803c-120">In the **Web reference name** field, type a name for the namespace, and then click **Add Reference**.</span></span>  
  
7. <span data-ttu-id="e803c-121">Web 參考會出現在**Web 參考**方案總管 中的節點。</span><span class="sxs-lookup"><span data-stu-id="e803c-121">The Web reference will appear under **Web References** node in Solution Explorer.</span></span>  
  
   > [!TIP]
   >  <span data-ttu-id="e803c-122">一旦您已將 web 參考加入至 BizTalk 專案時，**加入 Web 參考**命令時，直接使用您以滑鼠右鍵按一下專案名稱或**參考**或**的Web參考**.</span><span class="sxs-lookup"><span data-stu-id="e803c-122">Once you have a web reference added to a BizTalk project, the **Add Web Reference** command is directly available when you right-click the project name or **References** or **Web References**.</span></span>  
  
8. <span data-ttu-id="e803c-123">在 方案總管 中，以滑鼠右鍵按一下專案名稱，然後**屬性**以啟動 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="e803c-123">In Solution Explorer, right-click the project name, and then click **Properties** to launch the Project Designer.</span></span>  
  
9. <span data-ttu-id="e803c-124">在 [專案設計工具中，按一下**簽署**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e803c-124">In the Project Designer, click the **Signing** tab.</span></span>  
  
10. <span data-ttu-id="e803c-125">選取 **簽署組件**選項，請按一下下拉式清單，如**選擇強式名稱金鑰檔**，然後按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="e803c-125">Select **Sign the assembly** option, click the drop-down list for the **Choose a strong name key file**, and then click **Browse**.</span></span>  
  
11. <span data-ttu-id="e803c-126">瀏覽並選取組件金鑰檔案，然後按**開啟**。</span><span class="sxs-lookup"><span data-stu-id="e803c-126">Browse and select the assembly key file, and then click **Open**.</span></span>  
  
12. <span data-ttu-id="e803c-127">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。</span><span class="sxs-lookup"><span data-stu-id="e803c-127">In Solution Explorer, right-click the project name, and then click **Build**.</span></span>  
  
13. <span data-ttu-id="e803c-128">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="e803c-128">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span>  
  
### <a name="to-configure-a-send-port-and-receive-location-for-consuming-a-web-service"></a><span data-ttu-id="e803c-129">若要設定傳送埠和接收位置來使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="e803c-129">To configure a send port and receive location for consuming a Web service</span></span>  
  
1.  <span data-ttu-id="e803c-130">在 [BizTalk Server 管理] 主控台中，建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e803c-130">In the BizTalk Server Administration console, create a send port.</span></span> <span data-ttu-id="e803c-131">如需詳細資訊，請參閱 <<c0> [ 如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="e803c-131">For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="e803c-132">建立傳送埠時，請選取 SOAP 作為傳輸類型或傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e803c-132">When creating the send port, select SOAP as the transport type or transport protocol.</span></span>  
  
2.  <span data-ttu-id="e803c-133">設定下列設定的 SOAP 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e803c-133">Configure the SOAP send port with the following settings.</span></span> <span data-ttu-id="e803c-134">如需詳細資訊，請參閱 <<c0> [ 如何設定 SOAP 傳送埠](../core/how-to-configure-a-soap-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="e803c-134">For more information, see [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md).</span></span>  
  
    |<span data-ttu-id="e803c-135">使用</span><span class="sxs-lookup"><span data-stu-id="e803c-135">Use this</span></span>|<span data-ttu-id="e803c-136">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e803c-136">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e803c-137">**下列設定**</span><span class="sxs-lookup"><span data-stu-id="e803c-137">**The following settings**</span></span>|<span data-ttu-id="e803c-138">選取這個選項來指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e803c-138">Select this option to specify the following properties.</span></span>|  
    |<span data-ttu-id="e803c-139">**組件名稱**</span><span class="sxs-lookup"><span data-stu-id="e803c-139">**Assembly name**</span></span>|<span data-ttu-id="e803c-140">選取先前程序所建立的組件。</span><span class="sxs-lookup"><span data-stu-id="e803c-140">Select the assembly created in the previous procedure.</span></span> <span data-ttu-id="e803c-141">組件的完整的名稱會寫入至 SOAP 配接器**AssemblyName**屬性。</span><span class="sxs-lookup"><span data-stu-id="e803c-141">The fully qualified name of the assembly is written to the SOAP adapter **AssemblyName** property.</span></span>|  
    |<span data-ttu-id="e803c-142">**類型名稱**</span><span class="sxs-lookup"><span data-stu-id="e803c-142">**Type name**</span></span>|<span data-ttu-id="e803c-143">指定包含要叫用的 Web 方法的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="e803c-143">Specify the name of the class that contains the Web method to be invoked.</span></span> <span data-ttu-id="e803c-144">SOAP 配接器的型別名稱寫入**TypeName**屬性。</span><span class="sxs-lookup"><span data-stu-id="e803c-144">The type name is written to the SOAP adapter **TypeName** property.</span></span>|  
    |<span data-ttu-id="e803c-145">**方法名稱**</span><span class="sxs-lookup"><span data-stu-id="e803c-145">**Method name**</span></span>|<span data-ttu-id="e803c-146">在清單方塊中選取其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="e803c-146">Specify one of the methods in the list box.</span></span> <span data-ttu-id="e803c-147">Web 方法會寫入至 Soap 配接器**MethodName**屬性。</span><span class="sxs-lookup"><span data-stu-id="e803c-147">The Web method is written to the Soap Adapter **MethodName** property.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="e803c-148">若您要使用「根據訊息內容決定路由」(CBR)，請設定傳送埠的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="e803c-148">If you want to use Content-Based Routing (CBR), configure the filter of the send port.</span></span> <span data-ttu-id="e803c-149">如需詳細資訊，請參閱 <<c0> [ 如何設定傳送埠的篩選](../core/how-to-configure-filters-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="e803c-149">For more information, see [How to Configure Filters for a Send Port](../core/how-to-configure-filters-for-a-send-port.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e803c-150">如果來自所叫用 Web 服務的回應訊息沒有任何訂閱者，將會產生路由失敗錯誤。</span><span class="sxs-lookup"><span data-stu-id="e803c-150">If there is no subscriber to the response messages from the invoked Web services, a routing failure error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e803c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e803c-151">See Also</span></span>  
 [<span data-ttu-id="e803c-152">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="e803c-152">Consuming Web Services</span></span>](../core/consuming-web-services.md)