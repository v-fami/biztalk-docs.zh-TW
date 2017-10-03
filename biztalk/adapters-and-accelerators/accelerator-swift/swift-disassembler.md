---
title: "SWIFT 解譯器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler
- messages, receive pipelines
- receive pipelines, messages
ms.assetid: 42641550-0c88-4535-b5d5-b90acb30a6d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac0024abe862f777e7ee798991d97845ec5098a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler"></a>SWIFT 反組譯工具
輸入的接收管線會處理所有訊息提交至[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]（在接收位置接收） 的應用程式。  
  
 輸入的處理構成 BizTalk 與相關的邏輯的執行階段接收管線。 管線元件服務，或實作每個階段。 特別是，解譯器服務在接收管線的解譯階段。 A4SWIFT 提供特定 SWIFT 的訊息處理中的自訂解譯器元件的功能。  
  
 SWIFT 組譯工具，自訂的一般檔案解譯器處理輸入 SWIFT 訊息和批次中提供的功能，並執行下列功能：  
  
-   動態探索訊息類型，並解析文件結構描述  
  
-   將 SWIFT 的一般檔案剖析為 XML  
  
-   叫用驗證讀取器執行 XML （結構描述） 驗證的 XML  
  
-   叫用來執行 BRE 驗證商務規則引擎 (BRE)  
  
-   將剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML  
  
-   會處理並輸入批次會反組譯  
  
 下圖顯示 SWIFT 解譯器資料流。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro2.gif "FSA_Intro2")  
  
 如需 SWIFT 解譯器的詳細資訊，請參閱[SWIFT 解譯器和組合器使用](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for SWIFT 的執行階段](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)