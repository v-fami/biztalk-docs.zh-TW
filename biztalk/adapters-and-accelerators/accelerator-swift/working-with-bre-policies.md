---
title: "使用 BRE 原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE policies, about BRE policies
- BRE policies
ms.assetid: 4470f2b3-6891-46d7-9ba1-848f90d0767d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624af2a9c05e1a419acac66eeb6a1aea8d29d695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-bre-policies"></a><span data-ttu-id="20584-102">使用 BRE 原則</span><span class="sxs-lookup"><span data-stu-id="20584-102">Working with BRE Policies</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="20584-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]驗證 SWIFT 訊息所使用商務規則引擎 (BRE) 原則中所述*SWIFT 參考指南*。</span><span class="sxs-lookup"><span data-stu-id="20584-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] validates SWIFT messages by using Business Rule Engine (BRE) polices, as described in the *SWIFT Reference Guide*.</span></span> <span data-ttu-id="20584-104">這些原則包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="20584-104">These policies include the following:</span></span>  
  
-   <span data-ttu-id="20584-105">格式化</span><span class="sxs-lookup"><span data-stu-id="20584-105">Formatting</span></span>  
  
-   <span data-ttu-id="20584-106">數值範圍</span><span class="sxs-lookup"><span data-stu-id="20584-106">Value range</span></span>  
  
-   <span data-ttu-id="20584-107">有效的清單項目</span><span class="sxs-lookup"><span data-stu-id="20584-107">Valid list entries</span></span>  
  
-   <span data-ttu-id="20584-108">網路規則與對應的錯誤代碼</span><span class="sxs-lookup"><span data-stu-id="20584-108">Network rules with corresponding error codes</span></span>  
  
-   <span data-ttu-id="20584-109">使用規則可從訊息內容驗證</span><span class="sxs-lookup"><span data-stu-id="20584-109">Usage rules that can be validated from the message content</span></span>  
  
 <span data-ttu-id="20584-110">這些原則不會包含不是依存於訊息內容或任何跨訊息驗證的一般作法。</span><span class="sxs-lookup"><span data-stu-id="20584-110">These policies do not include general practices that are not dependent on the message content, or any cross-message validations.</span></span>  
  
 <span data-ttu-id="20584-111">基本欄位選用性和基數，實作格式化參考 SWIFT 基底 Types.xsd 結構描述的訊息結構描述時，會實作訊息 （和標頭和結尾） 的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="20584-111">The XSD schema for the message (and header and trailer) implements basic field optionality and cardinality, while the message schema that implements formatting references the SWIFT Base Types.xsd schema.</span></span> <span data-ttu-id="20584-112">每個訊息類型的兩個特定的原則定義與每個訊息相關聯的規則：</span><span class="sxs-lookup"><span data-stu-id="20584-112">Two specific policies for each message type define the rules associated with each message:</span></span>  
  
-   <span data-ttu-id="20584-113">主機原則 (MT*xxx*_Master_Policy.xml)</span><span class="sxs-lookup"><span data-stu-id="20584-113">Master policy (MT*xxx*_Master_Policy.xml)</span></span>  
  
-   <span data-ttu-id="20584-114">驗證原則 (MT*xxx*_Validation_Policy.xml)</span><span class="sxs-lookup"><span data-stu-id="20584-114">Validation policy (MT*xxx*_Validation_Policy.xml)</span></span>  
  
 <span data-ttu-id="20584-115">每個訊息類型的主要原則會叫用套用至該訊息類型的特定原則。</span><span class="sxs-lookup"><span data-stu-id="20584-115">The master policy for each message type invokes the specific policies that apply to that message type.</span></span> <span data-ttu-id="20584-116">這些特定的原則包含特殊欄位會檢查該一般函式實作、 網路規則和使用規則。</span><span class="sxs-lookup"><span data-stu-id="20584-116">These specific policies include special field checks that common functions implement, network rules, and usage rules.</span></span> <span data-ttu-id="20584-117">訊息的主要原則是第一個原則，該訊息執行。</span><span class="sxs-lookup"><span data-stu-id="20584-117">The master policy for the message is the first policy run for that message.</span></span> <span data-ttu-id="20584-118">原則的清單包含訊息類型的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="20584-118">The list of policies includes the validation policy for the message type.</span></span> <span data-ttu-id="20584-119">每個主要原則已建構 [如果這個訊息類型，然後執行原則的清單]。</span><span class="sxs-lookup"><span data-stu-id="20584-119">Each master policy has the construct "if this message type, then run the list of policies".</span></span>  
  
 <span data-ttu-id="20584-120">每個訊息類型的驗證原則會列出其他外部的規則實作，例如欄位碼的單一欄位檢查，或使用欄位的特定詞彙。</span><span class="sxs-lookup"><span data-stu-id="20584-120">The validation policy for each message type lists the single-field checks that other external rules implement, such as field codes, or uses a specific vocabulary for the field.</span></span> <span data-ttu-id="20584-121">這些個別規則通通常在兩個或多個訊息，因為它們是特定的欄位。</span><span class="sxs-lookup"><span data-stu-id="20584-121">These individual rules are generally common across two or more messages, because they are field-specific.</span></span> <span data-ttu-id="20584-122">沒有程式碼，BRE 詞彙，A4SWIFT_Codelists 提供允許的欄位值。</span><span class="sxs-lookup"><span data-stu-id="20584-122">The A4SWIFT_Codelists in the BRE vocabulary, not programming code, provide the allowed field values.</span></span>  
  
 <span data-ttu-id="20584-123">*SWIFT 參考指南*分別實作每個網路規則。</span><span class="sxs-lookup"><span data-stu-id="20584-123">The *SWIFT Reference Guide* implements each of the network rules independently.</span></span> <span data-ttu-id="20584-124">每個網路規則說明組訊息類型*SWIFT 參考指南*定義。</span><span class="sxs-lookup"><span data-stu-id="20584-124">Each network rule addresses the set of message types that the *SWIFT Reference Guide* defines.</span></span>  
  
 <span data-ttu-id="20584-125">A4SWIFT 安裝 A4SWIFT 安裝時，不會安裝規則。</span><span class="sxs-lookup"><span data-stu-id="20584-125">A4SWIFT Setup does not install rules when it installs A4SWIFT.</span></span> <span data-ttu-id="20584-126">您選取的結構描述，並建置並部署組件之後，您可以使用 BRE 部署公用程式來選取和部署的結構描述設定適當的規則。</span><span class="sxs-lookup"><span data-stu-id="20584-126">After you select the schemas, and build and deploy an assembly, you can use the BRE Deployment Utility to select and deploy the appropriate rules for the schema set.</span></span> <span data-ttu-id="20584-127">若要部署選取之訊息的規則，執行此公用程式並選取相關的組件。</span><span class="sxs-lookup"><span data-stu-id="20584-127">To deploy the rules for the selected messages, run the utility and select the relevant assemblies.</span></span> <span data-ttu-id="20584-128">此工具會選取對應的主要原則、 驗證原則和任何參考的網路或其他規則。</span><span class="sxs-lookup"><span data-stu-id="20584-128">The tool selects the corresponding master policies, validation policies, and any referenced network or other rules.</span></span>  
  
 <span data-ttu-id="20584-129">A4SWIFT 關聯 A4SWIFT 規則的兩種類型的詞彙。</span><span class="sxs-lookup"><span data-stu-id="20584-129">A4SWIFT associates two types of vocabularies with A4SWIFT rules.</span></span> <span data-ttu-id="20584-130">第一個詞彙是 A4SWIFT_Codelist，其中包含各種不同的程式碼清單值。</span><span class="sxs-lookup"><span data-stu-id="20584-130">The first vocabulary is A4SWIFT_Codelist, which contains the various code-list values.</span></span> <span data-ttu-id="20584-131">第二個詞彙是 A4SWIFT_Functions。</span><span class="sxs-lookup"><span data-stu-id="20584-131">The second vocabulary is A4SWIFT_Functions.</span></span> <span data-ttu-id="20584-132">這些詞彙是[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]邏輯驗證和計算的類別。</span><span class="sxs-lookup"><span data-stu-id="20584-132">These vocabularies are [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] classes for logic validations and calculations.</span></span>  
  
 <span data-ttu-id="20584-133">您可以將 BRE 驗證組態參數設定為 true，以叫用 A4SWIFT 解譯器在接收管線中，規則。</span><span class="sxs-lookup"><span data-stu-id="20584-133">You can invoke the rules by the A4SWIFT disassembler in a receive pipeline, by setting the BRE validation configuration parameter to true.</span></span> <span data-ttu-id="20584-134">您也可以叫用從協調流程的規則。</span><span class="sxs-lookup"><span data-stu-id="20584-134">You can also invoke the rules from an orchestration.</span></span> <span data-ttu-id="20584-135">您無法叫用由 A4SWIFT 組譯工具 (ASM) 的規則。</span><span class="sxs-lookup"><span data-stu-id="20584-135">You cannot invoke the rules by the A4SWIFT assembler (ASM).</span></span> <span data-ttu-id="20584-136">您必須使用協調流程或接收管線，來驗證針對結構描述的執行個體，並叫用規則。</span><span class="sxs-lookup"><span data-stu-id="20584-136">You must use an orchestration or receive pipeline to validate the instance against the schema and invoke the rules.</span></span>  
  
 <span data-ttu-id="20584-137">如果訊息無法結構描述驗證或商務規則，A4SWIFT 會準備包含描述發現之錯誤的錯誤集合和表示錯誤中的欄位或訊息中發生錯誤的位置。</span><span class="sxs-lookup"><span data-stu-id="20584-137">If a message fails either schema validation or a business rule, A4SWIFT prepares an error collection that contains a description of the errors found and an indication of the field in error or the position in the message where the error occurred.</span></span> <span data-ttu-id="20584-138">如需詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="20584-138">For more information, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span></span>  
  
 <span data-ttu-id="20584-139">您可以加入其他規則 A4SWIFT 提供的集合。</span><span class="sxs-lookup"><span data-stu-id="20584-139">You can add additional rules to the set that A4SWIFT provides.</span></span> <span data-ttu-id="20584-140">比方說，如果您採用市場作法群組規則，會影響一組新的訊息時，您可以實作包含一或多個新的驗證，視需要的主要原則的新版本。</span><span class="sxs-lookup"><span data-stu-id="20584-140">For example, if you adopt a market practice group rule that affects a new set of messages, you can implement a new version of the master policy that includes one or more new validations, as required.</span></span> <span data-ttu-id="20584-141">同樣地，如果您強制執行額外的單一欄位檢查，您可以將這些檢查加入訊息驗證原則的新版本。</span><span class="sxs-lookup"><span data-stu-id="20584-141">Similarly, if you impose additional single-field checks, you can add these checks to a new version of the message validation policy.</span></span> <span data-ttu-id="20584-142">您可以實作新的驗證為新的規則或詞彙函式。</span><span class="sxs-lookup"><span data-stu-id="20584-142">You can implement the new validation as a new rule or as a vocabulary function.</span></span>  
  
 <span data-ttu-id="20584-143">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="20584-143">This section contains:</span></span>  
  
-   [<span data-ttu-id="20584-144">啟用驗證的銀行識別項代碼</span><span class="sxs-lookup"><span data-stu-id="20584-144">Enabling Validation of Bank Identifier Codes</span></span>](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)  
  
-   [<span data-ttu-id="20584-145">管理 Bicplus 資料表 A4SWIFT 資料庫中</span><span class="sxs-lookup"><span data-stu-id="20584-145">Managing the Bicplus Table in the A4SWIFT Database</span></span>](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)  
  
-   [<span data-ttu-id="20584-146">支援前置 0 量欄位驗證</span><span class="sxs-lookup"><span data-stu-id="20584-146">Supporting Leading Zeros in Amount Field Validations</span></span>](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md)  
  
-   [<span data-ttu-id="20584-147">設定位移量驗證</span><span class="sxs-lookup"><span data-stu-id="20584-147">Setting Offsets for Amount Validation</span></span>](../../adapters-and-accelerators/accelerator-swift/setting-offsets-for-amount-validation.md)  
  
-   [<span data-ttu-id="20584-148">移除的使用方式規則驗證</span><span class="sxs-lookup"><span data-stu-id="20584-148">Removing Usage Rule Validation</span></span>](../../adapters-and-accelerators/accelerator-swift/removing-usage-rule-validation.md)