---
title: SQl 配接器疑難排解安裝問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48778158-6064-4731-be72-1af855ebe373
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9543c7dcd4c92cfd15aed5b93115ffc9a849652b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001455"
---
# <a name="troubleshoot-installation-issues-with-the-sql-adapter"></a><span data-ttu-id="b283a-102">SQl 配接器疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="b283a-102">Troubleshoot Installation Issues with the SQl adapter</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b283a-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可從屬於[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]以及個別的配接器。</span><span class="sxs-lookup"><span data-stu-id="b283a-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is available as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] as well as a separate adapter.</span></span> <span data-ttu-id="b283a-104">如果您要存取本主題來了解與安裝問題[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，為分開[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，所有參考[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式必須解譯為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="b283a-104">If you are accessing this topic to know about installation issues with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] that is separate from the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], all references to the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Setup must be interpreted as [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] Setup.</span></span>  

 <span data-ttu-id="b283a-105">安裝 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]複製產品二進位編碼檔案的電腦上，並註冊每個配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-105">Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter.</span></span> <span data-ttu-id="b283a-106">本節將討論使用來解決安裝錯誤的疑難排解技巧。</span><span class="sxs-lookup"><span data-stu-id="b283a-106">This section discusses using troubleshooting techniques to resolve installation errors.</span></span>  

## <a name="logging-messages-for-setup-actions"></a><span data-ttu-id="b283a-107">安裝動作的記錄訊息</span><span class="sxs-lookup"><span data-stu-id="b283a-107">Logging Messages for Setup Actions</span></span>  
 <span data-ttu-id="b283a-108">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會執行安裝的標準工作[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b283a-108">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="b283a-109">此外，安裝程式也會執行某些自訂動作，例如註冊配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-109">Additionally, the setup also performs certain custom actions such as registering the adapter bindings.</span></span> <span data-ttu-id="b283a-110">您可以記錄這兩個標準，以及自訂安裝程式執行動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="b283a-110">You can log messages for both the standard as well as custom actions that the setup performs.</span></span>  

- <span data-ttu-id="b283a-111">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會安裝使用 MSI 的配接器特定檔案。</span><span class="sxs-lookup"><span data-stu-id="b283a-111">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI.</span></span> <span data-ttu-id="b283a-112">因此，安裝程式記錄是標準的 MSI 記錄。</span><span class="sxs-lookup"><span data-stu-id="b283a-112">Therefore, the logging for the setup is the standard MSI logging.</span></span>  

- <span data-ttu-id="b283a-113">安裝程式會執行自訂動作的所有記錄檔位於 %temp%\adaptersetup.log。</span><span class="sxs-lookup"><span data-stu-id="b283a-113">All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log.</span></span> <span data-ttu-id="b283a-114">如果記錄檔追蹤失敗，追蹤也有事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="b283a-114">If the tracing to the log file fails, the traces are also available in the event log.</span></span>  

## <a name="known-issues"></a><span data-ttu-id="b283a-115">已知問題</span><span class="sxs-lookup"><span data-stu-id="b283a-115">Known Issues</span></span>  
 <span data-ttu-id="b283a-116">以下是您在安裝時可能會遇到最常見的錯誤[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，以及其可能的原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="b283a-116">The following are the most common errors you might encounter when installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.</span></span>  



###  <a name="BKMK_SQLSetupBinding"></a> <span data-ttu-id="b283a-117">安裝程式無法註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="b283a-117">Setup fails to register adapter bindings</span></span>  
 <span data-ttu-id="b283a-118">**問題**</span><span class="sxs-lookup"><span data-stu-id="b283a-118">**Problem**</span></span>  

 <span data-ttu-id="b283a-119">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈 無法註冊配接器繫結，但會繼續進行配接器安裝。</span><span class="sxs-lookup"><span data-stu-id="b283a-119">The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Setup Wizard fails to register the adapter bindings, but proceeds with the adapter installation.</span></span>  

 <span data-ttu-id="b283a-120">**原因**</span><span class="sxs-lookup"><span data-stu-id="b283a-120">**Cause**</span></span>  

 <span data-ttu-id="b283a-121">因為有問題，這可能會造成[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]安裝，[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="b283a-121">This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span> <span data-ttu-id="b283a-122">配接器繫結會寫入至 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b283a-122">The adapter bindings are written to the machine.config file.</span></span>  

 <span data-ttu-id="b283a-123">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="b283a-123">**Resolution**</span></span>  

 <span data-ttu-id="b283a-124">您應該手動註冊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-124">You should manually register the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.</span></span>  

##### <a name="to-register-the-adapter-binding"></a><span data-ttu-id="b283a-125">若要註冊的配接器繫結</span><span class="sxs-lookup"><span data-stu-id="b283a-125">To register the adapter binding</span></span>  

1. <span data-ttu-id="b283a-126">瀏覽至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="b283a-126">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="b283a-127">例如，32 位元平台上，machine.config 位於底下\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="b283a-127">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  

    <span data-ttu-id="b283a-128">在此路徑中，\<版本\>是.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="b283a-128">In this path, \<version\> is the version of the .NET Framework.</span></span>  

2. <span data-ttu-id="b283a-129">使用文字編輯器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="b283a-129">Open the file by using a text editor.</span></span>  

3. <span data-ttu-id="b283a-130">若要註冊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結：</span><span class="sxs-lookup"><span data-stu-id="b283a-130">To register the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding:</span></span>  

   1. <span data-ttu-id="b283a-131">搜尋 [system.serviceModel] 的項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="b283a-131">Search for the element "system.serviceModel" and add the following under it:</span></span>  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
      ```  

   2. <span data-ttu-id="b283a-132">搜尋 「 bindingElementExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="b283a-132">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  

   3. <span data-ttu-id="b283a-133">尋找遺漏[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-133">Look for the missing [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.</span></span> <span data-ttu-id="b283a-134">新增"bindingElementExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="b283a-134">Add the following section under the "bindingElementExtensions" node.</span></span>  

       <span data-ttu-id="b283a-135">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="b283a-135">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. <span data-ttu-id="b283a-136">搜尋 「 bindingExtensions"system.serviceModel\extensions 下的項目。</span><span class="sxs-lookup"><span data-stu-id="b283a-136">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  

   5. <span data-ttu-id="b283a-137">尋找遺漏[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-137">Look for the missing [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.</span></span> <span data-ttu-id="b283a-138">新增"bindingExtensions 」 節點的下一節。</span><span class="sxs-lookup"><span data-stu-id="b283a-138">Add the following section under the "bindingExtensions" node.</span></span>  

       <span data-ttu-id="b283a-139">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="b283a-139">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   > [!NOTE]
   >  <span data-ttu-id="b283a-140">如需如何判斷公開金鑰和版本資訊，請參閱[判斷的公開金鑰和版本](#BKMK_PubKey)。</span><span class="sxs-lookup"><span data-stu-id="b283a-140">For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  

4. <span data-ttu-id="b283a-141">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="b283a-141">Save and close the machine.config file.</span></span>  

####  <a name="BKMK_PubKey"></a> <span data-ttu-id="b283a-142">判斷的公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="b283a-142">Determining the Public Key and Version</span></span>  
 <span data-ttu-id="b283a-143">執行下列步驟來判斷公開金鑰[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b283a-143">Perform the following steps to determine the public key for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

###### <a name="to-determine-the-public-key"></a><span data-ttu-id="b283a-144">若要判斷公開金鑰</span><span class="sxs-lookup"><span data-stu-id="b283a-144">To determine the public key</span></span>  

1. <span data-ttu-id="b283a-145">瀏覽至 [Windows] 目錄中，通常 C:\WINDOWS\assembly。</span><span class="sxs-lookup"><span data-stu-id="b283a-145">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  

2. <span data-ttu-id="b283a-146">以滑鼠右鍵按一下，想要的公開金鑰和版本，並選取您的 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b283a-146">Right-click the DLL for which you want the public key and the version, and then select **Properties**.</span></span> <span data-ttu-id="b283a-147">下表列出的 DLL 名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b283a-147">The following table lists the name of the DLL for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  


   |                              <span data-ttu-id="b283a-148">配接器</span><span class="sxs-lookup"><span data-stu-id="b283a-148">Adapter</span></span>                              |    <span data-ttu-id="b283a-149">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="b283a-149">Name of the DLL</span></span>     |
   |-------------------------------------------------------------------|------------------------|
   | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] | <span data-ttu-id="b283a-150">Microsoft.Adapters.Sql</span><span class="sxs-lookup"><span data-stu-id="b283a-150">Microsoft.Adapters.Sql</span></span> |


3. <span data-ttu-id="b283a-151">在上**一般**索引標籤上，針對值**公開金鑰 Token**標籤都會指定 dll 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b283a-151">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="b283a-152">同樣地，針對值**版本**標籤都會指定 dll 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b283a-152">Similarly, value against the **Version** label specifies the version number for the DLL.</span></span>  

4. <span data-ttu-id="b283a-153">複製公開金鑰，然後再按**取消**。</span><span class="sxs-lookup"><span data-stu-id="b283a-153">Copy the public key, and then click **Cancel**.</span></span>  

###  <a name="BKMK_SQLConsumeBinding"></a> <span data-ttu-id="b283a-154">使用 64 位元安裝上的 取用配接器服務增益集或加入配接器服務參考外掛程式時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="b283a-154">Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation</span></span>  
 <span data-ttu-id="b283a-155">**問題**</span><span class="sxs-lookup"><span data-stu-id="b283a-155">**Problem**</span></span>  

 <span data-ttu-id="b283a-156">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]執行 64 位元版本的 64 位元電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="b283a-156">Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:</span></span>  

```  
No valid adapters are installed on this machine  
```  

 <span data-ttu-id="b283a-157">**原因**</span><span class="sxs-lookup"><span data-stu-id="b283a-157">**Cause**</span></span>  

 <span data-ttu-id="b283a-158">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="b283a-158">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="b283a-159">64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="b283a-159">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="b283a-160">所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-160">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="b283a-161">不過， [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 32 位元處理序執行，因此當您啟動[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，外掛程式會檢查是否有 32 位元版本的 machine.config 檔案中的繫結和失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="b283a-161">However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  

 <span data-ttu-id="b283a-162">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="b283a-162">**Resolution**</span></span>  

 <span data-ttu-id="b283a-163">同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="b283a-163">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="b283a-164">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="b283a-164">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="b283a-165">並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="b283a-165">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  

###  <a name="BKMK_SQLInvalidBinding"></a> <span data-ttu-id="b283a-166">在 BizTalk Server 管理主控台中設定 SQL 配接器連接埠，在 64 位元安裝上時無效的繫結錯誤</span><span class="sxs-lookup"><span data-stu-id="b283a-166">Invalid binding error while configuring SQL adapter ports in BizTalk Server Administration Console on a 64-bit installation</span></span>  
 <span data-ttu-id="b283a-167">**問題**</span><span class="sxs-lookup"><span data-stu-id="b283a-167">**Problem**</span></span>  

 <span data-ttu-id="b283a-168">當您嘗試設定中的配接器的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="b283a-168">When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:</span></span>  

```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sqlBinding".  
Verify the binding extension is registered in machine.config."  
```  

 <span data-ttu-id="b283a-169">**原因**</span><span class="sxs-lookup"><span data-stu-id="b283a-169">**Cause**</span></span>  

 <span data-ttu-id="b283a-170">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] WCF 自訂繫結，在 machine.config 檔的 System.ServiceModel 下登錄。</span><span class="sxs-lookup"><span data-stu-id="b283a-170">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file.</span></span> <span data-ttu-id="b283a-171">64 位元平台會有兩個的 machine.config 檔案，其中一個 32 位元應用程式使用，另一個 64 位元應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="b283a-171">A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications.</span></span> <span data-ttu-id="b283a-172">所以，當您安裝 64 位元版本的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，安裝精靈 註冊在 machine.config 檔案的 64 位元版本的繫結。</span><span class="sxs-lookup"><span data-stu-id="b283a-172">So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file.</span></span> <span data-ttu-id="b283a-173">不過，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中執行做為 32 位元處理序，並因此當您設定配接器的連接埠時，它會檢查 machine.config 檔案的 32 位元版本中的繫結並失敗時提供錯誤。</span><span class="sxs-lookup"><span data-stu-id="b283a-173">However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.</span></span>  

 <span data-ttu-id="b283a-174">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="b283a-174">**Resolution**</span></span>  

 <span data-ttu-id="b283a-175">同時安裝 32 位元和 64 位元版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="b283a-175">Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="b283a-176">您必須只有 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="b283a-176">You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.</span></span> <span data-ttu-id="b283a-177">並排顯示安裝 32 位元和 64 位元[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不支援在單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="b283a-177">Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b283a-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b283a-178">See Also</span></span>  
 [<span data-ttu-id="b283a-179">SQL 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b283a-179">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)