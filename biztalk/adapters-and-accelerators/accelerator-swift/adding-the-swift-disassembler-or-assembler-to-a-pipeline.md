---
title: 將 SWIFT 解譯器或組合器新增至管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, adding assembler
- assembler, adding to pipelines
- pipelines, adding disassembler
- disassembler, adding to pipelines
ms.assetid: f39eb340-fe58-4c8f-b3f2-f7686a245095
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f48317c21942e0912f88d3e48523e07728c16ad3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967999"
---
# <a name="adding-the-swift-disassembler-or-assembler-to-a-pipeline"></a>將 SWIFT 解譯器或組合器新增至管線
您可以搭配 Microsoft BizTalk 管線設計師[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]以建立自訂的 BizTalk 接收和傳送管線。 您可以使用 SWIFT 解譯器的自訂接收管線中的 「 解譯 」 階段。 同樣地，您可以使用 SWIFT 組合器自訂傳送管線中的 「 組合 」 階段。 要叫用的 SWIFT 解譯器或組合器 [管線設計師工具箱] 中，您將解譯器或組合器拖曳至對應的管線階段管線設計工具畫布上。 如需叫用的解譯器或組合器的逐步指示，請參閱[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)在端對端教學課程。 「 管線設計師 」 的詳細資訊或使用管線專案，請參閱 BizTalk Server 說明。  
  
 根據設計，SWIFT 解譯器會預期要的 「 解譯 」 階段*最終*叫用的接收管線階段。 使用任何後續的階段時，將會導致非預期的行為 （不叫用後續的階段，這類反組譯工具或移除它先前已填入並發佈到 MessageBox 的訊息之前升級內容屬性的解譯器資料庫）。 同樣地，SWIFT 組合器預期為 「 組合 」 階段*第一個*傳送管線階段。 使用任何上述的階段，可能會降低 SWIFT 組合器的動態訊息類型探索。  
  
 您可以使用它們的管線設計師工具箱第一個時間，您必須手動將 SWIFT 解譯器和組合器。 執行此動作的逐步指示的詳細[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)在端對端教學課程。 元件將會繼續出現在工具箱中，一旦您以手動方式加入 (直到您手動加以移除，或直到您解除安裝[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)])。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)