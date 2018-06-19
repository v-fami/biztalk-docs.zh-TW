---
title: 安裝錯誤訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation, error message
- error messages, installation
ms.assetid: 593b033f-03da-43ae-a948-f87aa5e4bccd
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ec99a2e9f20b09c4daddad0336037c7f539782a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971916"
---
# <a name="installation-error-message"></a><span data-ttu-id="ce282-102">安裝錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="ce282-102">Installation Error Message</span></span>
<span data-ttu-id="ce282-103">安裝 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 之後，定義其傳送或接收位置時，可能會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ce282-103">After you install Microsoft BizTalk Adapter for TIBCO Enterprise Message Service, defining a send or receive location for it might result in the following error:</span></span>  
  
 <span data-ttu-id="ce282-104">「 傳訊引擎無法將接收 URL"\<傳送/接收位置 URL\>」 配接器"TIBCO EMS"。</span><span class="sxs-lookup"><span data-stu-id="ce282-104">The Messaging Engine failed to add a receive URL "\< send/receive location URL\>" to the adapter "TIBCO EMS".</span></span> <span data-ttu-id="ce282-105">原因: 「 檔案或組件名稱 TIBCO。EMS，或其中一個相依性，找不到。 」</span><span class="sxs-lookup"><span data-stu-id="ce282-105">Reason: "File or assembly name TIBCO.EMS, or one of its dependencies, was not found."</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="ce282-106">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ce282-106">Possible Causes</span></span>  
 <span data-ttu-id="ce282-107">這個錯誤通常是因為下列其中一個原因造成。</span><span class="sxs-lookup"><span data-stu-id="ce282-107">This error usually has one of the following causes.</span></span>  
  
### <a name="assembly-not-in-gac"></a><span data-ttu-id="ce282-108">組件不在 GAC 中</span><span class="sxs-lookup"><span data-stu-id="ce282-108">Assembly Not in GAC</span></span>  
 <span data-ttu-id="ce282-109">BizTalk Adapter for TIBCO EMS 是 .NET Framework 應用程式，因此會使用 .NET Framework 組件 TIBCO.EMS。</span><span class="sxs-lookup"><span data-stu-id="ce282-109">BizTalk Adapter for TIBCO EMS is a .NET Framework application, and uses the .NET Framework assembly, TIBCO.EMS.</span></span> <span data-ttu-id="ce282-110">此組件必須位於 .NET Framework 全域組件快取 (GAC) 中，.NET Framework 在執行階段才能找到它。</span><span class="sxs-lookup"><span data-stu-id="ce282-110">This assembly must be present in the .NET Framework global assembly cache (GAC) for the .NET Framework to find it at run time.</span></span>  
  
#### <a name="solution"></a><span data-ttu-id="ce282-111">方案</span><span class="sxs-lookup"><span data-stu-id="ce282-111">Solution</span></span>  
 <span data-ttu-id="ce282-112">若要判斷組件是否位於 GAC 中，請開啟命令提示字元，然後輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ce282-112">To determine if the assembly is present in the GAC, open a command prompt and type the following command:</span></span>  
  
 `GACUTIL /L TIBCO.EMS`  
  
 <span data-ttu-id="ce282-113">如果結果沒有顯示任何項目，則您必須將組件加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="ce282-113">If the result shows zero items, you must add the assembly to the GAC.</span></span> <span data-ttu-id="ce282-114">若要執行這項操作，請開啟命令提示字元，將目錄變更為您的 TIBCO EMS 安裝用戶端\cs 目錄 (預設安裝位置為 C:\TIBCO\EMS\Clients\CS)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ce282-114">To do this, open a command prompt, change directories to your TIBCO EMS installation clients\cs directory (the default installation location is C:\TIBCO\EMS\Clients\CS), and run the following command:</span></span>  
  
 `GACUTIL /i TIBCO.EMS.DLL`  
  
### <a name="different-version-of-assembly-in-gac"></a><span data-ttu-id="ce282-115">GAC 中有不同版本的組件</span><span class="sxs-lookup"><span data-stu-id="ce282-115">Different Version of Assembly in GAC</span></span>  
 <span data-ttu-id="ce282-116">TIBCO.EMS.dll 組件位於 GAC 中，但它的版本不同於用來建置 BizTalk Adapter for TIBCO EMS 的版本。</span><span class="sxs-lookup"><span data-stu-id="ce282-116">The TIBCO.EMS.dll assembly is in the GAC, but it is a different version from the one used to build BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="ce282-117">如果安裝在電腦上的 TIBCO.EMS.dll 是產品版本 4.2 (含) 以上版本，則它應該能與用來建置配接器的版本相容 (您可以向 TIBCO 確認此資訊)。</span><span class="sxs-lookup"><span data-stu-id="ce282-117">If the TIBCO.EMS.dll that is installed on the computer is from a product version 4.2 or above, it should be compatible with the version used to build the adapter (you can verify that information with TIBCO).</span></span>  
  
#### <a name="solution"></a><span data-ttu-id="ce282-118">方案</span><span class="sxs-lookup"><span data-stu-id="ce282-118">Solution</span></span>  
 <span data-ttu-id="ce282-119">.NET Framework 已提供方法來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="ce282-119">The .NET Framework provides a way to work around this problem.</span></span> <span data-ttu-id="ce282-120">它會呼叫*繫結重新導向*，它會使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="ce282-120">It is called *binding redirection*, which uses a configuration file.</span></span>  
  
 <span data-ttu-id="ce282-121">請執行下列步驟來避免錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="ce282-121">Follow these steps to eliminate the error message:</span></span>  
  
1.  <span data-ttu-id="ce282-122">使用任何文字編輯器開啟 BTSNTSVC.exe.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce282-122">With any text editor, open the file BTSNTSVC.exe.config.</span></span>  
  
     <span data-ttu-id="ce282-123">此檔案位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]目錄 (預設安裝位置是： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="ce282-123">The file is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directory (the default installation location is: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).</span></span>  
  
2.  <span data-ttu-id="ce282-124">做為子系，將下列項目加入至 BTSNTSVC.exe.config 檔， \<assemblyBinding\>項目：</span><span class="sxs-lookup"><span data-stu-id="ce282-124">Add the following entry to the BTSNTSVC.exe.config file, as a child of the \<assemblyBinding\> element:</span></span>  
  
```  
<dependentAssembly>  
    <assemblyIdentity name='TIBCO.EMS'  
        publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
    <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
        newVersion='1.0.0.0' />  
</dependentAssembly>  
```  
  
 <span data-ttu-id="ce282-125">如果先前尚未修改 BTSNTSVC.exe.config 檔案， \<assemblyBinding\>項目不會看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="ce282-125">If the BTSNTSVC.exe.config file has not been previously modified, the \<assemblyBinding\> element would not look like this:</span></span>  
  
```  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
    <probing privatePath="BizTalk Assemblies;Developer  
        Tools;Tracking;Tracking\interop" />  
    <dependentAssembly>  
        <assemblyIdentity name='TIBCO.EMS'  
            publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
        <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
            newVersion='1.0.0.0' />  
    </dependentAssembly>  
</assemblyBinding>  
```  
  
1.  <span data-ttu-id="ce282-126">在命令提示字元中輸入命令： `GACUTIL /L TIBCO.EMS`。</span><span class="sxs-lookup"><span data-stu-id="ce282-126">In a command prompt, type the command: `GACUTIL /L TIBCO.EMS`.</span></span>  
  
2.  <span data-ttu-id="ce282-127">從輸出複製 TIBCO.EMS 組件版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ce282-127">Copy the TIBCO.EMS assembly version number from the output.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="ce282-128">會出現兩個版本號碼： 其中一個是 gacutil 公用程式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ce282-128">Two version numbers appear: one is the version number of the gacutil utility.</span></span> <span data-ttu-id="ce282-129">您想出現後方的第二個版本號碼**版本 =**。</span><span class="sxs-lookup"><span data-stu-id="ce282-129">You want the second version number, which appears just after **Version=**.</span></span>  
  
3.  <span data-ttu-id="ce282-130">貼上之後的版本號碼，在 BTSNTSVC.exe.config 檔案中，加上引號， **newVersion =** （粗體上述 XML 範例中的字元）。</span><span class="sxs-lookup"><span data-stu-id="ce282-130">Paste the version number in the BTSNTSVC.exe.config file, between the quotation marks, right after **newVersion=** (bold characters in the previous XML example).</span></span>  
  
4.  <span data-ttu-id="ce282-131">儲存已修改的 BTSNTSVC.exe.config 檔。</span><span class="sxs-lookup"><span data-stu-id="ce282-131">Save the modified BTSNTSVC.exe.config file.</span></span>  
  
5.  <span data-ttu-id="ce282-132">重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件。</span><span class="sxs-lookup"><span data-stu-id="ce282-132">Restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce282-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce282-133">See Also</span></span>  
 [<span data-ttu-id="ce282-134">TIBCO Enterprise Message Service 疑難排解</span><span class="sxs-lookup"><span data-stu-id="ce282-134">Troubleshooting TIBCO Enterprise Message Service</span></span>](../core/troubleshooting-tibco-enterprise-message-service.md)