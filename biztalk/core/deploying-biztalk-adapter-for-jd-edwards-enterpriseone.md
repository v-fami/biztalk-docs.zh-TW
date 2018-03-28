---
title: JD Edwards EnterpriseOne 應用程式匯入 |Microsoft 文件
description: 確認安裝、 匯入應用程式的繫結檔案，以及檢閱 JD Edwards EnterpriseOne 配接器在 BizTalk 的限制
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 852f948b-48ba-4ae2-b1eb-7c88c1542a52
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55374c87192c993e26cc11cb496d89074d527868
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a><span data-ttu-id="8ff61-103">JD Edwards EnterpriseOne 應用程式匯入</span><span class="sxs-lookup"><span data-stu-id="8ff61-103">Import the JD Edwards EnterpriseOne application</span></span>
  
## <a name="overview"></a><span data-ttu-id="8ff61-104">概觀</span><span class="sxs-lookup"><span data-stu-id="8ff61-104">Overview</span></span>
<span data-ttu-id="8ff61-105">與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以複製連接埠和組件的目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="8ff61-105">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8ff61-106"> 傳送埠/接收位置將組態匯出成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8ff61-106"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="8ff61-107">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="8ff61-107">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="8ff61-108">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件</span><span class="sxs-lookup"><span data-stu-id="8ff61-108">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="8ff61-109">在全域組件快取 (GAC) 中安裝或解除安裝組件</span><span class="sxs-lookup"><span data-stu-id="8ff61-109">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="8ff61-110">將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將之從繫結檔案中匯出</span><span class="sxs-lookup"><span data-stu-id="8ff61-110">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files</span></span>  
  
<span data-ttu-id="8ff61-111">若要使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8ff61-111">To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ff61-112">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 只要求來源 (程式開發) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="8ff61-112">The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="8ff61-113">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8ff61-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="8ff61-114">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="8ff61-114">Confirm your setup</span></span>
<span data-ttu-id="8ff61-115">使用 BizTalk Server 匯入繫結檔案之前，必須確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="8ff61-115">Before you use the BizTalk Server to import a binding file, you must verify the following:</span></span>  
  
-   <span data-ttu-id="8ff61-116">CLASSPATH 指向 JD Edwards EnterpriseOne 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="8ff61-116">The CLASSPATH is pointing to a specific location for the JD Edwards EnterpriseOne-specific files.</span></span> <span data-ttu-id="8ff61-117">確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="8ff61-117">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="8ff61-118">在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="8ff61-118">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="8ff61-119">JD Edwards EnterpriseOne 系統密碼 (如果出現在組態中) 以 \*\*\*\*\* 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="8ff61-119">JD Edwards EnterpriseOne system passwords, if present in the configuration, are saved as \*\*\*\*\* in the binding file.</span></span> <span data-ttu-id="8ff61-120">如需詳細資訊，請參閱**限制**本主題中。</span><span class="sxs-lookup"><span data-stu-id="8ff61-120">For more information, see **Limitations** in this topic.</span></span>

## <a name="clean-the-target-computer"></a><span data-ttu-id="8ff61-121">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="8ff61-121">Clean the target computer</span></span>
<span data-ttu-id="8ff61-122">當您在目標電腦上重新部署繫結檔案 (和組件)，傳送埠和接收位置會在重新匯入 XML 繫結檔案時，被取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="8ff61-122">When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.</span></span>  
  
<span data-ttu-id="8ff61-123">在匯入之前，移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="8ff61-123">Before you import, remove Send ports and Receive locations bound to the orchestration.</span></span> <span data-ttu-id="8ff61-124">如果目標電腦上未安裝 Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="8ff61-124">If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8ff61-125">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="8ff61-125">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8ff61-126">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="8ff61-126">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  

<span data-ttu-id="8ff61-127">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="8ff61-127">For example, from a command prompt run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
## <a name="limitations"></a><span data-ttu-id="8ff61-128">限制</span><span class="sxs-lookup"><span data-stu-id="8ff61-128">Limitations</span></span>
<span data-ttu-id="8ff61-129">「傳輸配接器」密碼以星號 (******) 儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出的繫結檔案中，並且會以相同格式傳遞給管理元件。</span><span class="sxs-lookup"><span data-stu-id="8ff61-129">The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span> <span data-ttu-id="8ff61-130">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="8ff61-130">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span>  
  
 <span data-ttu-id="8ff61-131">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="8ff61-131">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="8ff61-132">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="8ff61-132">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="8ff61-133">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="8ff61-133">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span>  
  
 <span data-ttu-id="8ff61-134">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="8ff61-134">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="8ff61-135">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="8ff61-135">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
### <a name="work-around-the-password-limitation"></a><span data-ttu-id="8ff61-136">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="8ff61-136">Work around the password limitation</span></span>  
  
1.  <span data-ttu-id="8ff61-137">不使用密碼，改為使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="8ff61-137">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="8ff61-138">使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。</span><span class="sxs-lookup"><span data-stu-id="8ff61-138">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="8ff61-139">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="8ff61-139">Verify the Logical system and the Transmit and Receive services.</span></span>  


## <a name="next-steps"></a><span data-ttu-id="8ff61-140">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="8ff61-140">Next steps</span></span>
[<span data-ttu-id="8ff61-141">在您的協調流程中使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="8ff61-141">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling3.md)