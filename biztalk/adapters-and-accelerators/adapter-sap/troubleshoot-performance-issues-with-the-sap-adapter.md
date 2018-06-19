---
title: 疑難排解 SAP 配接器的效能問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance
- performance, troubleshooting
ms.assetid: 7e8e9fec-0edf-4c67-837c-0e271b2ffe68
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9e18a2f26af993da36a13d389f2aff2ad2f60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217118"
---
# <a name="troubleshoot-performance-issues-with-the-sap-adapter"></a><span data-ttu-id="35f1d-102">疑難排解 SAP 配接器的效能問題</span><span class="sxs-lookup"><span data-stu-id="35f1d-102">Troubleshoot Performance Issues with the SAP adapter</span></span>
<span data-ttu-id="35f1d-103">本章節將討論使用來解決使用時，可能會遇到效能問題的疑難排解技巧[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35f1d-103">This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
##  <a name="BKMK_SAPSlowdown"></a><span data-ttu-id="35f1d-104">速度變慢或拖延輸送量與 BizTalk Server 使用配接器時</span><span class="sxs-lookup"><span data-stu-id="35f1d-104">Slowdown or stall in throughput when using the adapter with BizTalk Server</span></span>  
 <span data-ttu-id="35f1d-105">**問題**</span><span class="sxs-lookup"><span data-stu-id="35f1d-105">**Problem**</span></span>  
  
 <span data-ttu-id="35f1d-106">當使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，配接器所傳送或接收的訊息數目變慢或移至的拖延。</span><span class="sxs-lookup"><span data-stu-id="35f1d-106">When using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.</span></span>  
  
 <span data-ttu-id="35f1d-107">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="35f1d-107">**Cause**</span></span>  
  
 <span data-ttu-id="35f1d-108">**EnableBizTalkCompatibilityMode**繫結屬性未設定 Wcf-custom 傳送或接收埠，BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="35f1d-108">The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration Console.</span></span>  
  
 <span data-ttu-id="35f1d-109">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="35f1d-109">**Resolution**</span></span>  
  
 <span data-ttu-id="35f1d-110">設定**EnableBizTalkCompatibilityMode**繫結屬性為 True。</span><span class="sxs-lookup"><span data-stu-id="35f1d-110">Set the **EnableBizTalkCompatibilityMode** binding property to True.</span></span> <span data-ttu-id="35f1d-111">如需有關這個屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="35f1d-111">For more information about this property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span> <span data-ttu-id="35f1d-112">如需如何設定繫結屬性的指示，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="35f1d-112">For instructions on how to set a binding property, see [Configure the binding properties for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).</span></span>  
  
##  <a name="BKMK_SAPMemLeak"></a><span data-ttu-id="35f1d-113">使用參數的 NULL 值時，可能的記憶體流失</span><span class="sxs-lookup"><span data-stu-id="35f1d-113">Possible memory leak when using NULL values for parameters</span></span>  
 <span data-ttu-id="35f1d-114">**問題**</span><span class="sxs-lookup"><span data-stu-id="35f1d-114">**Problem**</span></span>  
  
 <span data-ttu-id="35f1d-115">您可能會注意到記憶體流失，如果您未指定輸入或資料表參數的值時叫用 SAP 系統中的成品。</span><span class="sxs-lookup"><span data-stu-id="35f1d-115">You may observe memory leak if you do not specify values for input or table parameters while invoking artifacts in the SAP system.</span></span>  
  
 <span data-ttu-id="35f1d-116">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="35f1d-116">**Resolution**</span></span>  
  
 <span data-ttu-id="35f1d-117">請確定您指定所有輸入與資料表參數的值時叫用 SAP 系統中的成品。</span><span class="sxs-lookup"><span data-stu-id="35f1d-117">Make sure you specify values for all the input and table parameters while invoking an artifact in the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f1d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35f1d-118">See Also</span></span>  
[<span data-ttu-id="35f1d-119">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="35f1d-119">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)