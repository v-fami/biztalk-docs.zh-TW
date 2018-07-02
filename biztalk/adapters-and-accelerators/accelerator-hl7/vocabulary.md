---
title: 詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, vocabulary
- vocabularies
ms.assetid: c5df05dd-4af8-4e48-8509-e692b04adf3c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e72b51e327581c0a17f18582b0511218b556a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979031"
---
# <a name="vocabulary"></a>詞彙
HL7 第 2 版提供詞彙的自動程式化項目，某些支援，但大部分的情況下，提供傳輸取自本機程式碼撰寫的系統程式碼的結構。  
  
 HL7 版本 2，在分割資料表會連結所有硬式編碼的欄位。 區段表格中包含之資料表的欄位會使用的識別項。 有三種類型的資料表： HL7 定義外部定義，以及使用者定義。 在某些情況下，標準會提供使用者定義資料表的範例值。 您應該將這些視為與 HL7 標準標記它們。  
  
 在新的版本中，您無法移除 HL7 定義資料表中的程式碼，但您可以加入新的代碼。 您可以變更將會在使用者定義的資料表。  
  
 Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
-   您可以使用所有 HL7 定義的資料表。  
  
-   您可以匯入和使用外部定義 LOINC ICD9 等的程式碼集。  
  
-   您可以在使用者定義資料表的提供值。  
  
-   在支援系統不同的程式碼的情況下，您可以設定允許不同的程式碼集互相的對應。 如有必要，您可以定義多個單一使用者定義資料表，來搭配中繼對應執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)