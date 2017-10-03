---
title: "設定 SWIFT 解譯器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, disassembler
- disassembler, configuring
ms.assetid: f3773781-7412-421c-943c-18cc665da8d9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7aa71ce6ba1d2a910626446ed45439b8c7132e75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-swift-disassembler"></a>設定 SWIFT 反組譯工具
SWIFT 的解譯器 (DASM) 執行下列工作，當您叫用在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：  
  
-   動態探索訊息類型，並解析文件結構描述  
  
-   將 SWIFT 的一般檔案剖析為 XML  
  
-   叫用驗證讀取器執行 XML （結構描述） 驗證的 XML  
  
-   叫用來執行 BRE 驗證商務規則引擎 (BRE)  
  
-   將剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML  
  
-   處理程序輸入批次  
  
 您可以設定以符合使用者案例的特定需求，上面所列的功能和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]方案。  
  
 BizTalk 管線設計師 」 的自訂接收管線開發期間設定 SWIFT 解譯器。  
  
 若要加入自訂接收管線的解譯階段之後，請設定 SWIFT 解譯器，選取 BizTalk 管線設計工具畫布上的 SWIFT 的解譯器元件。 SWIFT 解譯器就會接收焦點，因此您可以設定其組態屬性，使用 [屬性] 視窗內[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。  
  
 可用的設定屬性及其描述和使用方式詳細資料的資料表，請參閱[SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。  
  
 針對不同的案例使用 SWIFT 解譯器和設定組態屬性的相關資訊，請參閱[SWIFT 解譯器和組合器使用](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。  
  
 當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]編譯二進位，它以靜態方式寫入自訂管線的組態設定的自訂管線。 因此，您無法在部署期間變更的組態屬性，或執行階段。  
  
> [!NOTE]
>  設定、 編譯及部署自訂的管線之後，組態中的變更需要重新編譯和重新部署自訂管線。  
  
 如需建立資訊、 建置及部署自訂管線，請參閱[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
 此部分包含：  
  
-   [SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)