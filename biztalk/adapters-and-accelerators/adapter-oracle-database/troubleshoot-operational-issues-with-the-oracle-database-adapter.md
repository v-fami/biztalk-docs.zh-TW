---
title: 針對使用 Oracle 資料庫配接器的操作問題進行疑難排解 |Microsoft Docs
description: 常見問題和解決方案的 Oracle 資料庫配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fb83245-2b6a-48cc-8601-b923bb009a58
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dfe903e897ebc3d26e6dc380233f80253ddfc5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968415"
---
# <a name="troubleshoot-operational-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="3bb69-103">針對使用 Oracle 資料庫配接器的操作問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3bb69-103">Troubleshoot operational issues with the Oracle Database adapter</span></span>
<span data-ttu-id="3bb69-104">疑難排解技術來解決您可能會遇到使用的操作錯誤[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-104">Troubleshooting techniques to resolve operational errors that you may experience using [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="enable-tracing"></a><span data-ttu-id="3bb69-105">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="3bb69-105">Enable tracing</span></span>  
 <span data-ttu-id="3bb69-106">如需有關追蹤中的支援資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 診斷追蹤和訊息記錄的 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb69-106">For information about tracing support in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Diagnostic tracing and message logging for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="3bb69-107">已知問題</span><span class="sxs-lookup"><span data-stu-id="3bb69-107">Known Issues</span></span>  
 <span data-ttu-id="3bb69-108">以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，以及其可能的原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="3bb69-108">The following are the most common errors you might encounter when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], along with their probable cause and resolution.</span></span>   
  
### <a name="BKMK_OraDBLoading"></a> <span data-ttu-id="3bb69-109">載入配接器繫結時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3bb69-109">Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="3bb69-110">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-110">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-111">當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3bb69-111">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="3bb69-112">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-112">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-113">當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="3bb69-113">When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="3bb69-114">接著，配接器繫結均依存於企業應用程式特定的用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="3bb69-114">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="3bb69-115">您可能會面臨此問題的一個或兩個原因如下：</span><span class="sxs-lookup"><span data-stu-id="3bb69-115">You might face this issue for one or both of the following reasons:</span></span>  
  
- <span data-ttu-id="3bb69-116">在您安裝配接器的電腦上未安裝必要的 LOB 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="3bb69-116">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
- <span data-ttu-id="3bb69-117">未安裝中包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-117">You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="3bb69-118">不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="3bb69-118">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="3bb69-119">如此一來，GUI 無法載入其他配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="3bb69-119">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
  <span data-ttu-id="3bb69-120">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-120">**Resolution**</span></span>  
  
- <span data-ttu-id="3bb69-121">請確定所需的 LOB 用戶端版本已安裝在您安裝的電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-121">Make sure that the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="3bb69-122">[支援的營運 (LOB) 和企業系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的用戶端版本。</span><span class="sxs-lookup"><span data-stu-id="3bb69-122">[Supported Line-of-Business (LOB) and Enterprise systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported client versions.</span></span>  
  
- <span data-ttu-id="3bb69-123">請確定您執行自訂安裝來安裝您所需要的介面卡的介面卡。</span><span class="sxs-lookup"><span data-stu-id="3bb69-123">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="3bb69-124">若要確定您的應用程式會使用 ODP.NET 的最新版本，您必須擁有 「 原則 Dll 」 的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="3bb69-124">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="3bb69-125">如需詳細資訊，請參閱 <<c0> [ 適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 網站上。</span><span class="sxs-lookup"><span data-stu-id="3bb69-125">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.</span></span>  
  
###  <a name="BKMK_OraDBAdapDisplay"></a> <span data-ttu-id="3bb69-126">Oracle 資料庫配接器不會顯示在清單中，BizTalk Server 管理主控台中的配接器</span><span class="sxs-lookup"><span data-stu-id="3bb69-126">The Oracle database adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="3bb69-127">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-127">**Problem**</span></span>  
  
<span data-ttu-id="3bb69-128">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未列在 BizTalk Server 管理主控台中的配接器清單。</span><span class="sxs-lookup"><span data-stu-id="3bb69-128">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] inlcuded with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is not listed in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="3bb69-129">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-129">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-130">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="3bb69-130">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="3bb69-131">因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結，因此，不會顯示以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-131">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
 <span data-ttu-id="3bb69-132">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-132">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-133">您可以明確加入[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb69-133">You can explicitly add the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <a name="BKMK_OraDBXMLRetrieve"></a> <span data-ttu-id="3bb69-134">擷取具有超過 65536 節點的 XML 輸出時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3bb69-134">Error while retrieving XML output with more than 65,536 nodes</span></span>  
 <span data-ttu-id="3bb69-135">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-135">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-136">擷取 XML 輸出，具有超過 65536 的節點時，配接器就會產生下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="3bb69-136">The adapter gives the following error when retrieving XML output that has more than 65,536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="3bb69-137">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-137">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-138">配接器無法序列化和還原序列化的物件超過 65536 個項目。</span><span class="sxs-lookup"><span data-stu-id="3bb69-138">The adapter cannot serialize and deserialize an object with more than 65,536 items.</span></span>  
  
 <span data-ttu-id="3bb69-139">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-139">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-140">您可以修正此問題，藉由設定`maxItemsInObjectGraph`參數。</span><span class="sxs-lookup"><span data-stu-id="3bb69-140">You can fix this issue by setting the `maxItemsInObjectGraph` parameter.</span></span> <span data-ttu-id="3bb69-141">您可以將它設定在下列兩種方式之一：</span><span class="sxs-lookup"><span data-stu-id="3bb69-141">You can set this in either of the following two ways:</span></span>  
  
- <span data-ttu-id="3bb69-142">設定此參數，進而`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。</span><span class="sxs-lookup"><span data-stu-id="3bb69-142">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
- <span data-ttu-id="3bb69-143">將下列內容新增至您的應用程式的 app.config 檔。</span><span class="sxs-lookup"><span data-stu-id="3bb69-143">Add the following to your application's app.config file.</span></span>  
  
  ```  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="NewBehavior">  
        <dataContractSerializer maxItemsInObjectGraph="65536000" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  ```  
  
  <span data-ttu-id="3bb69-144">範例 app.config 看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="3bb69-144">A sample app.config looks like this.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="oracleDBBinding"  
       contract="IOutboundContract" name="oracle_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_OraDBPerfOps"></a> <span data-ttu-id="3bb69-145">執行的 Oracle 資料庫上的作業時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3bb69-145">Error while performing operations on the Oracle database</span></span>  
 <span data-ttu-id="3bb69-146">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-146">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-147">執行 Oracle 資料庫使用的任何作業時，配接器會提供下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-147">The adapter gives the following error when performing any operation on the Oracle database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
- <span data-ttu-id="3bb69-148">**BizTalk server**</span><span class="sxs-lookup"><span data-stu-id="3bb69-148">**For BizTalk Server**</span></span>  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  <span data-ttu-id="3bb69-149">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-149">**Cause**</span></span>  
  
  <span data-ttu-id="3bb69-150">未指定訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="3bb69-150">The WCF action for the message is not specified.</span></span> <span data-ttu-id="3bb69-151">WCF 會需要為每個作業，因為它會通知配接器要在 LOB 應用程式上執行的作業指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="3bb69-151">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
  <span data-ttu-id="3bb69-152">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-152">**Resolution**</span></span>  
  
  <span data-ttu-id="3bb69-153">指定的 SOAP 動作，傳送埠中或在 BizTalk 協調流程中的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="3bb69-153">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="3bb69-154">如需相關指示，請參閱 <<c0> [ 設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb69-154">For instructions, see [Configure the SOAP action for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md).</span></span> <span data-ttu-id="3bb69-155">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)以查看每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="3bb69-155">See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) to see a list of actions for each operation.</span></span>  
  
###  <a name="BKMK_OraDBXmlParsing"></a> <span data-ttu-id="3bb69-156">因為不正確的作業名稱中指定的動作而 XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="3bb69-156">XmlReaderParsingException due to an incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="3bb69-157">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-157">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-158">傳送訊息到 Oracle 資料庫時，BizTalk Server 管理主控台就會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3bb69-158">The BizTalk Server Administration Console gives the following error when sending messages to an Oracle database:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="3bb69-159">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-159">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-160">如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：</span><span class="sxs-lookup"><span data-stu-id="3bb69-160">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="3bb69-161">上述的格式，作業名稱係由您選擇在產生結構描述時的作業。</span><span class="sxs-lookup"><span data-stu-id="3bb69-161">In the above format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="3bb69-162">比方說，如果您產生結構描述的資料表上的插入作業時，動作中的作業名稱會是 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="3bb69-162">For example, if you generated schema for the Insert operation on a table, the operation name in the action will be "Insert".</span></span> <span data-ttu-id="3bb69-163">不過，作業名稱的邏輯連接埠中建立 BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。</span><span class="sxs-lookup"><span data-stu-id="3bb69-163">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="3bb69-164">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-164">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-165">請確定作業的名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體連接埠都相同。</span><span class="sxs-lookup"><span data-stu-id="3bb69-165">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration Console) are same.</span></span>  
  
###  <a name="BKMK_OraDBConnURI"></a> <span data-ttu-id="3bb69-166">在 BizTalk 中指定的 WCF 自訂連接埠的連線 URI 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3bb69-166">Error while specifying a connection URI for a WCF-Custom port in BizTalk</span></span>  
 <span data-ttu-id="3bb69-167">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-167">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3bb69-168"> 當您指定的連接來連接到 Oracle 資料庫的 URI 時，請提供下列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3bb69-168"> gives the following error when you specify a connection URI to connect to the Oracle database.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="3bb69-169">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-169">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-170">連線 URI 不會遵守標準的編碼格式。</span><span class="sxs-lookup"><span data-stu-id="3bb69-170">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="3bb69-171">例如，參數的值可能會包含空格。</span><span class="sxs-lookup"><span data-stu-id="3bb69-171">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="3bb69-172">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-172">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-173">請確定您指定的 URI 符合標準的編碼格式的連接。</span><span class="sxs-lookup"><span data-stu-id="3bb69-173">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="3bb69-174">例如，"%20"必須取代空格。</span><span class="sxs-lookup"><span data-stu-id="3bb69-174">For example, a blank space must be replaced by "%20".</span></span>  
  
###  <a name="BKMK_OraDBInvalCursor"></a> <span data-ttu-id="3bb69-175">無效的資料指標時叫用使用 REF CURSOR 參數的預存程序的例外狀況</span><span class="sxs-lookup"><span data-stu-id="3bb69-175">Invalid cursor exception while invoking stored procedures that take REF CURSOR parameters</span></span>  
 <span data-ttu-id="3bb69-176">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-176">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-177">當您叫用 Oracle 資料庫中採用 REF CURSOR 輸入的程序時，您可能會收到下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="3bb69-177">When you invoke procedures in the Oracle database that take REF CURSOR inputs, you might get the following exception:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.TargetSystemException: ORA-01001: invalid cursor ---> Oracle.DataAccess.Client.OracleException  
```  
  
 <span data-ttu-id="3bb69-178">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-178">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-179">您所叫用的程序的 PL/SQL 區塊無法使用 REF 資料指標，也就是在 REF CURSOR，可以取得指派給出 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="3bb69-179">The PL/SQL block for the procedure that you are invoking could be piping the REF CURSORs, that is, the IN REF CURSOR could be getting assigned to the OUT REF CURSOR.</span></span>  
  
 <span data-ttu-id="3bb69-180">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-180">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-181">PL/SQL 區塊必須傳送出 REF 資料指標不適當的處理。</span><span class="sxs-lookup"><span data-stu-id="3bb69-181">The PL/SQL block must not pipe the IN to the OUT REF CURSORs without proper processing.</span></span>  
  
###  <a name="BKMK_OraDBValidateResp"></a> <span data-ttu-id="3bb69-182">驗證使用 BizTalk Server ReadLOB 作業的回應時的錯誤</span><span class="sxs-lookup"><span data-stu-id="3bb69-182">Error while validating the response for the ReadLOB operation using BizTalk Server</span></span>  
 <span data-ttu-id="3bb69-183">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-183">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-184">在執行 ReadLOB 作業使用時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，驗證對 Web 服務描述語言 (WSDL) 的 Oracle 資料庫的回應失敗。</span><span class="sxs-lookup"><span data-stu-id="3bb69-184">While performing a ReadLOB operation using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the response from the Oracle database fails validation against the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="3bb69-185">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-185">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-186">WSDL 會包含定義執行的服務為基礎的要求，但 BizTalk 案例不需要 StreamBody 節點名稱。</span><span class="sxs-lookup"><span data-stu-id="3bb69-186">The WSDL contains a StreamBody node name that is defined for execution of service-based requests, but is not needed for BizTalk scenarios.</span></span> <span data-ttu-id="3bb69-187">因此，輸出 XML，不包含 StreamBody 節點，是相較於 WSDL，驗證將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3bb69-187">Therefore, when the output XML, which does not contain the StreamBody node, is compared with the WSDL, validation fails.</span></span>  
  
 <span data-ttu-id="3bb69-188">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-188">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-189">驗證符合使用 BizTalk Server 所產生的輸出時，則您可以移除 WSDL StreamBody 節點。</span><span class="sxs-lookup"><span data-stu-id="3bb69-189">Remove the StreamBody node from the WSDL when validating against the output that was generated using BizTalk Server.</span></span> <span data-ttu-id="3bb69-190">執行下列步驟來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="3bb69-190">Perform the following steps to do so:</span></span>  
  
1. <span data-ttu-id="3bb69-191">WSDL 包含 StreamBody 節點看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="3bb69-191">The WSDL containing the StreamBody node looks like this.</span></span>  
  
   ```  
   <xs:element name="ReadLOBResponse">  
       <xs:annotation>  
         <xs:documentation>  
           <doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>  
         </xs:documentation>  
       </xs:annotation>  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" nillable="true" type="ns3:StreamBody" />  
         </xs:sequence>  
       </xs:complexType>  
     </xs:element>  
   ```  
  
    <span data-ttu-id="3bb69-192">取代下列前面。</span><span class="sxs-lookup"><span data-stu-id="3bb69-192">Replace the preceding with the following.</span></span>  
  
   ```  
   <xs:element name="ReadLOBResponse">  
    <xs:annotation>  
    <xs:documentation>  
     <doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>   
     </xs:documentation>  
     </xs:annotation>  
    <xs:complexType>  
    <xs:sequence>  
     <xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" type="xs:base64Binary" />   
     </xs:sequence>  
     </xs:complexType>  
     </xs:element>  
   ```  
  
    <span data-ttu-id="3bb69-193">在此步驟中，您會移除輸入參考 = 原始 XSD 中的 「 ns3:StreamBody"並取代類型 ="xs:base64Binary 」。</span><span class="sxs-lookup"><span data-stu-id="3bb69-193">In this step, you removed the reference to type="ns3:StreamBody" in the original XSD and replaced it with type="xs:base64Binary".</span></span> <span data-ttu-id="3bb69-194">此外，您會從原始 XSD 移除 nillable ="true"值。</span><span class="sxs-lookup"><span data-stu-id="3bb69-194">Also, you removed the nillable="true" value from the original XSD.</span></span>  
  
2. <span data-ttu-id="3bb69-195">從 WSDL 中移除下列。</span><span class="sxs-lookup"><span data-stu-id="3bb69-195">Remove the following from the WSDL.</span></span>  
  
   ```  
   <xs:complexType name="StreamBody">  
       <xs:sequence>  
         <xs:element minOccurs="1" maxOccurs="1" name="Stream">  
           <xs:simpleType>  
             <xs:restriction base="xs:base64Binary">  
               <xs:minLength value="0" />  
             </xs:restriction>  
           </xs:simpleType>  
         </xs:element>  
       </xs:sequence>  
     </xs:complexType>  
     <xs:element name="StreamBody" nillable="true" type="ns3:StreamBody" />  
   ```  
  
   > [!NOTE]
   >  <span data-ttu-id="3bb69-196">不支援使用 ReadLOB 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-196">ReadLOB operation is not supported with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3bb69-197">您應該使用資料表的選取作業來讀取從 LOB 資料[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="3bb69-197">You should use a table Select operation to read LOB data from a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
###  <a name="BKMK_OraDBSchemaValidateFail"></a> <span data-ttu-id="3bb69-198">輪詢案例中的結構描述驗證可能會失敗</span><span class="sxs-lookup"><span data-stu-id="3bb69-198">Schema validation may fail in polling scenarios</span></span>  
 <span data-ttu-id="3bb69-199">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-199">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-200">在案例中的結構描述驗證失敗，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢資料庫資料表包含 ROWID 或 UNROWID 類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="3bb69-200">Schema validation fails in scenarios where the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] polls database tables that contain fields of type ROWID or UNROWID.</span></span>  
  
 <span data-ttu-id="3bb69-201">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-201">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-202">在設計階段，當配接器會產生含有 ROWID 或 UNROWID，類型的欄位之資料表的中繼資料結構描述會包含"nillable = false"，這表示 ROWID 或 UNROWID 類型的欄位不可為 null。</span><span class="sxs-lookup"><span data-stu-id="3bb69-202">At design-time, when the adapter generates metadata for the table containing fields of type ROWID or UNROWID, the schema includes “nillable=false”, which means that fields of type ROWID or UNROWID cannot be null.</span></span> <span data-ttu-id="3bb69-203">不過，在執行階段時，配接器擷取的中繼資料，ROWID 或 UNROWID 類型的欄位包含 null 值。</span><span class="sxs-lookup"><span data-stu-id="3bb69-203">However, at run-time when the adapter retrieves the metadata, the fields of type ROWID or UNROWID contain null values.</span></span> <span data-ttu-id="3bb69-204">因此，結構描述驗證會失敗。</span><span class="sxs-lookup"><span data-stu-id="3bb69-204">Hence the schema validation fails.</span></span>  
  
 <span data-ttu-id="3bb69-205">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-205">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-206">如果您使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以選擇停用結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="3bb69-206">If you are using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you may choose to disable schema validation.</span></span> <span data-ttu-id="3bb69-207">或者，您可以手動編輯要變更的結構描述"nillbale = true"ROWID 和 UNROWID 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3bb69-207">Alternatively, you may manually edit the schema to change “nillbale=true” for ROWID and UNROWID data types.</span></span>  
  
###  <a name="BKMK_OraDBUnreasonConv"></a> <span data-ttu-id="3bb69-208">做為參數 '要求不合理 conversion' 錯誤時執行預存的記錄類型的程序</span><span class="sxs-lookup"><span data-stu-id="3bb69-208">'Unreasonable conversion requested' error when executing stored procedures with Record Types as parameters</span></span>  
 <span data-ttu-id="3bb69-209">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-209">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-210">假設其中 Oracle 預存程序會採用記錄類型做為參數。</span><span class="sxs-lookup"><span data-stu-id="3bb69-210">Consider a scenario where an Oracle stored procedure takes a Record Type as a parameter.</span></span> <span data-ttu-id="3bb69-211">記錄類型會宣告為會假設\<資料表名稱\>%資料列型別，在資料表中有很長的資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="3bb69-211">Assume that the Record Type is declared as \<table name\>%ROWTYPE, where the table has a column of LONG data type.</span></span> <span data-ttu-id="3bb69-212">當[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]遇到的長資料型別，它會設定資料類型的大小等於指定的值**LongDatatypeColumnSize**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="3bb69-212">When the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] encounters the LONG data type, it sets the size of the data type equal to the value specified for the **LongDatatypeColumnSize** binding property.</span></span> <span data-ttu-id="3bb69-213">不過，Oracle 資料庫不會定義 LONG 資料類型的大小。</span><span class="sxs-lookup"><span data-stu-id="3bb69-213">However, the Oracle database does not define a size for the LONG data type.</span></span> <span data-ttu-id="3bb69-214">因此，當配接器叫用預存程序，它會導致 '要求不合理 conversion' 錯誤。</span><span class="sxs-lookup"><span data-stu-id="3bb69-214">So, when the adapter invokes the stored procedure, it results in an ‘Unreasonable conversion requested’ error.</span></span>  
  
 <span data-ttu-id="3bb69-215">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-215">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-216">如果記錄類型有 LONG 資料類型，必須明確將它定義為封裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="3bb69-216">If a Record Type has a LONG data type, you must explicitly define it as part of a package.</span></span>  
  
###  <a name="BKMK_OraDBAdapRecognize"></a> <span data-ttu-id="3bb69-217">配接器無法辨識的實體連接埠上的動作，即使您使用 取用配接器服務增益集所產生的繫結檔案建立連接埠</span><span class="sxs-lookup"><span data-stu-id="3bb69-217">The adapter does not recognize the action on the physical port even though you use the binding file generated by the Consume Adapter Service add-in to create the ports</span></span>  
 <span data-ttu-id="3bb69-218">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-218">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-219">使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的 Oracle 資料庫上的特定作業的結構描述，增益集也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="3bb69-219">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the Oracle database, the add-in also creates a port binding file.</span></span> <span data-ttu-id="3bb69-220">您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="3bb69-220">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="3bb69-221">不過，當您將訊息傳送至使用這類連接埠之 Oracle 資料庫時，配接器無法了解指定的連接埠上的動作，並提供類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="3bb69-221">However, when you send messages to the Oracle database using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="3bb69-222">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-222">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-223">當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠的作業，或您只使用預設名稱，例如 Operation_1、 Operation_2 等。不過，在所產生之繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是您要為其產生中繼資料的 Oracle 資料庫作業的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="3bb69-223">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the Oracle database operation for which you generate metadata.</span></span> <span data-ttu-id="3bb69-224">比方說，如果您的 Oracle 資料庫中產生 ACCOUNTACTIVITY 資料表上的選取作業的中繼資料，動作會設定如下：</span><span class="sxs-lookup"><span data-stu-id="3bb69-224">For example, if you generate metadata for Select operation on ACCOUNTACTIVITY table in the Oracle database, the action will be set to the following:</span></span>  
  
```  
<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
```  
  
 <span data-ttu-id="3bb69-225">當您匯入繫結檔案時，實體連接埠上設定相同的動作。</span><span class="sxs-lookup"><span data-stu-id="3bb69-225">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="3bb69-226">因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符的實體連接埠，導致錯誤的動作中指定的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="3bb69-226">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="3bb69-227">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-227">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-228">請確定作業中的名稱的邏輯連接埠是與實體連接埠中的動作中指定的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="3bb69-228">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="3bb69-229">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="3bb69-229">Do one of the following:</span></span>  
  
-   <span data-ttu-id="3bb69-230">變更從 Operation_1 等的 BizTalk 協調流程中的邏輯連接埠中的作業名稱，您要為其產生中繼資料，例如選取作業。</span><span class="sxs-lookup"><span data-stu-id="3bb69-230">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example Select.</span></span>  
  
-   <span data-ttu-id="3bb69-231">將邏輯連接埠中的作業名稱的實體連接埠動作中的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="3bb69-231">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="3bb69-232">例如，您可以變更如下所示的實體連接埠中的動作：</span><span class="sxs-lookup"><span data-stu-id="3bb69-232">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
    ```  
  
###  <a name="BKMK_OraDBOverflowExcep"></a> <span data-ttu-id="3bb69-233">配接器會擲回溢位例外狀況 (「 System.OverflowException") 上執行作業</span><span class="sxs-lookup"><span data-stu-id="3bb69-233">Adapter throws an overflow exception (“System.OverflowException”) on executing an operation</span></span>  
 <span data-ttu-id="3bb69-234">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-234">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-235">如果您嘗試執行包含 Oracle 資料集或弱式型別 REF 資料指標內的數值資料類型的作業，請使用配接器，配接器可能會擲回溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3bb69-235">Using the adapter, if you try to perform an operation containing Oracle numeric data types inside DataSets or weakly-typed REF CURSORS, the adapter might throw an overflow exception.</span></span>  
  
 <span data-ttu-id="3bb69-236">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-236">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-237">會發生這種情況是如果您提供 Oracle 數值資料類型資料集或弱式型別 REF CURSOR 無法放入個別的.NET 型別內的較大的值。</span><span class="sxs-lookup"><span data-stu-id="3bb69-237">This happens if you supply a large value for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS that cannot fit into the respective .NET type.</span></span>  
  
 <span data-ttu-id="3bb69-238">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-238">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-239">如果您想要將大型值傳給資料集或弱式型別 REF 資料指標內的 Oracle 數值資料類型，您必須啟用 「 安全輸入的值設定**EnableSafeTyping**繫結屬性**true**.</span><span class="sxs-lookup"><span data-stu-id="3bb69-239">If you want to pass large values for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS, you must enable safe typing by setting the value of the **EnableSafeTyping** binding property to **true**.</span></span> <span data-ttu-id="3bb69-240">啟用 「 安全輸入公開在資料集或弱式型別 REF CURSOR 的 Oracle 數值資料型別為字串。</span><span class="sxs-lookup"><span data-stu-id="3bb69-240">Enabling safe typing exposes the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS as strings.</span></span>  
  
###  <a name="BKMK_OraDBRootNode"></a> <span data-ttu-id="3bb69-241">在 BizTalk 專案中的根節點類型名稱錯誤</span><span class="sxs-lookup"><span data-stu-id="3bb69-241">Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="3bb69-242">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-242">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-243">在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:</span><span class="sxs-lookup"><span data-stu-id="3bb69-243">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="3bb69-244">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-244">**Resolution**</span></span>  
  
1.  <span data-ttu-id="3bb69-245">以滑鼠右鍵按一下參考錯誤，然後選取 rood 節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3bb69-245">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="3bb69-246">針對**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。</span><span class="sxs-lookup"><span data-stu-id="3bb69-246">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <a name="BKMK_OraDBInvalBinding"></a> <span data-ttu-id="3bb69-247">在 Visual Studio 中使用配接器時，會產生無效的繫結警告。</span><span class="sxs-lookup"><span data-stu-id="3bb69-247">Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="3bb69-248">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-248">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-249">當您建立應用程式中的使用配接器時[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]和開啟配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：</span><span class="sxs-lookup"><span data-stu-id="3bb69-249">When you use the adapter to create an application in [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'oracleDBBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="3bb69-250">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-250">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-251">會出現這個警告，因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結`oracleDBBinding`，沒有標準繫結隨附[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3bb69-251">This warning appears because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding, `oracleDBBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="3bb69-252">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-252">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-253">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="3bb69-253">You can safely ignore this warning.</span></span>  
  
###  <a name="BKMK_OraDBNotification"></a> <span data-ttu-id="3bb69-254">如果您在相同的應用程式中使用一個以上的通知結構描述，或在相同主機上的多個應用程式之間，使用通知結構描述，BizTalk Server 擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="3bb69-254">BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host</span></span>  
 <span data-ttu-id="3bb69-255">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-255">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-256">XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述符合訊息類型，會擲回 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="3bb69-256">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="3bb69-257">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-257">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-258">這是因為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3bb69-258">This happens because of either of the following:</span></span>  
  
- <span data-ttu-id="3bb69-259">當您產生一個以上的通知結構描述在 BizTalk Server 專案中，將它部署到 BizTalk Server 應用程式，然後執行應用程式要從 Oracle 資料庫接收通知。</span><span class="sxs-lookup"><span data-stu-id="3bb69-259">You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the Oracle database.</span></span> <span data-ttu-id="3bb69-260">因為通知結構描述是常見的就會發生衝突之間會部署在 BizTalk Server 應用程式中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3bb69-260">Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
- <span data-ttu-id="3bb69-261">發生多個專案，方法，您可以有為每個部署的專案，每個專案加入個別的 BizTalk Server 應用程式相同的主機上的 BizTalk Server 產生通知結構描述，並接著執行應用程式或應用程式收到的通知Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3bb69-261">In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the Oracle database.</span></span> <span data-ttu-id="3bb69-262">因為結構描述和組件都是可存取 BizTalk Server 中的應用程式，就會發生衝突之間通用的結構描述部署在各種 BizTalk Server 應用程式和組件。</span><span class="sxs-lookup"><span data-stu-id="3bb69-262">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
  <span data-ttu-id="3bb69-263">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-263">**Resolution**</span></span>  
  
  <span data-ttu-id="3bb69-264">使用 BizTalk Server 應用程式的單一通知結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="3bb69-264">Use a single Notification schema file for a BizTalk Server application.</span></span> <span data-ttu-id="3bb69-265">如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一的通知結構描述中，應用程式，然後使用 BizTalk Server 中的 從其他所有應用程式的通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="3bb69-265">If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.</span></span>  
  
###  <a name="BKMK_MemUsage"></a> <span data-ttu-id="3bb69-266">記憶體使用量和執行緒計數增加而增加時使用中交易的輸入作業的配接器</span><span class="sxs-lookup"><span data-stu-id="3bb69-266">Memory usage and thread count increases when using the adapter in a transacted inbound operation</span></span>  
 <span data-ttu-id="3bb69-267">**問題**</span><span class="sxs-lookup"><span data-stu-id="3bb69-267">**Problem**</span></span>  
  
 <span data-ttu-id="3bb69-268">在交易輸入作業中，輪詢，例如**是否有可用在所輪詢的資料表中的任何資料**和配接器會持續輪詢，經過一段時間中，您遇到增加的記憶體使用量和執行緒計數。</span><span class="sxs-lookup"><span data-stu-id="3bb69-268">In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.</span></span>  
  
 <span data-ttu-id="3bb69-269">**原因**</span><span class="sxs-lookup"><span data-stu-id="3bb69-269">**Cause**</span></span>  
  
 <span data-ttu-id="3bb69-270">**如果沒有資料輪詢的資料表中可用**之後，每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]會繁衍新的執行緒，以繼續輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="3bb69-270">**If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation.</span></span> <span data-ttu-id="3bb69-271">因此，執行緒計數和記憶體使用量會增加一段時間。</span><span class="sxs-lookup"><span data-stu-id="3bb69-271">Hence, the thread count and memory usage increases over a period of time.</span></span> <span data-ttu-id="3bb69-272">不過，如果輪詢的資料表會有一些資料，相同的執行緒會繼續執行所有的後續輪詢。</span><span class="sxs-lookup"><span data-stu-id="3bb69-272">However, if the table being polled has some data, the same thread continues to perform all subsequent polls.</span></span>  
  
 <span data-ttu-id="3bb69-273">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="3bb69-273">**Resolution**</span></span>  
  
 <span data-ttu-id="3bb69-274">我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （也就是 24 天），讓新的執行緒會繁衍只能每隔 24 天。</span><span class="sxs-lookup"><span data-stu-id="3bb69-274">We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days.</span></span> <span data-ttu-id="3bb69-275">這可確保，記憶體使用量和執行緒計數不會變得太多太快。</span><span class="sxs-lookup"><span data-stu-id="3bb69-275">This will ensure that the memory usage and thread count does not grow too much too soon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bb69-276">如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 也會設定為 最大可能的值，也就是 24.20:31:23.6470000 （也就是 24 天）。</span><span class="sxs-lookup"><span data-stu-id="3bb69-276">If SqlAdapterInboundTransactionBehavior has been set, make sure the TransactionTimeout is also configured to maximum possible value, which is 24.20:31:23.6470000 (24 days).</span></span> <span data-ttu-id="3bb69-277">當使用這個因應措施，我們可以新增 SqlAdapterInboundTransactionBehavior，只有當交易隔離等級必須設。</span><span class="sxs-lookup"><span data-stu-id="3bb69-277">When using this workaround, we can add the SqlAdapterInboundTransactionBehavior only if the transaction isolation level has to be configured.</span></span> <span data-ttu-id="3bb69-278">否則，就移除該行為的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="3bb69-278">Else, it is a best practice to remove that behavior.</span></span>  
  
 <span data-ttu-id="3bb69-279">如需詳細資訊**ReceiveTimeout**繫結屬性，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb69-279">For more information about the **ReceiveTimeout** binding property, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="3bb69-280">如需指定繫結屬性的指示，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb69-280">For instructions on specifying binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bb69-281">使用的介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，逾時設定為較大的值不會影響配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="3bb69-281">When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb69-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb69-282">See Also</span></span>  
[<span data-ttu-id="3bb69-283">Oracle 資料庫配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3bb69-283">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[<span data-ttu-id="3bb69-284">針對使用 Oracle 資料庫配接器的安裝問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3bb69-284">Troubleshoot installation issues with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)