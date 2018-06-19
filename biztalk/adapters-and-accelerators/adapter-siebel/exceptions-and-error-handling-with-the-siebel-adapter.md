---
title: 例外狀況和錯誤處理 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error handling, troubleshooting
- exceptions, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: d46e908f-0715-43e2-879b-f5d0beb9bc64
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 743e2a0f03e35282c24a506ff37e9d774f0b7505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221862"
---
# <a name="exceptions-and-error-handling-with-the-siebel-adapter"></a><span data-ttu-id="ac113-102">例外狀況和錯誤處理 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="ac113-102">Exceptions and Error Handling with the Siebel adapter</span></span>
## <a name="exception-list"></a><span data-ttu-id="ac113-103">例外狀況清單</span><span class="sxs-lookup"><span data-stu-id="ac113-103">Exception list</span></span>
<span data-ttu-id="ac113-104">所擲回的例外狀況[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac113-104">The exceptions thrown by the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span> <span data-ttu-id="ac113-105">這些可以包含：</span><span class="sxs-lookup"><span data-stu-id="ac113-105">These can contain:</span></span>  
  
-   <span data-ttu-id="ac113-106">內部例外狀況，也就是.NET Framework 就會擲回系統例外狀況</span><span class="sxs-lookup"><span data-stu-id="ac113-106">An inner exception, which is a system exception that the .NET Framework throws</span></span>  
  
-   <span data-ttu-id="ac113-107">LOB 用戶端程式庫會擲回 LOB 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-107">An LOB exception that the LOB client library throws.</span></span>  
  
 <span data-ttu-id="ac113-108">如需有關內部例外狀況的詳細資訊，請參閱個別的.NET Framework 或 Siebel 文件。</span><span class="sxs-lookup"><span data-stu-id="ac113-108">For more information about the inner exception, refer to the respective .NET Framework or Siebel documentation.</span></span> <span data-ttu-id="ac113-109">例外狀況還包含詳細的錯誤訊息，可協助解決問題。</span><span class="sxs-lookup"><span data-stu-id="ac113-109">The exception also contains a detailed error message that helps in resolving the problem.</span></span> <span data-ttu-id="ac113-110">請注意，此處提到的例外狀況的清單並不完整。</span><span class="sxs-lookup"><span data-stu-id="ac113-110">Note that the list of exceptions mentioned here is not comprehensive.</span></span>  
  
|<span data-ttu-id="ac113-111">Exception</span><span class="sxs-lookup"><span data-stu-id="ac113-111">Exception</span></span>|<span data-ttu-id="ac113-112">可能的原因/錯誤描述</span><span class="sxs-lookup"><span data-stu-id="ac113-112">Possible Cause/Error Description</span></span>|  
|---------------|---------------------------------------|  
|<span data-ttu-id="ac113-113">ConnectionException</span><span class="sxs-lookup"><span data-stu-id="ac113-113">ConnectionException</span></span>|<span data-ttu-id="ac113-114">如果無法建立連線，或關閉現有的連接至 Siebel 系統的配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-114">The adapter throws this exception if it is unable to establish a connection or close an existing connection to a Siebel system.</span></span>|  
|<span data-ttu-id="ac113-115">CredentialsException</span><span class="sxs-lookup"><span data-stu-id="ac113-115">CredentialsException</span></span>|<span data-ttu-id="ac113-116">如果配接器用戶端未指定使用者名稱或密碼來連接至 Siebel 系統的配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-116">The adapter throws this exception if the adapter client does not specify a user name or password to connect to a Siebel system.</span></span>|  
|<span data-ttu-id="ac113-117">MetadataException</span><span class="sxs-lookup"><span data-stu-id="ac113-117">MetadataException</span></span>|<span data-ttu-id="ac113-118">如果擷取 Siebel 成品的中繼資料失敗，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-118">The adapter throws this exception if it fails to retrieve metadata for Siebel artifacts.</span></span>|  
|<span data-ttu-id="ac113-119">XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="ac113-119">XmlReaderParsingException</span></span>|<span data-ttu-id="ac113-120">如果輸入配接器用戶端在 Siebel 系統中，叫用作業所提供的資訊不完整或不正確，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-120">The adapter throws this exception if the input information provided by the adapter clients to invoke an operation in the Siebel system, is either incomplete or incorrect.</span></span>|  
|<span data-ttu-id="ac113-121">XmlReaderGenerationException</span><span class="sxs-lookup"><span data-stu-id="ac113-121">XmlReaderGenerationException</span></span>|<span data-ttu-id="ac113-122">無法產生輸出 Siebel 系統中執行作業時，配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-122">The adapter throws this exception if it is unable to generate output for an operation executed in a Siebel system.</span></span>|  
|<span data-ttu-id="ac113-123">TargetSystemException</span><span class="sxs-lookup"><span data-stu-id="ac113-123">TargetSystemException</span></span>|<span data-ttu-id="ac113-124">配接器擲回這個例外狀況，如果配接器使用 Siebel COM API 介面為 Siebel 系統時，擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-124">The adapter throws this exception if the Siebel COM API, which the adapter uses to interface with the Siebel system, throws an exception.</span></span> <span data-ttu-id="ac113-125">內部例外狀況包含 Siebel COM API 所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac113-125">The inner exception contains the exception thrown by the Siebel COM API.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac113-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac113-126">See Also</span></span>  
 <span data-ttu-id="ac113-127">[瞭解 BizTalk Adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ac113-127">[Understand BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) </span></span>  
[<span data-ttu-id="ac113-128">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="ac113-128">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)