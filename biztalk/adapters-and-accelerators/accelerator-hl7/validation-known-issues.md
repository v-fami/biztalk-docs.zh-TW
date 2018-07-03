---
title: 驗證的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues, validating
- validating, known issues
ms.assetid: 136596f2-ee0f-4ea9-918c-3608f2ee1be3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73cc1caa3207901780a57e7b1213215217b73326
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010575"
---
# <a name="validation-known-issues"></a><span data-ttu-id="71b0a-102">驗證的已知問題</span><span class="sxs-lookup"><span data-stu-id="71b0a-102">Validation Known Issues</span></span>
<span data-ttu-id="71b0a-103">本節包含可協助您避免驗證錯誤的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="71b0a-103">This section contains useful information that may help you avoid validation errors.</span></span>  
  
## <a name="disabling-xml-validation"></a><span data-ttu-id="71b0a-104">停用的 XML 驗證</span><span class="sxs-lookup"><span data-stu-id="71b0a-104">Disabling XML validation</span></span>  
 <span data-ttu-id="71b0a-105">驗證主體使用者分佈 旗標在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管控制 XML 內文驗證，而且不包含未預期的分隔符號與尾端分隔符號的驗證。</span><span class="sxs-lookup"><span data-stu-id="71b0a-105">The "Validate Body Segments" flag in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer controls the XML body validation and does not include validation of unexpected delimiters and trailing delimiters.</span></span> <span data-ttu-id="71b0a-106">如果訊息沒有適當的分隔符號，訊息無法成功剖析。</span><span class="sxs-lookup"><span data-stu-id="71b0a-106">If a message does not have the proper delimiters, the message cannot be successfully parsed.</span></span> <span data-ttu-id="71b0a-107">如果訊息無法順利剖析，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]無法產生有效的中繼 XML。</span><span class="sxs-lookup"><span data-stu-id="71b0a-107">If a message cannot be successfully parsed, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] cannot generate valid intermediate XML.</span></span> <span data-ttu-id="71b0a-108">停用 [驗證的主體使用者分佈] 旗標會產生下列：</span><span class="sxs-lookup"><span data-stu-id="71b0a-108">Disabling the "Validate Body Segments" flag results in the following:</span></span>  
  
1.  <span data-ttu-id="71b0a-109">空的必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="71b0a-109">Empty required fields.</span></span>  
  
2.  <span data-ttu-id="71b0a-110">未驗證的資料類型。</span><span class="sxs-lookup"><span data-stu-id="71b0a-110">Data types not validated.</span></span>  
  
3.  <span data-ttu-id="71b0a-111">不會驗證區段結構 （不會驗證區段的順序）。</span><span class="sxs-lookup"><span data-stu-id="71b0a-111">Segment structure is not validated (order of segments is not validated).</span></span>  
  
## <a name="v2xml-acks-with-multiple-errors-will-fail-validation"></a><span data-ttu-id="71b0a-112">V2。有多個錯誤的 XML 通知將無法通過驗證</span><span class="sxs-lookup"><span data-stu-id="71b0a-112">V2.XML ACKs with multiple errors will fail validation</span></span>  
 <span data-ttu-id="71b0a-113">如果內送的 V2。XML 訊息包含多個錯誤，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 剖析器可能會產生 V2。XML 通知 (ACK) 與 [錯誤] 欄位中的多個錯誤。</span><span class="sxs-lookup"><span data-stu-id="71b0a-113">If an incoming V2.XML message contains more than one error, the Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) parser may generate a V2.XML acknowledgment (ACK) with more than one error in the error field.</span></span> <span data-ttu-id="71b0a-114">V2。XML 通知將無法通過驗證，因為 HL7 標準可讓您指定剖析器可以報告在 V2 中的一個錯誤。XML 通知錯誤的欄位。</span><span class="sxs-lookup"><span data-stu-id="71b0a-114">Such a V2.XML ACK will fail validation, because the HL7 standard specifies that the parser can report only one error in a V2.XML ACK error field.</span></span>  
  
## <a name="two-parsing-errors-are-logged-when-messages-in-the-batch-inbatch-out-scenario-contain-validation-errors"></a><span data-ttu-id="71b0a-115">兩個剖析錯誤會記錄當批次中的訊息在批次出案例包含驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="71b0a-115">Two parsing errors are logged when messages in the Batch In/Batch Out scenario contain validation errors</span></span>  
 <span data-ttu-id="71b0a-116">當第一個訊息批次中 / 批次出案例 （不含批次標頭中批次處理多個訊息） 包含驗證錯誤，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄在事件記錄檔中的兩個錯誤。</span><span class="sxs-lookup"><span data-stu-id="71b0a-116">When the first message in the Batch In/Batch Out scenario (multiple messages batched without batch headers) contains validation errors, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logs two errors in the Event Log.</span></span> <span data-ttu-id="71b0a-117">第一個錯誤的批次中的第一個訊息並第二個錯誤與訊息的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="71b0a-117">The first error pertains to the first message in the batch, and the second error pertains to the remainder of the messages.</span></span>  
  
## <a name="restrictions-in-validating-field-length"></a><span data-ttu-id="71b0a-118">驗證欄位長度的限制</span><span class="sxs-lookup"><span data-stu-id="71b0a-118">Restrictions in validating field length</span></span>  
 <span data-ttu-id="71b0a-119">HL7 元件和子元件包括複雜資料型別相關聯的欄位。</span><span class="sxs-lookup"><span data-stu-id="71b0a-119">Fields associated with HL7 complex data types are comprised of components and subcomponents.</span></span> <span data-ttu-id="71b0a-120">HL7 規則指定的長度和欄位層級，而不是在元件/子元件層級的選用性。</span><span class="sxs-lookup"><span data-stu-id="71b0a-120">HL7 rules specify the length and optionality at the field level and not at the component/subcomponent level.</span></span> <span data-ttu-id="71b0a-121">比方說在 V2.4，HL7 控管 MSH3 是 HD 的資料型別和 180 個字元的最大長度。</span><span class="sxs-lookup"><span data-stu-id="71b0a-121">For example in V2.4, HL7 governs MSH3 to be of HD data type and 180 characters maximum length.</span></span> <span data-ttu-id="71b0a-122">HD 是 HD1 集現況、 HD2 集為 ST，以及 HD3 設為識別碼的複合資料類型</span><span class="sxs-lookup"><span data-stu-id="71b0a-122">HD is a composite data type with HD1 set as IS, HD2 set as ST, and HD3 set as ID.</span></span> <span data-ttu-id="71b0a-123">欄位長度限制表示三個元件 （包括兩個元件分隔符號） 中的資料應該要小於或等於 180。</span><span class="sxs-lookup"><span data-stu-id="71b0a-123">The field length restriction implies that the data in the three components (including the two component separators) should be less than or equal to 180.</span></span> <span data-ttu-id="71b0a-124">不過，未指定三種資料類型的選用性;這表示所有或部分元件可能存在。</span><span class="sxs-lookup"><span data-stu-id="71b0a-124">However, the optionality of the three data types is not specified; which means that all or some components may exist.</span></span> <span data-ttu-id="71b0a-125">此外，ST 和 IS 的資料類型所定義的使用者，因此[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]無法留意長度散發，跨三個元件，因為它們通常是定義站台。</span><span class="sxs-lookup"><span data-stu-id="71b0a-125">Additionally, data types ST and IS are user defined and therefore [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] cannot be aware of the length distribution across the three components, since these are normally site defined.</span></span>  
  
 <span data-ttu-id="71b0a-126">由於這些和其他的複雜度，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會驗證欄位長度。</span><span class="sxs-lookup"><span data-stu-id="71b0a-126">Due to these and other complications, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not validate the field length.</span></span> <span data-ttu-id="71b0a-127">不過，您可以將長度限制在每個個別元件/子元件 （資料類型的簡單） 使用 「 BizTalk 編輯器中套用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71b0a-127">However, you can apply length restrictions at each individual component/subcomponent (of data type simple) using BizTalk Editor in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="71b0a-128"> 將會驗證這些在處理期間。</span><span class="sxs-lookup"><span data-stu-id="71b0a-128"> will validate these during processing.</span></span>  
  
## <a name="validation-of-batch-and-file-headerstrailers-are-affected-by-enabling-fragmentation"></a><span data-ttu-id="71b0a-129">啟用片段會影響批次和檔案的標頭/結尾的驗證</span><span class="sxs-lookup"><span data-stu-id="71b0a-129">Validation of batch and file headers/trailers are affected by enabling fragmentation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="71b0a-130"> 當 FHS3 欄位包含已啟用的分散程度的合作對象時，不會驗證批次和檔案的標頭/結尾。</span><span class="sxs-lookup"><span data-stu-id="71b0a-130"> does not validate batch and file headers/trailers when the FHS3 field contains a party that has fragmentation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b0a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b0a-131">See Also</span></span>  
 [<span data-ttu-id="71b0a-132">已知問題</span><span class="sxs-lookup"><span data-stu-id="71b0a-132">Known Issues</span></span>](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)