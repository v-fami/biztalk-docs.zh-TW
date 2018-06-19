---
title: 詞彙 |Microsoft 文件
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
ms.openlocfilehash: 5c77247054914097131103fe33d86fc78551d8cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206654"
---
# <a name="vocabulary"></a><span data-ttu-id="41fb0-102">詞彙</span><span class="sxs-lookup"><span data-stu-id="41fb0-102">Vocabulary</span></span>
<span data-ttu-id="41fb0-103">HL7 版本 2 提供的自動程式碼項目，詞彙的部分支援，但大部分的情況下，提供傳輸繪製從程式碼撰寫的本機系統的程式碼的結構。</span><span class="sxs-lookup"><span data-stu-id="41fb0-103">HL7 Version 2 provides some support for vocabularies for coded elements, but for the most part, provides a structure that transmits codes drawn from local coding systems.</span></span>  
  
 <span data-ttu-id="41fb0-104">HL7 版本 2 在區段資料表連結自動程式化的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="41fb0-104">In HL7 Version 2, a segment table links all coded fields.</span></span> <span data-ttu-id="41fb0-105">區段包含的欄位使用之資料表的識別項。</span><span class="sxs-lookup"><span data-stu-id="41fb0-105">The segment table includes the identifier of the table that the field uses.</span></span> <span data-ttu-id="41fb0-106">有三種類型的資料表： HL7 定義外部定義，以及使用者定義。</span><span class="sxs-lookup"><span data-stu-id="41fb0-106">There are three types of tables: HL7 defined, externally defined, and user-defined.</span></span> <span data-ttu-id="41fb0-107">在某些情況下，標準提供使用者定義資料表的範例值。</span><span class="sxs-lookup"><span data-stu-id="41fb0-107">In some cases, the standard supplies example values for a user-defined table.</span></span> <span data-ttu-id="41fb0-108">您應該將這些視為與標準 HL7 標示為它們。</span><span class="sxs-lookup"><span data-stu-id="41fb0-108">You should treat these as the HL7 standard has labeled them.</span></span>  
  
 <span data-ttu-id="41fb0-109">在新的版本中，您無法移除 HL7 定義資料表中的程式碼，但您可以加入新的代碼。</span><span class="sxs-lookup"><span data-stu-id="41fb0-109">In new versions, you cannot remove codes from HL7 defined tables, but you can add new codes.</span></span> <span data-ttu-id="41fb0-110">您可以變更在使用者定義的資料表。</span><span class="sxs-lookup"><span data-stu-id="41fb0-110">You can change user-defined tables at will.</span></span>  
  
 <span data-ttu-id="41fb0-111">下列函式的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：</span><span class="sxs-lookup"><span data-stu-id="41fb0-111">The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   <span data-ttu-id="41fb0-112">您可以使用所有 HL7 定義的資料表。</span><span class="sxs-lookup"><span data-stu-id="41fb0-112">You can use all of the HL7 defined tables.</span></span>  
  
-   <span data-ttu-id="41fb0-113">您可以匯入和使用外部定義 LOINC ICD9 等程式碼集。</span><span class="sxs-lookup"><span data-stu-id="41fb0-113">You can import and use externally defined code sets such as ICD9 and LOINC.</span></span>  
  
-   <span data-ttu-id="41fb0-114">您可以提供使用者定義資料表的值。</span><span class="sxs-lookup"><span data-stu-id="41fb0-114">You can provide the values for user-defined tables.</span></span>  
  
-   <span data-ttu-id="41fb0-115">在支援的系統組不同的程式碼的情況下，您可以設定允許不同的程式碼集交互操作的對應。</span><span class="sxs-lookup"><span data-stu-id="41fb0-115">In cases where systems are supporting different sets of codes, you can set up mappings that allow disparate code sets to interoperate.</span></span> <span data-ttu-id="41fb0-116">如有必要，您可以定義多個執行個體的單一使用者定義資料表，以便與中繼的對應。</span><span class="sxs-lookup"><span data-stu-id="41fb0-116">If necessary, you can define multiple instances of a single user-defined table to go along with the intermediary mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41fb0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41fb0-117">See Also</span></span>  
 <span data-ttu-id="41fb0-118">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="41fb0-118">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="41fb0-119">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="41fb0-119">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="41fb0-120">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="41fb0-120">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)