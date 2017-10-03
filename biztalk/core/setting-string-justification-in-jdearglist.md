---
title: "在 Jdearglist 中設定字串左右對齊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, setting string justification
- strings, configuring
- strings, right-justified
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daecf4101ebf5dc8964562dc7f385d41279a3401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-string-justification-in-jdearglist"></a>在 Jdearglist 中設定字串左右對齊
若要在 JD Edwards OneWorld jdearglist.txt 檔案中，將一些字串引數設定為靠右對齊 (填補左方)，您必須知道所想要存取的商務功能，特別是您必須知道您想要呼叫商務功能中的哪一個欄位。  
  
 您必須先更新 jdearglist.txt，然後才能在協調流程中產生繫結 (結構描述)。 更新 jdearglist.txt 檔案的指示所述[處理字串值](../core/handling-string-values1.md)。  
  
 如果您在稽核記錄中收到 jdearglist.txt 警告訊息，它是通知您找不到 jdearglist.txt。 如果您執行 SalesOrder 或 PurchaseOrder 商務功能，您的 PATH 中必須要有此檔案，否則商務功能將無法運作。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Adapter for JD Edwards OneWorld](../core/administering-biztalk-adapter-for-jd-edwards-oneworld.md)