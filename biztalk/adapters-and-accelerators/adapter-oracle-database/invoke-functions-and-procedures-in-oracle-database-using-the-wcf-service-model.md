---
title: 叫用函式，並使用 WCF 服務模型的 Oracle 資料庫中的程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, invoke functions and procedures using the WCF service model
- WCF service model, invoking functions and procedures
ms.assetid: 806fc803-3640-42d6-bdf9-53b08f9c7c50
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f1423d5945fe1c82ccc64027a28efa3c1777ca5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013151"
---
# <a name="invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="82f4b-102">叫用函式，並使用 WCF 服務模型的 Oracle 資料庫中的程序</span><span class="sxs-lookup"><span data-stu-id="82f4b-102">Invoke Functions and Procedures in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="82f4b-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現程序、 函數和封裝做為作業。</span><span class="sxs-lookup"><span data-stu-id="82f4b-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces procedures, functions, and packages as operations.</span></span> <span data-ttu-id="82f4b-104">WCF 服務模型中這些作業會表示為 WCF 用戶端上的方法。</span><span class="sxs-lookup"><span data-stu-id="82f4b-104">In the WCF service model these operations are represented as methods on a WCF client.</span></span> <span data-ttu-id="82f4b-105">WCF 服務模型和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="82f4b-105">The WCF service model and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:</span></span>  
  
-   <span data-ttu-id="82f4b-106">**支援的函式**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-106">**Support functions**.</span></span> <span data-ttu-id="82f4b-107">Oracle 函式的傳回值會呈現為 WCF 用戶端方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="82f4b-107">The RETURN value of the Oracle function is surfaced as the return value of the WCF client method.</span></span> <span data-ttu-id="82f4b-108">Oracle 參數做為參數 （使用適當的方向定義下方） 呈現給 WCF 用戶端方法。</span><span class="sxs-lookup"><span data-stu-id="82f4b-108">Oracle parameters are surfaced as parameters (with the appropriate direction as defined below) to the WCF client method.</span></span>  
  
-   <span data-ttu-id="82f4b-109">**支援程序**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-109">**Support procedures**.</span></span> <span data-ttu-id="82f4b-110">OUT 參數的 Oracle 程序的第一個會呈現為 WCF 用戶端方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="82f4b-110">The first OUT parameter of the Oracle procedure is surfaced as the return value of the WCF client method.</span></span> <span data-ttu-id="82f4b-111">所有其他的 Oracle 參數做為參數 （使用適當的方向定義下方） 呈現給 WCF 用戶端方法。</span><span class="sxs-lookup"><span data-stu-id="82f4b-111">All other Oracle parameters are surfaced as parameters (with the appropriate direction as defined below) to the WCF client method.</span></span>  
  
-   <span data-ttu-id="82f4b-112">**支援 Oracle package**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-112">**Support Oracle packages**.</span></span> <span data-ttu-id="82f4b-113">作業的名稱和其參數型別命名空間會依套件名稱限定。</span><span class="sxs-lookup"><span data-stu-id="82f4b-113">The name of the operation and the namespace of its parameter types are qualified by the package name.</span></span>  
  
-   <span data-ttu-id="82f4b-114">**支援多載的函式和程序**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-114">**Support overloaded functions and procedures**.</span></span>  
  
-   <span data-ttu-id="82f4b-115">**支援 IN，OUT 和 IN，OUT 參數的程序和函式的基本 Oracle 資料型別**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-115">**Support IN, OUT and IN OUT parameters for basic Oracle data types for both procedures and functions**.</span></span> <span data-ttu-id="82f4b-116">OUT 參數當成**放大**WCF 用戶端方法的參數，並在 OUT 參數當成**ref**參數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-116">OUT parameters are surfaced as **out** parameters on the WCF client method and IN OUT parameters are surfaced as **ref** parameters.</span></span>  
  
-   <span data-ttu-id="82f4b-117">**支援 IN、 OUT，並在 OUT REF CURSOR 參數的程序和函式，以及函式傳回值**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-117">**Support IN, OUT, and IN OUT REF CURSOR parameters for procedures and functions, as well as function RETURN values**.</span></span> <span data-ttu-id="82f4b-118">如需詳細資訊，請參閱 <<c0> [ 執行作業使用 REF 資料指標在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-118">For more information, see [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="82f4b-119">**支援外，IN 出記錄型別參數的程序和函式，以及函式傳回的值**。</span><span class="sxs-lookup"><span data-stu-id="82f4b-119">**Support IN, OUT, and IN OUT RECORD type parameters for procedures and functions, as well as function RETURN values**.</span></span> <span data-ttu-id="82f4b-120">如需詳細資訊，請參閱 <<c0> [ 執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-120">For more information, see [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="82f4b-121">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="82f4b-121">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="82f4b-122">本主題使用 /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT 中的範例多載程序。</span><span class="sxs-lookup"><span data-stu-id="82f4b-122">The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT overloaded procedure.</span></span> <span data-ttu-id="82f4b-123">此程序會從帳戶識別碼或帳戶名稱為基礎的 SCOTT/帳戶資料表讀取記錄。</span><span class="sxs-lookup"><span data-stu-id="82f4b-123">This procedure reads a record from the SCOTT/ACCOUNT table based on either an account ID or an account name.</span></span> <span data-ttu-id="82f4b-124">此程序和資料表所產生的指令碼隨附於 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="82f4b-124">A script to generate this procedure and table is supplied with the SDK samples.</span></span> <span data-ttu-id="82f4b-125">如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-125">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="82f4b-126">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="82f4b-126">The WCF Client Class</span></span>  
 <span data-ttu-id="82f4b-127">下表顯示的 WCF 用戶端和程序，產生的方法名稱的函式和封裝[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面。</span><span class="sxs-lookup"><span data-stu-id="82f4b-127">The following table shows the name of the WCF client and the method generated for procedures, functions and packages that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces.</span></span> <span data-ttu-id="82f4b-128">多載函式或程序，除非單一的 WCF 用戶端用來叫用的所有結構描述中所有結構描述中的程序或所有函式的函式和封裝中的程序。</span><span class="sxs-lookup"><span data-stu-id="82f4b-128">Unless a function or procedure is overloaded, a single WCF client is used to invoke all of the functions in a schema, all of the procedures in a schema, or all of the functions and procedures in a package.</span></span>  
  
|<span data-ttu-id="82f4b-129">Oracle 成品</span><span class="sxs-lookup"><span data-stu-id="82f4b-129">Oracle Artifact</span></span>|<span data-ttu-id="82f4b-130">WCF 用戶端作業名稱</span><span class="sxs-lookup"><span data-stu-id="82f4b-130">WCF Client Operation Name</span></span>|<span data-ttu-id="82f4b-131">範例</span><span class="sxs-lookup"><span data-stu-id="82f4b-131">Example</span></span>|  
|---------------------|-------------------------------|-------------|  
|<span data-ttu-id="82f4b-132">程序</span><span class="sxs-lookup"><span data-stu-id="82f4b-132">Procedure</span></span>|<span data-ttu-id="82f4b-133">[結構描述]ProcedureClient。[PROC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-133">[SCHEMA]ProcedureClient.[PROC_NAME]</span></span>|<span data-ttu-id="82f4b-134">SCOTTProcedureClient.MYPROC</span><span class="sxs-lookup"><span data-stu-id="82f4b-134">SCOTTProcedureClient.MYPROC</span></span>|  
|<span data-ttu-id="82f4b-135">函數</span><span class="sxs-lookup"><span data-stu-id="82f4b-135">Function</span></span>|<span data-ttu-id="82f4b-136">[結構描述]FunctionClient。[FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-136">[SCHEMA]FunctionClient.[FUNC_NAME]</span></span>|<span data-ttu-id="82f4b-137">SCOTTProcedureClient.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="82f4b-137">SCOTTProcedureClient.MYFUNC</span></span>|  
|<span data-ttu-id="82f4b-138">封裝 （程序或函數）</span><span class="sxs-lookup"><span data-stu-id="82f4b-138">Package (procedure or function)</span></span>|<span data-ttu-id="82f4b-139">[結構描述]封裝 [PACKAGE_NAME] 用戶端。[PROC_NAME 或 FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-139">[SCHEMA]Package[PACKAGE_NAME]Client.[PROC_NAME or FUNC_NAME]</span></span>|<span data-ttu-id="82f4b-140">SCOTTPackageMYPACKAGEClient.MYPROC</span><span class="sxs-lookup"><span data-stu-id="82f4b-140">SCOTTPackageMYPACKAGEClient.MYPROC</span></span>|  
  
 <span data-ttu-id="82f4b-141">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="82f4b-141">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="82f4b-142">[PROC_NAME] = Oracle 程序; 的名稱比方說，MYPROC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-142">[PROC_NAME] = The name of an Oracle procedure; for example, MYPROC.</span></span>  
  
 <span data-ttu-id="82f4b-143">[FUNC_NAME] = Oracle 函式; 的名稱比方說，MYFUNC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-143">[FUNC_NAME] = The name of an Oracle function; for example, MYFUNC.</span></span>  
  
 <span data-ttu-id="82f4b-144">[PACKAGE_NAME] = Oracle 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="82f4b-144">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="82f4b-145">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示 Oracle 記錄型別參數和傳回值，以及傳回 REF CURSOR 參數為複雜的 XML 型別包含 Oracle 資料錄的資料列的資料 （或欄位） 的結果集。</span><span class="sxs-lookup"><span data-stu-id="82f4b-145">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents Oracle RECORD type parameters and return values as well as the result sets returned by REF CURSOR parameters as complex XML types that contain the row data (or fields) of an Oracle record.</span></span> <span data-ttu-id="82f4b-146">在 WCF 服務模型中，每一種 XML 類型被以.NET 類別;此類別的屬性代表記錄型別或 REF 資料指標結果集的欄位。</span><span class="sxs-lookup"><span data-stu-id="82f4b-146">In the WCF service model, each of these XML types is represented as a .NET class; the properties of the class represent the fields of the RECORD type or REF CURSOR result set.</span></span> <span data-ttu-id="82f4b-147">強型別.NET 類別一律會以表示 oracle 記錄類型。</span><span class="sxs-lookup"><span data-stu-id="82f4b-147">Oracle RECORD types are always represented as strongly-typed .NET classes.</span></span> <span data-ttu-id="82f4b-148">然而，REF 資料指標結果集，可以表示為 REF CURSOR 本身是否宣告為強型別或弱式型別為基礎的強型別，或弱式型別的記錄。</span><span class="sxs-lookup"><span data-stu-id="82f4b-148">A REF CURSOR result set, however, can be represented as either strongly-typed or weakly-typed records based on whether the REF CURSOR itself is declared as strongly-typed or weakly-typed.</span></span> <span data-ttu-id="82f4b-149">表示 REF CURSOR 或記錄型別參數 （或傳回值） 會在基礎程序、 函數或封裝的唯一命名空間中產生的類別。</span><span class="sxs-lookup"><span data-stu-id="82f4b-149">The classes that represent REF CURSOR or RECORD type parameters (or return values) are generated in a unique namespace based on the procedure, function, or package.</span></span> <span data-ttu-id="82f4b-150">下表顯示這些命名空間。</span><span class="sxs-lookup"><span data-stu-id="82f4b-150">The following table shows these namespaces.</span></span>  
  
|<span data-ttu-id="82f4b-151">Oracle 成品</span><span class="sxs-lookup"><span data-stu-id="82f4b-151">Oracle Artifact</span></span>|<span data-ttu-id="82f4b-152">命名空間</span><span class="sxs-lookup"><span data-stu-id="82f4b-152">Namespace</span></span>|<span data-ttu-id="82f4b-153">範例</span><span class="sxs-lookup"><span data-stu-id="82f4b-153">Example</span></span>|  
|---------------------|---------------|-------------|  
|<span data-ttu-id="82f4b-154">程序</span><span class="sxs-lookup"><span data-stu-id="82f4b-154">Procedure</span></span>|<span data-ttu-id="82f4b-155">[BASE_NS]。</span><span class="sxs-lookup"><span data-stu-id="82f4b-155">[BASE_NS].</span></span> <span data-ttu-id="82f4b-156">[SCHEMA]。程序。[PROC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-156">[SCHEMA].Procedure.[PROC_NAME]</span></span>|<span data-ttu-id="82f4b-157">microsoft.lobservices.oracledb._2007._03.SCOTT。Procedure.MYPROC</span><span class="sxs-lookup"><span data-stu-id="82f4b-157">microsoft.lobservices.oracledb._2007._03.SCOTT.Procedure.MYPROC</span></span>|  
|<span data-ttu-id="82f4b-158">函數</span><span class="sxs-lookup"><span data-stu-id="82f4b-158">Function</span></span>|<span data-ttu-id="82f4b-159">[BASE_NS]。</span><span class="sxs-lookup"><span data-stu-id="82f4b-159">[BASE_NS].</span></span> <span data-ttu-id="82f4b-160">[SCHEMA]。函式。[FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-160">[SCHEMA].Function.[FUNC_NAME]</span></span>|<span data-ttu-id="82f4b-161">microsoft.lobservices.oracledb._2007._03.SCOTT。Function.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="82f4b-161">microsoft.lobservices.oracledb._2007._03.SCOTT.Function.MYFUNC</span></span>|  
|<span data-ttu-id="82f4b-162">封裝 （程序）</span><span class="sxs-lookup"><span data-stu-id="82f4b-162">Package (Procedure)</span></span>|<span data-ttu-id="82f4b-163">[BASE_NS]。</span><span class="sxs-lookup"><span data-stu-id="82f4b-163">[BASE_NS].</span></span> <span data-ttu-id="82f4b-164">[SCHEMA]。封裝。[PACKAGE_NAME]。[PROC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-164">[SCHEMA].Package.[PACKAGE_NAME].[PROC_NAME]</span></span>|<span data-ttu-id="82f4b-165">microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYPROC</span><span class="sxs-lookup"><span data-stu-id="82f4b-165">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYPROC</span></span>|  
|<span data-ttu-id="82f4b-166">封裝 （函式）</span><span class="sxs-lookup"><span data-stu-id="82f4b-166">Package (Function)</span></span>|<span data-ttu-id="82f4b-167">[BASE_NS]。</span><span class="sxs-lookup"><span data-stu-id="82f4b-167">[BASE_NS].</span></span> <span data-ttu-id="82f4b-168">[SCHEMA]。封裝。[PACKAGE_NAME]。[FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-168">[SCHEMA].Package.[PACKAGE_NAME].[FUNC_NAME]</span></span>|<span data-ttu-id="82f4b-169">microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="82f4b-169">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYFUNC</span></span>|  
|<span data-ttu-id="82f4b-170">一般記錄集 （弱型別）</span><span class="sxs-lookup"><span data-stu-id="82f4b-170">Generic Record Set (weakly-typed)</span></span>|<span data-ttu-id="82f4b-171">[BASE_NS]</span><span class="sxs-lookup"><span data-stu-id="82f4b-171">[BASE_NS]</span></span>|<span data-ttu-id="82f4b-172">microsoft.lobservices.oracledb._2007._03</span><span class="sxs-lookup"><span data-stu-id="82f4b-172">microsoft.lobservices.oracledb._2007._03</span></span>|  
  
 <span data-ttu-id="82f4b-173">[BASE_NS] = 的基底配接器命名空間中。microsoft.lobservices.oracledb._2007._03。</span><span class="sxs-lookup"><span data-stu-id="82f4b-173">[BASE_NS] = The base adapter namespace; microsoft.lobservices.oracledb._2007._03.</span></span>  
  
 <span data-ttu-id="82f4b-174">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="82f4b-174">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="82f4b-175">[PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-175">[PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.</span></span>  
  
 <span data-ttu-id="82f4b-176">[FUNC_NAME] = Oracle 函式; 的名稱比方說 MYFUNC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-176">[FUNC_NAME] = The name of an Oracle function; for example MYFUNC.</span></span>  
  
 <span data-ttu-id="82f4b-177">[PACKAGE_NAME] = Oracle 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="82f4b-177">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="82f4b-178">如需這些命名空間如何用於記錄參數資訊，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-178">For information about how these namespaces are used for RECORD parameters, see [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span> <span data-ttu-id="82f4b-179">如需這些命名空間中如何使用 REF CURSOR 參數的詳細資訊，請參閱[執行作業使用 REF 資料指標在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-179">For information about how these namespaces are used for REF CURSOR parameters, see [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="82f4b-180">一般情況下，Oracle 參數和傳回值會對應，如下所示的 WCF 用戶端方法中：</span><span class="sxs-lookup"><span data-stu-id="82f4b-180">In general, the Oracle parameters and return values are mapped as follows in the WCF client method:</span></span>  
  
- <span data-ttu-id="82f4b-181">Oracle IN 參數會對應至.NET （輸入） 的參數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-181">Oracle IN parameters are mapped to .NET (input) parameters.</span></span>  
  
- <span data-ttu-id="82f4b-182">Oracle OUT 參數會對應至.NET**出**參數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-182">Oracle OUT parameters are mapped to .NET **out** parameters.</span></span>  
  
- <span data-ttu-id="82f4b-183">Oracle 在 OUT 參數會對應至.NET **ref**參數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-183">Oracle IN OUT parameters are mapped to .NET **ref** parameters.</span></span>  
  
- <span data-ttu-id="82f4b-184">函式傳回值會對應至方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="82f4b-184">Function RETURN values are mapped to the method return value.</span></span>  
  
  <span data-ttu-id="82f4b-185">不過，有兩個重要的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="82f4b-185">However, two important exceptions exist:</span></span>  
  
- <span data-ttu-id="82f4b-186">Oracle IN 出 REF CURSOR 參數會分割輸入的字串和輸出 (**出**) 記錄集。</span><span class="sxs-lookup"><span data-stu-id="82f4b-186">Oracle IN OUT REF CURSOR parameters are split into an input string and an output (**out**) record set.</span></span> <span data-ttu-id="82f4b-187">這是因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示在 REF CUSROR 參數做為字串和出 REF CURSOR 參數做為複雜型別 （記錄集），無法合併至單一參數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-187">This is because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents IN REF CUSROR parameters as strings and OUT REF CURSOR parameters as complex types (record sets), these cannot be combined into a single parameter.</span></span>  
  
- <span data-ttu-id="82f4b-188">OUT 參數的 Oracle 程序中的第一個會對應至 WCF 用戶端方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="82f4b-188">The first OUT parameter in an Oracle procedure is mapped to the return value of the WCF client method.</span></span> <span data-ttu-id="82f4b-189">這是標準的 WCF 行為。</span><span class="sxs-lookup"><span data-stu-id="82f4b-189">This is standard WCF behavior.</span></span>  
  
  <span data-ttu-id="82f4b-190">下列範例會示範簡單 （載入 SCOTT 結構描述中） 的 Oracle 程序的一部分，並且會叫用它產生 WCF 用戶端方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="82f4b-190">The following example shows part of a simple Oracle procedure (loaded in the SCOTT schema) and the signature of the WCF client method that is generated to invoke it.</span></span> <span data-ttu-id="82f4b-191">Oracle 程序有三個 IN 參數、 三個在 OUT 參數，以及三個 OUT 參數。不過，WCF 用戶端方法未對應的 OUT 參數的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-191">The Oracle procedure has three IN parameters, three IN OUT parameters, and three OUT parameters; however, the WCF client method does not map a parameter for the first OUT parameter.</span></span> <span data-ttu-id="82f4b-192">而是會對應至方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="82f4b-192">Instead it is mapped to the method return value.</span></span>  
  
```  
CREATE or REPLACE PROCEDURE Sample_Procedure   
    (  
     INNUMBER      IN         NUMBER,  
     INVARCHAR     IN         VARCHAR2,  
     INDATE        IN         DATE,  
     INOUTNUMBER   IN OUT     NUMBER,  
     INOUTVARCHAR  IN OUT     VARCHAR,  
     INOUTDATE     IN OUT     DATE,  
     OUTNUMBER     OUT        NUMBER,  
     OUTVARCHAR    OUT        VARCHAR2,  
     OUTDATE       OUT        DATE  
    ) AS   
    BEGIN  
  
        ...  
  
    END;  
    /  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTProcedureClient : System.ServiceModel.ClientBase<SCOTTProcedure>, SCOTTProcedure {  
  
    public System.Nullable<decimal> SAMPLE_PROCEDURE  
       (  
        System.Nullable<decimal> INNUMBER,   
        string INVARCHAR,   
        System.Nullable\<System.DateTime\> INDATE,   
        ref System.Nullable<decimal> INOUTNUMBER,   
        ref string INOUTVARCHAR,   
        ref System.Nullable\<System.DateTime\> INOUTDATE,   
        out string OUTVARCHAR,   
        out System.Nullable\<System.DateTime\> OUTDATE  
        );  
}  
```  
  
### <a name="support-for-overloaded-procedures-functions-and-packages"></a><span data-ttu-id="82f4b-193">支援多載程序、 函數和封裝</span><span class="sxs-lookup"><span data-stu-id="82f4b-193">Support for Overloaded Procedures, Functions and Packages</span></span>  
 <span data-ttu-id="82f4b-194">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援由多載程序、 函數和封裝將唯一的字串附加至的節點識別碼，它會呈現每個多載成品的命名空間。</span><span class="sxs-lookup"><span data-stu-id="82f4b-194">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports overloaded procedures, functions, and packages by appending a unique string to the node ID and the namespace that it surfaces for each overloaded artifact.</span></span> <span data-ttu-id="82f4b-195">此字串會是第一個多載而言，「 overload2""overload1 」 下, 一個多載，依此類推。</span><span class="sxs-lookup"><span data-stu-id="82f4b-195">This string is "overload1" for the first overload, "overload2" for the next overload, and so on.</span></span>  
  
 <span data-ttu-id="82f4b-196">WCF 服務模型中每個多載程序或函式被以唯一的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="82f4b-196">In the WCF service model each overloaded procedure or function is represented by a unique WCF client.</span></span> <span data-ttu-id="82f4b-197">這點不同於非多載中的案例中的結構描述中結構描述的程序的所有函式的所有或所有的程序和封裝中的函式會叫用相同的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="82f4b-197">This is different from the non-overloaded case in which all of the functions in a SCHEMA, all of the procedures in a SCHEMA, or all of the procedures and functions in a PACKAGE are invoked by the same WCF client.</span></span> <span data-ttu-id="82f4b-198">下表會顯示 WCF 用戶端名稱和方法多載程序、 函式，以及封裝所產生。</span><span class="sxs-lookup"><span data-stu-id="82f4b-198">The following table shows the WCF client name and method generated for overloaded procedures, functions, and packages.</span></span>  
  
|<span data-ttu-id="82f4b-199">Oracle 成品</span><span class="sxs-lookup"><span data-stu-id="82f4b-199">Oracle Artifact</span></span>|<span data-ttu-id="82f4b-200">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="82f4b-200">WCF Client Name</span></span>|<span data-ttu-id="82f4b-201">範例</span><span class="sxs-lookup"><span data-stu-id="82f4b-201">Example</span></span>|  
|---------------------|---------------------|-------------|  
|<span data-ttu-id="82f4b-202">多載的封裝 （程序）</span><span class="sxs-lookup"><span data-stu-id="82f4b-202">Overloaded Package (Procedure)</span></span>|<span data-ttu-id="82f4b-203">[結構描述]套件 [PACKAGE_NAME] [PROC_NAME]] [OVERLOAD_ID] 用戶端。[PROC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-203">[SCHEMA]Package[PACKAGE_NAME][PROC_NAME] ][OVERLOAD_ID]Client.[PROC_NAME]</span></span>|<span data-ttu-id="82f4b-204">SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC</span><span class="sxs-lookup"><span data-stu-id="82f4b-204">SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC</span></span>|  
|<span data-ttu-id="82f4b-205">多載的封裝 （函式）</span><span class="sxs-lookup"><span data-stu-id="82f4b-205">Overloaded Package (Function)</span></span>|<span data-ttu-id="82f4b-206">[結構描述]套件 [PACKAGE_NAME] [FUNC_NAME]] [OVERLOAD_ID] 用戶端。[FUNC_NAME]</span><span class="sxs-lookup"><span data-stu-id="82f4b-206">[SCHEMA]Package[PACKAGE_NAME][FUNC_NAME] ][OVERLOAD_ID]Client.[FUNC_NAME]</span></span>|<span data-ttu-id="82f4b-207">SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC</span><span class="sxs-lookup"><span data-stu-id="82f4b-207">SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC</span></span>|  
  
 <span data-ttu-id="82f4b-208">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="82f4b-208">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="82f4b-209">[PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-209">[PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.</span></span>  
  
 <span data-ttu-id="82f4b-210">[FUNC_NAME] = Oracle 函式; 的名稱比方說 MYFUNC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-210">[FUNC_NAME] = The name of an Oracle function; for example MYFUNC.</span></span>  
  
 <span data-ttu-id="82f4b-211">[PACKAGE_NAME] = Oracle 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="82f4b-211">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="82f4b-212">[OVERLOAD_ID] = 唯一的字串，識別多載的成品;「 overload1"、"overload2"，等等。</span><span class="sxs-lookup"><span data-stu-id="82f4b-212">[OVERLOAD_ID] = The unique string that identifies the overloaded artifact; "overload1", "overload2", and so on.</span></span>  
  
 <span data-ttu-id="82f4b-213">下表顯示的多載程序、 函數和封裝所產生的命名空間。</span><span class="sxs-lookup"><span data-stu-id="82f4b-213">The following table shows the namespace generated for overloaded procedures, functions, and packages.</span></span>  
  
|<span data-ttu-id="82f4b-214">Oracle 成品</span><span class="sxs-lookup"><span data-stu-id="82f4b-214">Oracle Artifact</span></span>|<span data-ttu-id="82f4b-215">命名空間</span><span class="sxs-lookup"><span data-stu-id="82f4b-215">Namespace</span></span>|<span data-ttu-id="82f4b-216">範例</span><span class="sxs-lookup"><span data-stu-id="82f4b-216">Example</span></span>|  
|---------------------|---------------|-------------|  
|<span data-ttu-id="82f4b-217">封裝 （程序）</span><span class="sxs-lookup"><span data-stu-id="82f4b-217">Package (Procedure)</span></span>|<span data-ttu-id="82f4b-218">[BASE_NS]。</span><span class="sxs-lookup"><span data-stu-id="82f4b-218">[BASE_NS].</span></span> <span data-ttu-id="82f4b-219">[SCHEMA]。封裝。[PACKAGE_NAME]。[PROC_NAME][OVERLOAD_ID]</span><span class="sxs-lookup"><span data-stu-id="82f4b-219">[SCHEMA].Package.[PACKAGE_NAME].[PROC_NAME] [OVERLOAD_ID]</span></span>|<span data-ttu-id="82f4b-220">microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYPROC.overload1</span><span class="sxs-lookup"><span data-stu-id="82f4b-220">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYPROC.overload1</span></span>|  
|<span data-ttu-id="82f4b-221">封裝 （函式）</span><span class="sxs-lookup"><span data-stu-id="82f4b-221">Package (Function)</span></span>|<span data-ttu-id="82f4b-222">[BASE_NS]。</span><span class="sxs-lookup"><span data-stu-id="82f4b-222">[BASE_NS].</span></span> <span data-ttu-id="82f4b-223">[SCHEMA]。封裝。[PACKAGE_NAME]。[FUNC_NAME]。[OVERLOAD_ID]</span><span class="sxs-lookup"><span data-stu-id="82f4b-223">[SCHEMA].Package.[PACKAGE_NAME].[FUNC_NAME].[OVERLOAD_ID]</span></span>|<span data-ttu-id="82f4b-224">microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYFUNC.overload1</span><span class="sxs-lookup"><span data-stu-id="82f4b-224">microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYFUNC.overload1</span></span>|  
|<span data-ttu-id="82f4b-225">一般記錄集 （弱型別）</span><span class="sxs-lookup"><span data-stu-id="82f4b-225">Generic Record Set (weakly-typed)</span></span>|<span data-ttu-id="82f4b-226">[BASE_NS]</span><span class="sxs-lookup"><span data-stu-id="82f4b-226">[BASE_NS]</span></span>|<span data-ttu-id="82f4b-227">microsoft.lobservices.oracledb._2007._03</span><span class="sxs-lookup"><span data-stu-id="82f4b-227">microsoft.lobservices.oracledb._2007._03</span></span>|  
  
 <span data-ttu-id="82f4b-228">[BASE_NS] = 的基底配接器命名空間中。microsoft.lobservices.oracledb._2007._03。</span><span class="sxs-lookup"><span data-stu-id="82f4b-228">[BASE_NS] = The base adapter namespace; microsoft.lobservices.oracledb._2007._03.</span></span>  
  
 <span data-ttu-id="82f4b-229">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="82f4b-229">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="82f4b-230">[PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-230">[PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.</span></span>  
  
 <span data-ttu-id="82f4b-231">[FUNC_NAME] = Oracle 函式; 的名稱比方說 MYFUNC。</span><span class="sxs-lookup"><span data-stu-id="82f4b-231">[FUNC_NAME] = The name of an Oracle function; for example MYFUNC.</span></span>  
  
 <span data-ttu-id="82f4b-232">[PACKAGE_NAME] = Oracle 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="82f4b-232">[PACKAGE_NAME] = The name of an Oracle package.</span></span>  
  
 <span data-ttu-id="82f4b-233">[OVERLOAD_ID] = 唯一的字串，識別多載的成品;「 overload1"、"overload2"，等等。</span><span class="sxs-lookup"><span data-stu-id="82f4b-233">[OVERLOAD_ID] = The unique string that identifies the overloaded artifact; "overload1", "overload2", and so on.</span></span> <span data-ttu-id="82f4b-234">在字串中的數值是 Oracle 資料庫所維護之成品的多載識別碼。</span><span class="sxs-lookup"><span data-stu-id="82f4b-234">The numeric value in the string is the overload ID for the artifact maintained by the Oracle database.</span></span>  
  
 <span data-ttu-id="82f4b-235">下列範例示範 WCF 用戶端和 ACCOUNT_PKG 封裝中的多載 GET_ACCOUNT 程序所產生的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="82f4b-235">The following example shows the WCF clients and the method signatures generated for the overloaded GET_ACCOUNT procedure in the ACCOUNT_PKG package.</span></span> <span data-ttu-id="82f4b-236">（Oracle 宣告會包含）。此範例會示範如何產生唯一的 WCF 用戶端的每一個多載，以及如何產生每個用戶端的方法會傳回唯一的命名空間中的記錄集。</span><span class="sxs-lookup"><span data-stu-id="82f4b-236">(The Oracle declarations are included.) This example shows how a unique WCF client is generated for each overload and how the method generated for each client returns a record set in a unique namespace.</span></span>  
  
```  
/* Procedure that takes account ID and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aid IN account.acctid%TYPE, acct OUT account%ROWTYPE) ;  
  
/* Procedure that takes account name and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aname IN account.name%TYPE, acct OUT account%ROWTYPE) ;  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1.ACCTRECORD GET_ACCOUNT(System.Nullable<decimal> AID);  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2.ACCTRECORD GET_ACCOUNT(string ANAME);  
}  
```  
  
## <a name="invoking-functions-and-procedures"></a><span data-ttu-id="82f4b-237">叫用的函數和程序</span><span class="sxs-lookup"><span data-stu-id="82f4b-237">Invoking Functions and Procedures</span></span>  
 <span data-ttu-id="82f4b-238">若要使用 WCF 用戶端，叫用函式或程序，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="82f4b-238">To invoke a function or a procedure by using a WCF client, perform the following steps.</span></span>  
  
1. <span data-ttu-id="82f4b-239">產生 WCF 用戶端類別，目標函式、 程序，或封裝。</span><span class="sxs-lookup"><span data-stu-id="82f4b-239">Generate a WCF client class for the target function, procedure, or package.</span></span> <span data-ttu-id="82f4b-240">這個類別應該包含您將會在目標成品叫用作業的方法。</span><span class="sxs-lookup"><span data-stu-id="82f4b-240">This class should contain methods for the operations that you will invoke on the target artifact.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="82f4b-241">在[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，多載函式和程序會出現在**可用的類別和作業**為 [NAME].1、.2、.3，[名稱] [名稱] 方塊並依此類推，其中 [名稱] 是多載的成品和數字值的名稱是的 Oracle 資料庫上的多載識別碼。</span><span class="sxs-lookup"><span data-stu-id="82f4b-241">In the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], overloaded functions and procedures appear in the **Available categories and operations** box as [NAME].1, [NAME].2, [NAME].3, and so on, where [NAME] is the name of the overloaded artifact and the numeric value is the overload ID on the Oracle database.</span></span>  
  
2. <span data-ttu-id="82f4b-242">建立 WCF 用戶端類別的執行個體，並呼叫其方法來叫用函式或程序。</span><span class="sxs-lookup"><span data-stu-id="82f4b-242">Create an instance of the WCF client class and call its methods to invoke the function or procedure.</span></span>  
  
   <span data-ttu-id="82f4b-243">如需詳細資訊，有關如何建立 WCF 用戶端類別，並在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 的 Oracle 資料庫配接器使用 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-243">For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span></span>  
  
   <span data-ttu-id="82f4b-244">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的 Oracle 資料庫上執行每個作業在交易內。</span><span class="sxs-lookup"><span data-stu-id="82f4b-244">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes each operation inside of a transaction on the Oracle database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82f4b-245">唯一的命名空間中宣告類別代表 REF CURSOR 和記錄型別參數或傳回值的函式或程序 （和封裝） 中的每個函式或程序。</span><span class="sxs-lookup"><span data-stu-id="82f4b-245">The classes that represent REF CURSOR and RECORD type parameters or return values in functions or procedures (and packages) are declared in a unique namespace for each function or procedure.</span></span> <span data-ttu-id="82f4b-246">這表示，例如，做為兩個不同的函式的傳回值的封裝 REF 資料指標類型會宣告唯一的命名空間中，每個 WCF 用戶端方法。</span><span class="sxs-lookup"><span data-stu-id="82f4b-246">This means, for example, that a PACKAGE REF CURSOR type that is used as a return value in two different functions will be declared in a unique namespace for each WCF client method.</span></span> <span data-ttu-id="82f4b-247">您可能必須宣告不同變數來保存這些不同的傳回值，或當您叫用 WCF 用戶端方法的其中一個適當轉換變數。</span><span class="sxs-lookup"><span data-stu-id="82f4b-247">You must either declare separate variables to hold these different return values or appropriately cast the variable when you invoke one of the WCF client methods.</span></span>  
  
 <span data-ttu-id="82f4b-248">下列範例示範如何呼叫的多載的 /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT 程序，以取得 /SCOTT/ACCOUNT 資料表中的帳戶記錄。</span><span class="sxs-lookup"><span data-stu-id="82f4b-248">The following example demonstrates calling the overloaded /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT procedure to get account records from the /SCOTT/ACCOUNT table.</span></span> <span data-ttu-id="82f4b-249">先透過呼叫 /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT 程序建立新的記錄。</span><span class="sxs-lookup"><span data-stu-id="82f4b-249">First a new record is created by calling the /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT procedure.</span></span> <span data-ttu-id="82f4b-250">然後讀取新的記錄後，兩次藉由呼叫 GET_ACCOUNT 的不同多載。</span><span class="sxs-lookup"><span data-stu-id="82f4b-250">Then the new record is read back twice by calling different overloads of GET_ACCOUNT.</span></span> <span data-ttu-id="82f4b-251">此範例使用三個 WCF 用戶端，一個用於 CREATE_ACCOUNT 程序，每個代表 GET_ACCOUNT 多載。</span><span class="sxs-lookup"><span data-stu-id="82f4b-251">This example uses three WCF clients, one for the CREATE_ACCOUNT procedure and one each for the GET_ACCOUNT overloads.</span></span> <span data-ttu-id="82f4b-252">別名用來區別 GET_ACCOUNT 的傳回值所使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="82f4b-252">Aliases are used to distinguish between namespaces used for the return value of GET_ACCOUNT.</span></span> <span data-ttu-id="82f4b-253">使用 SDK 範例的完整範例。</span><span class="sxs-lookup"><span data-stu-id="82f4b-253">A full sample is available in the SDK samples.</span></span> <span data-ttu-id="82f4b-254">如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="82f4b-254">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// Alias client namespaces to shorten declarations of "shared" types   
using CREATE_ACCOUNTns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT;  
using GET_ACCOUNT_BY_IDns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1;  
using GET_ACCOUNT_BY_NAMEns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2;  
  
// This sample demonstrates calling overloaded packaged procedures on Oracle  
// First a new account is created by calling CREATE_ACCOUNT which takes two record parameters  
// Then the information for the new account is returned by calling an overloaded procedure GET_ACCOUNT  
// The first overload returns the account information by account ID  
// The second overload returns the account information by account name  
// Notice that different clients (and namespaces) are created for overloaded procedures and functions  
namespace OracleOverloadsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            decimal acctId;  
            string newAccountName = "Paula Bento";  
  
            Console.WriteLine("Creating clients");  
            // Create Client for CREATE_ACCOUNT Function  
            SCOTTPackageACCOUNT_PKGClient createAccountClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // NOTE: user name and password are case-sensitive  
            createAccountClient.ClientCredentials.UserName.UserName = "SCOTT";  
            createAccountClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 1 -- takes ACCOUNT ID parameter  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client getAccountByIdClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1");  
            // NOTE: user name and password are case-sensitive  
            getAccountByIdClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByIdClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 2 -- takes ACCOUNT NAME parameter  
            // NOTE: this client can be created from configuration; detail provided here  
            // for demonstration  
            OracleDBBinding overload2Binding = new OracleDBBinding();  
            EndpointAddress overload2EndpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client getAccountByNameClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client(overload2Binding, overload2EndpointAddress);  
            // NOTE: user name and password are case-sensitive  
            getAccountByNameClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByNameClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
                Console.WriteLine("Opening clients -- please wait");  
                // Open clients  
                createAccountClient.Open();  
                getAccountByIdClient.Open();  
                getAccountByNameClient.Open();  
  
                Console.WriteLine("Creating new account");  
                // Create an account record  
                // NOTE: ACCTRECORD is defined in all three namespaces so specify the definition  
                // that corresponds to the client.  
                CREATE_ACCOUNTns.ACCTRECORD acctRec = new CREATE_ACCOUNTns.ACCTRECORD();  
  
                // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
                acctRec.ACCTID = 0;  
                acctRec.NAME = newAccountName;  
                acctRec.BALANCE = 10537;  
  
                // Create address record  
                CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
                addrRec.STREET = "456 Valley Rd";  
                addrRec.CITY = "New York";  
                addrRec.STATE = "NY";  
  
                // Create account  
                acctId = (decimal)createAccountClient.CREATE_ACCOUNT(acctRec, addrRec);  
                Console.WriteLine("New Account Created: AccountId = {0}, Name = {1}, Balance = {2:C}",  
                   acctId, acctRec.NAME, acctRec.BALANCE);  
  
                /* Get new account by Id */  
                GET_ACCOUNT_BY_IDns.ACCTRECORD acctById = getAccountByIdClient.GET_ACCOUNT(acctId);  
                Console.WriteLine("Account Returned by Id: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctById.ACCTID, acctById.NAME, acctById.BALANCE);  
  
                /* Get new account by Name */  
                GET_ACCOUNT_BY_NAMEns.ACCTRECORD acctByName = getAccountByNameClient.GET_ACCOUNT(newAccountName);  
                Console.WriteLine("Account Returned by Name: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctByName.ACCTID, acctByName.NAME, acctByName.BALANCE);  
  
                Console.WriteLine("Hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close all the clients  
                createAccountClient.Close();  
                getAccountByIdClient.Close();  
                getAccountByNameClient.Close();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="82f4b-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82f4b-255">See Also</span></span>  
 [<span data-ttu-id="82f4b-256">使用 WCF 服務模型開發 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="82f4b-256">Develop Oracle Database Applications by Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)