---
title: "使用 Siebel 配接器疑難排解安裝問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, installation
- installation, troubleshooting
ms.assetid: f9f066d9-37b6-4a18-9f60-d0931ea91a18
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff49285df7e43103f2ad7441cbc82b96bb59eaa4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-siebel-adapter"></a><span data-ttu-id="464ce-102">使用 Siebel 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="464ce-102">Troubleshoot Installation Issues with the Siebel adapter</span></span>
<span data-ttu-id="464ce-103">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上安裝，並註冊每個配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="464ce-103">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="464ce-104">本章節將討論解決安裝錯誤的疑難排解技術。</span><span class="sxs-lookup"><span data-stu-id="464ce-104">This section discusses troubleshooting techniques to resolve installation errors.</span></span>  
  
## <a name="setup-logging"></a><span data-ttu-id="464ce-105">安裝程式記錄</span><span class="sxs-lookup"><span data-stu-id="464ce-105">Setup Logging</span></span>  
 <span data-ttu-id="464ce-106">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="464ce-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="464ce-107">此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="464ce-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="464ce-108">您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="464ce-108">You can log messages for both the standard as well as custom actions performed by the setup.</span></span>  
  
-   <span data-ttu-id="464ce-109">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。</span><span class="sxs-lookup"><span data-stu-id="464ce-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter specific files using an MSI.</span></span> <span data-ttu-id="464ce-110">因此，安裝程式的記錄將會是標準的 MSI 記錄。</span><span class="sxs-lookup"><span data-stu-id="464ce-110">Hence, the logging for the setup will be the standard MSI logging.</span></span>  
  
-   <span data-ttu-id="464ce-111">安裝程式所執行的自訂動作的記錄檔位於 %temp%\adaptersetup.log。</span><span class="sxs-lookup"><span data-stu-id="464ce-111">Logs for the custom actions performed by the setup program are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="464ce-112">如果失敗的追蹤記錄檔，追蹤也會提供事件記錄檔中的。</span><span class="sxs-lookup"><span data-stu-id="464ce-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="464ce-113">已知問題</span><span class="sxs-lookup"><span data-stu-id="464ce-113">Known Issues</span></span>  
  
### <a name="setup-fails-to-register-adapter-bindings"></a><span data-ttu-id="464ce-114">安裝程式無法註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="464ce-114">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="464ce-115">**問題**</span><span class="sxs-lookup"><span data-stu-id="464ce-115">**Problem**</span></span>  
  
 <span data-ttu-id="464ce-116">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結或[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，但會繼續進行配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="464ce-116">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding or the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="464ce-117">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="464ce-117">**Cause**</span></span>  
  
 <span data-ttu-id="464ce-118">這可能會造成與 WCF 安裝問題[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config。</span><span class="sxs-lookup"><span data-stu-id="464ce-118">This might result due to problems with WCF installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config being corrupt.</span></span> <span data-ttu-id="464ce-119">配接器繫結會寫入至 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="464ce-119">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="464ce-120">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="464ce-120">**Resolution**</span></span>  
  
<span data-ttu-id="464ce-121">手動註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結和[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="464ce-121">Manually register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding and [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] using the following steps:</span></span> 
  
1.  <span data-ttu-id="464ce-122">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="464ce-122">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="464ce-123">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="464ce-123">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="464ce-124">在此路徑中\<版本\>是.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="464ce-124">In this path, \<version\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="464ce-125">開啟檔案，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="464ce-125">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="464ce-126">若要註冊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="464ce-126">To register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="464ce-127">搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="464ce-127">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="464ce-128">搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="464ce-128">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="464ce-129">尋找遺漏[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="464ce-129">Look for the missing [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding.</span></span> <span data-ttu-id="464ce-130">新增下列區段，"bindingElementExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="464ce-130">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="464ce-131">如[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="464ce-131">For [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="464ce-132">搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="464ce-132">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="464ce-133">尋找遺漏[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="464ce-133">Look for the missing [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding.</span></span> <span data-ttu-id="464ce-134">新增下列各節的 「 bindingExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="464ce-134">Add the following sections under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="464ce-135">如[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="464ce-135">For [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="464ce-136">如需如何判斷公開金鑰資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="464ce-136">For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="464ce-137">若要註冊[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="464ce-137">To register the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="464ce-138">搜尋項目 DbProviderFactories system.data 節點下。</span><span class="sxs-lookup"><span data-stu-id="464ce-138">Search for the element DbProviderFactories under the system.data node.</span></span>  
  
    2.  <span data-ttu-id="464ce-139">尋找遺漏[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="464ce-139">Look for the missing [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span> <span data-ttu-id="464ce-140">新增下列區段，DbProviderFactories 節點下。</span><span class="sxs-lookup"><span data-stu-id="464ce-140">Add the following section under the DbProviderFactories node.</span></span>  
  
         <span data-ttu-id="464ce-141">如[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="464ce-141">For [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="464ce-142">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="464ce-142">Save and close the machine.config file.</span></span>  
  
####  <a name="BKMK_PubKey"></a><span data-ttu-id="464ce-143">判斷公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="464ce-143">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="464ce-144">執行下列步驟來判斷公開金鑰[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]或[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="464ce-144">Perform the following steps to determine the public key for [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] or [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span>  
  
###### <a name="to-determine-the-public-key"></a><span data-ttu-id="464ce-145">判斷公開金鑰</span><span class="sxs-lookup"><span data-stu-id="464ce-145">To determine the public key</span></span>  
  
1.  <span data-ttu-id="464ce-146">瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="464ce-146">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="464ce-147">以滑鼠右鍵按一下您想公開索引鍵，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="464ce-147">Right-click the DLL for which you want the public key and select **Properties**.</span></span> <span data-ttu-id="464ce-148">下表列出每個配接器和提供者 Dll 的名稱。</span><span class="sxs-lookup"><span data-stu-id="464ce-148">The following table lists the name of the DLLs for each adapter and provider.</span></span>  
  
    |<span data-ttu-id="464ce-149">配接器/ADO 提供者</span><span class="sxs-lookup"><span data-stu-id="464ce-149">Adapter/ADO Provider</span></span>|<span data-ttu-id="464ce-150">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="464ce-150">Name of the DLL</span></span>|  
    |---------------------------|---------------------|  
    |[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="464ce-151">Microsoft.Adapters.Siebel</span><span class="sxs-lookup"><span data-stu-id="464ce-151">Microsoft.Adapters.Siebel</span></span>|  
    |[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="464ce-152">Microsoft.Data.SiebelClient</span><span class="sxs-lookup"><span data-stu-id="464ce-152">Microsoft.Data.SiebelClient</span></span>|  
  
3.  <span data-ttu-id="464ce-153">在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="464ce-153">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="464ce-154">同樣地，針對值**版本**標籤指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="464ce-154">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="464ce-155">複製的公開金鑰，然後按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="464ce-155">Copy the public key, and then click **Cancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464ce-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="464ce-156">See Also</span></span>  
[<span data-ttu-id="464ce-157">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="464ce-157">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)