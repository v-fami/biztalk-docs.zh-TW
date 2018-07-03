---
title: 設定 BizTalk Accelerator for SWIFT |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e34b0b2d-f563-468b-b6b9-536f0df96f52
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57b56495e66d835451eb8641f3fd9407462593c9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997455"
---
# <a name="configure-biztalk-accelerator-for-swift"></a><span data-ttu-id="5d1d6-102">設定 BizTalk Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="5d1d6-102">Configure BizTalk Accelerator for SWIFT</span></span>

<span data-ttu-id="5d1d6-103">設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-103">Configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> 

<span data-ttu-id="5d1d6-104">當您安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]，沒有可讓您自動執行組態的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-104">When you install [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], there is a checkbox that lets you run the configuration automatically.</span></span> <span data-ttu-id="5d1d6-105">或者，您可以開啟 BizTalk Accelerator for SWIFT (A4SWIFT) 組態，您的應用程式中所列。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-105">Or, you can open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration listed in your apps.</span></span>

<span data-ttu-id="5d1d6-106">本主題說明如何設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]加速器，如何匯出或匯入組態，以及列出後續設定步驟。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-106">This topic shows you how to configure the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] accelerator, how to export or import a configuration, and also lists the post-configuration steps.</span></span>

## <a name="configure-a4swift"></a><span data-ttu-id="5d1d6-107">設定 A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="5d1d6-107">Configure A4SWIFT</span></span>

1. <span data-ttu-id="5d1d6-108">開啟 BizTalk Accelerator for SWIFT (A4SWIFT) 組態。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-108">Open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration.</span></span>
2. <span data-ttu-id="5d1d6-109">選取  **MCRR**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-109">Select **MCRR**.</span></span> <span data-ttu-id="5d1d6-110">MCRR 才會提供您安裝**Message Repair 和 New Submission**元件。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-110">MCRR is available only if you installed the **Message Repair and New Submission** components.</span></span>
3. <span data-ttu-id="5d1d6-111">當系統詢問**您想要建立新的資料庫群組**:</span><span class="sxs-lookup"><span data-stu-id="5d1d6-111">When asked **Do you want to create a new database group**:</span></span>

   * <span data-ttu-id="5d1d6-112">選取此選項以建立新的群組中所示**群組**窗格。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-112">Select this option to create the new groups shown in the **Group** pane.</span></span> 
   * <span data-ttu-id="5d1d6-113">若要將現有的資料庫群組，取消核取此選項。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-113">To join an existing database group, uncheck this option.</span></span>

4. <span data-ttu-id="5d1d6-114">如果您已安裝**Web 元件 Message Repair 和 New Submission**，然後選取**WebService**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-114">If you installed **Web Components for Message Repair and New Submission**, then select **WebService**.</span></span>
5. <span data-ttu-id="5d1d6-115">選取要主控 A4SWIFT Web 服務的網站。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-115">Select the web site to host the A4SWIFT Web service.</span></span> <span data-ttu-id="5d1d6-116">根據預設，會選取預設的網站。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-116">By default, the Default Web Site is selected.</span></span>
6. <span data-ttu-id="5d1d6-117">選取 **套用設定**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-117">Select **Apply Configuration**.</span></span>
7. <span data-ttu-id="5d1d6-118">在 **摘要**，確認組態設定，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-118">In **Summary**, verify the configuration settings, and then click **Configure**.</span></span> 

    > [!TIP] 
    > <span data-ttu-id="5d1d6-119">您可以視需要將組態設定儲存為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-119">You can save the configuration settings as an XML file, if desired.</span></span>

8. <span data-ttu-id="5d1d6-120">選取 **完成**組態完成時。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-120">Select **Finish** when the configuration completes.</span></span>

## <a name="export-or-import-a-configuration"></a><span data-ttu-id="5d1d6-121">匯出或匯入組態</span><span class="sxs-lookup"><span data-stu-id="5d1d6-121">Export or import a configuration</span></span>
<span data-ttu-id="5d1d6-122">您可以將 A4SWIFT 的組態設定匯出至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-122">You can export the configuration settings of A4SWIFT to an XML file.</span></span> <span data-ttu-id="5d1d6-123">這些設定然後設定另一個 A4SWIFT 安裝的匯入。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-123">These settings can then be imported to configure another A4SWIFT installation.</span></span> 

### <a name="export-the-configuration"></a><span data-ttu-id="5d1d6-124">匯出設定</span><span class="sxs-lookup"><span data-stu-id="5d1d6-124">Export the configuration</span></span>

1. <span data-ttu-id="5d1d6-125">開啟 Microsoft BizTalk Accelerator for SWIFT 組態，然後選取**匯出組態**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-125">Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Export Configuration**.</span></span>
2. <span data-ttu-id="5d1d6-126">在 **另存新檔**，瀏覽至您要儲存組態檔中，輸入組態檔的名稱的資料夾，然後**儲存**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-126">In **Save As**, browse to the folder where you want to save the configuration file, enter a name for the configuration file, and then **Save**.</span></span>
3. <span data-ttu-id="5d1d6-127">已成功匯出時選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-127">When exported successfully, select **OK**.</span></span>

### <a name="import-a-configuration"></a><span data-ttu-id="5d1d6-128">匯入組態</span><span class="sxs-lookup"><span data-stu-id="5d1d6-128">Import a configuration</span></span>
1. <span data-ttu-id="5d1d6-129">開啟 Microsoft BizTalk Accelerator for SWIFT 組態，然後選取**匯入組態**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-129">Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Import Configuration**.</span></span>
2. <span data-ttu-id="5d1d6-130">瀏覽至包含組態檔的資料夾、 選取檔案，然後按**匯入**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-130">Browse to the folder that contains the configuration file, select the file, and then select **Import**.</span></span>

## <a name="post-configuration-steps"></a><span data-ttu-id="5d1d6-131">後續設定步驟</span><span class="sxs-lookup"><span data-stu-id="5d1d6-131">Post-configuration steps</span></span>

### <a name="add-users-to-the-a4swift-users-group"></a><span data-ttu-id="5d1d6-132">將使用者新增至 A4SWIFT 使用者群組</span><span class="sxs-lookup"><span data-stu-id="5d1d6-132">Add users to the A4SWIFT Users group</span></span>

<span data-ttu-id="5d1d6-133">設定之後[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]，新增執行 BizTalkServerApplication 主控件執行個體的帳戶**A4SWIFT 使用者**群組 (*不* **A4SWIFT 管理員**群組)。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-133">After you configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)], add the account that runs the BizTalkServerApplication host instance to the **A4SWIFT Users** group (*not* the **A4SWIFT Administrators** group).</span></span> 

<span data-ttu-id="5d1d6-134">**步驟**:</span><span class="sxs-lookup"><span data-stu-id="5d1d6-134">**Steps**:</span></span>

1. <span data-ttu-id="5d1d6-135">開啟**Services**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-135">Open **Services**.</span></span> <span data-ttu-id="5d1d6-136">服務也會提供**伺服器管理員**，然後**工具**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-136">Services is also available in **Server Manager**, and then **Tools**.</span></span> 
2. <span data-ttu-id="5d1d6-137">在清單中，尋找**BizTalk Service BizTalk Group: BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-137">In the list, find **BizTalk Service BizTalk Group: BizTalkServerApplication**.</span></span> 
3. <span data-ttu-id="5d1d6-138">按兩下選取以開啟其屬性。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-138">Double-select to open its properties.</span></span>
4. <span data-ttu-id="5d1d6-139">在 **登入**索引標籤中，記下的使用者帳戶列為**此帳戶**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-139">In the **Log On** tab, note the user account listed as **This account**.</span></span>
5. <span data-ttu-id="5d1d6-140">開啟**本機使用者和群組**（在 電腦管理），然後尋找**A4SWIFT 使用者**群組。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-140">Open **Local Users and Groups** (in Computer Management), and then find the **A4SWIFT Users** group.</span></span> <span data-ttu-id="5d1d6-141">加入此群組中的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-141">Add the user account to this group.</span></span>

> [!TIP] 
> <span data-ttu-id="5d1d6-142">主控件執行個體帳戶需要主應用程式訊息修復執行階段元件此群組成員資格來存取 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-142">The host instance account needs this group membership for the host Message Repair runtime component to access the BizTalk Server database.</span></span>

### <a name="check-the-identity-of-the-application-pool"></a><span data-ttu-id="5d1d6-143">檢查應用程式集區的身分識別</span><span class="sxs-lookup"><span data-stu-id="5d1d6-143">Check the identity of the application pool</span></span>
<span data-ttu-id="5d1d6-144">A4SWIFT_MRSR web 服務會裝載於 IIS 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-144">The A4SWIFT_MRSR web service is hosted in an application in IIS.</span></span> <span data-ttu-id="5d1d6-145">應用程式集區身分識別*無法*網路服務。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-145">The application pool identity *cannot* be Network Service.</span></span> <span data-ttu-id="5d1d6-146">將應用程式集區身分識別變更為成員的本機或網域帳戶**A4SWIFT 使用者**群組。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-146">Change the identity of the application pool to a local or domain account that is a member of the **A4SWIFT Users** group.</span></span>

<span data-ttu-id="5d1d6-147">**步驟**:</span><span class="sxs-lookup"><span data-stu-id="5d1d6-147">**Steps**:</span></span>

1. <span data-ttu-id="5d1d6-148">開啟**Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-148">Open **Internet Information Services Manager**.</span></span> <span data-ttu-id="5d1d6-149">IIS 管理員中也會提供**伺服器管理員**，然後**工具**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-149">The IIS Manager is also available in **Server Manager**, and then **Tools**.</span></span> 
2. <span data-ttu-id="5d1d6-150">依序展開**Default Web Site**，然後選取 A4SWIFT_MRSR web 服務。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-150">Expand the **Default Web Site**, and select the A4SWIFT_MRSR web service.</span></span> 
3. <span data-ttu-id="5d1d6-151">選取 **基本設定**。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-151">Select **Basic Settings**.</span></span> <span data-ttu-id="5d1d6-152">會列出應用程式集區的名稱。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-152">The name of the application pool is listed.</span></span>
4. <span data-ttu-id="5d1d6-153">在左窗格中，選取**應用程式集區**，然後選取 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-153">In the left pane, select **Application Pools**, and then select your application pool.</span></span>
5. <span data-ttu-id="5d1d6-154">選取 [**進階設定]**，並將變更**識別**如有需要。</span><span class="sxs-lookup"><span data-stu-id="5d1d6-154">Select **Advanced Settings**, and change the **Identity** if needed.</span></span>