---
title: SWIFT 解譯器和組合器功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler, about disassembler
- assembler, about assembler
- assembler, functionality
- disassembler, functionality
ms.assetid: d4fc092e-586d-4360-921d-151af66b8bc1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f9a01480c5d308ffa882b2457e26548f4b5e43b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992855"
---
# <a name="swift-disassembler-and-assembler-functionality"></a>SWIFT 解譯器和組合器功能
SWIFT 解譯器可以執行下列工作中叫用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：  
  
- 以動態方式找出的訊息類型，並解決文件結構描述。 此啟用的單一的接收埠和管線來處理多個 SWIFT 的訊息類型。  
  
- 剖析為 XML 的 SWIFT 的一般檔案。  
  
- 叫用驗證讀取器執行 XML （結構描述） 驗證，例如資料類型的有效性、 資料格式或長度一致性檢查的 XML。  
  
- 叫用的 「 商務規則引擎 (BRE) 」，來執行 BRE 驗證，例如檢查一致性 SWIFT 網路規則，或執行其他複雜的驗證結構描述未實作。  
  
- 將已剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML （提供剖析或驗證期間發生任何錯誤的相關資訊）。  
  
  > [!NOTE]
  >  如果解譯器在剖析期間發生嚴重失敗，解譯器會發佈訊息到 MessageBox 資料庫中的原生的一般檔案格式，而不是 XML。  
  
- 處理輸入批次，如下所示：  
  
  -   剖析，並保留批次的信封 （批次結尾中的 批次標頭）  
  
  -   剖析，並保留訊息信封 （訊息標頭，訊息結尾）  
  
  -   剖析及驗證個別的批次中的 SWIFT 訊息  
  
  -   個別將 SWIFT 的訊息發佈到 MessageBox 資料庫  
  
  -   將整個輸入批次發佈至 MessageBox 資料庫中，當作單一訊息 （輸入完全相同複本）  
  
  -   升級用於排序或相互關聯訊息來自相同的批次的批次相關的內容屬性  
  
  SWIFT 組合器可以執行時叫用 BizTalk 傳送管線中的下列工作：  
  
- 以動態方式找出的訊息類型，並解決文件結構描述。 這可讓單一傳送埠和管線，以處理多個 SWIFT 訊息類型。  
  
- 將剖析的 XML 序列化至 SWIFT 的一般檔案中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)