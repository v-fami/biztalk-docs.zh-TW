---
title: "匯入繫結 for TIBCO EMS |Microsoft 文件"
description: "部署您的 BizTalk 配接器在 BizTalk Server 中使用匯入繫結功能的 TIBCO Enterprise Message Service 應用程式"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69dae448-4ec6-4a56-a628-bb447bc21b62
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79f7f3ec0478746b8c2c6762fe212229f9c7b11d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="deploy-tibco-ems-ports-and-assemblies"></a><span data-ttu-id="28b7c-103">部署 TIBCO EMS 通訊埠和組件</span><span class="sxs-lookup"><span data-stu-id="28b7c-103">Deploy TIBCO EMS ports and assemblies</span></span>

## <a name="overview"></a><span data-ttu-id="28b7c-104">概觀</span><span class="sxs-lookup"><span data-stu-id="28b7c-104">Overview</span></span>
<span data-ttu-id="28b7c-105">與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以複製連接埠和組件的目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="28b7c-105">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="28b7c-106">匯出至 XML 檔案傳送埠/接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="28b7c-106"> exports send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="28b7c-107">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="28b7c-107">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="28b7c-108">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="28b7c-108">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="28b7c-109">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="28b7c-109">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="28b7c-110">將 BizTalk 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="28b7c-110">Import or export BizTalk assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="28b7c-111">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="28b7c-111">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28b7c-112">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 只要求來源 (開發) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="28b7c-112">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="28b7c-113">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="28b7c-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="28b7c-114">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="28b7c-114">Confirm your setup</span></span>
<span data-ttu-id="28b7c-115">使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="28b7c-115">Before you use BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="28b7c-116">在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="28b7c-116">The folders for the responses must exist and be identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="28b7c-117">TIBCO Enterprise Message Service 系統密碼 (如果出現在組態中) 必須以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="28b7c-117">TIBCO Enterprise Message Service system passwords, if present in the configuration, must be saved as ***** in the binding file.</span></span> <span data-ttu-id="28b7c-118">請參閱**限制**本主題中。</span><span class="sxs-lookup"><span data-stu-id="28b7c-118">See **Limitations** in this topic.</span></span>


## <a name="clean-the-target-computer"></a><span data-ttu-id="28b7c-119">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="28b7c-119">Clean the target computer</span></span>
<span data-ttu-id="28b7c-120">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="28b7c-120">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="28b7c-121">當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。</span><span class="sxs-lookup"><span data-stu-id="28b7c-121">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  

<span data-ttu-id="28b7c-122">在匯入之前，移除任何傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="28b7c-122">Before you import, remove any send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="28b7c-123">如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="28b7c-123">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs`  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs`
  

<span data-ttu-id="28b7c-124">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="28b7c-124">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## <a name="limitations"></a><span data-ttu-id="28b7c-125">限制</span><span class="sxs-lookup"><span data-stu-id="28b7c-125">Limitations</span></span>
<span data-ttu-id="28b7c-126">「 傳輸配接器 」 密碼儲存為顆星 (\*\*\*\*\*\*) 繫結檔案中，會匯出 BizTalk Server 中，並且會傳遞給在同一個管理元件格式。</span><span class="sxs-lookup"><span data-stu-id="28b7c-126">The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format.</span></span> <span data-ttu-id="28b7c-127">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="28b7c-127">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="28b7c-128">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。</span><span class="sxs-lookup"><span data-stu-id="28b7c-128">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
 <span data-ttu-id="28b7c-129">此為已知的限制狀況。</span><span class="sxs-lookup"><span data-stu-id="28b7c-129">This is a known limitation.</span></span> <span data-ttu-id="28b7c-130">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="28b7c-130">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="28b7c-131">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="28b7c-131">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="28b7c-132">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="28b7c-132">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="28b7c-133">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="28b7c-133">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="28b7c-134">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="28b7c-134">In this case, you must delete the passwords from the binding file after the import operation successfully finishes.</span></span>  
  
 
### <a name="password-limitation-workaround"></a><span data-ttu-id="28b7c-135">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="28b7c-135">Password Limitation Workaround</span></span>  
 <span data-ttu-id="28b7c-136">若要解決這項密碼限制問題，請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="28b7c-136">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="28b7c-137">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。</span><span class="sxs-lookup"><span data-stu-id="28b7c-137">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="28b7c-138">基於安全理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="28b7c-138">This is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="28b7c-139">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="28b7c-139">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="28b7c-140">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。</span><span class="sxs-lookup"><span data-stu-id="28b7c-140">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28b7c-141">只有當目標電腦上安裝了 Visual Studio，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="28b7c-141">This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.</span></span>  
  
-   <span data-ttu-id="28b7c-142">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="28b7c-142">Verify the Logical system and the Transmit and Receive services.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="28b7c-143">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="28b7c-143">Next steps</span></span>
[<span data-ttu-id="28b7c-144">在您的協調流程中使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="28b7c-144">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling5.md)