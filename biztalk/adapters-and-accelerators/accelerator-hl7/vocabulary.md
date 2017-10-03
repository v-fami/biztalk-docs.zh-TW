---
title: "詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, vocabulary
- vocabularies
ms.assetid: c5df05dd-4af8-4e48-8509-e692b04adf3c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c77247054914097131103fe33d86fc78551d8cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="vocabulary"></a>詞彙
HL7 版本 2 提供的自動程式碼項目，詞彙的部分支援，但大部分的情況下，提供傳輸繪製從程式碼撰寫的本機系統的程式碼的結構。  
  
 HL7 版本 2 在區段資料表連結自動程式化的所有欄位。 區段包含的欄位使用之資料表的識別項。 有三種類型的資料表： HL7 定義外部定義，以及使用者定義。 在某些情況下，標準提供使用者定義資料表的範例值。 您應該將這些視為與標準 HL7 標示為它們。  
  
 在新的版本中，您無法移除 HL7 定義資料表中的程式碼，但您可以加入新的代碼。 您可以變更在使用者定義的資料表。  
  
 下列函式的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
-   您可以使用所有 HL7 定義的資料表。  
  
-   您可以匯入和使用外部定義 LOINC ICD9 等程式碼集。  
  
-   您可以提供使用者定義資料表的值。  
  
-   在支援的系統組不同的程式碼的情況下，您可以設定允許不同的程式碼集交互操作的對應。 如有必要，您可以定義多個執行個體的單一使用者定義資料表，以便與中繼的對應。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)