---
title: 例外狀況和錯誤處理與 Siebel 配接器 |Microsoft Docs
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
ms.openlocfilehash: 67a615bec1bf1b8cd29e84728f39d6fea626f16e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977118"
---
# <a name="exceptions-and-error-handling-with-the-siebel-adapter"></a><span data-ttu-id="8221e-102">例外狀況和錯誤處理與 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="8221e-102">Exceptions and Error Handling with the Siebel adapter</span></span>
## <a name="exception-list"></a><span data-ttu-id="8221e-103">例外狀況清單</span><span class="sxs-lookup"><span data-stu-id="8221e-103">Exception list</span></span>
<span data-ttu-id="8221e-104">擲回的例外狀況[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8221e-104">The exceptions thrown by the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span> <span data-ttu-id="8221e-105">其中可包含：</span><span class="sxs-lookup"><span data-stu-id="8221e-105">These can contain:</span></span>  
  
- <span data-ttu-id="8221e-106">內部例外狀況，也就是.NET Framework 會擲回系統例外狀況</span><span class="sxs-lookup"><span data-stu-id="8221e-106">An inner exception, which is a system exception that the .NET Framework throws</span></span>  
  
- <span data-ttu-id="8221e-107">LOB 用戶端程式庫會擲回 LOB 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-107">An LOB exception that the LOB client library throws.</span></span>  
  
  <span data-ttu-id="8221e-108">如需有關內部例外狀況的詳細資訊，請參閱個別的.NET Framework 或 Siebel 文件。</span><span class="sxs-lookup"><span data-stu-id="8221e-108">For more information about the inner exception, refer to the respective .NET Framework or Siebel documentation.</span></span> <span data-ttu-id="8221e-109">例外狀況也會包含詳細的錯誤訊息，以協助解決問題。</span><span class="sxs-lookup"><span data-stu-id="8221e-109">The exception also contains a detailed error message that helps in resolving the problem.</span></span> <span data-ttu-id="8221e-110">請注意，此處所提及的例外狀況的清單不完整。</span><span class="sxs-lookup"><span data-stu-id="8221e-110">Note that the list of exceptions mentioned here is not comprehensive.</span></span>  
  
|<span data-ttu-id="8221e-111">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8221e-111">Exception</span></span>|<span data-ttu-id="8221e-112">可能的原因/錯誤描述</span><span class="sxs-lookup"><span data-stu-id="8221e-112">Possible Cause/Error Description</span></span>|  
|---------------|---------------------------------------|  
|<span data-ttu-id="8221e-113">ConnectionException</span><span class="sxs-lookup"><span data-stu-id="8221e-113">ConnectionException</span></span>|<span data-ttu-id="8221e-114">如果無法建立連線，或關閉現有連接至 Siebel 系統的配接器，則會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-114">The adapter throws this exception if it is unable to establish a connection or close an existing connection to a Siebel system.</span></span>|  
|<span data-ttu-id="8221e-115">CredentialsException</span><span class="sxs-lookup"><span data-stu-id="8221e-115">CredentialsException</span></span>|<span data-ttu-id="8221e-116">如果配接器用戶端未指定使用者名稱或連接至 Siebel 系統的密碼，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-116">The adapter throws this exception if the adapter client does not specify a user name or password to connect to a Siebel system.</span></span>|  
|<span data-ttu-id="8221e-117">MetadataException</span><span class="sxs-lookup"><span data-stu-id="8221e-117">MetadataException</span></span>|<span data-ttu-id="8221e-118">如果它無法擷取 Siebel 構件的中繼資料，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-118">The adapter throws this exception if it fails to retrieve metadata for Siebel artifacts.</span></span>|  
|<span data-ttu-id="8221e-119">XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="8221e-119">XmlReaderParsingException</span></span>|<span data-ttu-id="8221e-120">如果輸入配接器用戶端，若要在 Siebel 系統中，叫用作業所提供的資訊不完整或不正確，則配接器會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-120">The adapter throws this exception if the input information provided by the adapter clients to invoke an operation in the Siebel system, is either incomplete or incorrect.</span></span>|  
|<span data-ttu-id="8221e-121">XmlReaderGenerationException</span><span class="sxs-lookup"><span data-stu-id="8221e-121">XmlReaderGenerationException</span></span>|<span data-ttu-id="8221e-122">如果無法產生在 Siebel 系統中執行作業的輸出配接器，則會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-122">The adapter throws this exception if it is unable to generate output for an operation executed in a Siebel system.</span></span>|  
|<span data-ttu-id="8221e-123">TargetSystemException</span><span class="sxs-lookup"><span data-stu-id="8221e-123">TargetSystemException</span></span>|<span data-ttu-id="8221e-124">配接器擲回這個例外狀況，如果配接器會使用 Siebel COM API 介面與 Siebel 系統擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-124">The adapter throws this exception if the Siebel COM API, which the adapter uses to interface with the Siebel system, throws an exception.</span></span> <span data-ttu-id="8221e-125">內部例外狀況包含 Siebel COM API 所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8221e-125">The inner exception contains the exception thrown by the Siebel COM API.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8221e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8221e-126">See Also</span></span>  
 <span data-ttu-id="8221e-127">[了解 BizTalk Adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) </span><span class="sxs-lookup"><span data-stu-id="8221e-127">[Understand BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) </span></span>  
[<span data-ttu-id="8221e-128">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="8221e-128">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)