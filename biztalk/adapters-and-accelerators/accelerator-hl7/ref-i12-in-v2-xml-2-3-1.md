---
title: V2 中 REF_I12。XML 2.3.1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- REF_I12 schema
ms.assetid: de30b128-3c70-41ea-849f-16f4c6d55430
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78633da4d6dd09f5ceebb3ad4717e3338f23b542
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206014"
---
# <a name="refi12-in-v2xml-231"></a><span data-ttu-id="906a4-102">V2 中 REF_I12。XML 2.3.1</span><span class="sxs-lookup"><span data-stu-id="906a4-102">REF_I12 in V2.XML 2.3.1</span></span>
<span data-ttu-id="906a4-103">您必須手動變更 v2 REF_I12 結構描述中的下列程式碼。XML 2.3.1 之後執行 Update2XMLSchema 工具：</span><span class="sxs-lookup"><span data-stu-id="906a4-103">You must manually change the following code in the REF_I12 schema in V2.XML 2.3.1 after running the Update2XMLSchema tool:</span></span>  
  
```  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
```  
  
 <span data-ttu-id="906a4-104">您必須以下列程式碼，取代上述程式碼，才能修正的多個項目所造成的模稜兩可**REF**項目定義：</span><span class="sxs-lookup"><span data-stu-id="906a4-104">You must replace the above code with the following, in order to fix the ambiguity caused by multiple occurrences of the **REF** element definition:</span></span>  
  
```  
<xsd:element minOccurs="0" maxOccurs="2" ref="REF_I12.PATIENT_VISIT" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="906a4-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="906a4-105">See Also</span></span>  
 <span data-ttu-id="906a4-106">[必要的手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span><span class="sxs-lookup"><span data-stu-id="906a4-106">[Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span></span>  
 [<span data-ttu-id="906a4-107">公用程式</span><span class="sxs-lookup"><span data-stu-id="906a4-107">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)