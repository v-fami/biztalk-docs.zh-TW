---
title: 更新或解除安裝 BizTalk Adapter Pack 2016 |Microsoft Docs
description: 使用安裝精靈 」 或 msiexec 變更，或解除安裝 BizTalk Server; 隨附的 BAP 2016包括移除繫結和移除自訂 Rfc
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3d6c001-1005-4d7b-a143-eaa37b48f898
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eef0252a2907287c3197d40558d605f5c9f5660e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981863"
---
# <a name="update-or-uninstall-the-biztalk-adapter-pack-2016"></a><span data-ttu-id="1be97-103">更新或解除安裝 BizTalk Adapter Pack 2016</span><span class="sxs-lookup"><span data-stu-id="1be97-103">Update or uninstall the BizTalk Adapter Pack 2016</span></span>
<span data-ttu-id="1be97-104">如何變更或解除安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1be97-104">How to change or uninstall the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>

<a name="BKMK_Modify_Adap"></a>
## <a name="change-or-update-the-installation"></a><span data-ttu-id="1be97-105">變更或更新安裝</span><span class="sxs-lookup"><span data-stu-id="1be97-105">Change or update the installation</span></span>  
<span data-ttu-id="1be97-106">執行安裝精靈來修改之前[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，請確定[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1be97-106">Before you run the setup wizard to modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] is installed.</span></span> 
  
 <span data-ttu-id="1be97-107">您可以修改的安裝以互動模式 （安裝程式精靈），或以無訊息模式 （命令列）。</span><span class="sxs-lookup"><span data-stu-id="1be97-107">You can modify the installation in interactive mode (the setup wizard), or in silent mode (the command line).</span></span>
  
### <a name="use-the-setup-wizard"></a><span data-ttu-id="1be97-108">使用安裝精靈</span><span class="sxs-lookup"><span data-stu-id="1be97-108">Use the setup wizard</span></span>  
  
1. <span data-ttu-id="1be97-109">使用 BizTalk Server 系統管理員群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="1be97-109">Sign in with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2. <span data-ttu-id="1be97-110">在 **程式和功能**，選取**解除安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="1be97-110">In **Programs and features**, select **Uninstall a program**.</span></span>  
  
3. <span data-ttu-id="1be97-111">以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="1be97-111">Right-click **Microsoft BizTalk Adapter Pack**, and then select **Change**.</span></span>  
  
4. <span data-ttu-id="1be97-112">在 歡迎 畫面中，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1be97-112">On the Welcome screen, select **Next**.</span></span>  
  
5. <span data-ttu-id="1be97-113">在 **變更、 修復或移除安裝**:</span><span class="sxs-lookup"><span data-stu-id="1be97-113">In **Change, repair, or remove installation**:</span></span>  
  
   - <span data-ttu-id="1be97-114">若要選取您想要安裝的元件，請選取**變更**並移至步驟 6。</span><span class="sxs-lookup"><span data-stu-id="1be97-114">To select the components you want to install, select **Change** and go to Step 6.</span></span>  
  
   - <span data-ttu-id="1be97-115">若要修復最近安裝中的錯誤，請選取**修復**並移至步驟 7。</span><span class="sxs-lookup"><span data-stu-id="1be97-115">To repair errors in the most recent installation, select **Repair** and go to Step 7.</span></span>  
  
   - <span data-ttu-id="1be97-116">若要移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從電腦中，選取**移除**然後移至步驟 10。</span><span class="sxs-lookup"><span data-stu-id="1be97-116">To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from the computer, select **Remove** and then go to Step 10.</span></span>  
  
6. <span data-ttu-id="1be97-117">如果您選擇修改安裝：</span><span class="sxs-lookup"><span data-stu-id="1be97-117">If you chose to modify the installation:</span></span>  
  
   -   <span data-ttu-id="1be97-118">依序展開**Microsoft BizTalk Adapter Pack**節點，選擇要安裝的基底介面卡、.NET Framework 資料提供者，或兩者。</span><span class="sxs-lookup"><span data-stu-id="1be97-118">Expand the **Microsoft BizTalk Adapter Pack** node to choose to install the base adapters, the .NET Framework Data Providers, or both.</span></span>  
  
   -   <span data-ttu-id="1be97-119">依序展開**基底配接器**節點，選擇要安裝的所有配接器或特定的配接器。</span><span class="sxs-lookup"><span data-stu-id="1be97-119">Expand the **Base Adapters** node to choose to install all the adapters or specific adapters.</span></span>  
  
   -   <span data-ttu-id="1be97-120">依序展開**ADO 提供者**節點，選擇要安裝的所有提供者或特定的提供者。</span><span class="sxs-lookup"><span data-stu-id="1be97-120">Expand the **ADO Providers** node to choose to install all the providers or specific providers.</span></span>  
  
   -   <span data-ttu-id="1be97-121">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1be97-121">Select **Next**.</span></span>  
  
   -   <span data-ttu-id="1be97-122">選取 **變更**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="1be97-122">Select **Change**, and then select **Finish**.</span></span>  
  
7. <span data-ttu-id="1be97-123">如果您選擇修復安裝，在**準備好修復 Microsoft BizTalk Adapter Pack**對話方塊中，選取**修復**。</span><span class="sxs-lookup"><span data-stu-id="1be97-123">If you chose to repair the installation, in the **Ready to repair Microsoft BizTalk Adapter Pack** dialog box, select **Repair**.</span></span> <span data-ttu-id="1be97-124">精靈會啟動修復安裝。</span><span class="sxs-lookup"><span data-stu-id="1be97-124">The wizard starts repairing the installation.</span></span>  
  
8. <span data-ttu-id="1be97-125">如有需要，變更您的喜好設定有關選擇加入 ceip，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="1be97-125">If required, change your preferences regarding opting for CEIP, and then select **OK**.</span></span> 
  
9. <span data-ttu-id="1be97-126">選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="1be97-126">Select **Finish**.</span></span>  
  
10. <span data-ttu-id="1be97-127">如果您選擇要移除介面卡，在**準備好移除 Microsoft BizTalk Adapter Pack**對話方塊中，選取**移除**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="1be97-127">If you chose to remove the adapters, in the **Ready to remove Microsoft BizTalk Adapter Pack** dialog box, select **Remove**, and then select **Finish**.</span></span>  
  
### <a name="use-msiexec-in-silent-mode"></a><span data-ttu-id="1be97-128">以無訊息模式使用 msiexec</span><span class="sxs-lookup"><span data-stu-id="1be97-128">Use msiexec in silent mode</span></span>  
  
1. <span data-ttu-id="1be97-129">開啟命令提示字元，並移至根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="1be97-129">Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.</span></span>  
  
2. <span data-ttu-id="1be97-130">執行命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1be97-130">Run a command similar to the following:</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="1be97-131">若要修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]上的 x64 型的平台，在下列命令中，以無訊息模式安裝取代`AdaptersSetup.msi`使用`AdaptersSetup64.msi`。</span><span class="sxs-lookup"><span data-stu-id="1be97-131">To modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in a silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.</span></span>  
  
   ```  
   msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
   ```  
  
    <span data-ttu-id="1be97-132">此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，並安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1be97-132">This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], and installs the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span></span>  
  
    <span data-ttu-id="1be97-133">使用不同的值，如`REMOVE`和`ADDLOCAL`屬性，您可以新增或移除特定的元件。</span><span class="sxs-lookup"><span data-stu-id="1be97-133">By using different values for the `REMOVE` and `ADDLOCAL` properties, you can add or remove specific components.</span></span> <span data-ttu-id="1be97-134">中的資料表是指**在無訊息模式中安裝**在[安裝 BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)如需您可以使用這些屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1be97-134">Refer to the table in **Install in silent mode** at [Installing BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) for information about the values that you can use for these properties.</span></span>  
  
    <span data-ttu-id="1be97-135">您也可以使用 msiexec 命令的 [/f] 選項，以執行無訊息的修復。</span><span class="sxs-lookup"><span data-stu-id="1be97-135">You can also do a silent repair by using the /f option as part of the msiexec command.</span></span> <span data-ttu-id="1be97-136">例如：</span><span class="sxs-lookup"><span data-stu-id="1be97-136">For example:</span></span>  
  
   ```  
   msiexec /i AdaptersSetup.msi /qn /f  
   ```  
  
    <span data-ttu-id="1be97-137">/F 選項，您可以使用各種不同的組合。</span><span class="sxs-lookup"><span data-stu-id="1be97-137">You can use various different combinations with the /f option.</span></span> <span data-ttu-id="1be97-138">如需有關 msiexec 命令型別`msiexec`上的命令列和按`ENTER`。</span><span class="sxs-lookup"><span data-stu-id="1be97-138">For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="1be97-139">或移至[ http://go.microsoft.com/fwlink/p/?LinkId=103199 ](http://go.microsoft.com/fwlink/p/?LinkId=103199)。</span><span class="sxs-lookup"><span data-stu-id="1be97-139">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="1be97-140">同時修改[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式安裝，您無法變更您的喜好設定選擇參與或退出 CEIP。</span><span class="sxs-lookup"><span data-stu-id="1be97-140">While modifying the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="1be97-141">選擇在安裝仍在即使您明確地設定為 true 或 false CEIP_OPTIN 喜好設定。</span><span class="sxs-lookup"><span data-stu-id="1be97-141">The preferences you chose during the installation remains, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  

## <a name="uninstall-or-remove-the-biztalk-adapter-pack"></a><span data-ttu-id="1be97-142">解除安裝或移除 BizTalk Adapter Pack</span><span class="sxs-lookup"><span data-stu-id="1be97-142">Uninstall or remove the BizTalk Adapter Pack</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1be97-143">如果您使用的 tRFC 功能的 SQL Server 資料庫中建立資料表[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，您必須解除安裝之前，手動移除它們[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1be97-143">If you created tables in the SQL Server database to work with the tRFC feature of the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], you must manually remove them before uninstalling the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="1be97-144">[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝複本`SapAdapter-DbScript-Uninstall.sql`檔案通常位於*\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* 。</span><span class="sxs-lookup"><span data-stu-id="1be97-144">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation copies a `SapAdapter-DbScript-Uninstall.sql` file typically at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]*.</span></span> <span data-ttu-id="1be97-145">執行這個檔案來移除您所建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="1be97-145">Run this file to remove the tables you created.</span></span>  
  
<span data-ttu-id="1be97-146">完成下列步驟來移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="1be97-146">Complete the following steps to remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from your computer.</span></span> <span data-ttu-id="1be97-147">請確定您有[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]之前執行安裝精靈安裝。</span><span class="sxs-lookup"><span data-stu-id="1be97-147">Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard.</span></span>  
  
 <span data-ttu-id="1be97-148">您可以移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以互動模式 （安裝程式精靈），或以無訊息模式 （命令列）。</span><span class="sxs-lookup"><span data-stu-id="1be97-148">You can remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode (setup wizard), or in silent mode (command line).</span></span>
  
### <a name="uninstall-using-the-setup-wizard"></a><span data-ttu-id="1be97-149">使用安裝精靈解除安裝</span><span class="sxs-lookup"><span data-stu-id="1be97-149">Uninstall using the setup wizard</span></span>  
  
1.  <span data-ttu-id="1be97-150">在 **程式和功能**，選取**解除安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="1be97-150">In **Programs and features**, select **Uninstall a program**.</span></span>  
  
2.  <span data-ttu-id="1be97-151">以滑鼠右鍵按一下**Microsoft BizTalk Adapter Pack**，然後選取**解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="1be97-151">Right-click **Microsoft BizTalk Adapter Pack**, and then select **Uninstall**.</span></span>  
  
### <a name="uninstall-in-silent-mode"></a><span data-ttu-id="1be97-152">解除安裝以無訊息模式</span><span class="sxs-lookup"><span data-stu-id="1be97-152">Uninstall in silent mode</span></span>  
  
1. <span data-ttu-id="1be97-153">開啟命令提示字元，並移至根目錄[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="1be97-153">Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.</span></span>  
  
2. <span data-ttu-id="1be97-154">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1be97-154">Run the following command:</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="1be97-155">若要移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在無訊息模式的 x64 型的平台，在下列命令中，將`AdaptersSetup.msi`使用`AdaptersSetup64.msi`。</span><span class="sxs-lookup"><span data-stu-id="1be97-155">To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.</span></span>  
  
   ```  
   msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
   ```  
  
    <span data-ttu-id="1be97-156">此命令會移除[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1be97-156">This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span>  
  
    <span data-ttu-id="1be97-157">藉由提供不同的值，如`REMOVE`屬性，您可以移除特定的元件，從[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1be97-157">By providing different values for the `REMOVE` property, you can remove specific components from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span> <span data-ttu-id="1be97-158">中的資料表是指**在無訊息模式中安裝**在[安裝 BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)如需您可以使用這個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1be97-158">Refer to the table in **Install in silent mode** at [Installing BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) for information about the values that you can use for this property.</span></span>  
  
    <span data-ttu-id="1be97-159">若要完全移除[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1be97-159">To completely remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], execute the following command:</span></span>  
  
   ```  
   msiexec /x AdaptersSetup.msi /qn  
   ```  
  
    <span data-ttu-id="1be97-160">如需有關 msiexec 命令型別`msiexec`上的命令列和按`ENTER`。</span><span class="sxs-lookup"><span data-stu-id="1be97-160">For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="1be97-161">或移至[ http://go.microsoft.com/fwlink/p/?LinkId=103199 ](http://go.microsoft.com/fwlink/p/?LinkId=103199)。</span><span class="sxs-lookup"><span data-stu-id="1be97-161">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>
  
## <a name="remove-the-bindings"></a><span data-ttu-id="1be97-162">移除繫結</span><span class="sxs-lookup"><span data-stu-id="1be97-162">Remove the bindings</span></span>  
 <span data-ttu-id="1be97-163">完成這些步驟*只*如果安裝精靈 無法移除 machine.config 檔案中的配接器繫結或.NET Framework 資料提供者註冊。</span><span class="sxs-lookup"><span data-stu-id="1be97-163">Complete these steps *only* if the setup wizard fails to remove the adapter bindings or .NET Framework Data Provider registration from the machine.config file.</span></span>  
  
1. <span data-ttu-id="1be97-164">請移至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="1be97-164">Go to the machine.config file on the computer.</span></span> <span data-ttu-id="1be97-165">例如，32 位元平台上，machine.config 位於底下*\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG*。</span><span class="sxs-lookup"><span data-stu-id="1be97-165">For example, on a 32-bit platform, the machine.config is available under *\<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG*.</span></span>  
  
2. <span data-ttu-id="1be97-166">開啟使用文字編輯器的檔案。</span><span class="sxs-lookup"><span data-stu-id="1be97-166">Open the file using a text editor.</span></span>  
  
3. <span data-ttu-id="1be97-167">移除配接器繫結註冊：</span><span class="sxs-lookup"><span data-stu-id="1be97-167">Remove the adapter binding registration:</span></span>  
  
   1. <span data-ttu-id="1be97-168">搜尋`system.serviceModel`項目，並移除下列項目底下：</span><span class="sxs-lookup"><span data-stu-id="1be97-168">Search for the `system.serviceModel` element, and remove the following from under the element:</span></span>  
  
      ```  
      <client>  
        <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
  
      ```  
  
   2. <span data-ttu-id="1be97-169">搜尋`bindingElementExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="1be97-169">Search for the `bindingElementExtensions` element under system.serviceModel\extensions.</span></span>  
  
   3. <span data-ttu-id="1be97-170">移除下列各節下的`bindingElementExtensions`節點，根據可用的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="1be97-170">Remove the following sections under the `bindingElementExtensions` node, depending on the available adapter binding.</span></span> <span data-ttu-id="1be97-171">若要移除任何安裝精靈時，您必須移除所有繫結。</span><span class="sxs-lookup"><span data-stu-id="1be97-171">You must remove all the bindings if the setup wizard fails to remove any.</span></span>  
  
       <span data-ttu-id="1be97-172">針對[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-172">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:</span></span>  
  
      ```  
      <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-173">針對[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-173">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:</span></span>  
  
      ```  
      <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-174">針對[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-174">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:</span></span>  
  
      ```  
      <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-175">針對[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-175">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:</span></span>  
  
      ```  
      <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-176">針對[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-176">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
   4. <span data-ttu-id="1be97-177">搜尋`bindingExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="1be97-177">Search for the `bindingExtensions` element under system.serviceModel\extensions.</span></span>  
  
   5. <span data-ttu-id="1be97-178">移除下列各節下的`bindingExtensions`節點，根據可用的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="1be97-178">Remove the following sections under the `bindingExtensions` node, depending on the available adapter binding.</span></span> <span data-ttu-id="1be97-179">若要移除任何安裝精靈時，您必須移除所有繫結。</span><span class="sxs-lookup"><span data-stu-id="1be97-179">You must remove all the bindings if the setup wizard fails to remove any.</span></span>  
  
       <span data-ttu-id="1be97-180">針對[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-180">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:</span></span>  
  
      ```  
      <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-181">針對[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-181">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:</span></span>  
  
      ```  
      <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-182">針對[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-182">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:</span></span>  
  
      ```  
      <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-183">針對[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-183">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:</span></span>  
  
      ```  
      <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       <span data-ttu-id="1be97-184">針對[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-184">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
4. <span data-ttu-id="1be97-185">移除.NET Framework 資料提供者註冊：</span><span class="sxs-lookup"><span data-stu-id="1be97-185">Remove the .NET Framework Data Provider registration:</span></span>  
  
   - <span data-ttu-id="1be97-186">搜尋`DbProviderFactories`system.data 節點下的項目。</span><span class="sxs-lookup"><span data-stu-id="1be97-186">Search for the `DbProviderFactories` element under the system.data node.</span></span>  
  
   - <span data-ttu-id="1be97-187">尋找仍註冊.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="1be97-187">Look for the .NET Framework Data Providers that are still registered.</span></span> <span data-ttu-id="1be97-188">移除下列各節下的`DbProviderFactories`節點，根據現有的.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="1be97-188">Remove the following sections under the `DbProviderFactories` node, depending on the existing .NET Framework Data Providers.</span></span> <span data-ttu-id="1be97-189">如果有的話，您必須移除所有的提供者。</span><span class="sxs-lookup"><span data-stu-id="1be97-189">You must remove all the providers if they exist.</span></span>  
  
      <span data-ttu-id="1be97-190">針對[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-190">For [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], remove:</span></span>  
  
     ```  
     <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
         description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
     ```  
  
      <span data-ttu-id="1be97-191">針對[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，移除：</span><span class="sxs-lookup"><span data-stu-id="1be97-191">For [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], remove:</span></span>  
  
     ```  
     <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
         description=".NET Framework Data Provider for Siebel eBusiness Applications"  
         type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
     ```  
  
5. <span data-ttu-id="1be97-192">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="1be97-192">Save and close the machine.config file.</span></span>  
  
## <a name="remove-the-custom-rfcs"></a><span data-ttu-id="1be97-193">移除自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="1be97-193">Remove the custom RFCs</span></span>  
<span data-ttu-id="1be97-194">完成此步驟才能移除您在 SAP 系統中安裝的自訂 Rfc。</span><span class="sxs-lookup"><span data-stu-id="1be97-194">Complete this step to remove the custom RFCs that you installed in the SAP system.</span></span> <span data-ttu-id="1be97-195">請參閱[安裝或移除自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="1be97-195">See [Install or remove custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
