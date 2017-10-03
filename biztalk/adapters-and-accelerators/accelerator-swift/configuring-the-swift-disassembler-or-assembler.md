---
title: "設定 SWIFT 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, configuring
- configuring, disassembler
- disassembler, configuring
- configuring, assembler
ms.assetid: 56e421f2-0292-40af-b878-0cba1b034e19
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 220c115edac37b8f7268719eefb2095fa7594243
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-swift-disassembler-or-assembler"></a>設定 SWIFT 解譯器或組譯工具
SWIFT 解譯器或 SWIFT 組譯工具加入自訂管線後，您必須將它提供您想要用於特定案例 （例如啟用/停用動態訊息類型探索、 輸入解除批次處理即將、 XML 驗證的功能設定商務規則引擎 (BRE) 驗證，等等）。 您必須設定 SWIFT 解譯器和組合器開發期間才能編譯和部署叫用的自訂管線。 若要設定 SWIFT 的解譯器/組合器，在管線設計師中選取的元件，並編輯 [屬性] 視窗中的組態屬性。  
  
 請參閱[SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)完整詳細資料和每個組態屬性，以及其他使用方式和組態資訊的描述。  
  
 請參閱[SWIFT 組合器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)完整詳細資料和編碼字元集組態屬性，以及其他使用方式和組態資訊的描述。  
  
> [!NOTE]
>  設定、 編譯及部署自訂的管線之後，組態中的變更將需要重新編譯和重新部署自訂的管線。  
  
 設定、 編譯及部署您的自訂管線來處理 SWIFT 訊息之後，您可以設定最多的使用您自訂的 SWIFT 接收管線和傳送連接埠會使用您自訂 SWIFT 傳送管線接收位置。 如需有關部署管線和設定接收埠、 接收位置和傳送埠，請參閱[單元 4： 建立 XML 接收和一般檔案傳送埠](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)，[單元 5： 建立一般檔案接收和XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)，和[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
 此部分包含：  
  
-   [設定 SWIFT 反組譯工具](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)  
  
-   [設定 SWIFT 組譯工具](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)  
  
## <a name="see-also"></a>另請參閱  
 [SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)