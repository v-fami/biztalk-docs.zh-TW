---
title: "如何設定 SOAP 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], virtual directories
- SOAP adapters, code samples
- configuring [SOAP adapters], receive locations
- virtual directories, SOAP adapters
- SOAP adapters, receive locations
- code samples, SOAP adapters
- configuring [SOAP adapters], code samples
- SOAP adapters, virtual directories
- receive locations, SOAP adapters
ms.assetid: 7e348409-9181-47e4-b3c0-c73eb2acffa3
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b33886296441082ea7d7e83b92659f81140d71f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-receive-location"></a><span data-ttu-id="fe409-102">如何設定 SOAP 接收位置</span><span class="sxs-lookup"><span data-stu-id="fe409-102">How to Configure a SOAP Receive Location</span></span>
<span data-ttu-id="fe409-103">您可以用程式設計方式或使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 來設定 SOAP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="fe409-103">You can configure a SOAP receive location either programmatically or by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="fe409-104">**如何設定 SOAP 接收位置以程式設計的方式**</span><span class="sxs-lookup"><span data-stu-id="fe409-104">**How to Configure a SOAP Receive Location Programmatically**</span></span>  
  
 <span data-ttu-id="fe409-105">「BizTalk 總管」物件模型可讓您以程式設計的方式建立和設定接收位置。</span><span class="sxs-lookup"><span data-stu-id="fe409-105">The BizTalk Explorer object model enables you to create and configure receive locations programmatically.</span></span> <span data-ttu-id="fe409-106">「 BizTalk 總管物件模型公開**IReceiveLocation**接收位置組態介面具有**TransportTypeData**讀/寫屬性。</span><span class="sxs-lookup"><span data-stu-id="fe409-106">The BizTalk Explorer object model exposes the**IReceiveLocation** receive location configuration interface that has a **TransportTypeData** read/write property.</span></span> <span data-ttu-id="fe409-107">此屬性接受的 SOAP 接收位置組態屬性包格式，是成對的名稱-數值 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="fe409-107">This property accepts a SOAP receive location configuration property bag in the form of a name-value pair of XML strings.</span></span> <span data-ttu-id="fe409-108">若要在 「 BizTalk 總管物件模型中設定這個屬性，您必須設定**InboundTransportLocation**屬性**IReceiveLocation**介面。</span><span class="sxs-lookup"><span data-stu-id="fe409-108">To set this property in the BizTalk Explorer object model, you must set the **InboundTransportLocation** property of the **IReceiveLocation** interface.</span></span>  
  
 <span data-ttu-id="fe409-109">**TransportTypeData**屬性**IReceiveLocation**介面沒有設定。</span><span class="sxs-lookup"><span data-stu-id="fe409-109">The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set.</span></span> <span data-ttu-id="fe409-110">若不設定此屬性，SOAP 配接器會按照下列表格指示，使用預設值做為 SOAP 接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="fe409-110">If it is not set, the SOAP adapter uses the default values for the SOAP receive location configuration as indicated in the following table.</span></span>  
  
 <span data-ttu-id="fe409-111">下列表格列出您可在「BizTalk 總管」物件模型中，為 SOAP 接收位置設定的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="fe409-111">The following table lists the configuration properties that you can set in the BizTalk Explorer object model for the SOAP receive location.</span></span>  
  
|<span data-ttu-id="fe409-112">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="fe409-112">Property name</span></span>|<span data-ttu-id="fe409-113">類型</span><span class="sxs-lookup"><span data-stu-id="fe409-113">Type</span></span>|<span data-ttu-id="fe409-114">Description</span><span class="sxs-lookup"><span data-stu-id="fe409-114">Description</span></span>|  
|-------------------|----------|-----------------|  
|<span data-ttu-id="fe409-115">**URI**</span><span class="sxs-lookup"><span data-stu-id="fe409-115">**URI**</span></span>|<span data-ttu-id="fe409-116">字串</span><span class="sxs-lookup"><span data-stu-id="fe409-116">String</span></span>|<span data-ttu-id="fe409-117">包含部署伺服器上 Web 服務的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fe409-117">Virtual directory containing the Web service on the deployment server.</span></span>|  
|<span data-ttu-id="fe409-118">**AddressableURI**</span><span class="sxs-lookup"><span data-stu-id="fe409-118">**AddressableURI**</span></span>|<span data-ttu-id="fe409-119">字串</span><span class="sxs-lookup"><span data-stu-id="fe409-119">String</span></span>|<span data-ttu-id="fe409-120">公用位址欄位，包含完整可呼叫的 URL。</span><span class="sxs-lookup"><span data-stu-id="fe409-120">Public address field containing the entire, callable URL.</span></span><br /><br /> <span data-ttu-id="fe409-121">預設值： 空白</span><span class="sxs-lookup"><span data-stu-id="fe409-121">Default value: Blank</span></span>|  
|<span data-ttu-id="fe409-122">**UseSSO**</span><span class="sxs-lookup"><span data-stu-id="fe409-122">**UseSSO**</span></span>|<span data-ttu-id="fe409-123">布林</span><span class="sxs-lookup"><span data-stu-id="fe409-123">Boolean</span></span>|<span data-ttu-id="fe409-124">指定 SOAP 配接器是否發出「單一登入」票證至扺達此接收位置的訊息。</span><span class="sxs-lookup"><span data-stu-id="fe409-124">Specifies whether the SOAP adapter issues the Single Sign-On ticket to the messages that arrive on this receive location.</span></span><br /><br /> <span data-ttu-id="fe409-125">預設值：False</span><span class="sxs-lookup"><span data-stu-id="fe409-125">Default value: False</span></span>|  
  
 <span data-ttu-id="fe409-126">使用下列格式設定屬性：</span><span class="sxs-lookup"><span data-stu-id="fe409-126">Use the following format to set the properties:</span></span>  
  
```  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
```  
  
 <span data-ttu-id="fe409-127">**URI**和**AddressableURI**屬性會設定使用**位址**和**PublicAddress**的接收位置屬性物件。</span><span class="sxs-lookup"><span data-stu-id="fe409-127">The **URI** and **AddressableURI** properties are set using the **Address** and **PublicAddress** properties of the receive location object.</span></span>  
  
 <span data-ttu-id="fe409-128">下列程式碼片段示範建立 SOAP 接收位置：</span><span class="sxs-lookup"><span data-stu-id="fe409-128">The following code fragment illustrates creating a SOAP receive location:</span></span>  
  
```  
// Use BizTalk Explorer object model to create new SOAP receive location.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
  
// Add a new Request-Response port  
ReceivePort receivePort = explorer.AddNewReceivePort(true);  
receivePort.Name = "SampleReceivePort";  
receivePort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
  
// Add primary SOAP receive location  
ReceiveLocation receiveLocation = receivePort.AddNewReceiveLocation();  
receiveLocation.Name = "SampleReceiveLocation";  
receiveLocation.Address = "/PurchaseOrder/POOrchestration.asmx";  
receiveLocation.TransportType = explorer.ProtocolTypes["SOAP"];  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
receiveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
foreach (ReceiveHandler receiveHandler in explorer.ReceiveHandlers)  
{  
if (receiveHandler.TransportType.Name == receiveLocation.TransportType.Name)  
{  
receiveLocation.ReceiveHandler = receiveHandler;   
}  
}  
  
// Save  
explorer.SaveChanges();   
```  
  
 <span data-ttu-id="fe409-129">**如何設定 SOAP 接收位置與 BizTalk Server 管理主控台**</span><span class="sxs-lookup"><span data-stu-id="fe409-129">**How to Configure a SOAP Receive Location with the BizTalk Server Administration Console**</span></span>  
  
 <span data-ttu-id="fe409-130">您可以在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中設定 SOAP 接收位置配接器變數。</span><span class="sxs-lookup"><span data-stu-id="fe409-130">You can set SOAP receive location adapter variables in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="fe409-131">如果接收位置並未設定屬性，系統就會使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中設定的預設接收處理常式值。</span><span class="sxs-lookup"><span data-stu-id="fe409-131">If properties are not set in the receive location, the default receive handler values set in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console are used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe409-132">完成下列程序之前，您必須已經新增接收埠。</span><span class="sxs-lookup"><span data-stu-id="fe409-132">Before completing the following procedures you must have already added a receive port.</span></span> <span data-ttu-id="fe409-133">如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="fe409-133">For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).</span></span>  
  
### <a name="to-configure-variables-for-a-soap-receive-location"></a><span data-ttu-id="fe409-134">設定 SOAP 接收位置的變數</span><span class="sxs-lookup"><span data-stu-id="fe409-134">To configure variables for a SOAP receive location</span></span>  
  
1.  <span data-ttu-id="fe409-135">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您想要在其中建立接收位置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe409-135">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application you want to create a receive location in.</span></span>  
  
2.  <span data-ttu-id="fe409-136">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在左窗格中，按一下**接收埠**節點。</span><span class="sxs-lookup"><span data-stu-id="fe409-136">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, in the left pane, click the **Receive Port** node.</span></span> <span data-ttu-id="fe409-137">然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fe409-137">Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="fe409-138">在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。</span><span class="sxs-lookup"><span data-stu-id="fe409-138">In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.</span></span>  
  
4.  <span data-ttu-id="fe409-139">在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**SOAP**從下拉式清單中，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="fe409-139">In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **SOAP** from the drop-down list, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="fe409-140">在**SOAP 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fe409-140">In the **SOAP Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="fe409-141">使用</span><span class="sxs-lookup"><span data-stu-id="fe409-141">Use this</span></span>|<span data-ttu-id="fe409-142">動作</span><span class="sxs-lookup"><span data-stu-id="fe409-142">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fe409-143">**虛擬目錄加 Web 服務.asmx 檔案**</span><span class="sxs-lookup"><span data-stu-id="fe409-143">**Virtual directory plus Web Service .asmx file**</span></span>|<span data-ttu-id="fe409-144">指示由「BizTalk Web 服務發佈精靈」所建立的 .asmx 檔案。</span><span class="sxs-lookup"><span data-stu-id="fe409-144">Indicate the .asmx file created by the BizTalk Web Services Publishing Wizard.</span></span><br /><br /> <span data-ttu-id="fe409-145">此訊息的格式類似下列各項：</span><span class="sxs-lookup"><span data-stu-id="fe409-145">The format of this message is similar to the following:</span></span><br /><br /> <span data-ttu-id="fe409-146">/PurchaseOrder/POOrchestration.asmx</span><span class="sxs-lookup"><span data-stu-id="fe409-146">/PurchaseOrder/POOrchestration.asmx</span></span><br /><br /> <span data-ttu-id="fe409-147">其中，.asmx 檔案的完整位置是 http://localhost/PurchaseOrder/POOrchestration.asmx。</span><span class="sxs-lookup"><span data-stu-id="fe409-147">Where the full location of the .asmx file is http://localhost/PurchaseOrder/POOrchestration.asmx.</span></span> <span data-ttu-id="fe409-148">**注意：** URI 傳送埠或接收位置不能超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="fe409-148">**Note:**  The URI for a send port or receive location cannot exceed 256 characters.</span></span>|  
    |<span data-ttu-id="fe409-149">**公用位址**</span><span class="sxs-lookup"><span data-stu-id="fe409-149">**Public address**</span></span>|<span data-ttu-id="fe409-150">指定此接收位置的完整格式 URI。</span><span class="sxs-lookup"><span data-stu-id="fe409-150">Specify the fully qualified URI for this receive location.</span></span> <span data-ttu-id="fe409-151">此屬性的值是由伺服器名稱與虛擬目錄所組成。</span><span class="sxs-lookup"><span data-stu-id="fe409-151">The value for this property is a combination of the server name and the virtual directory.</span></span> <span data-ttu-id="fe409-152">指定的 URI 應指定當訊息傳送至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，所要連接之交易夥伴的公用網站 URL。</span><span class="sxs-lookup"><span data-stu-id="fe409-152">The specified URI should designate the public Web site URL for trading partners to connect to when sending messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="fe409-153">此資訊是選擇性的，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不會使用。</span><span class="sxs-lookup"><span data-stu-id="fe409-153">This information is optional and is not used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="fe409-154">此參數可用來允許管理員記載接收位置所連結的公用 URL。</span><span class="sxs-lookup"><span data-stu-id="fe409-154">This parameter is available to allow administrators to document the public URL that the receive location is tied to.</span></span>|  
    |<span data-ttu-id="fe409-155">**使用單一登入**</span><span class="sxs-lookup"><span data-stu-id="fe409-155">**Use Single Sign-On**</span></span>|<span data-ttu-id="fe409-156">指示 SOAP 配接器使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="fe409-156">Indicate that the SOAP adapter uses Enterprise Single Sign-On.</span></span> <span data-ttu-id="fe409-157">**注意：** BizTalk Web 服務發佈精靈可讓您使用 SharePoint Portal Server 單一登入，則此屬性僅啟用 「 企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="fe409-157">**Note:**  The BizTalk Web Services Publishing Wizard allows you to use SharePoint Portal Server Single Sign-On; this property only enables Enterprise Single Sign-On.</span></span>|  
  
6.  <span data-ttu-id="fe409-158">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fe409-158">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="fe409-159">在**接收位置屬性**對話方塊方塊中，輸入適當的值，以完成設定的接收位置，然後按一下**確定**儲存設定。</span><span class="sxs-lookup"><span data-stu-id="fe409-159">In the **Receive Location Properties** dialog box, enter the appropriate values to complete the configuration of the receive location, and then click **OK** to save settings.</span></span> <span data-ttu-id="fe409-160">如需有關資訊**接收位置屬性**對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="fe409-160">For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
 <span data-ttu-id="fe409-161">SOAP 接收位置使用的安全性設定值，是在 IIS 中設定。</span><span class="sxs-lookup"><span data-stu-id="fe409-161">The security settings used by the SOAP receive location are set in IIS.</span></span> <span data-ttu-id="fe409-162">依照預設，SOAP 接收位置不會設成使用匿名驗證。</span><span class="sxs-lookup"><span data-stu-id="fe409-162">By default, the SOAP receive location is not set to use anonymous authentication.</span></span>  
  
 <span data-ttu-id="fe409-163">雖然 SOAP 用戶端會呼叫 Web 服務，但 SOAP 配接器會使用「匿名」、「基本」、「摘要」或「Windows 整合」驗證來驗證 SOAP 用戶端。</span><span class="sxs-lookup"><span data-stu-id="fe409-163">While the SOAP client calls the Web service, the SOAP adapter authenticates the SOAP client by using either Anonymous, Basic, Digest, or Windows Integrated authentication.</span></span> <span data-ttu-id="fe409-164">若未驗證使用者，使用者內容會傳送至接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="fe409-164">If the user is verified, the user context is passed to the receive handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe409-165">任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。</span><span class="sxs-lookup"><span data-stu-id="fe409-165">Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid.</span></span> <span data-ttu-id="fe409-166">每個程序只能有一個隔離的接收器。</span><span class="sxs-lookup"><span data-stu-id="fe409-166">You can have only one isolated receiver per process.</span></span>  
  
### <a name="to-update-a-virtual-directory-to-use-aspnet-40"></a><span data-ttu-id="fe409-167">若要更新虛擬目錄以使用 ASP.NET 4.0</span><span class="sxs-lookup"><span data-stu-id="fe409-167">To update a virtual directory to use ASP.NET 4.0</span></span>  
  
1.  <span data-ttu-id="fe409-168">啟動 Internet Information Services (IIS) Manager。</span><span class="sxs-lookup"><span data-stu-id="fe409-168">Launch the Internet Information Services (IIS) Manager.</span></span> <span data-ttu-id="fe409-169">按一下**啟動**，按一下 **所有程式**，然後按一下**網際網路資訊服務 (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="fe409-169">Click **Start**, click **All Programs**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="fe409-170">如果您需要連接遠端 IIS 伺服器，以滑鼠右鍵按一下**Internet Information Services**節點，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="fe409-170">If you need to connect to a remote IIS server, right click the **Internet Information Services** node and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="fe409-171">如有需要，輸入遠端 IIS 伺服器的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="fe409-171">Type the computer name for the remote IIS server and credentials if necessary.</span></span>  
  
4.  <span data-ttu-id="fe409-172">展開要更新的網站或虛擬目錄所在之伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="fe409-172">Expand the server name that houses the Web site or virtual directory to be updated.</span></span>  
  
5.  <span data-ttu-id="fe409-173">展開**網站**。</span><span class="sxs-lookup"><span data-stu-id="fe409-173">Expand **Sites**.</span></span>  
  
6.  <span data-ttu-id="fe409-174">展開**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="fe409-174">Expand **Default Web Site**.</span></span>  
  
7.  <span data-ttu-id="fe409-175">展開 [預設的網站]，以檢視網站下方的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fe409-175">Expand the Default Web site to view the virtual directories under the Web site.</span></span>  
  
8.  <span data-ttu-id="fe409-176">以滑鼠右鍵按一下您要更新成使用 ASP.NET 4.0 中，按一下虛擬目錄**管理應用程式**，然後按一下 **進階設定**。</span><span class="sxs-lookup"><span data-stu-id="fe409-176">Right-click the virtual directory that you want to update to use ASP.NET 4.0, click **Manage Application**, and then click **Advanced Settings**.</span></span> <span data-ttu-id="fe409-177">**應用程式集區**欄位會顯示所選的虛擬目錄設定應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="fe409-177">The **Application Pool** field displays the application pool set for the selected virtual directory.</span></span> <span data-ttu-id="fe409-178">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fe409-178">Click **OK**.</span></span>  
  
9. <span data-ttu-id="fe409-179">在 [網際網路資訊服務 (IIS) 管理員] 視窗中，按一下**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="fe409-179">In the Internet Information Services (IIS) Manager window, click **Application Pools**.</span></span> <span data-ttu-id="fe409-180">詳細資料窗格會顯示伺服器上的應用程式集區清單。</span><span class="sxs-lookup"><span data-stu-id="fe409-180">The details pane displays a list of application pools on the server.</span></span>  
  
10. <span data-ttu-id="fe409-181">以滑鼠右鍵按一下步驟 8 中設定的應用程式集區，然後按一下**基本設定**。</span><span class="sxs-lookup"><span data-stu-id="fe409-181">Right-click the application pool set in step 8, and then click **Basic Settings**.</span></span>  
  
11. <span data-ttu-id="fe409-182">在**編輯應用程式集區**對話方塊方塊中，變更下列：</span><span class="sxs-lookup"><span data-stu-id="fe409-182">In the **Edit Application Pool** dialog box, change the following:</span></span>  
  
    -   <span data-ttu-id="fe409-183">**.NET framework 版本**至**4.0**</span><span class="sxs-lookup"><span data-stu-id="fe409-183">**.NET Framework version** to **4.0**</span></span>  
  
    -   <span data-ttu-id="fe409-184">**Managed 的管線模式**至**傳統**</span><span class="sxs-lookup"><span data-stu-id="fe409-184">**Managed pipeline mode** to **Classic**</span></span>  
  
12. <span data-ttu-id="fe409-185">按一下**確定**才能套用變更。</span><span class="sxs-lookup"><span data-stu-id="fe409-185">Click **OK** to apply the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe409-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe409-186">See Also</span></span>  
 [<span data-ttu-id="fe409-187">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="fe409-187">Consuming Web Services</span></span>](../core/consuming-web-services.md)