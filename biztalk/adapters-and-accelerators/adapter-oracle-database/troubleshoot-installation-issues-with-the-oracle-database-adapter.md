---
title: 針對使用 Oracle 資料庫配接器的安裝問題進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation issues, troubleshooting
- troubleshooting, installation issues
ms.assetid: 2054b725-d657-4039-b83b-119571935f62
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fff4cc7948bd05043de9d9028b2c2a39bf940b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975959"
---
# <a name="troubleshoot-installation-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="1f6f2-102">針對使用 Oracle 資料庫配接器的安裝問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1f6f2-102">Troubleshoot installation issues with the Oracle Database adapter</span></span>
<span data-ttu-id="1f6f2-103">安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="1f6f2-104">本節討論如何使用來解決安裝錯誤的疑難排解技巧，並且也列出一些已知的問題。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-104">This section discusses using troubleshooting techniques to resolve installation errors, and also lists some known issues.</span></span>  

## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="1f6f2-105">安裝動作的記錄訊息</span><span class="sxs-lookup"><span data-stu-id="1f6f2-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="1f6f2-106">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="1f6f2-107">此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="1f6f2-108">您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  

- <span data-ttu-id="1f6f2-109">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="1f6f2-110">因此，安裝程式記錄是標準的 MSI 記錄。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-110">Therefore, the logging for the setup is the standard MSI logging.</span></span> 

- <span data-ttu-id="1f6f2-111">安裝程式會執行自訂動作的所有記錄檔位於 %temp%\adaptersetup.log。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-111">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="1f6f2-112">如果記錄檔追蹤失敗，追蹤也有事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-112">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  

##  <a name="BKMK_OraDBBinding"></a> <span data-ttu-id="1f6f2-113">安裝程式無法註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="1f6f2-113">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="1f6f2-114">**問題**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-114">**Problem**</span></span>  

 <span data-ttu-id="1f6f2-115">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊配接器繫結，但會繼續進行配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-115">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  

 <span data-ttu-id="1f6f2-116">**原因**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-116">**Cause**</span></span>  

 <span data-ttu-id="1f6f2-117">因為有問題，這可能會造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝，[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-117">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="1f6f2-118">配接器繫結會寫入至 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-118">The adapter bindings are written to the machine.config file.</span></span>  

 <span data-ttu-id="1f6f2-119">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-119">**Resolution**</span></span>  

<span data-ttu-id="1f6f2-120">手動註冊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-120">Manually register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:</span></span> 

1. <span data-ttu-id="1f6f2-121">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-121">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="1f6f2-122">例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-122">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  

    <span data-ttu-id="1f6f2-123">在此路徑中，\<版本\>是.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-123">In this path, \<version\> is the version of the .NET Framework.</span></span>  

2. <span data-ttu-id="1f6f2-124">使用文字編輯器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-124">Open the file by using a text editor.</span></span>  

3. <span data-ttu-id="1f6f2-125">若要註冊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-125">To register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:</span></span>  

   1. <span data-ttu-id="1f6f2-126">搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-126">Search for the element "system.serviceModel" and add the following under it:</span></span>  

      ```  
      <client>  
        <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
      </client>  
      ```  

   2. <span data-ttu-id="1f6f2-127">搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-127">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  

   3. <span data-ttu-id="1f6f2-128">尋找遺漏[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-128">Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding.</span></span> <span data-ttu-id="1f6f2-129">新增"bindingElementExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-129">Add the following section under the "bindingElementExtensions" node.</span></span>  

       <span data-ttu-id="1f6f2-130">針對[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-130">For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:</span></span>  

      ```  
      <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. <span data-ttu-id="1f6f2-131">搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-131">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  

   5. <span data-ttu-id="1f6f2-132">尋找遺漏[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-132">Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding.</span></span> <span data-ttu-id="1f6f2-133">新增"bindingExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-133">Add the following section under the "bindingExtensions" node.</span></span>  

       <span data-ttu-id="1f6f2-134">針對[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-134">For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:</span></span>  

      ```  
      <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   > [!NOTE]
   >  <span data-ttu-id="1f6f2-135">如需如何判斷公開金鑰和版本資訊，請參閱[判斷的公開金鑰和版本](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-135">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  

4. <span data-ttu-id="1f6f2-136">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-136">Save and close the machine.config file.</span></span>  

####  <a name="BKMK_PubKey"></a> <span data-ttu-id="1f6f2-137">判斷的公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="1f6f2-137">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="1f6f2-138">執行下列步驟來判斷公開金鑰[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-138">Perform the following steps to determine the public key for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  

1. <span data-ttu-id="1f6f2-139">瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-139">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  

2. <span data-ttu-id="1f6f2-140">以滑鼠右鍵按一下，想要的公開金鑰和版本，並選取您的 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-140">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="1f6f2-141">下表列出的 DLL 名稱[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-141">The following table lists the name of the DLL for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  


   |                                  <span data-ttu-id="1f6f2-142">配接器</span><span class="sxs-lookup"><span data-stu-id="1f6f2-142">Adapter</span></span>                                  |       <span data-ttu-id="1f6f2-143">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="1f6f2-143">Name of the DLL</span></span>       |
   |---------------------------------------------------------------------------|-----------------------------|
   | [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] | <span data-ttu-id="1f6f2-144">Microsoft.Adapters.OracleDB</span><span class="sxs-lookup"><span data-stu-id="1f6f2-144">Microsoft.Adapters.OracleDB</span></span> |


3. <span data-ttu-id="1f6f2-145">在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-145">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="1f6f2-146">同樣地，針對值**版本**標籤都會指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-146">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  

4. <span data-ttu-id="1f6f2-147">複製公開金鑰，然後再按**取消**。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-147">Copy the public key, and then click **Cancel**.</span></span>  

##  <a name="BKMK_ConsumeBinding"></a> <span data-ttu-id="1f6f2-148">使用 64 位元安裝上的 取用配接器服務增益集或加入配接器服務參考外掛程式時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="1f6f2-148">Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="1f6f2-149">**問題**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-149">**Problem**</span></span>  

 <span data-ttu-id="1f6f2-150">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-150">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  

```  
No valid adapters are installed on this machine  
```  

 <span data-ttu-id="1f6f2-151">**原因**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-151">**Cause**</span></span>  

 <span data-ttu-id="1f6f2-152">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-152">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="1f6f2-153">64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-153">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="1f6f2-154">所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-154">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="1f6f2-155">不過， [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查是否有 32 位元版本的 machine.config 檔案中的繫結和失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-155">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  

 <span data-ttu-id="1f6f2-156">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-156">**Resolution**</span></span>  

- <span data-ttu-id="1f6f2-157">同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-157">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="1f6f2-158">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-158">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="1f6f2-159">並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-159">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  

- <span data-ttu-id="1f6f2-160">安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-160">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="1f6f2-161">若要確定您的應用程式會使用 ODP.NET 的最新版本，您必須擁有 「 原則 Dll 」 的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-161">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="1f6f2-162">如需詳細資訊，請參閱 <<c0> [ 適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 網站上。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-162">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.</span></span>  

##  <a name="BKMK_InvalidBinding"></a> <span data-ttu-id="1f6f2-163">在 BizTalk Server 管理主控台中設定 Oracle 資料庫配接器連接埠，在 64 位元安裝上時無效的繫結錯誤</span><span class="sxs-lookup"><span data-stu-id="1f6f2-163">Invalid binding error while configuring Oracle database adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="1f6f2-164">**問題**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-164">**Problem**</span></span>  

 <span data-ttu-id="1f6f2-165">當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="1f6f2-165">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  

```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleDBBinding".  
Verify the binding extension is registered in machine.config."  
```  

 <span data-ttu-id="1f6f2-166">**原因**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-166">**Cause**</span></span>  

 <span data-ttu-id="1f6f2-167">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-167">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="1f6f2-168">64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-168">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="1f6f2-169">所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-169">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="1f6f2-170">不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中執行做為 32 位元處理序，並因此當您設定配接器的連接埠時，它會檢查 machine.config 檔案的 32 位元版本中的繫結並失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-170">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  

 <span data-ttu-id="1f6f2-171">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1f6f2-171">**Resolution**</span></span>  

- <span data-ttu-id="1f6f2-172">同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-172">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  

  > [!IMPORTANT]
  >  <span data-ttu-id="1f6f2-173">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-173">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="1f6f2-174">並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-174">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  

- <span data-ttu-id="1f6f2-175">安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-175">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="1f6f2-176">若要確定您的應用程式會使用 ODP.NET 的最新版本，您必須擁有 「 原則 Dll 」 的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-176">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="1f6f2-177">如需詳細資訊，請參閱 <<c0> [ 適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 網站上。</span><span class="sxs-lookup"><span data-stu-id="1f6f2-177">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle website.</span></span> 

## <a name="see-also"></a><span data-ttu-id="1f6f2-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f6f2-178">See Also</span></span>  
[<span data-ttu-id="1f6f2-179">Oracle 資料庫配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1f6f2-179">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)