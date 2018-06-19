---
title: Oracle E-business Suite 配接器疑難排解安裝問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09b3af20-ab87-44e8-8ded-c19432552be7
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29fbee54262f1b45e3cc9be67c057767a80b325f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965628"
---
# <a name="troubleshoot-installation-issues-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="005a9-102">Oracle E-business Suite 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="005a9-102">Troubleshoot Installation Issues with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="005a9-103">安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-103">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="005a9-104">本節將討論使用來解決安裝錯誤的疑難排解技術。</span><span class="sxs-lookup"><span data-stu-id="005a9-104">This section discusses using troubleshooting techniques to resolve installation errors.</span></span>  
  
## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="005a9-105">安裝程式動作的記錄訊息</span><span class="sxs-lookup"><span data-stu-id="005a9-105">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="005a9-106">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="005a9-106">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="005a9-107">此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-107">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="005a9-108">您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="005a9-108">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  
  
-   <span data-ttu-id="005a9-109">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝在使用 MSI 的配接器特定檔案。</span><span class="sxs-lookup"><span data-stu-id="005a9-109">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="005a9-110">因此，安裝程式的記錄是標準的 MSI 記錄。</span><span class="sxs-lookup"><span data-stu-id="005a9-110">Therefore, the logging for the setup is the standard MSI logging.</span></span> <span data-ttu-id="005a9-111">[Windows Installer 記錄](https://msdn.microsoft.com/library/windows/desktop/aa372847.aspx)提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="005a9-111">[Windows Installer Logging](https://msdn.microsoft.com/library/windows/desktop/aa372847.aspx) provides more details.</span></span> 
  
-   <span data-ttu-id="005a9-112">安裝程式會執行自訂動作的所有記錄檔位於 %temp%\adaptersetup.log。</span><span class="sxs-lookup"><span data-stu-id="005a9-112">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="005a9-113">如果失敗的追蹤記錄檔，追蹤也會提供事件記錄檔中的。</span><span class="sxs-lookup"><span data-stu-id="005a9-113">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="005a9-114">已知問題</span><span class="sxs-lookup"><span data-stu-id="005a9-114">Known Issues</span></span>  
 <span data-ttu-id="005a9-115">以下是最常見的錯誤，安裝時，可能會遇到[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]、 以及它們的可能原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="005a9-115">The following are the most common errors you might encounter when installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.</span></span>  
  
  
  
###  <a name="BKMK_OraAppBinding"></a><span data-ttu-id="005a9-116">安裝程式無法註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="005a9-116">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="005a9-117">**問題**</span><span class="sxs-lookup"><span data-stu-id="005a9-117">**Problem**</span></span>  
  
 <span data-ttu-id="005a9-118">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈無法註冊配接器繫結，但會繼續進行配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="005a9-118">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  
  
 <span data-ttu-id="005a9-119">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="005a9-119">**Cause**</span></span>  
  
 <span data-ttu-id="005a9-120">這可能會因為發生問題造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="005a9-120">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="005a9-121">配接器繫結會寫入至 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="005a9-121">The adapter bindings are written to the machine.config file.</span></span>  
  
 <span data-ttu-id="005a9-122">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="005a9-122">**Resolution**</span></span>  
  
 <span data-ttu-id="005a9-123">您應該手動註冊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-123">You should manually register the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding.</span></span>  
  
##### <a name="to-register-the-adapter-binding"></a><span data-ttu-id="005a9-124">若要註冊的配接器繫結</span><span class="sxs-lookup"><span data-stu-id="005a9-124">To register the adapter binding</span></span>  
  
1.  <span data-ttu-id="005a9-125">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="005a9-125">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="005a9-126">例如，32 位元平台上，machine.config 位在\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="005a9-126">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
     <span data-ttu-id="005a9-127">在此路徑中\<*版本*\>是.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="005a9-127">In this path, \<*version*\> is the version of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="005a9-128">使用文字編輯器開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="005a9-128">Open the file by using a text editor.</span></span>  
  
3.  <span data-ttu-id="005a9-129">若要註冊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="005a9-129">To register the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding:</span></span>  
  
    1.  <span data-ttu-id="005a9-130">搜尋 「 system.serviceModel 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="005a9-130">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleebs" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="005a9-131">搜尋"bindingElementExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="005a9-131">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="005a9-132">尋找遺漏[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-132">Look for the missing [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding.</span></span> <span data-ttu-id="005a9-133">新增下列區段，"bindingElementExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="005a9-133">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="005a9-134">如[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="005a9-134">For [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="005a9-135">搜尋"bindingExtensions"system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="005a9-135">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="005a9-136">尋找遺漏[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-136">Look for the missing [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding.</span></span> <span data-ttu-id="005a9-137">新增下列區段，"bindingExtensions 」 節點下。</span><span class="sxs-lookup"><span data-stu-id="005a9-137">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="005a9-138">如[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="005a9-138">For [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="005a9-139">如需如何判斷公開金鑰和版本資訊，請參閱[公開金鑰和版本判斷](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="005a9-139">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="005a9-140">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="005a9-140">Save and close the machine.config file.</span></span>  
  
####  <a name="BKMK_PubKey"></a><span data-ttu-id="005a9-141">判斷公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="005a9-141">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="005a9-142">執行下列步驟來判斷公開金鑰[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="005a9-142">Perform the following steps to determine the public key for [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
###### <a name="to-determine-the-public-key"></a><span data-ttu-id="005a9-143">判斷公開金鑰</span><span class="sxs-lookup"><span data-stu-id="005a9-143">To determine the public key</span></span>  
  
1.  <span data-ttu-id="005a9-144">瀏覽至 Windows 目錄，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="005a9-144">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="005a9-145">以滑鼠右鍵按一下您想要的公開金鑰和版本，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="005a9-145">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="005a9-146">下表列出的 DLL 名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="005a9-146">The following table lists the name of the DLL for [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
    |<span data-ttu-id="005a9-147">配接器</span><span class="sxs-lookup"><span data-stu-id="005a9-147">Adapter</span></span>|<span data-ttu-id="005a9-148">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="005a9-148">Name of the DLL</span></span>|  
    |-------------|---------------------|  
    |[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="005a9-149">Microsoft.Adapters.OracleEBS</span><span class="sxs-lookup"><span data-stu-id="005a9-149">Microsoft.Adapters.OracleEBS</span></span>|  
  
3.  <span data-ttu-id="005a9-150">在**一般**索引標籤上，根據值**公開金鑰語彙基元**標籤指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="005a9-150">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="005a9-151">同樣地，針對值**版本**標籤指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="005a9-151">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="005a9-152">複製的公開金鑰，然後按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="005a9-152">Copy the public key, and then click **Cancel**.</span></span>  
  
###  <a name="BKMK_ConsumeOraApp"></a><span data-ttu-id="005a9-153">使用 64 位元安裝上使用配接器服務增益集或加入配接器服務參考外掛程式時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="005a9-153">Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="005a9-154">**問題**</span><span class="sxs-lookup"><span data-stu-id="005a9-154">**Problem**</span></span>  
  
 <span data-ttu-id="005a9-155">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="005a9-155">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  
  
```  
No valid adapters are installed on this machine  
```  
  
 <span data-ttu-id="005a9-156">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="005a9-156">**Cause**</span></span>  
  
 <span data-ttu-id="005a9-157">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="005a9-157">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="005a9-158">64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="005a9-158">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="005a9-159">因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-159">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="005a9-160">不過，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查 machine.config 檔案的 32 位元版本中的繫結和失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="005a9-160">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="005a9-161">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="005a9-161">**Resolution**</span></span>  
  
-   <span data-ttu-id="005a9-162">同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="005a9-162">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="005a9-163">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="005a9-163">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="005a9-164">由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="005a9-164">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="005a9-165">安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="005a9-165">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="005a9-166">若要確定您的應用程式的運作方式與 ODP.NET 的最新版本，您必須使用"原則 DLLs"的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="005a9-166">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="005a9-167">如需詳細資訊，請參閱"Oracle 資料提供者的.NET 常見問題集 」 在[http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834)。</span><span class="sxs-lookup"><span data-stu-id="005a9-167">For more information, see "Oracle Data Provider for .NET FAQ" at [http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834).</span></span>  
  
###  <a name="BKMK_OraAppInvalidBinding"></a><span data-ttu-id="005a9-168">無效的繫結時發生的 64 位元安裝上設定 BizTalk Server 管理主控台中的 Oracle E-business Suite 介面卡連接埠</span><span class="sxs-lookup"><span data-stu-id="005a9-168">Invalid binding error while configuring Oracle E-Business Suite adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="005a9-169">**問題**</span><span class="sxs-lookup"><span data-stu-id="005a9-169">**Problem**</span></span>  
  
 <span data-ttu-id="005a9-170">當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="005a9-170">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleEBSBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 <span data-ttu-id="005a9-171">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="005a9-171">**Cause**</span></span>  
  
 <span data-ttu-id="005a9-172">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="005a9-172">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="005a9-173">64 位元平台都有兩個 machine.config 檔案，其中一個 32 位元應用程式所使用，另一個 64 位元應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="005a9-173">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="005a9-174">因此，當您安裝 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="005a9-174">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="005a9-175">不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台執行以 32 位元處理序，因此當您設定配接器的連接埠，它會檢查 machine.config 檔案的 32 位元版本中的繫結而會失敗，提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="005a9-175">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  
  
 <span data-ttu-id="005a9-176">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="005a9-176">**Resolution**</span></span>  
  
-   <span data-ttu-id="005a9-177">同時安裝 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="005a9-177">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="005a9-178">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="005a9-178">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="005a9-179">由並行安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="005a9-179">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  
  
-   <span data-ttu-id="005a9-180">安裝 Oracle 用戶端 11.1.0.6 修補組 11.1.0.7 Oracle 資料存取元件的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="005a9-180">Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="005a9-181">若要確定您的應用程式的運作方式與 ODP.NET 的最新版本，您必須使用"原則 DLLs"的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="005a9-181">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="005a9-182">如需詳細資訊，請參閱"Oracle 資料提供者的.NET 常見問題集 」 在[http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834)。</span><span class="sxs-lookup"><span data-stu-id="005a9-182">For more information, see "Oracle Data Provider for .NET FAQ" at [http://go.microsoft.com/fwlink/p/?LinkId=92834](http://go.microsoft.com/fwlink/p/?LinkId=92834).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005a9-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="005a9-183">See Also</span></span>  
[<span data-ttu-id="005a9-184">Oracle EBS 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="005a9-184">Troubleshooting the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)