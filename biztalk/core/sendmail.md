---
title: "SendMail |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- SMTP adapters
ms.assetid: a0258619-b195-4c8a-8326-77add6e6f04d
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6cf0243eccb6a38dc121cfe06a60e30fa0c26c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="sendmail"></a><span data-ttu-id="f0611-102">SendMail</span><span class="sxs-lookup"><span data-stu-id="f0611-102">SendMail</span></span>
<span data-ttu-id="f0611-103">SendMail 範例示範如何使用 Simple Mail Transfer Protocol (SMTP) 配接器，從 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程內傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="f0611-103">The SendMail sample demonstrates how you can use the Simple Mail Transfer Protocol (SMTP) adapter to send e-mail messages from within a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span> <span data-ttu-id="f0611-104">用來傳送電子郵件訊息的動態資訊，會使用以屬性升級功能從 XML 訊息擷取。</span><span class="sxs-lookup"><span data-stu-id="f0611-104">Dynamic information used to send the e-mail messages is retrieved from an XML message using property promotion functionality.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="f0611-105">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="f0611-105">What This Sample Does</span></span>  
 <span data-ttu-id="f0611-106">此範例會依下列步驟順序，從內送 XML 訂單 (PO) 訊息升級而來的屬性取得資訊，再使用該項資訊傳送電子郵件訊息：</span><span class="sxs-lookup"><span data-stu-id="f0611-106">This sample sends an e-mail message using information obtained from properties promoted out of an incoming XML purchase order (PO) message, using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="f0611-107">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程擷取輸入 XML PO 訊息。</span><span class="sxs-lookup"><span data-stu-id="f0611-107">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration retrieves an input XML PO message.</span></span>  
  
2.  <span data-ttu-id="f0611-108">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程升級**PONumber**和**電子郵件**將來更容易存取的屬性。</span><span class="sxs-lookup"><span data-stu-id="f0611-108">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration promotes the **PONumber** and **Email** properties for easier access in the future.</span></span>  
  
3.  <span data-ttu-id="f0611-109">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，使用升級屬性的值來設定動態傳送埠的目的地址和電子郵件訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="f0611-109">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration uses the values of the promoted properties to set the destination address of the dynamic send port and to set the subject of the e-mail message.</span></span>  
  
4.  <span data-ttu-id="f0611-110">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程透過 SMTP 配接器傳送所建構的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="f0611-110">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration sends the constructed e-mail message through the SMTP adapter.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="f0611-111">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f0611-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="f0611-112">\<*範例路徑*\>\AdaptersUsage\SendMail\\</span><span class="sxs-lookup"><span data-stu-id="f0611-112">\<*Samples Path*\>\AdaptersUsage\SendMail\\</span></span>  
  
 <span data-ttu-id="f0611-113">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f0611-113">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="f0611-114">檔案</span><span class="sxs-lookup"><span data-stu-id="f0611-114">File(s)</span></span>|<span data-ttu-id="f0611-115">Description</span><span class="sxs-lookup"><span data-stu-id="f0611-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0611-116">AssemblyInfo.cs, SendMail.btproj, SendMail.sln</span><span class="sxs-lookup"><span data-stu-id="f0611-116">AssemblyInfo.cs, SendMail.btproj, SendMail.sln</span></span>|<span data-ttu-id="f0611-117">提供此範例的專案、解決方案和組件資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="f0611-117">Provides project, solution, and assembly information files for this sample.</span></span>|  
|<span data-ttu-id="f0611-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="f0611-118">Cleanup.bat</span></span>|<span data-ttu-id="f0611-119">從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f0611-119">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="f0611-120">PropertySchema.xsd, PurchaseOrder.xsd</span><span class="sxs-lookup"><span data-stu-id="f0611-120">PropertySchema.xsd, PurchaseOrder.xsd</span></span>|<span data-ttu-id="f0611-121">分別針對您要升級的屬性和 XML PO 訊息提供結構描述。</span><span class="sxs-lookup"><span data-stu-id="f0611-121">Provides schemas for the properties that you want to promote, and for the XML PO message, respectively.</span></span>|  
|<span data-ttu-id="f0611-122">ReceiveSend.odx</span><span class="sxs-lookup"><span data-stu-id="f0611-122">ReceiveSend.odx</span></span>|<span data-ttu-id="f0611-123">提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，以處理內送 XML PO 訊息，並根據訊息內的資訊傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="f0611-123">Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that processes the incoming XML PO message and sends an e-mail message based on information in the message.</span></span>|  
|<span data-ttu-id="f0611-124">SendMailInput.xml</span><span class="sxs-lookup"><span data-stu-id="f0611-124">SendMailInput.xml</span></span>|<span data-ttu-id="f0611-125">包含範本輸入檔，其中包含使用 XML 指定的訂單。</span><span class="sxs-lookup"><span data-stu-id="f0611-125">Contains a sample input file with a PO specified using XML.</span></span>|  
|<span data-ttu-id="f0611-126">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="f0611-126">Setup.bat</span></span>|<span data-ttu-id="f0611-127">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="f0611-127">Builds and initializes this sample.</span></span> <span data-ttu-id="f0611-128">**注意：**和此安裝程式檔案建立並繫結連接埠，依此類推，使用不同的機制，比大多數的安裝程式檔案的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="f0611-128">**Note:**  This setup file creates and binds ports, and so on, using a different mechanism than most of the setup files for the SDK samples.</span></span> <span data-ttu-id="f0611-129">並不需要附贈 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="f0611-129">It does not require a companion .xml file.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="f0611-130">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="f0611-130">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="f0611-131">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f0611-131">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="f0611-132">\<*範例路徑*\>\AdaptersUsage\SendMail</span><span class="sxs-lookup"><span data-stu-id="f0611-132">\<*Samples Path*\>\AdaptersUsage\SendMail</span></span>  
  
2.  <span data-ttu-id="f0611-133">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f0611-133">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="f0611-134">為此範例建立下列輸入資料夾：</span><span class="sxs-lookup"><span data-stu-id="f0611-134">Creates the following input folder for this sample:</span></span>  
  
         <span data-ttu-id="f0611-135">\<*範例路徑*\>\AdaptersUsage\SendMail\In</span><span class="sxs-lookup"><span data-stu-id="f0611-135">\<*Samples Path*\>\AdaptersUsage\SendMail\In</span></span>  
  
    -   <span data-ttu-id="f0611-136">為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f0611-136">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="f0611-137">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="f0611-137">Starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f0611-138">在嘗試執行此範例之前，您必須確認 BizTalk 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0611-138">You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f0611-139">如果您在此範例中選擇開啟並建置專案，而不執行檔案 Setup.bat，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="f0611-139">If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="f0611-140">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="f0611-140">Use this key pair to sign the resulting assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f0611-141">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat 並刪除所有前置詞為 SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail 的接收埠和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f0611-141">To undo changes made by Setup.bat, run Cleanup.bat and delete all receive and send ports prefixed with SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail.</span></span> <span data-ttu-id="f0611-142">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="f0611-142">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
3.  <span data-ttu-id="f0611-143">在**BizTalk Server 管理**主控台中，尋找前置詞為 SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail 的接收埠。</span><span class="sxs-lookup"><span data-stu-id="f0611-143">In the **BizTalk Server Administration** console, locate the receive port prefixed by SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail.</span></span> <span data-ttu-id="f0611-144">更新此接收埠的接收位置，以指向檔案系統上做為輸入位置的目錄。</span><span class="sxs-lookup"><span data-stu-id="f0611-144">Update the receive location for this receive port to point to a directory on your file system to use as the input location.</span></span>  
  
4.  <span data-ttu-id="f0611-145">使用 [記事本] 之類的程式來修改檔案 SendMailInput.xml，讓**電子郵件**項目會指定要接收此範例所產生的電子郵件訊息的合法電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="f0611-145">Using a program such as Notepad, modify the file SendMailInput.xml so that the **Email** element specifies a legitimate e-mail address at which you want to receive the e-mail message generated by this sample.</span></span>  
  
5.  <span data-ttu-id="f0611-146">按一下**啟動**，指向 **程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f0611-146">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
6.  <span data-ttu-id="f0611-147">在**BizTalk Server 管理**主控台中，展開 BizTalk 群組樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="f0611-147">In the **BizTalk Server Administration** console, expand the BizTalk Group tree.</span></span>  
  
7.  <span data-ttu-id="f0611-148">展開**平台設定**樹狀目錄中的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="f0611-148">Expand the **Platform Settings** tree in the left pane.</span></span>  
  
8.  <span data-ttu-id="f0611-149">展開**配接器**資料夾中，按一下  **SMTP**節點，然後再按兩下右窗格中的資料列的 SMTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="f0611-149">Expand the **Adapters** folder, click the **SMTP** node, and then double-click the SMTP adapter row in the right pane.</span></span>  
  
9. <span data-ttu-id="f0611-150">在**SMTP-配接器處理常式屬性**對話方塊中，按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="f0611-150">In the **SMTP - Adapter Handler Properties** dialog box, click **Properties**.</span></span>  
  
10. <span data-ttu-id="f0611-151">在**SMTP 傳輸屬性**對話方塊**屬性**索引標籤上，提供適當的值，如**SMTP 伺服器名稱**和**（電子郵件地址）**屬性，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f0611-151">In the **SMTP Transport Properties** dialog box, on the **Properties** tab, provide appropriate values for the **SMTP server name** and **From (e-mail address)** properties, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f0611-152">透過此 SMTP 配接器傳送的任何電子郵件訊息，都是使用這些值來建構寄件者電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="f0611-152">These values will be used to construct the From e-mail address for any e-mail messages sent through this SMTP adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0611-153">若您需要驗證 SMTP 伺服器，必須確保寄件者電子郵件地址的所屬帳號與驗證所用的帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="f0611-153">If you need to authenticate with your SMTP server, you must ensure that the From e-mail address belongs to the same account that you use for authentication.</span></span>  
  
11. <span data-ttu-id="f0611-154">請停止再重新啟動 BizTalk 服務 ( BizTalkServerApplication )，協調流程才會採用這些變更。</span><span class="sxs-lookup"><span data-stu-id="f0611-154">Stop and then restart the BizTalk service (BizTalkServerApplication) so that the orchestration will adopt these changes.</span></span>  
  
### <a name="to-run-this-sample"></a><span data-ttu-id="f0611-155">執行此範例</span><span class="sxs-lookup"><span data-stu-id="f0611-155">To run this sample</span></span>  
  
1.  <span data-ttu-id="f0611-156">將修改後之 SendMailInput.xml 檔案的複本放在 [輸入] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f0611-156">Put a copy of the modified file SendMailInput.xml into the input folder.</span></span>  
  
2.  <span data-ttu-id="f0611-157">請觀察您在上一個程序中指定的電子郵件地址是否接收到電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="f0611-157">Observe the arrival of an e-mail message to the e-mail address you specified in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0611-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0611-158">See Also</span></span>  
 [<span data-ttu-id="f0611-159">配接器範例 - 用法</span><span class="sxs-lookup"><span data-stu-id="f0611-159">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)