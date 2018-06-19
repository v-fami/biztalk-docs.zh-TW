---
title: XML 解譯器管線元件中的 XML 資訊集項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], information set
- XML Disassembler [pipeline component], processing instructions
- pipeline components, XML Disassembler
ms.assetid: cc82344c-6c4b-4154-a662-0b7ae5caad30
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b3140cbe23637160aafabdccb37104efd1d318
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289294"
---
# <a name="xml-information-set-elements-in-the-xml-disassembler-pipeline-component"></a>XML 解譯器管線元件中的 XML 資訊集項目
XML 解譯器處理 XML 資訊設定項目的方式如下。  
  
|元素|Description|  
|-------------|-----------------|  
|comment|註解會保留在文件中，不過 XML 封套中的任何註解都不會保留。|  
|CDATA|CDATA 會保留在文件中。 不會保留出現在文件外部 (例如，在信封中) 的 CDATA 項目。|  
|處理指示|XML 解譯器會保留出現在 XML 裡面或前面的處理指示。 但是不會保留出現在 XML 文件之後或在信封前後的處理指示。|  
|XML 宣告|會移除任何內送 XML 訊息的 XML 宣告項目。|  
  
## <a name="see-also"></a>另請參閱  
 [XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md)   
 [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)