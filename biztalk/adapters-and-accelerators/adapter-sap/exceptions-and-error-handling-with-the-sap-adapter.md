---
title: 例外狀況和錯誤處理與 SAP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions and error handling
- error handling, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: 598a25c5-6905-4c0c-835b-159d827b2269
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 043f76f7fc730430610b7598bbab208ca8b135a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216846"
---
# <a name="exceptions-and-error-handling-with-the-sap-adapter"></a><span data-ttu-id="0250a-102">例外狀況和錯誤處理與 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="0250a-102">Exceptions and Error Handling with the SAP adapter</span></span>
<span data-ttu-id="0250a-103">會列出例外狀況，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]會擲回。</span><span class="sxs-lookup"><span data-stu-id="0250a-103">Lists the exceptions that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] throws.</span></span> <span data-ttu-id="0250a-104">這些可以包含：</span><span class="sxs-lookup"><span data-stu-id="0250a-104">These can contain:</span></span>  
  
-   <span data-ttu-id="0250a-105">內部例外狀況，也就是.NET Framework 就會擲回系統例外狀況</span><span class="sxs-lookup"><span data-stu-id="0250a-105">An inner exception, which is a system exception that the .NET Framework throws</span></span>  
  
-   <span data-ttu-id="0250a-106">LOB 用戶端程式庫會擲回 LOB 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-106">An LOB exception that the LOB client library throws.</span></span>  
  
 <span data-ttu-id="0250a-107">如需有關內部例外狀況的詳細資訊，請參閱.NET Framework 或 SAP 文件。</span><span class="sxs-lookup"><span data-stu-id="0250a-107">For more information about the inner exception, see the .NET Framework or SAP documentation.</span></span> <span data-ttu-id="0250a-108">例外狀況也會包含可能有助於解決此問題的詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0250a-108">Exceptions also contain a detailed error message that may help resolve the problem.</span></span>  

## <a name="exception-descriptions"></a><span data-ttu-id="0250a-109">例外狀況的描述</span><span class="sxs-lookup"><span data-stu-id="0250a-109">Exception descriptions</span></span>  
|<span data-ttu-id="0250a-110">Exception</span><span class="sxs-lookup"><span data-stu-id="0250a-110">Exception</span></span>|<span data-ttu-id="0250a-111">可能的原因描述</span><span class="sxs-lookup"><span data-stu-id="0250a-111">Possible Cause/Description</span></span>|  
|---------------|---------------------------------|  
|<span data-ttu-id="0250a-112">ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="0250a-112">ObjectDisposedException</span></span>|<span data-ttu-id="0250a-113">配接器用戶端嘗試存取已在處置之後的 XMLReader 的回應時，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-113">The adapter throws this exception when the adapter client is trying to access the response XMLReader after it has been disposed.</span></span>|  
|<span data-ttu-id="0250a-114">XmlReaderGenerationException</span><span class="sxs-lookup"><span data-stu-id="0250a-114">XmlReaderGenerationException</span></span>|<span data-ttu-id="0250a-115">無法從輸出訊息產生 XmlReader 時，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-115">The adapter throws this exception when it is unable to generate an XmlReader from the output message.</span></span> <span data-ttu-id="0250a-116">這也可能是因為從 SAP 系統接收的資料發生一些問題。</span><span class="sxs-lookup"><span data-stu-id="0250a-116">This could also be due to some problems with the data received from the SAP system.</span></span> <span data-ttu-id="0250a-117">查看內部例外狀況和錯誤訊息，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0250a-117">Look for the inner exception and the error message for more information.</span></span>|  
|<span data-ttu-id="0250a-118">InvalidUriException</span><span class="sxs-lookup"><span data-stu-id="0250a-118">InvalidUriException</span></span>|<span data-ttu-id="0250a-119">URI 的連接沒有必要的元件，連接字串時，會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-119">This exception is thrown when the connection URI does not have the required components for the connection string.</span></span>|  
|<span data-ttu-id="0250a-120">ConnectionException</span><span class="sxs-lookup"><span data-stu-id="0250a-120">ConnectionException</span></span>|<span data-ttu-id="0250a-121">當連接到 SAP 系統問題，或是基礎的連接就會變成無效，原因是因為 SAP 系統上發生錯誤，或是因為發生網路問題，則會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-121">This exception is thrown when there is a problem connecting to the SAP system or if an underlying connection becomes invalid, either due to an error on the SAP system or due to a network problem.</span></span>|  
|<span data-ttu-id="0250a-122">「 逾時</span><span class="sxs-lookup"><span data-stu-id="0250a-122">TimeoutException</span></span>|<span data-ttu-id="0250a-123">指定作業的逾時值屆滿時，會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-123">This exception is thrown when the timeout specified for an operation is lapsed.</span></span> <span data-ttu-id="0250a-124">內部例外狀況包含指定的逾時的原因不足夠的細節。</span><span class="sxs-lookup"><span data-stu-id="0250a-124">The inner exception contains the specifics of why the specified timeout was not sufficient.</span></span>|  
|<span data-ttu-id="0250a-125">XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="0250a-125">XmlReaderParsingException</span></span>|<span data-ttu-id="0250a-126">如果不支援指定的型別，或不正確的值指定的類型，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-126">The adapter throws this exception if it does not support the specified type, or if an incorrect value is specified for the type.</span></span> <span data-ttu-id="0250a-127">此外，輸入 XML 可能不正確。</span><span class="sxs-lookup"><span data-stu-id="0250a-127">Also, the input XML could be incorrect.</span></span> <span data-ttu-id="0250a-128">不正確的值包含超出文字或最大的數字的最大數量的情況。</span><span class="sxs-lookup"><span data-stu-id="0250a-128">An incorrect value includes cases where the maximum amount of text or maximum digits is exceeded.</span></span> <span data-ttu-id="0250a-129">輸入 XML 可能不正確的作業名稱或命名空間是否正確。</span><span class="sxs-lookup"><span data-stu-id="0250a-129">The input XML might be incorrect if the operation name or namespace is incorrect.</span></span>|  
|<span data-ttu-id="0250a-130">RFCException （衍生自 AdapterException）</span><span class="sxs-lookup"><span data-stu-id="0250a-130">RFCException (derived from AdapterException)</span></span>|<span data-ttu-id="0250a-131">如果沒有從 SAP 系統接收到錯誤，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-131">The adapter throws this exception if there is an error received from the SAP system.</span></span> <span data-ttu-id="0250a-132">內部例外狀況是實際從 SAP 系統接收到的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-132">The inner exception is the actual exception received from the SAP system.</span></span>|  
|<span data-ttu-id="0250a-133">UnsupportedOperationException</span><span class="sxs-lookup"><span data-stu-id="0250a-133">UnsupportedOperationException</span></span>|<span data-ttu-id="0250a-134">當配接器用戶端指定無效的動作時，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-134">The adapter throws this exception when the adapter client specifies an invalid action.</span></span>|  
|<span data-ttu-id="0250a-135">MetadataException</span><span class="sxs-lookup"><span data-stu-id="0250a-135">MetadataException</span></span>|<span data-ttu-id="0250a-136">如果擷取中繼資料中，瀏覽或搜尋期間發生錯誤，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0250a-136">The adapter throws this exception if there is an error during metadata retrieval, browse, or search.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0250a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0250a-137">See Also</span></span>  
[<span data-ttu-id="0250a-138">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0250a-138">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)