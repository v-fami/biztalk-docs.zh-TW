---
title: "疑難排解安裝問題的 Oracle 資料庫配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation issues, troubleshooting
- troubleshooting, installation issues
ms.assetid: 2054b725-d657-4039-b83b-119571935f62
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dc2603a2e86d29797919fb51c3985c384ff9580
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-installation-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="4a3c9-102">疑難排解安裝問題的 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="4a3c9-102">Troubleshoot installation issues with the Oracle Database adapter</span></span>
<span data-ttu-id="4a3c9-103">安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="4a3c9-104">本節討論如何使用來解決安裝錯誤的疑難排解技術，也會列出一些已知的問題。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-104">This section discusses using troubleshooting techniques to resolve installation errors, and also lists some known issues.</span></span>  
  
## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="4a3c9-105">安裝程式動作的記錄訊息</span><span class="sxs-lookup"><span data-stu-id="4a3c9-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="4a3c9-106">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="4a3c9-107">此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="4a3c9-108">您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  
  
-   <span data-ttu-id="4a3c9-109">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝在使用 MSI 的配接器特定檔案。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="4a3c9-110">因此，安裝程式的記錄是標準的 MSI 記錄。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-110">Therefore, the logging for the setup is the standard MSI logging.</span></span> 
  
-   <span data-ttu-id="4a3c9-111">安裝程式會執行自訂動作的所有記錄檔位於 %temp%\adaptersetup.log。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-111">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="4a3c9-112">如果失敗的追蹤記錄檔，追蹤也會提供事件記錄檔中的。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
##  <a name="BKMK_OraDBBinding"></a><span data-ttu-id="4a3c9-113">安裝程式無法註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="4a3c9-113">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="4a3c9-114">**問題**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-114">**Problem**</span></span>  
  
 <span data-ttu-id="4a3c9-115">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈無法註冊配接器繫結，但會繼續進行配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-115">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="4a3c9-116">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-116">**Cause**</span></span>  
  
 <span data-ttu-id="4a3c9-117">這可能會因為發生問題造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-117">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="4a3c9-118">配接器繫結會寫入至 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-118">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="4a3c9-119">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-119">**Resolution**</span></span>  
  
<span data-ttu-id="4a3c9-120">手動註冊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-120">Manually register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:</span></span> 
  
1.  <span data-ttu-id="4a3c9-121">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-121">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="4a3c9-122">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-122">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="4a3c9-123">在此路徑中\<版本\>是.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-123">In this path, \<version\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="4a3c9-124">使用文字編輯器開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-124">Open the file by using a text editor.</span></span>  
  
3.  <span data-ttu-id="4a3c9-125">若要註冊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-125">To register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="4a3c9-126">搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-126">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="4a3c9-127">搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-127">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="4a3c9-128">尋找遺漏[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-128">Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding.</span></span> <span data-ttu-id="4a3c9-129">新增下列區段，"bindingElementExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-129">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="4a3c9-130">如[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-130">For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="4a3c9-131">搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-131">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="4a3c9-132">尋找遺漏[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-132">Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding.</span></span> <span data-ttu-id="4a3c9-133">新增下列區段，"bindingExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-133">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="4a3c9-134">如[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-134">For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4a3c9-135">如需如何判斷公開金鑰和版本資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-135">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="4a3c9-136">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-136">Save and close the machine.config file.</span></span>  
  
####  <a name="BKMK_PubKey"></a><span data-ttu-id="4a3c9-137">判斷公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="4a3c9-137">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="4a3c9-138">執行下列步驟來判斷公開金鑰[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-138">Perform the following steps to determine the public key for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
1.  <span data-ttu-id="4a3c9-139">瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-139">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="4a3c9-140">以滑鼠右鍵按一下您想要的公開金鑰和版本，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-140">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="4a3c9-141">下表列出的 DLL 名稱[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-141">The following table lists the name of the DLL for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
    |<span data-ttu-id="4a3c9-142">配接器</span><span class="sxs-lookup"><span data-stu-id="4a3c9-142">Adapter</span></span>|<span data-ttu-id="4a3c9-143">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="4a3c9-143">Name of the DLL</span></span>|  
    |-------------|---------------------|  
    |[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]|<span data-ttu-id="4a3c9-144">Microsoft.Adapters.OracleDB</span><span class="sxs-lookup"><span data-stu-id="4a3c9-144">Microsoft.Adapters.OracleDB</span></span>|  
  
3.  <span data-ttu-id="4a3c9-145">在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-145">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="4a3c9-146">同樣地，針對值**版本**標籤指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-146">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="4a3c9-147">複製的公開金鑰，然後按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-147">Copy the public key, and then click **Cancel**.</span></span>  
  
##  <a name="BKMK_ConsumeBinding"></a><span data-ttu-id="4a3c9-148">使用 64 位元安裝上使用配接器服務增益集或加入配接器服務參考外掛程式時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="4a3c9-148">Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="4a3c9-149">**問題**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-149">**Problem**</span></span>  
  
 <span data-ttu-id="4a3c9-150">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-150">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  
  
```  
No valid adapters are installed on this machine  
```  
  
 <span data-ttu-id="4a3c9-151">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-151">**Cause**</span></span>  
  
 <span data-ttu-id="4a3c9-152">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-152">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="4a3c9-153">64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-153">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="4a3c9-154">因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-154">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="4a3c9-155">不過，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查 machine.config 檔案的 32 位元版本中的繫結和失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-155">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="4a3c9-156">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-156">**Resolution**</span></span>  
  
-   <span data-ttu-id="4a3c9-157">同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-157">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a3c9-158">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-158">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="4a3c9-159">由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-159">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="4a3c9-160">安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-160">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a3c9-161">若要確定您的應用程式的運作方式與 ODP.NET 的最新版本，您必須使用"原則 DLLs"的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-161">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="4a3c9-162">如需詳細資訊，請參閱[適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 的網站上。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-162">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.</span></span>  
  
##  <a name="BKMK_InvalidBinding"></a><span data-ttu-id="4a3c9-163">無效的繫結時發生的 64 位元安裝上設定 BizTalk Server 管理主控台中的 Oracle 資料庫配接器連接埠</span><span class="sxs-lookup"><span data-stu-id="4a3c9-163">Invalid binding error while configuring Oracle database adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="4a3c9-164">**問題**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-164">**Problem**</span></span>  
  
 <span data-ttu-id="4a3c9-165">當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="4a3c9-165">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleDBBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 <span data-ttu-id="4a3c9-166">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-166">**Cause**</span></span>  
  
 <span data-ttu-id="4a3c9-167">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-167">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="4a3c9-168">64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-168">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="4a3c9-169">因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-169">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="4a3c9-170">不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台執行以 32 位元處理序，因此當您設定配接器的連接埠，它會檢查 machine.config 檔案的 32 位元版本中的繫結而會失敗，提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-170">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="4a3c9-171">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="4a3c9-171">**Resolution**</span></span>  
  
-   <span data-ttu-id="4a3c9-172">同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-172">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a3c9-173">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-173">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="4a3c9-174">由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-174">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="4a3c9-175">安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-175">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a3c9-176">若要確定您的應用程式的運作方式與 ODP.NET 的最新版本，您必須使用"原則 DLLs"的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-176">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="4a3c9-177">如需詳細資訊，請參閱[適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 網站上。</span><span class="sxs-lookup"><span data-stu-id="4a3c9-177">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle website.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="4a3c9-178">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a3c9-178">See Also</span></span>  
[<span data-ttu-id="4a3c9-179">Oracle 資料庫配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="4a3c9-179">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)