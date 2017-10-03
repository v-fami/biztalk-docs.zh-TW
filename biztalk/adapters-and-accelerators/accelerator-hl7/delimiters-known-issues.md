---
title: "分隔符號的已知的問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues, delimiters
- delimiters
ms.assetid: 4eaacb3c-9d8d-43da-91dd-8bb25dec70e1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18168ade94eed99efff0a062904c14b387de6bcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-known-issues"></a>分隔符號的已知的問題
本節包含可協助您避免分隔符號錯誤的有用資訊。  
  
## <a name="characters-not-recommended-to-be-used-as-delimiters"></a>不建議使用做為分隔符號的字元  
 建議您執行不使用下列字元做為分隔符號可能造成錯誤：  
  
-   Null 字元  
  
-   空格  
  
## <a name="extra-delimiters-in-a-header-or-body-field-cause-multiple-errors"></a>標頭或本文欄位中的額外分隔符號會導致多個錯誤  
 當您有額外的分隔符號 HL7 V2 中的欄位。訊息，x [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 剖析器可能會產生兩個錯誤訊息，其中一個相關 XML 驗證，以及其他相關結構化驗證。  
  
## <a name="trailing-delimiters-permitted-in-hl7-batch-segments"></a>HL7 批次區段允許尾端分隔符號  
 HL7 定義批次區段例如 FHS、 BHS、 BTS 和 FTS 可以有尾端分隔符號，而且不會受到尾端分隔符號旗標，因為[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會驗證批次區段的尾端分隔符號。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)