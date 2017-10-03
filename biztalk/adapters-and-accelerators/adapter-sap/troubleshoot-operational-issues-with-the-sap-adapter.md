---
title: "SAP BizTalk 配接器疑難排解操作問題 |Microsoft 文件"
description: "常見的錯誤、 問題和 mySAP 配接器在 BizTalk 配接器組件 (BAP) 中的解決方式"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb0f005b-7548-478b-8243-69e07c29d02c
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5298782f23cb8c7c32a2bcbd512f3a1b78f8a69d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-sap-adapter"></a><span data-ttu-id="c7f57-103">SAP 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="c7f57-103">Troubleshoot Operational Issues with the SAP adapter</span></span>
<span data-ttu-id="c7f57-104">本章節將討論使用來解析作業使用時可能遭遇的錯誤的疑難排解技術[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-104">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
### <a name="enable-tracing"></a><span data-ttu-id="c7f57-105">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="c7f57-105">Enable tracing</span></span>  
 <span data-ttu-id="c7f57-106">如需有關追蹤中的支援資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[診斷追蹤和訊息記錄 SAP 配接器的](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-106">For information about tracing support in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Diagnostic Tracing and Message Logging for the SAP adapter](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md).</span></span>  
  
##  <span data-ttu-id="c7f57-107"><a name="client_dll"></a>載入的繫結時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-107"><a name="client_dll"></a> Error loading the binding</span></span>  
 <span data-ttu-id="c7f57-108">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-108">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-109">當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，GUI 會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="c7f57-109">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the GUI gives the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="c7f57-110">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-110">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-111">當您啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]載入所有已安裝的配接器的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="c7f57-111">When you start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="c7f57-112">接著，配接器繫結會相依於企業應用程式的特定用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="c7f57-112">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="c7f57-113">您可能會面臨這個問題的一個或兩個原因如下：</span><span class="sxs-lookup"><span data-stu-id="c7f57-113">You might face this issue for one or both of the following reasons:</span></span>  
  
-   <span data-ttu-id="c7f57-114">將介面卡安裝在電腦上未安裝必要的 LOB 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="c7f57-114">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
-   <span data-ttu-id="c7f57-115">未安裝中所包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-115">You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="c7f57-116">不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="c7f57-116">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="c7f57-117">如此一來，GUI 無法載入其他配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="c7f57-117">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="c7f57-118">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-118">**Resolution**</span></span>  
  
-   <span data-ttu-id="c7f57-119">請確定您執行自訂安裝，安裝您所需要的介面卡的介面卡。</span><span class="sxs-lookup"><span data-stu-id="c7f57-119">Make sure you do a Custom installation of the adapters to install only the adapter you need.</span></span>  
  
-   <span data-ttu-id="c7f57-120">請確定您安裝的電腦上已安裝必要的 LOB 用戶端版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-120">Make sure the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="c7f57-121">[支援部署 LOB 系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的版本。</span><span class="sxs-lookup"><span data-stu-id="c7f57-121">[Supported LOB systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported versions.</span></span> <span data-ttu-id="c7f57-122">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]也需要特定 Dll SAP 系統的介面。</span><span class="sxs-lookup"><span data-stu-id="c7f57-122">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] also requires certain DLLs to interface with the SAP system.</span></span> <span data-ttu-id="c7f57-123">如需配接器所需的 Dll 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-123">For more information about the DLLs required by the adapter, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>
  
##  <span data-ttu-id="c7f57-124"><a name="BKMK_SAPDisplay"></a>SAP 配接器在 BizTalk 管理主控台遺漏</span><span class="sxs-lookup"><span data-stu-id="c7f57-124"><a name="BKMK_SAPDisplay"></a> The SAP adapter is missing in BizTalk Administration console</span></span>  
 <span data-ttu-id="c7f57-125">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-125">**Problem**</span></span>  
  
<span data-ttu-id="c7f57-126">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在 BizTalk Server 管理主控台中的配接器清單中。</span><span class="sxs-lookup"><span data-stu-id="c7f57-126">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] included with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="c7f57-127">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-127">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-128">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="c7f57-128">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="c7f57-129">因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-129">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="c7f57-130">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-130">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-131">您可以明確加入[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-131">You can explicitly add the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
##  <span data-ttu-id="c7f57-132"><a name="BKMK_SAPConnOpen"></a>Dll 遺漏開啟 SAP 的連線時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-132"><a name="BKMK_SAPConnOpen"></a> DLLs are missing error opening a connection to SAP</span></span>  
 <span data-ttu-id="c7f57-133">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-133">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-134">當您嘗試開啟 SAP 系統使用的連接[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，在 SAP 系統中，會出現一個對話方塊通知某些 Dll 會遺失。</span><span class="sxs-lookup"><span data-stu-id="c7f57-134">When you try to open a connection to the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], a dialog box appears in the SAP system, informing that some DLLs are missing.</span></span>  
  
 <span data-ttu-id="c7f57-135">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-135">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-136">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 librfc32u.dll 建立與 SAP 系統的連線。</span><span class="sxs-lookup"><span data-stu-id="c7f57-136">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses librfc32u.dll to establish a connection with the SAP system.</span></span> <span data-ttu-id="c7f57-137">Librfc32u.dll 相對的需要一組 Dll 才能運作。</span><span class="sxs-lookup"><span data-stu-id="c7f57-137">The librfc32u.dll, in turn, requires a set of DLLs to function.</span></span> <span data-ttu-id="c7f57-138">當這些支援的 Dll 不會加入至電腦上的 PATH 變數，就會出現此錯誤其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="c7f57-138">You get this error if these supporting DLLs are not added to the PATH variable on the computer where the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is installed.</span></span>  
  
 <span data-ttu-id="c7f57-139">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-139">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-140">提供以解決問題的資料表是指[載入配接器繫結時發生錯誤](#client_dll)問題。</span><span class="sxs-lookup"><span data-stu-id="c7f57-140">Refer to the table provided as a resolution to the [Error in loading the adapter bindings](#client_dll) issue.</span></span> <span data-ttu-id="c7f57-141">這個表格會列出支援使用 SAP 系統互動所需的 Dll [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-141">The table lists the supporting DLLs required to interface with the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
##  <span data-ttu-id="c7f57-142"><a name="BKMK_SAPXmlRetrieve"></a>擷取具有超過 65536 節點的 XML 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-142"><a name="BKMK_SAPXmlRetrieve"></a> Error retrieving XML with more than 65,536 nodes</span></span>  
 <span data-ttu-id="c7f57-143">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-143">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-144">配接器會提供下列的錯誤，同時擷取有超過 65536 節點的 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="c7f57-144">The adapter gives the following error while retrieving XML output that has more than 65,536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="c7f57-145">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-145">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-146">配接器無法進行序列化和還原序列化物件，超過 65536 個項目。</span><span class="sxs-lookup"><span data-stu-id="c7f57-146">The adapter cannot serialize and deserialize an object with more than 65,536 items.</span></span>  
  
 <span data-ttu-id="c7f57-147">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-147">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-148">您可以設定來修正此問題`maxItemsInObjectGraph`參數，在下列兩種方法之一：</span><span class="sxs-lookup"><span data-stu-id="c7f57-148">You can fix this issue by setting the `maxItemsInObjectGraph` parameter in either of the following two ways:</span></span>  
  
-   <span data-ttu-id="c7f57-149">設定此參數，藉由變更`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7f57-149">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
-   <span data-ttu-id="c7f57-150">將下列加入至您的應用程式的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="c7f57-150">Add the following to your application's app.config file.</span></span>  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 <span data-ttu-id="c7f57-151">範例 app.config 看起來將如下所示。</span><span class="sxs-lookup"><span data-stu-id="c7f57-151">A sample app.config will look like the following.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  \<system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="sapBinding"  
       contract="IOutboundContract" name="sap_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
##  <span data-ttu-id="c7f57-152"><a name="BKMK_SAPConnURI"></a>輸入 WCF 自訂連接埠的連線 URI，在 BizTalk Server 中的錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-152"><a name="BKMK_SAPConnURI"></a> Error entering a connection URI for a WCF-Custom port in BizTalk Server</span></span>  
 <span data-ttu-id="c7f57-153">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-153">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c7f57-154">當您指定的連接來連接到 SAP 系統的 URI 時，請提供下列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7f57-154"> gives the following error when you specify a connection URI to connect to the SAP system.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="c7f57-155">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-155">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-156">連線 URI 並不依循標準編碼格式。</span><span class="sxs-lookup"><span data-stu-id="c7f57-156">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="c7f57-157">例如，參數的值可能會包含空格。</span><span class="sxs-lookup"><span data-stu-id="c7f57-157">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="c7f57-158">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-158">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-159">請確定您指定的 URI 符合標準的編碼格式的連接。</span><span class="sxs-lookup"><span data-stu-id="c7f57-159">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="c7f57-160">例如，"%20"必須取代的空白區域。</span><span class="sxs-lookup"><span data-stu-id="c7f57-160">For example, a blank space must be replaced by "%20".</span></span>  
  
##  <span data-ttu-id="c7f57-161"><a name="BKMK_SAPOperate"></a>在完成的作業上 SAP 時 System.ArgumentNullException 錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-161"><a name="BKMK_SAPOperate"></a> System.ArgumentNullException error while completing an operation on SAP</span></span>  
 <span data-ttu-id="c7f57-162">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-162">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-163">執行 SAP 系統使用的任何作業時，配接器會產生下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-163">The adapter gives the following error when performing any operation on the SAP system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
```  
System.ArgumentNullException: Value cannot be null.  
```  
  
 <span data-ttu-id="c7f57-164">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-164">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-165">未指定訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="c7f57-165">The WCF action for the message is not specified.</span></span> <span data-ttu-id="c7f57-166">WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="c7f57-166">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="c7f57-167">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-167">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-168">指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="c7f57-168">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="c7f57-169">如需指示，請參閱[設定 SAP 系統的 SOAP 動作](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-169">For instructions, see [Configure the SOAP action for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md).</span></span> <span data-ttu-id="c7f57-170">請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)若要查看每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="c7f57-170">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) to see a list of actions for each operation.</span></span>  
  
##  <span data-ttu-id="c7f57-171"><a name="BKMK_SAPXmlParsing"></a>因為不正確的作業名稱中指定的動作而 XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="c7f57-171"><a name="BKMK_SAPXmlParsing"></a> XmlReaderParsingException due to incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="c7f57-172">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-172">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-173">傳送訊息至 SAP 系統時，BizTalk Server 管理主控台就會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="c7f57-173">The BizTalk Server Administration Console gives the following error when sending messages to an SAP system:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="c7f57-174">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-174">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-175">如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：</span><span class="sxs-lookup"><span data-stu-id="c7f57-175">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="c7f57-176">在上述格式中，作業名稱係由您產生結構描述時所選擇的作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-176">In the above format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="c7f57-177">比方說，如果您針對 RFC_CUSTOMER_GET 產生結構描述，動作中的作業名稱會"RFC_CUSTOMER_GET"。</span><span class="sxs-lookup"><span data-stu-id="c7f57-177">For example, if you generated schema for RFC_CUSTOMER_GET, the operation name in the action will be "RFC_CUSTOMER_GET".</span></span> <span data-ttu-id="c7f57-178">不過，在 BizTalk 協調流程中建立的邏輯連接埠中的作業名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。</span><span class="sxs-lookup"><span data-stu-id="c7f57-178">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="c7f57-179">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-179">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-180">請確定作業名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體通訊埠都相同。</span><span class="sxs-lookup"><span data-stu-id="c7f57-180">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration Console) are same.</span></span>  
  
##  <span data-ttu-id="c7f57-181"><a name="BKMK_SAPHundredCons"></a>開啟 100 個以上對 SAP 的連線時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-181"><a name="BKMK_SAPHundredCons"></a> Error opening more than 100 connections to SAP</span></span>  
 <span data-ttu-id="c7f57-182">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-182">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-183">開啟超過 100 個連接至 SAP 系統時，配接器會擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7f57-183">The adapter throws the following exception when opening more than 100 connections to the SAP system.</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.ConnectionException: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  GWHOST=<gw_host>, GWSERV=<gw_serv>, SYSNR=<sys_number>  
LOCATION    CPIC (TCP/IP) on local host with Unicode  
ERROR       max no of 100 conversations exceeded  
```  
  
 <span data-ttu-id="c7f57-184">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-184">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-185">根據預設，SAP 不會啟用超過 100 個連線到系統。</span><span class="sxs-lookup"><span data-stu-id="c7f57-185">By default, SAP does not enable more than 100 connections into the system.</span></span>  
  
 <span data-ttu-id="c7f57-186">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-186">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-187">若要增加最大連接數目，您必須已安裝，並將它設定為數值的 SAP 用戶端程式庫的電腦上建立環境變數。</span><span class="sxs-lookup"><span data-stu-id="c7f57-187">To increase the maximum number of connections, you must create an environment variable on the computer that has the SAP client libraries installed and set it to a numeric value.</span></span> <span data-ttu-id="c7f57-188">您指定這個環境變數的值是可成為 SAP 系統的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="c7f57-188">The value you specify for this environment variable is the maximum number of connections that can be made into the SAP system.</span></span> <span data-ttu-id="c7f57-189">建立環境變數詳細資料如下：</span><span class="sxs-lookup"><span data-stu-id="c7f57-189">Create the environment variable with the following details:</span></span>  
  
-   <span data-ttu-id="c7f57-190">**變數名稱**: CPIC_MAX_CONV</span><span class="sxs-lookup"><span data-stu-id="c7f57-190">**Variable name**: CPIC_MAX_CONV</span></span>  
  
-   <span data-ttu-id="c7f57-191">**變數值**： 任何正數值。</span><span class="sxs-lookup"><span data-stu-id="c7f57-191">**Variable value**: any positive numeric value.</span></span> <span data-ttu-id="c7f57-192">比方說，如果要啟用 200 個連接至 SAP 系統，您可以指定的值為 200。</span><span class="sxs-lookup"><span data-stu-id="c7f57-192">For example, to enable 200 connections into the SAP system, specify the value as 200.</span></span>  
  
 <span data-ttu-id="c7f57-193">如需建立環境變數的指示，請參閱 < 如何建立在 Windows 2000 的系統變數 」 在[http://go.microsoft.com/fwlink/?LinkId=95020](http://go.microsoft.com/fwlink/?LinkId=95020)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-193">For instructions on creating an environment variable, see "How To Create System Variables in Windows 2000" at [http://go.microsoft.com/fwlink/?LinkId=95020](http://go.microsoft.com/fwlink/?LinkId=95020).</span></span>  
  
##  <span data-ttu-id="c7f57-194"><a name="BKMK_SAPIDOCMetadata"></a>產生錯誤或擷取 Idoc 的中繼資料</span><span class="sxs-lookup"><span data-stu-id="c7f57-194"><a name="BKMK_SAPIDOCMetadata"></a> Error generating or retrieving metadata for IDOCs</span></span>  
 <span data-ttu-id="c7f57-195">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-195">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-196">產生的中繼資料時**接收**在 SAP 系統中，IDOC 的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7f57-196">While generating metadata for the **Receive** operation for an IDOC in an SAP system, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives the following error.</span></span>  
  
```  
Error while retrieving or generating the WSDL.  
Adapter message: Details: ErrorCode=RFC_EXCEPTION.  
ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage= OBJECT_UNKNOWN.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: IDOCTYPE_READ_COMPLETE.  
```  
  
 <span data-ttu-id="c7f57-197">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-197">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-198">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取的中繼資料會使用 RFC IDOCTYPE_READ_COMPLETE**接收**IDOC 的作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-198">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the IDOCTYPE_READ_COMPLETE RFC to retrieve the metadata for the **Receive** operation for an IDOC.</span></span> <span data-ttu-id="c7f57-199">叫用這個 RFC SAP 系統中需要特定的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="c7f57-199">Invoking this RFC requires specific user permissions in the SAP system.</span></span> <span data-ttu-id="c7f57-200">如果您已經連接到 SAP 系統使用沒有叫用 IDOCTYPE_READ_COMPLETE RFC，權限的認證，產生中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7f57-200">To generate metadata, if you have connected to the SAP system using a credential that does not have permission to invoke the IDOCTYPE_READ_COMPLETE RFC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an error.</span></span>  
  
 <span data-ttu-id="c7f57-201">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-201">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-202">SAP GUI，您有配接器所使用的相同認證登入。</span><span class="sxs-lookup"><span data-stu-id="c7f57-202">Log in to the SAP GUI using the same credentials you had used for the adapter.</span></span> <span data-ttu-id="c7f57-203">瀏覽至交易 SE37，並輸入要執行為 IDOCTYPE_READ_COMPLETE RFC 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7f57-203">Navigate to transaction SE37, and enter the name of the RFC to execute as IDOCTYPE_READ_COMPLETE.</span></span>  
  
 <span data-ttu-id="c7f57-204">對於 PI_IDOCTYP 和 PI_CIMTYP 的輸入參數，輸入的值對應至自訂 IDoc。</span><span class="sxs-lookup"><span data-stu-id="c7f57-204">For the input parameters PI_IDOCTYP and PI_CIMTYP, enter the values corresponding to the custom IDoc.</span></span> <span data-ttu-id="c7f57-205">PI_VERSION 和 PI_RELEASE 參數，為所選配接器中繼資料的 UI 中輸入相同的值。</span><span class="sxs-lookup"><span data-stu-id="c7f57-205">For the parameters PI_VERSION and PI_RELEASE, enter the same values as being chosen in the Adapter Metadata UI.</span></span> <span data-ttu-id="c7f57-206">然後，按 F8 以執行。</span><span class="sxs-lookup"><span data-stu-id="c7f57-206">And, press F8 to execute.</span></span>  
  
 <span data-ttu-id="c7f57-207">您應該取得相同的例外狀況做什麼配接器接收，關於此問題的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c7f57-207">You should get the same exception as what the adapter receives, with more information about the issue.</span></span>  
  
 <span data-ttu-id="c7f57-208">如果您仍然無法解決問題時，產生的結構描述**ReceiveIdoc**作業而不是**接收**作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-208">If you are still not able to resolve the issue, generate a schema for the **ReceiveIdoc** operation instead of the **Receive** operation.</span></span> <span data-ttu-id="c7f57-209">在此情況下，SAP 配接器不會使用 IDOCTYPE_READ_COMPLETE，並不會擲回任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7f57-209">In this case, the SAP adapter does not use IDOCTYPE_READ_COMPLETE, and does not throw any error.</span></span>  
  
##  <span data-ttu-id="c7f57-210"><a name="BKMK_SAPIDOCReceive"></a>傳送或接收已釋放區段的 Idoc 的錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-210"><a name="BKMK_SAPIDOCReceive"></a> Error sending or receiving IDOCs that have unreleased segments</span></span>  
 <span data-ttu-id="c7f57-211">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-211">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-212">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供 XmlReaderParsingException 傳送 Idoc 時 (使用**傳送**作業) 或接收的 Idoc (使用**接收**作業)，已釋放區段。</span><span class="sxs-lookup"><span data-stu-id="c7f57-212">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an XmlReaderParsingException while sending IDOCs (using **Send** operation) or receiving IDOCs (using **Receive** operation) that have unreleased segments.</span></span>  
  
 <span data-ttu-id="c7f57-213">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-213">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-214">Idoc 被 constituted 的區段。</span><span class="sxs-lookup"><span data-stu-id="c7f57-214">IDOCs are constituted of segments.</span></span> <span data-ttu-id="c7f57-215">在產生中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取 SAP 系統中的所有發行的區段。</span><span class="sxs-lookup"><span data-stu-id="c7f57-215">While generating metadata, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves all the released segments that are present in the SAP system.</span></span> <span data-ttu-id="c7f57-216">不過，當配接器用戶端使用的中繼資料執行作業，例如接收 IDOC，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供 XmlReaderParsingException。</span><span class="sxs-lookup"><span data-stu-id="c7f57-216">However, when the adapter client uses the metadata to perform an operation such as receiving an IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an XmlReaderParsingException.</span></span> <span data-ttu-id="c7f57-217">這是因為 SAP 系統接收 IDOC 時，可能會傳送一些未發行的區段，也未配接器所產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c7f57-217">This occurs because when the IDOC is received, the SAP system might have sent some unreleased segments as well, the metadata for which was not generated by the adapter.</span></span>  
  
 <span data-ttu-id="c7f57-218">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-218">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-219">執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c7f57-219">Do any of the following:</span></span>  
  
-   <span data-ttu-id="c7f57-220">藉由套用適當的修補程式的未發行區段升級您的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="c7f57-220">Upgrade your SAP system by applying appropriate patches for the unreleased segments.</span></span>  
  
-   <span data-ttu-id="c7f57-221">使用**SendIdoc**或**ReceiveIdoc**傳送和接收 Idoc 分別作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-221">Use **SendIdoc** or **ReceiveIdoc** operations to send and receive IDOCs respectively.</span></span> <span data-ttu-id="c7f57-222">如需有關這些作業的詳細資訊，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-222">For more information about these operations, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span></span>  
  
##  <span data-ttu-id="c7f57-223"><a name="BKMK_SAPIDOCSend"></a>傳送至已收到使用 SAP FilePort 的 SAP Idoc 一般檔案時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-223"><a name="BKMK_SAPIDOCSend"></a> Error sending flat-file IDOCs to SAP that were received using the SAP FilePort</span></span>  
 <span data-ttu-id="c7f57-224">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-224">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-225">如果您嘗試傳送 (使用**傳送**作業) 的 SAP 系統，使用 SAP FilePort 產生一般檔案 IDOC，BizTalk 協調流程中的一般檔案剖析器無法將 flatf 檔案轉換成 XML 格式，藉此失敗IDOD**傳送**作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-225">If you try to send (using **Send** operation) a flat-file IDOC to an SAP system that was generated using an SAP FilePort, the flat-file parser in the BizTalk orchestration fails to convert the flatf-file to an XML format, thereby failing the IDOD **Send** operation.</span></span>  
  
 <span data-ttu-id="c7f57-226">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-226">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-227">當 SAP 系統產生使用 FilePort IDOC 時，它會修剪關閉區段結尾處的空白空間。</span><span class="sxs-lookup"><span data-stu-id="c7f57-227">When the SAP system generates an IDOC using a FilePort, it trims off all the empty spaces at the end of a segment.</span></span> <span data-ttu-id="c7f57-228">不過，一般檔案剖析器預期要有已成功將一般檔案轉換成 XML 區段中的最後一個欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="c7f57-228">However, the flat-file parser expects the data of the last field in the segment to be present to successfully convert the flat-file to XML.</span></span> <span data-ttu-id="c7f57-229">因為空的空間不存在區段中，一般檔案剖析器無法剖析一般檔案為 XML。</span><span class="sxs-lookup"><span data-stu-id="c7f57-229">Because the empty spaces are not present in the segment, the flat-file parser fails to parse the flat-file to XML.</span></span>  
  
 <span data-ttu-id="c7f57-230">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-230">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-231">對於使用 SAP FilePort 產生這類一般檔案 Idoc，使用**SendIdoc**作業改為。</span><span class="sxs-lookup"><span data-stu-id="c7f57-231">For such flat-file IDOCs generated using the SAP FilePort, use the **SendIdoc** operation instead.</span></span> <span data-ttu-id="c7f57-232">如需有關這項作業的詳細資訊，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f57-232">For more information about this operation, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span></span>  
  
##  <span data-ttu-id="c7f57-233"><a name="BKMK_SAPRecIDOCCompat"></a>錯誤從 SAP 接收 Idoc，如果 EnableBizTalkCompatibilityMode 屬性設定為 true</span><span class="sxs-lookup"><span data-stu-id="c7f57-233"><a name="BKMK_SAPRecIDOCCompat"></a> Error receiving IDOCs from SAP if EnableBizTalkCompatibilityMode property is set to true</span></span>  
 <span data-ttu-id="c7f57-234">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-234">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-235">在接收的 IDOC 時發生下列例外狀況， **EnableBizTalkCompatibilityMode**屬性組繫結為 true:</span><span class="sxs-lookup"><span data-stu-id="c7f57-235">The following exception is encountered while receiving an IDOC with the **EnableBizTalkCompatibilityMode** binding property set to true:</span></span>  
  
```  
System.Exception: Loading property information list by namespace failed or property not found in the list. Verify that the schema is deployed properly.  
```  
  
 <span data-ttu-id="c7f57-236">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-236">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-237">如果繫結屬性**EnableBizTalkCompatibilityMode**設**true**，您必須新增 BizTalk 屬性結構描述 DLL 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 BizTalk 應用程式中，也就是資源您的專案部署所在的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7f57-237">If the binding property **EnableBizTalkCompatibilityMode** is set to **true**, you must add the BizTalk property schema DLL for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a resource in your BizTalk application, that is, the application in which your project is deployed.</span></span>  
  
 <span data-ttu-id="c7f57-238">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-238">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-239">BizTalk 屬性結構描述的名稱[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是*Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*。</span><span class="sxs-lookup"><span data-stu-id="c7f57-239">The name for the BizTalk property schema for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*.</span></span> <span data-ttu-id="c7f57-240">這會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]下安裝\<安裝磁碟機 >: \Program Files\Microsoft BizTalk 配接器 Pack\bin。</span><span class="sxs-lookup"><span data-stu-id="c7f57-240">This is installed by the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup under \<installation drive>:\ Program Files\Microsoft BizTalk Adapter Pack\bin.</span></span> <span data-ttu-id="c7f57-241">執行下列工作將這個組件新增為 BizTalk 應用程式中的資源。</span><span class="sxs-lookup"><span data-stu-id="c7f57-241">Perform the following tasks to add this assembly as a resource in your BizTalk application.</span></span>  
  
#### <a name="add-an-assembly-as-a-resource-in-biztalk-application"></a><span data-ttu-id="c7f57-242">加入組件為 BizTalk 應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="c7f57-242">Add an assembly as a resource in BizTalk application</span></span>  
  
1.  <span data-ttu-id="c7f57-243">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c7f57-243">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="c7f57-244">在主控台樹狀目錄中，依序展開**BizTalk 群組**，依序展開**應用程式**，，然後您要新增 BizTalk 組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7f57-244">In the console tree, expand **BizTalk Group**, expand **Applications**, and then the application to which you want to add a BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="c7f57-245">展開**應用程式**和您要新增 BizTalk 組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7f57-245">Expand **Applications** and the application to which you want to add a BizTalk assembly.</span></span>  
  
4.  <span data-ttu-id="c7f57-246">以滑鼠右鍵按一下**資源**，指向 **新增**，然後按一下  **BizTalk 組件**。</span><span class="sxs-lookup"><span data-stu-id="c7f57-246">Right-click **Resources**, point to **Add**, and then click **BizTalk Assemblies**.</span></span>  
  
5.  <span data-ttu-id="c7f57-247">按一下**新增**、 瀏覽至包含 BizTalk 組件檔案的資料夾中，選取 BizTalk 組件檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="c7f57-247">Click **Add**, navigate to the folder containing the BizTalk assembly file, select the BizTalk assembly file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="c7f57-248">在**選項**，指定安裝至 GAC，BizTalk 組件的選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c7f57-248">In **Options**, specify the options for installing the BizTalk assembly to the GAC, and then click **OK**.</span></span>  
  
##  <span data-ttu-id="c7f57-249"><a name="BKMK_SAPIDOCValidate"></a>從 SAP 系統接收 Idoc 時的驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-249"><a name="BKMK_SAPIDOCValidate"></a> Error in validation while receiving IDOCs from an SAP system</span></span>  
 <span data-ttu-id="c7f57-250">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-250">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-251">從 SAP 系統接收 IDOC 無法驗證具有類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="c7f57-251">An IDOC received from an SAP system fails validation with an error similar to the following:</span></span>  
  
```  
There was a failure executing the receive pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=<token>"  
Source: "Pipeline " Receive Port: "ReceiveIdoc" URI: "<connection uri>"  
Reason: The document failed to validate because of the following error:  
"The 'http://Microsoft.LobServices.Sap/2007/03/Types/Idoc/3/CREMAS03//620:TAXBS' element has an invalid value according to its data type."  
```  
  
 <span data-ttu-id="c7f57-252">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-252">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-253">產生用於接收 IDOC 的中繼資料包含允許的值可以接收特定的資料行，做為接收作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="c7f57-253">The metadata generated for receiving an IDOC contains the permissible values that can be received for a particular column as part of the receive operation.</span></span> <span data-ttu-id="c7f57-254">這些值會公開為產生的中繼資料中的列舉。</span><span class="sxs-lookup"><span data-stu-id="c7f57-254">These values are exposed as enumeration in the generated metadata.</span></span> <span data-ttu-id="c7f57-255">不過，當實際收到的 IDOC，所收到的值可能會不同於列舉值。</span><span class="sxs-lookup"><span data-stu-id="c7f57-255">However, when the IDOC is actually received, the value received could be different from the enumerated values.</span></span> <span data-ttu-id="c7f57-256">因此，接收作業失敗時驗證值。</span><span class="sxs-lookup"><span data-stu-id="c7f57-256">Hence the receive operation fails while validating the values.</span></span> <span data-ttu-id="c7f57-257">例如，在上述錯誤訊息驗證會失敗 TAXBS 資料行。</span><span class="sxs-lookup"><span data-stu-id="c7f57-257">For example, in the above error message validation fails for the TAXBS column.</span></span>  
  
 <span data-ttu-id="c7f57-258">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-258">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-259">您必須手動會包含從 SAP 系統接收到的值編輯結構描述 （適用於 BizTalk 專案） 或用戶端 proxy 中的列舉型別 （適用於.NET 專案使用 WCF 服務模型）。</span><span class="sxs-lookup"><span data-stu-id="c7f57-259">You must manually edit the enumeration in schema (for BizTalk projects) or the client proxy (for .NET projects using WCF service model) to include the value received from the SAP system.</span></span>  
  
##  <span data-ttu-id="c7f57-260"><a name="BKMK_SAPFFIDOC"></a>一般檔案 Idoc 之前和之後轉換成 XML，並不相同</span><span class="sxs-lookup"><span data-stu-id="c7f57-260"><a name="BKMK_SAPFFIDOC"></a> Flat-file IDOCs, before and after converting to XML, are not identical</span></span>  
 <span data-ttu-id="c7f57-261">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-261">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-262">如果您使用一般檔案剖析器使用的結構描述的 XML 轉換成一般檔案 IDOC，再將 XML 轉換回一般檔案 IDOC，透過使用結構描述的管線，兩個一般檔案 Idoc 並不相同。</span><span class="sxs-lookup"><span data-stu-id="c7f57-262">If you use a flat file parser to convert a flat-file IDOC to an XML using the schema, and then convert the XML back to a flat-file IDOC through a pipeline using the schema, the two flat-file IDOCs are not identical.</span></span>  
  
 <span data-ttu-id="c7f57-263">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-263">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-264">當一般檔案 IDOC 產生 XML 時，一般檔案剖析器不會產生 XML 節點會以空白值。</span><span class="sxs-lookup"><span data-stu-id="c7f57-264">When generating the XML from a flat-file IDOC, the flat file parser does not generate the XML nodes with blank values.</span></span> <span data-ttu-id="c7f57-265">當這個 XML 轉換回一般檔案時，XML 中遺漏的節點不會反映在一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="c7f57-265">When this XML is converted back to a flat-file, the nodes missing from the XML are not reflected in the flat-file IDOC.</span></span> <span data-ttu-id="c7f57-266">因此一般檔案 Idoc 並不相同。</span><span class="sxs-lookup"><span data-stu-id="c7f57-266">Hence the flat-file IDOCs are not identical.</span></span>  
  
 <span data-ttu-id="c7f57-267">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-267">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-268">用來轉換成 XML，反之亦然，在 「 傳送 」 或 「 接收 」 節點定義中的 一般檔案結構描述中執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c7f57-268">In the schema used to convert the flat-file to XML and vice-versa, within the "Send" or "Receive" node definition, do the following:</span></span>  
  
1.  <span data-ttu-id="c7f57-269">設定**suppress_empty_nodes**屬性**false**並設定**generate_empty_nodes**屬性**true**。</span><span class="sxs-lookup"><span data-stu-id="c7f57-269">Set the **suppress_empty_nodes** property to **false** and set the **generate_empty_nodes** property to **true**.</span></span> <span data-ttu-id="c7f57-270">根據預設， **suppress_empty_nodes**屬性設定為**true**和**generate_empty_nodes**屬性設定為**false**，和因此在 XML 中不會反映所有空的節點。</span><span class="sxs-lookup"><span data-stu-id="c7f57-270">By default, the **suppress_empty_nodes** property is set to **true** and the **generate_empty_nodes** property is set to **false**, and hence all empty nodes are not reflected in the XML.</span></span>  
  
2.  <span data-ttu-id="c7f57-271">一般檔案可能包含額外歸位字元結尾。</span><span class="sxs-lookup"><span data-stu-id="c7f57-271">The flat-file may contain an extra carriage return at the end.</span></span> <span data-ttu-id="c7f57-272">您可以設定**suppress_trailing_delimiters**屬性**是**若要避免此額外歸位字元。</span><span class="sxs-lookup"><span data-stu-id="c7f57-272">You can set the **suppress_trailing_delimiters** property to **Yes** to avoid this extra carriage return.</span></span> <span data-ttu-id="c7f57-273">這個屬性也會公開成**隱藏尾端分隔符號**屬性，如果您開啟中的結構描述[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-273">This property is also exposed as the **Suppress Trailing Delimiters** property if you open the schema in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
##  <span data-ttu-id="c7f57-274"><a name="BKMK_SAPAction"></a>使用建立與繫結檔案的實體通訊埠不正確的動作時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-274"><a name="BKMK_SAPAction"></a> Incorrect Action error using a physical port creating with a binding file</span></span>  
 <span data-ttu-id="c7f57-275">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-275">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-276">使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生 SAP 系統上的特定作業的結構描述，增益集也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="c7f57-276">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the SAP system, the add-in also creates a port binding file.</span></span> <span data-ttu-id="c7f57-277">您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="c7f57-277">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="c7f57-278">不過，當您使用這種連接埠之 SAP 系統傳送訊息，配接器來了解指定的連接埠上的動作失敗，而且會提供類似下面的錯誤：</span><span class="sxs-lookup"><span data-stu-id="c7f57-278">However, when you send messages to the SAP system using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="c7f57-279">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-279">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-280">當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠上的作業，或您只使用類似 Operation_1、 Operation_2 等的預設名稱。不過，在產生的繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是做為您產生中繼資料作業的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c7f57-280">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the operation for which you generate metadata.</span></span> <span data-ttu-id="c7f57-281">比方說，如果您針對 RFC_CUSTOMER_GET 產生中繼資料，動作會設定下列：</span><span class="sxs-lookup"><span data-stu-id="c7f57-281">For example, if you generate metadata for RFC_CUSTOMER_GET, the action will be set to the following:</span></span>  
  
```  
<Operation Name="RFC_CUSTOMER_GET" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
```  
  
 <span data-ttu-id="c7f57-282">當您匯入繫結檔案時，實體連接埠上設定相同的動作。</span><span class="sxs-lookup"><span data-stu-id="c7f57-282">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="c7f57-283">因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符造成錯誤之實體通訊埠，在動作中指定的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="c7f57-283">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="c7f57-284">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-284">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-285">請確定作業中的名稱的邏輯連接埠是實體連接埠中的動作中指定的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c7f57-285">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="c7f57-286">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="c7f57-286">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c7f57-287">產生中繼資料，例如 RFC_CUSTOMER_GET 作業，從 Operation_1 等變更 BizTalk 協調流程中的邏輯連接埠中的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="c7f57-287">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example RFC_CUSTOMER_GET.</span></span>  
  
-   <span data-ttu-id="c7f57-288">將實體連接埠上的動作中的作業名稱變更為中的邏輯連接埠的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="c7f57-288">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="c7f57-289">例如，您可以變更中實體的通訊埠，如下所示的動作：</span><span class="sxs-lookup"><span data-stu-id="c7f57-289">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
    ```  
  
##  <span data-ttu-id="c7f57-290"><a name="BKMK_SAPTableParams"></a>回應訊息的 SAP 上執行的作業不會包含任何資料表參數</span><span class="sxs-lookup"><span data-stu-id="c7f57-290"><a name="BKMK_SAPTableParams"></a> The response message for an operation ran on SAP does not contain any table parameters</span></span>  
 <span data-ttu-id="c7f57-291">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-291">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-292">如果您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]執行 SAP 系統上的作業會傳回大量資料表，以及每個資料表有大量的記錄，將大型資料集做為回應訊息的一部分傳回從 SAP 系統金額。</span><span class="sxs-lookup"><span data-stu-id="c7f57-292">If you use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to execute an operation on the SAP system that returns a large number of tables, and each table has a large number of records, that will amount to a large dataset being returned as part of the response message from the SAP system.</span></span> <span data-ttu-id="c7f57-293">因此，根據預設，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不會傳回資料表中的任何參數做為回應訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="c7f57-293">So, by default, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not return any table parameters as part of the response message.</span></span>  
  
 <span data-ttu-id="c7f57-294">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-294">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-295">您可以要求您想要的資料表[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]傳回回應的過程。</span><span class="sxs-lookup"><span data-stu-id="c7f57-295">You can request the tables that you want [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to return as part of the response.</span></span> <span data-ttu-id="c7f57-296">您可以藉由提供空白資料表參數做為要求訊息傳送至 SAP 系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="c7f57-296">You can do so by providing an empty table parameter as part of the request message that you send to the SAP system.</span></span> <span data-ttu-id="c7f57-297">例如， `<table_parameter_name />`。</span><span class="sxs-lookup"><span data-stu-id="c7f57-297">For example, `<table_parameter_name />`.</span></span>  
  
##  <span data-ttu-id="c7f57-298"><a name="BKMK_SAPIncorrectCreds"></a>配接器用戶端不從 SAP 接收回應</span><span class="sxs-lookup"><span data-stu-id="c7f57-298"><a name="BKMK_SAPIncorrectCreds"></a> Adapter Clients do not receive the response from SAP</span></span>
 <span data-ttu-id="c7f57-299">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-299">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-300">使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果的認證在 WCF 自訂傳送連接埠不正確，無法處理要求訊息。</span><span class="sxs-lookup"><span data-stu-id="c7f57-300">When using the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], if the credentials on the WCF-custom send port are incorrect, the request messages are not processed.</span></span> <span data-ttu-id="c7f57-301">指定正確的認證之後，將訊息傳送到 SAP 系統，並收到回應。</span><span class="sxs-lookup"><span data-stu-id="c7f57-301">After you specify the correct credentials, the message is sent to the SAP system and a response is received.</span></span> <span data-ttu-id="c7f57-302">不過，回應訊息不適用於輸出通訊埠。</span><span class="sxs-lookup"><span data-stu-id="c7f57-302">However, the response message is not available to the out port.</span></span>  
  
 <span data-ttu-id="c7f57-303">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-303">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-304">重新啟動 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7f57-304">Restart the BizTalk host instance.</span></span>  
  
##  <span data-ttu-id="c7f57-305"><a name="BKMK_SAPInboundConn"></a>從 SAP 伺服器接收傳入的訊息的連線問題</span><span class="sxs-lookup"><span data-stu-id="c7f57-305"><a name="BKMK_SAPInboundConn"></a> Connectivity issues receiving an inbound message from the SAP server</span></span>  
 <span data-ttu-id="c7f57-306">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-306">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-307">您收到下列錯誤只有在接收傳入的訊息從 SAP 伺服器使用 Wcf-custom 接收埠，讓時[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-307">You get the following error only while receiving an inbound message from the SAP server using a WCF-Custom receive port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
```  
The Messaging Engine failed to add a receive location "<location_name>" with URL "<connection URI>" to the adapter "WCF-Custom".  
Reason: "Microsoft.Adapters.SAP.RFCException: Details: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  TPNAME=<name>, GWHOST=<host>, GWSERV=<server>  
```  
  
 <span data-ttu-id="c7f57-308">不過，您必須能夠成功地將訊息傳送至 SAP 系統的 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="c7f57-308">However, you are successfully able to send messages to the SAP system using a WCF-Custom send port.</span></span>  
  
 <span data-ttu-id="c7f57-309">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-309">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-310">在您執行配接器用戶端並再試一次接收內送的訊息的相同電腦上安裝 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="c7f57-310">Install the SAP GUI on the same computer where you are running the adapter client and try receiving the inbound message again.</span></span> <span data-ttu-id="c7f57-311">如需如何安裝 SAP GUI 的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="c7f57-311">For more information about how to install the SAP GUI, refer to SAP documentation.</span></span>  
  
##  <span data-ttu-id="c7f57-312"><a name="BKMK_SAPRootNode"></a>RootNode TypeName 在 BizTalk 專案中的錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f57-312"><a name="BKMK_SAPRootNode"></a> Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="c7f57-313">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-313">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-314">在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:</span><span class="sxs-lookup"><span data-stu-id="c7f57-314">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="c7f57-315">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-315">**Resolution**</span></span>  
  
1.  <span data-ttu-id="c7f57-316">以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c7f57-316">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c7f57-317">如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。</span><span class="sxs-lookup"><span data-stu-id="c7f57-317">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
##  <span data-ttu-id="c7f57-318"><a name="BKMK_SAPVS2008"></a>在 Visual Studio 中使用配接器時，無效的繫結警告</span><span class="sxs-lookup"><span data-stu-id="c7f57-318"><a name="BKMK_SAPVS2008"></a> Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="c7f57-319">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-319">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-320">當您使用 Visual Studio 中建立的應用程式的配接器，並開啟配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：</span><span class="sxs-lookup"><span data-stu-id="c7f57-320">When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'sapBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="c7f57-321">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-321">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-322">會出現這個警告，因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結， `sapBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7f57-322">This warning appears because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding, `sapBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="c7f57-323">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-323">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-324">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="c7f57-324">You can safely ignore this warning.</span></span>  
  
##  <span data-ttu-id="c7f57-325"><a name="BKMK_SAPSimilarSchema"></a>在 BizTalk Server 的 XLANG 例外狀況</span><span class="sxs-lookup"><span data-stu-id="c7f57-325"><a name="BKMK_SAPSimilarSchema"></a> XLANG exception in BizTalk Server</span></span>
 <span data-ttu-id="c7f57-326">**問題**</span><span class="sxs-lookup"><span data-stu-id="c7f57-326">**Problem**</span></span>  
  
 <span data-ttu-id="c7f57-327">XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述比對訊息類型，會擲回 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="c7f57-327">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="c7f57-328">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="c7f57-328">**Cause**</span></span>  
  
 <span data-ttu-id="c7f57-329">這是因為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c7f57-329">This happens because of either of the following:</span></span>  
  
-   <span data-ttu-id="c7f57-330">產生一個以上的 BizTalk Server 專案中，一般作業 （例如 SendIdoc 和 ReceiveIdoc） 結構描述部署至 BizTalk Server 應用程式中，以及然後執行應用程式執行的 SAP 系統上的個別作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-330">You have generated more than one schema of a generic operation (such as SendIdoc and ReceiveIdoc) in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to perform respective operations on an SAP system.</span></span> <span data-ttu-id="c7f57-331">因為結構描述是常見的就會發生衝突的 BizTalk Server 應用程式以部署的結構描述之間。</span><span class="sxs-lookup"><span data-stu-id="c7f57-331">Because the schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
-   <span data-ttu-id="c7f57-332">發生多個專案，您已為每個 BizTalk Server 專案中產生泛型作業結構描述，請部署到個別上相同的 BizTalk Server 應用程式裝載，並再執行應用程式或應用程式執行個別的每個專案SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="c7f57-332">In case of multiple projects, you have generated a generic operation schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to perform respective operations on an SAP system.</span></span> <span data-ttu-id="c7f57-333">因為結構描述和組件都可存取 BizTalk Server 中的應用程式，就會發生衝突之間常見的結構描述部署在不同的 BizTalk Server 應用程式和組件。</span><span class="sxs-lookup"><span data-stu-id="c7f57-333">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
 <span data-ttu-id="c7f57-334">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="c7f57-334">**Resolution**</span></span>  
  
 <span data-ttu-id="c7f57-335">BizTalk Server 應用程式使用單一的一般作業的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="c7f57-335">Use a single generic operation schema file for a BizTalk Server application.</span></span> <span data-ttu-id="c7f57-336">如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用的一般作業的結構描述，建立包含單一的一般作業結構描述的應用程式，然後再使用 BizTalk Server 中的 從所有其他應用程式的一般作業結構描述。</span><span class="sxs-lookup"><span data-stu-id="c7f57-336">If you need to use a generic operation schema in multiple BizTalk Server applications on the same host, create an application containing a single generic operation schema, and then use the generic operation schema from all other applications in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f57-337">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f57-337">See Also</span></span>  
[<span data-ttu-id="c7f57-338">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c7f57-338">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)