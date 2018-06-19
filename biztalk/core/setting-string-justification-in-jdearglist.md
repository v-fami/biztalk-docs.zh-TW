---
title: 在 JD Edwards OneWorld 配接器中設定字串左右對齊 |Microsoft 文件
description: 更新 jdearglist 檔案，以在 BizTalk Server 協調流程中使用 JD Edwards OneWorld 配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b32d0106d95a1970b480e32dfa47a81ebf98ca
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24012997"
---
# <a name="set-string-justification-in-jdearglist"></a>在 Jdearglist 中設定字串左右對齊

## <a name="overview"></a>概觀
若要在 JD Edwards OneWorld jdearglist.txt 檔案中，將一些字串引數設定為靠右對齊 (填補左方)，您必須知道所想要存取的商務功能，特別是您必須知道您想要呼叫商務功能中的哪一個欄位。  
  
 您必須先更新 jdearglist.txt，然後才能在協調流程中產生繫結 (結構描述)。 更新 jdearglist.txt 檔案的指示所述[處理字串值](../core/handling-string-values1.md)。  
  
 如果您在稽核記錄中收到 jdearglist.txt 警告訊息，它是通知您找不到 jdearglist.txt。 如果您執行 SalesOrder 或 PurchaseOrder 商務功能，您的 PATH 中必須要有此檔案，否則商務功能將無法運作。  
  
## <a name="see-also"></a>另請參閱  
[使用 BizTalk Server 例外狀況處理](using-biztalk-server-exception-handling1.md)