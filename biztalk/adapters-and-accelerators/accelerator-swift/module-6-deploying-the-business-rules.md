---
title: 模組 6： 部署商務規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorial, deploying business rules
- deploying, business rules
- business rules
ms.assetid: e8fb8993-3450-4795-80fd-ff28bff8fe97
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 389d8038b5a216f90d85399eeefaebde86284c71
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972839"
---
# <a name="module-6-deploying-the-business-rules"></a><span data-ttu-id="1d086-102">模組 6： 部署商務規則</span><span class="sxs-lookup"><span data-stu-id="1d086-102">Module 6: Deploying the Business Rules</span></span>
<span data-ttu-id="1d086-103">在這個模組中，您可以部署 商務規則，確認您的安裝記錄檔，並確認您使用 「 商務規則編輯器 」 工具的部署。</span><span class="sxs-lookup"><span data-stu-id="1d086-103">In this module, you deploy the business rules, confirm your installation log, and confirm your deployment using the Business Rule Composer tool.</span></span>  
  
 <span data-ttu-id="1d086-104">您可以使用商務規則來確保 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]協會全球 Interbank 財務電信 (SWIFT) 標準中所定義的訊息遵守格式規格欄位規格，驗證的網路規則。</span><span class="sxs-lookup"><span data-stu-id="1d086-104">You use business rules to ensure that Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] messages adhere to format specifications, field specifications, and network validated rules as defined in the Society for Worldwide Interbank Financial Telecommunication (SWIFT) standards.</span></span> <span data-ttu-id="1d086-105">格式規格屬於整個訊息的結構和欄位規格會詳細說明每個訊息中的欄位。</span><span class="sxs-lookup"><span data-stu-id="1d086-105">Format specifications pertain to the structure of the message as a whole and field specifications detail each field in the message.</span></span> <span data-ttu-id="1d086-106">網路驗證規則套用到欄位交互驗證，而且在本質上複雜。</span><span class="sxs-lookup"><span data-stu-id="1d086-106">Network validated rules apply to cross-field validations and are complex in nature.</span></span>  
  
 <span data-ttu-id="1d086-107">A4SWIFT 提供每個訊息的 XSD 結構描述規格。</span><span class="sxs-lookup"><span data-stu-id="1d086-107">A4SWIFT provides XSD schema specifications for each message.</span></span> <span data-ttu-id="1d086-108">A4SWIFT 反組譯工具 (DASM) 和組譯工具 (ASM) 使用的結構描述來剖析或序列化及驗證原生的一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="1d086-108">The A4SWIFT disassembler (DASM) and assembler (ASM) use the schema to parse or serialize and validate native flat-file messages.</span></span> <span data-ttu-id="1d086-109">驗證受限於格式規格和欄位規格的結構描述編碼。</span><span class="sxs-lookup"><span data-stu-id="1d086-109">Validations are limited to format specifications and field specifications that the schema encodes.</span></span> <span data-ttu-id="1d086-110">不過，您無法將某些格式的編碼，並欄位在結構描述中的相關的規則。</span><span class="sxs-lookup"><span data-stu-id="1d086-110">However, you cannot encode some formats and field related rules within the schema.</span></span>  
  
 <span data-ttu-id="1d086-111">A4SWIFT 也包含一組遵循 SWIFT 標準版指南 (SRG) 的商務規則。</span><span class="sxs-lookup"><span data-stu-id="1d086-111">A4SWIFT also includes a set of business rules that follow the SWIFT Standards Release Guides (SRG).</span></span> <span data-ttu-id="1d086-112">BizTalk Server 商務規則引擎 (BRE) 呼叫 A4SWIFT 原則，並強制執行 A4SWIFT 的商務規則。</span><span class="sxs-lookup"><span data-stu-id="1d086-112">The BizTalk Server Business Rule Engine (BRE) calls the A4SWIFT policies and enforces the A4SWIFT business rules.</span></span>  
  
 <span data-ttu-id="1d086-113">這些商務規則會包含因為格式和欄位，以及已超出的結構描述的自然功能的網路驗證規則相關的複雜驗證項目。</span><span class="sxs-lookup"><span data-stu-id="1d086-113">These business rules are included due to the complex validations relating to format and fields, and network-validated rules that are beyond the natural capability of the schema.</span></span> <span data-ttu-id="1d086-114">SWIFT DASM 或 ASM 元件接收或傳送管線內呼叫 BRE。</span><span class="sxs-lookup"><span data-stu-id="1d086-114">The SWIFT DASM or ASM components within a receive or send pipeline call the BRE.</span></span>  
  
 <span data-ttu-id="1d086-115">您開啟或關閉驗證變更**BREValidation** DASM 您管線內的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d086-115">You turn the validations on or off by changing the **BREValidation** property for the DASM within your pipeline.</span></span>  
  
 <span data-ttu-id="1d086-116">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="1d086-116">This section contains:</span></span>  
  
-   [<span data-ttu-id="1d086-117">課程 1：部署相關商務規則</span><span class="sxs-lookup"><span data-stu-id="1d086-117">Lesson 1: Deploying the Related Business Rules</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)  
  
-   [<span data-ttu-id="1d086-118">課程 2：使用商務規則編輯器工具確認部署</span><span class="sxs-lookup"><span data-stu-id="1d086-118">Lesson 2: Confirming the Deployment Using the Business Rule Composer Tool</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)