---
title: "步驟 3： 實作 Echo 介面卡的連線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc223901-3ad3-4e71-8672-fea6bb4efe65
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a735654fd03f5efb39fe73eb845f4db3632d283
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-implement-the-connection-for-the-echo-adapter"></a><span data-ttu-id="2ffe9-102">步驟 3： 實作 Echo 介面卡的連線</span><span class="sxs-lookup"><span data-stu-id="2ffe9-102">Step 3: Implement the Connection for the Echo Adapter</span></span>
<span data-ttu-id="2ffe9-103">![步驟 3 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")</span><span class="sxs-lookup"><span data-stu-id="2ffe9-103">![Step 3 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")</span></span>  
  
 <span data-ttu-id="2ffe9-104">**若要完成的時間：** 45 分鐘的時間</span><span class="sxs-lookup"><span data-stu-id="2ffe9-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="2ffe9-105">在此步驟中，您可以實作回應配接器的連線能力。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-105">In this step, you implement the connection capability of the Echo adapter.</span></span> <span data-ttu-id="2ffe9-106">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您連接到目標系統時必須實作下列的抽象類別和介面。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-106">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you must implement the following abstract class and interfaces when connecting to the target system.</span></span>  
  
-   `Microsoft.ServiceModel.Channels.Common.ConnectionUri`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnection`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`  
  
 <span data-ttu-id="2ffe9-107">而不是衍生自上述抽象類別和介面，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生三個衍生的類別、 EchoAdapterConnection、 EchoAdapterConnectionUri 和 EchoAdapterConnectionFactory。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-107">Instead of deriving from the above abstract class and interfaces, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the three derived classes, EchoAdapterConnection, EchoAdapterConnectionUri, and EchoAdapterConnectionFactory.</span></span> <span data-ttu-id="2ffe9-108">除了建立類別，每個有預設的方法會擲回特定例外狀況， `System.NotImplementedException`。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-108">In addition to creating the classes, each has a default method that throws a specific exception, `System.NotImplementedException`.</span></span>  <span data-ttu-id="2ffe9-109">這個陳述式會提醒開發人員實作每個類別。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-109">This statement reminds the developer to implement each class.</span></span>  <span data-ttu-id="2ffe9-110">類別實作時，您必須移除這個擲回例外狀況的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-110">When the class is implemented, this exception-throwing statement must be removed.</span></span>  
  
 <span data-ttu-id="2ffe9-111">在下列區段中，您可以更新這些三個類別，以取得更深入了解如何處理連接、 URI 結構為何，以及如何以程式設計方式擷取各種 URI 項目，然後使用 配接器內的這些項目。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-111">In the following section, you update those three classes to get a better understanding of how to handle a connection, what the URI structure is, and how to programmatically retrieve various URI elements and then use those elements within the adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2ffe9-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="2ffe9-112">Prerequisites</span></span>  
 <span data-ttu-id="2ffe9-113">在開始此步驟之前，您必須已順利完成[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-113">Before you begin this step, you must have successfully completed [Step 2: Categorize the Adapter and Connection Properties](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).</span></span> <span data-ttu-id="2ffe9-114">而且您應該已經清楚了解`Microsoft.ServiceModel.Channels.Common.IConnection`， `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`，和`Microsoft.ServiceModel.Channels.Common.ConnectionUri`類別。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-114">And you should have a clear understanding of the `Microsoft.ServiceModel.Channels.Common.IConnection`, `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`, and `Microsoft.ServiceModel.Channels.Common.ConnectionUri` classes.</span></span>  
  
## <a name="connection-related-classes"></a><span data-ttu-id="2ffe9-115">連線相關類別</span><span class="sxs-lookup"><span data-stu-id="2ffe9-115">Connection-Related Classes</span></span>  
 <span data-ttu-id="2ffe9-116">[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]產生三個衍生的類別、 EchoAdapterConnection、 EchoAdapterConnectionUri 和 EchoAdapterConnectionFactory。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-116">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] generates three derived classes, EchoAdapterConnection, EchoAdapterConnectionUri, and EchoAdapterConnectionFactory.</span></span> <span data-ttu-id="2ffe9-117">下面提供方法的每個相關聯的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-117">The following provides a brief overview of methods associated with each.</span></span>  
  
### <a name="echoadapterconnection"></a><span data-ttu-id="2ffe9-118">EchoAdapterConnection</span><span class="sxs-lookup"><span data-stu-id="2ffe9-118">EchoAdapterConnection</span></span>  
 <span data-ttu-id="2ffe9-119">根據您的配接器複雜度，您可能需要實作所有下列五個方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-119">Depending on your adapter complexity, you might need to implement all of the following five methods.</span></span> <span data-ttu-id="2ffe9-120">為了回應配接器，也不支援大多數，因為回應配接器範例並不包含任何目標系統。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-120">For Echo adapter, most are not supported, because the Echo adapter sample does not involve any target system.</span></span>  
  
|<span data-ttu-id="2ffe9-121">**方法**</span><span class="sxs-lookup"><span data-stu-id="2ffe9-121">**Method**</span></span>|<span data-ttu-id="2ffe9-122">**說明**</span><span class="sxs-lookup"><span data-stu-id="2ffe9-122">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="2ffe9-123">public void 關閉 （TimeSpan 逾時）</span><span class="sxs-lookup"><span data-stu-id="2ffe9-123">public void Close(TimeSpan timeout)</span></span>|<span data-ttu-id="2ffe9-124">關閉的連接到目標系統。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-124">Closes the connection to the target system.</span></span> <span data-ttu-id="2ffe9-125">回應配接器會使用這個方法只將追蹤事件加入至追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-125">The Echo adapter uses this method to only add trace events to the trace listener.</span></span>|  
|<span data-ttu-id="2ffe9-126">公用 bool IsValid （TimeSpan 逾時）</span><span class="sxs-lookup"><span data-stu-id="2ffe9-126">public bool IsValid(TimeSpan timeout)</span></span>|<span data-ttu-id="2ffe9-127">傳回值，指出連接是否仍然有效。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-127">Returns a value indicating whether the connection is still valid.</span></span><br /><br /> <span data-ttu-id="2ffe9-128">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-128">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="2ffe9-129">public void 開啟 （TimeSpan 逾時）</span><span class="sxs-lookup"><span data-stu-id="2ffe9-129">public void Open(TimeSpan timeout)</span></span>|<span data-ttu-id="2ffe9-130">開啟 連接到目標系統。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-130">Opens the connection to the target system.</span></span><br /><br /> <span data-ttu-id="2ffe9-131">不適用於 「 回應配接器。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-131">N/A for the Echo adapter.</span></span> <span data-ttu-id="2ffe9-132">不過，此範例示範您如何使用稱為 enableAuthentication URI 項目以要求使用者提供的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-132">However, the example shows you how to use a URI element called enableAuthentication to require users to provide a user name.</span></span>|  
|<span data-ttu-id="2ffe9-133">public void ClearContext()</span><span class="sxs-lookup"><span data-stu-id="2ffe9-133">public void ClearContext()</span></span>|<span data-ttu-id="2ffe9-134">清除連接內容。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-134">Clears the context of the connection.</span></span> <span data-ttu-id="2ffe9-135">連接重設為連接集區時，會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-135">This method is called when the connection is set back to the connection pool.</span></span><br /><br /> <span data-ttu-id="2ffe9-136">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-136">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="2ffe9-137">public void abort （)</span><span class="sxs-lookup"><span data-stu-id="2ffe9-137">public void Abort()</span></span>|<span data-ttu-id="2ffe9-138">中止連線到目標系統。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-138">Aborts the connection to the target system.</span></span><br /><br /> <span data-ttu-id="2ffe9-139">不支援回應配接器。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-139">Not supported by the Echo adapter.</span></span>|  
  
### <a name="echoadapterconnectionfactory"></a><span data-ttu-id="2ffe9-140">EchoAdapterConnectionFactory</span><span class="sxs-lookup"><span data-stu-id="2ffe9-140">EchoAdapterConnectionFactory</span></span>  
 <span data-ttu-id="2ffe9-141">連線 factory 會負責建立連線。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-141">The connection factory is responsible for creating the connection.</span></span> <span data-ttu-id="2ffe9-142">根據預設，您必須在連接到目標系統時，才修改這個類別。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-142">By default, you must modify this class only when connecting to a target system.</span></span> <span data-ttu-id="2ffe9-143">雖然回應配接器不含任何目標系統，它會顯示您如何使用自訂的 URI 項目，如果您的連線要求使用者驗證呼叫 enableAuthentication。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-143">Although the Echo adapter does not involve any target system, it shows you how to use a custom URI element called enableAuthentication if your connection requires user authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ffe9-144">EnableAuthentication 不能是關鍵字，只是變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-144">The enableAuthentication is not a keyword, it is just a variable name.</span></span> <span data-ttu-id="2ffe9-145">因此，您可以選擇任何名稱。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-145">Hence, you can choose any name for it.</span></span>  
  
### <a name="echoadapterconnectionuri"></a><span data-ttu-id="2ffe9-146">EchoAdapterConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2ffe9-146">EchoAdapterConnectionUri</span></span>  
 <span data-ttu-id="2ffe9-147">這表示目標系統的連接字串。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-147">This represents a connection string to the target system.</span></span>  
  
|<span data-ttu-id="2ffe9-148">**方法**</span><span class="sxs-lookup"><span data-stu-id="2ffe9-148">**Method**</span></span>|<span data-ttu-id="2ffe9-149">**說明**</span><span class="sxs-lookup"><span data-stu-id="2ffe9-149">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="2ffe9-150">Uri 的 Uri 的公用覆寫</span><span class="sxs-lookup"><span data-stu-id="2ffe9-150">public override Uri Uri</span></span>|<span data-ttu-id="2ffe9-151">取得和設定的 Uri。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-151">Gets and sets the Uri.</span></span> <span data-ttu-id="2ffe9-152">若要建置 Uri 字串取得及設定剖析 Uri 的字串。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-152">Gets to build the Uri string and sets to parse the Uri string.</span></span>|  
|<span data-ttu-id="2ffe9-153">公用 EchoAdapterConnectionUri()</span><span class="sxs-lookup"><span data-stu-id="2ffe9-153">public EchoAdapterConnectionUri()</span></span>|<span data-ttu-id="2ffe9-154">初始化 ConnectionUri 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-154">Initializes a new instance of the ConnectionUri class.</span></span>|  
|<span data-ttu-id="2ffe9-155">公用覆寫字串 SampleUriString</span><span class="sxs-lookup"><span data-stu-id="2ffe9-155">public override string SampleUriString</span></span>|<span data-ttu-id="2ffe9-156">傳回 EchoAdapter.SCHEME +": //{hostname}/{application}?enableAuthentication={True &#124;False}"。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-156">Returns EchoAdapter.SCHEME + "://{hostname}/{application}?enableAuthentication={True&#124;False}".</span></span><br /><br /> <span data-ttu-id="2ffe9-157">這個傳回的字串會顯示為**範例**中[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-157">This return string displays as the **Example** in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, as shown in the following figure.</span></span>|  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
## <a name="echo-adapter-connection-uri"></a><span data-ttu-id="2ffe9-158">回應配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="2ffe9-158">Echo Adapter Connection URI</span></span>  
 <span data-ttu-id="2ffe9-159">範例回應配接器連線 URI 如下： EchoAapter.SCHEME://{hostname}/{application}?enableAuthentication={true &#124; false}</span><span class="sxs-lookup"><span data-stu-id="2ffe9-159">The sample Echo adapter connection URI is described as: EchoAapter.SCHEME://{hostname}/{application}?enableAuthentication={true&#124;false}</span></span>  
  
 <span data-ttu-id="2ffe9-160">由於 EchoAapter.SCHEME echov2，連線 URI 是：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-160">Since the EchoAapter.SCHEME is echov2, the connection URI is:</span></span>  
  
 <span data-ttu-id="2ffe9-161">echo2: / lobhostname/lobapplication？ enableAuthentication = {true &#124; false}</span><span class="sxs-lookup"><span data-stu-id="2ffe9-161">echo2://lobhostname/lobapplication?enableAuthentication={true&#124;false}</span></span>  
  
 <span data-ttu-id="2ffe9-162">您可以讀取先前的連線 URI 時 enableAuthentication = false，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-162">You can read the previous connection URI when enableAuthentication=false as follows:</span></span>  
  
 <span data-ttu-id="2ffe9-163">使用 echov2 傳輸結構描述，請移至名為 lobhostname，電腦名為不需要任何驗證的 lobapplication 的應用程式正在等待您的連線。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-163">Using the echov2 transport schema, go to a computer named lobhostname, where an application named lobapplication that does not require any authentication is waiting for your connection.</span></span>  
  
 <span data-ttu-id="2ffe9-164">或者，當 enableAuthentication = true 時，讀取連接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-164">Or, when enableAuthentication=true, read the connection as follows:</span></span>  
  
 <span data-ttu-id="2ffe9-165">使用 echov2 傳輸結構描述，請移至名為 lobhostname，電腦名為 lobapplication 的應用程式預期驗證正在等候您的連線。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-165">Using the echov2 transport schema, go to a computer named lobhostname, where an application named lobapplication expects that authentication is waiting for your connection.</span></span> <span data-ttu-id="2ffe9-166">回應配接器，使用者則只需要名稱。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-166">For the Echo adapter, only a user name is required.</span></span>  
  
 <span data-ttu-id="2ffe9-167">具有已定義的 URI，可以透過程式設計方式取用及剖析進行連接，並設定。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-167">With a defined URI, you can programmatically consume and parse it for connectivity and configuration.</span></span> <span data-ttu-id="2ffe9-168">如果連接需要使用者名稱和密碼等機密資料，並包含在 URI 中的這類資訊。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-168">If the connection requires sensitive data such as a user name and password, do not contain such information in the URI.</span></span> <span data-ttu-id="2ffe9-169">相反地，將在這類資訊`System.ServiceModel.Description.ClientCredentials`物件。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-169">Instead, add such information in the `System.ServiceModel.Description.ClientCredentials` object.</span></span> <span data-ttu-id="2ffe9-170">您加入的程式碼範例會示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-170">The code example that you add shows you how to do so.</span></span>  
  
 <span data-ttu-id="2ffe9-171">下列程式碼，回應配接器會建構兩種方式可以顯示配接器可以如何使用各種 URI 項目修改配接器功能中的 URI。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-171">In the following code, the Echo adapter constructs the URI in two ways to show you how the adapter can use various URI elements to modify the adapter feature.</span></span>  
  
 <span data-ttu-id="2ffe9-172">echo2: / lobhostname/lobapplication？ enableAuthentication = [true &#124; false]</span><span class="sxs-lookup"><span data-stu-id="2ffe9-172">echo2://lobhostname/lobapplication?enableAuthentication=[true&#124;false]</span></span>  
  
 <span data-ttu-id="2ffe9-173">echo2: / lobhostname/lobapplication？ enableAuthentication = [true &#124; false] （& s) echoInUpperCase = true</span><span class="sxs-lookup"><span data-stu-id="2ffe9-173">echo2://lobhostname/lobapplication?enableAuthentication=[true&#124;false]&echoInUpperCase=true</span></span>  
  
### <a name="retrieving-the-uri-element"></a><span data-ttu-id="2ffe9-174">擷取 URI 項目</span><span class="sxs-lookup"><span data-stu-id="2ffe9-174">Retrieving the URI Element</span></span>  
 <span data-ttu-id="2ffe9-175">您可以剖析 URI 中的各個項目的回應配接器 URI echo2: / lobhostname/lobapplication？ enableAuthentication = false & echoInUpperCase = false。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-175">You can parse each URI element in the Echo adapter URI echo2://lobhostname/lobapplication?enableAuthentication=false&echoInUpperCase=false.</span></span>  <span data-ttu-id="2ffe9-176">下表中列出的 URI 項目值和相關聯的方法：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-176">The URI element values and associated methods are listed in the following table:</span></span>  
  
|<span data-ttu-id="2ffe9-177">**URI 的項目值**</span><span class="sxs-lookup"><span data-stu-id="2ffe9-177">**URI Element Value**</span></span>|<span data-ttu-id="2ffe9-178">**方法**</span><span class="sxs-lookup"><span data-stu-id="2ffe9-178">**Method**</span></span>|  
|---------------------------|----------------|  
|<span data-ttu-id="2ffe9-179">lobhostname</span><span class="sxs-lookup"><span data-stu-id="2ffe9-179">lobhostname</span></span>|<span data-ttu-id="2ffe9-180">`System.Uri.Host%2A`若要擷取的主機名稱</span><span class="sxs-lookup"><span data-stu-id="2ffe9-180">`System.Uri.Host%2A` to retrieve the host name</span></span>|  
|<span data-ttu-id="2ffe9-181">Lobapplication</span><span class="sxs-lookup"><span data-stu-id="2ffe9-181">Lobapplication</span></span>|<span data-ttu-id="2ffe9-182">`System.Uri.AbsolutePath%2A`若要擷取的目標應用程式名稱</span><span class="sxs-lookup"><span data-stu-id="2ffe9-182">`System.Uri.AbsolutePath%2A` to retrieve the target application name</span></span>|  
|<span data-ttu-id="2ffe9-183">enableAuthentation = false</span><span class="sxs-lookup"><span data-stu-id="2ffe9-183">enableAuthentation=false</span></span>|<span data-ttu-id="2ffe9-184">GetQueryStringValue("enableAuthentication")</span><span class="sxs-lookup"><span data-stu-id="2ffe9-184">GetQueryStringValue("enableAuthentication")</span></span><br /><br /> <span data-ttu-id="2ffe9-185">使用此 URI 的項目，來驗證使用者認證**附註：** GetQueryStringValue 是中定義的靜態方法`Microsoft.ServiceModel.Channels.Common.ConnectionUri`</span><span class="sxs-lookup"><span data-stu-id="2ffe9-185">Use this URI element to validate user credentials **Note:**  GetQueryStringValue is a static method defined in the `Microsoft.ServiceModel.Channels.Common.ConnectionUri`</span></span>|  
|<span data-ttu-id="2ffe9-186">echoInUpperValue = false</span><span class="sxs-lookup"><span data-stu-id="2ffe9-186">echoInUpperValue=false</span></span>|<span data-ttu-id="2ffe9-187">GetQueryStringValue("echoInUpperValue")</span><span class="sxs-lookup"><span data-stu-id="2ffe9-187">GetQueryStringValue("echoInUpperValue")</span></span><br /><br /> <span data-ttu-id="2ffe9-188">您可以使用此 URI 項目，將傳入的字串轉換為大寫。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-188">Use this URI element to convert the incoming string to upper case.</span></span>|  
  
### <a name="enableauthentication-uri-element"></a><span data-ttu-id="2ffe9-189">EnableAuthentication URI 項目</span><span class="sxs-lookup"><span data-stu-id="2ffe9-189">EnableAuthentication URI Element</span></span>  
 <span data-ttu-id="2ffe9-190">目標系統通常會要求您提供用戶端認證以連接到目標系統。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-190">Your target system often requires you to provide client credentials to establish a connection to the target system.</span></span> <span data-ttu-id="2ffe9-191">如前所述，回應配接器不包括任何目標系統。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-191">As mentioned, the Echo adapter does not involve any target system.</span></span> <span data-ttu-id="2ffe9-192">雖然作為範例，它會示範如何使用自訂的 URI 項目，稱為 enableAuthentication 提供的認證。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-192">Though as a sample, it shows how to use a custom URI element called enableAuthentication to provide the credentials.</span></span>  
  
```  
 public class EchoAdapterConnection : IConnection   
{  
….  
   public void Open(TimeSpan timeout)  
  {  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
  }  
}  
```  
  
 <span data-ttu-id="2ffe9-193">程式碼會檢查以查看 enableAuthentication 為 true，如果未提供使用者名稱。如果未提供使用者名稱，就會擲回的例外狀況，它會攔截[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-193">The code checks to see if enableAuthentication is true and if a user name is not provided; if a user name is not provided, it throws an exception, which is caught by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, as shown below:</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/901095c7-c70d-491a-a1ae-8f37f22a61a7.gif "901095c7-c70d-491a-a1ae-8f37f22a61a7")  
  
 <span data-ttu-id="2ffe9-194">若要提供使用者名稱，也可以輸入在設定配接器 對話方塊中[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-194">To provide the user name, you can enter it in the Configure Adapter dialog box in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, as shown in the following figure:</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4069a7d-1403-4195-b0b5-21ad97dbc3ce.gif "e4069a7d-1403-4195-b0b5-21ad97dbc3ce")  
  
### <a name="echoinuppercase-uri-element"></a><span data-ttu-id="2ffe9-195">EchoInUpperCase URI 項目</span><span class="sxs-lookup"><span data-stu-id="2ffe9-195">EchoInUpperCase URI Element</span></span>  
 <span data-ttu-id="2ffe9-196">布林旗標，例如，您可以參考 EchoInUpperCase URI 項目。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-196">The EchoInUpperCase URI element can be referenced like a Boolean flag.</span></span> <span data-ttu-id="2ffe9-197">如果旗標為 true，配接器會轉換 EchoStrings 作業的輸入的字串為大寫。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-197">If the flag is true, then the adapter converts the input string of the EchoStrings operation to uppercase.</span></span>  
  
 <span data-ttu-id="2ffe9-198">若要變更預設值的 echoInUpperCase URI 項目，使用 [URI 屬性] 索引標籤中設定的介面卡[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如下所示。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-198">To change the default value of the echoInUpperCase URI element, use the URI Properties tab of the Configure Adapter in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], as shown below.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f22511b2-3fca-4875-ac65-8e61f4367e94.gif "f22511b2-3fca-4875-ac65-8e61f4367e94")  
  
## <a name="updating-echoadapterconnection"></a><span data-ttu-id="2ffe9-199">更新 EchoAdapterConnection</span><span class="sxs-lookup"><span data-stu-id="2ffe9-199">Updating EchoAdapterConnection</span></span>  
 <span data-ttu-id="2ffe9-200">您實作 IsValid、 開啟和關閉 EchoAdapterConnection 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-200">You implement the IsValid, Open, and Close method of the EchoAdapterConnection class.</span></span>  
  
#### <a name="to-update-the-echoadapterconnection-class"></a><span data-ttu-id="2ffe9-201">若要更新 EchoAdapterConnection 類別</span><span class="sxs-lookup"><span data-stu-id="2ffe9-201">To update the EchoAdapterConnection class</span></span>  
  
1.  <span data-ttu-id="2ffe9-202">在**方案總管 中**，連按兩下**EchoAdapterConnection.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-202">In **Solution Explorer**, double-click the **EchoAdapterConnection.cs** file.</span></span>  
  
2.  <span data-ttu-id="2ffe9-203">在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-203">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="2ffe9-204">在 Visual Studio 編輯器中，尋找**IsValid**方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-204">In the Visual Studio editor, find the **IsValid** method.</span></span> <span data-ttu-id="2ffe9-205">內部**IsValid**方法，取代現有的實作如下：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-205">Inside the **IsValid** method, replace the existing implementation with the one below:</span></span>  
  
    ```csharp  
    return true;  
    ```  
  
4.  <span data-ttu-id="2ffe9-206">在 Visual Studio 編輯器中，尋找**開啟**方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-206">In the Visual Studio editor, find the **Open** method.</span></span> <span data-ttu-id="2ffe9-207">內部**開啟**方法，以下列實作取代現有的實作。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-207">Inside the **Open** method, replace the existing implementation with the following implementation.</span></span> <span data-ttu-id="2ffe9-208">這會顯示您如何使用 URI enableAuthentication 項目，以確保在提供使用者名稱：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-208">This shows you how to use the URI enableAuthentication element to ensure user  name is provided:</span></span>  
  
    ```csharp  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        // it just logs the credentials in the trace file  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
        // got the username, log it in trace file  
        EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Username is " + this.connectionFactory.ClientCredentials.UserName.UserName);  
    }  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully established!");  
    ```  
  
5.  <span data-ttu-id="2ffe9-209">在 Visual Studio 編輯器中，尋找**關閉**方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-209">In the Visual Studio editor, find the **Close** method.</span></span> <span data-ttu-id="2ffe9-210">內部**關閉**方法，加入下列單一陳述式：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-210">Inside the **Close** method, add the following single statement:</span></span>  
  
    ```csharp  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Close", "Connection successfully closed!");  
    ```  
  
## <a name="updating-the-echoadapterconnectionfactory"></a><span data-ttu-id="2ffe9-211">更新 EchoAdapterConnectionFactory</span><span class="sxs-lookup"><span data-stu-id="2ffe9-211">Updating the EchoAdapterConnectionFactory</span></span>  
 <span data-ttu-id="2ffe9-212">您實作 EchoAdapterConnectionFactory 建構函式，並加入稱為 ClientCredentials 和 ConnectionUri 的兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-212">You implement EchoAdapterConnectionFactory constructor, and add two properties called ClientCredentials and ConnectionUri.</span></span>  
  
#### <a name="to-update-the-echoadapterconnectionfactory-class"></a><span data-ttu-id="2ffe9-213">若要更新 EchoAdapterConnectionFactory 類別</span><span class="sxs-lookup"><span data-stu-id="2ffe9-213">To update the EchoAdapterConnectionFactory class</span></span>  
  
1.  <span data-ttu-id="2ffe9-214">在**方案總管 中**，連按兩下**EchoAdapterConnectionFactory.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-214">In **Solution Explorer**, double-click the **EchoAdapterConnectionFactory.cs** file.</span></span>  
  
2.  <span data-ttu-id="2ffe9-215">在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-215">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="2ffe9-216">在 Visual Studio 編輯器中，尋找**私用欄位**區域。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-216">In the Visual Studio editor, find the **Private Fields** region.</span></span> <span data-ttu-id="2ffe9-217">加入下列單一陳述式：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-217">Add the following single statement:</span></span>  
  
    ```csharp  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
     <span data-ttu-id="2ffe9-218">您的私用欄位的清單應該符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-218">Your list of private fields should match the following:</span></span>  
  
    ```csharp  
    // Stores the client credentials  
    private ClientCredentials clientCredentials;  
    // Stores the adapter class  
    private EchoAdapter adapter;  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
4.  <span data-ttu-id="2ffe9-219">在 Visual Studio 編輯器中，尋找**EchoAdapterConnectionFactory**方法。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-219">In the Visual Studio editor, find the **EchoAdapterConnectionFactory** method.</span></span> <span data-ttu-id="2ffe9-220">內部**EchoAdapterConnectionFactory**建構函式方法之前"}"，做為最後一個陳述式加入下列單一陳述式。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-220">Inside the **EchoAdapterConnectionFactory** constructor method, before "}", add the following single statement as the last statement.</span></span>  
  
    ```csharp  
    this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    ```  
  
     <span data-ttu-id="2ffe9-221">實作**EchoAdapterConnectionFactory**方法應符合下列：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-221">The implementation of the **EchoAdapterConnectionFactory** method should match the following:</span></span>  
  
    ```csharp  
    /// <summary>  
    /// Initializes a new instance of the EchoAdapterConnectionFactory class  
    /// </summary>  
    public EchoAdapterConnectionFactory(ConnectionUri connectionUri  
        , ClientCredentials clientCredentials  
        , EchoAdapter adapter)  
    {  
        this.clientCredentials = clientCredentials;  
        this.adapter = adapter;  
        //added  
        this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    }  
    ```  
  
5.  <span data-ttu-id="2ffe9-222">在 Visual Studio 編輯器中，尋找**公用屬性**區域。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-222">In the Visual Studio editor, find the **Public Properties** region.</span></span> <span data-ttu-id="2ffe9-223">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-223">Add the following code:</span></span>  
  
    ```csharp  
    /// <summary>  
    /// Returns the client credentials  
    /// </summary>  
    public ClientCredentials ClientCredentials  
    {  
        get  
        {  
            return this.clientCredentials;  
        }  
    }  
  
    /// <summary>  
    /// Returns the Connection Uri for this adapter  
    /// </summary>  
    public EchoAdapterConnectionUri ConnectionUri  
    {  
        get  
        {  
            return this.connectionUri;  
        }  
    }  
    ```  
  
## <a name="updating-the-echoadapterconnectionuri"></a><span data-ttu-id="2ffe9-224">更新 EchoAdapterConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2ffe9-224">Updating the EchoAdapterConnectionUri</span></span>  
 <span data-ttu-id="2ffe9-225">實作 EchoAdapterConnectionUri 預設建構函式、 EchoAdapterConnectionUri(Uri uri) 多載建構函式，而且公用覆寫 Uri Uri 屬性。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-225">You implement the EchoAdapterConnectionUri default constructor, EchoAdapterConnectionUri(Uri uri) overloaded constructor, and the public override Uri Uri property.</span></span>  
  
#### <a name="to-update-the-echoadapterconnectionuri-class"></a><span data-ttu-id="2ffe9-226">若要更新 EchoAdapterConnectionUri 類別</span><span class="sxs-lookup"><span data-stu-id="2ffe9-226">To update the EchoAdapterConnectionUri class</span></span>  
  
1.  <span data-ttu-id="2ffe9-227">在**方案總管 中**，連按兩下**EchoAdapterConnectionUri.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-227">In **Solution Explorer**, double-click the **EchoAdapterConnectionUri.cs** file.</span></span>  
  
2.  <span data-ttu-id="2ffe9-228">在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-228">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="2ffe9-229">在 Visual Studio 編輯器中，尋找**建構函式**區域。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-229">In the Visual Studio editor, find the **Constructors** region.</span></span> <span data-ttu-id="2ffe9-230">內部**EchoAdapterConnectionUri()**預設建構函式中，加入下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-230">Inside the **EchoAdapterConnectionUri()** default constructor, add the following statement:</span></span>  
  
    ```csharp  
    Uri = new Uri("echov2://lobhostname/lobapplication?enableauthentication=False");  
    ```  
  
4.  <span data-ttu-id="2ffe9-231">在 Visual Studio 編輯器中，內部**EchoAdapterConnectionUri (Uri uri)**多載建構函式，並加入下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-231">In the Visual Studio editor, inside the **EchoAdapterConnectionUri(Uri uri)** overloaded constructor, and add the following statement:</span></span>  
  
    ```csharp  
    Uri = uri;  
    ```  
  
     <span data-ttu-id="2ffe9-232">EchoAdapterConnectionUri(Uri uri) 方法的實作應該符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="2ffe9-232">Your implementation of the EchoAdapterConnectionUri(Uri uri) method should match the following:</span></span>  
  
    ```csharp  
    public EchoAdapterConnectionUri(Uri uri)  
        : base()  
    {  
        Uri = uri;  
    }  
    ```  
  
5.  <span data-ttu-id="2ffe9-233">在 Visual Studio 編輯器中，內部**公用覆寫 Uri Uri**方法，取代現有的使用下列邏輯。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-233">In the Visual Studio editor, inside the **public override Uri Uri** method, replace the existing with the following logic.</span></span> <span data-ttu-id="2ffe9-234">取得建置 echoInUpperCase 不論它的 Uri。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-234">The get builds the Uri with echoInUpperCase or without it.</span></span> <span data-ttu-id="2ffe9-235">將剖析的 URI 來擷取主機名稱、 資料庫名稱和查詢值。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-235">The set parses the URI to retrieve host name, database name, and query values.</span></span>  
  
    ```csharp  
    get  
    {  
        // Build the uri  
        if (String.IsNullOrEmpty(this.hostname)) throw new InvalidUriException("Invalid target system host name.");  
        if (String.IsNullOrEmpty(this.application)) throw new InvalidUriException("Invalid target system data source name.");  
        if (EchoInUpperCase)  
        {  
            // build the uri with echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication + "&" + "echoInUpperCase=" + echoInUpperCase);  
        }  
        else  
        {  
            // build the uri without echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication);  
        }  
    }  
    set  
    {  
        // Parse the uri  
        String[] enableAuthValue = GetQueryStringValue(value, "enableAuthentication");  
        if (enableAuthValue.Length > 0) this.enableAuthentication = Boolean.Parse(enableAuthValue[0]);  
        String[] echoInUpperValue = GetQueryStringValue(value, "echoInUpperCase");  
        if (echoInUpperValue.Length > 0) this.echoInUpperCase = Boolean.Parse(echoInUpperValue[0]);  
  
        this.hostname = value.Host;  
        String[] applicationValue = value.AbsolutePath.Split('/');  
        if (applicationValue.Length > 1) this.Application = applicationValue[1];  
    }  
    ```  
  
6.  <span data-ttu-id="2ffe9-236">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-236">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
7.  <span data-ttu-id="2ffe9-237">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-237">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="2ffe9-238">您應該成功編譯專案。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-238">You should successfully compile the project.</span></span> <span data-ttu-id="2ffe9-239">如果沒有，請確定您已依照上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-239">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ffe9-240">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-240">You saved your work.</span></span> <span data-ttu-id="2ffe9-241">您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 4： 實作回應配接器中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-241">You can safely close Visual Studio at this time or go to the next step, [Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="2ffe9-242">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="2ffe9-242">What Did I Just Do?</span></span>  
 <span data-ttu-id="2ffe9-243">您實作回應配接器的連接。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-243">You implemented the connection for the Echo adapter.</span></span> <span data-ttu-id="2ffe9-244">您已了解連接元件的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]、 連線 URI 的基本結構、 如何以程式設計方式剖析 URI 的項目，以及如何使用 URI 項目來變更介面卡功能。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-244">You learned the connection components of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the basic structure of the connection URI, how to programmatically parse the URI elements, and how you can use the URI element to change the adapter feature.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2ffe9-245">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2ffe9-245">Next Steps</span></span>  
 <span data-ttu-id="2ffe9-246">您可以實作中繼資料瀏覽、 搜尋和解析功能，以及輸出的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-246">You implement metadata browsing, searching, and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="2ffe9-247">最後，您會建置並部署配接器。</span><span class="sxs-lookup"><span data-stu-id="2ffe9-247">Finally, you build and deploy the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ffe9-248">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ffe9-248">See Also</span></span>  
 <span data-ttu-id="2ffe9-249">[步驟 4： 回應配接器實作中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="2ffe9-249">[Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="2ffe9-250">教學課程 1： 在開發回應配接器</span><span class="sxs-lookup"><span data-stu-id="2ffe9-250">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)