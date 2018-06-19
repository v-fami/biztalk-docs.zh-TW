---
title: HL7 2.X 組合器中的結構描述判斷 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, assembler
- MSH5
- assembler, schemas
ms.assetid: 464c006e-4fae-4e2a-99ea-157301c0179e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50a430750846ae2567f063f9aa77221bad9c97e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206094"
---
# <a name="schema-determination-in-the-hl7-2x-assembler"></a><span data-ttu-id="af4f0-102">HL7 2.X 組合器中的結構描述判斷</span><span class="sxs-lookup"><span data-stu-id="af4f0-102">Schema Determination in the HL7 2.X Assembler</span></span>
<span data-ttu-id="af4f0-103">當訊息流程中的序列化程式序列化程式， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會使用 MSH5 （目的合作對象） 的訊息，以判斷要在訊息上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="af4f0-103">When a message flows to the serializer, the serializer in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses MSH5 (destination party) of the message to determine the operations to be performed on the message.</span></span> <span data-ttu-id="af4f0-104">這類作業包括：</span><span class="sxs-lookup"><span data-stu-id="af4f0-104">Such operations include:</span></span>  
  
-   <span data-ttu-id="af4f0-105">是否要執行 XML 驗證的主體區段</span><span class="sxs-lookup"><span data-stu-id="af4f0-105">Whether to perform XML validation for body segments</span></span>  
  
-   <span data-ttu-id="af4f0-106">是否要驗證的主體區段的自訂資料型別</span><span class="sxs-lookup"><span data-stu-id="af4f0-106">Whether to validate custom data types for body segments</span></span>  
  
-   <span data-ttu-id="af4f0-107">是否允許尾端分隔符號，在主體中</span><span class="sxs-lookup"><span data-stu-id="af4f0-107">Whether to allow trailing delimiters in the body</span></span>  
  
-   <span data-ttu-id="af4f0-108">序列化程式將使用哪一個結構描述目標命名空間</span><span class="sxs-lookup"><span data-stu-id="af4f0-108">Which schema target namespace the serializer will use</span></span>  
  
-   <span data-ttu-id="af4f0-109">序列化程式是否需要對應的標頭</span><span class="sxs-lookup"><span data-stu-id="af4f0-109">Whether the serializer needs to map the header</span></span>  
  
 <span data-ttu-id="af4f0-110">若要判斷結構描述，序列化程式會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="af4f0-110">To determine the schema, the serializer does the following:</span></span>  
  
-   <span data-ttu-id="af4f0-111">設定目標命名空間 (**Targetns-xdrt.xml**) 為針對目的合作對象設定的命名空間相同的值</span><span class="sxs-lookup"><span data-stu-id="af4f0-111">Sets the target namespace (**TargetNS**) to the same value as the namespace configured for the destination party</span></span>  
  
-   <span data-ttu-id="af4f0-112">擷取**Rootnode**從**BTS。MessageType**升級屬性</span><span class="sxs-lookup"><span data-stu-id="af4f0-112">Extracts **Rootnode** from the **BTS.MessageType** promoted property</span></span>  
  
 <span data-ttu-id="af4f0-113">**Doctype**變成**Targetns-xdrt.xml +"#"+ Rootnode**。</span><span class="sxs-lookup"><span data-stu-id="af4f0-113">The **doctype** becomes **TargetNS + "#" + Rootnode**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4f0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af4f0-114">See Also</span></span>  
 <span data-ttu-id="af4f0-115">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="af4f0-115">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="af4f0-116">BTAHL72X 一般檔案處理</span><span class="sxs-lookup"><span data-stu-id="af4f0-116">BTAHL72X Flat File Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)