---
title: 閱讀安裝已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 245379f2-4048-4803-83ea-38dc23eb1a81
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4bc572cc18ca7d9d5515fe9f189287df5d1440f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022948"
---
# <a name="read-the-installation-known-issues"></a><span data-ttu-id="056b8-102">閱讀安裝已知問題</span><span class="sxs-lookup"><span data-stu-id="056b8-102">Read the installation known issues</span></span>
[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]<span data-ttu-id="056b8-103"> 有列在下列各節中的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="056b8-103"> have known issues listed in the following sections.</span></span>  
  
## <a name="swift-does-not-support-stress-testing-on-integration-test-bed-itb-and-swiftnet-stub-environment"></a><span data-ttu-id="056b8-104">SWIFT 不支援整合測試平台 (ITB) 和 SWIFTNet 虛設常式環境測試的壓力</span><span class="sxs-lookup"><span data-stu-id="056b8-104">SWIFT Does Not Support Stress Testing on Integration Test Bed (ITB) and SWIFTNet Stub Environment</span></span>  
 <span data-ttu-id="056b8-105">ITB 不提供以輸送量，服務等級協定 (SLA)，而且無法保證資料是完全傳輸，或是一致。</span><span class="sxs-lookup"><span data-stu-id="056b8-105">The ITB does not provide Service Level Agreement (SLA) in terms of throughput, and cannot guarantee that data is completely transmitted or consistent.</span></span> <span data-ttu-id="056b8-106">您應該實作到實際執行網路試驗環境中的壓力測試。</span><span class="sxs-lookup"><span data-stu-id="056b8-106">You should stress test your implementation on the production network in the Pilot environment.</span></span>  
  
 <span data-ttu-id="056b8-107">此外，您必須確定所有節點 （伺服器、 線條和頻寬） 已正確設定以避免遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="056b8-107">Additionally, you must ensure that all of the nodes (server, lines, and bandwidth) are properly configured to avoid any data loss.</span></span> <span data-ttu-id="056b8-108">以下是典型的範例輸送量：</span><span class="sxs-lookup"><span data-stu-id="056b8-108">Following are typical sample throughputs:</span></span>  
  
- <span data-ttu-id="056b8-109">Fileact 互動傳送使用量較大的電腦 下： 20 的訊息/分鐘</span><span class="sxs-lookup"><span data-stu-id="056b8-109">Interact/Fileact Send under stressed computer: 20 messages/minute</span></span>  
  
- <span data-ttu-id="056b8-110">互動/Fileact 接收使用量較大的電腦 下： 300-400 訊息/分鐘</span><span class="sxs-lookup"><span data-stu-id="056b8-110">Interact/Fileact Receive under stressed computer: 300-400 messages/minute</span></span>  
  
  <span data-ttu-id="056b8-111">如需詳細資訊，請參閱您 SWIFT 的文件。</span><span class="sxs-lookup"><span data-stu-id="056b8-111">For more information, see your SWIFT documentation.</span></span>  
  
## <a name="messages-not-pushed-when-queue-is-open"></a><span data-ttu-id="056b8-112">開啟佇列時不會發送的訊息</span><span class="sxs-lookup"><span data-stu-id="056b8-112">Messages Not Pushed When Queue Is Open</span></span>  
 <span data-ttu-id="056b8-113">當您使用互動或 FileAct 儲存和轉寄 (SnF) 模式中，如果佇列的工作階段已開啟，而且不會發送訊息時，您必須重新 SNLreceiver.exe。</span><span class="sxs-lookup"><span data-stu-id="056b8-113">When you are using InterAct or FileAct Store and Forward (SnF) mode, if the session with the queue is open and messages are not being pushed, then you must restart SNLreceiver.exe.</span></span> <span data-ttu-id="056b8-114">這可避免 SWIFT 可能偶爾發生的問題。</span><span class="sxs-lookup"><span data-stu-id="056b8-114">This avoids an issue with SWIFT that can occur occasionally.</span></span>  
  
## <a name="you-must-use-cdata-when-passing-characters-like--and--in-message"></a><span data-ttu-id="056b8-115">您必須使用 CDATA 當傳遞字元像是"<"和"&"訊息</span><span class="sxs-lookup"><span data-stu-id="056b8-115">You Must Use CDATA when Passing Characters like "<" and "&" in message</span></span>  
 <span data-ttu-id="056b8-116">CDATA 會使用不應由 XML 剖析器剖析的文字資料的相關詞彙。</span><span class="sxs-lookup"><span data-stu-id="056b8-116">The term CDATA is used about text data that should not be parsed by the XML parser.</span></span>  <span data-ttu-id="056b8-117">字元像是"<"和"&"是不合法的 XML 項目中。</span><span class="sxs-lookup"><span data-stu-id="056b8-117">Characters like "<" and "&" are illegal in XML elements.</span></span> <span data-ttu-id="056b8-118">"<"會產生錯誤，因為剖析器將它解譯為新項目的開頭。</span><span class="sxs-lookup"><span data-stu-id="056b8-118">"<" will generate an error because the parser interprets it as the start of a new element.</span></span> <span data-ttu-id="056b8-119">"&"會產生錯誤，因為剖析器將它解譯為開頭的字元實體。</span><span class="sxs-lookup"><span data-stu-id="056b8-119">"&" will generate an error because the parser interprets it as the start of a character entity.</span></span> <span data-ttu-id="056b8-120">剖析器會忽略 CDATA 區段內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="056b8-120">Everything inside a CDATA section is ignored by the parser.</span></span> <span data-ttu-id="056b8-121">CDATA 區段的開頭 「\<！ [CDATA ["和結尾是"]]\>"</span><span class="sxs-lookup"><span data-stu-id="056b8-121">A CDATA section starts with "\<![CDATA[" and ends with "]]\>"</span></span>  
  
## <a name="you-must-use-passthrough-pipelines-with-payload-only-mode"></a><span data-ttu-id="056b8-122">您必須使用 Passthrough 管線具有僅限裝載模式</span><span class="sxs-lookup"><span data-stu-id="056b8-122">You Must Use Passthrough Pipelines with Payload-Only Mode</span></span>  
 <span data-ttu-id="056b8-123">如果您使用僅限裝載模式 InterAct 配接器，您必須使用通過管線，在這兩個傳送和接收埠，如果您不想要使用自訂管線。</span><span class="sxs-lookup"><span data-stu-id="056b8-123">If you are using payload-only mode for the InterAct adapter, you must use pass-through pipelines on both the send and receive ports if you are not using custom pipelines.</span></span>  
  
## <a name="multiple-security-contexts-not-created-swiftnet-stub-computer"></a><span data-ttu-id="056b8-124">無法建立 （SWIFTNet 虛設常式電腦） 的多個安全性內容</span><span class="sxs-lookup"><span data-stu-id="056b8-124">Multiple Security Contexts Not Created (SWIFTNet Stub Computer)</span></span>  
 <span data-ttu-id="056b8-125">SWIFTNet 虛設常式的電腦上，多個安全性內容不會針對不同的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="056b8-125">On a SWIFTNet stub computer, multiple security contexts are not created for different send ports.</span></span> <span data-ttu-id="056b8-126">ITB 上建立多個安全性內容。</span><span class="sxs-lookup"><span data-stu-id="056b8-126">Multiple security contexts are created on ITB.</span></span>