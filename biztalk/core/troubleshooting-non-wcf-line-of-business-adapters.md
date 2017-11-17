---
title: "疑難排解非-WCF 線條的商務配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d5f7877-656f-406e-9edb-d6b9a0705b02
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba36ed8a8efb62e2eb8e885791c3c28012dcc49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-non-wcf-line-of-business-adapters"></a><span data-ttu-id="ed1fb-102">疑難排解非 WCF 商務營運系統配接器</span><span class="sxs-lookup"><span data-stu-id="ed1fb-102">Troubleshooting non-WCF Line of Business Adapters</span></span>
## <a name="failed-to-retrieve-error"></a><span data-ttu-id="ed1fb-103">「無法擷取」錯誤</span><span class="sxs-lookup"><span data-stu-id="ed1fb-103">“Failed to retrieve” error</span></span>  
 <span data-ttu-id="ed1fb-104">使用非 WCF 企業營運 (LOB) 配接器時，可能發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ed1fb-104">When using a non-WCF Line of Business (LOB) adapter, the following errors may occur:</span></span>  
  
-   <span data-ttu-id="ed1fb-105">無法擷取系統</span><span class="sxs-lookup"><span data-stu-id="ed1fb-105">Failed to retrieve system</span></span>  
  
-   <span data-ttu-id="ed1fb-106">瀏覽代理程式： 錯誤受困於建構函式。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-106">Browsing agent: Error trapped in constructor.</span></span> <span data-ttu-id="ed1fb-107">目標電腦主動拒絕連線。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-107">Target machine Actively refused connection.</span></span>  
  
-   <span data-ttu-id="ed1fb-108">執行階段代理程式： 錯誤受困於建構函式。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-108">Runtime agent: Error trapped in constructor.</span></span> <span data-ttu-id="ed1fb-109">目標電腦主動拒絕連線。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-109">Target machine Actively refused connection.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="ed1fb-110">原因</span><span class="sxs-lookup"><span data-stu-id="ed1fb-110">Cause</span></span>  
 <span data-ttu-id="ed1fb-111">LOB 配接器使用 .Net 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-111">The LOB adapters use .Net Remoting.</span></span> <span data-ttu-id="ed1fb-112">如果 .Net 遠端處理的啟用時間比預期長，配接器便可能傳回這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-112">If the .Net Remoting activation takes longer than expected, the adapter may return these errors.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ed1fb-113">解決方案</span><span class="sxs-lookup"><span data-stu-id="ed1fb-113">Resolution</span></span>  
 <span data-ttu-id="ed1fb-114">建立**StartAgentSleep**登錄機碼，增加逾時值：</span><span class="sxs-lookup"><span data-stu-id="ed1fb-114">Create the **StartAgentSleep** registry key and increase the timeout value:</span></span>  
  
1.  <span data-ttu-id="ed1fb-115">開啟登錄，並移至*HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-115">Open the registry and go to *HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*.</span></span>  
  
2.  <span data-ttu-id="ed1fb-116">以下列屬性建立新的 DWORD 值：</span><span class="sxs-lookup"><span data-stu-id="ed1fb-116">Create a new DWORD value with the following properties:</span></span>  
  
     <span data-ttu-id="ed1fb-117">名稱： StartAgentSleep</span><span class="sxs-lookup"><span data-stu-id="ed1fb-117">Name: StartAgentSleep</span></span>  
  
     <span data-ttu-id="ed1fb-118">基底： 十進位</span><span class="sxs-lookup"><span data-stu-id="ed1fb-118">Base: Decimal</span></span>  
  
     <span data-ttu-id="ed1fb-119">值資料： 1000年</span><span class="sxs-lookup"><span data-stu-id="ed1fb-119">Value data: 1000</span></span>  
  
 <span data-ttu-id="ed1fb-120">屬值資料的單位是毫秒 (ms)。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-120">Value data is measured in milliseconds (ms).</span></span> <span data-ttu-id="ed1fb-121">1000ms 等於 1 秒。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-121">1000ms equals 1 second.</span></span>  
  
 <span data-ttu-id="ed1fb-122">在某些系統中，1 秒可能不夠。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-122">In some systems, one second may not be enough.</span></span> <span data-ttu-id="ed1fb-123">增加該值並進行測試，有助於決定所需的適當逾時。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-123">Increase the value and test to help determine the appropriate timeout needed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed1fb-124">加入**StartAgentSleep**登錄機碼將影響**所有**非 WCF LOB 配接器。</span><span class="sxs-lookup"><span data-stu-id="ed1fb-124">Adding the **StartAgentSleep** registry key impacts **all** the non-WCF LOB adapters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1fb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed1fb-125">See Also</span></span>  
 [<span data-ttu-id="ed1fb-126">疑難排解 BizTalk Server 配接器</span><span class="sxs-lookup"><span data-stu-id="ed1fb-126">Troubleshooting BizTalk Server Adapters</span></span>](../core/troubleshooting-biztalk-server-adapters.md)