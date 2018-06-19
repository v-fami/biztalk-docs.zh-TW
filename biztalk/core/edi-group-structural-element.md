---
title: EDI 群組結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 100a7118-9c02-474e-8685-9e4bb6f52e81
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555d7b86e069adda4f7761b698793fd4ec2af721
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242518"
---
# <a name="edi-group-structural-element"></a>EDI 群組結構元素
群組包含一或多個交易集。 EDIFACT 群組必須包含相同類型的交易集。 X12 群組包含交易集類似類型的 （根據交易集 – 群組對應 (GS01 ST01)） 或型別相同的交易集。 下表列出類似 X12 交易集 (ST01)，可以在單一群組 (GS01) 一起出現。  
  
|GS01|ST01|  
|----------|----------|  
|CF|844|  
|CF|849|  
|DX|894|  
|DX|895|  
|FR|821|  
|FR|827|  
|GC|920|  
|GC|924|  
|GC|925|  
|GC|926|  
|HC|837|  
|HC|837_D|  
|HC|837_I|  
|HC|837_P|  
|採用 IA-64|110|  
|採用 IA-64|980|  
|IO|310|  
|IO|312|  
|我|198|  
|我|200|  
|我|201|  
|我|245|  
|我|261|  
|我|262|  
|我|263|  
|我|833|  
|我|872|  
|MG|203|  
|MG|206|  
|MG|259|  
|MG|260|  
|MG|264|  
|MG|266|  
|OG|875|  
|OG|876|  
|PK|196|  
|PK|839|  
|QG|878|  
|QG|879|  
|QG|888|  
|QG|889|  
|QG|896|  
|QO|313|  
|QO|315|  
|RO|300|  
|RO|301|  
|RO|303|  
|RQ|836|  
|RQ|840|  
|RS|869|  
|RS|870|  
|SL|135|  
|SL|139|  
|因此|302|  
|因此|311|  
|因此|317|  
|因此|319|  
|因此|322|  
|因此|323|  
|因此|324|  
|因此|325|  
|因此|326|  
|因此|361|  
|TO|197|  
|TO|199|  
|TO|265|  
|TO|485|  
|TO|486|  
|TP|460|  
|TP|463|  
|TP|466|  
|TP|468|  
|TP|490|  
|TP|492|  
|TP|494|  
|WA|140|  
|WA|141|  
|WA|142|  
|WA|143|  
  
> [!NOTE]
>  HIPAA 5010 群組也可讓單一群組內的不同版本的交易集。  
  
 若設定處理異動時遇到例外狀況時，會擱置 EDI 合作對象屬性用來判斷整個交換或只失敗的交易設定。  
  
 群組必須以功能群組標頭 (X12 中的 GS 或 EDIFACT 中的 UNG) 做為開頭，而且必須以功能群組結尾 (X12 中的 GE 或 EDIFACT 中的 UNE) 做為結尾。 群組標頭中包含傳送者和接收者代碼、與標頭和結尾相符的日期和時間、定義可包含在功能群組內之交易集集合的群組識別碼，以及其他資訊。 群組結尾則具有指出群組內部交易集數目的元素。  
  
 群組是 EDIFACT 交換中的選擇性項目。 即使沒有任何群組 (UNG 區段不存在)，EDIFACT 交換也可以包含多個交易集. 在這種情況下，這些交易集全都必須屬於同一種類型，因為單一群組中的交易集必須屬於相同類型。 例如，APERAK 和 ORDERS 交易集不能同時存在單一群組或是沒有多個群組的交換中。  
  
 群組在 X12 交換中是必要的項目。