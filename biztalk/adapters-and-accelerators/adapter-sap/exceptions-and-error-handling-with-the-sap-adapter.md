---
title: 例外狀況和錯誤處理與 SAP 配接器 |Microsoft Docs
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
ms.openlocfilehash: 5439ae9cc58dfbb649fefd7ae3f18348502bcd48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991623"
---
# <a name="exceptions-and-error-handling-with-the-sap-adapter"></a><span data-ttu-id="1f6d6-102">例外狀況和錯誤處理與 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="1f6d6-102">Exceptions and Error Handling with the SAP adapter</span></span>
<span data-ttu-id="1f6d6-103">會列出例外狀況，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]會擲回。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-103">Lists the exceptions that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] throws.</span></span> <span data-ttu-id="1f6d6-104">其中可包含：</span><span class="sxs-lookup"><span data-stu-id="1f6d6-104">These can contain:</span></span>  

- <span data-ttu-id="1f6d6-105">內部例外狀況，也就是.NET Framework 會擲回系統例外狀況</span><span class="sxs-lookup"><span data-stu-id="1f6d6-105">An inner exception, which is a system exception that the .NET Framework throws</span></span>  

- <span data-ttu-id="1f6d6-106">LOB 用戶端程式庫會擲回 LOB 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-106">An LOB exception that the LOB client library throws.</span></span>  

  <span data-ttu-id="1f6d6-107">如需有關內部例外狀況的詳細資訊，請參閱.NET Framework 或 SAP 文件。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-107">For more information about the inner exception, see the .NET Framework or SAP documentation.</span></span> <span data-ttu-id="1f6d6-108">例外狀況也會包含詳細的錯誤訊息，可能有助於解決此問題。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-108">Exceptions also contain a detailed error message that may help resolve the problem.</span></span>  

## <a name="exception-descriptions"></a><span data-ttu-id="1f6d6-109">例外狀況描述</span><span class="sxs-lookup"><span data-stu-id="1f6d6-109">Exception descriptions</span></span>  

|<span data-ttu-id="1f6d6-110">例外狀況</span><span class="sxs-lookup"><span data-stu-id="1f6d6-110">Exception</span></span>|<span data-ttu-id="1f6d6-111">可能的原因描述</span><span class="sxs-lookup"><span data-stu-id="1f6d6-111">Possible Cause/Description</span></span>|  
|---------------|---------------------------------|  
|<span data-ttu-id="1f6d6-112">ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-112">ObjectDisposedException</span></span>|<span data-ttu-id="1f6d6-113">當配接器用戶端嘗試存取 XMLReader 的回應，已在處置之後，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-113">The adapter throws this exception when the adapter client is trying to access the response XMLReader after it has been disposed.</span></span>|  
|<span data-ttu-id="1f6d6-114">XmlReaderGenerationException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-114">XmlReaderGenerationException</span></span>|<span data-ttu-id="1f6d6-115">無法從輸出訊息產生 XmlReader 時，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-115">The adapter throws this exception when it is unable to generate an XmlReader from the output message.</span></span> <span data-ttu-id="1f6d6-116">這也可能是因為 SAP 系統從收到的資料有一些問題。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-116">This could also be due to some problems with the data received from the SAP system.</span></span> <span data-ttu-id="1f6d6-117">查看內部例外狀況和錯誤訊息，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-117">Look for the inner exception and the error message for more information.</span></span>|  
|<span data-ttu-id="1f6d6-118">InvalidUriException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-118">InvalidUriException</span></span>|<span data-ttu-id="1f6d6-119">當連線 URI 沒有連接字串所需的元件時，會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-119">This exception is thrown when the connection URI does not have the required components for the connection string.</span></span>|  
|<span data-ttu-id="1f6d6-120">ConnectionException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-120">ConnectionException</span></span>|<span data-ttu-id="1f6d6-121">無法連接至 SAP 系統時，或基礎的連接就會變成無效，原因是因為 SAP 系統上發生錯誤，或是因為發生網路問題，則會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-121">This exception is thrown when there is a problem connecting to the SAP system or if an underlying connection becomes invalid, either due to an error on the SAP system or due to a network problem.</span></span>|  
|<span data-ttu-id="1f6d6-122">TimeoutException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-122">TimeoutException</span></span>|<span data-ttu-id="1f6d6-123">指定作業的逾時值失效時，會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-123">This exception is thrown when the timeout specified for an operation is lapsed.</span></span> <span data-ttu-id="1f6d6-124">內部例外狀況包含的細節為何指定的逾時已不足夠。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-124">The inner exception contains the specifics of why the specified timeout was not sufficient.</span></span>|  
|<span data-ttu-id="1f6d6-125">XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-125">XmlReaderParsingException</span></span>|<span data-ttu-id="1f6d6-126">如果它不支援指定的型別，或不正確的值指定的類型，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-126">The adapter throws this exception if it does not support the specified type, or if an incorrect value is specified for the type.</span></span> <span data-ttu-id="1f6d6-127">此外，可能不正確的輸入 XML。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-127">Also, the input XML could be incorrect.</span></span> <span data-ttu-id="1f6d6-128">不正確的值包括超出文字或最大的數字的最大數量的案例。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-128">An incorrect value includes cases where the maximum amount of text or maximum digits is exceeded.</span></span> <span data-ttu-id="1f6d6-129">輸入 XML 可能不正確的作業名稱或命名空間是否正確。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-129">The input XML might be incorrect if the operation name or namespace is incorrect.</span></span>|  
|<span data-ttu-id="1f6d6-130">RFCException （衍生自 AdapterException）</span><span class="sxs-lookup"><span data-stu-id="1f6d6-130">RFCException (derived from AdapterException)</span></span>|<span data-ttu-id="1f6d6-131">如果沒有從 SAP 系統接收到錯誤，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-131">The adapter throws this exception if there is an error received from the SAP system.</span></span> <span data-ttu-id="1f6d6-132">內部例外狀況是從 SAP 系統接收到實際的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-132">The inner exception is the actual exception received from the SAP system.</span></span>|  
|<span data-ttu-id="1f6d6-133">UnsupportedOperationException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-133">UnsupportedOperationException</span></span>|<span data-ttu-id="1f6d6-134">當配接器用戶端指定了無效的動作時，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-134">The adapter throws this exception when the adapter client specifies an invalid action.</span></span>|  
|<span data-ttu-id="1f6d6-135">MetadataException</span><span class="sxs-lookup"><span data-stu-id="1f6d6-135">MetadataException</span></span>|<span data-ttu-id="1f6d6-136">如果中繼資料擷取、 瀏覽或搜尋期間發生錯誤，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-136">The adapter throws this exception if there is an error during metadata retrieval, browse, or search.</span></span>|  

## <a name="see-also"></a><span data-ttu-id="1f6d6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f6d6-137">See Also</span></span>  
[<span data-ttu-id="1f6d6-138">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1f6d6-138">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)