---
title: "如何使用 BizTalk WCF 服務發佈精靈來發佈服務中繼資料的 WCF 接收位置的內容為基礎的路由 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Service Publishing Wizard, publishing metadata
- WCF services, metadata
ms.assetid: e900b0a0-db17-4db9-a639-54891e02d6d7
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9c46af9724d12609f599c790a7f0a52b2d5d0b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing"></a><span data-ttu-id="18791-102">如何使用 BizTalk WCF 服務發佈精靈來發佈根據訊息內容決定路由之 WCF 接收位置的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="18791-102">How to Use the BizTalk WCF Service Publishing Wizard to Publish Service Metadata for a WCF Receive Location for Content-Based Routing</span></span>
<span data-ttu-id="18791-103">您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 WCF 服務，以便發佈根據訊息內容決定路由之現有 WCF 接收位置的服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="18791-103">You use the BizTalk WCF Service Publishing Wizard to create a WCF service to publish service metadata for existing WCF receive locations for content-based routing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18791-104">您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="18791-104">You must build your BizTalk projects before running the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="18791-105">BizTalk 專案必須包含結構描述，才能發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="18791-105">The BizTalk projects must include schemas to publish as WCF services.</span></span> <span data-ttu-id="18791-106">發佈 WCF 配接器的服務中繼資料之前，您也必須使用 BizTalk Server 管理主控台或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的 BTSTask 命令列工具來建立 WCF 接收位置。</span><span class="sxs-lookup"><span data-stu-id="18791-106">Before you publish service metadata for the WCF adapters, you must also create the WCF receive locations by using the BizTalk Server Administration console or the BTSTask command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="18791-107">如需有關如何建立 WCF 接收位置，請參閱中的每個 WCF 配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="18791-107">For more information about how to create a WCF receive location, see the appropriate topic for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
### <a name="to-publish-service-metadata-for-an-existing-wcf-receive-location-for-content-based-routing"></a><span data-ttu-id="18791-108">若要發佈根據訊息內容決定路由之現有 WCF 接收位置的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="18791-108">To publish service metadata for an existing WCF receive location for content-based routing</span></span>  
  
1.  <span data-ttu-id="18791-109">按一下**啟動**，指向 **所有程式**，指向   **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** ，然後按一下 **BizTalk WCF 服務發佈精靈**。</span><span class="sxs-lookup"><span data-stu-id="18791-109">Click **Start**, point to **All Programs**, point to **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, and then click **BizTalk WCF Service Publishing Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-110">若要建立並發佈 BizTalk 協調流程和結構描述的 WCF 服務中繼資料，您可以使用 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="18791-110">To create and publish WCF service metadata for BizTalk orchestrations and schemas, you use the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="18791-111">若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="18791-111">To publish orchestrations and schemas as Web services with the SOAP adapter, you use the BizTalk Web Services Publishing Wizard.</span></span>  
  
2.  <span data-ttu-id="18791-112">在**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="18791-112">On the **Welcome to the BizTalk WCF Service Publishing Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="18791-113">在**WCF 服務類型**頁面上，選取**中繼資料唯一端點 (MEX)**選項來發佈 WCF 服務，以提供服務中繼資料之 wcf 接收位置，您將在下一個步驟中選取。</span><span class="sxs-lookup"><span data-stu-id="18791-113">On the **WCF Service Type** page, select the **Metdata only endpoint (MEX)** option to publish the WCF services to provide service metadata for the WCF receive location that you will select in the next step.</span></span>  
  
     <span data-ttu-id="18791-114">![WCF 服務類型 頁面上](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")</span><span class="sxs-lookup"><span data-stu-id="18791-114">![WCF Service Type page](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")</span></span>  
  
4.  <span data-ttu-id="18791-115">在**WCF 服務類型**頁面上，於**發行中繼資料的接收位置**下拉式清單中，選取之 WCF 接收位置發佈服務中繼資料，然後按一下**下一步**.</span><span class="sxs-lookup"><span data-stu-id="18791-115">On the **WCF Service Type** page, in the **Publish metadata for receive location** drop-down list, select a WCF receive location to publish service metadata for, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="18791-116">在**建立 WCF 服務**頁面上，選取**結構描述發佈為 WCF 服務**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="18791-116">On the **Create WCF Service** page, select **Publish schemas as WCF service**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="18791-117">![建立 WCF 服務頁面](../core/media/717db27a-2843-4950-899d-0946460f5c1f.gif "717db27a-2843-4950-899d-0946460f5c1f")</span><span class="sxs-lookup"><span data-stu-id="18791-117">![Create WCF Service page](../core/media/717db27a-2843-4950-899d-0946460f5c1f.gif "717db27a-2843-4950-899d-0946460f5c1f")</span></span>  
  
6.  <span data-ttu-id="18791-118">在**WCF 服務**頁面上，定義發行服務中繼資料的 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="18791-118">On the **WCF Service** page, define the WCF service contract(s) to publish service metadata for.</span></span> <span data-ttu-id="18791-119">使用中的樹狀結構**Web 服務描述**加入、 移除、 重新命名，以及編輯發佈的 WCF 服務的 Web 服務描述節點 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="18791-119">You use the tree in the **Web service description** dialog box to add, remove, rename, and edit the Web service description nodes for the WCF services to publish.</span></span> <span data-ttu-id="18791-120">**資訊**對話方塊提供所選節點的相關資訊，並顯示目前的節點或任何子節點中的任何錯誤：</span><span class="sxs-lookup"><span data-stu-id="18791-120">The **Information** dialog box provides information about the selected node and displays any errors in the current node or any subnodes:</span></span>  
  
    -   <span data-ttu-id="18791-121">樹狀結構的根節點 (Web 服務描述) 會描述要發佈的 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="18791-121">The root node to the tree (Web service description) describes the WCF service contracts to publish.</span></span> <span data-ttu-id="18791-122">虛擬目錄名稱會使用根節點做為預設名稱。</span><span class="sxs-lookup"><span data-stu-id="18791-122">The virtual directory name uses the root node as the default name.</span></span> <span data-ttu-id="18791-123">您可以修改的選取將發佈的 WCF 服務 Web 服務描述名稱**重新命名 web 服務描述**。</span><span class="sxs-lookup"><span data-stu-id="18791-123">You can modify the Web service description name for the WCF services to publish by selecting **Rename web service description**.</span></span>  
  
         <span data-ttu-id="18791-124">![WCF 服務頁面](../core/media/35131a58-dae7-45fe-ac6a-928c8570f27d.gif "35131a58-dae7-45fe-ac6a-928c8570f27d")</span><span class="sxs-lookup"><span data-stu-id="18791-124">![WCF Service page](../core/media/35131a58-dae7-45fe-ac6a-928c8570f27d.gif "35131a58-dae7-45fe-ac6a-928c8570f27d")</span></span>  
  
    -   <span data-ttu-id="18791-125">Web 方法節點，而**Operation1**的預設服務節點**Service1**，預設會在所示**Web 服務描述**適用於對話方塊要求-回應接收位置。</span><span class="sxs-lookup"><span data-stu-id="18791-125">The Web method node, **Operation1**, of the default service node, **Service1**, shown by default in the **Web service description** dialog box can be used for a request-response receive location.</span></span> <span data-ttu-id="18791-126">如果您選取單向 WCF 接收位置，此服務合約，以滑鼠右鍵按一下 預設的 Web 方法節點，按一下**刪除 web 方法**，然後建立一個單向 Web 方法，如下所示： 以滑鼠右鍵按一下預設服務節點點若要**新增 web 方法**，然後按一下**單向**。</span><span class="sxs-lookup"><span data-stu-id="18791-126">If you selected a one-way WCF receive location for this service contract, right-click the default Web method node, click **Delete web method**, and then create a one-way Web method as follows: Right-click the default service node, point to **Add web method**, and then click **One-Way**.</span></span>  
  
    -   <span data-ttu-id="18791-127">若要加入新的 WCF 服務，以滑鼠右鍵按一下 Web 服務描述名稱，然後**加入 web 服務**。</span><span class="sxs-lookup"><span data-stu-id="18791-127">To add a new WCF service, right-click the Web service description name, and then click **Add web service**.</span></span> <span data-ttu-id="18791-128">這樣便會建立新的 WCF 服務，而不需要進行任何 WCF 作業。</span><span class="sxs-lookup"><span data-stu-id="18791-128">This creates a new WCF service without any WCF operations.</span></span> <span data-ttu-id="18791-129">修改 WCF 服務的名稱，以滑鼠右鍵按一下該 WCF 服務節點，再按**重新命名 web 服務**，然後按 ENTER 以接受新的名稱。</span><span class="sxs-lookup"><span data-stu-id="18791-129">To modify the name of the WCF service, right-click the WCF service node, click **Rename web service**, and then press ENTER to accept the new name.</span></span>  
  
    -   <span data-ttu-id="18791-130">若要加入新的 WCF 作業，以滑鼠右鍵按一下該 WCF 服務節點，指向**新增 Web 方法**，然後按一下**單向**（針對要求 WCF 作業） 或**要求-回應**(如要求-回應 WCF 作業）。</span><span class="sxs-lookup"><span data-stu-id="18791-130">To add a new WCF operation, right-click the WCF service node, point to **Add Web Method**, and then click **One-way** (for a request WCF operation) or **Request-response** (for a request-response WCF operation).</span></span>  
  
    -   <span data-ttu-id="18791-131">若要設定的要求和回應結構描述型別，以滑鼠右鍵按一下**要求**或**回應**節點，然後再按一下**選取結構描述類型**。</span><span class="sxs-lookup"><span data-stu-id="18791-131">To set the request and response schema types, right-click the **Request** or **Response** node, and then click **Select schema type**.</span></span> <span data-ttu-id="18791-132">在**要求訊息類型**對話方塊方塊中，輸入包含中的文件結構描述的組件名稱**BizTalk 組件檔案**文字方塊中或按一下**瀏覽**搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="18791-132">In the **Request Message Type** dialog box, type the name of the assembly containing the document schema in the **BizTalk assembly file** text box or click **Browse** to search for the assembly.</span></span> <span data-ttu-id="18791-133">**可用結構描述型別**清單檢視會顯示結構描述的每個根項目。</span><span class="sxs-lookup"><span data-stu-id="18791-133">The **Available schema types** list view displays each root element of the schema.</span></span> <span data-ttu-id="18791-134">選取要新增為要求或回應結構描述類型的根節點。</span><span class="sxs-lookup"><span data-stu-id="18791-134">Select a root node to add as the request or response schema type.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="18791-135">如果您安裝到全域組件快取 (GAC) 的 BizTalk 組件檔案，請確定您會在選取的組件，已更新組件在 GAC 中的**要求訊息類型** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="18791-135">If you installed the BizTalk assembly file into the global assembly cache (GAC), make sure that the assembly in the GAC has been updated with the assembly that you will select in the **Request Message Type** dialog box.</span></span> <span data-ttu-id="18791-136">如果 GAC 中的組件具有相同的完整格式名稱，[BizTalk WCF 服務發佈精靈] 就會使用 GAC 中的組件檔案，而非您所選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="18791-136">If the GAC has the same fully qualified name, the BizTalk WCF Service Publishing Wizard uses the assembly file in the GAC instead of the one you selected.</span></span>  
  
         <span data-ttu-id="18791-137">![要求訊息類型頁面](../core/media/6bb4cc17-b108-4692-a5ca-548c7ef46045.gif "6bb4cc17-b108-4692-a5ca-548c7ef46045")</span><span class="sxs-lookup"><span data-stu-id="18791-137">![Request Message Type page](../core/media/6bb4cc17-b108-4692-a5ca-548c7ef46045.gif "6bb4cc17-b108-4692-a5ca-548c7ef46045")</span></span>  
  
    -   <span data-ttu-id="18791-138">您可以重新命名**要求**和**回應**節點，而不會影響產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="18791-138">You can rename the **Request** and **Response** nodes without affecting the generated code.</span></span> <span data-ttu-id="18791-139">在定義結構描述之後，您便可以重新命名部分項目，這樣做會修改 WCF 作業參數名稱。</span><span class="sxs-lookup"><span data-stu-id="18791-139">After defining your schemas, you can rename the part elements, which modifies the WCF operation parameter name.</span></span> <span data-ttu-id="18791-140">您可以透過檢視 WCF 服務所要發佈的服務中繼資料，查看這些變更。</span><span class="sxs-lookup"><span data-stu-id="18791-140">You can see the changes by viewing the service metadata for the WCF services to publish.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-141">重新命名任何 Web 服務描述節點時，不可以使用空格。</span><span class="sxs-lookup"><span data-stu-id="18791-141">You cannot use spaces when renaming any of the Web service description nodes.</span></span>  
  
7.  <span data-ttu-id="18791-142">按一下**下一步**繼續使用精靈。</span><span class="sxs-lookup"><span data-stu-id="18791-142">Click **Next** to continue the wizard.</span></span>  
  
8.  <span data-ttu-id="18791-143">在**WCF 服務屬性**頁面上，於**WCF 服務的 Targetnamespace**  文字方塊中，輸入 WCF 服務的目標命名空間，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="18791-143">On the **WCF Service Properties** page, in the **Targetnamespace of the WCF service** text box, type a target namespace for the WCF services, and then click **Next**.</span></span>  
  
     <span data-ttu-id="18791-144">![WCF 服務屬性頁面](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")</span><span class="sxs-lookup"><span data-stu-id="18791-144">![WCF Service Properties page](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")</span></span>  
  
9. <span data-ttu-id="18791-145">在**WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="18791-145">On the **WCF Service Location** page, in the **Location** text box, type the Web directory name where the WCF services are generated.</span></span> <span data-ttu-id="18791-146">您可以接受預設位置 (http://localhost/\<*Web 服務描述名稱*>)，輸入中的 WCF 服務的位置**位置**文字方塊中或按一下**瀏覽**，並選取 Web 目錄。</span><span class="sxs-lookup"><span data-stu-id="18791-146">You can accept the default location (http://localhost/\<*Web service description name*>), type a location for the WCF services in the **Location** text box, or click **Browse** and select a Web directory.</span></span> <span data-ttu-id="18791-147">接著，選取下列任何一個選項：</span><span class="sxs-lookup"><span data-stu-id="18791-147">Select any of the following options:</span></span>  
  
    -   <span data-ttu-id="18791-148">**覆寫現有的專案。**</span><span class="sxs-lookup"><span data-stu-id="18791-148">**Overwrite existing project.**</span></span> <span data-ttu-id="18791-149">此選項只有在 Web 目錄已存在時才能使用。</span><span class="sxs-lookup"><span data-stu-id="18791-149">This option is available only if the Web directory already exists.</span></span> <span data-ttu-id="18791-150">只有當您選取了這個選項時，才能夠發佈至相同的位置。</span><span class="sxs-lookup"><span data-stu-id="18791-150">You will be able to publish to the same location only if you select this option.</span></span> <span data-ttu-id="18791-151">否則，您必須輸入不同的專案位置。</span><span class="sxs-lookup"><span data-stu-id="18791-151">Otherwise, you must enter a different project location.</span></span>  
  
    -   <span data-ttu-id="18791-152">**允許匿名存取 WCF 服務。**</span><span class="sxs-lookup"><span data-stu-id="18791-152">**Allow anonymous access to WCF service.**</span></span> <span data-ttu-id="18791-153">這個選項會新增已建立之虛擬目錄的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="18791-153">This option adds anonymous access to the created virtual directory.</span></span> <span data-ttu-id="18791-154">根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。</span><span class="sxs-lookup"><span data-stu-id="18791-154">By default, the virtual directory inherits the access privileges from its parent virtual directory or the Web site (if it is a top-level virtual directory).</span></span>  
  
     <span data-ttu-id="18791-155">當您完成這個頁面上時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="18791-155">When you finish this page, click **Next**.</span></span>  
  
     <span data-ttu-id="18791-156">![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")</span><span class="sxs-lookup"><span data-stu-id="18791-156">![WCF Service location page](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-157">專案位置可以存在不同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="18791-157">The project location can exist on a different server.</span></span> <span data-ttu-id="18791-158">若要將 WCF 服務發佈到另一部伺服器中，輸入專案名稱做為 http://\<*servername*>/\<*WCF 服務位置*>。</span><span class="sxs-lookup"><span data-stu-id="18791-158">To publish the WCF services to a different server, type the project name as http://\<*servername*>/\<*WCF service location*>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-159">專案位置可以存在非預設的網站上。</span><span class="sxs-lookup"><span data-stu-id="18791-159">The project location can exist on a non-default Web site.</span></span> <span data-ttu-id="18791-160">發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="18791-160">When publishing to a non-default Web site, include the port number of the Web site in the URL.</span></span> <span data-ttu-id="18791-161">例如 http://\<*servername*>: 8080 /\<*WCF 服務位置*>。</span><span class="sxs-lookup"><span data-stu-id="18791-161">For example, http://\<*servername*>:8080/\<*WCF service location*>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-162">精靈在 Web 應用程式之 \App_Data\Temp 資料夾中建立的 BindingInfo.xml 檔案會使用管線的預設值。</span><span class="sxs-lookup"><span data-stu-id="18791-162">The BindingInfo.xml file that the wizard creates in the \App_Data\Temp folder of the Web application uses the default values for the pipelines.</span></span> <span data-ttu-id="18791-163">接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.XMLReceive**管線，而預設值的傳送管線是**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**管線。</span><span class="sxs-lookup"><span data-stu-id="18791-163">The default value for the receive pipeline is the **Microsoft.BizTalk.DefaultPipelines.XMLReceive** pipeline, and the default value for the send pipeline is the **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit** pipeline.</span></span>  
  
10. <span data-ttu-id="18791-164">在**WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="18791-164">On the **WCF Service Summary** page, review your settings for the WCF services.</span></span>  
  
11. <span data-ttu-id="18791-165">按一下**建立**建立 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="18791-165">Click **Create** to create the WCF services.</span></span>  
  
12. <span data-ttu-id="18791-166">按一下**完成**完成 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="18791-166">Click **Finish** to complete the BizTalk WCF Service Publishing Wizard.</span></span>  
  
### <a name="to-configure-the-web-application-for-publishing-service-metadata"></a><span data-ttu-id="18791-167">若要設定發佈服務中繼資料的 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="18791-167">To configure the Web application for publishing service metadata</span></span>  
  
1.  <span data-ttu-id="18791-168">針對 BizTalk WCF 服務發佈精靈所建立的 Web 應用程式啟用 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="18791-168">Enable ASP.NET for the Web application that the BizTalk WCF Service Publishing Wizard created.</span></span> <span data-ttu-id="18791-169">如需詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="18791-169">For more information, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-170">如果您正使用其他版本的 Windows 作業系統，就必須將應用程式集區的識別帳戶新增至 BizTalk Server 系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="18791-170">If you are using another version of the Windows operating system, you must add the Identity Account of the Application Pool to the BizTalk Server Administrators group.</span></span> <span data-ttu-id="18791-171">將適當的帳戶新增至 BizTalk Server 系統管理員群組之後，您必須重新啟動 IIS 服務，才能讓設定生效。</span><span class="sxs-lookup"><span data-stu-id="18791-171">After you add the appropriate account to the BizTalk Server Administrators group, you need to restart the IIS service for the setting to take effect.</span></span>  
  
2.  <span data-ttu-id="18791-172">開啟命令提示字元，請移至 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾\\，然後開啟 Web.config 檔案，使用 記事本。</span><span class="sxs-lookup"><span data-stu-id="18791-172">Open a command prompt, go to the folder where the BizTalk WCF Service Publishing Wizard created the WCF services in %SystemDrive%\InetPub\\, and then open the Web.config file using Notepad.</span></span>  
  
3.  <span data-ttu-id="18791-173">在記事本中，加入下列一行 **\<system.web >**項目：</span><span class="sxs-lookup"><span data-stu-id="18791-173">In Notepad, add the following line inside the **\<system.web>** element:</span></span>  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="18791-174">這項設定是選擇性的，而且它會將受限於作業系統安全性之任何資源的存取權授與主控已發佈之 WCF 服務的 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="18791-174">This setting is optional and it grants the ASP.NET application hosting the published WCF service access to any resource that is subject to operating system security.</span></span> <span data-ttu-id="18791-175">當您在同一部電腦上安裝和執行 Windows SharePoint Services 以及已發佈的 WCF 服務時，這就是 WCF 所需的信任層級。</span><span class="sxs-lookup"><span data-stu-id="18791-175">This is the trust level that WCF requires when you have Windows SharePoint Services installed and running on the same machine with the published WCF services.</span></span>  
  
4.  <span data-ttu-id="18791-176">在 Internet Explorer 中**位址**方塊中，輸入使用 http:// 的格式為 WCF 服務的 URL*主機 [: 連接埠]*/*apppath* /*wcfservicename.svc*來測試已發佈的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="18791-176">In Internet Explorer, in the **Address** box, type the URL for the WCF service using the format http://*host[:port]*/*apppath*/*wcfservicename.svc* to test the published WCF service.</span></span> <span data-ttu-id="18791-177">下表將描述這些參數。</span><span class="sxs-lookup"><span data-stu-id="18791-177">The parameters are described in the following table.</span></span>  
  
    |<span data-ttu-id="18791-178">參數</span><span class="sxs-lookup"><span data-stu-id="18791-178">Parameter</span></span>|<span data-ttu-id="18791-179">值</span><span class="sxs-lookup"><span data-stu-id="18791-179">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="18791-180">*主機 [: 連接埠]*</span><span class="sxs-lookup"><span data-stu-id="18791-180">*host[:port]*</span></span>|<span data-ttu-id="18791-181">您已部署 WCF 服務之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="18791-181">The name of the computer where you have deployed your WCF service.</span></span> <span data-ttu-id="18791-182">冒號和連接埠編號可以接在這個伺服器名稱後面。</span><span class="sxs-lookup"><span data-stu-id="18791-182">A colon and the port number can follow this server name.</span></span>|  
    |<span data-ttu-id="18791-183">*apppath*</span><span class="sxs-lookup"><span data-stu-id="18791-183">*apppath*</span></span>|<span data-ttu-id="18791-184">虛擬目錄的名稱和 Web 應用程式路徑。</span><span class="sxs-lookup"><span data-stu-id="18791-184">The name of your virtual directory and the Web application path.</span></span>|  
    |<span data-ttu-id="18791-185">*wcfservicename.svc*</span><span class="sxs-lookup"><span data-stu-id="18791-185">*wcfservicename.svc*</span></span>|<span data-ttu-id="18791-186">WCF 服務 .svc 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="18791-186">The name of the WCF service .svc file.</span></span>|  
  
5.  <span data-ttu-id="18791-187">為了避免不小心洩露可能含有機密的服務中繼資料，我們建議您透過執行下列工作，在實際執行環境中停用這種行為：</span><span class="sxs-lookup"><span data-stu-id="18791-187">To prevent unintentional disclosure of potentially sensitive service metadata, we recommend that you disable this behavior in the production environment by performing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="18791-188">在 記事本 開啟 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾中的 Web.config\\。</span><span class="sxs-lookup"><span data-stu-id="18791-188">In Notepad, open Web.config in the folder where the BizTalk WCF Service Publishing Wizard created the WCF service in %SystemDrive%\InetPub\\.</span></span>  
  
    2.  <span data-ttu-id="18791-189">在 [記事本]，設定**httpGetEnabled**屬性 **\<serviceMetadata >**為 false，如下列的行項目：</span><span class="sxs-lookup"><span data-stu-id="18791-189">In Notepad, set the  the **httpGetEnabled** attribute in the  **\<serviceMetadata>** element to false as following line:</span></span>  
  
        ```  
        <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="18791-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18791-190">See Also</span></span>  
 <span data-ttu-id="18791-191">[如何使用 BizTalk WCF 服務發佈精靈結構描述發佈為 WCF 服務](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="18791-191">[How to Use the BizTalk WCF Service Publishing Wizard to Publish Schemas as WCF Services](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md) </span></span>  
 [<span data-ttu-id="18791-192">逐步解說： 使用發佈 WCF 服務 Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="18791-192">Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)