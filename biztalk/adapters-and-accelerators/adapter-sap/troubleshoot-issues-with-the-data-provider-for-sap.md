---
title: "適用於 SAP 的資料提供者的問題進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, troubleshooting
- troubleshooting, Data Provider for SAP
ms.assetid: 6fe9baed-0404-4f15-b76e-88cc11c5ff46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba61b75f95fad429c70da42479f22a32fa4e5a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-issues-with-the-data-provider-for-sap"></a><span data-ttu-id="74f52-102">疑難排解資料提供者適用於 SAP 的問題</span><span class="sxs-lookup"><span data-stu-id="74f52-102">Troubleshoot Issues with the Data Provider for SAP</span></span>
<span data-ttu-id="74f52-103">本章節將討論使用來解析作業使用時可能遭遇的錯誤的疑難排解技術[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="74f52-103">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>  
  
##  <span data-ttu-id="74f52-104"><a name="BKMK_SAPUnknownParam"></a>使用此資料提供者適用於 SAP 的未知的參數錯誤</span><span class="sxs-lookup"><span data-stu-id="74f52-104"><a name="BKMK_SAPUnknownParam"></a> Unknown Parameter error using the Data Provider for SAP</span></span>  
 <span data-ttu-id="74f52-105">**問題**</span><span class="sxs-lookup"><span data-stu-id="74f52-105">**Problem**</span></span>  
  
 <span data-ttu-id="74f52-106">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="74f52-106">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] gives the following error:</span></span>  
  
```  
Microsoft.Data.SAPClient.SAPException: Failed to retrieve data from SAP server --- > Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Unknown Parameter OUT_ZDATATABLE.  
```  
  
 <span data-ttu-id="74f52-107">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="74f52-107">**Cause**</span></span>  
  
 <span data-ttu-id="74f52-108">不是最新的自訂 RFC、 Z_EXTRACT_DATA_OO，安裝在 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="74f52-108">The custom RFC, Z_EXTRACT_DATA_OO, installed in your SAP system is not the latest.</span></span> <span data-ttu-id="74f52-109">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用的自訂 RFC Z_EXTRACT_DATA_OO，執行 SAP 資料表上的 SELECT 作業。</span><span class="sxs-lookup"><span data-stu-id="74f52-109">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC, Z_EXTRACT_DATA_OO, to perform SELECT operations on the SAP table.</span></span>  
  
 <span data-ttu-id="74f52-110">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="74f52-110">**Resolution**</span></span>  
  
 <span data-ttu-id="74f52-111">您必須更新自訂 RFC 為最新可用版本。</span><span class="sxs-lookup"><span data-stu-id="74f52-111">You must update the custom RFC to the latest available version.</span></span> <span data-ttu-id="74f52-112">此 RFC，Z_EXTRACT_DATA_OO，隨附於 adapterpacknoversion。</span><span class="sxs-lookup"><span data-stu-id="74f52-112">This RFC, Z_EXTRACT_DATA_OO, is available with the adapterpacknoversion.</span></span> <span data-ttu-id="74f52-113">如需如何安裝和解除安裝自訂 RFC 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="74f52-113">For more information about how to install and uninstall the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>
  
##  <span data-ttu-id="74f52-114"><a name="BKMK_SAPOOM"></a>記憶體不足例外狀況時從 SAP 資料表選取資料</span><span class="sxs-lookup"><span data-stu-id="74f52-114"><a name="BKMK_SAPOOM"></a> Out of memory exceptions when selecting data from an SAP table</span></span>  
 <span data-ttu-id="74f52-115">**問題**</span><span class="sxs-lookup"><span data-stu-id="74f52-115">**Problem**</span></span>  
  
 <span data-ttu-id="74f52-116">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] SAP 系統從選取的資料時，會擲回記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74f52-116">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] throws an out of memory exception when selecting data from an SAP system.</span></span>  
  
 <span data-ttu-id="74f52-117">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="74f52-117">**Cause**</span></span>  
  
 <span data-ttu-id="74f52-118">根據預設， [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] 10,000 個資料列擷取一次。</span><span class="sxs-lookup"><span data-stu-id="74f52-118">By default, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retrieves 10,000 rows at a time.</span></span> <span data-ttu-id="74f52-119">此外，從 SAP 系統擷取資料列的每個批次會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="74f52-119">Also, each batch of rows retrieved from the SAP system is stored in the memory.</span></span> <span data-ttu-id="74f52-120">因此，</span><span class="sxs-lookup"><span data-stu-id="74f52-120">So,</span></span>  
  
-   <span data-ttu-id="74f52-121">如果從中擷取資料的資料表包含大量的資料列，或</span><span class="sxs-lookup"><span data-stu-id="74f52-121">If the table from which data is being retrieved contains a large number of rows, or</span></span>  
  
-   <span data-ttu-id="74f52-122">如果資料表包含資料行的資料型別會耗用大量的記憶體，</span><span class="sxs-lookup"><span data-stu-id="74f52-122">If the table contains columns of data types that consume a significant amount of memory,</span></span>  
  
 <span data-ttu-id="74f52-123">記憶體耗用量[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]大幅增加，而且可能會導致記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74f52-123">The memory consumption by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] increases significantly and may result in an out of memory exception.</span></span>  
  
 <span data-ttu-id="74f52-124">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="74f52-124">**Resolution**</span></span>  
  
 <span data-ttu-id="74f52-125">您可以變更從 SAP 系統擷取資料列的數目上限。</span><span class="sxs-lookup"><span data-stu-id="74f52-125">You can change the maximum number of rows retrieved from the SAP system.</span></span> <span data-ttu-id="74f52-126">您可以藉由指定 SELECT 陳述式的 'batchsize' 選項。</span><span class="sxs-lookup"><span data-stu-id="74f52-126">You can do so by specifying a 'batchsize' option with the SELECT statement.</span></span> <span data-ttu-id="74f52-127">例如：</span><span class="sxs-lookup"><span data-stu-id="74f52-127">For example:</span></span>  
  
```  
SELECT * FROM <tablename> OPTION 'batchsize 1000'  
```  
  
 <span data-ttu-id="74f52-128">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]現在一次擷取只 1000 個資料列，因此不會耗用大量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="74f52-128">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] now retrieves only 1000 rows at a time and hence does not consume large amount of memory.</span></span>  
  
##  <span data-ttu-id="74f52-129"><a name="BKMK_SAPQueryExcep"></a>例外狀況時執行的查詢，會採用具有日期值的參數</span><span class="sxs-lookup"><span data-stu-id="74f52-129"><a name="BKMK_SAPQueryExcep"></a> Exception while executing a query that takes parameters with date values</span></span>  
 <span data-ttu-id="74f52-130">**問題**</span><span class="sxs-lookup"><span data-stu-id="74f52-130">**Problem**</span></span>  
  
 <span data-ttu-id="74f52-131">當您執行查詢，使用 EXECQUERY 命令採用日期值的參數時，您會取得下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="74f52-131">You get the following exception when you execute a query using the EXECQUERY command that has a parameter which takes a date value:</span></span>  
  
```  
ErrorCode=RFC_SYS_EXCEPTION. ErrorGroup=RFC_ERROR_SYSTEM_FAILURE.   
SapErrorMessage=Enter date in the format __.__.____.  
```  
  
 <span data-ttu-id="74f52-132">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="74f52-132">**Cause**</span></span>  
  
 <span data-ttu-id="74f52-133">執行時使用 EXECQUERY 命令的查詢，您必須一律指定日期值，格式為 YYYYMMDD。</span><span class="sxs-lookup"><span data-stu-id="74f52-133">When executing queries using the EXECQUERY command, you must always specify date values in YYYYMMDD format.</span></span>  
  
 <span data-ttu-id="74f52-134">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="74f52-134">**Resolution**</span></span>  
  
 <span data-ttu-id="74f52-135">請確定您指定的日期值格式為 YYYYMMDD。</span><span class="sxs-lookup"><span data-stu-id="74f52-135">Make sure you specify date values in YYYYMMDD format.</span></span> <span data-ttu-id="74f52-136">例如：</span><span class="sxs-lookup"><span data-stu-id="74f52-136">For example:</span></span>  
  
```  
EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1='20080606'  
```  
  
##  <span data-ttu-id="74f52-137"><a name="BKMK_SAPNOVARIANT"></a>執行查詢使用 EXECQUERY 命令 NO_VARIANT 例外狀況</span><span class="sxs-lookup"><span data-stu-id="74f52-137"><a name="BKMK_SAPNOVARIANT"></a> NO_VARIANT exception executing queries using the EXECQUERY command</span></span>  
 <span data-ttu-id="74f52-138">**問題**</span><span class="sxs-lookup"><span data-stu-id="74f52-138">**Problem**</span></span>  
  
 <span data-ttu-id="74f52-139">當您執行查詢，使用 EXECQUERY 命令時，您會取得下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="74f52-139">You get the following exception when you execute a query using the EXECQUERY command:</span></span>  
  
```  
Exception: Details: ErrorCode=RFC_EXCEPTION. ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage=NO_VARIANT.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: <RFC name>  
```  
  
 <span data-ttu-id="74f52-140">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="74f52-140">**Cause**</span></span>  
  
 <span data-ttu-id="74f52-141">可以有兩個可能原因，此例外狀況：</span><span class="sxs-lookup"><span data-stu-id="74f52-141">There can be two probable causes for this exception:</span></span>  
  
1.  <span data-ttu-id="74f52-142">您嘗試執行此查詢有 SAP 系統中定義的變數。</span><span class="sxs-lookup"><span data-stu-id="74f52-142">The query you are trying to execute has variants defined in the SAP system.</span></span> <span data-ttu-id="74f52-143">變數是指一組儲存執行 SAP 查詢時，您可以指定的選取準則。</span><span class="sxs-lookup"><span data-stu-id="74f52-143">Variants refer to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="74f52-144">例如，您可以使用變數來指定查詢的預設值。</span><span class="sxs-lookup"><span data-stu-id="74f52-144">For example, you can use variants to specify default values for queries.</span></span>  
  
2.  <span data-ttu-id="74f52-145">您嘗試執行兩者皆非的查詢已定義的變數，也不預期要傳遞的參數值。</span><span class="sxs-lookup"><span data-stu-id="74f52-145">The query you are trying to execute neither has a variant defined nor it expects a parameter value to be passed.</span></span>  
  
 <span data-ttu-id="74f52-146">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="74f52-146">**Resolution**</span></span>  
  
1.  <span data-ttu-id="74f52-147">原因 1 時，請確定您指定與查詢相關聯之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="74f52-147">For reason 1, make sure you specify the name of the variant associated with the query.</span></span> <span data-ttu-id="74f52-148">例如：</span><span class="sxs-lookup"><span data-stu-id="74f52-148">For example:</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant =  ‘variant1’  
    ```  
  
2.  <span data-ttu-id="74f52-149">原因 2，請確定您指定查詢命令的同時提供空的參數名稱和值。</span><span class="sxs-lookup"><span data-stu-id="74f52-149">For reason 2, make sure you provide a dummy parameter name and value while specifying the query command.</span></span> <span data-ttu-id="74f52-150">例如，如果"myquery"查詢不需要執行任何參數，EXECQUERY 命令必須指定為：</span><span class="sxs-lookup"><span data-stu-id="74f52-150">For example, if “myquery” query does not require any parameter to execute, the EXECQUERY command must be specified as:</span></span>  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@P1 = 'dummy_value'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74f52-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74f52-151">See Also</span></span>  
[<span data-ttu-id="74f52-152">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="74f52-152">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)