---
title: SWIFT 文字 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT, text
ms.assetid: 90851d38-7789-4b1b-813b-7943f77ab984
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80d8ee0343cbf8ac96d57119ef198d623159b26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-text"></a>SWIFT 的文字
訊息文字的財務 (FIN) 訊息中，裝載所組成，且包含的所有資料欄位包含寄件者、 接收者和訊息類型的欄位除外。 這三個欄位都包含在標頭部分。 有些訊息也包含選擇性使用者標頭，也會提供處理資訊。  
  
 每個 FIN 訊息內容是由一系列的定義順序中的欄位所組成。 這些欄位符合下列規則：  
  
-   欄位是必要或選擇性在序列。  
  
-   序列可能包含子，與子序列可能會重複序列中。  
  
-   您可以使用數種訊息類型中的欄位。  
  
-   在欄位中，可能會有項目或子欄位。 項目或子欄位可能是通用於數個欄位。  
  
-   每個重複的順序是由群組節點表示。  
  
-   每個欄位可能本身會有多個 nodal 等級，以記錄每個所述。  
  
-   結構描述項目代表只最低層級子欄位。  
  
-   一般記錄和項目是一般和基底結構描述中定義，如下所述。  
  
-   某些欄位可以數種格式 （例如合作對象的欄位） 來表示。 這類欄位會定義為結構描述中的選項欄位。  
  
 某些欄位具有有限的一組值。 大部分的情況下，結構描述會列出這些值。 結構描述定義也包含字元集驗證。