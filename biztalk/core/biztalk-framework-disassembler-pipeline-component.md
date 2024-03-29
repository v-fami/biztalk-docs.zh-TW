---
title: BizTalk Framework 解譯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- BizTalk Framework Disassembler [pipeline component]
ms.assetid: 48d6c530-5c02-4c70-ad11-0ea6c3c808f8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ab54ddb9ef0b5fa389e6716fc4426978dcbd7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230582"
---
# <a name="biztalk-framework-disassembler-pipeline-component"></a>BizTalk Framework 解譯器管線元件
BizTalk Framework 解譯器管線元件會剖析 XML 資料，並判斷它是否包含 BizTalk Framework 類型的傳訊內容。 管線元件會儲存訊息內容，以及透過需要產生的 BizTalk Framework 屬性建立新的訊息內容。 此屬性用以將訊息路由到 BizTalk Framework 輸入處理常式，以便接收訊息進行處理。  
  
 若傳送者要求在 BizTalk Framework 信封內使用 deliverReceiptRequest 標頭，則 BizTalk Framework 解譯器管線元件會為產生的訊息產生一個通知。 這是由 BizTalk Framework 組合器管線元件中的產生送達回條屬性所控制。 如需 BizTalk Framework 的詳細資訊，請參閱[BizTalk Framework 組合器管線元件](../core/biztalk-framework-assembler-pipeline-component.md)。  
  
 如需設定 BizTalk Framework 解譯器管線元件和建立協調流程的資訊，請參閱[如何設定 BizTalk Framework 解譯器管線元件](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 BizTalk Framework 解譯器管線元件](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)   
 [管線元件](../core/pipeline-components.md)