---
title: "Siebel BizTalk 配接器疑難排解操作問題 |Microsoft 文件"
description: "常見問題和 Siebel 配接器在 BizTalk 配接器組件 (BAP) 中的解決方式"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d152d9-9893-4f93-894a-350bae8be7bd
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62d1ffae1318f4d04f7bd61ef27dd24fd1d5a2b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-siebel-adapter"></a><span data-ttu-id="24406-103">使用 Siebel 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="24406-103">Troubleshoot Operational Issues with the Siebel adapter</span></span>
<span data-ttu-id="24406-104">本節提供使用時，可能會遇到操作問題的相關資訊的集中式的位置[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-104">This section provides a centralized location for information about operational issues you might encounter when using the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="24406-105">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="24406-105">Enabling Tracing</span></span>  
 <span data-ttu-id="24406-106">如需有關追蹤中的支援資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[診斷追蹤和訊息記錄 Siebel 配接器的](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="24406-106">For information about tracing support in the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Diagnostic Tracing and Message Logging for the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="24406-107">已知問題</span><span class="sxs-lookup"><span data-stu-id="24406-107">Known Issues</span></span>  
 <span data-ttu-id="24406-108">以下是一些問題及使用時可能會遇到的建議的方案[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-108">The following are some issues and recommended solutions that you might encounter while using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
  
###  <span data-ttu-id="24406-109"><a name="BKMK_SiebelBindingError"></a>載入配接器繫結時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="24406-109"><a name="BKMK_SiebelBindingError"></a> Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="24406-110">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-110">**Problem**</span></span>  
  
 <span data-ttu-id="24406-111">當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，GUI 會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="24406-111">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the GUI gives the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="24406-112">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-112">**Cause**</span></span>  
  
 <span data-ttu-id="24406-113">當您啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="24406-113">When you start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="24406-114">接著，配接器繫結會相依於特定企業應用程式用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="24406-114">In turn, the adapter bindings are dependent on the specific enterprise application client software.</span></span> <span data-ttu-id="24406-115">因此，您可能面臨這個問題的一個或兩個原因如下：</span><span class="sxs-lookup"><span data-stu-id="24406-115">So, you could face this issue for one or both of the following reasons:</span></span>  
  
-   <span data-ttu-id="24406-116">將介面卡安裝在電腦上未安裝必要的 LOB 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="24406-116">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
-   <span data-ttu-id="24406-117">未安裝在所有介面卡的配接器的 「 一般 」 或 「 完成 」 安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-117">You did a "Typical" or "Complete" installation of the adapter, which installs all the adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="24406-118">不過，只有一個企業應用程式可能會安裝用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="24406-118">However, the client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="24406-119">如此一來，GUI 無法載入其他配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="24406-119">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="24406-120">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-120">**Resolution**</span></span>  
  
-   <span data-ttu-id="24406-121">請確定您已安裝在電腦上安裝了必要的用戶端版[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-121">Make sure the required client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="24406-122">請確定您執行自訂安裝的配接器安裝您所需要的介面卡。</span><span class="sxs-lookup"><span data-stu-id="24406-122">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
###  <span data-ttu-id="24406-123"><a name="BKMK_SiebelDispAdap"></a>Siebel 配接器不會顯示在 BizTalk Server 管理主控台中的配接器清單</span><span class="sxs-lookup"><span data-stu-id="24406-123"><a name="BKMK_SiebelDispAdap"></a> The Siebel adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="24406-124">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-124">**Problem**</span></span>  
  
 <span data-ttu-id="24406-125">與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ，隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在 BizTalk Server 管理主控台中的配接器清單中。</span><span class="sxs-lookup"><span data-stu-id="24406-125">Unlike the earlier version of the adapters that shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] that shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="24406-126">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-126">**Cause**</span></span>  
  
 <span data-ttu-id="24406-127">最新[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="24406-127">The latest [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="24406-128">因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-128">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
 <span data-ttu-id="24406-129">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-129">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-130">您可以明確加入[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="24406-130">You can explicitly add the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <span data-ttu-id="24406-131"><a name="BKMK_SiebelConnecting"></a>連線至 Siebel 系統時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="24406-131"><a name="BKMK_SiebelConnecting"></a> Error while connecting to the Siebel system</span></span>  
 <span data-ttu-id="24406-132">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-132">**Problem**</span></span>  
  
 <span data-ttu-id="24406-133">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]當您嘗試連接至 Siebel 系統時，會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="24406-133">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] gives the following error when you try to connect to the Siebel system:</span></span>  
  
```  
Connecting to the system LOB has failed. Retrieving the COM class factory for component with CLSID {ID} failed due to the following error: 80040154  
```  
  
 <span data-ttu-id="24406-134">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-134">**Cause**</span></span>  
  
 <span data-ttu-id="24406-135">Siebel Web 用戶端可能未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="24406-135">The Siebel Web client might not be installed on the computer.</span></span>  
  
 <span data-ttu-id="24406-136">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-136">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-137">請確定電腦上安裝 Siebel Web 用戶端的支援的版本。</span><span class="sxs-lookup"><span data-stu-id="24406-137">Make sure the supported version of the Siebel Web client is installed on the computer.</span></span> <span data-ttu-id="24406-138">請參閱支援的用戶端的安裝指南和 siebel 伺服器版本。</span><span class="sxs-lookup"><span data-stu-id="24406-138">Refer to the installation guide for supported client and server versions for Siebel.</span></span> <span data-ttu-id="24406-139">安裝指南位於\<系統磁碟機 >: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="24406-139">The installation guide is available at \<system drive>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
  
###  <span data-ttu-id="24406-140"><a name="BKMK_SiebelXMLRetrieve"></a>具有多個 65536 節點擷取 Xml 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="24406-140"><a name="BKMK_SiebelXMLRetrieve"></a> Error while retrieving XMLs with more than 65536 nodes</span></span>  
 <span data-ttu-id="24406-141">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-141">**Problem**</span></span>  
  
 <span data-ttu-id="24406-142">配接器會提供下列的錯誤，同時擷取有多個 65536 節點的 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="24406-142">The adapter gives the following error while retrieving XML output that has more than 65536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="24406-143">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-143">**Cause**</span></span>  
  
 <span data-ttu-id="24406-144">配接器無法進行序列化和還原序列化物件，超過 65536 的項目。</span><span class="sxs-lookup"><span data-stu-id="24406-144">The adapter cannot serialize and deserialize an object with more than 65536 items.</span></span>  
  
 <span data-ttu-id="24406-145">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-145">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-146">您可以設定來修正此問題`maxItemsInObjectGraph`參數。</span><span class="sxs-lookup"><span data-stu-id="24406-146">You can fix this issue by setting the `maxItemsInObjectGraph` parameter.</span></span> <span data-ttu-id="24406-147">您可以將它設定在任何下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="24406-147">You can set this in any of the following two ways:</span></span>  
  
-   <span data-ttu-id="24406-148">設定此參數，藉由變更`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。</span><span class="sxs-lookup"><span data-stu-id="24406-148">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
-   <span data-ttu-id="24406-149">將下列加入至您的應用程式的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="24406-149">Add the following to your application's app.config file.</span></span>  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 <span data-ttu-id="24406-150">範例 app.config 看起來像：</span><span class="sxs-lookup"><span data-stu-id="24406-150">A sample app.config will look like:</span></span>  
  
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
      <endpoint   behaviorConfiguration="NewBehavior" binding="siebelBinding"  
       contract="IOutboundContract" name="siebel_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
###  <span data-ttu-id="24406-151"><a name="BKMK_SiebelConnURI"></a>在 BizTalk 中指定連線 URI WCF 自訂連接埠時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="24406-151"><a name="BKMK_SiebelConnURI"></a> Error while specifying a connection URI for a WCF-Custom port in BizTalk</span></span>  
 <span data-ttu-id="24406-152">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-152">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="24406-153">當您指定連接至 Siebel 系統連接 URI，請提供下列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="24406-153"> gives the following error when you specify a connection URI to connect to the Siebel system.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="24406-154">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-154">**Cause**</span></span>  
  
 <span data-ttu-id="24406-155">連線 URI 並不依循標準編碼格式。</span><span class="sxs-lookup"><span data-stu-id="24406-155">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="24406-156">例如，參數的值可能會包含空格。</span><span class="sxs-lookup"><span data-stu-id="24406-156">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="24406-157">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-157">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-158">請確定您指定的 URI 符合標準的編碼格式的連接。</span><span class="sxs-lookup"><span data-stu-id="24406-158">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="24406-159">例如，"%20"必須取代的空白區域。</span><span class="sxs-lookup"><span data-stu-id="24406-159">For example, a blank space must be replaced by "%20".</span></span>  
  
###  <span data-ttu-id="24406-160"><a name="BKMK_SiebelPerfOps"></a>Siebel 系統上執行作業時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="24406-160"><a name="BKMK_SiebelPerfOps"></a> Error while performing operation on the Siebel system</span></span>  
 <span data-ttu-id="24406-161">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-161">**Problem**</span></span>  
  
 <span data-ttu-id="24406-162">配接器會產生下列錯誤，執行任何作業在 Siebel 系統使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-162">The adapter gives the following error when performing any operation on the Siebel system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="24406-163">**針對[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="24406-163">**For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**</span></span>  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 <span data-ttu-id="24406-164">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-164">**Cause**</span></span>  
  
 <span data-ttu-id="24406-165">未指定訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="24406-165">The WCF action for the message is not specified.</span></span> <span data-ttu-id="24406-166">WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="24406-166">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="24406-167">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-167">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-168">指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="24406-168">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="24406-169">如需指示，請參閱[設定 Siebel 的 SOAP 動作](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="24406-169">For instructions, see [Configure the SOAP action for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md).</span></span> <span data-ttu-id="24406-170">請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="24406-170">See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation.</span></span>  
  
###  <span data-ttu-id="24406-171"><a name="BKMK_SiebelXmlParsing"></a>XmlReaderParsingException 由於作業名稱中指定的動作</span><span class="sxs-lookup"><span data-stu-id="24406-171"><a name="BKMK_SiebelXmlParsing"></a> XmlReaderParsingException due to an incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="24406-172">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-172">**Problem**</span></span>  
  
 <span data-ttu-id="24406-173">傳送訊息至 Siebel 系統時，BizTalk Server 管理主控台提供下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="24406-173">The BizTalk Server Administration console gives the following error when sending messages to a Siebel system:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="24406-174">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-174">**Cause**</span></span>  
  
 <span data-ttu-id="24406-175">如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：</span><span class="sxs-lookup"><span data-stu-id="24406-175">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="24406-176">在上述格式中，作業名稱係由您產生結構描述時所選擇的作業。</span><span class="sxs-lookup"><span data-stu-id="24406-176">In the preceding format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="24406-177">例如，如果您產生結構描述在 Siebel 商務元件上的查詢作業，動作中的作業名稱會 「 查詢 」。</span><span class="sxs-lookup"><span data-stu-id="24406-177">For example, if you generated schema for a Query operation on a Siebel business component, the operation name in the action will be "Query".</span></span> <span data-ttu-id="24406-178">不過，在 BizTalk 協調流程中建立的邏輯連接埠中的作業名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。</span><span class="sxs-lookup"><span data-stu-id="24406-178">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="24406-179">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-179">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-180">請確定作業名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體通訊埠都相同。</span><span class="sxs-lookup"><span data-stu-id="24406-180">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration console) are the same.</span></span>  
  
###  <span data-ttu-id="24406-181"><a name="BKMK_SiebelTerminate"></a>使用 Siebel 配接器的應用程式不會終止</span><span class="sxs-lookup"><span data-stu-id="24406-181"><a name="BKMK_SiebelTerminate"></a> Application using the Siebel adapter does not terminate</span></span>  
 <span data-ttu-id="24406-182">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-182">**Problem**</span></span>  
  
 <span data-ttu-id="24406-183">使用的應用程式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 7.5 版用戶端不會終止。</span><span class="sxs-lookup"><span data-stu-id="24406-183">An application that uses the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Siebel client version 7.5 does not terminate.</span></span>  
  
 <span data-ttu-id="24406-184">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-184">**Cause**</span></span>  
  
 <span data-ttu-id="24406-185">這是因為 Siebel 用戶端問題處理序無法從 Siebel 伺服器登出時結束。</span><span class="sxs-lookup"><span data-stu-id="24406-185">This is because of a Siebel client issue where the process does not terminate when logging off from a Siebel server.</span></span>  
  
 <span data-ttu-id="24406-186">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-186">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-187">請確定您已安裝 Siebel 伺服器，以及快速檢修 QF0H05 7.5.3.17 修補程式。</span><span class="sxs-lookup"><span data-stu-id="24406-187">Make sure you have the patch 7.5.3.17 installed for the Siebel server, along with the quick fix QF0H05.</span></span>  
  
###  <span data-ttu-id="24406-188"><a name="BKMK_SiebelHang"></a>Siebel 配接器可能會停止回應，如果 Siebel 伺服器重新啟動</span><span class="sxs-lookup"><span data-stu-id="24406-188"><a name="BKMK_SiebelHang"></a> Siebel adapter may hang if the Siebel server is restarted</span></span>  
 <span data-ttu-id="24406-189">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-189">**Problem**</span></span>  
  
 <span data-ttu-id="24406-190">如果 Siebel 伺服器重新啟動時[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]正在傳送訊息到 Siebel 伺服器使用，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可能會停止回應。</span><span class="sxs-lookup"><span data-stu-id="24406-190">If the Siebel server is restarted while the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is sending a message to the Siebel server using, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] may hang.</span></span>  
  
 <span data-ttu-id="24406-191">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-191">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-192">重新啟動 BizTalk 應用程式主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="24406-192">Restart the BizTalk application host instance.</span></span> <span data-ttu-id="24406-193">若要這樣做從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在主控台樹狀目錄中展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="24406-193">To do so from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, in the console tree expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="24406-194">從右窗格中，以滑鼠右鍵按一下 主機名稱，然後選取**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="24406-194">From the right pane, right-click the host name, and then select **Restart**.</span></span>  
  
###  <span data-ttu-id="24406-195"><a name="BKMK_SiebelAction"></a>配接器無法辨識的實體通訊埠上的動作，即使您使用 取用配接器服務增益集所產生的繫結檔案建立連接埠</span><span class="sxs-lookup"><span data-stu-id="24406-195"><a name="BKMK_SiebelAction"></a> The adapter does not recognize the action on the physical port even though you use the binding file generated by the Consume Adapter Service add-in to create the ports</span></span>  
 <span data-ttu-id="24406-196">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-196">**Problem**</span></span>  
  
 <span data-ttu-id="24406-197">使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生 Siebel 系統的特定作業的結構描述，增益集也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="24406-197">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the Siebel system, the add-in also creates a port binding file.</span></span> <span data-ttu-id="24406-198">您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="24406-198">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="24406-199">不過，當您使用這種連接埠之 Siebel 系統傳送訊息，配接器來了解指定的連接埠上的動作失敗，而且會提供類似下面的錯誤：</span><span class="sxs-lookup"><span data-stu-id="24406-199">However, when you send messages to the Siebel system using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="24406-200">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-200">**Cause**</span></span>  
  
 <span data-ttu-id="24406-201">當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠上的作業，或您只使用類似 Operation_1、 Operation_2 等的預設名稱。不過，在產生的繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是做為您產生中繼資料作業的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="24406-201">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the operation for which you generate metadata.</span></span> <span data-ttu-id="24406-202">比方說，如果您產生帳戶商務元件上的插入作業的中繼資料，動作會設定下列：</span><span class="sxs-lookup"><span data-stu-id="24406-202">For example, if you generate metadata for Insert operation on the Account business component, the action will be set to the following:</span></span>  
  
```  
<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
```  
  
 <span data-ttu-id="24406-203">當您匯入繫結檔案時，實體連接埠上設定相同的動作。</span><span class="sxs-lookup"><span data-stu-id="24406-203">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="24406-204">因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符造成錯誤之實體通訊埠，在動作中指定的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="24406-204">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="24406-205">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-205">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-206">請確定作業中的名稱的邏輯連接埠是實體連接埠中的動作中指定的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="24406-206">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="24406-207">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="24406-207">Do one of the following:</span></span>  
  
-   <span data-ttu-id="24406-208">從 Operation_1 等變更 BizTalk 協調流程中的邏輯連接埠中的作業名稱，您可以為其產生中繼資料，例如 Insert 作業。</span><span class="sxs-lookup"><span data-stu-id="24406-208">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example Insert.</span></span>  
  
-   <span data-ttu-id="24406-209">將實體連接埠上的動作中的作業名稱變更為中的邏輯連接埠的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="24406-209">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="24406-210">例如，您可以變更中實體的通訊埠，如下所示的動作：</span><span class="sxs-lookup"><span data-stu-id="24406-210">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
    ```  
  
###  <span data-ttu-id="24406-211"><a name="BKMK_SiebelXMLEncode"></a>Siebel 配接器不會處理與在名稱中的 XML 編碼字串的 Siebel 物件</span><span class="sxs-lookup"><span data-stu-id="24406-211"><a name="BKMK_SiebelXMLEncode"></a> Siebel adapter does not handle Siebel objects with XML encoded strings in the name</span></span>  
 <span data-ttu-id="24406-212">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-212">**Problem**</span></span>  
  
 <span data-ttu-id="24406-213">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]無法執行作業涉及有編碼的 XML 字串，其名稱中的 Siebel 物件 （商務物件、 商業元件、 商務服務、 挑選清單、 方法、 欄位、 引數、 等等）。</span><span class="sxs-lookup"><span data-stu-id="24406-213">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] cannot perform operations involving Siebel objects (business objects, business components, business services, picklist, methods, fields, arguments, etc) that have XML encoded strings in their name.</span></span> <span data-ttu-id="24406-214">例如，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不能叫用名稱 Time_x0020_Stamp 的商務服務方法。</span><span class="sxs-lookup"><span data-stu-id="24406-214">For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will not be able to invoke a business service method with the name Time_x0020_Stamp.</span></span>  
  
 <span data-ttu-id="24406-215">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-215">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-216">請確定 Siebel 物件不包含其名稱中的 XML 編碼字串。</span><span class="sxs-lookup"><span data-stu-id="24406-216">Make sure the Siebel objects do not contain XML encoded strings in their name.</span></span>  
  
###  <span data-ttu-id="24406-217"><a name="BKMK_SiebelRootNode"></a>RootNode TypeName 在 BizTalk 專案中的錯誤</span><span class="sxs-lookup"><span data-stu-id="24406-217"><a name="BKMK_SiebelRootNode"></a> Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="24406-218">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-218">**Problem**</span></span>  
  
 <span data-ttu-id="24406-219">在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:</span><span class="sxs-lookup"><span data-stu-id="24406-219">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="24406-220">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-220">**Resolution**</span></span>  
  
1.  <span data-ttu-id="24406-221">以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="24406-221">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="24406-222">如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。</span><span class="sxs-lookup"><span data-stu-id="24406-222">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <span data-ttu-id="24406-223"><a name="BKMK_SiebelVS2008"></a>在 Visual Studio 中使用配接器時，無效的繫結警告</span><span class="sxs-lookup"><span data-stu-id="24406-223"><a name="BKMK_SiebelVS2008"></a> Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="24406-224">**問題**</span><span class="sxs-lookup"><span data-stu-id="24406-224">**Problem**</span></span>  
  
 <span data-ttu-id="24406-225">當您建立的應用程式中使用配接器[!INCLUDE[vs2010](../../includes/vs2010-md.md)]並開啟配接器所產生的組態檔 (app.config)，您會看到類似下列的警告：</span><span class="sxs-lookup"><span data-stu-id="24406-225">When you use the adapter to create an application in [!INCLUDE[vs2010](../../includes/vs2010-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'siebelBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="24406-226">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="24406-226">**Cause**</span></span>  
  
 <span data-ttu-id="24406-227">會出現這個警告，因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結， `siebelBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24406-227">This warning appears because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding, `siebelBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="24406-228">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="24406-228">**Resolution**</span></span>  
  
 <span data-ttu-id="24406-229">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="24406-229">You can safely ignore this warning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24406-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24406-230">See Also</span></span>  
[<span data-ttu-id="24406-231">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="24406-231">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)