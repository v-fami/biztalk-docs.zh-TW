---
title: BizTalk Server 中的 HIPAA 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ad8c64-6375-4364-80ce-440db943c222
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7817e3b69edd0a34c13b92128f7ddba0f28a5586
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014759"
---
# <a name="hipaa-support-in-biztalk-server"></a><span data-ttu-id="107f1-102">BizTalk Server 中的 HIPAA 支援</span><span class="sxs-lookup"><span data-stu-id="107f1-102">HIPAA Support in BizTalk Server</span></span>
<span data-ttu-id="107f1-103">本主題提供 HIPAA 和 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 如何支援 HIPAA 的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="107f1-103">This topic provides a brief overview of HIPAA and how [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] supports HIPAA.</span></span>  
  
## <a name="introduction-to-hipaa"></a><span data-ttu-id="107f1-104">HIPAA 簡介</span><span class="sxs-lookup"><span data-stu-id="107f1-104">Introduction to HIPAA</span></span>  
 <span data-ttu-id="107f1-105">根據 1996 年的健康保險流通與責任法案 (HIPAA) 規定，受規範的實體在透過電子方式執行交易 (如理賠、匯款、合格性、理賠狀態要求與回應等等) 時，必須達到所規定的標準。</span><span class="sxs-lookup"><span data-stu-id="107f1-105">The Health Insurance Portability and Accountability Act of 1996 (HIPAA) requires covered entities to use mandated standards when they electronically conduct transactions such as claims, remittance, eligibility, claims status requests and responses, and others.</span></span> <span data-ttu-id="107f1-106">HIPAA 下規範的實體包括健保計畫、票據交換所與大部分的醫療保健業者。</span><span class="sxs-lookup"><span data-stu-id="107f1-106">Covered entities under HIPAA are health plans, clearing houses, and most health care providers.</span></span>  
  
## <a name="hipaa-support-in-biztalk-server"></a><span data-ttu-id="107f1-107">BizTalk Server 中的 HIPAA 支援</span><span class="sxs-lookup"><span data-stu-id="107f1-107">HIPAA support in BizTalk Server</span></span>  
 <span data-ttu-id="107f1-108">Microsoft 一向致力於協助醫療保健相關組織改善醫療保健服務的提供與財務情況。</span><span class="sxs-lookup"><span data-stu-id="107f1-108">Microsoft is committed to helping health care and allied organizations improve the way health care is delivered and financed.</span></span> <span data-ttu-id="107f1-109">Microsoft 矢志要降低這些組織為符合 HIPAA 法規所需花費的時間與金錢。</span><span class="sxs-lookup"><span data-stu-id="107f1-109">Microsoft intends to reduce the amount of time and money that organizations must spend complying with HIPAA regulations.</span></span>  
  
 <span data-ttu-id="107f1-110">組織面臨需要綜合各種醫療保健系統來建立自動化商務程序的挑戰，但是有了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，他們將能克服這項挑戰。</span><span class="sxs-lookup"><span data-stu-id="107f1-110">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] helps organizations meet the challenges of creating automated business processes that connect and interoperate across diverse healthcare systems.</span></span> <span data-ttu-id="107f1-111">受 HIPAA 規範的組織可使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能，來開發、實作及整合既與交易相容、又符合聯邦法律的解決方案。</span><span class="sxs-lookup"><span data-stu-id="107f1-111">Organizations affected by HIPAA can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]’s capabilities to help in developing, implementing, and integrating transaction-compliant solutions which also comply with federal law.</span></span>  
  
[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="107f1-112"> 所包含的原生功能可提供 HIPAA 的支援。</span><span class="sxs-lookup"><span data-stu-id="107f1-112"> includes native functionality providing support for HIPAA.</span></span> <span data-ttu-id="107f1-113">這項功能不是產品的增益集 (例如配接器或加速器)，</span><span class="sxs-lookup"><span data-stu-id="107f1-113">It is not an add-in to the product, such as an adapter or an accelerator.</span></span> <span data-ttu-id="107f1-114">它已經內建於產品中。</span><span class="sxs-lookup"><span data-stu-id="107f1-114">It is built into the product.</span></span> [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="107f1-115"> 所包含的 EDI 元件與功能，不僅能協助組織符合 HIPAA 法規，還能夠真正將 HIPAA 的精髓融入商務程序，以建立管理縝密、講求數據的商務程序。</span><span class="sxs-lookup"><span data-stu-id="107f1-115"> includes the EDI components and capabilities that are required to both comply with the HIPAA mandates and to also embrace HIPAA as a well-managed and measured business process.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="107f1-116"> 支援 HIPAA 5010 和 4010 版。</span><span class="sxs-lookup"><span data-stu-id="107f1-116"> supports HIPAA version 5010 and 4010.</span></span>  
  
## <a name="hipaa-documentation-in-biztalk-server"></a><span data-ttu-id="107f1-117">BizTalk Server 中的 HIPAA 文件</span><span class="sxs-lookup"><span data-stu-id="107f1-117">HIPAA documentation in BizTalk Server</span></span>  
 <span data-ttu-id="107f1-118">主要的 EDI 標準是 X12 (由 ANSI 制定標準，主要用於北美洲) 及 EDIFACT (由聯合國制定標準，主要用於美國以外的地區)。</span><span class="sxs-lookup"><span data-stu-id="107f1-118">The primary EDI standards are X12 (standardized by ANSI and primarily used in North America) and EDIFACT (standardized by the United Nations and primarily used outside the U.S.).</span></span> <span data-ttu-id="107f1-119">HIPAA 是衍生自 X12 的標準。</span><span class="sxs-lookup"><span data-stu-id="107f1-119">HIPAA is a standard derived from X12.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="107f1-120"> 的原生 X12 EDI 功能中已經提供了 HIPAA 支援。</span><span class="sxs-lookup"><span data-stu-id="107f1-120"> provides HIPAA support as part of the native X12 EDI functionality.</span></span> <span data-ttu-id="107f1-121">因此，只要您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中讀到 X12 支援，除非另有指明，否則該支援同樣也適用於 HIPAA 處理。</span><span class="sxs-lookup"><span data-stu-id="107f1-121">Therefore, where you see references to X12 support in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation, this support also applies to HIPAA processing, unless explicitly stated otherwise.</span></span>  
  
 <span data-ttu-id="107f1-122">下列各節中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的 HIPAA 的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="107f1-122">The following sections in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] have specific information about HIPAA.</span></span>  
  
 <span data-ttu-id="107f1-123">**快速入門**</span><span class="sxs-lookup"><span data-stu-id="107f1-123">**Getting Started**</span></span>  
  
- [<span data-ttu-id="107f1-124">HIPAA 交易集</span><span class="sxs-lookup"><span data-stu-id="107f1-124">HIPAA Transaction Sets</span></span>](../core/hipaa-transaction-sets.md)  
  
  <span data-ttu-id="107f1-125">**規劃和架構**</span><span class="sxs-lookup"><span data-stu-id="107f1-125">**Planning and Architecture**</span></span>  
  
- [<span data-ttu-id="107f1-126">HIPAA 文件結構描述版本 5010</span><span class="sxs-lookup"><span data-stu-id="107f1-126">HIPAA Document Schema Version 5010</span></span>](../core/hipaa-document-schema-version-5010.md)  
  
- [<span data-ttu-id="107f1-127">HIPAA 結構描述觸發欄位註解</span><span class="sxs-lookup"><span data-stu-id="107f1-127">HIPAA Schema Trigger Field Annotations</span></span>](../core/hipaa-schema-trigger-field-annotations.md)  
  
- [<span data-ttu-id="107f1-128">分割 HIPAA 子文件</span><span class="sxs-lookup"><span data-stu-id="107f1-128">Splitting HIPAA Subdocuments</span></span>](../core/splitting-hipaa-subdocuments.md)  
  
  <span data-ttu-id="107f1-129">**開發**</span><span class="sxs-lookup"><span data-stu-id="107f1-129">**Development**</span></span>  
  
- [<span data-ttu-id="107f1-130">修改 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="107f1-130">Modifying EDI Schemas</span></span>](../core/modifying-edi-schemas.md) 

- [<span data-ttu-id="107f1-131">在信封結構描述中自訂列舉</span><span class="sxs-lookup"><span data-stu-id="107f1-131">Customizing Enumerations in the Envelope Schema</span></span>](../core/customizing-enumerations-in-the-envelope-schema.md)

- [<span data-ttu-id="107f1-132">設定欄位交互驗證</span><span class="sxs-lookup"><span data-stu-id="107f1-132">Configuring Cross-Field Validation</span></span>](../core/configuring-cross-field-validation.md)

  
 <span data-ttu-id="107f1-133">**疑難排解**</span><span class="sxs-lookup"><span data-stu-id="107f1-133">**Troubleshooting**</span></span>  
  
-   [<span data-ttu-id="107f1-134">EDI 接收處理的已知問題</span><span class="sxs-lookup"><span data-stu-id="107f1-134">Known Issues with EDI Receive Processing</span></span>](../core/known-issues-with-edi-receive-processing.md)  
  
-   [<span data-ttu-id="107f1-135">與 EDI 解決方案搭配使用之 XML 工具的已知問題</span><span class="sxs-lookup"><span data-stu-id="107f1-135">Known Issues with XML Tools Used with EDI Solutions</span></span>](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)  
  
## <a name="more-information-about-hipaa"></a><span data-ttu-id="107f1-136">HIPAA 的相關資訊</span><span class="sxs-lookup"><span data-stu-id="107f1-136">More information about HIPAA</span></span>  
  
-   <span data-ttu-id="107f1-137">如需 American National Standards Institute，Accredited Standards Committee for Electronic Data Interchange，請移至[ASC X12 首頁](http://www.x12.org/)。</span><span class="sxs-lookup"><span data-stu-id="107f1-137">For information about the American National Standards Institute, Accredited Standards Committee for Electronic Data Interchange, go to [ASC X12 home](http://www.x12.org/).</span></span>  
  
-   <span data-ttu-id="107f1-138">如需 x12's Insurance Subcommittee 及其實作的資訊引導 HIPAA 下採用，請移至[Washington Publishing Company's HIPAA EDI 引導](http://www.wpc-edi.com/)。</span><span class="sxs-lookup"><span data-stu-id="107f1-138">For information about X12's Insurance Subcommittee and their implementation guides adopted under HIPAA, go to [Washington Publishing Company's HIPAA EDI guides](http://www.wpc-edi.com/).</span></span>
  
-   <span data-ttu-id="107f1-139">如需 Workgroup for Electronic Data Interchange 資訊，請移至[Workgroup for Electronic Data Interchange 首頁](http://www.wedi.org/)。</span><span class="sxs-lookup"><span data-stu-id="107f1-139">For information about the Workgroup for Electronic Data Interchange, go to [Workgroup for Electronic Data Interchange home page](http://www.wedi.org/).</span></span>