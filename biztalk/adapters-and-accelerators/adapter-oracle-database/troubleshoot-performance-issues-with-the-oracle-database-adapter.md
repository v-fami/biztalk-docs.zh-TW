---
title: "搭配 Oracle 資料庫配接器的效能問題疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance issues, troubleshooting
- troubleshooting, performance issues
ms.assetid: 2035cd2e-ce87-419b-aada-61d257671623
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20b0f8db3f1b7549f6189b348b7353d6dac159a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="7e067-102">搭配 Oracle 資料庫配接器的效能問題疑難排解</span><span class="sxs-lookup"><span data-stu-id="7e067-102">Troubleshoot performance issues with the Oracle Database adapter</span></span>
<span data-ttu-id="7e067-103">本章節將討論使用來解決使用時，可能會遇到效能問題的疑難排解技巧[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7e067-103">This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="7e067-104">已知的問題</span><span class="sxs-lookup"><span data-stu-id="7e067-104">Known Issue</span></span>  
 <span data-ttu-id="7e067-105">以下是最常見的效能問題時使用，可能會遇到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連同其可能的原因和解決方式。</span><span class="sxs-lookup"><span data-stu-id="7e067-105">The following is the most common performance issue you might encounter when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], along with its probable cause and resolution.</span></span>  
  
##  <span data-ttu-id="7e067-106"><a name="BKMK_Slowdown"></a>速度變慢或拖延輸送量與 BizTalk Server 使用配接器時</span><span class="sxs-lookup"><span data-stu-id="7e067-106"><a name="BKMK_Slowdown"></a> Slowdown or stall in throughput when using the adapter with BizTalk Server</span></span>  
 <span data-ttu-id="7e067-107">**問題**</span><span class="sxs-lookup"><span data-stu-id="7e067-107">**Problem**</span></span>  
  
 <span data-ttu-id="7e067-108">當使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，配接器所傳送或接收的訊息數目變慢或移至的拖延。</span><span class="sxs-lookup"><span data-stu-id="7e067-108">When using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.</span></span>  
  
 <span data-ttu-id="7e067-109">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="7e067-109">**Cause**</span></span>  
  
 <span data-ttu-id="7e067-110">**EnableBizTalkCompatibilityMode**繫結屬性未設定 Wcf-custom 傳送或接收埠，BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="7e067-110">The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="7e067-111">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="7e067-111">**Resolution**</span></span>  
  
 <span data-ttu-id="7e067-112">設定**EnableBizTalkCompatibilityMode**繫結屬性為 True。</span><span class="sxs-lookup"><span data-stu-id="7e067-112">Set the **EnableBizTalkCompatibilityMode** binding property to True.</span></span> <span data-ttu-id="7e067-113">如需有關這個屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="7e067-113">For more information about this property, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="7e067-114">如需如何設定繫結屬性的指示，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="7e067-114">For instructions on how to set a binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
### <a name="possible-memory-leak-on-a-64-bit-computer-when-using-the-oracle-database-adapter-to-perform-operations-involving-float-data-type"></a><span data-ttu-id="7e067-115">當您使用 Oracle 資料庫配接器執行涉及浮點資料類型的作業時的 64 位元電腦上可能有記憶體流失</span><span class="sxs-lookup"><span data-stu-id="7e067-115">Possible memory leak on a 64-bit computer when using the Oracle database adapter to perform operations involving FLOAT data type</span></span>  
 <span data-ttu-id="7e067-116">**問題**</span><span class="sxs-lookup"><span data-stu-id="7e067-116">**Problem**</span></span>  
  
 <span data-ttu-id="7e067-117">使用時，您可能會遇到記憶體流失[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來執行作業，涉及 FLOAT 資料類型的 64 位元電腦上。</span><span class="sxs-lookup"><span data-stu-id="7e067-117">You may experience a memory leak when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on a 64-bit computer to perform operations that involve FLOAT data types.</span></span>  
  
 <span data-ttu-id="7e067-118">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="7e067-118">**Resolution**</span></span>  
  
 <span data-ttu-id="7e067-119">安裝.NET \<*版本*> (x64) 64 位元電腦上的。</span><span class="sxs-lookup"><span data-stu-id="7e067-119">Install .NET \<*version*> (x64) on the 64-bit computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e067-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e067-120">See Also</span></span>  
[<span data-ttu-id="7e067-121">疑難排解 Oracle 資料庫 adapter.md</span><span class="sxs-lookup"><span data-stu-id="7e067-121">Troubleshoot the Oracle Database adapter.md</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)