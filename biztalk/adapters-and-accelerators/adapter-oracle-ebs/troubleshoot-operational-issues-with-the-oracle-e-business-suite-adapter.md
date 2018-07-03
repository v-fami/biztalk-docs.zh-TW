---
title: Oracle E-business Suite 配接器的疑難排解操作問題 |Microsoft Docs
description: 常見問題和解決方案的 Oracle EBS 配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 667633e0-055a-418a-ab64-d4f6e6c7a898
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d119afaea2382e1ede6c780a40bbe2bf4329860f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989984"
---
# <a name="troubleshoot-operational-issues-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="41aa7-103">Oracle E-business Suite 配接器的疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="41aa7-103">Troubleshoot Operational Issues with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="41aa7-104">本節討論如何使用以解決使用時可能遭遇的操作錯誤的疑難排解技巧[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-104">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="41aa7-105">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="41aa7-105">Enabling Tracing</span></span>  
 <span data-ttu-id="41aa7-106">如需有關追蹤中的支援[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，[診斷追蹤和訊息記錄在 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-106">For more information about tracing support in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], [Diagnostic Tracing and Message Logging in the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="41aa7-107">已知問題</span><span class="sxs-lookup"><span data-stu-id="41aa7-107">Known Issues</span></span>  
 <span data-ttu-id="41aa7-108">以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]，以及其可能的原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="41aa7-108">The following are the most common errors you might encounter when using the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.</span></span>  
  
  
  
###  <a name="BKMK_LoadBindings"></a> <span data-ttu-id="41aa7-109">載入配接器繫結時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="41aa7-109">Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="41aa7-110">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-110">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-111">當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="41aa7-111">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="41aa7-112">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-112">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-113">當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="41aa7-113">When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="41aa7-114">接著，配接器繫結均依存於企業應用程式特定的用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="41aa7-114">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="41aa7-115">您可能會面臨此問題的一個或兩個原因如下：</span><span class="sxs-lookup"><span data-stu-id="41aa7-115">You might face this issue for one or both of the following reasons:</span></span>  
  
- <span data-ttu-id="41aa7-116">在您安裝配接器的電腦上未安裝必要的 LOB 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="41aa7-116">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
- <span data-ttu-id="41aa7-117">未安裝中包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-117">You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="41aa7-118">不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="41aa7-118">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="41aa7-119">如此一來，GUI 無法載入其他配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="41aa7-119">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
  <span data-ttu-id="41aa7-120">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-120">**Resolution**</span></span>  
  
- <span data-ttu-id="41aa7-121">請確定所需的 LOB 用戶端版本已安裝在您安裝的電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-121">Make sure that the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="41aa7-122">如需支援的用戶端版本的詳細資訊，請參閱安裝指南 》，網址\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-122">For information about the supported client versions, see the installation guide available at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
- <span data-ttu-id="41aa7-123">請確定您執行自訂安裝來安裝您所需要的介面卡的介面卡。</span><span class="sxs-lookup"><span data-stu-id="41aa7-123">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
###  <a name="BKMK_Display"></a> <span data-ttu-id="41aa7-124">Oracle E-business Suite 配接器不會顯示在清單中，BizTalk Server 管理主控台中的配接器</span><span class="sxs-lookup"><span data-stu-id="41aa7-124">The Oracle E-Business Suite adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="41aa7-125">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-125">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-126">與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在清單中的配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="41aa7-126">Unlike the earlier version of the adapters shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="41aa7-127">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-127">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-128">最新[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="41aa7-128">The latest [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="41aa7-129">因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結，因此，不會顯示以 WCF 為基礎[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-129">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
 <span data-ttu-id="41aa7-130">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-130">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-131">您可以明確加入[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[新增至 BizTalk Server 管理主控台的 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-131">You can explicitly add the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the Oracle E-Business Suite adapter to BizTalk Server Administration console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <a name="BKMK_MissingAction"></a> <span data-ttu-id="41aa7-132">在 Oracle E-business Suite 上執行作業時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="41aa7-132">Error while performing operations on the Oracle E-Business Suite</span></span>  
 <span data-ttu-id="41aa7-133">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-133">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-134">執行 Oracle E-business Suite 使用的任何作業時，配接器會提供下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-134">The adapter gives the following error when performing any operation on the Oracle E-Business Suite using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
- <span data-ttu-id="41aa7-135">**BizTalk server**</span><span class="sxs-lookup"><span data-stu-id="41aa7-135">**For BizTalk Server**</span></span>  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  <span data-ttu-id="41aa7-136">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-136">**Cause**</span></span>  
  
  <span data-ttu-id="41aa7-137">未指定訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="41aa7-137">The WCF action for the message is not specified.</span></span> <span data-ttu-id="41aa7-138">WCF 會需要為每個作業，因為它會通知配接器要在 LOB 應用程式上執行的作業指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="41aa7-138">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
  <span data-ttu-id="41aa7-139">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-139">**Resolution**</span></span>  
  
  <span data-ttu-id="41aa7-140">指定的 SOAP 動作，傳送埠中或在 BizTalk 協調流程中的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="41aa7-140">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="41aa7-141">如需相關指示，請參閱 <<c0> [ 設定 Oracle E-business Suite 的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-141">For instructions, see [Configure the SOAP action for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md).</span></span> <span data-ttu-id="41aa7-142">請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)以查看每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="41aa7-142">See [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md) to see a list of actions for each operation.</span></span>  
  
###  <a name="BKMK_WrongClient"></a> <span data-ttu-id="41aa7-143">BizTalk 處理序可能會當機由於不正確的 Oracle 用戶端版本時將要求訊息放在接收位置</span><span class="sxs-lookup"><span data-stu-id="41aa7-143">BizTalk process might crash due to an incorrect Oracle client version when a request message is dropped at the receive location</span></span>  
 <span data-ttu-id="41aa7-144">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-144">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-145">在 BizTalk 協調流程中定義的接收位置卸除要求訊息之後，協調流程會取用訊息和 BizTalk 主控件 (BTSNTSvc.exe) 損毀，並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="41aa7-145">After a request message is dropped at a receive location defined in a BizTalk orchestration, the orchestration consumes the message and BizTalk host (BTSNTSvc.exe) crashes and restarts.</span></span>  
  
 <span data-ttu-id="41aa7-146">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-146">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-147">安裝 Oracle 用戶端將最新的用戶端組件參考加入 PATH 變數中。</span><span class="sxs-lookup"><span data-stu-id="41aa7-147">Installing the Oracle client adds the reference to the latest client assemblies in the PATH variable.</span></span> <span data-ttu-id="41aa7-148">此外，最新安裝的 Oracle 用戶端組件參考現有的用戶端組件參考之前。</span><span class="sxs-lookup"><span data-stu-id="41aa7-148">Also, the references to the most recent installation of the Oracle client assembly precede the reference to the existing client assemblies.</span></span> <span data-ttu-id="41aa7-149">因此，如果最新的 Oracle 用戶端安裝不是支援的用戶端版本中，BizTalk 主控件損毀，然後重新啟動。</span><span class="sxs-lookup"><span data-stu-id="41aa7-149">So, if the most recent Oracle client installation is not of a supported client version, BizTalk host crashes and then restarts.</span></span>  
  
 <span data-ttu-id="41aa7-150">例如，假設電腦上已安裝支援的 Oracle 用戶端 11.1.0.7，和 PATH 變數具有下列參考：</span><span class="sxs-lookup"><span data-stu-id="41aa7-150">For example, assume that the supported Oracle client 11.1.0.7 is already installed on the computer and the PATH variable has the following reference:</span></span>  
  
```  
C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 <span data-ttu-id="41aa7-151">如果同一部電腦上安裝不支援的 Oracle 用戶端，例如 10.2.0.3，PATH 變數將會有下列參考：</span><span class="sxs-lookup"><span data-stu-id="41aa7-151">If an unsupported Oracle client, for example 10.2.0.3, is installed on the same computer, the PATH variable will have the following reference:</span></span>  
  
```  
C:\oracle\product\10.2.0\db_2\bin;C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 <span data-ttu-id="41aa7-152">請注意，不支援的用戶端參考的版本是支援的版本之前，因此 BizTalk 主控件的當機。</span><span class="sxs-lookup"><span data-stu-id="41aa7-152">Note that the unsupported client version is referenced before the supported version and hence BizTalk host crashes.</span></span> <span data-ttu-id="41aa7-153">如果有多個執行的 BizTalk 主控件，裝載配接器發生損毀。</span><span class="sxs-lookup"><span data-stu-id="41aa7-153">If there are more than one BizTalk hosts running, then the one hosting the adapter crashes.</span></span>  
  
 <span data-ttu-id="41aa7-154">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-154">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-155">如果同一部電腦上安裝一個以上的 Oracle 用戶端，請確定 PATH 變數中的其他 Oracle 用戶端版本之前參考支援的 Oracle 用戶端版本。</span><span class="sxs-lookup"><span data-stu-id="41aa7-155">If more than one Oracle client is installed on the same computer, make sure the supported Oracle client version is referenced before the other Oracle client versions in the PATH variable.</span></span> <span data-ttu-id="41aa7-156">例如，如果 11.1.0.7 支援的 Oracle 用戶端版本，PATH 變數中的參考必須如下：</span><span class="sxs-lookup"><span data-stu-id="41aa7-156">For example, if the supported Oracle client version is 11.1.0.7, the reference in the PATH variable must look like:</span></span>  
  
```  
  
C:\oracle\product\11.1.0\client_1\bin;C:\oracle\product\10.2.0\db_2\bin;  
```  
  
###  <a name="BKMK_Overflow"></a> <span data-ttu-id="41aa7-157">配接器可能會擲回溢位例外狀況上執行作業</span><span class="sxs-lookup"><span data-stu-id="41aa7-157">Adapter might throw an overflow exception on executing an operation</span></span>  
 <span data-ttu-id="41aa7-158">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-158">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-159">如果您嘗試執行包含 Oracle 資料集或弱式型別 REF 資料指標內的數值資料類型的作業，請使用配接器，配接器可能會擲回溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41aa7-159">Using the adapter, if you try to perform an operation containing Oracle numeric data types inside DataSets or weakly-typed REF CURSORS, the adapter might throw an overflow exception.</span></span>  
  
 <span data-ttu-id="41aa7-160">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-160">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-161">會發生這種情況是如果您提供 Oracle 數值資料類型資料集或弱式型別 REF CURSOR 無法放入個別的.NET 型別內的較大的值。</span><span class="sxs-lookup"><span data-stu-id="41aa7-161">This happens if you supply a large value for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS that cannot fit into the respective .NET type.</span></span>  
  
 <span data-ttu-id="41aa7-162">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-162">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-163">如果您想要將大型值傳給資料集或弱式型別 REF 資料指標內的 Oracle 數值資料類型，您必須啟用 「 安全輸入的值設定**EnableSafeTyping**繫結屬性**true**.</span><span class="sxs-lookup"><span data-stu-id="41aa7-163">If you want to pass large values for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS, you must enable safe typing by setting the value of the **EnableSafeTyping** binding property to **true**.</span></span> <span data-ttu-id="41aa7-164">啟用 「 安全輸入公開在資料集或弱式型別 REF CURSOR 的 Oracle 數值資料型別為字串。</span><span class="sxs-lookup"><span data-stu-id="41aa7-164">Enabling safe typing exposes the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS as strings.</span></span>  
  
###  <a name="BKMK_Arithmetic"></a> <span data-ttu-id="41aa7-165">配接器可能會擲回算術溢位例外狀況執行 ExecuteScalar 作業</span><span class="sxs-lookup"><span data-stu-id="41aa7-165">Adapter might throw an arithmetic overflow exception on executing an ExecuteScalar operation</span></span>  
 <span data-ttu-id="41aa7-166">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-166">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-167">如果您嘗試執行 SELECT 陳述式中擷取大量的 ExecuteScalar 作業，請使用配接器，配接器會擲回下列例外狀況: 「 System.OverflowException： 數學運算導致溢位。 」</span><span class="sxs-lookup"><span data-stu-id="41aa7-167">Using the adapter, if you try to execute a SELECT statement in an ExecuteScalar operation that retrieves a large number, the adapter throws the following exception: “System.OverflowException: Arithmetic operation resulted in an overflow.”</span></span>  
  
 <span data-ttu-id="41aa7-168">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-168">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-169">這是因為在 ODP.NET ExecuteScalar 作業的已知限制。</span><span class="sxs-lookup"><span data-stu-id="41aa7-169">This happens due to the known limitation of ExecuteScalar operation in ODP.NET.</span></span> <span data-ttu-id="41aa7-170">ODP.NET 會盡量配合.NET 的 Decimal 資料類型，將資料中，如果結果太大而無法符合.NET 的 Decimal 型別，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41aa7-170">ODP.NET tries to fit in the data into the .NET Decimal data type, and if the result is too large to fit in the .NET Decimal type, the exception is thrown.</span></span>  
  
 <span data-ttu-id="41aa7-171">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-171">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-172">在 ExecuteScalar 作業的 SELECT 陳述式中使用 TO_CHAR() 轉換字串形式傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="41aa7-172">Use TO_CHAR() in the SELECT statement in the ExecuteScalar operation to convert the returned data as string.</span></span>  
  
###  <a name="BKMK_AppContext"></a> <span data-ttu-id="41aa7-173">配接器用戶端可能會擲回下列例外狀況上執行作業: 「 無法擷取使用者識別碼、 責任識別碼、 應用程式識別碼。檢查是否傳入正確的值。 」</span><span class="sxs-lookup"><span data-stu-id="41aa7-173">Adapter client might throw the following exception on executing an operation: “Could not retrieve user id, responsibility id, application id.  Check if correct values were passed in.”</span></span>  
 <span data-ttu-id="41aa7-174">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-174">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-175">如果您要執行 Oracle E-business Suite 成品 （介面資料表、 介面檢視、 同時執行的程式，並要求集） 上的作業，則配接器用戶端可能會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41aa7-175">The adapter clients might throw this exception if you are performing operations on Oracle E-Business Suite artifacts (interface tables, interface views, concurrent programs, and request sets).</span></span>  
  
 <span data-ttu-id="41aa7-176">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-176">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-177">會發生這種情況是如果您提供的 Oracle 使用者名稱、 密碼和責任名稱時在介面資料表、 介面檢視、 同時執行的程式，並要求集上執行作業的正確組合。</span><span class="sxs-lookup"><span data-stu-id="41aa7-177">This happens if you supply an incorrect combination of Oracle user name, password, and responsibility name while performing operations on interface tables, interface views, concurrent programs, and request sets.</span></span> <span data-ttu-id="41aa7-178">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]需要這些值來設定這些成品的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="41aa7-178">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] requires these values in order to set the application context for these artifacts.</span></span> <span data-ttu-id="41aa7-179">如需有關設定應用程式內容的詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-179">For more information about setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
 <span data-ttu-id="41aa7-180">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-180">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-181">您必須指定正確的 Oracle 使用者名稱、 密碼和必須負責適當地設定 Oracle E-business Suite 成品的應用程式內容組合。</span><span class="sxs-lookup"><span data-stu-id="41aa7-181">You must specify a correct combination of the Oracle user name, password, and responsibility to appropriately set application context for an Oracle E-Business Suite artifact.</span></span> <span data-ttu-id="41aa7-182">若要指定 Oracle 使用者名稱和密碼值，您必須使用**OracleUserName**並**OraclePassword**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="41aa7-182">To specify values for Oracle user name and password, you must use the **OracleUserName** and **OraclePassword** binding properties.</span></span> <span data-ttu-id="41aa7-183">若要指定 Oracle 責任的值，您可以使用**OracleEBSResponsibilityName**繫結屬性或訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="41aa7-183">To specify value for the Oracle responsibility, you can either use the **OracleEBSResponsibilityName** binding property or message context property.</span></span>  
  
###  <a name="BKMK_RootNode"></a> <span data-ttu-id="41aa7-184">在 BizTalk 專案中的根節點類型名稱錯誤</span><span class="sxs-lookup"><span data-stu-id="41aa7-184">Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="41aa7-185">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-185">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-186">在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:</span><span class="sxs-lookup"><span data-stu-id="41aa7-186">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="41aa7-187">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-187">**Resolution**</span></span>  
  
1.  <span data-ttu-id="41aa7-188">以滑鼠右鍵按一下參考錯誤，然後選取 rood 節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="41aa7-188">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="41aa7-189">針對**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。</span><span class="sxs-lookup"><span data-stu-id="41aa7-189">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <a name="BKMK_InvalidBinding"></a> <span data-ttu-id="41aa7-190">在 Visual Studio 中使用配接器時，會產生無效的繫結警告。</span><span class="sxs-lookup"><span data-stu-id="41aa7-190">Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="41aa7-191">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-191">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-192">當您建立應用程式中的使用配接器時[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]和開啟配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：</span><span class="sxs-lookup"><span data-stu-id="41aa7-192">When you use the adapter to create an application in [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'oracleEBSBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="41aa7-193">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-193">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-194">會出現這個警告，因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結`oracleEBSBinding`，沒有標準繫結隨附[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41aa7-194">This warning appears because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding, `oracleEBSBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="41aa7-195">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-195">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-196">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="41aa7-196">You can safely ignore this warning.</span></span>  
  
###  <a name="BKMK_Notify"></a> <span data-ttu-id="41aa7-197">如果您在相同的應用程式中使用一個以上的通知結構描述，或在相同主機上的多個應用程式之間，使用通知結構描述，BizTalk Server 擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="41aa7-197">BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host</span></span>  
 <span data-ttu-id="41aa7-198">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-198">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-199">XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述符合訊息類型，會擲回 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="41aa7-199">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="41aa7-200">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-200">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-201">這是因為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="41aa7-201">This happens because of either of the following:</span></span>  
  
- <span data-ttu-id="41aa7-202">當您產生一個以上的通知結構描述在 BizTalk Server 專案中，將它部署到 BizTalk Server 應用程式，然後執行應用程式要從 Oracle 資料庫接收通知。</span><span class="sxs-lookup"><span data-stu-id="41aa7-202">You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the Oracle database.</span></span> <span data-ttu-id="41aa7-203">因為通知結構描述是常見的就會發生衝突之間會部署在 BizTalk Server 應用程式中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="41aa7-203">Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
- <span data-ttu-id="41aa7-204">發生多個專案，方法，您可以有為每個部署的專案，每個專案加入個別的 BizTalk Server 應用程式相同的主機上的 BizTalk Server 產生通知結構描述，並接著執行應用程式或應用程式收到的通知Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="41aa7-204">In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the Oracle database.</span></span> <span data-ttu-id="41aa7-205">因為結構描述和組件都是可存取 BizTalk Server 中的應用程式，就會發生衝突之間通用的結構描述部署在各種 BizTalk Server 應用程式和組件。</span><span class="sxs-lookup"><span data-stu-id="41aa7-205">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
  <span data-ttu-id="41aa7-206">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-206">**Resolution**</span></span>  
  
  <span data-ttu-id="41aa7-207">使用 BizTalk Server 應用程式的單一通知結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="41aa7-207">Use a single Notification schema file for a BizTalk Server application.</span></span> <span data-ttu-id="41aa7-208">如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一的通知結構描述中，應用程式，然後使用 BizTalk Server 中的 從其他所有應用程式的通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="41aa7-208">If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.</span></span>  
  
###  <a name="BKMK_Timeout"></a> <span data-ttu-id="41aa7-209">在瀏覽 Visual Studio 中的 Oracle E-business Suite 成品時的逾時例外狀況</span><span class="sxs-lookup"><span data-stu-id="41aa7-209">Timeout Exception while browsing Oracle E-Business Suite Artifacts in Visual Studio</span></span>  
 <span data-ttu-id="41aa7-210">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-210">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-211">在瀏覽 Oracle E-business Suite 中的成品時[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用的專案[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]， [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]您可能會遇到逾時例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41aa7-211">While browsing Oracle E-Business Suite artifacts in a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] you might encounter a timeout exception.</span></span>  
  
 <span data-ttu-id="41aa7-212">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-212">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-213">如果裝載 Oracle E-business Suite 的伺服器變慢、 伺服器所在的遠端位置，或想要在結構描述有大量的成品，就可能發生這個情形。</span><span class="sxs-lookup"><span data-stu-id="41aa7-213">This might happen if the server hosting the Oracle E-Business Suite is slow, server is located at a remote location, or the schema you are looking under has a large number of artifacts.</span></span>  
  
 <span data-ttu-id="41aa7-214">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-214">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-215">您可以選擇的值增加**SendTimeout**繫結屬性，或提供的搜尋運算式**類別目錄中的搜尋**文字方塊中，以減少的成品，配接器擷取。</span><span class="sxs-lookup"><span data-stu-id="41aa7-215">You can either choose to increase the value of the **SendTimeout** binding property or provide a search expression in the **Search in category** text box to reduce the number of artifacts that the adapter retrieves.</span></span>  
  
 <span data-ttu-id="41aa7-216">如需指定繫結屬性的詳細資訊，請參閱[for Oracle E-business Suite 中設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-216">For more information about specifying binding properties, see [Configure the binding properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).</span></span> <span data-ttu-id="41aa7-217">如需有關搜尋 Oracle E-business Suite 中的成品的詳細資訊，請參閱[瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-217">For more information about searching artifacts in Oracle E-Business Suite, see [Browse, search, and get metadata for Oracle E-Business Suite operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).</span></span>  
  
###  <a name="BKMK_MemUsage"></a> <span data-ttu-id="41aa7-218">記憶體使用量和執行緒計數增加而增加時使用中交易的輸入作業的配接器</span><span class="sxs-lookup"><span data-stu-id="41aa7-218">Memory usage and thread count increases when using the adapter in a transacted inbound operation</span></span>  
 <span data-ttu-id="41aa7-219">**問題**</span><span class="sxs-lookup"><span data-stu-id="41aa7-219">**Problem**</span></span>  
  
 <span data-ttu-id="41aa7-220">在交易輸入作業中，輪詢，例如**是否有可用在所輪詢的資料表中的任何資料**和配接器會持續輪詢，經過一段時間中，您遇到增加的記憶體使用量和執行緒計數。</span><span class="sxs-lookup"><span data-stu-id="41aa7-220">In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.</span></span>  
  
 <span data-ttu-id="41aa7-221">**原因**</span><span class="sxs-lookup"><span data-stu-id="41aa7-221">**Cause**</span></span>  
  
 <span data-ttu-id="41aa7-222">**如果沒有資料輪詢的資料表中可用**之後，每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]會繁衍新的執行緒，以繼續輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="41aa7-222">**If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation.</span></span> <span data-ttu-id="41aa7-223">因此，執行緒計數和記憶體使用量會增加一段時間。</span><span class="sxs-lookup"><span data-stu-id="41aa7-223">Hence, the thread count and memory usage increases over a period of time.</span></span> <span data-ttu-id="41aa7-224">不過，如果輪詢的資料表會有一些資料，相同的執行緒會繼續執行所有的後續輪詢。</span><span class="sxs-lookup"><span data-stu-id="41aa7-224">However, if the table being polled has some data, the same thread continues to perform all subsequent polls.</span></span>  
  
 <span data-ttu-id="41aa7-225">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="41aa7-225">**Resolution**</span></span>  
  
 <span data-ttu-id="41aa7-226">我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （也就是 24 天），讓新的執行緒會繁衍只能每隔 24 天。</span><span class="sxs-lookup"><span data-stu-id="41aa7-226">We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days.</span></span> <span data-ttu-id="41aa7-227">這可確保，記憶體使用量和執行緒計數不會變得太多太快。</span><span class="sxs-lookup"><span data-stu-id="41aa7-227">This will ensure that the memory usage and thread count does not grow too much too soon.</span></span>  
  
 <span data-ttu-id="41aa7-228">如需詳細資訊**ReceiveTimeout**繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-228">For more information about the **ReceiveTimeout** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="41aa7-229">如需指定繫結屬性的指示，請參閱[for Oracle E-business Suite 中設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa7-229">For instructions on specifying binding properties, see [Configure the binding properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41aa7-230">使用的介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，逾時設定為較大的值不會影響配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="41aa7-230">When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41aa7-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41aa7-231">See Also</span></span>  
[<span data-ttu-id="41aa7-232">Oracle EBS 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="41aa7-232">Troubleshooting the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)