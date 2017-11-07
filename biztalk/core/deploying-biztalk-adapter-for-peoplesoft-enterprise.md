---
title: "PeopleSoft 應用程式匯入 |Microsoft 文件"
description: "您的 PeopleSoft 配接器應用程式匯入到 BizTalk Server 使用 XML 繫結檔案，而讀取的任何限制，當匯入"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f53d1b4-e1df-41ff-b554-1bb1d20b9111
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dad4639c8432b5b9cc61935afadb0703a363045
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="deploy-biztalk-adapter-for-peoplesoft-enterprise"></a><span data-ttu-id="4334e-103">部署 BizTalk Adapter for PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="4334e-103">Deploy BizTalk Adapter for PeopleSoft Enterprise</span></span>
<span data-ttu-id="4334e-104">本節提供有關部署 BizTalk Adapter for PeopleSoft Enterprise 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4334e-104">This section provides information about deploying BizTalk Adapter for PeopleSoft Enterprise.</span></span>  

## <a name="overview"></a><span data-ttu-id="4334e-105">概觀</span><span class="sxs-lookup"><span data-stu-id="4334e-105">Overview</span></span>
<span data-ttu-id="4334e-106">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="4334e-106">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4334e-107">傳送埠/接收位置將組態匯出成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4334e-107"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="4334e-108">您會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="4334e-108">You use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform these tasks:</span></span>  
  
-   <span data-ttu-id="4334e-109">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="4334e-109">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="4334e-110">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="4334e-110">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="4334e-111">將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="4334e-111">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files.</span></span>  
  
<span data-ttu-id="4334e-112">若要使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4334e-112">To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4334e-113">Microsoft BizTalk Adapter for PeopleSoft Enterprise 只要求來源 (開發) 電腦上必須有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4334e-113">The Microsoft BizTalk Adapter for PeopleSoft Enterprise only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="4334e-114">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4334e-114">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="4334e-115">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="4334e-115">Confirm your setup</span></span>
<span data-ttu-id="4334e-116">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="4334e-116">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="4334e-117">CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="4334e-117">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="4334e-118">確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="4334e-118">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="4334e-119">在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="4334e-119">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="4334e-120">PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="4334e-120">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="4334e-121">請參閱**限制**本主題中。</span><span class="sxs-lookup"><span data-stu-id="4334e-121">See **Limitations** in this topic.</span></span>

> [!NOTE]
>  <span data-ttu-id="4334e-122">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="4334e-122">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="4334e-123">當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="4334e-123">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="4334e-124">如需有關匯入繫結檔案的逐步指示，請參閱[如何匯入繫結至 BizTalk 群組](../core/how-to-import-bindings-into-a-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="4334e-124">For step-by-step directions about importing binding files, see [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md).</span></span> 
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="4334e-125">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="4334e-125">Clean the target computer</span></span>
<span data-ttu-id="4334e-126">若要清除目標電腦，部署新的應用程式、 移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="4334e-126">To clean the target computer for deploying the new application, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="4334e-127">如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="4334e-127">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
<span data-ttu-id="4334e-128">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="4334e-128">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
<span data-ttu-id="4334e-129">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**</span><span class="sxs-lookup"><span data-stu-id="4334e-129">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
<span data-ttu-id="4334e-130">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="4334e-130">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name>
```

## <a name="limitations"></a><span data-ttu-id="4334e-131">限制</span><span class="sxs-lookup"><span data-stu-id="4334e-131">Limitations</span></span>
<span data-ttu-id="4334e-132">傳輸配接器 」 密碼以星號 （*） 儲存在繫結檔案匯出的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並且會傳遞給管理元件，在相同的格式。</span><span class="sxs-lookup"><span data-stu-id="4334e-132">The Transport Adapter password is stored as asterisks (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span>  
  
 <span data-ttu-id="4334e-133">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="4334e-133">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="4334e-134">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="4334e-134">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="4334e-135">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4334e-135">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="4334e-136">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="4334e-136">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="4334e-137">在這種情況下，匯入作業完成後您必須刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="4334e-137">In this case, you must delete the passwords from the binding file after the import operation finishes.</span></span>  
  

### <a name="work-around-the-password-limitation"></a><span data-ttu-id="4334e-138">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="4334e-138">Work around the password limitation</span></span>  

<span data-ttu-id="4334e-139">**選項 1**</span><span class="sxs-lookup"><span data-stu-id="4334e-139">**Option 1**</span></span>   
  
-   <span data-ttu-id="4334e-140">在匯入之前，更新繫結檔案以純文字取代星號。</span><span class="sxs-lookup"><span data-stu-id="4334e-140">Before you import, update the binding file by replacing the asterisks with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="4334e-141">基於安全性理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="4334e-141">This practice is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="4334e-142">您匯入之前，先更新星號取代為某些垃圾值 （也就是不正確的密碼） 的繫結 fileby。</span><span class="sxs-lookup"><span data-stu-id="4334e-142">Before you import, update the binding fileby replacing the asterisks with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="4334e-143">您匯入後，請輸入正確的密碼中**傳輸屬性**BizTalk Server 管理 中。</span><span class="sxs-lookup"><span data-stu-id="4334e-143">After you import, enter the correct password in the **Transport Properties** in BizTalk Server Administration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4334e-144">只有當目標電腦上安裝了 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="4334e-144">This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.</span></span>  
  
<span data-ttu-id="4334e-145">**選項 2**</span><span class="sxs-lookup"><span data-stu-id="4334e-145">**Option 2**</span></span>  
  
-   <span data-ttu-id="4334e-146">不使用密碼，改為使用「企業單一登入」(SSO)。</span><span class="sxs-lookup"><span data-stu-id="4334e-146">Use Enterprise Single Sign-On (SSO) instead of using passwords.</span></span> <span data-ttu-id="4334e-147">使用 SSO 選項需要先匯入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="4334e-147">Using the SSO option requires an import of the binding file.</span></span>  
  
- <span data-ttu-id="4334e-148">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="4334e-148">Verify the logical system and the Transmit and Receive services.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="4334e-149">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="4334e-149">Next steps</span></span>
[<span data-ttu-id="4334e-150">在您的協調流程中使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="4334e-150">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling2.md)