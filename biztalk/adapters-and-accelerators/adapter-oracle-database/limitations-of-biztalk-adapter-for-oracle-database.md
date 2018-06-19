---
title: Oracle Database 的 BizTalk 配接器的限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, limitations of
ms.assetid: eab4ddea-f986-43c2-82bb-b9fe37961a5b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd6cfea523333752c0ee18fefbc6a1848057fe36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214398"
---
# <a name="limitations-of-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="6509e-102">Oracle Database 的 BizTalk 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="6509e-102">Limitations of BizTalk Adapter for Oracle Database</span></span>
## <a name="general"></a><span data-ttu-id="6509e-103">一般</span><span class="sxs-lookup"><span data-stu-id="6509e-103">General</span></span>  
 <span data-ttu-id="6509e-104">下列已知限制[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="6509e-104">The following are known limitations for the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span></span>  
  
-   <span data-ttu-id="6509e-105">限制某些例外狀況，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與配接器之前的版本相容。</span><span class="sxs-lookup"><span data-stu-id="6509e-105">Barring some exceptions, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is compatible with the previous release of the adapters.</span></span> <span data-ttu-id="6509e-106">上次發行以來發生的變更清單，請參閱[BizTalk Adapter for Oracle 資料庫中的金鑰功能](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="6509e-106">For a list of changes that has happened since the last release, see [Key Features in BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md).</span></span>  
  
-   <span data-ttu-id="6509e-107">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="6509e-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support XML Types.</span></span>  
  
-   <span data-ttu-id="6509e-108">SQLEXECUTE 作業不會傳回值，代表 OUT 或 IN OUT 參數的程序、 函數或封裝。</span><span class="sxs-lookup"><span data-stu-id="6509e-108">The SQLEXECUTE operation does not return values for OUT or IN OUT parameters to procedures, functions, or packages.</span></span> <span data-ttu-id="6509e-109">基於這個理由，您必須叫用程序、 函數以及封裝使用專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。</span><span class="sxs-lookup"><span data-stu-id="6509e-109">For this reason, you must invoke procedures, functions, and packages by using the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.</span></span>  
  
-   <span data-ttu-id="6509e-110">從使用 proxy 的程式設計、 Oracle 資料庫擷取資料時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]無法還原序列化 XML 訊息有多個 65536 的節點。</span><span class="sxs-lookup"><span data-stu-id="6509e-110">When retrieving data from the Oracle database using proxy programming, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not deserialize XML messages that have more than 65536 nodes.</span></span> <span data-ttu-id="6509e-111">請確定回應訊息具有節點小於或等於為 65536。</span><span class="sxs-lookup"><span data-stu-id="6509e-111">Make sure the response message has nodes less than or equal to 65536.</span></span> <span data-ttu-id="6509e-112">您可以修改您的應用程式的 app.config 檔案，以解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="6509e-112">You can work around this limitation by modifying the app.config file for your application.</span></span> <span data-ttu-id="6509e-113">如需指示，請參閱[操作 Oracle 資料庫配接器問題的疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6509e-113">For instructions, see [Troubleshoot operational issues with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md).</span></span>  
  
-   <span data-ttu-id="6509e-114">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會採用輸入字串和建構 SQL 命令，然後執行配接器。</span><span class="sxs-lookup"><span data-stu-id="6509e-114">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] takes input strings and constructs SQL commands that are then executed by the adapter.</span></span> <span data-ttu-id="6509e-115">不過，輸入的字串可能包含其他的 SQL 命令，也會執行，而且可能會中斷作業合約。</span><span class="sxs-lookup"><span data-stu-id="6509e-115">However, the input string might contain other SQL commands that also get executed and might break the operation contract.</span></span>  
  
     <span data-ttu-id="6509e-116">假設其中配接器會提供預存程序輸入的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="6509e-116">Consider a scenario where the adapter provides an input REF CURSOR to a stored procedure.</span></span> <span data-ttu-id="6509e-117">在這種情況下，配接器用戶端必須提供的命令，在執行時，會取得 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="6509e-117">In such a scenario, the adapter client must provide a command that, when executed, obtains the REF CURSOR.</span></span> <span data-ttu-id="6509e-118">配接器接著會傳遞 REF 資料指標預存程序。</span><span class="sxs-lookup"><span data-stu-id="6509e-118">The adapter then passes on the REF CURSOR to the stored procedure.</span></span> <span data-ttu-id="6509e-119">不過，如果取得 REF CURSOR 的命令會執行一些額外的修改資料庫，執行預存程序的作業合約會中斷。</span><span class="sxs-lookup"><span data-stu-id="6509e-119">However, if the command for obtaining the REF CURSOR performs some additional modifications to the database, the operation contract for executing the stored procedure is broken.</span></span>  
  
-   <span data-ttu-id="6509e-120">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援巢狀只有最多兩個層級的 UDT。</span><span class="sxs-lookup"><span data-stu-id="6509e-120">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports UDT nesting only up to two levels.</span></span>  
  
-   <span data-ttu-id="6509e-121">使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果的認證在 WCF 自訂傳送連接埠不正確，無法處理要求訊息。</span><span class="sxs-lookup"><span data-stu-id="6509e-121">When using the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], if the credentials on the WCF-custom send port are incorrect, the request messages are not processed.</span></span> <span data-ttu-id="6509e-122">指定正確的認證之後，訊息會傳送到 Oracle 資料庫，並收到回應。</span><span class="sxs-lookup"><span data-stu-id="6509e-122">After you specify the correct credentials, the message is sent to the Oracle database and a response is received.</span></span> <span data-ttu-id="6509e-123">不過，回應訊息不適用於輸出通訊埠。</span><span class="sxs-lookup"><span data-stu-id="6509e-123">However, the response message is not available to the out port.</span></span> <span data-ttu-id="6509e-124">在這種情況下，您可能需要重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="6509e-124">In such scenarios, you may need to restart the host instance.</span></span>  
  
-   <span data-ttu-id="6509e-125">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援複雜型別 （例如記錄類型，資料表類型、 UDT，以及 VARRAY） 內 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="6509e-125">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support the BFILE data type inside complex types (such as RECORD type, TABLE type, UDT, and VARRAY).</span></span>  
  
-   <span data-ttu-id="6509e-126">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。</span><span class="sxs-lookup"><span data-stu-id="6509e-126">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support User-Defined Types (UDTs) that have circular references.</span></span>  
  
-   <span data-ttu-id="6509e-127">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含的欄位的記錄是否輸入 PL/SQL 資料表的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="6509e-127">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support records that contain fields of type PL/SQL tables of RECORD type.</span></span>  
  
-   <span data-ttu-id="6509e-128">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。</span><span class="sxs-lookup"><span data-stu-id="6509e-128">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not enable clients to set the value of the first element in a VARRAY to NULL.</span></span>  
  
-   <span data-ttu-id="6509e-129">除了 PL/SQL 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援封裝內定義的 Udt。</span><span class="sxs-lookup"><span data-stu-id="6509e-129">Except for PL/SQL tables, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that are defined inside a package.</span></span>  
  
## <a name="limitations-due-to-odpnet"></a><span data-ttu-id="6509e-130">由於 ODP.NET 限制</span><span class="sxs-lookup"><span data-stu-id="6509e-130">Limitations due to ODP.NET</span></span>  
 <span data-ttu-id="6509e-131">下列已知限制[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]基於 ODP.NET 限制：</span><span class="sxs-lookup"><span data-stu-id="6509e-131">The following are known limitations for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] due to the limitation of ODP.NET:</span></span>  
  
-   <span data-ttu-id="6509e-132">接受十進位值的 Oracle 資料類型，ODP.NET 不會擲回例外狀況如果輸入的值包含字母字元。</span><span class="sxs-lookup"><span data-stu-id="6509e-132">For Oracle data types that take decimal values, ODP.NET does not throw an exception if the input value contains alphabetic characters.</span></span> <span data-ttu-id="6509e-133">因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 Oracle 資料庫時，配接器介面 ODP.NET 太不會擲回例外狀況時傳遞字母字元。</span><span class="sxs-lookup"><span data-stu-id="6509e-133">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses ODP.NET to interface with the Oracle database, the adapter too does not throw an exception when passing alphabetic characters.</span></span> <span data-ttu-id="6509e-134">例如：</span><span class="sxs-lookup"><span data-stu-id="6509e-134">For example:</span></span>  
  
    -   <span data-ttu-id="6509e-135">傳遞的值"54r 」 插入作業不會擲回例外狀況。而被插入值"54"。</span><span class="sxs-lookup"><span data-stu-id="6509e-135">Passing a value “54r” for an insert operation does not throw an exception; the value “54” is inserted instead.</span></span>  
  
    -   <span data-ttu-id="6509e-136">傳遞的值"r54 」 插入作業不會擲回例外狀況。而被插入值"0"。</span><span class="sxs-lookup"><span data-stu-id="6509e-136">Passing a value “r54” for an insert operation does not throw an exception; the value “0” is inserted instead.</span></span>  
  
-   <span data-ttu-id="6509e-137">由於 ODP.NET 的限制，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援使用強型別和弱式類型的 REF CURSOR 的多載程序使用。</span><span class="sxs-lookup"><span data-stu-id="6509e-137">Because of an ODP.NET limitation, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support the use of overloaded procedures using strongly-typed and weakly-typed REF CURSORS.</span></span> <span data-ttu-id="6509e-138">就內部而言，配接器會將這兩個強型別和弱型別 REF 資料指標視為只 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="6509e-138">Internally, the adapter treats both the strongly-typed and weakly-typed REF CURSORS as just REF CURSORS.</span></span>  
  
-   <span data-ttu-id="6509e-139">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 PL/SQL 資料表未建立索引的數值欄位。</span><span class="sxs-lookup"><span data-stu-id="6509e-139">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support PL/SQL tables that are not indexed by a numeric field.</span></span>  
  
-   <span data-ttu-id="6509e-140">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援不包含任何元素的關聯陣列。</span><span class="sxs-lookup"><span data-stu-id="6509e-140">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support associative arrays that do not contain any element.</span></span>  
  
-   <span data-ttu-id="6509e-141">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含時間戳記資料類型，以本地時間區域屬性 (TimeStampLTZ) 的 Udt。</span><span class="sxs-lookup"><span data-stu-id="6509e-141">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain the TimeStamp data type with local time zone attributes (TimeStampLTZ).</span></span>  
  
-   <span data-ttu-id="6509e-142">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含 Udt"。"</span><span class="sxs-lookup"><span data-stu-id="6509e-142">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain a “.”</span></span> <span data-ttu-id="6509e-143">（句號） 在其名稱中。</span><span class="sxs-lookup"><span data-stu-id="6509e-143">(period) in their names.</span></span>  
  
-   <span data-ttu-id="6509e-144">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 Udt，包含 BLOB、 CLOB、 和 NCLOB 資料類型做為 IN OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="6509e-144">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain BLOB, CLOB, and NCLOB data types as an IN OUT parameter.</span></span>  
  
-   <span data-ttu-id="6509e-145">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。</span><span class="sxs-lookup"><span data-stu-id="6509e-145">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support Varray of Varray of the following simple types: BFILE, IntervalDS, IntervalYM, TimeStampLTZ, and TimeStampTZ.</span></span>  
  
-   <span data-ttu-id="6509e-146">由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的資料錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="6509e-146">Due to the limitation of associative arrays, PL/SQL tables or PL/SQL tables of records that contain any of the following data types are not supported in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span></span>  
  
    -   <span data-ttu-id="6509e-147">BFILE</span><span class="sxs-lookup"><span data-stu-id="6509e-147">BFILE</span></span>  
  
    -   <span data-ttu-id="6509e-148">BLOB</span><span class="sxs-lookup"><span data-stu-id="6509e-148">BLOB</span></span>  
  
    -   <span data-ttu-id="6509e-149">CLOB</span><span class="sxs-lookup"><span data-stu-id="6509e-149">CLOB</span></span>  
  
    -   <span data-ttu-id="6509e-150">IntervalDS</span><span class="sxs-lookup"><span data-stu-id="6509e-150">IntervalDS</span></span>  
  
    -   <span data-ttu-id="6509e-151">IntervalYM</span><span class="sxs-lookup"><span data-stu-id="6509e-151">IntervalYM</span></span>  
  
    -   <span data-ttu-id="6509e-152">長整數</span><span class="sxs-lookup"><span data-stu-id="6509e-152">Long</span></span>  
  
    -   <span data-ttu-id="6509e-153">NCLOB</span><span class="sxs-lookup"><span data-stu-id="6509e-153">NCLOB</span></span>  
  
    -   <span data-ttu-id="6509e-154">RowID</span><span class="sxs-lookup"><span data-stu-id="6509e-154">RowID</span></span>  
  
    -   <span data-ttu-id="6509e-155">TimeStamp</span><span class="sxs-lookup"><span data-stu-id="6509e-155">TimeStamp</span></span>  
  
    -   <span data-ttu-id="6509e-156">TimeStampLTZ</span><span class="sxs-lookup"><span data-stu-id="6509e-156">TimeStampLTZ</span></span>  
  
    -   <span data-ttu-id="6509e-157">TimeStampTZ</span><span class="sxs-lookup"><span data-stu-id="6509e-157">TimeStampTZ</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6509e-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6509e-158">See Also</span></span>  
 [<span data-ttu-id="6509e-159">瞭解 BizTalk Adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="6509e-159">Understand the BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)