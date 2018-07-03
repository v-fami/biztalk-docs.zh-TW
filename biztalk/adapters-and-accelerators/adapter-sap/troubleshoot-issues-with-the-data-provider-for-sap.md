---
title: 針對適用於 SAP 的資料提供者的問題進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, troubleshooting
- troubleshooting, Data Provider for SAP
ms.assetid: 6fe9baed-0404-4f15-b76e-88cc11c5ff46
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f481a5f71ea5677165390177eb809239961eb9e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018433"
---
# <a name="troubleshoot-issues-with-the-data-provider-for-sap"></a><span data-ttu-id="eb0a7-102">針對適用於 SAP 的資料提供者的問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="eb0a7-102">Troubleshoot Issues with the Data Provider for SAP</span></span>
<span data-ttu-id="eb0a7-103">本節討論如何使用以解決使用時可能遭遇的操作錯誤的疑難排解技巧[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-103">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>  
  
##  <a name="BKMK_SAPUnknownParam"></a> <span data-ttu-id="eb0a7-104">使用適用於 SAP 的資料提供者的未知的參數時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="eb0a7-104">Unknown Parameter error using the Data Provider for SAP</span></span>  
 <span data-ttu-id="eb0a7-105">**問題**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-105">**Problem**</span></span>  
  
 <span data-ttu-id="eb0a7-106">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-106">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] gives the following error:</span></span>  
  
```  
Microsoft.Data.SAPClient.SAPException: Failed to retrieve data from SAP server --- > Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Unknown Parameter OUT_ZDATATABLE.  
```  
  
 <span data-ttu-id="eb0a7-107">**原因**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-107">**Cause**</span></span>  
  
 <span data-ttu-id="eb0a7-108">不是最新的自訂 RFC、 Z_EXTRACT_DATA_OO，安裝在您的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-108">The custom RFC, Z_EXTRACT_DATA_OO, installed in your SAP system is not the latest.</span></span> <span data-ttu-id="eb0a7-109">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用的自訂 RFC Z_EXTRACT_DATA_OO，執行 SAP 資料表上的 SELECT 作業。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-109">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC, Z_EXTRACT_DATA_OO, to perform SELECT operations on the SAP table.</span></span>  
  
 <span data-ttu-id="eb0a7-110">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-110">**Resolution**</span></span>  
  
 <span data-ttu-id="eb0a7-111">您必須更新自訂 RFC 為最新可用版本。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-111">You must update the custom RFC to the latest available version.</span></span> <span data-ttu-id="eb0a7-112">這個 RFC、 Z_EXTRACT_DATA_OO，適用於 adapterpacknoversion。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-112">This RFC, Z_EXTRACT_DATA_OO, is available with the adapterpacknoversion.</span></span> <span data-ttu-id="eb0a7-113">如需如何安裝和解除安裝自訂 RFC 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-113">For more information about how to install and uninstall the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>
  
##  <a name="BKMK_SAPOOM"></a> <span data-ttu-id="eb0a7-114">記憶體不足例外狀況從 SAP 資料表選取資料時</span><span class="sxs-lookup"><span data-stu-id="eb0a7-114">Out of memory exceptions when selecting data from an SAP table</span></span>  
 <span data-ttu-id="eb0a7-115">**問題**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-115">**Problem**</span></span>  
  
 <span data-ttu-id="eb0a7-116">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] SAP 系統從選取的資料時，會擲回記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-116">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] throws an out of memory exception when selecting data from an SAP system.</span></span>  
  
 <span data-ttu-id="eb0a7-117">**原因**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-117">**Cause**</span></span>  
  
 <span data-ttu-id="eb0a7-118">根據預設，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]擷取 10,000 個資料列一次。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-118">By default, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retrieves 10,000 rows at a time.</span></span> <span data-ttu-id="eb0a7-119">此外，每個 SAP 系統從擷取的資料列的批次會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-119">Also, each batch of rows retrieved from the SAP system is stored in the memory.</span></span> <span data-ttu-id="eb0a7-120">因此，</span><span class="sxs-lookup"><span data-stu-id="eb0a7-120">So,</span></span>  
  
- <span data-ttu-id="eb0a7-121">如果從中擷取資料的資料表包含大量資料列，或</span><span class="sxs-lookup"><span data-stu-id="eb0a7-121">If the table from which data is being retrieved contains a large number of rows, or</span></span>  
  
- <span data-ttu-id="eb0a7-122">如果資料表包含會耗用大量記憶體的資料類型的資料行</span><span class="sxs-lookup"><span data-stu-id="eb0a7-122">If the table contains columns of data types that consume a significant amount of memory,</span></span>  
  
  <span data-ttu-id="eb0a7-123">記憶體耗用量[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]大幅增加，可能會導致記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-123">The memory consumption by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] increases significantly and may result in an out of memory exception.</span></span>  
  
  <span data-ttu-id="eb0a7-124">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-124">**Resolution**</span></span>  
  
  <span data-ttu-id="eb0a7-125">您可以變更 SAP 系統從擷取的資料列數目上限。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-125">You can change the maximum number of rows retrieved from the SAP system.</span></span> <span data-ttu-id="eb0a7-126">您可以藉由指定 SELECT 陳述式的 'batchsize' 選項來這麼做。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-126">You can do so by specifying a 'batchsize' option with the SELECT statement.</span></span> <span data-ttu-id="eb0a7-127">例如：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-127">For example:</span></span>  
  
```  
SELECT * FROM <tablename> OPTION 'batchsize 1000'  
```  
  
 <span data-ttu-id="eb0a7-128">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]現在會只 1000 個資料列擷取一次，因此不會耗用大量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-128">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] now retrieves only 1000 rows at a time and hence does not consume large amount of memory.</span></span>  
  
##  <a name="BKMK_SAPQueryExcep"></a> <span data-ttu-id="eb0a7-129">執行查詢： 接受具有日期值的參數時發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="eb0a7-129">Exception while executing a query that takes parameters with date values</span></span>  
 <span data-ttu-id="eb0a7-130">**問題**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-130">**Problem**</span></span>  
  
 <span data-ttu-id="eb0a7-131">當您執行查詢，使用 EXECQUERY 命令可接受的日期值的參數時，您會取得下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-131">You get the following exception when you execute a query using the EXECQUERY command that has a parameter which takes a date value:</span></span>  
  
```  
ErrorCode=RFC_SYS_EXCEPTION. ErrorGroup=RFC_ERROR_SYSTEM_FAILURE.   
SapErrorMessage=Enter date in the format __.__.____.  
```  
  
 <span data-ttu-id="eb0a7-132">**原因**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-132">**Cause**</span></span>  
  
 <span data-ttu-id="eb0a7-133">執行時使用 EXECQUERY 命令的查詢，您一律必須以 YYYYMMDD 格式來指定日期值。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-133">When executing queries using the EXECQUERY command, you must always specify date values in YYYYMMDD format.</span></span>  
  
 <span data-ttu-id="eb0a7-134">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-134">**Resolution**</span></span>  
  
 <span data-ttu-id="eb0a7-135">請確定您指定日期值格式為 YYYYMMDD。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-135">Make sure you specify date values in YYYYMMDD format.</span></span> <span data-ttu-id="eb0a7-136">例如：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-136">For example:</span></span>  
  
```  
EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1='20080606'  
```  
  
##  <a name="BKMK_SAPNOVARIANT"></a> <span data-ttu-id="eb0a7-137">執行查詢使用 EXECQUERY 命令 NO_VARIANT 例外狀況</span><span class="sxs-lookup"><span data-stu-id="eb0a7-137">NO_VARIANT exception executing queries using the EXECQUERY command</span></span>  
 <span data-ttu-id="eb0a7-138">**問題**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-138">**Problem**</span></span>  
  
 <span data-ttu-id="eb0a7-139">當您執行查詢，使用 EXECQUERY 命令時，您就會收到下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-139">You get the following exception when you execute a query using the EXECQUERY command:</span></span>  
  
```  
Exception: Details: ErrorCode=RFC_EXCEPTION. ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage=NO_VARIANT.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: <RFC name>  
```  
  
 <span data-ttu-id="eb0a7-140">**原因**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-140">**Cause**</span></span>  
  
 <span data-ttu-id="eb0a7-141">可以有兩個可能的原因，這個例外狀況：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-141">There can be two probable causes for this exception:</span></span>  
  
1. <span data-ttu-id="eb0a7-142">您嘗試執行的查詢的 SAP 系統中定義的變數。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-142">The query you are trying to execute has variants defined in the SAP system.</span></span> <span data-ttu-id="eb0a7-143">變化是指一組儲存執行 SAP 查詢時，您可以指定的選取準則。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-143">Variants refer to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="eb0a7-144">比方說，您可以使用變數來指定查詢的預設值。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-144">For example, you can use variants to specify default values for queries.</span></span>  
  
2. <span data-ttu-id="eb0a7-145">您嘗試執行未查詢的變數定義也預期要傳遞的參數值。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-145">The query you are trying to execute neither has a variant defined nor it expects a parameter value to be passed.</span></span>  
  
   <span data-ttu-id="eb0a7-146">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="eb0a7-146">**Resolution**</span></span>  
  
3. <span data-ttu-id="eb0a7-147">基於為 1 時，請確定您指定與查詢相關聯之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-147">For reason 1, make sure you specify the name of the variant associated with the query.</span></span> <span data-ttu-id="eb0a7-148">例如：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-148">For example:</span></span>  
  
   ```  
   EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant =  ‘variant1’  
   ```  
  
4. <span data-ttu-id="eb0a7-149">基於為 2 時，請確定您指定查詢命令時提供空的參數名稱和值。</span><span class="sxs-lookup"><span data-stu-id="eb0a7-149">For reason 2, make sure you provide a dummy parameter name and value while specifying the query command.</span></span> <span data-ttu-id="eb0a7-150">例如，"myquery 」 查詢不需要任何參數來執行，如果 EXECQUERY 命令必須指定為：</span><span class="sxs-lookup"><span data-stu-id="eb0a7-150">For example, if “myquery” query does not require any parameter to execute, the EXECQUERY command must be specified as:</span></span>  
  
   ```  
   EXECQUERY myquery @usergroup='mygroup',@P1 = 'dummy_value'  
   ```  
  
## <a name="see-also"></a><span data-ttu-id="eb0a7-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb0a7-151">See Also</span></span>  
[<span data-ttu-id="eb0a7-152">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="eb0a7-152">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)