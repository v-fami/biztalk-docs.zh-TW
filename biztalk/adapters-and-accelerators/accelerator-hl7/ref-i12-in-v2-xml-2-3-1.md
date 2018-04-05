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
---
# <a name="refi12-in-v2xml-231"></a>V2 中 REF_I12。XML 2.3.1
您必須手動變更 v2 REF_I12 結構描述中的下列程式碼。XML 2.3.1 之後執行 Update2XMLSchema 工具：  
  
```  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
```  
  
 您必須以下列程式碼，取代上述程式碼，才能修正的多個項目所造成的模稜兩可**REF**項目定義：  
  
```  
<xsd:element minOccurs="0" maxOccurs="2" ref="REF_I12.PATIENT_VISIT" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [必要的手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)   
 [公用程式](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)