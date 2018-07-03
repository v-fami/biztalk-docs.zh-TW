---
title: SWIFT 文字 |Microsoft Docs
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
ms.openlocfilehash: 06e46c8be5da2f62f2b59ce2591e0559367adf08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990927"
---
# <a name="swift-text"></a>SWIFT 文字
訊息文字的財務 (FIN) 訊息中，裝載所組成，並包含的所有資料欄位包含寄件者、 接收者和訊息型別欄位除外。 這三個欄位都包含在標頭部分。 有些訊息也包含選擇性使用者標頭，也會提供處理資訊。  
  
 每個 FIN 訊息內容是由一系列已定義的序列中的欄位所組成。 這些欄位會符合下列規則：  
  
- 欄位可能是必要或選擇性序列內。  
  
- 序列可能包含子序列，與子序列可能會在序列中重複。  
  
- 您可以使用數種訊息類型中的欄位。  
  
- 在欄位中可能有項目或子欄位。 項目或子欄位可能是通用於數個欄位。  
  
- 每個重複的序列被以群組節點。  
  
- 每個欄位可能本身有多個 nodal 層次，每個描述為一筆記錄。  
  
- 結構描述項目代表只有最低的層級子欄位。  
  
- 常見的記錄和項目中定義的一般和基底結構描述，如下所述。  
  
- 以數種格式 （例如合作對象的欄位），就可以表示的某些欄位。 這類欄位會定義為結構描述中的選項欄位。  
  
  某些欄位具有有限的一組值。 大部分的情況下，結構描述會列出這些值。 結構描述定義也包含字元集驗證。