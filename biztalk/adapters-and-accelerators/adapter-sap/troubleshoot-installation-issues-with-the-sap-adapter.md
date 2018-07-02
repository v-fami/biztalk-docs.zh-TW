---
title: 使用 SAP 配接器疑難排解安裝問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, installation
- installation, troubleshooting
ms.assetid: fdfdaf44-c32d-43a5-998d-02032c0b9211
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a72a5e2da055a9e4137e3e8954b72ad32cde40db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982727"
---
# <a name="troubleshoot-installation-issues-with-the-sap-adapter"></a><span data-ttu-id="62289-102">使用 SAP 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="62289-102">Troubleshoot Installation Issues with the SAP adapter</span></span>
<span data-ttu-id="62289-103">安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="62289-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="62289-104">本章節將討論解決安裝錯誤的疑難排解技巧。</span><span class="sxs-lookup"><span data-stu-id="62289-104">This section discusses troubleshooting techniques to resolve installation errors.</span></span>  

## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="62289-105">安裝動作的記錄訊息</span><span class="sxs-lookup"><span data-stu-id="62289-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="62289-106">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62289-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="62289-107">此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="62289-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="62289-108">您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="62289-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  

- <span data-ttu-id="62289-109">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。</span><span class="sxs-lookup"><span data-stu-id="62289-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter specific files using an MSI.</span></span> <span data-ttu-id="62289-110">因此，安裝程式記錄是標準的 MSI 記錄。</span><span class="sxs-lookup"><span data-stu-id="62289-110">Hence, the logging for the setup is the standard MSI logging.</span></span>  

- <span data-ttu-id="62289-111">安裝程式會執行自訂動作的記錄檔位於 %temp%\adaptersetup.log。</span><span class="sxs-lookup"><span data-stu-id="62289-111">Logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="62289-112">如果記錄檔追蹤失敗，追蹤也有事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="62289-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  

##  <a name="BKMK_SAPSetupBinding"></a> <span data-ttu-id="62289-113">安裝程式無法註冊配接器繫結或資料提供者</span><span class="sxs-lookup"><span data-stu-id="62289-113">Setup fails to register adapter bindings or data providers</span></span>  
 <span data-ttu-id="62289-114">**問題**</span><span class="sxs-lookup"><span data-stu-id="62289-114">**Problem**</span></span>  

 <span data-ttu-id="62289-115">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊配接器繫結或[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，但會繼續進行配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="62289-115">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings or the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], but proceeds with the adapter installation.</span></span>  

 <span data-ttu-id="62289-116">**原因**</span><span class="sxs-lookup"><span data-stu-id="62289-116">**Cause**</span></span>  

 <span data-ttu-id="62289-117">因為有問題，這可能會造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝，[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="62289-117">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="62289-118">配接器繫結會寫入至 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="62289-118">The adapter bindings are written to the machine.config file.</span></span>  

 <span data-ttu-id="62289-119">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="62289-119">**Resolution**</span></span>  

 <span data-ttu-id="62289-120">您應該手動註冊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結或[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62289-120">You should manually register the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding or the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  

### <a name="register-the-adapter-bindings-or-the-data-provider"></a><span data-ttu-id="62289-121">註冊配接器繫結或資料提供者</span><span class="sxs-lookup"><span data-stu-id="62289-121">Register the adapter bindings or the data provider</span></span>  

1. <span data-ttu-id="62289-122">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="62289-122">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="62289-123">例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="62289-123">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  

    <span data-ttu-id="62289-124">在此路徑中，\<版本\>是.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="62289-124">In this path, \<version\> is the version of the .NET Framework.</span></span>  

2. <span data-ttu-id="62289-125">開啟使用文字編輯器的檔案。</span><span class="sxs-lookup"><span data-stu-id="62289-125">Open the file using a text editor.</span></span>  

3. <span data-ttu-id="62289-126">若要註冊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="62289-126">To register the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding:</span></span>  

   1. <span data-ttu-id="62289-127">搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="62289-127">Search for the element "system.serviceModel" and add the following under it:</span></span>  

      ```  
      <client>  
        <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
      </client>  
      ```  

   2. <span data-ttu-id="62289-128">搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="62289-128">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  

   3. <span data-ttu-id="62289-129">尋找遺漏[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="62289-129">Look for the missing [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding.</span></span> <span data-ttu-id="62289-130">新增"bindingElementExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="62289-130">Add the following section under the "bindingElementExtensions" node.</span></span>  

       <span data-ttu-id="62289-131">針對[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="62289-131">For [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], add:</span></span>  

      ```  
      <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. <span data-ttu-id="62289-132">搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="62289-132">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  

   5. <span data-ttu-id="62289-133">尋找遺漏[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="62289-133">Look for the missing [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding.</span></span> <span data-ttu-id="62289-134">新增"bindingExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="62289-134">Add the following section under the "bindingExtensions" node.</span></span>  

       <span data-ttu-id="62289-135">針對[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="62289-135">For [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], add:</span></span>  

      ```  
      <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

      > [!NOTE]
      >  <span data-ttu-id="62289-136">如需如何判斷公開金鑰的資訊，請參閱[判斷的公開金鑰和版本](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="62289-136">For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  

4. <span data-ttu-id="62289-137">若要註冊[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="62289-137">To register the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span></span>  

   1. <span data-ttu-id="62289-138">搜尋"system.data 」 節點下的項目 」 DbProviderFactories"。</span><span class="sxs-lookup"><span data-stu-id="62289-138">Search for the element "DbProviderFactories" under the "system.data" node.</span></span>  

   2. <span data-ttu-id="62289-139">尋找遺漏[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62289-139">Look for the missing [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="62289-140">新增"DbProviderFactories 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="62289-140">Add the following section under the "DbProviderFactories" node.</span></span>  

       <span data-ttu-id="62289-141">針對[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="62289-141">For [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], add:</span></span>  

      ```  
      <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient" description=".NET Framework Data Provider for mySAP Business Suite" type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

5. <span data-ttu-id="62289-142">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="62289-142">Save and close the machine.config file.</span></span>  

###  <a name="BKMK_PubKey"></a> <span data-ttu-id="62289-143">判斷的公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="62289-143">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="62289-144">執行下列步驟來判斷的公開金鑰[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]或[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62289-144">Perform the following steps to determine the public key for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] or [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  

1. <span data-ttu-id="62289-145">瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="62289-145">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  

2. <span data-ttu-id="62289-146">以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="62289-146">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="62289-147">下表列出的 Dll 名稱[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62289-147">The following table lists the name of the DLLs for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  


   |                           <span data-ttu-id="62289-148">配接器/資料提供者</span><span class="sxs-lookup"><span data-stu-id="62289-148">Adapter/Data Provider</span></span>                           |     <span data-ttu-id="62289-149">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="62289-149">Name of the DLL</span></span>      |
   |---------------------------------------------------------------------------|--------------------------|
   |    [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]    |  <span data-ttu-id="62289-150">Microsoft.Adapters.SAP</span><span class="sxs-lookup"><span data-stu-id="62289-150">Microsoft.Adapters.SAP</span></span>  |
   | [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] | <span data-ttu-id="62289-151">Microsoft.Data.SAPClient</span><span class="sxs-lookup"><span data-stu-id="62289-151">Microsoft.Data.SAPClient</span></span> |


3. <span data-ttu-id="62289-152">在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="62289-152">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="62289-153">同樣地，針對值**版本**標籤都會指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="62289-153">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  

4. <span data-ttu-id="62289-154">複製公開金鑰，然後再按**取消**。</span><span class="sxs-lookup"><span data-stu-id="62289-154">Copy the public key, and then click **Cancel**.</span></span>  

##  <a name="BKMK_SAPConsumeBinding"></a> <span data-ttu-id="62289-155">沒有有效的配接器是已安裝的錯誤</span><span class="sxs-lookup"><span data-stu-id="62289-155">No valid adapters are installed error</span></span>

 <span data-ttu-id="62289-156">**問題**</span><span class="sxs-lookup"><span data-stu-id="62289-156">**Problem**</span></span>  

 <span data-ttu-id="62289-157">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="62289-157">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  

```  
No valid adapters are installed on this machine  
```  

 <span data-ttu-id="62289-158">**原因**</span><span class="sxs-lookup"><span data-stu-id="62289-158">**Cause**</span></span>  

 <span data-ttu-id="62289-159">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="62289-159">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="62289-160">64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="62289-160">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="62289-161">所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="62289-161">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="62289-162">不過， [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查是否有 32 位元版本的 machine.config 檔案中的繫結和失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="62289-162">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  

 <span data-ttu-id="62289-163">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="62289-163">**Resolution**</span></span>  

- <span data-ttu-id="62289-164">同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="62289-164">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="62289-165">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="62289-165">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="62289-166">並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="62289-166">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  

- <span data-ttu-id="62289-167">加入這兩個 32 位元和 64 位元版本的用戶端 Dll [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] （例如 librfc32u.dll) 至 PATH 變數。</span><span class="sxs-lookup"><span data-stu-id="62289-167">Add both the 32-bit and 64-bit versions of the client DLLs for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (such as librfc32u.dll) to the PATH variable.</span></span> <span data-ttu-id="62289-168">32 位元版本的 dll 必須加入至 C:\Windows\SysWow64 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="62289-168">The 32-bit version of the DLLs must be added to C:\Windows\SysWow64 folder.</span></span> <span data-ttu-id="62289-169">64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="62289-169">The 64-bit version of the DLLs must be added to C:\Windows\System32 folder.</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="62289-170">如果配接器 （32 或 64 位元） 執行 64 位元作業系統的電腦上，而且您用來撰寫應用程式配接器，您應該將標示要與相同類型 （32 或 64 位元） 配接器的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62289-170">If the adapter (32 or 64-bit) is running on a computer that has a 64-bit operating system, and you are using the adapter to write an application, you should mark the application to the same type (32 or 64-bit) as the adapter.</span></span> <span data-ttu-id="62289-171">此外，RFC SDK （32 或 64 位元） 的版本必須是相同的版本 （32 或 64 位元） 的介面卡。</span><span class="sxs-lookup"><span data-stu-id="62289-171">Also, the version of the RFC SDK (32 or 64-bit) must be same as the version of the adapter (32 or 64-bit).</span></span>  
  >   
  >  <span data-ttu-id="62289-172">例如，如果使用 64 位元作業系統的電腦上執行 32 位元的配接器，配接器用戶端應用程式必須標示為 32 位元。</span><span class="sxs-lookup"><span data-stu-id="62289-172">For example, if a 32-bit adapter is running on a computer with a 64-bit operating system, the adapter client application must be marked as 32-bit.</span></span>  

   <span data-ttu-id="62289-173">如需有關 SAP 用戶端 Dll 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="62289-173">For more information about the SAP client DLLs, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  

##  <a name="BKMK_SAPInvalidBinding"></a> <span data-ttu-id="62289-174">設定 SAP 配接器連接埠時發生的不正確的繫結錯誤</span><span class="sxs-lookup"><span data-stu-id="62289-174">Invalid binding error while configuring SAP adapter ports</span></span>  
 <span data-ttu-id="62289-175">**問題**</span><span class="sxs-lookup"><span data-stu-id="62289-175">**Problem**</span></span>  

 <span data-ttu-id="62289-176">當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="62289-176">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  

```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sapBinding".  
Verify the binding extension is registered in machine.config."  
```  

 <span data-ttu-id="62289-177">**原因**</span><span class="sxs-lookup"><span data-stu-id="62289-177">**Cause**</span></span>  

 <span data-ttu-id="62289-178">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="62289-178">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="62289-179">64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="62289-179">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="62289-180">所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="62289-180">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="62289-181">不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中執行做為 32 位元處理序，並因此當您設定配接器的連接埠時，它會檢查 machine.config 檔案的 32 位元版本中的繫結並失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="62289-181">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  

 <span data-ttu-id="62289-182">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="62289-182">**Resolution**</span></span>  

- <span data-ttu-id="62289-183">同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="62289-183">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="62289-184">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="62289-184">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="62289-185">並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="62289-185">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  

- <span data-ttu-id="62289-186">加入這兩個 32 位元和 64 位元版本的用戶端 Dll [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] （例如 librfc32u.dll) 至 PATH 變數。</span><span class="sxs-lookup"><span data-stu-id="62289-186">Add both the 32-bit and 64-bit versions of the client DLLs for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (such as librfc32u.dll) to the PATH variable.</span></span> <span data-ttu-id="62289-187">32 位元版本的 dll 必須加入至 C:\Windows\SysWow64 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="62289-187">The 32-bit version of the DLLs must be added to C:\Windows\SysWow64 folder.</span></span> <span data-ttu-id="62289-188">64 位元版本的 dll 必須新增到 C:\Windows\System32 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="62289-188">The 64-bit version of the DLLs must be added to C:\Windows\System32 folder.</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="62289-189">如果配接器 （32 或 64 位元） 執行 64 位元作業系統的電腦上，而且您用來撰寫應用程式配接器，您應該將標示要與相同類型 （32 或 64 位元） 配接器的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62289-189">If the adapter (32 or 64-bit) is running on a computer that has a 64-bit operating system, and you are using the adapter to write an application, you should mark the application to the same type (32 or 64-bit) as the adapter.</span></span> <span data-ttu-id="62289-190">此外，RFC SDK （32 或 64 位元） 的版本必須是相同的版本 （32 或 64 位元） 的介面卡。</span><span class="sxs-lookup"><span data-stu-id="62289-190">Also, the version of the RFC SDK (32 or 64-bit) must be same as the version of the adapter (32 or 64-bit).</span></span>  
  >   
  >  <span data-ttu-id="62289-191">例如，如果使用 64 位元作業系統的電腦上執行 32 位元的配接器，配接器用戶端應用程式必須標示為 32 位元。</span><span class="sxs-lookup"><span data-stu-id="62289-191">For example, if a 32-bit adapter is running on a computer with a 64-bit operating system, the adapter client application must be marked as 32-bit.</span></span>  

   <span data-ttu-id="62289-192">如需有關 SAP 用戶端 Dll 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="62289-192">For more information about the SAP client DLLs, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62289-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62289-193">See Also</span></span>  
[<span data-ttu-id="62289-194">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="62289-194">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)