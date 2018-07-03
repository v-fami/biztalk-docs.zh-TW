---
title: 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types, messages
- messages, data types
ms.assetid: 7a758289-1629-48a0-843d-6f6773bd5ba6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a7b8d75be35be01e9c961d6bd054dcaed6d3aee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984671"
---
# <a name="data-types"></a><span data-ttu-id="2d514-102">資料型別</span><span class="sxs-lookup"><span data-stu-id="2d514-102">Data Types</span></span>
<span data-ttu-id="2d514-103">資料類型規格是重要的工具，進行資料分割 HL7 標準的複雜度，並請務必了解 HL7 欄位的資料內容。</span><span class="sxs-lookup"><span data-stu-id="2d514-103">The data type specification is an important tool for partitioning the complexity of the HL7 standard, and is critical to understanding the data contents of an HL7 field.</span></span> <span data-ttu-id="2d514-104">某些資料類型是簡單，而且包含只有一個元件，而且部分包含許多元件和子元件。</span><span class="sxs-lookup"><span data-stu-id="2d514-104">Some data types are simple and contain only one component, and some contain many components and subcomponents.</span></span> <span data-ttu-id="2d514-105">例如，PID.5 病患名稱有輸入 XPN 版本 2.4 中的資料。</span><span class="sxs-lookup"><span data-stu-id="2d514-105">For example, PID.5 Patient Name has the data type XPN in Version 2.4.</span></span> <span data-ttu-id="2d514-106">此資料類型支援常見量度的英文語言名稱，比方說，姓氏、 名字、 中間名，以及後置詞，前置詞、 名稱型別程式碼和名稱的有效性 （日期） 範圍。</span><span class="sxs-lookup"><span data-stu-id="2d514-106">This data type supports the common subdivisions of an English language name, for example, surname, first name, middle name, as well as suffix, prefix, name type code, and name validity (date) range.</span></span>  
  
 <span data-ttu-id="2d514-107">在新的 HL7 版本中，您可以新增，但不是會移除資料型別。</span><span class="sxs-lookup"><span data-stu-id="2d514-107">In new HL7 versions, you can add but not remove data types.</span></span> <span data-ttu-id="2d514-108">如果您將內容加入的資料類型，藉由新增新的元件或子元件，您只可以將它們在其中內嵌結構的結尾。</span><span class="sxs-lookup"><span data-stu-id="2d514-108">If you add content to a data type, by adding new components or subcomponents, you can only add them at the end of the structure within which they are nested.</span></span> <span data-ttu-id="2d514-109">在某些情況下，HL7 組織會合併現有的資料類型，以形成新的。</span><span class="sxs-lookup"><span data-stu-id="2d514-109">In some cases, the HL7 organization merged existing data types to form new ones.</span></span> <span data-ttu-id="2d514-110">這會導致需要支援先前在原始的資料類型的子元件的項目。</span><span class="sxs-lookup"><span data-stu-id="2d514-110">This led to the need to support items that were formerly subcomponents within the original data types.</span></span>  
  
 <span data-ttu-id="2d514-111">Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：</span><span class="sxs-lookup"><span data-stu-id="2d514-111">The following functions of Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2d514-112"> 支援標準的資料類型從 V2.1 所有 HL7 版本上。</span><span class="sxs-lookup"><span data-stu-id="2d514-112"> supports standard data types for all HL7 versions from V2.1 on.</span></span>  
  
- <span data-ttu-id="2d514-113">您可以限制資料型別在適當時開發介面。</span><span class="sxs-lookup"><span data-stu-id="2d514-113">You can restrict data types where appropriate when developing interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d514-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="2d514-114">In This Section</span></span>  
  
-   [<span data-ttu-id="2d514-115">資料類型識別碼 HL7 2.1</span><span class="sxs-lookup"><span data-stu-id="2d514-115">Data Type ID in HL7 2.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/data-type-id-in-hl7.md)