---
title: XML 組合器管線元件中的 XML 資訊集項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], processing instructions
- Add XML declaration property
- XMLNorm.AddXMLDeclaration property
- pipeline components, XML Assembler
- XML Assembler [pipeline component], XML information set
ms.assetid: 5a262763-838e-476b-8117-30c94bc1d64a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b194b85c88f63036cd74fcd9838aa99e73de6556
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289518"
---
# <a name="xml-information-set-elements-in-the-xml-assembler-pipeline-component"></a>XML 組合器管線元件中的 XML 資訊集項目
XML 組合器元件處理 XML 資訊集項目的方式如下。  
  
|元素|Description|  
|-------------|-----------------|  
|comment|在文件開頭和結尾的 XML 標記之間的註解會保留。|  
|CDATA|在文件開頭和結尾的 XML 標記之間的 CDATA 會保留。 CDATA 值不用於屬性升級或辨別欄位。|  
|處理指示|處理指示位於之前處理文件的 XML 標記會根據其值 (如需詳細資訊，請參閱[XML 組合器管線元件中的處理指示](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md))。 在文件開頭和結尾標記之間的處理指示會保留。 結尾 XML 標記之後的處理指示會忽略，與信封之前、之中或之後的任何指示一樣。|  
|XML 宣告|XML 宣告字串 (如 `<?xml version='1.0'? encoding='UTF-8'>`) 可由 XML 組合器管線元件保留。 這由控制**新增 XML 宣告**屬性或在訊息內容，其對等項目**XMLNorm.AddXMLDeclaration**。<br /><br /> 如果此選項設定為**True** XML 宣告會加入至文件。 若 XML 宣告已經存在，則會將它覆寫。<br /><br /> 如果此選項設定為**False**沒有 XML 宣告會新增，將會移除任何現有的 XML 宣告。 訊息內容中的此屬性值優先於管線設計師中所指定的值。<br /><br /> 預設值： **True** （永遠新增 XML 宣告）|  
  
## <a name="see-also"></a>另請參閱  
 [XML 組合器管線元件](../core/xml-assembler-pipeline-component.md)   
 [如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)