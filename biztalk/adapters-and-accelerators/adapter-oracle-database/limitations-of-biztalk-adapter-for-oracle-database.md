---
title: BizTalk Adapter for Oracle 資料庫的限制 |Microsoft Docs
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
ms.openlocfilehash: 8138449cf3af067c9a76848f203c7e1809f6adbc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986607"
---
# <a name="limitations-of-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="71ebb-102">BizTalk Adapter for Oracle 資料庫的限制</span><span class="sxs-lookup"><span data-stu-id="71ebb-102">Limitations of BizTalk Adapter for Oracle Database</span></span>
## <a name="general"></a><span data-ttu-id="71ebb-103">一般</span><span class="sxs-lookup"><span data-stu-id="71ebb-103">General</span></span>  
 <span data-ttu-id="71ebb-104">下列已知限制[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="71ebb-104">The following are known limitations for the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span></span>  
  
- <span data-ttu-id="71ebb-105">限制某些例外狀況，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]相容於舊版的配接器。</span><span class="sxs-lookup"><span data-stu-id="71ebb-105">Barring some exceptions, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is compatible with the previous release of the adapters.</span></span> <span data-ttu-id="71ebb-106">自上次發行後發生的變更清單，請參閱 < [BizTalk Adapter for Oracle 資料庫中的重要功能](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="71ebb-106">For a list of changes that has happened since the last release, see [Key Features in BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md).</span></span>  
  
- <span data-ttu-id="71ebb-107">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援的 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="71ebb-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support XML Types.</span></span>  
  
- <span data-ttu-id="71ebb-108">SQLEXECUTE 作業不會傳回值的 OUT 或 IN 出程序、 函式，或封裝的參數。</span><span class="sxs-lookup"><span data-stu-id="71ebb-108">The SQLEXECUTE operation does not return values for OUT or IN OUT parameters to procedures, functions, or packages.</span></span> <span data-ttu-id="71ebb-109">基於這個理由，您必須叫用程序、 函數和封裝所使用的專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。</span><span class="sxs-lookup"><span data-stu-id="71ebb-109">For this reason, you must invoke procedures, functions, and packages by using the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.</span></span>  
  
- <span data-ttu-id="71ebb-110">從 使用 proxy 進行程式設計，Oracle 資料庫擷取資料時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會還原序列化 XML 訊息，其超過 65536 的節點。</span><span class="sxs-lookup"><span data-stu-id="71ebb-110">When retrieving data from the Oracle database using proxy programming, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not deserialize XML messages that have more than 65536 nodes.</span></span> <span data-ttu-id="71ebb-111">請確定回應訊息含有節點小於或等於為 65536。</span><span class="sxs-lookup"><span data-stu-id="71ebb-111">Make sure the response message has nodes less than or equal to 65536.</span></span> <span data-ttu-id="71ebb-112">您可以修改您的應用程式的 app.config 檔，以解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="71ebb-112">You can work around this limitation by modifying the app.config file for your application.</span></span> <span data-ttu-id="71ebb-113">如需相關指示，請參閱 <<c0> [ 疑難排解操作問題的 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="71ebb-113">For instructions, see [Troubleshoot operational issues with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md).</span></span>  
  
- <span data-ttu-id="71ebb-114">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會採用輸入字串，並建構然後配接器所執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="71ebb-114">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] takes input strings and constructs SQL commands that are then executed by the adapter.</span></span> <span data-ttu-id="71ebb-115">不過，輸入的字串可能包含其他的 SQL 命令，也會執行，而且可能會中斷作業合約。</span><span class="sxs-lookup"><span data-stu-id="71ebb-115">However, the input string might contain other SQL commands that also get executed and might break the operation contract.</span></span>  
  
   <span data-ttu-id="71ebb-116">假設其中配接器會提供預存程序輸入的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="71ebb-116">Consider a scenario where the adapter provides an input REF CURSOR to a stored procedure.</span></span> <span data-ttu-id="71ebb-117">在這類案例中，配接器用戶端必須提供的命令，在執行時，取得 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="71ebb-117">In such a scenario, the adapter client must provide a command that, when executed, obtains the REF CURSOR.</span></span> <span data-ttu-id="71ebb-118">配接器接著會傳遞 REF 資料指標預存程序。</span><span class="sxs-lookup"><span data-stu-id="71ebb-118">The adapter then passes on the REF CURSOR to the stored procedure.</span></span> <span data-ttu-id="71ebb-119">不過，如果取得 REF CURSOR 的命令會執行一些額外的修改資料庫，執行預存程序的作業合約會中斷。</span><span class="sxs-lookup"><span data-stu-id="71ebb-119">However, if the command for obtaining the REF CURSOR performs some additional modifications to the database, the operation contract for executing the stored procedure is broken.</span></span>  
  
- <span data-ttu-id="71ebb-120">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援巢狀只有最多兩個層級的 UDT。</span><span class="sxs-lookup"><span data-stu-id="71ebb-120">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports UDT nesting only up to two levels.</span></span>  
  
- <span data-ttu-id="71ebb-121">使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果您的認證，在 WCF 自訂傳送連接埠不正確，不會處理要求訊息。</span><span class="sxs-lookup"><span data-stu-id="71ebb-121">When using the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], if the credentials on the WCF-custom send port are incorrect, the request messages are not processed.</span></span> <span data-ttu-id="71ebb-122">指定正確的認證之後，將訊息傳送至 Oracle 資料庫，並在收到回應。</span><span class="sxs-lookup"><span data-stu-id="71ebb-122">After you specify the correct credentials, the message is sent to the Oracle database and a response is received.</span></span> <span data-ttu-id="71ebb-123">不過，回應訊息不適用於輸出連接埠。</span><span class="sxs-lookup"><span data-stu-id="71ebb-123">However, the response message is not available to the out port.</span></span> <span data-ttu-id="71ebb-124">在此情況下，您可能需要重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="71ebb-124">In such scenarios, you may need to restart the host instance.</span></span>  
  
- <span data-ttu-id="71ebb-125">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援複雜類型 （例如記錄類型、 資料表類型、 UDT 和 VARRAY） 內的 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="71ebb-125">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support the BFILE data type inside complex types (such as RECORD type, TABLE type, UDT, and VARRAY).</span></span>  
  
- <span data-ttu-id="71ebb-126">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。</span><span class="sxs-lookup"><span data-stu-id="71ebb-126">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support User-Defined Types (UDTs) that have circular references.</span></span>  
  
- <span data-ttu-id="71ebb-127">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行不支援包含的欄位的記錄類型的記錄類型的 PL/SQL 資料表。</span><span class="sxs-lookup"><span data-stu-id="71ebb-127">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support records that contain fields of type PL/SQL tables of RECORD type.</span></span>  
  
- <span data-ttu-id="71ebb-128">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。</span><span class="sxs-lookup"><span data-stu-id="71ebb-128">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not enable clients to set the value of the first element in a VARRAY to NULL.</span></span>  
  
- <span data-ttu-id="71ebb-129">PL/SQL 資料表，除了[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援封裝內定義的 Udt。</span><span class="sxs-lookup"><span data-stu-id="71ebb-129">Except for PL/SQL tables, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that are defined inside a package.</span></span>  
  
## <a name="limitations-due-to-odpnet"></a><span data-ttu-id="71ebb-130">由於 ODP.NET 的限制</span><span class="sxs-lookup"><span data-stu-id="71ebb-130">Limitations due to ODP.NET</span></span>  
 <span data-ttu-id="71ebb-131">下列已知限制[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]由於 ODP.NET 的限制：</span><span class="sxs-lookup"><span data-stu-id="71ebb-131">The following are known limitations for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] due to the limitation of ODP.NET:</span></span>  
  
- <span data-ttu-id="71ebb-132">採用十進位值的 Oracle 資料類型，ODP.NET 不會擲回例外狀況如果輸入的值包含字母字元。</span><span class="sxs-lookup"><span data-stu-id="71ebb-132">For Oracle data types that take decimal values, ODP.NET does not throw an exception if the input value contains alphabetic characters.</span></span> <span data-ttu-id="71ebb-133">因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 來與 Oracle 資料庫時，配接器也不會擲回例外狀況時傳遞字母字元。</span><span class="sxs-lookup"><span data-stu-id="71ebb-133">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses ODP.NET to interface with the Oracle database, the adapter too does not throw an exception when passing alphabetic characters.</span></span> <span data-ttu-id="71ebb-134">例如：</span><span class="sxs-lookup"><span data-stu-id="71ebb-134">For example:</span></span>  
  
  -   <span data-ttu-id="71ebb-135">將插入作業的值"54r 」 傳遞不會擲回例外狀況;而被插入值"54"。</span><span class="sxs-lookup"><span data-stu-id="71ebb-135">Passing a value “54r” for an insert operation does not throw an exception; the value “54” is inserted instead.</span></span>  
  
  -   <span data-ttu-id="71ebb-136">傳遞的值"r54 」 插入作業不會擲回例外狀況;而被插入值"0"。</span><span class="sxs-lookup"><span data-stu-id="71ebb-136">Passing a value “r54” for an insert operation does not throw an exception; the value “0” is inserted instead.</span></span>  
  
- <span data-ttu-id="71ebb-137">由於 ODP.NET 的限制，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援使用多載使用強型別和弱型別 REF CURSOR 的程序。</span><span class="sxs-lookup"><span data-stu-id="71ebb-137">Because of an ODP.NET limitation, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support the use of overloaded procedures using strongly-typed and weakly-typed REF CURSORS.</span></span> <span data-ttu-id="71ebb-138">就內部而言，配接器會將這兩個強型別和弱型別 REF 資料指標視為只是 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="71ebb-138">Internally, the adapter treats both the strongly-typed and weakly-typed REF CURSORS as just REF CURSORS.</span></span>  
  
- <span data-ttu-id="71ebb-139">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援未編製索引為數值欄位的 PL/SQL 資料表。</span><span class="sxs-lookup"><span data-stu-id="71ebb-139">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support PL/SQL tables that are not indexed by a numeric field.</span></span>  
  
- <span data-ttu-id="71ebb-140">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援不包含任何元素的關聯陣列。</span><span class="sxs-lookup"><span data-stu-id="71ebb-140">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support associative arrays that do not contain any element.</span></span>  
  
- <span data-ttu-id="71ebb-141">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含當地時間區域屬性 (TimeStampLTZ) 的時間戳記資料類型的 Udt。</span><span class="sxs-lookup"><span data-stu-id="71ebb-141">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain the TimeStamp data type with local time zone attributes (TimeStampLTZ).</span></span>  
  
- <span data-ttu-id="71ebb-142">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含 Udt"。"</span><span class="sxs-lookup"><span data-stu-id="71ebb-142">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain a “.”</span></span> <span data-ttu-id="71ebb-143">（句號） 在其名稱中。</span><span class="sxs-lookup"><span data-stu-id="71ebb-143">(period) in their names.</span></span>  
  
- <span data-ttu-id="71ebb-144">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含 BLOB、 CLOB、 和 NCLOB 資料類型為在 OUT 參數的 Udt。</span><span class="sxs-lookup"><span data-stu-id="71ebb-144">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain BLOB, CLOB, and NCLOB data types as an IN OUT parameter.</span></span>  
  
- <span data-ttu-id="71ebb-145">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Nepodporuje Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。</span><span class="sxs-lookup"><span data-stu-id="71ebb-145">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support Varray of Varray of the following simple types: BFILE, IntervalDS, IntervalYM, TimeStampLTZ, and TimeStampTZ.</span></span>  
  
- <span data-ttu-id="71ebb-146">由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的任何記錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="71ebb-146">Due to the limitation of associative arrays, PL/SQL tables or PL/SQL tables of records that contain any of the following data types are not supported in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span></span>  
  
  -   <span data-ttu-id="71ebb-147">BFILE</span><span class="sxs-lookup"><span data-stu-id="71ebb-147">BFILE</span></span>  
  
  -   <span data-ttu-id="71ebb-148">BLOB</span><span class="sxs-lookup"><span data-stu-id="71ebb-148">BLOB</span></span>  
  
  -   <span data-ttu-id="71ebb-149">CLOB</span><span class="sxs-lookup"><span data-stu-id="71ebb-149">CLOB</span></span>  
  
  -   <span data-ttu-id="71ebb-150">IntervalDS</span><span class="sxs-lookup"><span data-stu-id="71ebb-150">IntervalDS</span></span>  
  
  -   <span data-ttu-id="71ebb-151">IntervalYM</span><span class="sxs-lookup"><span data-stu-id="71ebb-151">IntervalYM</span></span>  
  
  -   <span data-ttu-id="71ebb-152">長整數</span><span class="sxs-lookup"><span data-stu-id="71ebb-152">Long</span></span>  
  
  -   <span data-ttu-id="71ebb-153">NCLOB</span><span class="sxs-lookup"><span data-stu-id="71ebb-153">NCLOB</span></span>  
  
  -   <span data-ttu-id="71ebb-154">RowID</span><span class="sxs-lookup"><span data-stu-id="71ebb-154">RowID</span></span>  
  
  -   <span data-ttu-id="71ebb-155">TimeStamp</span><span class="sxs-lookup"><span data-stu-id="71ebb-155">TimeStamp</span></span>  
  
  -   <span data-ttu-id="71ebb-156">TimeStampLTZ</span><span class="sxs-lookup"><span data-stu-id="71ebb-156">TimeStampLTZ</span></span>  
  
  -   <span data-ttu-id="71ebb-157">TimeStampTZ</span><span class="sxs-lookup"><span data-stu-id="71ebb-157">TimeStampTZ</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ebb-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71ebb-158">See Also</span></span>  
 [<span data-ttu-id="71ebb-159">了解 BizTalk Adapter for Oracle Database</span><span class="sxs-lookup"><span data-stu-id="71ebb-159">Understand the BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)