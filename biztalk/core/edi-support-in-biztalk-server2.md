---
title: EDI 支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04cd9c14b9c3663bdf332155cc9824e1681ca7a6
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710293"
---
# <a name="edi-support-in-biztalk-server"></a><span data-ttu-id="22c9d-102">BizTalk Server 中的 EDI 支援</span><span class="sxs-lookup"><span data-stu-id="22c9d-102">EDI Support in BizTalk Server</span></span>
<span data-ttu-id="22c9d-103">EDI 內建於 BizTalk Server 時，則選擇性元件安裝和設定 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="22c9d-103">EDI is built-in to BizTalk Server, and is an optional component when you install and configure BizTalk Server.</span></span> 
  
## <a name="feature-set-comparison-chart"></a><span data-ttu-id="22c9d-104">功能集合比較表</span><span class="sxs-lookup"><span data-stu-id="22c9d-104">Feature Set Comparison Chart</span></span>  
 <span data-ttu-id="22c9d-105">下表顯示 BizTalk Server 隨附的 EDI 支援。</span><span class="sxs-lookup"><span data-stu-id="22c9d-105">The following table shows the EDI support included with BizTalk Server.</span></span>
  
|<span data-ttu-id="22c9d-106">功能</span><span class="sxs-lookup"><span data-stu-id="22c9d-106">Feature</span></span>|<span data-ttu-id="22c9d-107">註解</span><span class="sxs-lookup"><span data-stu-id="22c9d-107">Comment</span></span>|  
|---|---|
|<span data-ttu-id="22c9d-108">在交易集修改 ISA 區段</span><span class="sxs-lookup"><span data-stu-id="22c9d-108">ISA    Segment modification at transaction set</span></span>| <span data-ttu-id="22c9d-109">建立 TransactionSet 特有協議</span><span class="sxs-lookup"><span data-stu-id="22c9d-109">Create TransactionSet-specific agreements</span></span>|  
|<span data-ttu-id="22c9d-110">ISA11︰ 美國或其他標準類型</span><span class="sxs-lookup"><span data-stu-id="22c9d-110">ISA11:    US or other standard type</span></span>| |  
|<span data-ttu-id="22c9d-111">ISA12︰ 交換控制版本</span><span class="sxs-lookup"><span data-stu-id="22c9d-111">ISA12:    Interchange Control Version</span></span>| |  
|<span data-ttu-id="22c9d-112">ISA13︰ 交換控制編號 （遞增編號）</span><span class="sxs-lookup"><span data-stu-id="22c9d-112">ISA13:    Interchange Control Number (incrementing number)</span></span>| |  
|<span data-ttu-id="22c9d-113">ISA15︰ 測試或實際執行</span><span class="sxs-lookup"><span data-stu-id="22c9d-113">ISA15:    Test or Production</span></span>| |  
|<span data-ttu-id="22c9d-114">在文件/交易層級修改 GS 區段</span><span class="sxs-lookup"><span data-stu-id="22c9d-114">GS    Segment modification at document/transaction level</span></span>| |  
|<span data-ttu-id="22c9d-115">GS 傳送者/接收者識別碼不可為與 ISA 不同</span><span class="sxs-lookup"><span data-stu-id="22c9d-115">GS    sender/receiver IDs allowed to be different than ISA</span></span>| |  
|<span data-ttu-id="22c9d-116">不同於 ISA 與 GS 輸出識別的輸入文件識別碼</span><span class="sxs-lookup"><span data-stu-id="22c9d-116">Inbound    Document IDs different than ISA & GS Outbound IDs</span></span>| |  
|<span data-ttu-id="22c9d-117">GS01︰ 能夠變更的文件類型</span><span class="sxs-lookup"><span data-stu-id="22c9d-117">GS01:    Ability to change type of document</span></span>| |  
|<span data-ttu-id="22c9d-118">GS04︰ 日期 （變更格式的能力）</span><span class="sxs-lookup"><span data-stu-id="22c9d-118">GS04:    Date (Ability to change format)</span></span>|<span data-ttu-id="22c9d-119">包含可選取 CCYYMMDD 和 yymmdd 日期格式的 UI</span><span class="sxs-lookup"><span data-stu-id="22c9d-119">Contains UI to select format as CCYYMMDD and YYMMDD</span></span>|  
|<span data-ttu-id="22c9d-120">GS05︰ 時間 （變更格式的能力）</span><span class="sxs-lookup"><span data-stu-id="22c9d-120">GS05:    Time (Ability to change format)</span></span>|<span data-ttu-id="22c9d-121">包含可選取 HHMM、 HHMMSS 和 HHMMSSdd 格式的 UI</span><span class="sxs-lookup"><span data-stu-id="22c9d-121">Contains UI to select format as HHMM, HHMMSS, and HHMMSSdd</span></span>|  
|<span data-ttu-id="22c9d-122">GS06︰ 變更控制編號</span><span class="sxs-lookup"><span data-stu-id="22c9d-122">GS06:    Change the control number</span></span>| |  
|<span data-ttu-id="22c9d-123">GS07︰ 代理程式碼</span><span class="sxs-lookup"><span data-stu-id="22c9d-123">GS07:    Agency Code</span></span>| |  
|<span data-ttu-id="22c9d-124">GS08︰ 能夠放在標準版本</span><span class="sxs-lookup"><span data-stu-id="22c9d-124">GS08:    Able to put in standards version</span></span>| |  
|<span data-ttu-id="22c9d-125">若要覆寫在執行階段的 EDI 信封的能力</span><span class="sxs-lookup"><span data-stu-id="22c9d-125">Ability to override EDI envelope at runtime</span></span>| |  
|<span data-ttu-id="22c9d-126">自訂 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="22c9d-126">Custom    EDI Schemas</span></span>| |  
|<span data-ttu-id="22c9d-127">組織/合作對象設定</span><span class="sxs-lookup"><span data-stu-id="22c9d-127">Organization/Party Setting</span></span>|<span data-ttu-id="22c9d-128">建立個別的合作對象和協議。</span><span class="sxs-lookup"><span data-stu-id="22c9d-128">Create separate party and agreements.</span></span> <span data-ttu-id="22c9d-129">也請建立範本為基礎的協議。</span><span class="sxs-lookup"><span data-stu-id="22c9d-129">Also create agreements based off templates.</span></span>|  
|<span data-ttu-id="22c9d-130">透過文件定義路由 EDI 文件</span><span class="sxs-lookup"><span data-stu-id="22c9d-130">EDI    document routing via document definition</span></span>| |  
|<span data-ttu-id="22c9d-131">交易夥伴的自動 997</span><span class="sxs-lookup"><span data-stu-id="22c9d-131">Automatic 997’s to trading partners</span></span>|<span data-ttu-id="22c9d-132">特定商務設定檔組態</span><span class="sxs-lookup"><span data-stu-id="22c9d-132">Configuration specific to business profiles</span></span>|  
|<span data-ttu-id="22c9d-133">可信賴傳訊透過 997 輸出 EDI</span><span class="sxs-lookup"><span data-stu-id="22c9d-133">Outbound    EDI reliable messaging via 997’s</span></span>| |  
|<span data-ttu-id="22c9d-134">EDIFACT 支援</span><span class="sxs-lookup"><span data-stu-id="22c9d-134">EDIFACT    Support</span></span>|<span data-ttu-id="22c9d-135">支援 D93 至 D05 ISO 9735 v4.1</span><span class="sxs-lookup"><span data-stu-id="22c9d-135">Supports D93 to D05 per ISO 9735 v4.1</span></span>|  
|<span data-ttu-id="22c9d-136">X12 支援</span><span class="sxs-lookup"><span data-stu-id="22c9d-136">X12    Support</span></span>|<span data-ttu-id="22c9d-137">2040 到 5030</span><span class="sxs-lookup"><span data-stu-id="22c9d-137">2040 to 5030</span></span>|  
|<span data-ttu-id="22c9d-138">HIPAA 支援</span><span class="sxs-lookup"><span data-stu-id="22c9d-138">HIPAA support</span></span>| <span data-ttu-id="22c9d-139">Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) 做為原生 EDI 功能的一部分</span><span class="sxs-lookup"><span data-stu-id="22c9d-139">Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) as  part of native EDI functionality</span></span>|  
|<span data-ttu-id="22c9d-140">移除列舉值/程式碼清單的能力</span><span class="sxs-lookup"><span data-stu-id="22c9d-140">Ability to remove enumerators/codelists</span></span>|<span data-ttu-id="22c9d-141">使用 Visual Studio/BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="22c9d-141">Use Visual Studio/BizTalk Editor</span></span>|  
|<span data-ttu-id="22c9d-142">AS2 傳送/接收</span><span class="sxs-lookup"><span data-stu-id="22c9d-142">AS2    Send/Receive</span></span>| <span data-ttu-id="22c9d-143">AS2 是 Crummond Certified 標準： 多個檔案附件支援、 檔案名稱保留支援和互通性。</span><span class="sxs-lookup"><span data-stu-id="22c9d-143">AS2 is Drummond Certified for multi-file attachment support, file name preservation support and interoperability.</span></span>|  
|<span data-ttu-id="22c9d-144">AS2 檔案名稱保留</span><span class="sxs-lookup"><span data-stu-id="22c9d-144">AS2 file name preservation</span></span>| |  
|<span data-ttu-id="22c9d-145">AS2 可信賴傳訊</span><span class="sxs-lookup"><span data-stu-id="22c9d-145">AS2 reliable messaging</span></span>| |  
|<span data-ttu-id="22c9d-146">輸出批次處理 （累積在單一交易中的多個交易類型）</span><span class="sxs-lookup"><span data-stu-id="22c9d-146">Outbound    Batching (accumulating multiple transaction types in a single transaction)</span></span>|<span data-ttu-id="22c9d-147">支援多個批次組態的每個商務設定檔</span><span class="sxs-lookup"><span data-stu-id="22c9d-147">Supports multiple batch configurations for each business profile</span></span>|  
|<span data-ttu-id="22c9d-148">輸入批次處理： 交換 XML （保留內送的 「 批次 」 交換） 或根據組態選項的交易集 XML</span><span class="sxs-lookup"><span data-stu-id="22c9d-148">Inbound    Batching – Interchange XML (preserving an incoming ‘batched’ interchange) or Transaction Set XML based off configuration options</span></span>|<span data-ttu-id="22c9d-149">也支援輸入-解除批次處理即將，亦即，交換分割成個別交易集 Xml</span><span class="sxs-lookup"><span data-stu-id="22c9d-149">Also supports inbound-debatching, i.e., splitting interchange into individual Transaction Set Xml</span></span>|  
|<span data-ttu-id="22c9d-150">交換和交易集產生和驗證 Visual Studio 中於設計階段</span><span class="sxs-lookup"><span data-stu-id="22c9d-150">Interchange    and Transaction Set Generation and Validation in Design Time in Visual Studio</span></span>| |  
|<span data-ttu-id="22c9d-151">TA1 （技術通知） 的產生和重新調整</span><span class="sxs-lookup"><span data-stu-id="22c9d-151">TA1    (Technical ACK) Generation and Reconciliation</span></span>| |  
|<span data-ttu-id="22c9d-152">選用的 EDI 和 XSD 驗證旗標</span><span class="sxs-lookup"><span data-stu-id="22c9d-152">Optional    EDI and XSD Validation flags</span></span>| |  
|<span data-ttu-id="22c9d-153">文件格式/定義 GS 層級</span><span class="sxs-lookup"><span data-stu-id="22c9d-153">Document    format/definition at GS level</span></span>| |  
  
## <a name="see-also"></a><span data-ttu-id="22c9d-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22c9d-154">See Also</span></span>  
 <span data-ttu-id="22c9d-155">[EDI 標準支援](../core/edi-standards-support.md) </span><span class="sxs-lookup"><span data-stu-id="22c9d-155">[EDI Standards Support](../core/edi-standards-support.md) </span></span>  
 <span data-ttu-id="22c9d-156">[EDI 文件結構描述支援](../core/edi-document-schema-support.md) </span><span class="sxs-lookup"><span data-stu-id="22c9d-156">[EDI Document Schema Support](../core/edi-document-schema-support.md) </span></span>  
 [<span data-ttu-id="22c9d-157">EDI 字元集支援</span><span class="sxs-lookup"><span data-stu-id="22c9d-157">EDI Character Set Support</span></span>](../core/edi-character-set-support.md)