---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 5290f424bbeb5cf54e78c903c50a6c2d945bc8cc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-jd-edwards-oneworld-transport-properties"></a><span data-ttu-id="0212d-101">如何設定 JD Edwards OneWorld 傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="0212d-101">How to Set JD Edwards OneWorld Transport Properties</span></span>

## <a name="overview"></a><span data-ttu-id="0212d-102">概觀</span><span class="sxs-lookup"><span data-stu-id="0212d-102">Overview</span></span>
<span data-ttu-id="0212d-103">「JD Edwards OneWorld 傳輸屬性系統定義」用於設計和執行階段登入。</span><span class="sxs-lookup"><span data-stu-id="0212d-103">The JD Edwards OneWorld Transport Property System Definition is used for design and run-time logon.</span></span> <span data-ttu-id="0212d-104">您要設定這些認證以在設計階段瀏覽 JD Edwards OneWorld 商務功能，並在執行階段進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="0212d-104">You set these credentials to browse JD Edwards OneWorld business functions at design time and make calls at run time.</span></span>  
  
 <span data-ttu-id="0212d-105">當與 JD Edwards OneWorld 建立連線時，參數會傳送到連線物件 (使用者、密碼、環境)。</span><span class="sxs-lookup"><span data-stu-id="0212d-105">When a connection is made to JD Edwards OneWorld, parameters are passed to the connection object (User, Password, Environment).</span></span> <span data-ttu-id="0212d-106">它會傳回一個 JD Edwards OneWorld 應用程式商務函數。</span><span class="sxs-lookup"><span data-stu-id="0212d-106">It returns an instance of the JD Edwards OneWorld aApplication business function.</span></span> <span data-ttu-id="0212d-107">企業/應用程式伺服器名稱與服務接聽的已定義 TCP/IP 連接埠會進一步定義認證。</span><span class="sxs-lookup"><span data-stu-id="0212d-107">The credentials are further defined by the name of the enterprise/application server, and the defined TCP/IP port on which the service listens.</span></span>  
  
 <span data-ttu-id="0212d-108">從名為 jdeinterop.ini 的檔案讀取企業伺服器名稱和連接埠。</span><span class="sxs-lookup"><span data-stu-id="0212d-108">The enterprise server name and port are read from a file that is named jdeinterop.ini.</span></span> <span data-ttu-id="0212d-109">這些值必須是相同的系統定義的設定中。</span><span class="sxs-lookup"><span data-stu-id="0212d-109">These values must be the same as those that are in the System Definition settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0212d-110">所有項目均區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0212d-110">All entries are case sensitive.</span></span>  
  
## <a name="set-the-transport-properties"></a><span data-ttu-id="0212d-111">設定傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="0212d-111">Set the transport properties</span></span>  
 <span data-ttu-id="0212d-112">在**傳輸屬性**對話方塊中，設定伺服器系統和您嘗試存取的物件特有的連接和認證參數。</span><span class="sxs-lookup"><span data-stu-id="0212d-112">In the **Transport Properties** dialog box, you set the connection and credential parameters that are specific to the server system and the objects you are trying to access.</span></span>  
  
1.  <span data-ttu-id="0212d-113">提供認證。</span><span class="sxs-lookup"><span data-stu-id="0212d-113">Provide credentials.</span></span>  
  
     <span data-ttu-id="0212d-114">您可以使用下列其中一種方法來存取 JD Edwards OneWorld 系統：</span><span class="sxs-lookup"><span data-stu-id="0212d-114">You can access the JD Edwards OneWorld system using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="0212d-115">登入認證 （密碼、 使用者名稱）： 如果您使用此方法時，請移至步驟 5。</span><span class="sxs-lookup"><span data-stu-id="0212d-115">Logon credentials (Password, User name): If you use this method, go to step 5.</span></span>  
  
    -   <span data-ttu-id="0212d-116">單一登入。</span><span class="sxs-lookup"><span data-stu-id="0212d-116">Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="0212d-117">若要使用單一登入 (SSO)，選取**是**中**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="0212d-117">To use Single Sign-On (SSO), select **Yes** in the **Use SSO**.</span></span>  
  
     <span data-ttu-id="0212d-118">如需如何設定 SSO 的詳細資訊，請參閱[配接器中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)</span><span class="sxs-lookup"><span data-stu-id="0212d-118">For more information about how to set up SSO, see [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)</span></span>  
  
3.  <span data-ttu-id="0212d-119">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="0212d-119">Select an affiliate application in the list.</span></span>  
  
     <span data-ttu-id="0212d-120">企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 JD Edwards OneWorld)。</span><span class="sxs-lookup"><span data-stu-id="0212d-120">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as JD Edwards OneWorld.</span></span> <span data-ttu-id="0212d-121">Microsoft BizTalk Adapter for JD Edwards OneWorld 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="0212d-121">Microsoft BizTalk Adapter for JD Edwards OneWorld uses the credentials of an application user.</span></span> <span data-ttu-id="0212d-122">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 認證資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="0212d-122">These credentials are retrieved from the SSO Credentials database for the server system for a specified affiliate application.</span></span> <span data-ttu-id="0212d-123">這些認證就是啟動 BizTalk Server 專案之應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="0212d-123">The credentials are those of the application user who launched the BizTalk Server project.</span></span>  
  
     <span data-ttu-id="0212d-124">如需詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications3.md)。</span><span class="sxs-lookup"><span data-stu-id="0212d-124">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).</span></span>  
  
4.  <span data-ttu-id="0212d-125">展開**JD Edwards OneWorld 系統**節點，然後輸入連線的所有必要的資訊至 JD Edwards OneWorld 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0212d-125">Expand the **JD Edwards OneWorld system** node and enter all required information for connection to the JD Edwards OneWorld server.</span></span>  
  
     ![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")  
  
     <span data-ttu-id="0212d-126">在設定連線參數後，您可以瀏覽 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="0212d-126">After you set the connection parameters, you can browse a JD Edwards OneWorld system.</span></span> <span data-ttu-id="0212d-127">如需詳細資訊，請參閱[匯入 JD Edwards OneWorld 結構描述至 BizTalk Server 專案](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="0212d-127">For more information, see [Importing JD Edwards OneWorld Schemas into BizTalk Server Projects](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md).</span></span>  
  
5.  <span data-ttu-id="0212d-128">輸入值，在代表的呼叫，例如 200，**同時呼叫數目上限**如有必要。</span><span class="sxs-lookup"><span data-stu-id="0212d-128">Enter a value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.</span></span>  
  
     <span data-ttu-id="0212d-129">`Max Concurrent Calls`參數可讓您最佳化組態。</span><span class="sxs-lookup"><span data-stu-id="0212d-129">The `Max Concurrent Calls` parameter lets you optimize your configuration.</span></span> <span data-ttu-id="0212d-130">在輸送量超過後端處理能力時，可以使用這個參數來啟動訊息多載保護。</span><span class="sxs-lookup"><span data-stu-id="0212d-130">You use this parameter in instances where the throughput exceeds back-end processing capabilities, to activate message-overload protection.</span></span> <span data-ttu-id="0212d-131">預設值為 -1，表示呼叫沒有上限。</span><span class="sxs-lookup"><span data-stu-id="0212d-131">The default is -1, which means that the calls are unlimited.</span></span>  
  
     <span data-ttu-id="0212d-132">當 BizTalk Server 將訊息提交到傳輸配接器時，會先收到來自配接器的批次。</span><span class="sxs-lookup"><span data-stu-id="0212d-132">When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter.</span></span> <span data-ttu-id="0212d-133">它會在批次上叫用 `TransmitMessage` 以傳輸每個訊息。</span><span class="sxs-lookup"><span data-stu-id="0212d-133">It invokes `TransmitMessage` on the batch to transmit each message.</span></span> <span data-ttu-id="0212d-134">完成傳輸時，BizTalk Server 會在批次上叫用 `Done`，這時配接器就會開始將訊息傳輸至後端。</span><span class="sxs-lookup"><span data-stu-id="0212d-134">When done, BizTalk Server invokes `Done` on the batch, and the adapter starts transmitting the messages to the back-end.</span></span> <span data-ttu-id="0212d-135">如果 BizTalk Server 在叫用 `Done` 之前取得多個批次，可能永遠不會叫用。</span><span class="sxs-lookup"><span data-stu-id="0212d-135">If BizTalk Server obtains multiple batches before invoking `Done`, it might never occur.</span></span> <span data-ttu-id="0212d-136">藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。</span><span class="sxs-lookup"><span data-stu-id="0212d-136">By setting the maximum number of messages in a batch, you can control messages to the back-end.</span></span>  
  
     <span data-ttu-id="0212d-137">此參數的變更會在 1 分鐘內生效；BizTalk Server 必須擷取儲存在 SQL 資料庫中的配接器組態變更。</span><span class="sxs-lookup"><span data-stu-id="0212d-137">Changing this parameter takes effect within one minute; BizTalk Server must retrieve the changes to the adapter configuration saved in the SQL database.</span></span>  
  
6.  <span data-ttu-id="0212d-138">選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="0212d-138">Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.</span></span>  
  
     <span data-ttu-id="0212d-139">例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。</span><span class="sxs-lookup"><span data-stu-id="0212d-139">For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0212d-140">這個 browsingagent.exe 要等到您結束目前的瀏覽工作階段才會重新整理。</span><span class="sxs-lookup"><span data-stu-id="0212d-140">The browsingagent.exe does not refresh until you exit the current browsing session.</span></span> <span data-ttu-id="0212d-141">例如，您必須先結束**新增產生的項目**瀏覽工作階段，並重新進入，才能更新 browsingagent.exe。</span><span class="sxs-lookup"><span data-stu-id="0212d-141">For example, you must exit the **Add generated item** browsing session and reenter to update the browsingagent.exe.</span></span>  
  
7.  <span data-ttu-id="0212d-142">提供之後所有必要的資訊，請按一下**套用**，然後按一下 **確定**以採用連線資訊。</span><span class="sxs-lookup"><span data-stu-id="0212d-142">After providing all required information, click **Apply**, and then click **OK** to accept the connection information.</span></span>  
  
     <span data-ttu-id="0212d-143">您必須為 BizTalk Adapter for JD Edwards OneWorld 設定連線參數，才能存取 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="0212d-143">You must set connection parameters for BizTalk Adapter for JD Edwards OneWorld to access JD Edwards OneWorld.</span></span>  
  
## <a name="adapter-required-properties"></a><span data-ttu-id="0212d-144">配接器必要屬性</span><span class="sxs-lookup"><span data-stu-id="0212d-144">Adapter required properties</span></span>  
 <span data-ttu-id="0212d-145">如果沒有在 [控制台] 中設定全域環境變數，您可以在此區段中設定。</span><span class="sxs-lookup"><span data-stu-id="0212d-145">If you did not set global environment variables in Control Panel, you can do so in this section.</span></span>  
  
|<span data-ttu-id="0212d-146">參數</span><span class="sxs-lookup"><span data-stu-id="0212d-146">Parameter</span></span>|<span data-ttu-id="0212d-147">Description</span><span class="sxs-lookup"><span data-stu-id="0212d-147">Description</span></span>|  
|---------------|-----------------|  
|`Host`|<span data-ttu-id="0212d-148">輸入主控件伺服器電腦名稱的名稱 (例如， `actsvr1`); 或電腦的 IP 位址 (例如， `123.456.0.789`)。</span><span class="sxs-lookup"><span data-stu-id="0212d-148">Type the name of the host server computer name (for example, `actsvr1`); or the IP address of the computer (for example, `123.456.0.789`).</span></span>|  
|<span data-ttu-id="0212d-149">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="0212d-149">JAVA_HOME</span></span>|<span data-ttu-id="0212d-150">輸入 JDK 安裝的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="0212d-150">Type the complete path of your JDK installation.</span></span>|  
|<span data-ttu-id="0212d-151">JDE Edwards 環境</span><span class="sxs-lookup"><span data-stu-id="0212d-151">JDE Edwards Environment</span></span>|<span data-ttu-id="0212d-152">在 JD Edwards OneWorld 中，輸入環境的名稱，例如`DV7333`。</span><span class="sxs-lookup"><span data-stu-id="0212d-152">Type the name of an environment in JD Edwards OneWorld, for example, `DV7333`.</span></span><br /><br /> <span data-ttu-id="0212d-153">DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="0212d-153">DV7333 is a common name for the development environment, PY7333 is common for the prototype environment, and PD7333 is common for the production environment.</span></span>|  
|<span data-ttu-id="0212d-154">JDEdwards JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="0212d-154">JDEdwards JAR Files</span></span>|<span data-ttu-id="0212d-155">輸入每個 JAR 檔案的完整路徑與檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="0212d-155">Enter the complete path and file name for each JAR file:</span></span><br /><br /> <span data-ttu-id="0212d-156">-Connector.jar</span><span class="sxs-lookup"><span data-stu-id="0212d-156">-   Connector.jar</span></span><br /><span data-ttu-id="0212d-157">-Kernel.jar</span><span class="sxs-lookup"><span data-stu-id="0212d-157">-   Kernel.jar</span></span><br /><span data-ttu-id="0212d-158">-JDEJAccess.jar</span><span class="sxs-lookup"><span data-stu-id="0212d-158">-   JDEJAccess.jar</span></span><br /><span data-ttu-id="0212d-159">-JDEActionalInterop.jar</span><span class="sxs-lookup"><span data-stu-id="0212d-159">-   JDEActionalInterop.jar</span></span><br /><br /> <span data-ttu-id="0212d-160">每個 JAR 檔案都必須以分號 (;) 分隔，且不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="0212d-160">Each jar file must be separated with a semi-colon (;) and no space.</span></span> <span data-ttu-id="0212d-161">例如：</span><span class="sxs-lookup"><span data-stu-id="0212d-161">For example:</span></span><br /><br /> `<drive>\Connector.jar;<drive>\Kernel.jar;`|  
|<span data-ttu-id="0212d-162">密碼</span><span class="sxs-lookup"><span data-stu-id="0212d-162">Password</span></span>|<span data-ttu-id="0212d-163">輸入指定使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="0212d-163">Type the password of the specified user.</span></span>|  
|<span data-ttu-id="0212d-164">通訊埠</span><span class="sxs-lookup"><span data-stu-id="0212d-164">Port</span></span>|<span data-ttu-id="0212d-165">輸入會交換資料的連接埠號碼 (例如， `6009`)。</span><span class="sxs-lookup"><span data-stu-id="0212d-165">Type the port number that will exchange data (for example, `6009`).</span></span>|  
|<span data-ttu-id="0212d-166">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="0212d-166">User Name</span></span>|<span data-ttu-id="0212d-167">輸入將用來登入 JD Edwards OneWorld 系統的 JD Edwards OneWorld 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0212d-167">Type a JD Edwards OneWorld user name that will be used to log on to the JD Edwards OneWorld system.</span></span>|  
  
