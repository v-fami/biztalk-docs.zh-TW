---
title: 匯入 BizTalk 配接器適用於 JD Edwards OneWorld |Microsoft Docs
description: 匯入應用程式的繫結檔案，並檢閱 JD Edwards OneWorld 配接器在 BizTalk 中的任何限制
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f308d2fe-39dd-4008-94ed-292c4c26fe06
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ca65c71e14d488b264d861616fe170220ac249b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999215"
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a><span data-ttu-id="15d6c-103">匯入 JD Edwards EnterpriseOne 應用程式</span><span class="sxs-lookup"><span data-stu-id="15d6c-103">Import the JD Edwards EnterpriseOne application</span></span>
  
## <a name="overview"></a><span data-ttu-id="15d6c-104">概觀</span><span class="sxs-lookup"><span data-stu-id="15d6c-104">Overview</span></span>
<span data-ttu-id="15d6c-105">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="15d6c-105">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="15d6c-106">BizTalk Server 會將傳送埠/接收位置組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="15d6c-106">BizTalk Server exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="15d6c-107">您可以使用 BizTalk Server 執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="15d6c-107">You can use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="15d6c-108">在 BizTalk 組態資料庫中部署或移除 BizTalk Server 組件</span><span class="sxs-lookup"><span data-stu-id="15d6c-108">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="15d6c-109">在全域組件快取 (GAC) 中安裝或解除安裝組件</span><span class="sxs-lookup"><span data-stu-id="15d6c-109">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="15d6c-110">將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出</span><span class="sxs-lookup"><span data-stu-id="15d6c-110">Import or export BizTalk Server assembly binding information to and from binding files</span></span>  

<span data-ttu-id="15d6c-111">若要使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要將連接埠和組件的部署，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="15d6c-111">To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15d6c-112">Microsoft BizTalk Adapter for JD Edwards OneWorld 只要求來源 (部署) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="15d6c-112">The Microsoft BizTalk Adapter for JD Edwards OneWorld only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="15d6c-113">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="15d6c-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="15d6c-114">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="15d6c-114">Confirm your setup</span></span>
<span data-ttu-id="15d6c-115">使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="15d6c-115">Before you use the BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="15d6c-116">CLASSPATH 指向 JD Edwards 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="15d6c-116">The CLASSPATH is pointing to a specific location for the JD Edwards-specific files.</span></span> <span data-ttu-id="15d6c-117">確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="15d6c-117">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="15d6c-118">在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="15d6c-118">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="15d6c-119">JD Edwards 系統密碼 (如果出現在組態中) 會以 \*\*\*\*\* 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="15d6c-119">JD Edwards system passwords, if present in the configuration, are saved as \*\*\*\*\* in the binding file.</span></span> <span data-ttu-id="15d6c-120">請參閱**限制**本主題中。</span><span class="sxs-lookup"><span data-stu-id="15d6c-120">See **Limitations** in this topic.</span></span>

  
> [!NOTE]
>  <span data-ttu-id="15d6c-121">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="15d6c-121">Deployment overwrites Receive Location configuration.</span></span> <span data-ttu-id="15d6c-122">在目標電腦上部署繫結檔案 (和組件) 時，傳送埠和接收位置會在匯入時被取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="15d6c-122">When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="15d6c-123">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="15d6c-123">Clean the target computer</span></span>
<span data-ttu-id="15d6c-124">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="15d6c-124">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="15d6c-125">當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。</span><span class="sxs-lookup"><span data-stu-id="15d6c-125">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
<span data-ttu-id="15d6c-126">在匯入之前，移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="15d6c-126">Before you import, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="15d6c-127">如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="15d6c-127">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="15d6c-128">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="15d6c-128">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="15d6c-129">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="15d6c-129">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
<span data-ttu-id="15d6c-130">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="15d6c-130">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="limitations"></a><span data-ttu-id="15d6c-131">限制</span><span class="sxs-lookup"><span data-stu-id="15d6c-131">Limitations</span></span>
<span data-ttu-id="15d6c-132">傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 中的繫結檔案匯出 BizTalk 部署精靈 」，並傳遞給管理在相同的格式中的元件。</span><span class="sxs-lookup"><span data-stu-id="15d6c-132">The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format.</span></span> <span data-ttu-id="15d6c-133">繫結檔案前先行編輯匯入的星號取代成隨機英數字元值 （也就是不正確的密碼）。</span><span class="sxs-lookup"><span data-stu-id="15d6c-133">Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password).</span></span> <span data-ttu-id="15d6c-134">然後輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。</span><span class="sxs-lookup"><span data-stu-id="15d6c-134">Then enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
 <span data-ttu-id="15d6c-135">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="15d6c-135">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="15d6c-136">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="15d6c-136">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="15d6c-137">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="15d6c-137">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="15d6c-138">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="15d6c-138">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="15d6c-139">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="15d6c-139">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15d6c-140">匯入到.msi 檔案時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含企業配接器之繫結資訊的應用程式可能會收到匯入錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="15d6c-140">When importing an .msi file into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="15d6c-141">支援的 hotfix 可從 Microsoft 以及在錯誤的完整描述[ http://support.microsoft.com/kb/923733/en-us ](http://support.microsoft.com/kb/923733/en-us)。</span><span class="sxs-lookup"><span data-stu-id="15d6c-141">A supported hotfix is available from Microsoft along with a full description of the error at [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).</span></span>  
  
### <a name="work-around-the-password-limitation"></a><span data-ttu-id="15d6c-142">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="15d6c-142">Work around the password limitation</span></span>  

<span data-ttu-id="15d6c-143">**選項 1**</span><span class="sxs-lookup"><span data-stu-id="15d6c-143">**Option 1**</span></span>  

- <span data-ttu-id="15d6c-144">您匯入之前，更新繫結檔案，並以純文字取代星號。</span><span class="sxs-lookup"><span data-stu-id="15d6c-144">Before you import, update the binding file by replacing the asterisks with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="15d6c-145">基於安全理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="15d6c-145">This is not recommended for security reasons.</span></span>  
  
- <span data-ttu-id="15d6c-146">在匯入之前，更新繫結檔案星號取代為某些垃圾值 （也就是不正確的密碼）。</span><span class="sxs-lookup"><span data-stu-id="15d6c-146">Before you import, update the binding file by replacing the asterisks with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="15d6c-147">您匯入之後，請輸入正確的密碼使用**傳輸屬性**。</span><span class="sxs-lookup"><span data-stu-id="15d6c-147">After you import, enter the correct password using the **Transport Properties**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15d6c-148">只有當目標電腦上安裝了 Microsoft Visual Studio，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="15d6c-148">This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.</span></span>  
  
<span data-ttu-id="15d6c-149">**選項 2**</span><span class="sxs-lookup"><span data-stu-id="15d6c-149">**Option 2**</span></span>  
  
1.  <span data-ttu-id="15d6c-150">不使用密碼，改為使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="15d6c-150">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="15d6c-151">使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。</span><span class="sxs-lookup"><span data-stu-id="15d6c-151">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="15d6c-152">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="15d6c-152">Verify the Logical system and the Transmit and Receive services.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="15d6c-153">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="15d6c-153">Next steps</span></span>
[<span data-ttu-id="15d6c-154">使用 協調流程中的 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="15d6c-154">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling1.md)