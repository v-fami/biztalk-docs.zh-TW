---
title: "Siebel 配接器疑難排解效能問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance issues
- performance, troubleshooting
ms.assetid: fe413b15-f703-4148-99df-17b5be3c74c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6443dd8b96b19b3cf42f6444ba1ae6c16f2b4ee6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-siebel-adapter"></a><span data-ttu-id="568b5-102">Siebel 配接器疑難排解效能問題</span><span class="sxs-lookup"><span data-stu-id="568b5-102">Troubleshoot Performance Issues with the Siebel adapter</span></span>
<span data-ttu-id="568b5-103">本章節將討論使用來解決使用時，可能會遇到效能問題的疑難排解技巧[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="568b5-103">This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="568b5-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="568b5-104">Known Issues</span></span>  
  
###  <a name="slowdown-or-stall-in-throughput-when-using-the-adapter-with-biztalk-server"></a><span data-ttu-id="568b5-105">速度變慢或拖延輸送量與 BizTalk Server 使用配接器時</span><span class="sxs-lookup"><span data-stu-id="568b5-105">Slowdown or stall in throughput when using the adapter with BizTalk Server</span></span>  
 <span data-ttu-id="568b5-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="568b5-106">**Problem**</span></span>  
  
 <span data-ttu-id="568b5-107">當使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，配接器所傳送或接收的訊息數目變慢或移至的拖延。</span><span class="sxs-lookup"><span data-stu-id="568b5-107">When using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.</span></span>  
  
 <span data-ttu-id="568b5-108">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="568b5-108">**Cause**</span></span>  
  
 <span data-ttu-id="568b5-109">**EnableBizTalkCompatibilityMode**繫結屬性未設定 Wcf-custom 傳送或接收埠，BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="568b5-109">The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="568b5-110">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="568b5-110">**Resolution**</span></span>  
  
 <span data-ttu-id="568b5-111">設定**EnableBizTalkCompatibilityMode**繫結屬性為 True。</span><span class="sxs-lookup"><span data-stu-id="568b5-111">Set the **EnableBizTalkCompatibilityMode** binding property to True.</span></span> <span data-ttu-id="568b5-112">如需有關這個屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="568b5-112">For more information about this property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span> <span data-ttu-id="568b5-113">如需如何設定繫結屬性的指示，請參閱[siebel 設定繫結屬性](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="568b5-113">For instructions on how to set a binding property, see [Configure the binding properties for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568b5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="568b5-114">See Also</span></span>  
[<span data-ttu-id="568b5-115">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="568b5-115">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)