---
title: 疑難排解與 Oracle 資料庫配接器的操作問題 |Microsoft 文件
description: 常見的問題與 Oracle 資料庫配接器在 BizTalk 配接器組件 (BAP) 中的解決方案
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
ms.openlocfilehash: 8ac926a378224e09dce36a52b52c171fb27911b0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010103"
---
# <a name="troubleshoot-operational-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="d48fa-103">疑難排解與 Oracle 資料庫配接器的操作問題</span><span class="sxs-lookup"><span data-stu-id="d48fa-103">Troubleshoot operational issues with the Oracle Database adapter</span></span>
<span data-ttu-id="d48fa-104">疑難排解技術來解決您可能會使用的作業錯誤[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-104">Troubleshooting techniques to resolve operational errors that you may experience using [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="enable-tracing"></a><span data-ttu-id="d48fa-105">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="d48fa-105">Enable tracing</span></span>  
 <span data-ttu-id="d48fa-106">如需有關追蹤中的支援資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[診斷追蹤和 Oracle 資料庫配接器的訊息記錄](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d48fa-106">For information about tracing support in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Diagnostic tracing and message logging for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="d48fa-107">已知問題</span><span class="sxs-lookup"><span data-stu-id="d48fa-107">Known Issues</span></span>  
 <span data-ttu-id="d48fa-108">以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]、 以及它們的可能原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="d48fa-108">The following are the most common errors you might encounter when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], along with their probable cause and resolution.</span></span>   
  
### <a name="BKMK_OraDBLoading"></a><span data-ttu-id="d48fa-109">載入配接器繫結時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d48fa-109">Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="d48fa-110">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-110">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-111">當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="d48fa-111">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="d48fa-112">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-112">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-113">當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="d48fa-113">When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="d48fa-114">接著，配接器繫結會相依於企業應用程式的特定用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="d48fa-114">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="d48fa-115">您可能會面臨這個問題的一個或兩個原因如下：</span><span class="sxs-lookup"><span data-stu-id="d48fa-115">You might face this issue for one or both of the following reasons:</span></span>  
  
-   <span data-ttu-id="d48fa-116">將介面卡安裝在電腦上未安裝必要的 LOB 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="d48fa-116">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
-   <span data-ttu-id="d48fa-117">未安裝中所包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-117">You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d48fa-118">不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="d48fa-118">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="d48fa-119">如此一來，GUI 無法載入其他配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="d48fa-119">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="d48fa-120">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-120">**Resolution**</span></span>  
  
-   <span data-ttu-id="d48fa-121">請確定所需的 LOB 用戶端版本已安裝在您安裝的電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-121">Make sure that the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d48fa-122">[支援的特定業務 (LOB) 和企業系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的用戶端版本。</span><span class="sxs-lookup"><span data-stu-id="d48fa-122">[Supported Line-of-Business (LOB) and Enterprise systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported client versions.</span></span>  
  
-   <span data-ttu-id="d48fa-123">請確定您執行自訂安裝的配接器安裝您所需要的介面卡。</span><span class="sxs-lookup"><span data-stu-id="d48fa-123">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d48fa-124">若要確定您的應用程式的運作方式與 ODP.NET 的最新版本，您必須使用"原則 DLLs"的電腦上安裝並註冊在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="d48fa-124">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="d48fa-125">如需詳細資訊，請參閱[適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 的網站上。</span><span class="sxs-lookup"><span data-stu-id="d48fa-125">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.</span></span>  
  
###  <a name="BKMK_OraDBAdapDisplay"></a><span data-ttu-id="d48fa-126">Oracle 資料庫配接器不會顯示在 BizTalk Server 管理主控台中的配接器清單</span><span class="sxs-lookup"><span data-stu-id="d48fa-126">The Oracle database adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="d48fa-127">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-127">**Problem**</span></span>  
  
<span data-ttu-id="d48fa-128">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]所含與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未列在 BizTalk Server 管理主控台中的配接器清單。</span><span class="sxs-lookup"><span data-stu-id="d48fa-128">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] inlcuded with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is not listed in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="d48fa-129">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-129">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-130">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d48fa-130">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="d48fa-131">因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-131">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
 <span data-ttu-id="d48fa-132">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-132">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-133">您可以明確加入[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="d48fa-133">You can explicitly add the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <a name="BKMK_OraDBXMLRetrieve"></a><span data-ttu-id="d48fa-134">擷取具有超過 65536 節點的 XML 輸出時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d48fa-134">Error while retrieving XML output with more than 65,536 nodes</span></span>  
 <span data-ttu-id="d48fa-135">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-135">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-136">擷取 XML 輸出，已超過 65536 的節點時，配接器會提供下列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d48fa-136">The adapter gives the following error when retrieving XML output that has more than 65,536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="d48fa-137">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-137">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-138">配接器無法進行序列化和還原序列化物件，超過 65536 個項目。</span><span class="sxs-lookup"><span data-stu-id="d48fa-138">The adapter cannot serialize and deserialize an object with more than 65,536 items.</span></span>  
  
 <span data-ttu-id="d48fa-139">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-139">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-140">您可以設定來修正此問題`maxItemsInObjectGraph`參數。</span><span class="sxs-lookup"><span data-stu-id="d48fa-140">You can fix this issue by setting the `maxItemsInObjectGraph` parameter.</span></span> <span data-ttu-id="d48fa-141">您可以將它設定在下列兩種方法之一：</span><span class="sxs-lookup"><span data-stu-id="d48fa-141">You can set this in either of the following two ways:</span></span>  
  
-   <span data-ttu-id="d48fa-142">設定此參數，藉由變更`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。</span><span class="sxs-lookup"><span data-stu-id="d48fa-142">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
-   <span data-ttu-id="d48fa-143">將下列加入至您的應用程式的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="d48fa-143">Add the following to your application's app.config file.</span></span>  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 <span data-ttu-id="d48fa-144">範例 app.config 看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="d48fa-144">A sample app.config looks like this.</span></span>  
  
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
  
###  <a name="BKMK_OraDBPerfOps"></a><span data-ttu-id="d48fa-145">在 Oracle 資料庫上執行作業時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d48fa-145">Error while performing operations on the Oracle database</span></span>  
 <span data-ttu-id="d48fa-146">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-146">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-147">執行 Oracle 資料庫使用中的任何作業時，配接器會產生下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-147">The adapter gives the following error when performing any operation on the Oracle database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d48fa-148">**BizTalk server**</span><span class="sxs-lookup"><span data-stu-id="d48fa-148">**For BizTalk Server**</span></span>  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 <span data-ttu-id="d48fa-149">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-149">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-150">未指定訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="d48fa-150">The WCF action for the message is not specified.</span></span> <span data-ttu-id="d48fa-151">WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="d48fa-151">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="d48fa-152">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-152">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-153">指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="d48fa-153">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="d48fa-154">如需指示，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d48fa-154">For instructions, see [Configure the SOAP action for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md).</span></span> <span data-ttu-id="d48fa-155">請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)若要查看每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="d48fa-155">See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) to see a list of actions for each operation.</span></span>  
  
###  <a name="BKMK_OraDBXmlParsing"></a><span data-ttu-id="d48fa-156">XmlReaderParsingException 由於作業名稱中指定的動作</span><span class="sxs-lookup"><span data-stu-id="d48fa-156">XmlReaderParsingException due to an incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="d48fa-157">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-157">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-158">傳送訊息到 Oracle 資料庫時，BizTalk Server 管理主控台就會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="d48fa-158">The BizTalk Server Administration Console gives the following error when sending messages to an Oracle database:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="d48fa-159">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-159">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-160">如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：</span><span class="sxs-lookup"><span data-stu-id="d48fa-160">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="d48fa-161">在上述格式中，作業名稱係由您產生結構描述時所選擇的作業。</span><span class="sxs-lookup"><span data-stu-id="d48fa-161">In the above format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="d48fa-162">比方說，如果您產生的資料表上的插入作業結構描述，動作中的作業名稱就是 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="d48fa-162">For example, if you generated schema for the Insert operation on a table, the operation name in the action will be "Insert".</span></span> <span data-ttu-id="d48fa-163">不過，在 BizTalk 協調流程中建立的邏輯連接埠中的作業名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。</span><span class="sxs-lookup"><span data-stu-id="d48fa-163">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="d48fa-164">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-164">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-165">請確定作業名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體通訊埠都相同。</span><span class="sxs-lookup"><span data-stu-id="d48fa-165">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration Console) are same.</span></span>  
  
###  <a name="BKMK_OraDBConnURI"></a><span data-ttu-id="d48fa-166">在 BizTalk 中指定連線 URI WCF 自訂連接埠時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d48fa-166">Error while specifying a connection URI for a WCF-Custom port in BizTalk</span></span>  
 <span data-ttu-id="d48fa-167">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-167">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d48fa-168">當您指定 URI 要連接到 Oracle 資料庫的連接，請提供下列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d48fa-168"> gives the following error when you specify a connection URI to connect to the Oracle database.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="d48fa-169">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-169">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-170">連線 URI 並不依循標準編碼格式。</span><span class="sxs-lookup"><span data-stu-id="d48fa-170">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="d48fa-171">例如，參數的值可能會包含空格。</span><span class="sxs-lookup"><span data-stu-id="d48fa-171">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="d48fa-172">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-172">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-173">請確定您指定的 URI 符合標準的編碼格式的連接。</span><span class="sxs-lookup"><span data-stu-id="d48fa-173">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="d48fa-174">例如，"%20"必須取代的空白區域。</span><span class="sxs-lookup"><span data-stu-id="d48fa-174">For example, a blank space must be replaced by "%20".</span></span>  
  
###  <a name="BKMK_OraDBInvalCursor"></a><span data-ttu-id="d48fa-175">無效的資料指標時叫用的 REF CURSOR 參數的預存程序的例外狀況</span><span class="sxs-lookup"><span data-stu-id="d48fa-175">Invalid cursor exception while invoking stored procedures that take REF CURSOR parameters</span></span>  
 <span data-ttu-id="d48fa-176">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-176">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-177">當您叫用的程序的 Oracle 資料庫中 REF CURSOR 的輸入時，您可能會收到下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d48fa-177">When you invoke procedures in the Oracle database that take REF CURSOR inputs, you might get the following exception:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.TargetSystemException: ORA-01001: invalid cursor ---> Oracle.DataAccess.Client.OracleException  
```  
  
 <span data-ttu-id="d48fa-178">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-178">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-179">所叫用的程序的 PL/SQL 區塊無法使用 REF 資料指標，也就是在 REF CURSOR 無法取得指派給出 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="d48fa-179">The PL/SQL block for the procedure that you are invoking could be piping the REF CURSORs, that is, the IN REF CURSOR could be getting assigned to the OUT REF CURSOR.</span></span>  
  
 <span data-ttu-id="d48fa-180">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-180">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-181">PL/SQL 區塊必須不使用管線傳送出 REF 資料指標而不需要適當的處理。</span><span class="sxs-lookup"><span data-stu-id="d48fa-181">The PL/SQL block must not pipe the IN to the OUT REF CURSORs without proper processing.</span></span>  
  
###  <a name="BKMK_OraDBValidateResp"></a><span data-ttu-id="d48fa-182">驗證使用 BizTalk Server ReadLOB 作業的回應時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d48fa-182">Error while validating the response for the ReadLOB operation using BizTalk Server</span></span>  
 <span data-ttu-id="d48fa-183">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-183">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-184">執行 ReadLOB 作業使用時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，從 Oracle 資料庫回應驗證對 Web 服務描述語言 (WSDL) 失敗。</span><span class="sxs-lookup"><span data-stu-id="d48fa-184">While performing a ReadLOB operation using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the response from the Oracle database fails validation against the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="d48fa-185">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-185">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-186">WSDL 會包含定義為執行的服務為基礎的要求，但不需要使用 BizTalk 案例 StreamBody 節點名稱。</span><span class="sxs-lookup"><span data-stu-id="d48fa-186">The WSDL contains a StreamBody node name that is defined for execution of service-based requests, but is not needed for BizTalk scenarios.</span></span> <span data-ttu-id="d48fa-187">因此，當輸出 XML，不包含 StreamBody 節點，相較於 WSDL，驗證將會失敗。</span><span class="sxs-lookup"><span data-stu-id="d48fa-187">Therefore, when the output XML, which does not contain the StreamBody node, is compared with the WSDL, validation fails.</span></span>  
  
 <span data-ttu-id="d48fa-188">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-188">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-189">針對使用 BizTalk Server 產生的輸出進行驗證時，請從 WSDL 移除 StreamBody 節點。</span><span class="sxs-lookup"><span data-stu-id="d48fa-189">Remove the StreamBody node from the WSDL when validating against the output that was generated using BizTalk Server.</span></span> <span data-ttu-id="d48fa-190">執行下列步驟來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="d48fa-190">Perform the following steps to do so:</span></span>  
  
1.  <span data-ttu-id="d48fa-191">WSDL 包含 StreamBody 節點看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="d48fa-191">The WSDL containing the StreamBody node looks like this.</span></span>  
  
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
  
     <span data-ttu-id="d48fa-192">取代下列前面。</span><span class="sxs-lookup"><span data-stu-id="d48fa-192">Replace the preceding with the following.</span></span>  
  
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
  
     <span data-ttu-id="d48fa-193">您可以在此步驟中，移除型別參考 ="ns3:StreamBody"原始 XSD 中的並取代類型 ="xs: base64binary"。</span><span class="sxs-lookup"><span data-stu-id="d48fa-193">In this step, you removed the reference to type="ns3:StreamBody" in the original XSD and replaced it with type="xs:base64Binary".</span></span> <span data-ttu-id="d48fa-194">此外，您會從原始 XSD 移除 nillable ="true"值。</span><span class="sxs-lookup"><span data-stu-id="d48fa-194">Also, you removed the nillable="true" value from the original XSD.</span></span>  
  
2.  <span data-ttu-id="d48fa-195">移除下列從 WSDL。</span><span class="sxs-lookup"><span data-stu-id="d48fa-195">Remove the following from the WSDL.</span></span>  
  
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
    >  <span data-ttu-id="d48fa-196">不支援的作業 ReadLOB [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-196">ReadLOB operation is not supported with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d48fa-197">您應該用來讀取從 LOB 資料的資料表的 Select 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="d48fa-197">You should use a table Select operation to read LOB data from a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
###  <a name="BKMK_OraDBSchemaValidateFail"></a><span data-ttu-id="d48fa-198">輪詢案例中的結構描述驗證可能會失敗</span><span class="sxs-lookup"><span data-stu-id="d48fa-198">Schema validation may fail in polling scenarios</span></span>  
 <span data-ttu-id="d48fa-199">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-199">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-200">結構描述驗證失敗案例中，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢資料庫資料表，其中包含 ROWID 或 UNROWID 類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="d48fa-200">Schema validation fails in scenarios where the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] polls database tables that contain fields of type ROWID or UNROWID.</span></span>  
  
 <span data-ttu-id="d48fa-201">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-201">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-202">在設計階段時，配接器會產生中繼資料包含 ROWID 或 UNROWID，類型的欄位的資料表結構描述包含"nillable = false"，這表示 ROWID 或 UNROWID 類型的欄位不可為 null。</span><span class="sxs-lookup"><span data-stu-id="d48fa-202">At design-time, when the adapter generates metadata for the table containing fields of type ROWID or UNROWID, the schema includes “nillable=false”, which means that fields of type ROWID or UNROWID cannot be null.</span></span> <span data-ttu-id="d48fa-203">不過，在執行階段時，配接器擷取的中繼資料，ROWID 或 UNROWID 類型的欄位包含 null 值。</span><span class="sxs-lookup"><span data-stu-id="d48fa-203">However, at run-time when the adapter retrieves the metadata, the fields of type ROWID or UNROWID contain null values.</span></span> <span data-ttu-id="d48fa-204">因此，結構描述驗證會失敗。</span><span class="sxs-lookup"><span data-stu-id="d48fa-204">Hence the schema validation fails.</span></span>  
  
 <span data-ttu-id="d48fa-205">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-205">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-206">如果您使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以選擇停用結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="d48fa-206">If you are using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you may choose to disable schema validation.</span></span> <span data-ttu-id="d48fa-207">或者，您可以手動編輯來變更結構描述 」 nillbale = true"ROWID 和 UNROWID 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d48fa-207">Alternatively, you may manually edit the schema to change “nillbale=true” for ROWID and UNROWID data types.</span></span>  
  
###  <a name="BKMK_OraDBUnreasonConv"></a><span data-ttu-id="d48fa-208">做為參數 '要求不合理 conversion' 錯誤時執行預存程記錄類型</span><span class="sxs-lookup"><span data-stu-id="d48fa-208">'Unreasonable conversion requested' error when executing stored procedures with Record Types as parameters</span></span>  
 <span data-ttu-id="d48fa-209">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-209">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-210">假設其中 Oracle 預存程序會採用記錄類型做為參數。</span><span class="sxs-lookup"><span data-stu-id="d48fa-210">Consider a scenario where an Oracle stored procedure takes a Record Type as a parameter.</span></span> <span data-ttu-id="d48fa-211">假設記錄類型宣告為\<資料表名稱\>%rowtype，在資料表有 LONG 資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="d48fa-211">Assume that the Record Type is declared as \<table name\>%ROWTYPE, where the table has a column of LONG data type.</span></span> <span data-ttu-id="d48fa-212">當[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]遇到 LONG 資料類型，它會設定資料類型的大小等於指定的值**LongDatatypeColumnSize**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d48fa-212">When the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] encounters the LONG data type, it sets the size of the data type equal to the value specified for the **LongDatatypeColumnSize** binding property.</span></span> <span data-ttu-id="d48fa-213">不過，Oracle 資料庫並未定義 LONG 資料類型的大小。</span><span class="sxs-lookup"><span data-stu-id="d48fa-213">However, the Oracle database does not define a size for the LONG data type.</span></span> <span data-ttu-id="d48fa-214">因此，當配接器會叫用預存程序，它會導致 '要求不合理 conversion' 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d48fa-214">So, when the adapter invokes the stored procedure, it results in an ‘Unreasonable conversion requested’ error.</span></span>  
  
 <span data-ttu-id="d48fa-215">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-215">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-216">如果記錄類型具有 LONG 資料類型，必須明確將其定義為封裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="d48fa-216">If a Record Type has a LONG data type, you must explicitly define it as part of a package.</span></span>  
  
###  <a name="BKMK_OraDBAdapRecognize"></a><span data-ttu-id="d48fa-217">配接器無法辨識的實體通訊埠上的動作，即使您使用 取用配接器服務增益集所產生的繫結檔案建立連接埠</span><span class="sxs-lookup"><span data-stu-id="d48fa-217">The adapter does not recognize the action on the physical port even though you use the binding file generated by the Consume Adapter Service add-in to create the ports</span></span>  
 <span data-ttu-id="d48fa-218">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-218">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-219">使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]若要產生的 Oracle 資料庫上的特定作業的結構描述，增益集也會建立連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="d48fa-219">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the Oracle database, the add-in also creates a port binding file.</span></span> <span data-ttu-id="d48fa-220">您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="d48fa-220">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="d48fa-221">不過，當您將訊息傳送至使用這種連接埠之 Oracle 資料庫時，配接器無法了解指定的連接埠上的動作，並提供類似下面的錯誤：</span><span class="sxs-lookup"><span data-stu-id="d48fa-221">However, when you send messages to the Oracle database using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="d48fa-222">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-222">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-223">當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠上的作業，或您只使用類似 Operation_1、 Operation_2 等的預設名稱。不過，在產生的繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是做為您產生中繼資料的 Oracle 資料庫作業的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="d48fa-223">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the Oracle database operation for which you generate metadata.</span></span> <span data-ttu-id="d48fa-224">比方說，如果您產生 ACCOUNTACTIVITY 資料表上的選取作業的中繼資料的 Oracle 資料庫中，動作會設定下列：</span><span class="sxs-lookup"><span data-stu-id="d48fa-224">For example, if you generate metadata for Select operation on ACCOUNTACTIVITY table in the Oracle database, the action will be set to the following:</span></span>  
  
```  
<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
```  
  
 <span data-ttu-id="d48fa-225">當您匯入繫結檔案時，實體連接埠上設定相同的動作。</span><span class="sxs-lookup"><span data-stu-id="d48fa-225">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="d48fa-226">因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符造成錯誤之實體通訊埠，在動作中指定的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="d48fa-226">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="d48fa-227">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-227">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-228">請確定作業中的名稱的邏輯連接埠是實體連接埠中的動作中指定的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="d48fa-228">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="d48fa-229">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="d48fa-229">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d48fa-230">從 Operation_1 等變更 BizTalk 協調流程中的邏輯連接埠中的作業名稱，產生中繼資料，例如 Select 作業。</span><span class="sxs-lookup"><span data-stu-id="d48fa-230">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example Select.</span></span>  
  
-   <span data-ttu-id="d48fa-231">將實體連接埠上的動作中的作業名稱變更為中的邏輯連接埠的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="d48fa-231">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="d48fa-232">例如，您可以變更中實體的通訊埠，如下所示的動作：</span><span class="sxs-lookup"><span data-stu-id="d48fa-232">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
    ```  
  
###  <a name="BKMK_OraDBOverflowExcep"></a><span data-ttu-id="d48fa-233">配接器會擲回上執行作業的溢位例外狀況 (「 System.OverflowException")</span><span class="sxs-lookup"><span data-stu-id="d48fa-233">Adapter throws an overflow exception (“System.OverflowException”) on executing an operation</span></span>  
 <span data-ttu-id="d48fa-234">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-234">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-235">如果您嘗試執行包含在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型的作業，請使用配接器，配接器可能會發生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d48fa-235">Using the adapter, if you try to perform an operation containing Oracle numeric data types inside DataSets or weakly-typed REF CURSORS, the adapter might throw an overflow exception.</span></span>  
  
 <span data-ttu-id="d48fa-236">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-236">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-237">會發生這種情況是如果您提供的 Oracle 數值資料類型，在資料集或弱式類型的 REF CURSOR 無法放入個別的.NET 型別之較大的值。</span><span class="sxs-lookup"><span data-stu-id="d48fa-237">This happens if you supply a large value for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS that cannot fit into the respective .NET type.</span></span>  
  
 <span data-ttu-id="d48fa-238">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-238">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-239">如果您想要傳遞的資料集或弱式類型的 REF CURSOR 內 Oracle 數值資料類型的較大的值，您必須啟用 「 安全輸入的值設定**EnableSafeTyping**內容繫結至**true**.</span><span class="sxs-lookup"><span data-stu-id="d48fa-239">If you want to pass large values for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS, you must enable safe typing by setting the value of the **EnableSafeTyping** binding property to **true**.</span></span> <span data-ttu-id="d48fa-240">啟用 「 安全輸入字串的形式公開在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="d48fa-240">Enabling safe typing exposes the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS as strings.</span></span>  
  
###  <a name="BKMK_OraDBRootNode"></a><span data-ttu-id="d48fa-241">RootNode TypeName 在 BizTalk 專案中的錯誤</span><span class="sxs-lookup"><span data-stu-id="d48fa-241">Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="d48fa-242">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-242">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-243">在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:</span><span class="sxs-lookup"><span data-stu-id="d48fa-243">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="d48fa-244">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-244">**Resolution**</span></span>  
  
1.  <span data-ttu-id="d48fa-245">以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d48fa-245">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d48fa-246">如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。</span><span class="sxs-lookup"><span data-stu-id="d48fa-246">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <a name="BKMK_OraDBInvalBinding"></a><span data-ttu-id="d48fa-247">在 Visual Studio 中使用配接器時，無效的繫結警告</span><span class="sxs-lookup"><span data-stu-id="d48fa-247">Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="d48fa-248">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-248">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-249">當您建立的應用程式中使用配接器[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]並開啟配接器所產生的組態檔 (app.config)，您會看到類似下列的警告：</span><span class="sxs-lookup"><span data-stu-id="d48fa-249">When you use the adapter to create an application in [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'oracleDBBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="d48fa-250">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-250">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-251">會出現這個警告，因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結， `oracleDBBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d48fa-251">This warning appears because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding, `oracleDBBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="d48fa-252">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-252">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-253">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="d48fa-253">You can safely ignore this warning.</span></span>  
  
###  <a name="BKMK_OraDBNotification"></a><span data-ttu-id="d48fa-254">如果您使用一個以上的通知結構描述中相同的應用程式或跨多個相同的主機上的應用程式使用通知結構描述，BizTalk Server 擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="d48fa-254">BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host</span></span>  
 <span data-ttu-id="d48fa-255">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-255">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-256">XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述比對訊息類型，會擲回 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="d48fa-256">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="d48fa-257">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-257">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-258">這是因為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d48fa-258">This happens because of either of the following:</span></span>  
  
-   <span data-ttu-id="d48fa-259">產生一個以上的通知結構描述在 BizTalk Server 專案中，部署至 BizTalk Server 應用程式，然後執行應用程式要從 Oracle 資料庫接收通知。</span><span class="sxs-lookup"><span data-stu-id="d48fa-259">You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the Oracle database.</span></span> <span data-ttu-id="d48fa-260">因為通知結構描述是常見的就會發生衝突的 BizTalk Server 應用程式以部署的結構描述之間。</span><span class="sxs-lookup"><span data-stu-id="d48fa-260">Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
-   <span data-ttu-id="d48fa-261">發生多個專案，通知結構描述產生的每個 BizTalk 伺服器，每個專案加入相同主機上，個別的 BizTalk Server 應用程式部署的專案，然後執行應用程式或應用程式收到的通知Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d48fa-261">In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the Oracle database.</span></span> <span data-ttu-id="d48fa-262">因為結構描述和組件都可存取 BizTalk Server 中的應用程式，就會發生衝突之間常見的結構描述部署在不同的 BizTalk Server 應用程式和組件。</span><span class="sxs-lookup"><span data-stu-id="d48fa-262">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
 <span data-ttu-id="d48fa-263">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-263">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-264">BizTalk Server 應用程式使用單一的通知結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="d48fa-264">Use a single Notification schema file for a BizTalk Server application.</span></span> <span data-ttu-id="d48fa-265">如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一通知結構描述時，應用程式，然後再使用 BizTalk Server 中的 從所有其他應用程式的通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="d48fa-265">If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.</span></span>  
  
###  <a name="BKMK_MemUsage"></a><span data-ttu-id="d48fa-266">記憶體使用量和執行緒計數則會增加交易的輸入作業中使用配接器時</span><span class="sxs-lookup"><span data-stu-id="d48fa-266">Memory usage and thread count increases when using the adapter in a transacted inbound operation</span></span>  
 <span data-ttu-id="d48fa-267">**問題**</span><span class="sxs-lookup"><span data-stu-id="d48fa-267">**Problem**</span></span>  
  
 <span data-ttu-id="d48fa-268">在交易輸入作業中，例如輪詢，**是否有可用輪詢資料表中的任何資料**和配接器會持續輪詢，經過一段時間，您遇到的增加記憶體使用量和執行緒計數。</span><span class="sxs-lookup"><span data-stu-id="d48fa-268">In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.</span></span>  
  
 <span data-ttu-id="d48fa-269">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="d48fa-269">**Cause**</span></span>  
  
 <span data-ttu-id="d48fa-270">**如果沒有資料輪詢的資料表中可用**，之後每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]需要產生新的執行緒，以繼續輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="d48fa-270">**If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation.</span></span> <span data-ttu-id="d48fa-271">因此，執行緒計數和記憶體使用量會增加經過一段時間。</span><span class="sxs-lookup"><span data-stu-id="d48fa-271">Hence, the thread count and memory usage increases over a period of time.</span></span> <span data-ttu-id="d48fa-272">不過，如果資料表輪詢有一些資料，在相同的執行緒會繼續執行所有後續輪詢。</span><span class="sxs-lookup"><span data-stu-id="d48fa-272">However, if the table being polled has some data, the same thread continues to perform all subsequent polls.</span></span>  
  
 <span data-ttu-id="d48fa-273">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="d48fa-273">**Resolution**</span></span>  
  
 <span data-ttu-id="d48fa-274">我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （24 天），讓新的執行緒未繁衍只能每隔 24 天。</span><span class="sxs-lookup"><span data-stu-id="d48fa-274">We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days.</span></span> <span data-ttu-id="d48fa-275">這可確保，記憶體使用量和執行緒計數不會成長得太多太快。</span><span class="sxs-lookup"><span data-stu-id="d48fa-275">This will ensure that the memory usage and thread count does not grow too much too soon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d48fa-276">如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 同時設定為最大可能的值，這是 24.20:31:23.6470000 （24 天）。</span><span class="sxs-lookup"><span data-stu-id="d48fa-276">If SqlAdapterInboundTransactionBehavior has been set, make sure the TransactionTimeout is also configured to maximum possible value, which is 24.20:31:23.6470000 (24 days).</span></span> <span data-ttu-id="d48fa-277">當使用這個因應措施，我們可以加入 SqlAdapterInboundTransactionBehavior 才必須設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d48fa-277">When using this workaround, we can add the SqlAdapterInboundTransactionBehavior only if the transaction isolation level has to be configured.</span></span> <span data-ttu-id="d48fa-278">否則，就移除該行為的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d48fa-278">Else, it is a best practice to remove that behavior.</span></span>  
  
 <span data-ttu-id="d48fa-279">如需有關**ReceiveTimeout**繫結屬性，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d48fa-279">For more information about the **ReceiveTimeout** binding property, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="d48fa-280">如需指定繫結屬性的指示，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d48fa-280">For instructions on specifying binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d48fa-281">使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="d48fa-281">When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d48fa-282">請參閱</span><span class="sxs-lookup"><span data-stu-id="d48fa-282">See Also</span></span>  
[<span data-ttu-id="d48fa-283">Oracle 資料庫配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="d48fa-283">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[<span data-ttu-id="d48fa-284">疑難排解安裝問題的 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="d48fa-284">Troubleshoot installation issues with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)