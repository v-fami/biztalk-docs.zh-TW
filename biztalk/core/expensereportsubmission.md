---
title: ExpenseReportSubmission |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
ms.assetid: d0bacab3-7092-44b8-a1c6-6f574a2db8bd
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09cec8e16b8b145206a2cd6b2a30859e502ce8b3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967895"
---
# <a name="expensereportsubmission"></a><span data-ttu-id="c7d63-102">ExpenseReportSubmission</span><span class="sxs-lookup"><span data-stu-id="c7d63-102">ExpenseReportSubmission</span></span>
<span data-ttu-id="c7d63-103">ExpenseReportSubmission 範例說明如何透過如 Microsoft Excel 的多功能用戶端，將文件提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="c7d63-103">The ExpenseReportSubmission sample demonstrates how to submit a document to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration from a rich client such as Microsoft Excel.</span></span>  

 <span data-ttu-id="c7d63-104">多功能的用戶端可以讓您在用戶端上執行資料驗證和初步計算等動作。</span><span class="sxs-lookup"><span data-stu-id="c7d63-104">Rich clients enable you to perform a number of actions, such as data validation and preliminary calculations, on the client.</span></span> <span data-ttu-id="c7d63-105">這有助於降低與後端伺服器的互動，相當適合只有低頻寬連線的情形。</span><span class="sxs-lookup"><span data-stu-id="c7d63-105">This helps to minimize interactions with the back-end server, which can be useful when only low bandwidth connections are available.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="c7d63-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="c7d63-106">Prerequisites</span></span>  
 <span data-ttu-id="c7d63-107">您必須確定已設定和啟用您的開發環境來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c7d63-107">You must ensure that your development environment is configured and enabled to work with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services.</span></span> <span data-ttu-id="c7d63-108">如需詳細資訊，請參閱 <<c0> [ 啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d63-108">For more information, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="c7d63-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="c7d63-109">What This Sample Does</span></span>  
 <span data-ttu-id="c7d63-110">此範例說明如何使用下列步驟，直接從 Excel 將費用報表提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="c7d63-110">This sample shows how you can submit an expense report to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directly from Excel, using the following sequence of steps:</span></span>  

1. <span data-ttu-id="c7d63-111">使用者執行 Excel 試算表中提供的手動範例步驟。</span><span class="sxs-lookup"><span data-stu-id="c7d63-111">The user performs the manual sample steps provided in the Excel spreadsheet.</span></span>  

2. <span data-ttu-id="c7d63-112">試算表中的巨集程式碼會將試算表資料轉換成可延伸標記語言 (XML) 格式，並且使用 HTTP 連線將 XML 訊息提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7d63-112">Macro code in the spreadsheet converts the spreadsheet data to Extensible Markup Language (XML) format, and submits the XML message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using an HTTP connection.</span></span>  

3. <span data-ttu-id="c7d63-113">執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦會擷取 XML 費用報表訊息、使用提供的結構描述驗證它的格式，然後將它放置到不同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c7d63-113">The computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] retrieves the XML expense report message, validates its format using the provided schema, and then drops it into a different folder.</span></span>  

4. <span data-ttu-id="c7d63-114">在實際情況中 (這超出此範例的說明範圍)，其他如「企業資源規劃」(ERP) 系統的應用程式會擷取試算表檔案，並進行進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="c7d63-114">In practice, beyond the scope of this sample, another application such as an Enterprise Resource Planning (ERP) system would then retrieve the spreadsheet file for further processing.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="c7d63-115">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="c7d63-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="c7d63-116">\<*範例路徑*\>\AdaptersUsage\ExpenseReportSubmission\\</span><span class="sxs-lookup"><span data-stu-id="c7d63-116">\<*Samples Path*\>\AdaptersUsage\ExpenseReportSubmission\\</span></span>  

 <span data-ttu-id="c7d63-117">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="c7d63-117">The following table shows the files in this sample and describes their purpose.</span></span>  


|                                                            <span data-ttu-id="c7d63-118">檔案</span><span class="sxs-lookup"><span data-stu-id="c7d63-118">File(s)</span></span>                                                            |                                                                                           <span data-ttu-id="c7d63-119">描述</span><span class="sxs-lookup"><span data-stu-id="c7d63-119">Description</span></span>                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                          <span data-ttu-id="c7d63-120">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="c7d63-120">Cleanup.bat</span></span>                                                          | <span data-ttu-id="c7d63-121">從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="c7d63-121">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span> |
|                                                    <span data-ttu-id="c7d63-122">ExpenseReport.15.3.xls</span><span class="sxs-lookup"><span data-stu-id="c7d63-122">ExpenseReport.15.3.xls</span></span>                                                     |                                              <span data-ttu-id="c7d63-123">Excel 試算表，含有費用報表配置、關聯的巨集以及可叫用巨集的按鈕。</span><span class="sxs-lookup"><span data-stu-id="c7d63-123">Excel spreadsheet with the expense report layout, associated macros, and buttons to invoke the macros.</span></span>                                              |
|                                                      <span data-ttu-id="c7d63-124">MessageExample.xml</span><span class="sxs-lookup"><span data-stu-id="c7d63-124">MessageExample.xml</span></span>                                                       |                                                                            <span data-ttu-id="c7d63-125">XML 費用報表格式的範例。</span><span class="sxs-lookup"><span data-stu-id="c7d63-125">Example of the XML expense report format.</span></span>                                                                             |
|                                                           <span data-ttu-id="c7d63-126">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="c7d63-126">Setup.bat</span></span>                                                           |                                                                               <span data-ttu-id="c7d63-127">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="c7d63-127">Builds and initializes this sample.</span></span>                                                                                |
| <span data-ttu-id="c7d63-128">在 \BTSExpenseDemo 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="c7d63-128">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="c7d63-129">AssemblyInfo.cs、</span><span class="sxs-lookup"><span data-stu-id="c7d63-129">AssemblyInfo.cs,</span></span><br /><br /> <span data-ttu-id="c7d63-130">BTSExpenseDemo.btproj、</span><span class="sxs-lookup"><span data-stu-id="c7d63-130">BTSExpenseDemo.btproj,</span></span><br /><br /> <span data-ttu-id="c7d63-131">BTSExpenseDemo.sln</span><span class="sxs-lookup"><span data-stu-id="c7d63-131">BTSExpenseDemo.sln</span></span> |                                                                  <span data-ttu-id="c7d63-132">提供此範例的專案、解決方案和關聯檔案。</span><span class="sxs-lookup"><span data-stu-id="c7d63-132">Provides project, solution, and related files for this sample.</span></span>                                                                  |
|                             <span data-ttu-id="c7d63-133">在 \BTSExpenseDemo 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="c7d63-133">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="c7d63-134">BTSExpenseDemoBinding.xml</span><span class="sxs-lookup"><span data-stu-id="c7d63-134">BTSExpenseDemoBinding.xml</span></span>                              |                                                                         <span data-ttu-id="c7d63-135">用於自動化安裝，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="c7d63-135">Used for automated setup, such as port binding.</span></span>                                                                          |
|                            <span data-ttu-id="c7d63-136">在 \BTSExpenseDemo 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="c7d63-136">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="c7d63-137">BTSExpenseOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="c7d63-137">BTSExpenseOrchestration.odx</span></span>                             |                                   <span data-ttu-id="c7d63-138">提供此範例的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="c7d63-138">Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for this sample.</span></span>                                   |
|                              <span data-ttu-id="c7d63-139">在 \BTSExpenseDemo 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="c7d63-139">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="c7d63-140">SchemaExpenseReport.xsd</span><span class="sxs-lookup"><span data-stu-id="c7d63-140">SchemaExpenseReport.xsd</span></span>                               |                                                                       <span data-ttu-id="c7d63-141">提供 XML 費用報表格式的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c7d63-141">Provides a schema for the XML expense report format.</span></span>                                                                       |

### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="c7d63-142">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="c7d63-142">To build and initialize this sample</span></span>  

1. <span data-ttu-id="c7d63-143">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c7d63-143">In a command window, navigate to the following folder:</span></span>  

    <span data-ttu-id="c7d63-144">\<*範例路徑*\>\AdaptersUsage\ExpenseReportSubmission</span><span class="sxs-lookup"><span data-stu-id="c7d63-144">\<*Samples Path*\>\AdaptersUsage\ExpenseReportSubmission</span></span>  

2. <span data-ttu-id="c7d63-145">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c7d63-145">Run the file Setup.bat, which performs the following actions:</span></span>  

   - <span data-ttu-id="c7d63-146">編譯此範例的 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，並部署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="c7d63-146">Compiles the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample, and deploys the resulting assembly.</span></span>  

   - <span data-ttu-id="c7d63-147">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="c7d63-147">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.</span></span>  

     > [!NOTE]
     >  <span data-ttu-id="c7d63-148">此範例會在建立和繫結連接埠時顯示下列警告：</span><span class="sxs-lookup"><span data-stu-id="c7d63-148">This sample displays the following warnings when creating and binding the ports:</span></span>  
     >   
     >  `Warning: Receive handler not specified for receive location "BTSExpenseReceiveLocation"; updating with first receive handler with matching transport type.`  
     >   
     >  <span data-ttu-id="c7d63-149">`Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`。</span><span class="sxs-lookup"><span data-stu-id="c7d63-149">`Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`.</span></span>  
     >   
     >  <span data-ttu-id="c7d63-150">您可以安全地忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="c7d63-150">You can safely ignore these warnings.</span></span> <span data-ttu-id="c7d63-151">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="c7d63-151">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  

   - <span data-ttu-id="c7d63-152">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c7d63-152">Enables the receive location, and starts the send port.</span></span>  

   - <span data-ttu-id="c7d63-153">設定 IIS。</span><span class="sxs-lookup"><span data-stu-id="c7d63-153">Configures IIS.</span></span>  

   - <span data-ttu-id="c7d63-154">繫結並啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="c7d63-154">Binds and starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  

   - <span data-ttu-id="c7d63-155">將 HTTP 位址設定至 Excel 試算表預期的位置。</span><span class="sxs-lookup"><span data-stu-id="c7d63-155">Sets the HTTP address to the location expected by the Excel spreadsheet.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="c7d63-156">如需有關 BizTalk ISAPI 篩選器的詳細資訊，請參閱[針對 HTTP 接收位置設定 IIS 如何](../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d63-156">For more information about the BizTalk ISAPI filter, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="c7d63-157">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7d63-157">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="c7d63-158">如果您在此範例中選擇開啟並建置專案，而不執行檔案 Setup.bat，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c7d63-158">If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="c7d63-159">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="c7d63-159">Use this key pair to sign the resulting assembly.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="c7d63-160">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="c7d63-160">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="c7d63-161">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="c7d63-161">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  

3. <span data-ttu-id="c7d63-162">setup.bat 檔會設定此範例的虛擬目錄，以在與預設網站關聯的 IIS 應用程式集區中執行。</span><span class="sxs-lookup"><span data-stu-id="c7d63-162">The setup.bat file configures the virtual directory for this sample to run in the IIS application pool associated with the default web site.</span></span>  <span data-ttu-id="c7d63-163">若要設定此範例中的使用者內容下執行的虛擬目錄**BizTalk Isolated Host Users**並**IIS_WPG**使用者群組，您應該設定要執行新的虛擬目錄IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="c7d63-163">To configure the virtual directory for this sample to run under the context of a user in the **BizTalk Isolated Host Users** and **IIS_WPG** user groups, you should configure the virtual directory to run in a new IIS application pool.</span></span>  <span data-ttu-id="c7d63-164">請依照下列步驟執行，將虛擬目錄設定為在新的 IIS 應用程式集區中執行：</span><span class="sxs-lookup"><span data-stu-id="c7d63-164">Configure the virtual directory to run in a new IIS application pool by completing the following steps:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="c7d63-165">如果您已經為其他 SDK 範例建立新的應用程式集區，則可以繼續執行下面最後一項步驟。</span><span class="sxs-lookup"><span data-stu-id="c7d63-165">If you have already created a new application pool for another SDK sample then you can proceed to the last bullet item below.</span></span>  

   1.  <span data-ttu-id="c7d63-166">按一下 **開始**，指向**程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="c7d63-166">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  

   2.  <span data-ttu-id="c7d63-167">在  **Internet Information Services (IIS) 管理員**，瀏覽至**應用程式集區**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c7d63-167">In the **Internet Information Services (IIS) Manager**, navigate to the **Application Pools** folder.</span></span>  

   3.  <span data-ttu-id="c7d63-168">以滑鼠右鍵按一下**應用程式集區**資料夾，然後按一下**新增**，**應用程式集區...**</span><span class="sxs-lookup"><span data-stu-id="c7d63-168">Right-click the **Application Pools** folder and click **New**, **Application Pool...**</span></span>  

   4.  <span data-ttu-id="c7d63-169">輸入的名稱**應用程式集區識別碼：** （例如 biztalksdksamples），確認**新的應用程式集區使用預設設定**選項已選取，然後按一下**確定**至建立新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="c7d63-169">Enter a name for the **Application Pool ID:** such as BizTalkSDKSamples, verify that the **Use default settings for new application pool** option is selected and click **OK** to create the new application pool.</span></span>  

   5.  <span data-ttu-id="c7d63-170">以滑鼠右鍵按一下新的應用程式集區，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c7d63-170">Right-click the new application pool and then click **Properties**.</span></span>  

   6.  <span data-ttu-id="c7d63-171">按一下 [**身分識別**] 索引標籤的 [屬性] 對話方塊中，並將變更此應用程式集區執行屬於使用者的身分識別**BizTalk 外掛式主控件使用者**使用者群組。</span><span class="sxs-lookup"><span data-stu-id="c7d63-171">Click the **Identity** tab of the properties dialog box and change the identity under which this application pool runs to a user that is a member of the **BizTalk Isolated Host Users** user group.</span></span>  <span data-ttu-id="c7d63-172">此使用者也應該屬於本機**IIS_WPG**使用者群組。</span><span class="sxs-lookup"><span data-stu-id="c7d63-172">This user should also be a member of the local **IIS_WPG** user group.</span></span>  

   7.  <span data-ttu-id="c7d63-173">設定這個 SDK 範例的虛擬目錄為在新的應用程式集區下執行。</span><span class="sxs-lookup"><span data-stu-id="c7d63-173">Configure the virtual directory for this SDK sample to run under the new application pool.</span></span> <span data-ttu-id="c7d63-174">**應用程式集區：** 設定可用於**虛擬目錄**] 索引標籤的 [虛擬目錄的 [內容] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c7d63-174">The **Application pool:** setting is available on the **Virtual Directory** tab of the Virtual Directory properties dialog box.</span></span> <span data-ttu-id="c7d63-175">針對此範例會建立虛擬目錄**ExpenseReportSubmission**。</span><span class="sxs-lookup"><span data-stu-id="c7d63-175">The virtual directory created for this sample is **ExpenseReportSubmission**.</span></span>  

4. <span data-ttu-id="c7d63-176">為 HTTPReceive.dll 將 Web 服務延伸模組新增至 IIS</span><span class="sxs-lookup"><span data-stu-id="c7d63-176">Add a web service extension to IIS for HTTPReceive.dll</span></span>  

   1.  <span data-ttu-id="c7d63-177">在  **Internet Information Services (IIS) 管理員**，瀏覽至**網頁服務延伸**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c7d63-177">In the **Internet Information Services (IIS) Manager**, navigate to the **Web Service Extensions** folder.</span></span>  

   2.  <span data-ttu-id="c7d63-178">以滑鼠右鍵按一下**網頁服務延伸模組**資料夾，然後選取**新增新的 Web 服務延伸**以顯示**新增網頁服務延伸** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c7d63-178">Right-click the **Web Service Extensions** folder and select **Add a new Web service extension** to display the **New Web Service Extension** dialog box.</span></span>  

   3.  <span data-ttu-id="c7d63-179">請輸入**ExpenseReportSubmission**如**延伸模組名稱：**</span><span class="sxs-lookup"><span data-stu-id="c7d63-179">Enter **ExpenseReportSubmission** for **Extension name:**</span></span>  

   4.  <span data-ttu-id="c7d63-180">按一下 [**新增**顯示**Add file** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c7d63-180">Click **Add** to display the **Add file** dialog box.</span></span>  

   5.  <span data-ttu-id="c7d63-181">按一下 **瀏覽**顯示**開啟**對話方塊方塊中，並瀏覽至 *\<BizTalk Server 安裝資料夾\>* \HttpReceive\BTSHTTPReceive.dll，然後按一下 **開放**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c7d63-181">Click **Browse** to display the **Open** dialog box and navigate to *\<BizTalk Server Installation folder\>* \HttpReceive\BTSHTTPReceive.dll and click **Open**, then click **OK**.</span></span>  

   6.  <span data-ttu-id="c7d63-182">啟用的選項**設定延伸狀態成允許**然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c7d63-182">Enable the option to **Set extension status to Allowed** and click **OK**.</span></span>  

## <a name="running-this-sample"></a><span data-ttu-id="c7d63-183">執行此範例</span><span class="sxs-lookup"><span data-stu-id="c7d63-183">Running This Sample</span></span>  
 <span data-ttu-id="c7d63-184">使用下列程序以執行 ExpenseReportSubmission 範例。</span><span class="sxs-lookup"><span data-stu-id="c7d63-184">Use the following procedure to run the ExpenseReportSubmission sample.</span></span>  

> [!NOTE]
>  <span data-ttu-id="c7d63-185">如果您使用 Microsoft Excel 的增強型安全性功能，試算表中的巨集可能會被停用。</span><span class="sxs-lookup"><span data-stu-id="c7d63-185">If you are using the enhanced security features of Microsoft Excel, the macros in the spreadsheet may be disabled.</span></span> <span data-ttu-id="c7d63-186">如需有關如何執行來自信任來源的未簽署巨集的資訊，請參閱 Excel 所提供的指示。</span><span class="sxs-lookup"><span data-stu-id="c7d63-186">Follow the instructions provided by Excel about how to run unsigned macros from a trusted source.</span></span>  

#### <a name="to-run-this-sample"></a><span data-ttu-id="c7d63-187">執行此範例</span><span class="sxs-lookup"><span data-stu-id="c7d63-187">To run this sample</span></span>  

1.  <span data-ttu-id="c7d63-188">開啟此範例所隨附的 Excel 檔 ExpenseReport.15.3.xls。</span><span class="sxs-lookup"><span data-stu-id="c7d63-188">Open the Excel file ExpenseReport.15.3.xls included with this sample.</span></span>  

2.  <span data-ttu-id="c7d63-189">在試算表中變更範例資料，但不要變更它的格式 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="c7d63-189">Optionally, change the sample data in the spreadsheet without changing its format.</span></span>  

3.  <span data-ttu-id="c7d63-190">在 excel 中，按一下**啟動**以執行本機計算。</span><span class="sxs-lookup"><span data-stu-id="c7d63-190">In the spreadsheet, click **Start** to perform local calculations.</span></span>  

     <span data-ttu-id="c7d63-191">從按鈕的文字變更**開始**要**送出**。</span><span class="sxs-lookup"><span data-stu-id="c7d63-191">The text of the button changes from **Start** to **Submit**.</span></span>  

4.  <span data-ttu-id="c7d63-192">在 excel 中，按一下**送出**。</span><span class="sxs-lookup"><span data-stu-id="c7d63-192">In the spreadsheet, click **Submit**.</span></span>  

5.  <span data-ttu-id="c7d63-193">檢查所提交訊息的文字、資料表上背景為黃色的結果 (儲存格 C7)，以及右下方實際的傳回程式碼和文字描述 (儲存格 G23)。</span><span class="sxs-lookup"><span data-stu-id="c7d63-193">Observe the text of the submitted message, the result above the table with yellow background (cell C7), and the actual return code and text description below and to the right (cell G23).</span></span>  

     <span data-ttu-id="c7d63-194">如果提交失敗，請再試一次，</span><span class="sxs-lookup"><span data-stu-id="c7d63-194">If submission fails, try again.</span></span> <span data-ttu-id="c7d63-195">並請參閱＜註解＞一節中的疑難排解表格。</span><span class="sxs-lookup"><span data-stu-id="c7d63-195">Also, refer to the troubleshooting table in the Comments section.</span></span>  

## <a name="comments"></a><span data-ttu-id="c7d63-196">註解</span><span class="sxs-lookup"><span data-stu-id="c7d63-196">Comments</span></span>  
 <span data-ttu-id="c7d63-197">例如現場銷售人員配備的舊版 Microsoft Windows 不支援 .NET Framework，且不具有升級為最新版 Windows 的條件，就可能會發生這樣的情況。</span><span class="sxs-lookup"><span data-stu-id="c7d63-197">Scenarios such as this can occur when, for example, a field sales force is equipped with older versions of Microsoft Windows that do not support the .NET Framework, and for which the requirement to upgrade to a more current version of Windows is not a viable option.</span></span>  

 <span data-ttu-id="c7d63-198">此範例展示的重要功能如下：</span><span class="sxs-lookup"><span data-stu-id="c7d63-198">Essential features demonstrated in this sample are:</span></span>  

- <span data-ttu-id="c7d63-199">透過多功能的用戶端 (非 .NET) 提交</span><span class="sxs-lookup"><span data-stu-id="c7d63-199">Submission from a rich client (not .NET-based)</span></span>  

- <span data-ttu-id="c7d63-200">Microsoft Office 整合</span><span class="sxs-lookup"><span data-stu-id="c7d63-200">Microsoft Office integration</span></span>  

- <span data-ttu-id="c7d63-201">HTTP 接收連線</span><span class="sxs-lookup"><span data-stu-id="c7d63-201">HTTP receive connections</span></span>  

- <span data-ttu-id="c7d63-202">簡易的協調流程</span><span class="sxs-lookup"><span data-stu-id="c7d63-202">Simple orchestration</span></span>  

- <span data-ttu-id="c7d63-203">File adapter (FILE 配接器)</span><span class="sxs-lookup"><span data-stu-id="c7d63-203">File adapter</span></span>  

  <span data-ttu-id="c7d63-204">下表說明一些可能發生的提交錯誤及其解決方案。</span><span class="sxs-lookup"><span data-stu-id="c7d63-204">The following table shows some possible submission errors and their solutions.</span></span>  

|<span data-ttu-id="c7d63-205">HTTP 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="c7d63-205">HTTP error code</span></span>|<span data-ttu-id="c7d63-206">可能的動作</span><span class="sxs-lookup"><span data-stu-id="c7d63-206">Possible action</span></span>|  
|---------------------|---------------------|  
|<span data-ttu-id="c7d63-207">401 未經授權</span><span class="sxs-lookup"><span data-stu-id="c7d63-207">401 Unauthorized</span></span>|<span data-ttu-id="c7d63-208">允許匿名存取虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="c7d63-208">Enable anonymous access on the virtual directory.</span></span>|  
|<span data-ttu-id="c7d63-209">503 服務無法使用 (以及大部分在 400 和 500 範圍內的其他 HTTP 代碼)</span><span class="sxs-lookup"><span data-stu-id="c7d63-209">503 Service Unavailable, and most other HTTP codes in the 400 and 500 ranges</span></span>|<span data-ttu-id="c7d63-210">確認主機正在執行，且服務已部署完成、繫結至正確的連接埠並已啟動。</span><span class="sxs-lookup"><span data-stu-id="c7d63-210">Ensure that the host runs and that the service is deployed, bound to the correct port, and started.</span></span>|  

## <a name="see-also"></a><span data-ttu-id="c7d63-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7d63-211">See Also</span></span>  
 [<span data-ttu-id="c7d63-212">配接器範例 - 用法</span><span class="sxs-lookup"><span data-stu-id="c7d63-212">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)