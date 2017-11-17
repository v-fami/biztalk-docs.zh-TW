---
title: "SAP 配接器範例 |Microsoft 文件"
description: "可以搭配 BizTalk Server、 WCF 服務模型中，WCF 通道模型和資料提供者適用於 SAP mySAP WCF 配接器範例"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d163c573003f40b2049f7e921e5edc4997b4e115
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-sap-adapter"></a><span data-ttu-id="a86c5-103">適用於 SAP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-103">Samples for the SAP adapter</span></span>
<span data-ttu-id="a86c5-104">範例如[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]分類成：</span><span class="sxs-lookup"><span data-stu-id="a86c5-104">Samples for [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] are categorized into:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a86c5-105"> 範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-105"> samples</span></span>  
  
-   <span data-ttu-id="a86c5-106">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-106">WCF service model samples</span></span>  
  
-   <span data-ttu-id="a86c5-107">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-107">WCF channel model samples</span></span>  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="a86c5-108"> 範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-108"> samples</span></span>  

  
 <span data-ttu-id="a86c5-109">這些範例位於[BizTalk Adapter Pack 2010: SAP 配接器範例](https://www.microsoft.com/download/details.aspx?id=1314)。</span><span class="sxs-lookup"><span data-stu-id="a86c5-109">The samples are available at [BizTalk Adapter Pack 2010: SAP adapter samples](https://www.microsoft.com/download/details.aspx?id=1314).</span></span> 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
 <span data-ttu-id="a86c5-110">下列清單描述的範例。</span><span class="sxs-lookup"><span data-stu-id="a86c5-110">The following list describes the samples.</span></span>
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="a86c5-111">BizTalk Server 範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-111">BizTalk Server samples</span></span>  
  
|<span data-ttu-id="a86c5-112">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="a86c5-112">Sample Directory Name</span></span>|<span data-ttu-id="a86c5-113">Description</span><span class="sxs-lookup"><span data-stu-id="a86c5-113">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="a86c5-114">IDOCSend</span><span class="sxs-lookup"><span data-stu-id="a86c5-114">IDOCSend</span></span>|<span data-ttu-id="a86c5-115">示範如何傳送 IDOC 至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="a86c5-115">Demonstrates how to send an IDOC to an SAP system.</span></span>|  
|<span data-ttu-id="a86c5-116">ReceiveIDOC</span><span class="sxs-lookup"><span data-stu-id="a86c5-116">ReceiveIDOC</span></span>|<span data-ttu-id="a86c5-117">示範如何從 SAP 系統接收 IDOC。</span><span class="sxs-lookup"><span data-stu-id="a86c5-117">Demonstrates how to receive an IDOC from an SAP system.</span></span>|  
|<span data-ttu-id="a86c5-118">ReceiveIDOC_SYSREL</span><span class="sxs-lookup"><span data-stu-id="a86c5-118">ReceiveIDOC_SYSREL</span></span>|<span data-ttu-id="a86c5-119">示範如何從 SAP 系統接收 IDOC。</span><span class="sxs-lookup"><span data-stu-id="a86c5-119">Demonstrates how to receive an IDOC from an SAP system.</span></span> <span data-ttu-id="a86c5-120">正在接收的 IDOC 具有小於 SAP SYSREL 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a86c5-120">The IDOC being received has the version number less than the SAP SYSREL.</span></span>|  
|<span data-ttu-id="a86c5-121">RFCServer</span><span class="sxs-lookup"><span data-stu-id="a86c5-121">RFCServer</span></span>|<span data-ttu-id="a86c5-122">示範如何從 SAP 系統接收的 RFC 伺服器呼叫。</span><span class="sxs-lookup"><span data-stu-id="a86c5-122">Demonstrates how to receive an RFC server call from the SAP system.</span></span>|  
|<span data-ttu-id="a86c5-123">SAPTransaction</span><span class="sxs-lookup"><span data-stu-id="a86c5-123">SAPTransaction</span></span>|<span data-ttu-id="a86c5-124">示範如何執行 SAP 系統使用的交易。</span><span class="sxs-lookup"><span data-stu-id="a86c5-124">Demonstrates how to perform transactions in an SAP system using.</span></span>|  
|<span data-ttu-id="a86c5-125">tRFCClient</span><span class="sxs-lookup"><span data-stu-id="a86c5-125">tRFCClient</span></span>|<span data-ttu-id="a86c5-126">示範如何在 SAP 系統上進行 tRFC 用戶端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a86c5-126">Demonstrates how to make tRFC client calls on an SAP system.</span></span>|  
  
## <a name="wcf-service-model-samples"></a><span data-ttu-id="a86c5-127">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-127">WCF service model samples</span></span>   
  
|<span data-ttu-id="a86c5-128">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="a86c5-128">Sample Directory Name</span></span>|<span data-ttu-id="a86c5-129">Description</span><span class="sxs-lookup"><span data-stu-id="a86c5-129">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="a86c5-130">SapIdocStringClientSM</span><span class="sxs-lookup"><span data-stu-id="a86c5-130">SapIdocStringClientSM</span></span>|<span data-ttu-id="a86c5-131">示範如何叫用 SendIdoc 作業傳送 IDOC 到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="a86c5-131">Demonstrates how to send an IDOC to an SAP system by invoking the SendIdoc operation.</span></span>|  
|<span data-ttu-id="a86c5-132">SapRfcServerSM</span><span class="sxs-lookup"><span data-stu-id="a86c5-132">SapRfcServerSM</span></span>|<span data-ttu-id="a86c5-133">示範如何從 SAP 系統接收的 RFC 伺服器呼叫。</span><span class="sxs-lookup"><span data-stu-id="a86c5-133">Demonstrates how to receive an RFC server call from an SAP system.</span></span>|  
|<span data-ttu-id="a86c5-134">SapBapiTxClientSM</span><span class="sxs-lookup"><span data-stu-id="a86c5-134">SapBapiTxClientSM</span></span>|<span data-ttu-id="a86c5-135">示範如何在 SAP 系統上的交易內叫用的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="a86c5-135">Demonstrates how to invoke BAPIs inside a transaction on an SAP system.</span></span>|  
|<span data-ttu-id="a86c5-136">SapTrfcClientSM</span><span class="sxs-lookup"><span data-stu-id="a86c5-136">SapTrfcClientSM</span></span>|<span data-ttu-id="a86c5-137">示範如何叫用對 SAP 系統進行 tRFC 用戶端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a86c5-137">Demonstrates how to invoke tRFC client calls on an SAP system.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="a86c5-138">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="a86c5-138">WCF channel model samples</span></span>  
  
|<span data-ttu-id="a86c5-139">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="a86c5-139">Sample Directory Name</span></span>|<span data-ttu-id="a86c5-140">Description</span><span class="sxs-lookup"><span data-stu-id="a86c5-140">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="a86c5-141">SapIdocReceiveCM</span><span class="sxs-lookup"><span data-stu-id="a86c5-141">SapIdocReceiveCM</span></span>|<span data-ttu-id="a86c5-142">示範如何從 SAP 系統接收 Idoc</span><span class="sxs-lookup"><span data-stu-id="a86c5-142">Demonstrates how to receive IDOCs from an SAP system</span></span>|  
|<span data-ttu-id="a86c5-143">SapRfcServerCM</span><span class="sxs-lookup"><span data-stu-id="a86c5-143">SapRfcServerCM</span></span>|<span data-ttu-id="a86c5-144">示範如何從 SAP 系統接收的 RFC 伺服器呼叫。</span><span class="sxs-lookup"><span data-stu-id="a86c5-144">Demonstrates how to receive an RFC server call from the SAP system.</span></span>|  
  
## <a name="data-provider-for-sap-samples"></a><span data-ttu-id="a86c5-145">如需 SAP 範例的資料提供者</span><span class="sxs-lookup"><span data-stu-id="a86c5-145">Data Provider for SAP samples</span></span>  
  
|<span data-ttu-id="a86c5-146">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="a86c5-146">Sample Directory Name</span></span>|<span data-ttu-id="a86c5-147">Description</span><span class="sxs-lookup"><span data-stu-id="a86c5-147">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="a86c5-148">sap ado</span><span class="sxs-lookup"><span data-stu-id="a86c5-148">sap ado</span></span>|<span data-ttu-id="a86c5-149">示範如何使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a86c5-149">Demonstrates how to use the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>|  
  
 
## <a name="see-also"></a><span data-ttu-id="a86c5-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a86c5-150">See Also</span></span>  
[<span data-ttu-id="a86c5-151">開發您的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="a86c5-151">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)