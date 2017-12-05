---
title: "在 BizTalk SQL 配接器疑難排解操作問題 |Microsoft 文件"
description: "常見問題和解決方法，SQL 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c75f85f4-cd03-4c6a-aac9-a6d02d3c3449
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b6850a1b8c3b0cb5d1356078fce8dc8f50c6963
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshoot-operational-issues-with-the-sql-adapter"></a><span data-ttu-id="abadf-103">SQL 配接器疑難排解操作問題</span><span class="sxs-lookup"><span data-stu-id="abadf-103">Troubleshoot Operational Issues with the SQL adapter</span></span>
<span data-ttu-id="abadf-104">本章節將討論使用來解析作業使用時可能遭遇的錯誤的疑難排解技術[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-104">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="abadf-105">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="abadf-105">Enabling Tracing</span></span>  
 <span data-ttu-id="abadf-106">您必須啟用配接器之間的追蹤[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，並使用時所遇到的 SQL Server 來收集更多資訊的相關問題[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-106">You must enable tracing between the adapter, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and SQL Server to gather more information about any issues you encounter while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="abadf-107">如需有關追蹤中的支援[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[診斷追蹤和訊息記錄在 SQL 配接器](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="abadf-107">For more information about tracing support in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Diagnostic Tracing and Message Logging in the SQL adapter](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="abadf-108">已知問題</span><span class="sxs-lookup"><span data-stu-id="abadf-108">Known Issues</span></span>  
 <span data-ttu-id="abadf-109">以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]、 以及它們的可能原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="abadf-109">The following are the most common errors you might encounter when using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], along with their probable cause and resolution.</span></span>  
  
  
  
###  <a name="BKMK_SQLLoadBinding"></a><span data-ttu-id="abadf-110">載入配接器繫結時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="abadf-110">Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="abadf-111">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-111">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-112">當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="abadf-112">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="abadf-113">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-113">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-114">當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="abadf-114">When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="abadf-115">接著，配接器繫結會相依於企業應用程式的特定用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="abadf-115">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="abadf-116">如果您未安裝中所包含的所有配接器的配接器的一般或完整安裝，您可能會面臨這個問題[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-116">You might face this issue if you did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="abadf-117">不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="abadf-117">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="abadf-118">如此一來，GUI 無法載入其他配接器的繫結。</span><span class="sxs-lookup"><span data-stu-id="abadf-118">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="abadf-119">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-119">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-120">請確定您執行自訂安裝的配接器安裝您所需要的介面卡。</span><span class="sxs-lookup"><span data-stu-id="abadf-120">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
###  <a name="BKMK_SQLDisplay"></a><span data-ttu-id="abadf-121">SQL 配接器不會顯示在 BizTalk Server 管理主控台中的配接器清單</span><span class="sxs-lookup"><span data-stu-id="abadf-121">The SQL adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="abadf-122">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-122">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-123">與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在清單中的配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="abadf-123">Unlike the earlier version of the adapters shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="abadf-124">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-124">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-125">最新[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="abadf-125">The latest [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="abadf-126">因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-126">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="abadf-127">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-127">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-128">您可以明確加入[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="abadf-128">You can explicitly add the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <a name="BKMK_MissingAction"></a><span data-ttu-id="abadf-129">執行 SQL Server 資料庫上的作業時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="abadf-129">Error while performing operations on a SQL Server database</span></span>  
 <span data-ttu-id="abadf-130">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-130">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-131">執行 SQL Server 資料庫使用中的任何作業時，配接器會提供下列的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-131">The adapter gives the following error when performing any operation on a SQL Server database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="abadf-132">**BizTalk server**</span><span class="sxs-lookup"><span data-stu-id="abadf-132">**For BizTalk Server**</span></span>  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 <span data-ttu-id="abadf-133">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-133">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-134">未指定訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="abadf-134">The WCF action for the message is not specified.</span></span> <span data-ttu-id="abadf-135">WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="abadf-135">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="abadf-136">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-136">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-137">指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="abadf-137">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="abadf-138">如需指示，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="abadf-138">For instructions, see [Configure the SOAP action for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).</span></span> <span data-ttu-id="abadf-139">請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)若要查看每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="abadf-139">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) to see a list of actions for each operation.</span></span>  
  
###  <a name="BKMK_SQLInvalidOp"></a><span data-ttu-id="abadf-140">InvalidOperationException ErrorCode 與執行 FILESTREAM 操作時 = 5</span><span class="sxs-lookup"><span data-stu-id="abadf-140">InvalidOperationException with ErrorCode=5 while performing FILESTREAM operations</span></span>  
 <span data-ttu-id="abadf-141">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-141">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-142">使用時收到下列錯誤[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用於執行 FILESTREAM 操作。</span><span class="sxs-lookup"><span data-stu-id="abadf-142">You get the following error while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform FILESTREAM operations.</span></span>  
  
```  
System.InvalidOperationException: OpenSqlFileStream returned error.  
ErrorCode:5  
  
```  
  
 <span data-ttu-id="abadf-143">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-143">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-144">您可能會指定要連接到 SQL Server 資料庫的資料庫認證。</span><span class="sxs-lookup"><span data-stu-id="abadf-144">You might have specified database credentials to connect to the SQL Server database.</span></span> <span data-ttu-id="abadf-145">若要用於執行 FILESTREAM 操作，您必須一律使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="abadf-145">To perform FILESTREAM operations, you must always use Windows Authentication.</span></span> <span data-ttu-id="abadf-146">錯誤碼"5"代表拒絕存取時，是因為不正確的認證。</span><span class="sxs-lookup"><span data-stu-id="abadf-146">The error code “5” denotes that access is denied because of incorrect credentials.</span></span> <span data-ttu-id="abadf-147">如需不同錯誤碼的詳細資訊，請參閱[系統錯誤碼 (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="abadf-147">For more information about the different error codes, see [System Error Codes (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx).</span></span>
  
 <span data-ttu-id="abadf-148">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-148">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-149">您可以使用 Windows 驗證來連接到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="abadf-149">Use Windows Authentication to connect to the SQL Server database.</span></span> <span data-ttu-id="abadf-150">在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以透過將使用者名稱和密碼欄位保留空白 Wcf-custom 或 WCF SQL 連接埠組態 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="abadf-150">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can do so by leaving the user name and password fields blank in the WCF-Custom or WCF-SQL port configuration dialog box.</span></span>  
  
###  <a name="BKMK_SQLPolling"></a><span data-ttu-id="abadf-151">輪詢作業不會傳回任何訊息即使 PollingStatement 和 PolledDataAvailableStatement 指定了有效的陳述式</span><span class="sxs-lookup"><span data-stu-id="abadf-151">Polling operation does not return any messages even if valid statements are specified for PollingStatement and PolledDataAvailableStatement</span></span>  
 <span data-ttu-id="abadf-152">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-152">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-153">即使 PollingStatement 和 PolledDataAvailableStatement 繫結屬性指定有效值，則配接器沒有從 SQL Server 收到輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="abadf-153">Even if valid values are specified for the PollingStatement and PolledDataAvailableStatement binding properties, the adapter does not receive a polling message from SQL Server.</span></span>  
  
 <span data-ttu-id="abadf-154">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-154">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-155">請確認其他交易是否已正在輪詢配接器在資料表上取得鎖定。</span><span class="sxs-lookup"><span data-stu-id="abadf-155">Verify whether any other transaction has taken a lock on the table that the adapter is polling.</span></span>  
  
 <span data-ttu-id="abadf-156">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-156">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-157">如果您想要輪詢的資料表，正在更新做為另一個交易的一部分，您可以考慮 PolledDataAvailableStatement 繫結屬性中指定的查詢的一部分使用"with (nolock) 」 參數，以確保即使鎖定會加諸，就會傳回資料另一個交易。</span><span class="sxs-lookup"><span data-stu-id="abadf-157">If you want to poll a table that is being updated as part of another transaction, you can consider using “with (nolock)” parameter as part of the query specified for PolledDataAvailableStatement binding property to ensure that data is returned even if a lock is imposed by the other transaction.</span></span> <span data-ttu-id="abadf-158">如需詳細資訊，請參閱[Database Engine 中鎖定 SQL](https://msdn.microsoft.com/library/ms190615.aspx)。</span><span class="sxs-lookup"><span data-stu-id="abadf-158">For more information, see [SQL Locking in the Database Engine](https://msdn.microsoft.com/library/ms190615.aspx).</span></span>
  
###  <a name="BKMK_SQLSingleOp"></a><span data-ttu-id="abadf-159">配接器無法插入、 更新或刪除大量使用 BizTalk Server 在單一作業中的資料</span><span class="sxs-lookup"><span data-stu-id="abadf-159">The adapter fails to insert, update, or delete large volumes of data in a single operation using BizTalk Server</span></span>  
 <span data-ttu-id="abadf-160">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-160">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-161">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]無法插入、 更新或刪除大量資料，在單一作業中使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-161">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fails to insert, update, or delete large volumes of data in a single operation using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="abadf-162">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-162">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-163">插入、 更新或刪除大量資料可能會花時間和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]或的交易中正在執行的作業，可能會逾時。</span><span class="sxs-lookup"><span data-stu-id="abadf-163">Inserting, updating, or deleting large volumes of data may take time and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] or the transaction in which the operation is being performed, may time out.</span></span>  
  
 <span data-ttu-id="abadf-164">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-164">**Resolution**</span></span>  
  
-   <span data-ttu-id="abadf-165">**BizTalk server**</span><span class="sxs-lookup"><span data-stu-id="abadf-165">**For BizTalk Server**</span></span>  
  
    1.  <span data-ttu-id="abadf-166">在 machine.config 中指定的 WCF 配接器的逾時。瀏覽至 machine.config 檔名\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG 並加入類似如下所示的摘要。</span><span class="sxs-lookup"><span data-stu-id="abadf-166">Specify the timeout for the WCF adapter in the machine.config. Navigate to the machine.config file under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG and add the excerpt that resembles the following.</span></span>  
  
        ```  
        <configuration>  
         <system.transactions>  
          <machineSettings maxTimeout="02:00:00" />  
         </system.transactions>  
        </configuration>  
        ```  
  
         <span data-ttu-id="abadf-167">使用此設定時，WCF 配接器逾時設為 2 小時。</span><span class="sxs-lookup"><span data-stu-id="abadf-167">With this setting, the WCF adapter timeout is set to 2 hours.</span></span>  
  
    2.  <span data-ttu-id="abadf-168">在 machine.config 中指定 MSDTC 交易的逾時的設定。瀏覽至 machine.config 檔名\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG 並加入類似如下所示的摘要。</span><span class="sxs-lookup"><span data-stu-id="abadf-168">Specify the timeout settings for MSDTC transactions in the machine.config. Navigate to the machine.config file under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG and add the excerpt that resembles the following.</span></span>  
  
        ```  
        <system.transactions>   
                <defaultSettings distributedTransactionManagerName="<computer_name>" timeout="02:00:00"/>   
            </system.transactions>  
  
        ```  
  
         <span data-ttu-id="abadf-169">使用此設定時，MSDTC 逾時設為 2 小時。</span><span class="sxs-lookup"><span data-stu-id="abadf-169">With this setting, the MSDTC timeout is set to 2 hours.</span></span> <span data-ttu-id="abadf-170">MSDTC 逾時的預設值是 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="abadf-170">The default value for MSDTC timeout is 10 minutes.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="abadf-171">您必須執行的配接器用戶端和 SQL Server 的電腦上進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="abadf-171">You must make this change on the computers running the adapter client and SQL Server.</span></span> <span data-ttu-id="abadf-172">在摘錄中，以執行配接器用戶端和 SQL Server 的電腦名稱取代 < 電腦名稱 >。</span><span class="sxs-lookup"><span data-stu-id="abadf-172">In the excerpt, replace <computer_name> with the name of computer running the adapter client and SQL Server.</span></span>  
  
    3.  <span data-ttu-id="abadf-173">設定**SendTimeout**繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]相當大的值。</span><span class="sxs-lookup"><span data-stu-id="abadf-173">Set the **SendTimeout** binding property for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to a fairly large value.</span></span> <span data-ttu-id="abadf-174">如需有關如何設定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="abadf-174">For instructions on how to set the binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
###  <a name="BKMK_SQLFullSchemaValidate"></a><span data-ttu-id="abadf-175">在 BizTalk Server 中的完整結構描述驗證失敗之回應訊息包含資料集</span><span class="sxs-lookup"><span data-stu-id="abadf-175">Full schema validation in BizTalk Server fails for response messages containing DataSet</span></span>  
 <span data-ttu-id="abadf-176">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-176">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-177">傳回回應訊息包含的資料集，例如 ExecuteReader 作業的完整結構描述驗證失敗[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-177">For operations that return a response message containing a DataSet, for example ExecuteReader, full schema validation fails in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="abadf-178">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-178">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-179">我們建議您不會包含資料集的回應訊息的完整結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="abadf-179">We recommend you to not do a full schema validation for response messages containing a dataset.</span></span> <span data-ttu-id="abadf-180">相反地，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="abadf-180">Instead, you could do the following:</span></span>  
  
1.  <span data-ttu-id="abadf-181">一旦傳回回應訊息的結構描述，請執行作業。</span><span class="sxs-lookup"><span data-stu-id="abadf-181">Execute the operation once that returns the response message with the schema.</span></span>  
  
2.  <span data-ttu-id="abadf-182">從回應訊息的結構描述複製到.xsd 檔案，並將這個檔案加入您的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="abadf-182">Copy the schema from the response message to a .xsd file and add this file to your BizTalk project.</span></span>  
  
3.  <span data-ttu-id="abadf-183">在您的協調流程會使用 xpath 查詢從回應訊息中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="abadf-183">Use an xpath query in your orchestration to extract the data from the response message.</span></span>  
  
###  <a name="BKMK_SQLRootNode"></a><span data-ttu-id="abadf-184">RootNode TypeName 在 BizTalk 專案中的錯誤</span><span class="sxs-lookup"><span data-stu-id="abadf-184">Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="abadf-185">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-185">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-186">在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:</span><span class="sxs-lookup"><span data-stu-id="abadf-186">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="abadf-187">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-187">**Resolution**</span></span>  
  
1.  <span data-ttu-id="abadf-188">以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="abadf-188">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="abadf-189">如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。</span><span class="sxs-lookup"><span data-stu-id="abadf-189">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <a name="BKMK_SQLMetadataStronglyTyped"></a><span data-ttu-id="abadf-190">配接器無法產生強型別與暫存資料表的預存程序的中繼資料</span><span class="sxs-lookup"><span data-stu-id="abadf-190">Adapter fails to generate metadata of strongly-typed stored procedure with temporary tables</span></span>  
 <span data-ttu-id="abadf-191">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-191">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-192">配接器無法產生強型別的預存程序，其定義中包含暫存資料表的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="abadf-192">The adapter fails to generate metadata for strongly-typed stored procedures that include temporary tables in their definition.</span></span> <span data-ttu-id="abadf-193">配接器會提供下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="abadf-193">The adapter gives the following exception.</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.MetadataException:  
Retrieval of Operation Metadata has failed while building WSDL at 'TypedProcedure/<schema>/<stored_procedure_name>' --->  
System.Data.SqlClient.SqlException: Invalid object name '<temp_table_name>'.  
  
```  
  
 <span data-ttu-id="abadf-194">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-194">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-195">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]強型別的預存程序包含其定義中的暫存資料表不支援產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="abadf-195">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support generating metadata for strongly-typed stored procedures that contain temporary tables in their definition.</span></span> <span data-ttu-id="abadf-196">相反地，您應該產生中繼資料相同的程序，從下**程序**時使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-196">Instead, you should generate metadata for the same procedure from under the **Procedures** node while using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
###  <a name="BKMK_SQLVS2008"></a><span data-ttu-id="abadf-197">在 Visual Studio 中使用配接器時，無效的繫結警告</span><span class="sxs-lookup"><span data-stu-id="abadf-197">Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="abadf-198">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-198">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-199">當您使用 Visual Studio 中建立的應用程式的配接器，並開啟配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：</span><span class="sxs-lookup"><span data-stu-id="abadf-199">When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'sqlBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="abadf-200">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-200">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-201">會出現這個警告，因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結， `sqlBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abadf-201">This warning appears because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding, `sqlBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="abadf-202">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-202">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-203">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="abadf-203">You can safely ignore this warning.</span></span>  
  
###  <a name="BKMK_SQLNotification"></a><span data-ttu-id="abadf-204">如果您使用一個以上的通知結構描述中相同的應用程式或跨多個相同的主機上的應用程式使用通知結構描述，BizTalk Server 擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="abadf-204">BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host</span></span>  
 <span data-ttu-id="abadf-205">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-205">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-206">XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述比對訊息類型，會擲回 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="abadf-206">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="abadf-207">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-207">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-208">這是因為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="abadf-208">This happens because of either of the following:</span></span>  
  
-   <span data-ttu-id="abadf-209">產生一個以上的通知結構描述在 BizTalk Server 專案中，部署至 BizTalk Server 應用程式，，然後執行應用程式要從 SQL Server 資料庫接收通知。</span><span class="sxs-lookup"><span data-stu-id="abadf-209">You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the SQL Server database.</span></span> <span data-ttu-id="abadf-210">因為通知結構描述是常見的就會發生衝突的 BizTalk Server 應用程式以部署的結構描述之間。</span><span class="sxs-lookup"><span data-stu-id="abadf-210">Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
-   <span data-ttu-id="abadf-211">發生多個專案，通知結構描述產生的每個 BizTalk 伺服器，每個專案加入相同主機上，個別的 BizTalk Server 應用程式部署的專案，然後執行應用程式或應用程式收到的通知SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="abadf-211">In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the SQL Server database.</span></span> <span data-ttu-id="abadf-212">因為結構描述和組件都可存取 BizTalk Server 中的應用程式，就會發生衝突之間常見的結構描述部署在不同的 BizTalk Server 應用程式和組件。</span><span class="sxs-lookup"><span data-stu-id="abadf-212">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
 <span data-ttu-id="abadf-213">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-213">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-214">BizTalk Server 應用程式使用單一的通知結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="abadf-214">Use a single Notification schema file for a BizTalk Server application.</span></span> <span data-ttu-id="abadf-215">如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一通知結構描述時，應用程式，然後再使用 BizTalk Server 中的 從所有其他應用程式的通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="abadf-215">If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.</span></span>  
  
###  <a name="BKMK_SQLRestoreConn"></a><span data-ttu-id="abadf-216">配接器用戶端擲回例外狀況在連線恢復配接器用戶端之間的 SQL Server 資料庫後執行的作業</span><span class="sxs-lookup"><span data-stu-id="abadf-216">Adapter client throws an exception on performing an operation after the connectivity is restored between the adapter client and the SQL Server database</span></span>  
 <span data-ttu-id="abadf-217">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-217">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-218">配接器用戶端擲回下列例外狀況，在執行 SQL Server 資料庫上的作業：</span><span class="sxs-lookup"><span data-stu-id="abadf-218">Adapter client throws the following exception on executing an operation on the SQL Server database:</span></span>  
  
```  
{System.Data.Common.DbException} = {"A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.)"}  
```  
  
 <span data-ttu-id="abadf-219">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-219">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-220">在執行作業時，配接器會使用連線連接到 SQL Server 資料庫，並執行作業，SQL ADO.NET 連接集區。</span><span class="sxs-lookup"><span data-stu-id="abadf-220">During the execution of an operation, the adapter uses the connection from the SQL ADO.NET connection pool to connect to the SQL Server database, and perform the operation.</span></span> <span data-ttu-id="abadf-221">如果配接器用戶端和 SQL Server 資料庫之間在短暫的網路中斷，或如果 SQL Server 資料庫已關閉的暫時，SQL ADO.NET 連接集區中的所有連線都會都變成無效。</span><span class="sxs-lookup"><span data-stu-id="abadf-221">If there is a brief network outage between the adapter client and the SQL Server database or if the SQL Server database is down temporarily, all the connections in the SQL ADO.NET connection pool become invalid.</span></span> <span data-ttu-id="abadf-222">連線已還原，而且您嘗試執行 SQL Server 資料庫上的作業之後，配接器使用相同的無效連接從 SQL ADO.NET 連接集區，因此配接器用戶端擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="abadf-222">After the connectivity is restored and you try to perform an operation on the SQL Server database, the adapter uses the same invalid connections from the SQL ADO.NET connection pool, and therefore the adapter client throws the exception.</span></span>  
  
 <span data-ttu-id="abadf-223">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-223">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-224">配接器用戶端應該實作重試邏輯，其作業執行，它們應該在此攔截例外狀況，並指定為"n + 1"的作業重試計數，其中"n"是指定 MaxConnectionPoolSize 繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="abadf-224">The adapter client should implement retry logic in their operation execution where they should catch the exception and specify the operation retry count as “n+1”, where “n” is the value specified for the MaxConnectionPoolSize binding property.</span></span> <span data-ttu-id="abadf-225">這表示，有"n"連接集區中有已呈現正確的連接數目，如果理論上配接器用戶端應該重試的最大值為"n + 1"以取得有效的連接，並因此執行作業的時間。</span><span class="sxs-lookup"><span data-stu-id="abadf-225">This implies that if there are “n” number of connections in the connection pool that have been rendered invalid, theoretically the adapter client should retry for a maximum of “n+1” times to get a valid connection, and hence perform the operation.</span></span>  
  
 <span data-ttu-id="abadf-226">例如，若要指定重試計數[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，開啟**屬性**對話方塊的 傳送埠的應用程式中，按一下 **傳輸進階選項**對話方塊中，然後在左窗格中**傳輸選項**區域中，指定的值**重試計數**清單。</span><span class="sxs-lookup"><span data-stu-id="abadf-226">For example, to specify the retry count in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], open the **Properties** dialog box of a send port in an application, click **Transport Advanced Options** in the left pane of the dialog box, and in the **Transport Options** area, specify a value in the **Retry count** list.</span></span>  
  
###  <a name="BKMK_MemUsage"></a><span data-ttu-id="abadf-227">記憶體使用量和執行緒計數則會增加交易的輸入作業中使用配接器時</span><span class="sxs-lookup"><span data-stu-id="abadf-227">Memory usage and thread count increases when using the adapter in a transacted inbound operation</span></span>  
 <span data-ttu-id="abadf-228">**問題**</span><span class="sxs-lookup"><span data-stu-id="abadf-228">**Problem**</span></span>  
  
 <span data-ttu-id="abadf-229">在交易輸入作業中，例如輪詢，**是否有可用輪詢資料表中的任何資料**和配接器會持續輪詢，經過一段時間，您遇到的增加記憶體使用量和執行緒計數。</span><span class="sxs-lookup"><span data-stu-id="abadf-229">In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.</span></span>  
  
 <span data-ttu-id="abadf-230">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="abadf-230">**Cause**</span></span>  
  
 <span data-ttu-id="abadf-231">**如果沒有資料輪詢的資料表中可用**，之後每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]需要產生新的執行緒，以繼續輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="abadf-231">**If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation.</span></span> <span data-ttu-id="abadf-232">因此，執行緒計數和記憶體使用量會增加經過一段時間。</span><span class="sxs-lookup"><span data-stu-id="abadf-232">Hence, the thread count and memory usage increases over a period of time.</span></span> <span data-ttu-id="abadf-233">不過，如果資料表輪詢有一些資料，在相同的執行緒會繼續執行所有後續輪詢。</span><span class="sxs-lookup"><span data-stu-id="abadf-233">However, if the table being polled has some data, the same thread continues to perform all subsequent polls.</span></span>  
  
 <span data-ttu-id="abadf-234">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="abadf-234">**Resolution**</span></span>  
  
 <span data-ttu-id="abadf-235">我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （24 天），讓新的執行緒未繁衍只能每隔 24 天。</span><span class="sxs-lookup"><span data-stu-id="abadf-235">We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days.</span></span> <span data-ttu-id="abadf-236">這可確保，記憶體使用量和執行緒計數不會成長得太多太快。</span><span class="sxs-lookup"><span data-stu-id="abadf-236">This will ensure that the memory usage and thread count does not grow too much too soon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abadf-237">如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 同時設定為最大可能的值，這是 24.20:31:23.6470000 （24 天）。</span><span class="sxs-lookup"><span data-stu-id="abadf-237">If SqlAdapterInboundTransactionBehavior has been set, make sure the TransactionTimeout is also configured to maximum possible value, which is 24.20:31:23.6470000 (24 days).</span></span> <span data-ttu-id="abadf-238">當使用這個因應措施，我們可以加入 SqlAdapterInboundTransactionBehavior 才必須設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="abadf-238">When using this workaround, we can add the SqlAdapterInboundTransactionBehavior only if the transaction isolation level has to be configured.</span></span> <span data-ttu-id="abadf-239">否則，就移除該行為的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="abadf-239">Else, it is a best practice to remove that behavior.</span></span>  
  
 <span data-ttu-id="abadf-240">如需有關**ReceiveTimeout**繫結屬性，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="abadf-240">For more information about the **ReceiveTimeout** binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="abadf-241">如需指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="abadf-241">For instructions on specifying binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abadf-242">使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="abadf-242">When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abadf-243">請參閱</span><span class="sxs-lookup"><span data-stu-id="abadf-243">See Also</span></span>  
[<span data-ttu-id="abadf-244">SQL 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="abadf-244">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)