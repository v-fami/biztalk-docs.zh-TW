---
title: 交易式配接器 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31a13377-cc89-4763-ad1b-508a16fc9708
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f934857103952a035159cc08678c8ce8c8e51a56
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "26009887"
---
# <a name="transactional-adapter-biztalk-server-sample"></a><span data-ttu-id="2b834-102">交易式配接器 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="2b834-102">Transactional Adapter (BizTalk Server Sample)</span></span>
<span data-ttu-id="2b834-103">交易式配接器範例示範如何建立和使用在處理期間針對資料庫明確 Microsoft 分散式交易協調器 (MSDTC) 交易[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息。</span><span class="sxs-lookup"><span data-stu-id="2b834-103">The Transactional Adapter sample demonstrates how to create and use an explicit Microsoft Distributed Transaction Coordinator (MSDTC) transaction against a database during processing of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="2b834-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="2b834-104">What This Sample Does</span></span>  
 <span data-ttu-id="2b834-105">此範例包含接收配接器，會依使用者指定的間隔執行 SQL 陳述式，以便從使用 MSDTC 交易的 SQL Server 資料庫取得資料。</span><span class="sxs-lookup"><span data-stu-id="2b834-105">This sample contains a receive adapter which runs a SQL statement at a user-specified interval to obtain data from a SQL Server database using an MSDTC transaction.</span></span> <span data-ttu-id="2b834-106">資料然後提交給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相同交易的內容下，以訊息形式的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b834-106">The data is then submitted to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database in the form of a message under the context of the same transaction.</span></span>  
  
 <span data-ttu-id="2b834-107">對應的傳送配接器會使用交易環境中的 BizTalk 訊息的輸入，以執行使用者指定的 SQL 預存程序。</span><span class="sxs-lookup"><span data-stu-id="2b834-107">The corresponding send adapter runs a user-specified SQL stored procedure using input from a BizTalk message in the context of a transaction.</span></span> <span data-ttu-id="2b834-108">它使用該訊息中的特定資料，透過上述相同交易從 MessageBox 資料庫中尋找和刪除對應訊息。</span><span class="sxs-lookup"><span data-stu-id="2b834-108">It uses specific data from that message to locate and delete the corresponding message from the Message Box database under that same transaction.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="2b834-109">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="2b834-109">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="2b834-110">這個範例在其解決方案中有兩個專案。</span><span class="sxs-lookup"><span data-stu-id="2b834-110">This sample has two projects in its solution.</span></span> <span data-ttu-id="2b834-111">第一個是管理專案 (Admin)，可在執行階段前用來讓使用者設定使用此配接器的接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="2b834-111">The first is the administrative project (Admin) which is used prior to runtime to allow a user to configure the receive locations and send ports that use this adapter.</span></span> <span data-ttu-id="2b834-112">第二個是執行階段專案 (Runtime)，可在傳送配接器及接收配接器正在執行時執行。</span><span class="sxs-lookup"><span data-stu-id="2b834-112">The second is the runtime project (Runtime) that runs when the send and receive adapters are executing.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="2b834-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="2b834-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="2b834-114">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="2b834-114">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="2b834-115">\<*範例路徑*\>\Samples\AdaptersDevelopment\TransactionalAdapter。</span><span class="sxs-lookup"><span data-stu-id="2b834-115">\<*Samples Path*\>\Samples\AdaptersDevelopment\TransactionalAdapter.</span></span> <span data-ttu-id="2b834-116">管理組態專案位於 \Admin 資料夾，而執行階段專案則存在於 \Runtime 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2b834-116">The administrative configuration project is located in the \Admin folder, while the runtime project exists in the \Runtime folder.</span></span>  
  
 <span data-ttu-id="2b834-117">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="2b834-117">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="2b834-118">Admin 專案檔案名稱</span><span class="sxs-lookup"><span data-stu-id="2b834-118">Admin Project Filename</span></span>|<span data-ttu-id="2b834-119">Admin 專案檔案描述</span><span class="sxs-lookup"><span data-stu-id="2b834-119">Admin Project File Description</span></span>|  
|----------------------------|------------------------------------|  
|<span data-ttu-id="2b834-120">TransactionalAdmin.csproj</span><span class="sxs-lookup"><span data-stu-id="2b834-120">TransactionalAdmin.csproj</span></span>|<span data-ttu-id="2b834-121">用於執行階段前組態的配接器管理專案檔案</span><span class="sxs-lookup"><span data-stu-id="2b834-121">Adapter administrative project file used for pre-runtime configuration</span></span>|  
|<span data-ttu-id="2b834-122">TransactionalReceiveHandler.xsd</span><span class="sxs-lookup"><span data-stu-id="2b834-122">TransactionalReceiveHandler.xsd</span></span>|<span data-ttu-id="2b834-123">接收處理常式屬性的 XSD</span><span class="sxs-lookup"><span data-stu-id="2b834-123">XSD for receive handler properties</span></span>|  
|<span data-ttu-id="2b834-124">TransactionalReceiveLocation.xsd</span><span class="sxs-lookup"><span data-stu-id="2b834-124">TransactionalReceiveLocation.xsd</span></span>|<span data-ttu-id="2b834-125">接收位置屬性的 XSD</span><span class="sxs-lookup"><span data-stu-id="2b834-125">XSD for receive location properties</span></span>|  
|<span data-ttu-id="2b834-126">TransactionalTransmitLocation.xsd</span><span class="sxs-lookup"><span data-stu-id="2b834-126">TransactionalTransmitLocation.xsd</span></span>|<span data-ttu-id="2b834-127">傳輸位置屬性的 XSD</span><span class="sxs-lookup"><span data-stu-id="2b834-127">XSD for transmit location properties</span></span>|  
|<span data-ttu-id="2b834-128">TransactionalTransmitHandler.xsd</span><span class="sxs-lookup"><span data-stu-id="2b834-128">TransactionalTransmitHandler.xsd</span></span>|<span data-ttu-id="2b834-129">傳輸處理常式屬性的 XSD</span><span class="sxs-lookup"><span data-stu-id="2b834-129">XSD for transmit handler properties</span></span>|  
|<span data-ttu-id="2b834-130">TransactionalAdapterManagement.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-130">TransactionalAdapterManagement.cs</span></span>|<span data-ttu-id="2b834-131">配接器組態管理。</span><span class="sxs-lookup"><span data-stu-id="2b834-131">Adapter configuration management.</span></span> <span data-ttu-id="2b834-132">包含 GetConfigSchema，這是由 BizTalk 配接器架構所叫用，以傳回它支援的每一個組態類型 (共四個可能類型) 的 XSD 組態結構描述。</span><span class="sxs-lookup"><span data-stu-id="2b834-132">Contains GetConfigSchema which is invoked by the BizTalk Adapter Framework to return an XSD configuration schema for each of the (four) possible configuration types it supports.</span></span>|  
  
|<span data-ttu-id="2b834-133">執行階段專案檔案名稱</span><span class="sxs-lookup"><span data-stu-id="2b834-133">Runtime Project Filename</span></span>|<span data-ttu-id="2b834-134">執行階段專案檔案描述</span><span class="sxs-lookup"><span data-stu-id="2b834-134">Runtime Project File Description</span></span>|  
|------------------------------|--------------------------------------|  
|<span data-ttu-id="2b834-135">Transactional.csproj</span><span class="sxs-lookup"><span data-stu-id="2b834-135">Transactional.csproj</span></span>|<span data-ttu-id="2b834-136">配接器執行階段專案檔案</span><span class="sxs-lookup"><span data-stu-id="2b834-136">Adapter runtime project file</span></span>|  
|<span data-ttu-id="2b834-137">TransactionalAsyncBatch.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-137">TransactionalAsyncBatch.cs</span></span>|<span data-ttu-id="2b834-138">配接器傳送組件的非同步實作</span><span class="sxs-lookup"><span data-stu-id="2b834-138">Asynchronous implementation of the send part of the adapter</span></span>|  
|<span data-ttu-id="2b834-139">TransactionalDeleteBatch.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-139">TransactionalDeleteBatch.cs</span></span>|<span data-ttu-id="2b834-140">刪除訊息及表決批次以認可或中止交易</span><span class="sxs-lookup"><span data-stu-id="2b834-140">Deletes a batch of messages and votes to commit or abort a transaction</span></span>|  
|<span data-ttu-id="2b834-141">TransactionalProperties.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-141">TransactionalProperties.cs</span></span>|<span data-ttu-id="2b834-142">擷取和設定組態屬性</span><span class="sxs-lookup"><span data-stu-id="2b834-142">Extracts and sets configuration properties</span></span>|  
|<span data-ttu-id="2b834-143">TransactionalReceiver.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-143">TransactionalReceiver.cs</span></span>|<span data-ttu-id="2b834-144">建立和管理接收結束點</span><span class="sxs-lookup"><span data-stu-id="2b834-144">Creates and manages receive endpoints</span></span>|  
|<span data-ttu-id="2b834-145">TransactionalReceiverEndpoint.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-145">TransactionalReceiverEndpoint.cs</span></span>|<span data-ttu-id="2b834-146">每個接收位置的實際監聽或輪詢</span><span class="sxs-lookup"><span data-stu-id="2b834-146">Actual listening or polling for each receive location</span></span>|  
|<span data-ttu-id="2b834-147">TransactionalTransmitter.cs</span><span class="sxs-lookup"><span data-stu-id="2b834-147">TransactionalTransmitter.cs</span></span>|<span data-ttu-id="2b834-148">從傳訊引擎接受要被傳送的訊息批次</span><span class="sxs-lookup"><span data-stu-id="2b834-148">Accepts a batch of messages from the Messaging Engine to be transmitted</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="2b834-149">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="2b834-149">How to Use This Sample</span></span>  
 <span data-ttu-id="2b834-150">這個範例主要提供可用來做為使用明確交易建立自訂傳送配接器及接收配接器的架構。</span><span class="sxs-lookup"><span data-stu-id="2b834-150">This sample is meant as a framework for you to use in creating custom send and receive adapters using explicit transactions.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="2b834-151">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="2b834-151">Building and Initializing This Sample</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b834-152">如果 BizTalk 安裝是 64 位元，或安裝位置已有修改，則需要隨之變更 OutboundAssemblyPath、InboundAssemblyPath、AdapterMgmtAssemblyPath。</span><span class="sxs-lookup"><span data-stu-id="2b834-152">If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.</span></span>  
  
#### <a name="create-a-strong-name-key-for-the-transactional-adapter-sample"></a><span data-ttu-id="2b834-153">建立交易式配接器範例的強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="2b834-153">Create a Strong Name Key for the Transactional Adapter sample</span></span>  
  
1.  <span data-ttu-id="2b834-154">啟動 **Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="2b834-154">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="2b834-155">在命令提示字元輸入下列命令，然後按下 ENTER：</span><span class="sxs-lookup"><span data-stu-id="2b834-155">At the command prompt, type the following and then press enter:</span></span>  
  
    ```  
    cd \Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Runtime  
    ```  
  
3.  <span data-ttu-id="2b834-156">在命令提示字元輸入下列命令，然後按下 ENTER：</span><span class="sxs-lookup"><span data-stu-id="2b834-156">At the command prompt, type the following and then press enter:</span></span>  
  
    ```  
    sn –k TransactionalAdapter.snk  
    ```  
  
4.  <span data-ttu-id="2b834-157">在命令提示字元中，輸入 **結束**, ，然後按 enter 鍵關閉命令提示字元 視窗。</span><span class="sxs-lookup"><span data-stu-id="2b834-157">At the command prompt, type **exit**, and then press enter to close the command prompt window.</span></span>  
  
#### <a name="build-the-transactional-adapter-solution"></a><span data-ttu-id="2b834-158">建立交易式配接器解決方案</span><span class="sxs-lookup"><span data-stu-id="2b834-158">Build the Transactional Adapter Solution</span></span>  
  
1.  <span data-ttu-id="2b834-159">按一下  **啟動**, ，指向  **所有程式**, ，指向 **附屬應用程式**, ，然後按一下  **Windows 檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="2b834-159">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="2b834-160">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter，然後按兩下**TransactionalAdapter.sln**來開啟這個解決方案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b834-160">Browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter, and double-click **TransactionalAdapter.sln** to open this solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="2b834-161">若要建置這兩個方案總管] 中的交易式配接器專案 （Admin 和 Runtime），以滑鼠右鍵按一下 **解決方案 TransactionalAdapter**, ，然後按一下 [ **重建**。</span><span class="sxs-lookup"><span data-stu-id="2b834-161">To build both of the Transactional Adapter projects (Admin and Runtime) in Solution Explorer, right-click **Solution TransactionalAdapter**, and then click **Rebuild**.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="2b834-162">執行此範例</span><span class="sxs-lookup"><span data-stu-id="2b834-162">Running This Sample</span></span>  
  
#### <a name="register-the-transactional-adapter"></a><span data-ttu-id="2b834-163">註冊交易式配接器</span><span class="sxs-lookup"><span data-stu-id="2b834-163">Register the Transactional Adapter</span></span>  
  
1.  <span data-ttu-id="2b834-164">在 [Windows 檔案總管] 中，瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin。</span><span class="sxs-lookup"><span data-stu-id="2b834-164">In Windows Explorer, navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin.</span></span>  
  
2.  <span data-ttu-id="2b834-165">若要將交易式配接器的資料加入至登錄中，按兩下 **TransactionalAdmin.reg**。</span><span class="sxs-lookup"><span data-stu-id="2b834-165">To add the transactional adapter data to the registry, double-click **TransactionalAdmin.reg**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2b834-166">**TransactionalAdmin.reg**包含硬式編碼路徑 C:\Program Files\Microsoft BizTalk Server\\。</span><span class="sxs-lookup"><span data-stu-id="2b834-166">**TransactionalAdmin.reg** includes hard-coded paths to C:\Program Files\Microsoft BizTalk Server\\.</span></span> <span data-ttu-id="2b834-167">如果您未將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在預設位置中，或者已從舊版升級 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝，則必須以適當的路徑來修改 TransactionalAdmin.reg 檔案。</span><span class="sxs-lookup"><span data-stu-id="2b834-167">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the default location or if you upgraded your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from a previous version, you must modify the file TransactionalAdmin.reg with the appropriate paths.</span></span> <span data-ttu-id="2b834-168">更新與 "InboundAssemblyPath"、"OutboundAssemblyPath" 和 "AdapterMgmtAssemblyPath" 值相關聯的路徑，以指向指定檔案的正確位置。</span><span class="sxs-lookup"><span data-stu-id="2b834-168">Update the paths associated with the "InboundAssemblyPath", "OutboundAssemblyPath", and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2b834-169">如果您在 64 位元電腦上安裝 BizTalk，變更所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體都變更為 HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ 中 **TransactionalAdmin.reg** 登錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b834-169">If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **TransactionalAdmin.reg** registry file.</span></span>  
  
3.  <span data-ttu-id="2b834-170">在 **登錄編輯程式** 對話方塊中，按一下  **是** 以將範例配接器新增至登錄，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b834-170">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="2b834-171">若要關閉 Windows 檔案總管中，按一下 **檔案**, ，然後按一下  **關閉**。</span><span class="sxs-lookup"><span data-stu-id="2b834-171">To close Windows Explorer, click **File**, and then click **Close**.</span></span>  
  
#### <a name="add-the-transactional-adapter-to-biztalk-server"></a><span data-ttu-id="2b834-172">將交易式配接器加入至 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2b834-172">Add the Transactional Adapter to BizTalk Server</span></span>  
  
1.  <span data-ttu-id="2b834-173">按一下**啟動**功能表上，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="2b834-173">Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2b834-174">在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk Server 管理**樹狀目錄中，展開  **BizTalk 群組**樹狀結構、，然後展開 **平台設定**樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="2b834-174">In the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **BizTalk Server Administration** tree, expand the **BizTalk Group** tree, and then expand the **Platform Settings**  tree.</span></span>  
  
3.  <span data-ttu-id="2b834-175">以滑鼠右鍵按一下 **配接器**, ，按一下  **新增**, ，然後按一下  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="2b834-175">Right-click **Adapters**, click **New**, and then click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="2b834-176">在 **配接器屬性** 對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="2b834-176">In the **Adapter Properties** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="2b834-177">使用</span><span class="sxs-lookup"><span data-stu-id="2b834-177">Use this</span></span>|<span data-ttu-id="2b834-178">動作</span><span class="sxs-lookup"><span data-stu-id="2b834-178">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2b834-179">名稱</span><span class="sxs-lookup"><span data-stu-id="2b834-179">Name</span></span>|<span data-ttu-id="2b834-180">型別 **TransactionalAdapter**。</span><span class="sxs-lookup"><span data-stu-id="2b834-180">Type **TransactionalAdapter**.</span></span>|  
    |<span data-ttu-id="2b834-181">配接器</span><span class="sxs-lookup"><span data-stu-id="2b834-181">Adapter</span></span>|<span data-ttu-id="2b834-182">選取 **Txn** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="2b834-182">Select **Txn** from the drop-down list.</span></span> <span data-ttu-id="2b834-183">執行此項目出現 **TransactionalAdmin.reg** 先前檔案。</span><span class="sxs-lookup"><span data-stu-id="2b834-183">This entry appears as a result of running the **TransactionalAdmin.reg** file previously.</span></span>|  
    |<span data-ttu-id="2b834-184">Description</span><span class="sxs-lookup"><span data-stu-id="2b834-184">Description</span></span>|<span data-ttu-id="2b834-185">型別 **範例交易式配接器**。</span><span class="sxs-lookup"><span data-stu-id="2b834-185">Type **Sample Transactional Adapter**.</span></span>|  
  
5.  <span data-ttu-id="2b834-186">按一下 **[確定].**</span><span class="sxs-lookup"><span data-stu-id="2b834-186">Click **OK.**</span></span> <span data-ttu-id="2b834-187">配接器隨即會出現在 BizTalk 管理主控台右側視窗的配接器清單中。</span><span class="sxs-lookup"><span data-stu-id="2b834-187">The adapter now appears in the list of adapters in the right window of the BizTalk Administration console.</span></span>  
  
#### <a name="create-a-receive-port-and-location-that-uses-the-adapter"></a><span data-ttu-id="2b834-188">建立使用配接器的接收埠和接收位置</span><span class="sxs-lookup"><span data-stu-id="2b834-188">Create a Receive Port and Location that uses the Adapter</span></span>  
  
1.  <span data-ttu-id="2b834-189">展開**BizTalk 群組 [伺服器名稱]** 節點[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**應用程式**] 節點，展開 [ **BizTalk Application 1**節點。</span><span class="sxs-lookup"><span data-stu-id="2b834-189">Expand the **BizTalk Group[server name]** node in [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **Applications** node, expand **BizTalk Application 1** node.</span></span>  
  
2.  <span data-ttu-id="2b834-190">以滑鼠右鍵按一下 **接收埠**, ，然後按一下  **新增**, ，請選取 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="2b834-190">Right-click **Receive Ports**, and then click **New**, select **One-Way Receive Port.**</span></span>  
  
3.  <span data-ttu-id="2b834-191">如 **名稱**, ，輸入 **TxnReceivePort1**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b834-191">For **Name**, enter **TxnReceivePort1**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="2b834-192">以滑鼠右鍵按一下 **接收位置** 節點中，按一下  **新增**, ，然後選取 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="2b834-192">Right-click the **Receive Locations** node, click **New**, and then select **One-Way Receive Location**.</span></span>  
  
5.  <span data-ttu-id="2b834-193">在**選取接收埠** 對話方塊中，選取 **TxnReceivePort1**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b834-193">In the**Select a Receive Port** dialog box, select **TxnReceivePort1**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="2b834-194">在 **接收位置屬性** 對話方塊的  **一般** 索引標籤上，輸入 **TxnReceiveLocation1** 的 **名稱**。</span><span class="sxs-lookup"><span data-stu-id="2b834-194">In the **Receive Location Properties** dialog box, under the **General** tab, enter **TxnReceiveLocation1** for **Name**.</span></span> <span data-ttu-id="2b834-195">請確定 **接收埠** 標籤顯示 **TxnReceivePort1**。</span><span class="sxs-lookup"><span data-stu-id="2b834-195">Ensure the **Receive Port** label displays **TxnReceivePort1**.</span></span>  
  
7.  <span data-ttu-id="2b834-196">在**類型** 下拉式清單方塊中 **傳輸** 框架中，選取 **TransactionalAdapter。**</span><span class="sxs-lookup"><span data-stu-id="2b834-196">In the**Type** dropdown list box, in the **Transport** frame, select **TransactionalAdapter.**</span></span>  
  
8.  <span data-ttu-id="2b834-197">在 **接收 \* \* \* 管線** 方塊中，確認 **PassThruReceive** 已選取。</span><span class="sxs-lookup"><span data-stu-id="2b834-197">In the **Receive****Pipeline** box, ensure **PassThruReceive** is selected.</span></span> <span data-ttu-id="2b834-198">剩下的屬性則保留其預設設定。</span><span class="sxs-lookup"><span data-stu-id="2b834-198">Leave the rest of the properties with their default settings.</span></span>  
  
9. <span data-ttu-id="2b834-199">按一下  **設定** 旁 **類型** 下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="2b834-199">Click the **Configure** button next to the **Type** drop down box.</span></span> <span data-ttu-id="2b834-200">這樣會顯示這個配接器專用的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2b834-200">This displays a dialog specific to this adapter.</span></span> <span data-ttu-id="2b834-201">指定下列各項視情況需要，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b834-201">Specify the following as you see appropriate, then click **OK**.</span></span>  
  
    |<span data-ttu-id="2b834-202">屬性</span><span class="sxs-lookup"><span data-stu-id="2b834-202">Property</span></span>|<span data-ttu-id="2b834-203">設定</span><span class="sxs-lookup"><span data-stu-id="2b834-203">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="2b834-204">連接字串</span><span class="sxs-lookup"><span data-stu-id="2b834-204">Connection String</span></span>|<span data-ttu-id="2b834-205">用來連接和驗證 Northwind 資料庫的 SQL 資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="2b834-205">The SQL database connection string used to connect and authenticate with the Northwind database.</span></span> <span data-ttu-id="2b834-206">我們稍後會執行使用這個資料庫的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="2b834-206">We will later run a SQL script that will use this database.</span></span>|  
    |<span data-ttu-id="2b834-207">命令文字</span><span class="sxs-lookup"><span data-stu-id="2b834-207">Command Text</span></span>|<span data-ttu-id="2b834-208">對 Northwind 資料庫所執行的 SQL 陳述式，用意在取得資料以置入 BizTalk 訊息中。</span><span class="sxs-lookup"><span data-stu-id="2b834-208">The SQL statements that are executed against the Northwind database to obtain data to put into a BizTalk Message.</span></span>|  
    |<span data-ttu-id="2b834-209">Cookie</span><span class="sxs-lookup"><span data-stu-id="2b834-209">Cookie</span></span>|<span data-ttu-id="2b834-210">包含 URI 的一部分，因此輸入唯一的值，例如接收位置的名稱，例如︰ TxnReceiveLocation1。</span><span class="sxs-lookup"><span data-stu-id="2b834-210">Comprises part of the URI so enter a unique value, such as the name of the receive location, for instance: TxnReceiveLocation1.</span></span>|  
    |<span data-ttu-id="2b834-211">輪詢間隔單位</span><span class="sxs-lookup"><span data-stu-id="2b834-211">Polling Interval Unit</span></span>|<span data-ttu-id="2b834-212">資料輪詢的時間量值單位數。</span><span class="sxs-lookup"><span data-stu-id="2b834-212">The number of units of time measure for the polling of the data.</span></span> <span data-ttu-id="2b834-213">設定為秒數。</span><span class="sxs-lookup"><span data-stu-id="2b834-213">Set this to seconds.</span></span>|  
    |<span data-ttu-id="2b834-214">輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="2b834-214">Polling Interval</span></span>|<span data-ttu-id="2b834-215">資料輪詢的時間量值單位。</span><span class="sxs-lookup"><span data-stu-id="2b834-215">The unit of time measure for the polling of the data.</span></span> <span data-ttu-id="2b834-216">設定為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="2b834-216">Set this to 15 seconds.</span></span>|  
  
10. <span data-ttu-id="2b834-217">按一下 **[確定]** 關閉 [設定] 對話方塊中，然後**確定**] 以關閉 [**接收位置屬性**對話方塊，即可返回[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b834-217">Click **OK** to close the Configure dialog box, then **OK** again to close the **Receive Location Properties** dialog box to return to the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
#### <a name="create-a-send-port-and-send-handler-that-use-the-adapter"></a><span data-ttu-id="2b834-218">建立使用配接器的傳送埠和傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="2b834-218">Create a Send Port and Send Handler that use the Adapter</span></span>  
  
1.  <span data-ttu-id="2b834-219">使用 **BizTalk Application 1** 節點保持展開，以滑鼠右鍵按一下 **傳送埠**, ，然後按一下  **新增**, ，然後選取 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="2b834-219">With the **BizTalk Application 1** node still expanded, right-click **Send Ports**, and then click **New**, and select **Static One-Way Send Port**.</span></span>  
  
2.  <span data-ttu-id="2b834-220">在 **名稱** 欄位中，輸入 **TxnSendPort1**。</span><span class="sxs-lookup"><span data-stu-id="2b834-220">In the **Name** field, enter **TxnSendPort1**.</span></span>  
  
3.  <span data-ttu-id="2b834-221">在 **傳輸** 框架 **類型** 下拉式清單中，選取**TransactionalAdapter**`.`</span><span class="sxs-lookup"><span data-stu-id="2b834-221">In the **Transport** frame, in the **Type** drop-down list, select**TransactionalAdapter**`.`</span></span>  
  
4.  <span data-ttu-id="2b834-222">在 **傳送管線** 方塊中，確認 **PassThruTransmit** 已選取。</span><span class="sxs-lookup"><span data-stu-id="2b834-222">In the **Send Pipeline** box, ensure **PassThruTransmit** is selected.</span></span>  
  
5.  <span data-ttu-id="2b834-223">按一下  **設定** 旁 **傳輸** 下拉式清單。在出現的對話方塊中指定下列視情況需要，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b834-223">Click the **Configure** button next to the **transport** drop-down list.In the dialog that appears specify the following as you see appropriate, then click **OK**.</span></span>  
  
    |<span data-ttu-id="2b834-224">屬性</span><span class="sxs-lookup"><span data-stu-id="2b834-224">Property</span></span>|<span data-ttu-id="2b834-225">設定</span><span class="sxs-lookup"><span data-stu-id="2b834-225">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="2b834-226">Cookie</span><span class="sxs-lookup"><span data-stu-id="2b834-226">Cookie</span></span>|<span data-ttu-id="2b834-227">包含組件的 URI-輸入唯一的值，例如接收位置的名稱，例如︰ **TxnSendPort1**。</span><span class="sxs-lookup"><span data-stu-id="2b834-227">Comprises part of the URI - Enter a unique value here such as the name of the receive location, for instance: **TxnSendPort1**.</span></span>|  
    |<span data-ttu-id="2b834-228">連接字串</span><span class="sxs-lookup"><span data-stu-id="2b834-228">Connection String</span></span>|<span data-ttu-id="2b834-229">用來連接和驗證 Northwind 資料庫的 SQL 資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="2b834-229">The SQL database connection string used to connect and authenticate with the Northwind database.</span></span> <span data-ttu-id="2b834-230">它很可能會用來設定相同 **TxnReceiveLocation1** 接收位置。</span><span class="sxs-lookup"><span data-stu-id="2b834-230">It will most likely be the same one used to configure the **TxnReceiveLocation1** receive location.</span></span>|  
    |<span data-ttu-id="2b834-231">預存程序</span><span class="sxs-lookup"><span data-stu-id="2b834-231">Stored Procedure</span></span>|<span data-ttu-id="2b834-232">預存程序名稱，執行以輪詢資料庫- **sp_txnProc**。</span><span class="sxs-lookup"><span data-stu-id="2b834-232">The stored procedure name that gets executed to poll the database - **sp_txnProc**.</span></span> <span data-ttu-id="2b834-233">BizTalk 訊息傳送至該主體做為字串參數呼叫預存程序@Data。</span><span class="sxs-lookup"><span data-stu-id="2b834-233">The body of the BizTalk message is given to that stored procedure as a string parameter called @Data.</span></span> <span data-ttu-id="2b834-234">例如，使用者會在此情況下稍後預存程序的名稱設定**sp_txnProc**。</span><span class="sxs-lookup"><span data-stu-id="2b834-234">For example, the user will in this case later configure the stored procedure with the name **sp_txnProc**.</span></span> <span data-ttu-id="2b834-235">配接器的執行階段會對資料庫執行相當於這個呼叫的命令。</span><span class="sxs-lookup"><span data-stu-id="2b834-235">The runtime of the adapter would execute the equivalent of this call to the database.</span></span><br /><br /> <span data-ttu-id="2b834-236">exec sp_txnProc @Data = 「 BizTalk 訊息的內容 」</span><span class="sxs-lookup"><span data-stu-id="2b834-236">exec sp_txnProc @Data = “the contents of the BizTalk message”</span></span>|  
  
6.  <span data-ttu-id="2b834-237">在左的導覽窗格中，按一下  **篩選**。</span><span class="sxs-lookup"><span data-stu-id="2b834-237">In the left navigation pane, click **Filter**.</span></span>  
  
7.  <span data-ttu-id="2b834-238">在篩選條件運算式編輯器中，輸入下列運算式設定訂閱，讓此傳送埠接收 TxnReceivePort1 接收埠收到的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="2b834-238">In the filter expression editor, enter the following expression to set up a subscription for this send port to receive any messages received by the TxnReceivePort1 receive port.</span></span>  
  
     <span data-ttu-id="2b834-239">輸入這些值︰**BTS。ReceivePortName = = TxnReceivePort1**</span><span class="sxs-lookup"><span data-stu-id="2b834-239">Enter these values:**BTS.ReceivePortName== TxnReceivePort1**</span></span>  
  
    1.  <span data-ttu-id="2b834-240">`(property)`  **BTS。ReceivePortName**</span><span class="sxs-lookup"><span data-stu-id="2b834-240">`(property)`  **BTS.ReceivePortName**</span></span>  
  
    2.  <span data-ttu-id="2b834-241">`(operator)`  **==**</span><span class="sxs-lookup"><span data-stu-id="2b834-241">`(operator)`  **==**</span></span>  
  
    3.  <span data-ttu-id="2b834-242">`(value)`  **TxnReceivePort1**</span><span class="sxs-lookup"><span data-stu-id="2b834-242">`(value)`  **TxnReceivePort1**</span></span>  
  
8.  <span data-ttu-id="2b834-243">配接器屬性的其餘部分使用的預設值，並選取 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b834-243">Use the default values for the remainder of the adapter properties and select **OK**.</span></span>  
  
## <a name="run-the-sample"></a><span data-ttu-id="2b834-244">執行範例</span><span class="sxs-lookup"><span data-stu-id="2b834-244">Run the sample</span></span>  
  
1.  <span data-ttu-id="2b834-245">按一下  **啟動**, ，指向  **所有程式**, ，指向  **Microsoft SQL Server 2008 R2**, ，請選取 **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="2b834-245">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, select **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="2b834-246">在 **連接到伺服器** 對話方塊方塊中，請確定 **伺服器類型** 設為 **Database Engine**, ，並輸入認證來驗證資料庫伺服器，然後選取 **連接**。</span><span class="sxs-lookup"><span data-stu-id="2b834-246">In the **Connect to Server** dialog box, make sure **Server Type** is set to **Database Engine**, and enter credentials to authenticate to the database server, then select **Connect**.</span></span>  
  
3.  <span data-ttu-id="2b834-247">選取 **新查詢** 工具列按鈕，再將下列內容貼入新的查詢視窗，將測試資料表、 測試資料和測試預存程序插入 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b834-247">Select the **New Query** toolbar button and paste the following into the new query window to insert a test table, test data, and a test stored procedure into the Northwind database.</span></span> <span data-ttu-id="2b834-248">選取 **Execute** 工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="2b834-248">Select the **Execute** toolbar button.</span></span>  
  
    ```  
    use [Northwind]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[scratch]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    drop table [dbo].[scratch]  
    GO  
    CREATE TABLE [dbo].[scratch] (  
         [id] [int] IDENTITY (1, 1) NOT NULL ,  
         [msg] [nvarchar] (4000) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    GRANT SELECT , UPDATE , INSERT ON [dbo].[scratch] TO [public]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_txnProc]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[sp_txnProc]  
    GO  
    CREATE PROCEDURE [dbo].[sp_txnProc] @Data nvarchar (4000)  
    AS   
    INSERT scratch ( msg ) values ( @Data )  
    GO  
    GRANT EXECUTE ON [dbo].[sp_txnProc] TO [public]  
    GO  
    ```  
  
4.  <span data-ttu-id="2b834-249">在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**傳送埠**節點中，選取**TxnSendPort1**傳送埠，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="2b834-249">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **Send Ports** node, select the **TxnSendPort1** send port, and select **Start**.</span></span>  
  
5.  <span data-ttu-id="2b834-250">在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**ReceiveLocations**節點中，選取 **[txnrecievelocation1]** 接收位置，然後再選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="2b834-250">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **ReceiveLocations** node, select the **TxnRecieveLocation1** receive location, and then select **Enable**.</span></span>  
  
6.  <span data-ttu-id="2b834-251">一旦啟用接收位置，它會自動輪詢資料庫，在指定的時間間隔的資料。</span><span class="sxs-lookup"><span data-stu-id="2b834-251">Once the receive location is enabled, it will automatically poll the database at the designated intervals for data.</span></span>  
  
## <a name="classes-or-methods-used-in-the-sample"></a><span data-ttu-id="2b834-252">類別或方法中使用範例</span><span class="sxs-lookup"><span data-stu-id="2b834-252">Classes or Methods Used in the sample</span></span>  
* <span data-ttu-id="2b834-253">IBTTransmitterBatch 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="2b834-253">IBTTransmitterBatch Interface (COM)</span></span>
  
* <span data-ttu-id="2b834-254">IBTTransportProxy 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="2b834-254">IBTTransportProxy Interface (COM)</span></span>

<span data-ttu-id="2b834-255">將描述這些方法[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b834-255">These methods are described [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="2b834-256">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b834-256">See Also</span></span>  
 <span data-ttu-id="2b834-257">[配接器範例-開發](../core/adapter-samples-development.md) </span><span class="sxs-lookup"><span data-stu-id="2b834-257">[Adapter Samples - Development](../core/adapter-samples-development.md) </span></span>  
 [<span data-ttu-id="2b834-258">註冊配接器</span><span class="sxs-lookup"><span data-stu-id="2b834-258">Registering an Adapter</span></span>](../core/registering-an-adapter.md)