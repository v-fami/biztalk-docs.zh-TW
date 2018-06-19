---
title: 如何匯出 BPEL4WS |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL4WS, exporting
- BPEL4WS, restrictions
- orchestrations, BPEL4WS
ms.assetid: 4648dfcf-cf48-4471-b088-07252c080fb8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16c2e34b498a9fb8d5fd3f6e69f022c2876a763
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253830"
---
# <a name="how-to-export-bpel4ws"></a><span data-ttu-id="531e2-102">如何匯出 BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="531e2-102">How to Export BPEL4WS</span></span>
<span data-ttu-id="531e2-103">您可以將現有的 BizTalk 協調流程匯出至 BPEL4WS。</span><span class="sxs-lookup"><span data-stu-id="531e2-103">You can export an existing BizTalk orchestration to BPEL4WS.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="531e2-104">這個版本的 BizTalk Server 支援 BPEL4WS 1.1。</span><span class="sxs-lookup"><span data-stu-id="531e2-104">This release of BizTalk Server supports BPEL4WS 1.1.</span></span> <span data-ttu-id="531e2-105">您不能匯入或匯出 BPEL4WS 1.0。</span><span class="sxs-lookup"><span data-stu-id="531e2-105">You cannot import or export BPEL4WS 1.0.</span></span>  
  
 <span data-ttu-id="531e2-106">當您匯出時，供編譯的 BPEL4WS 規範要求協調流程只能包含 XLANG/s 和 BPEL4WS 之間通用的功能，或可以轉譯為 BPEL4WS 且不影響行為的功能。</span><span class="sxs-lookup"><span data-stu-id="531e2-106">If you are exporting, BPEL4WS compliance for compilation requires that orchestrations contain only features that are common between XLANG/s and BPEL4WS, or features that can be translated into BPEL4WS without affecting behavior.</span></span>  
  
## <a name="export-restrictions-on-orchestrations-for-bpel4ws-compliance"></a><span data-ttu-id="531e2-107">BPEL4WS 規範的協調流程匯出限制</span><span class="sxs-lookup"><span data-stu-id="531e2-107">Export restrictions on orchestrations for BPEL4WS compliance</span></span>  
  
-   <span data-ttu-id="531e2-108">您不能使用 [呼叫協調流程] 圖形或 [啟動協調流程] 圖形。</span><span class="sxs-lookup"><span data-stu-id="531e2-108">You cannot use the Call Orchestration shape or the Start Orchestration shape.</span></span>  
  
-   <span data-ttu-id="531e2-109">您不能使用 [轉換] 圖形。</span><span class="sxs-lookup"><span data-stu-id="531e2-109">You cannot use the Transform shape.</span></span>  
  
-   <span data-ttu-id="531e2-110">您不能在自訂 .NET 元件叫用方法。</span><span class="sxs-lookup"><span data-stu-id="531e2-110">You cannot invoke methods on custom .NET components.</span></span>  
  
-   <span data-ttu-id="531e2-111">您不能將逾時套用到長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="531e2-111">You cannot apply a timeout to a long-running transaction.</span></span>  
  
-   <span data-ttu-id="531e2-112">您的協調流程不能接受參數。</span><span class="sxs-lookup"><span data-stu-id="531e2-112">Your orchestration cannot take parameters.</span></span>  
  
-   <span data-ttu-id="531e2-113">可呼叫的補償處理常式不能有參數。</span><span class="sxs-lookup"><span data-stu-id="531e2-113">Callable compensation handlers cannot have parameters.</span></span>  
  
-   <span data-ttu-id="531e2-114">XPATH 必須能夠支援變數類型。</span><span class="sxs-lookup"><span data-stu-id="531e2-114">Variable types must be supportable in XPATH.</span></span>  
  
-   <span data-ttu-id="531e2-115">您不能使用 [擱置] 圖形。</span><span class="sxs-lookup"><span data-stu-id="531e2-115">You cannot use the Suspend shape.</span></span>  
  
-   <span data-ttu-id="531e2-116">常值必須為下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="531e2-116">Literal values must be one of the following types:</span></span>  
  
     <span data-ttu-id="531e2-117">boolean、char、byte、sbyte、int32、uint32、int64、uint64、single、double、string</span><span class="sxs-lookup"><span data-stu-id="531e2-117">boolean, char, byte, sbyte, int32, uint32, int64, uint64, single, double, string</span></span>  
  
-   <span data-ttu-id="531e2-118">算術運算子只允許出現在下列數字型別的運算元：</span><span class="sxs-lookup"><span data-stu-id="531e2-118">Arithmetic operators are allowed only on operands of following numeric types:</span></span>  
  
     <span data-ttu-id="531e2-119">byte、sbyte、int32、uint32、int64、uint64、single、double</span><span class="sxs-lookup"><span data-stu-id="531e2-119">byte, sbyte, int32, uint32, int64, uint64, single, double</span></span>  
  
-   <span data-ttu-id="531e2-120">char 類型不能使用關係運算子。</span><span class="sxs-lookup"><span data-stu-id="531e2-120">Relational operators cannot be applied to type char.</span></span>  
  
-   <span data-ttu-id="531e2-121">您不能參考運算式中的服務連結屬性。</span><span class="sxs-lookup"><span data-stu-id="531e2-121">You cannot make a reference to a servicelink property in an expression.</span></span>  
  
-   <span data-ttu-id="531e2-122">您無法執行任何動作之間**傳送**圖形和**接收**使用相同的輸出要求-回應連接埠的圖形。</span><span class="sxs-lookup"><span data-stu-id="531e2-122">You cannot perform any actions between a **Send** shape and a **Receive** shape that use the same outbound request-response port.</span></span>  
  
-   <span data-ttu-id="531e2-123">您不能間接參考 Web 服務，像是透過參考包含參考的另一個專案。</span><span class="sxs-lookup"><span data-stu-id="531e2-123">You cannot indirectly reference a web service, as through a reference to another project that contains a reference.</span></span> <span data-ttu-id="531e2-124">您必須明確參考您的專案中之 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="531e2-124">You must explicitly reference the web service in your project.</span></span>  
  
-   <span data-ttu-id="531e2-125">您不能在延遲中指定常數 DateTime 或 TimeSpan。</span><span class="sxs-lookup"><span data-stu-id="531e2-125">You cannot specify a constant DateTime or TimeSpan in a delay.</span></span> <span data-ttu-id="531e2-126">而是要使用 System.Xml 命名空間中的其中一個轉換類別：</span><span class="sxs-lookup"><span data-stu-id="531e2-126">Instead, use one of the conversion classes in the System.Xml namespace:</span></span>  
  
     <span data-ttu-id="531e2-127">常數 DateTime：System.Xml.XmlConvert.ToDateTime，例如 System.Xml.XmlConvert.ToDateTime("2004-04-15")</span><span class="sxs-lookup"><span data-stu-id="531e2-127">For a constant DateTime: System.Xml.XmlConvert.ToDateTime, e.g System.Xml.XmlConvert.ToDateTime("2004-04-15")</span></span>  
  
     <span data-ttu-id="531e2-128">常數 TimeSpan：System.Xml.XmlConvert.ToTimeSpan，例如 System.Xml.XmlConvert.ToTimeSpan("2004-04-15")</span><span class="sxs-lookup"><span data-stu-id="531e2-128">For a constant TimeSpan: System.Xml.XmlConvert.ToTimeSpan, e.g System.Xml.XmlConvert.ToTimeSpan("2004-04-15")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="531e2-129">字元常值匯出為不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="531e2-129">Character literals are exported as unsigned integers.</span></span> <span data-ttu-id="531e2-130">例如，'a' 匯出為 97，'b' 匯出為 98 等等。</span><span class="sxs-lookup"><span data-stu-id="531e2-130">For example, 'a' is exported as 97, 'b' is exported as 98, and so forth.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="531e2-131">識別項名稱必須符合 W3C「可延伸標記語言」(XML) 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="531e2-131">Identifier names must conform to the W3C Extensible Markup Language (XML) 1.0 specification.</span></span>  
  
#### <a name="to-export-an-orchestration-to-bpel4ws"></a><span data-ttu-id="531e2-132">將協調流程匯出至 BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="531e2-132">To export an orchestration to BPEL4WS</span></span>  
  
1.  <span data-ttu-id="531e2-133">將類型為 BizTalk 協調流程的新項目加入您的專案。</span><span class="sxs-lookup"><span data-stu-id="531e2-133">Add a new item of type BizTalk Orchestration to your project.</span></span>  
  
2.  <span data-ttu-id="531e2-134">按一下設計介面，以顯示 [協調流程屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="531e2-134">Click the design surface to bring up the Orchestration Properties window.</span></span>  
  
3.  <span data-ttu-id="531e2-135">設定**模組可匯出**為 True。</span><span class="sxs-lookup"><span data-stu-id="531e2-135">Set **Module Exportable** to True.</span></span>  
  
4.  <span data-ttu-id="531e2-136">您想要用於命名空間中的型別**模組 XML 目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="531e2-136">Type in the namespace you want for **Module XML Target Namespace**.</span></span>  
  
5.  <span data-ttu-id="531e2-137">設定**協調流程可匯出**為 True。</span><span class="sxs-lookup"><span data-stu-id="531e2-137">Set **Orchestration Exportable** to True.</span></span>  
  
6.  <span data-ttu-id="531e2-138">您想要用於命名空間中的型別**協調流程 XML 目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="531e2-138">Type in the namespace you want for **Orchestration XML Target Namespace**.</span></span>  
  
7.  <span data-ttu-id="531e2-139">在 [方案總管] 中，使用滑鼠右鍵按一下協調流程的 .ODX 檔案。</span><span class="sxs-lookup"><span data-stu-id="531e2-139">In Solution Explorer, right-click the .ODX file for your orchestration.</span></span>  
  
8.  <span data-ttu-id="531e2-140">選取**匯出到 BPEL**。</span><span class="sxs-lookup"><span data-stu-id="531e2-140">Select **Export to BPEL**.</span></span>  
  
     <span data-ttu-id="531e2-141">您的協調流程會匯出到 BPEL4WS。</span><span class="sxs-lookup"><span data-stu-id="531e2-141">Your orchestration will be exported to BPEL4WS.</span></span> <span data-ttu-id="531e2-142">請參閱 [輸出視窗] 和 [工作清單]，以確認成功或診斷問題。</span><span class="sxs-lookup"><span data-stu-id="531e2-142">See the Output Window and Task List to confirm success or diagnose problems.</span></span> <span data-ttu-id="531e2-143">若匯出成功，則 .WSDL 檔案和 .BPEL 檔案會建立在您的專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="531e2-143">Once your export succeeds, a .WSDL file and a .BPEL file will be created in your project directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="531e2-144">若您的協調流程包含對角色連結 (服務連結) 的指派或對動態連接埠的常值指派，則 BizTalk 會產生空的 BPEL4WS 結束點參考並產生警告。</span><span class="sxs-lookup"><span data-stu-id="531e2-144">If your orchestration contains an assignment to a role link (service link) or a literal assignment to a dynamic port, BizTalk generates a dummy BPEL4WS endpoint reference and raises a warning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531e2-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="531e2-145">See Also</span></span>  
 <span data-ttu-id="531e2-146">[如何匯入 BPEL4WS](../core/how-to-import-bpel4ws.md) </span><span class="sxs-lookup"><span data-stu-id="531e2-146">[How to Import BPEL4WS](../core/how-to-import-bpel4ws.md) </span></span>  
 [<span data-ttu-id="531e2-147">XLANG-s 至 BPEL4WS 型別轉換</span><span class="sxs-lookup"><span data-stu-id="531e2-147">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)