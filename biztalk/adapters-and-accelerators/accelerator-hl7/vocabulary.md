---
title: 詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, vocabulary
- vocabularies
ms.assetid: c5df05dd-4af8-4e48-8509-e692b04adf3c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e72b51e327581c0a17f18582b0511218b556a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979031"
---
# <a name="vocabulary"></a><span data-ttu-id="9ea10-102">詞彙</span><span class="sxs-lookup"><span data-stu-id="9ea10-102">Vocabulary</span></span>
<span data-ttu-id="9ea10-103">HL7 第 2 版提供詞彙的自動程式化項目，某些支援，但大部分的情況下，提供傳輸取自本機程式碼撰寫的系統程式碼的結構。</span><span class="sxs-lookup"><span data-stu-id="9ea10-103">HL7 Version 2 provides some support for vocabularies for coded elements, but for the most part, provides a structure that transmits codes drawn from local coding systems.</span></span>  
  
 <span data-ttu-id="9ea10-104">HL7 版本 2，在分割資料表會連結所有硬式編碼的欄位。</span><span class="sxs-lookup"><span data-stu-id="9ea10-104">In HL7 Version 2, a segment table links all coded fields.</span></span> <span data-ttu-id="9ea10-105">區段表格中包含之資料表的欄位會使用的識別項。</span><span class="sxs-lookup"><span data-stu-id="9ea10-105">The segment table includes the identifier of the table that the field uses.</span></span> <span data-ttu-id="9ea10-106">有三種類型的資料表： HL7 定義外部定義，以及使用者定義。</span><span class="sxs-lookup"><span data-stu-id="9ea10-106">There are three types of tables: HL7 defined, externally defined, and user-defined.</span></span> <span data-ttu-id="9ea10-107">在某些情況下，標準會提供使用者定義資料表的範例值。</span><span class="sxs-lookup"><span data-stu-id="9ea10-107">In some cases, the standard supplies example values for a user-defined table.</span></span> <span data-ttu-id="9ea10-108">您應該將這些視為與 HL7 標準標記它們。</span><span class="sxs-lookup"><span data-stu-id="9ea10-108">You should treat these as the HL7 standard has labeled them.</span></span>  
  
 <span data-ttu-id="9ea10-109">在新的版本中，您無法移除 HL7 定義資料表中的程式碼，但您可以加入新的代碼。</span><span class="sxs-lookup"><span data-stu-id="9ea10-109">In new versions, you cannot remove codes from HL7 defined tables, but you can add new codes.</span></span> <span data-ttu-id="9ea10-110">您可以變更將會在使用者定義的資料表。</span><span class="sxs-lookup"><span data-stu-id="9ea10-110">You can change user-defined tables at will.</span></span>  
  
 <span data-ttu-id="9ea10-111">Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：</span><span class="sxs-lookup"><span data-stu-id="9ea10-111">The following functions of Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   <span data-ttu-id="9ea10-112">您可以使用所有 HL7 定義的資料表。</span><span class="sxs-lookup"><span data-stu-id="9ea10-112">You can use all of the HL7 defined tables.</span></span>  
  
-   <span data-ttu-id="9ea10-113">您可以匯入和使用外部定義 LOINC ICD9 等的程式碼集。</span><span class="sxs-lookup"><span data-stu-id="9ea10-113">You can import and use externally defined code sets such as ICD9 and LOINC.</span></span>  
  
-   <span data-ttu-id="9ea10-114">您可以在使用者定義資料表的提供值。</span><span class="sxs-lookup"><span data-stu-id="9ea10-114">You can provide the values for user-defined tables.</span></span>  
  
-   <span data-ttu-id="9ea10-115">在支援系統不同的程式碼的情況下，您可以設定允許不同的程式碼集互相的對應。</span><span class="sxs-lookup"><span data-stu-id="9ea10-115">In cases where systems are supporting different sets of codes, you can set up mappings that allow disparate code sets to interoperate.</span></span> <span data-ttu-id="9ea10-116">如有必要，您可以定義多個單一使用者定義資料表，來搭配中繼對應執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ea10-116">If necessary, you can define multiple instances of a single user-defined table to go along with the intermediary mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea10-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ea10-117">See Also</span></span>  
 <span data-ttu-id="9ea10-118">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="9ea10-118">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="9ea10-119">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="9ea10-119">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="9ea10-120">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="9ea10-120">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)