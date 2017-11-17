---
title: "Oracle EBS 配接器範例 |Microsoft 文件"
description: "可以使用 BizTalk Server、 WCF 服務模型時，與 WCF 通道模型的 oracle Enterprise Business Suite WCF 配接器範例"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12f19f13-3b01-40d6-b12c-811f99841040
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4069b7f5916291544ce76534e04b20af5680d69
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-oracle-ebs-adapter"></a><span data-ttu-id="4abdd-103">適用於 Oracle EBS 配接器範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-103">Samples for the Oracle EBS adapter</span></span>
<span data-ttu-id="4abdd-104">範例如[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]分類成：</span><span class="sxs-lookup"><span data-stu-id="4abdd-104">Samples for [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] are categorized into:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4abdd-105"> 範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-105"> samples</span></span>  
  
-   <span data-ttu-id="4abdd-106">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-106">WCF service model samples</span></span>  
  
-   <span data-ttu-id="4abdd-107">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-107">WCF channel model samples</span></span>  
  
-   <span data-ttu-id="4abdd-108">Microsoft Office SharePoint Server 範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-108">Microsoft Office SharePoint Server samples</span></span>  
  
 <span data-ttu-id="4abdd-109">這些範例位於[BizTalk Adapter Pack 2010: Oracle E-business Suite 配接器範例](https://www.microsoft.com/download/details.aspx?id=6464)。</span><span class="sxs-lookup"><span data-stu-id="4abdd-109">The samples are available at [BizTalk Adapter Pack 2010: Oracle E-Business Suite adapter samples](https://www.microsoft.com/download/details.aspx?id=6464).</span></span> <span data-ttu-id="4abdd-110">建立介面資料表、 同時執行的程式、 資料表和封裝範例中所使用的 SQL 指令碼會包含項目。</span><span class="sxs-lookup"><span data-stu-id="4abdd-110">The SQL scripts for creating the interface tables, concurrent programs, tables, and packages used in the samples are included.</span></span> 
  
> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
 <span data-ttu-id="4abdd-111">下列清單描述的範例。</span><span class="sxs-lookup"><span data-stu-id="4abdd-111">The following list describes the samples.</span></span> 
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="4abdd-112">BizTalk Server 範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-112">BizTalk Server samples</span></span>  
  
|<span data-ttu-id="4abdd-113">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="4abdd-113">Sample Directory Name</span></span>|<span data-ttu-id="4abdd-114">Description</span><span class="sxs-lookup"><span data-stu-id="4abdd-114">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4abdd-115">InterfaceTableInsert</span><span class="sxs-lookup"><span data-stu-id="4abdd-115">InterfaceTableInsert</span></span>|<span data-ttu-id="4abdd-116">示範如何將記錄插入介面資料表中使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-116">Demonstrates how to insert records into an interface table in Oracle E-Business Suite using [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-117">ConcurrentProgram</span><span class="sxs-lookup"><span data-stu-id="4abdd-117">ConcurrentProgram</span></span>|<span data-ttu-id="4abdd-118">示範如何叫用中使用 Oracle E-business Suite 的並行程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-118">Demonstrates how to invoke a concurrent program in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-119">RequestSet</span><span class="sxs-lookup"><span data-stu-id="4abdd-119">RequestSet</span></span>|<span data-ttu-id="4abdd-120">示範如何叫用要求中使用 Oracle E-business Suite 設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-120">Demonstrates how to invoke a request set in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-121">MsgContextProperty</span><span class="sxs-lookup"><span data-stu-id="4abdd-121">MsgContextProperty</span></span>|<span data-ttu-id="4abdd-122">示範如何使用訊息內容屬性所公開[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來設定要在使用 Oracle E-business Suite 成品上執行作業的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-122">Demonstrates how to use the message context properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to set application context to perform operations on artifacts in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-123">OracleEBS_CompositeOperation</span><span class="sxs-lookup"><span data-stu-id="4abdd-123">OracleEBS_CompositeOperation</span></span>|<span data-ttu-id="4abdd-124">示範如何執行複合操作中使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-124">Demonstrates how to perform composite operations in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-125">OracleNotifyIncremental</span><span class="sxs-lookup"><span data-stu-id="4abdd-125">OracleNotifyIncremental</span></span>|<span data-ttu-id="4abdd-126">示範如何使用 Oracle 時，收到 「 增量 」 的查詢通知訊息[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-126">Demonstrates how to receive “incremental” query notification messages from Oracle using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-127">PollingUsingSelectStatement</span><span class="sxs-lookup"><span data-stu-id="4abdd-127">PollingUsingSelectStatement</span></span>|<span data-ttu-id="4abdd-128">示範如何設定使用 SELECT 陳述式在有輪詢查詢，並接收結果使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-128">Demonstrates how to configure a polling query using a SELECT statement and receive the results using the   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
|<span data-ttu-id="4abdd-129">PollingUsingStoredProc</span><span class="sxs-lookup"><span data-stu-id="4abdd-129">PollingUsingStoredProc</span></span>|<span data-ttu-id="4abdd-130">示範如何設定使用預存程序在有輪詢查詢，並接收結果使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4abdd-130">Demonstrates how to configure a polling query using a stored procedure and receive the results using the   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>|  
  
## <a name="wcf-service-model-sasamplesmples"></a><span data-ttu-id="4abdd-131">WCF 服務模型 Sasamplesmples</span><span class="sxs-lookup"><span data-stu-id="4abdd-131">WCF Service model Sasamplesmples</span></span>  
  
|<span data-ttu-id="4abdd-132">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="4abdd-132">Sample Directory Name</span></span>|<span data-ttu-id="4abdd-133">Description</span><span class="sxs-lookup"><span data-stu-id="4abdd-133">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4abdd-134">ConcProgram_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4abdd-134">ConcProgram_ServiceModel</span></span>|<span data-ttu-id="4abdd-135">示範如何叫用使用配接器的 Oracle E-business Suite 中的並行程式。</span><span class="sxs-lookup"><span data-stu-id="4abdd-135">Demonstrates how to invoke concurrent programs in Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-136">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="4abdd-136">ExecuteReader</span></span>|<span data-ttu-id="4abdd-137">示範如何叫用 ExecuteReader 作業上使用配接器的 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="4abdd-137">Demonstrates how to invoke an ExecuteReader operation on Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-138">Interface_Table_Ops</span><span class="sxs-lookup"><span data-stu-id="4abdd-138">Interface_Table_Ops</span></span>|<span data-ttu-id="4abdd-139">示範如何在 Oracle E-business Suite 使用配接器介面資料表上執行作業。</span><span class="sxs-lookup"><span data-stu-id="4abdd-139">Demonstrates how to perform operations on interface tables in Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-140">LargeDataTypes_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4abdd-140">LargeDataTypes_ServiceModel</span></span>|<span data-ttu-id="4abdd-141">示範如何在 Oracle E-business Suite 使用配接器具有大型資料類型的資料行的資料表上執行作業。</span><span class="sxs-lookup"><span data-stu-id="4abdd-141">Demonstrates how to perform operations on tables with columns of large data types in Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-142">Notification_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4abdd-142">Notification_ServiceModel</span></span>|<span data-ttu-id="4abdd-143">示範如何從資料庫後使用配接器的 Oracle E-business Suite 接收通知。</span><span class="sxs-lookup"><span data-stu-id="4abdd-143">Demonstrates how to receive notifications from databases behind Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-144">SelectPolling_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4abdd-144">SelectPolling_ServiceModel</span></span>|<span data-ttu-id="4abdd-145">示範如何使用輪詢使用配接器的 Oracle E-business Suite 中的介面資料表的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4abdd-145">Demonstrates how to use a SELECT statement to poll an interface table in Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-146">StoredProcPolling_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4abdd-146">StoredProcPolling_ServiceModel</span></span>|<span data-ttu-id="4abdd-147">示範如何使用預存程序來輪詢使用配接器的 Oracle E-business Suite 中的資料表。</span><span class="sxs-lookup"><span data-stu-id="4abdd-147">Demonstrates how to use a stored procedure to poll tables in Oracle E-Business Suite using the adapter.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="4abdd-148">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-148">WCF Channel model samples</span></span>  
  
|<span data-ttu-id="4abdd-149">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="4abdd-149">Sample Directory Name</span></span>|<span data-ttu-id="4abdd-150">Description</span><span class="sxs-lookup"><span data-stu-id="4abdd-150">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4abdd-151">InsertOperation</span><span class="sxs-lookup"><span data-stu-id="4abdd-151">InsertOperation</span></span>|<span data-ttu-id="4abdd-152">示範如何使用配接器的 Oracle E-business Suite 中執行插入作業介面資料表上。</span><span class="sxs-lookup"><span data-stu-id="4abdd-152">Demonstrates how to perform an Insert operation on an interface table in Oracle E-Business Suite using the adapter.</span></span>|  
|<span data-ttu-id="4abdd-153">SelectPolling_ChannelModel</span><span class="sxs-lookup"><span data-stu-id="4abdd-153">SelectPolling_ChannelModel</span></span>|<span data-ttu-id="4abdd-154">示範如何使用輪詢使用配接器的 Oracle E-business Suite 中的介面資料表的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4abdd-154">Demonstrates how to use a SELECT statement to poll an interface table in Oracle E-Business Suite using the adapter.</span></span>|  
  
## <a name="microsoft-office-sharepoint-server-samples"></a><span data-ttu-id="4abdd-155">Microsoft Office SharePoint Server 範例</span><span class="sxs-lookup"><span data-stu-id="4abdd-155">Microsoft Office SharePoint Server samples</span></span>  
  
|<span data-ttu-id="4abdd-156">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="4abdd-156">Sample Directory Name</span></span>|<span data-ttu-id="4abdd-157">Description</span><span class="sxs-lookup"><span data-stu-id="4abdd-157">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4abdd-158">MOSS_Sample</span><span class="sxs-lookup"><span data-stu-id="4abdd-158">MOSS_Sample</span></span>|<span data-ttu-id="4abdd-159">示範如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]Oracle E-business Suite 成品從建立 Windows Communication Foundation (WCF) 服務，然後使用 Microsoft Office SharePoint Server 使用商務資料清單網頁組件中顯示資料的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4abdd-159">Demonstrates how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to create a Windows Communication Foundation (WCF) service from Oracle E-Business Suite artifacts, and then use the WCF service to display data in Microsoft Office SharePoint Server using a Business Data List Web Part.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4abdd-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4abdd-160">See Also</span></span>  
[<span data-ttu-id="4abdd-161">開發 Oracle E-business Suite 應用程式</span><span class="sxs-lookup"><span data-stu-id="4abdd-161">Develop your Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)