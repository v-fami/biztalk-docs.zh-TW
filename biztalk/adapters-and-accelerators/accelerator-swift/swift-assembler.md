---
title: SWIFT 組合器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assembler
- send pipelines, messages
- messages, send pipelines
ms.assetid: 2a95c7d4-da10-4058-bc2c-3efc35958e14
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39f89720a36c026fa0e8f02902a8fefb08fcebf9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973311"
---
# <a name="swift-assembler"></a>SWIFT 組合器
輸出的傳送管線會處理傳輸的所有訊息[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]（透過傳送埠傳送） 的應用程式。  
  
 輸出處理相關的邏輯的執行階段是由 BizTalk 傳送管線所組成。 管線元件或服務實作的每個階段。 特別是，「 組合器 」 服務在接收管線中的 「 組合 」 階段。 A4SWIFT 提供 SWIFT 特定輸出訊息處理的自訂組合器元件中的功能。  
  
 SWIFT 組合器的自訂的一般檔案組合器中，提供功能來處理輸出 SWIFT 的訊息，並執行下列功能：  
  
- 動態探索訊息類型，並解析文件結構描述  
  
- 將剖析的 XML 序列化至 SWIFT 的一般檔案  
  
  下圖顯示 SWIFT 組合器資料流。  
  
  ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro3.gif "FSA_Intro3")  
  
  如需有關 SWIFT 組合器的詳細資訊，請參閱[使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for SWIFT 執行階段](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)