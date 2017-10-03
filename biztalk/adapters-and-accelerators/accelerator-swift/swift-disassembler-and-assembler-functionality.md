---
title: "SWIFT 解譯器和組合器功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, about disassembler
- assembler, about assembler
- assembler, functionality
- disassembler, functionality
ms.assetid: d4fc092e-586d-4360-921d-151af66b8bc1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0109979fbb9bf61fc0e1be833061b2a15b470690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler-and-assembler-functionality"></a>SWIFT 解譯器和組合器功能
SWIFT 反組譯工具可以執行下列工作中叫用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：  
  
-   以動態方式找出的訊息類型，並解決文件結構描述。 這樣做可讓的單一接收埠和管線來處理多個 SWIFT 訊息類型。  
  
-   剖析為 XML 的 SWIFT 的一般檔案。  
  
-   叫用驗證讀取器執行 XML （結構描述） 驗證，例如資料類型的有效性，資料格式或長度一致性檢查的 XML。  
  
-   叫用來執行 BRE 驗證，例如，檢查符合 SWIFT 網路規則或執行其他複雜的驗證結構描述不會實作商務規則引擎 (BRE)。  
  
-   將剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML （以提供資訊進行剖析或驗證期間發生的錯誤）。  
  
    > [!NOTE]
    >  如果解譯器在剖析期間發生嚴重失敗，解譯器將會發佈訊息至 MessageBox 資料庫，在原生的一般檔案格式，而不是 XML。  
  
-   處理輸入批次，如下所示：  
  
    -   剖析和保留批次的信封 （批次標頭、 批次結尾）  
  
    -   剖析，並保留訊息信封 （訊息標頭、 訊息結尾）  
  
    -   剖析及驗證 SWIFT 訊息批次中個別  
  
    -   個別將 SWIFT 訊息發佈到 MessageBox 資料庫  
  
    -   發佈至 MessageBox 資料庫的整個輸入批次當做單一訊息 （輸入的完全相同複本）  
  
    -   升級適用於排序或來自相同的批次的訊息相互關聯的批次相關的內容屬性  
  
 SWIFT 組譯工具可以執行時叫用 BizTalk 傳送管線中的下列工作：  
  
-   以動態方式找出的訊息類型，並解決文件結構描述。 這可讓單一傳送埠和管線來處理多個 SWIFT 訊息類型。  
  
-   將剖析的 XML 序列化為 SWIFT 的一般檔案。  
  
## <a name="see-also"></a>另請參閱  
 [SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)