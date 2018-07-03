---
title: 步驟 6： 驗證結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, schemas
- schemas, validating
- validating, schemas
ms.assetid: 58cd8680-d135-485a-9463-e7701202eaf7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94f0ab3ba2d9586aa60817bb261be0660305c820
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005335"
---
# <a name="step-6-validate-the-schemas"></a><span data-ttu-id="cdc20-102">步驟 6： 驗證結構描述</span><span class="sxs-lookup"><span data-stu-id="cdc20-102">Step 6: Validate the Schemas</span></span>
<span data-ttu-id="cdc20-103">在此步驟中，您可以使用 驗證結構描述命令以判斷其中一個結構描述包含的任何內部不一致，或有其他問題，可能會讓其中一個結構描述，使其不用於有效地處理執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="cdc20-103">In this step, you use the validate schema command to determine if either of the schemas contains any internal inconsistencies, or has other issues that might prevent either schema from being used effectively for processing instance messages.</span></span>  
  
### <a name="to-validate-the-schema"></a><span data-ttu-id="cdc20-104">驗證結構描述</span><span class="sxs-lookup"><span data-stu-id="cdc20-104">To validate the schema</span></span>  
  
1. <span data-ttu-id="cdc20-105">在 [方案總管] 中，以滑鼠右鍵按一下**Doorbell.xsd** ，然後按一下**驗證結構描述**。</span><span class="sxs-lookup"><span data-stu-id="cdc20-105">In Solution Explorer, right-click **Doorbell.xsd** and then click **Validate Schema**.</span></span> <span data-ttu-id="cdc20-106">請確定在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="cdc20-106">Ensure that a success message appears in the output window.</span></span>  
  
    <span data-ttu-id="cdc20-107">如果不成功的訊息，請確認您建立**Doorbell.xsd**正確。</span><span class="sxs-lookup"><span data-stu-id="cdc20-107">If a success message does not appear, verify that you created **Doorbell.xsd** properly.</span></span>  
  
2. <span data-ttu-id="cdc20-108">重複步驟 1 **ADT_A04_22_GLO_DEF.xsd**結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="cdc20-108">Repeat step 1 for the **ADT_A04_22_GLO_DEF.xsd** schema file.</span></span> <span data-ttu-id="cdc20-109">請確定在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="cdc20-109">Ensure that a success message appears in the output window.</span></span>  
  
   <span data-ttu-id="cdc20-110">請繼續進行[步驟 7： 簽署和建置專案](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="cdc20-110">Proceed to [Step 7: Sign and Build the Projects](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc20-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdc20-111">See Also</span></span>  
 [<span data-ttu-id="cdc20-112">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="cdc20-112">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)