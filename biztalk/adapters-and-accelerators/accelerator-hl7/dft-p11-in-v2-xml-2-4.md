---
title: V2 中 DFT_P11。XML 2.4 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DFT_P11 schema
ms.assetid: 3887a8bb-94df-4a3b-b828-f46013d1abb8
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8142e3b878fbffa782e467d64906076b06320318
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204710"
---
# <a name="dftp11-in-v2xml-24"></a><span data-ttu-id="cbda8-102">V2 中 DFT_P11。XML 2.4</span><span class="sxs-lookup"><span data-stu-id="cbda8-102">DFT_P11 in V2.XML 2.4</span></span>
<span data-ttu-id="cbda8-103">您必須手動變更 v2 DFT_P11 結構描述中的下列程式碼。XML 2.4 之後執行 Update2XMLSchema 工具：</span><span class="sxs-lookup"><span data-stu-id="cbda8-103">You must manually change the following code in the DFT_P11 schema in V2.XML 2.4 after running the Update2XMLSchema tool:</span></span>  
  
```  
<xsd:element ref="ROL" minOccurs="0" maxOccurs="unbounded" />  
<xsd:element ref="PV1" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="PV2" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="ROL" minOccurs="0" maxOccurs="unbounded" />  
```  
  
 <span data-ttu-id="cbda8-104">您必須以下列程式碼，取代上述程式碼，才能修正的多個項目所造成的模稜兩可**ROL**項目定義：</span><span class="sxs-lookup"><span data-stu-id="cbda8-104">You must replace the above code with the following, in order to fix the ambiguity caused by multiple occurrences of the **ROL** element definition:</span></span>  
  
```  
<xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
  <xsd:choice minOccurs="0" maxOccurs="1">  
    <xsd:sequence>  
      <xsd:element minOccurs="1" maxOccurs="1" ref="PV1" />  
      <xsd:element minOccurs="0" maxOccurs="1" ref="PV2" />  
      <xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
    </xsd:sequence>  
    <xsd:sequence>  
      <xsd:element minOccurs="1" maxOccurs="1" ref="PV2" />  
      <xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
    </xsd:sequence>  
  </xsd:choice>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbda8-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbda8-105">See Also</span></span>  
 <span data-ttu-id="cbda8-106">[必要的手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span><span class="sxs-lookup"><span data-stu-id="cbda8-106">[Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span></span>  
 [<span data-ttu-id="cbda8-107">公用程式</span><span class="sxs-lookup"><span data-stu-id="cbda8-107">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)