---
title: 設定 SWIFT 解譯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, disassembler
- disassembler, configuring
ms.assetid: f3773781-7412-421c-943c-18cc665da8d9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ad88310f5bbf600edd576bc0bc17c64fe3ecbea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001463"
---
# <a name="configuring-the-swift-disassembler"></a>設定 SWIFT 解譯器
SWIFT 解譯器 (DASM) 執行下列工作，當您在 Microsoft 中叫用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：  
  
- 動態探索訊息類型，並解析文件結構描述  
  
- 將 SWIFT 的一般檔案剖析為 XML  
  
- 叫用驗證讀取器執行 XML （結構描述） 驗證的 XML  
  
- 叫用的 「 商務規則引擎 (BRE) 」，來執行 BRE 驗證  
  
- 將已剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML  
  
- 處理程序的輸入批次  
  
  您可以設定以符合使用者案例的特定需求，上面所列的功能和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解決方案。  
  
  BizTalk 管線設計師會在開發期間，自訂接收管線設定 SWIFT 解譯器。  
  
  若要新增至自訂接收管線的 「 解譯 」 階段之後，請設定 SWIFT 解譯器，選取 BizTalk 管線設計工具畫布上的 SWIFT 解譯器元件。 SWIFT 解譯器，然後接收焦點，而且您可以設定它使用在 Microsoft [屬性] 視窗的組態屬性[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。  
  
  可用的設定屬性及其描述和使用方式詳細資料的資料表，請參閱[SWIFT 解譯器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。  
  
  針對不同的案例使用 SWIFT 解譯器和設定組態屬性的相關資訊，請參閱[使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。  
  
  當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]編譯二進位檔，它必須以靜態方式的組態設定寫入至自訂管線的自訂管線。 因此，您無法變更在部署期間的組態屬性，或執行階段。  
  
> [!NOTE]
>  設定、 編譯及部署自訂的管線之後，在組態中的變更會需要重新編譯並重新部署自訂的管線。  
  
 如需建立、 建置和部署自訂的管線資訊，請參閱 BizTalk Server 說明。  
  
 此部分包含：  
  
-   [SWIFT 解譯器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)