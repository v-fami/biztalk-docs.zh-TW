---
title: "設定 BizTalk Accelerator for SWIFT |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e34b0b2d-f563-468b-b6b9-536f0df96f52
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaa9812243ef7d5ff4bb8b902ac7aee48e54ab99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-biztalk-accelerator-for-swift"></a><span data-ttu-id="336c3-102">設定 BizTalk Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="336c3-102">Configure BizTalk Accelerator for SWIFT</span></span>

<span data-ttu-id="336c3-103">設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="336c3-103">Configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> 

<span data-ttu-id="336c3-104">當您安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]，還有可讓您自動執行設定的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="336c3-104">When you install [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], there is a checkbox that lets you run the configuration automatically.</span></span> <span data-ttu-id="336c3-105">或者，您可以開啟 BizTalk Accelerator for SWIFT (A4SWIFT) 組態，您的應用程式中所列。</span><span class="sxs-lookup"><span data-stu-id="336c3-105">Or, you can open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration listed in your apps.</span></span>

<span data-ttu-id="336c3-106">本主題會示範如何設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]快速鍵，如何匯出或匯入組態，以及列出後設定步驟。</span><span class="sxs-lookup"><span data-stu-id="336c3-106">This topic shows you how to configure the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] accelerator, how to export or import a configuration, and also lists the post-configuration steps.</span></span>

## <a name="configure-a4swift"></a><span data-ttu-id="336c3-107">設定 A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="336c3-107">Configure A4SWIFT</span></span>

1. <span data-ttu-id="336c3-108">開啟 BizTalk Accelerator for SWIFT (A4SWIFT) 組態。</span><span class="sxs-lookup"><span data-stu-id="336c3-108">Open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration.</span></span>
2. <span data-ttu-id="336c3-109">選取**MCRR**。</span><span class="sxs-lookup"><span data-stu-id="336c3-109">Select **MCRR**.</span></span> <span data-ttu-id="336c3-110">MCRR 是您安裝時，才可以使用**Message Repair 和 New Submission**元件。</span><span class="sxs-lookup"><span data-stu-id="336c3-110">MCRR is available only if you installed the **Message Repair and New Submission** components.</span></span>
3. <span data-ttu-id="336c3-111">當系統詢問**您想要建立新的資料庫群組**:</span><span class="sxs-lookup"><span data-stu-id="336c3-111">When asked **Do you want to create a new database group**:</span></span>

  * <span data-ttu-id="336c3-112">選取此選項可建立新的群組中顯示**群組**窗格。</span><span class="sxs-lookup"><span data-stu-id="336c3-112">Select this option to create the new groups shown in the **Group** pane.</span></span> 
  * <span data-ttu-id="336c3-113">若要將現有的資料庫群組，取消核取此選項。</span><span class="sxs-lookup"><span data-stu-id="336c3-113">To join an existing database group, uncheck this option.</span></span>

3. <span data-ttu-id="336c3-114">如果您已安裝**Web 元件 Message Repair 和 New Submission**，然後選取**WebService**。</span><span class="sxs-lookup"><span data-stu-id="336c3-114">If you installed **Web Components for Message Repair and New Submission**, then select **WebService**.</span></span>
4. <span data-ttu-id="336c3-115">選取要主控 A4SWIFT Web 服務的網站。</span><span class="sxs-lookup"><span data-stu-id="336c3-115">Select the web site to host the A4SWIFT Web service.</span></span> <span data-ttu-id="336c3-116">根據預設，會選取預設的網站。</span><span class="sxs-lookup"><span data-stu-id="336c3-116">By default, the Default Web Site is selected.</span></span>
5. <span data-ttu-id="336c3-117">選取**套用組態**。</span><span class="sxs-lookup"><span data-stu-id="336c3-117">Select **Apply Configuration**.</span></span>
6. <span data-ttu-id="336c3-118">在**摘要**，確認組態設定，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="336c3-118">In **Summary**, verify the configuration settings, and then click **Configure**.</span></span> 

    > [!TIP] 
    > <span data-ttu-id="336c3-119">您可以視需要將組態設定儲存為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="336c3-119">You can save the configuration settings as an XML file, if desired.</span></span>

7. <span data-ttu-id="336c3-120">選取**完成**時設定完成。</span><span class="sxs-lookup"><span data-stu-id="336c3-120">Select **Finish** when the configuration completes.</span></span>

## <a name="export-or-import-a-configuration"></a><span data-ttu-id="336c3-121">匯出或匯入組態</span><span class="sxs-lookup"><span data-stu-id="336c3-121">Export or import a configuration</span></span>
<span data-ttu-id="336c3-122">您可以將 A4SWIFT 的組態設定匯出至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="336c3-122">You can export the configuration settings of A4SWIFT to an XML file.</span></span> <span data-ttu-id="336c3-123">接著可以設定另一個 A4SWIFT 安裝匯入這些設定。</span><span class="sxs-lookup"><span data-stu-id="336c3-123">These settings can then be imported to configure another A4SWIFT installation.</span></span> 

### <a name="export-the-configuration"></a><span data-ttu-id="336c3-124">匯出設定</span><span class="sxs-lookup"><span data-stu-id="336c3-124">Export the configuration</span></span>

1. <span data-ttu-id="336c3-125">開啟 Microsoft BizTalk Accelerator for SWIFT 組態，然後選取**匯出組態**。</span><span class="sxs-lookup"><span data-stu-id="336c3-125">Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Export Configuration**.</span></span>
2. <span data-ttu-id="336c3-126">在**存**，瀏覽至您要儲存組態檔中，輸入組態檔中，名稱的資料夾，然後**儲存**。</span><span class="sxs-lookup"><span data-stu-id="336c3-126">In **Save As**, browse to the folder where you want to save the configuration file, enter a name for the configuration file, and then **Save**.</span></span>
3. <span data-ttu-id="336c3-127">已成功匯出時選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="336c3-127">When exported successfully, select **OK**.</span></span>

### <a name="import-a-configuration"></a><span data-ttu-id="336c3-128">匯入組態</span><span class="sxs-lookup"><span data-stu-id="336c3-128">Import a configuration</span></span>
1. <span data-ttu-id="336c3-129">開啟 Microsoft BizTalk Accelerator for SWIFT 組態，然後選取**匯入組態**。</span><span class="sxs-lookup"><span data-stu-id="336c3-129">Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Import Configuration**.</span></span>
2. <span data-ttu-id="336c3-130">瀏覽至包含組態檔的資料夾，選取檔案，並選取**匯入**。</span><span class="sxs-lookup"><span data-stu-id="336c3-130">Browse to the folder that contains the configuration file, select the file, and then select **Import**.</span></span>

## <a name="post-configuration-steps"></a><span data-ttu-id="336c3-131">組態後步驟</span><span class="sxs-lookup"><span data-stu-id="336c3-131">Post-configuration steps</span></span>

### <a name="add-users-to-the-a4swift-users-group"></a><span data-ttu-id="336c3-132">將使用者新增至 A4SWIFT 使用者群組</span><span class="sxs-lookup"><span data-stu-id="336c3-132">Add users to the A4SWIFT Users group</span></span>

<span data-ttu-id="336c3-133">設定之後[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]，加入執行 BizTalkServerApplication 主控件執行個體的帳戶**A4SWIFT 使用者**群組 (*不* **A4SWIFT 管理員**群組)。</span><span class="sxs-lookup"><span data-stu-id="336c3-133">After you configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)], add the account that runs the BizTalkServerApplication host instance to the **A4SWIFT Users** group (*not* the **A4SWIFT Administrators** group).</span></span> 

<span data-ttu-id="336c3-134">**步驟**:</span><span class="sxs-lookup"><span data-stu-id="336c3-134">**Steps**:</span></span>

1. <span data-ttu-id="336c3-135">開啟**服務**。</span><span class="sxs-lookup"><span data-stu-id="336c3-135">Open **Services**.</span></span> <span data-ttu-id="336c3-136">服務也會提供**伺服器管理員**，然後**工具**。</span><span class="sxs-lookup"><span data-stu-id="336c3-136">Services is also available in **Server Manager**, and then **Tools**.</span></span> 
2. <span data-ttu-id="336c3-137">在清單中，尋找**BizTalk Service BizTalk Group: BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="336c3-137">In the list, find **BizTalk Service BizTalk Group: BizTalkServerApplication**.</span></span> 
3. <span data-ttu-id="336c3-138">雙選取，開啟其內容。</span><span class="sxs-lookup"><span data-stu-id="336c3-138">Double-select to open its properties.</span></span>
4. <span data-ttu-id="336c3-139">在**登入** 索引標籤時，請注意，使用者帳戶列為**此帳戶**。</span><span class="sxs-lookup"><span data-stu-id="336c3-139">In the **Log On** tab, note the user account listed as **This account**.</span></span>
5. <span data-ttu-id="336c3-140">開啟**本機使用者和群組**（在 電腦管理），然後尋找**A4SWIFT 使用者**群組。</span><span class="sxs-lookup"><span data-stu-id="336c3-140">Open **Local Users and Groups** (in Computer Management), and then find the **A4SWIFT Users** group.</span></span> <span data-ttu-id="336c3-141">將使用者帳戶加入至這個群組。</span><span class="sxs-lookup"><span data-stu-id="336c3-141">Add the user account to this group.</span></span>

> [!TIP] 
> <span data-ttu-id="336c3-142">主控件執行個體帳戶需要存取 BizTalk Server 資料庫主機訊息修復執行階段元件的這個群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="336c3-142">The host instance account needs this group membership for the host Message Repair runtime component to access the BizTalk Server database.</span></span>

### <a name="check-the-identity-of-the-application-pool"></a><span data-ttu-id="336c3-143">檢查應用程式集區身分識別</span><span class="sxs-lookup"><span data-stu-id="336c3-143">Check the identity of the application pool</span></span>
<span data-ttu-id="336c3-144">A4SWIFT_MRSR web 服務裝載於 IIS 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="336c3-144">The A4SWIFT_MRSR web service is hosted in an application in IIS.</span></span> <span data-ttu-id="336c3-145">應用程式集區識別*無法*成網路服務。</span><span class="sxs-lookup"><span data-stu-id="336c3-145">The application pool identity *cannot* be Network Service.</span></span> <span data-ttu-id="336c3-146">應用程式集區身分識別變更為成員的本機或網域帳戶**A4SWIFT 使用者**群組。</span><span class="sxs-lookup"><span data-stu-id="336c3-146">Change the identity of the application pool to a local or domain account that is a member of the **A4SWIFT Users** group.</span></span>

<span data-ttu-id="336c3-147">**步驟**:</span><span class="sxs-lookup"><span data-stu-id="336c3-147">**Steps**:</span></span>

1. <span data-ttu-id="336c3-148">開啟**Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="336c3-148">Open **Internet Information Services Manager**.</span></span> <span data-ttu-id="336c3-149">IIS 管理員也會提供**伺服器管理員**，然後**工具**。</span><span class="sxs-lookup"><span data-stu-id="336c3-149">The IIS Manager is also available in **Server Manager**, and then **Tools**.</span></span> 
2. <span data-ttu-id="336c3-150">展開**Default Web Site**，然後選取 A4SWIFT_MRSR web 服務。</span><span class="sxs-lookup"><span data-stu-id="336c3-150">Expand the **Default Web Site**, and select the A4SWIFT_MRSR web service.</span></span> 
3. <span data-ttu-id="336c3-151">選取**基本設定**。</span><span class="sxs-lookup"><span data-stu-id="336c3-151">Select **Basic Settings**.</span></span> <span data-ttu-id="336c3-152">會列出應用程式集區的名稱。</span><span class="sxs-lookup"><span data-stu-id="336c3-152">The name of the application pool is listed.</span></span>
4. <span data-ttu-id="336c3-153">在左窗格中，選取**應用程式集區**，然後選取 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="336c3-153">In the left pane, select **Application Pools**, and then select your application pool.</span></span>
5. <span data-ttu-id="336c3-154">選取**進階設定**，並變更**識別**視。</span><span class="sxs-lookup"><span data-stu-id="336c3-154">Select **Advanced Settings**, and change the **Identity** if needed.</span></span>