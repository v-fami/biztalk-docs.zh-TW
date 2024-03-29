---
title: 設定 SWIFT 組合器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assembler, configuring
- configuring, assembler
ms.assetid: 76944226-e29b-4a7f-a4ab-3c3d5f13ec51
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50c58ad000e465949229400128ce4c47da40806e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993663"
---
# <a name="configuring-the-swift-assembler"></a>設定 SWIFT 組合器
SWIFT 組合器會執行下列工作，當您在 Microsoft 中叫用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送管線：  
  
- 動態探索訊息類型，並解析文件結構描述  
  
- 將剖析的 XML 序列化至 SWIFT 的一般檔案  
  
  您可以設定編碼使用的字元集編碼 （例如，若要使用 ASCII 或 Unicode 編碼） 序列化的輸出。  
  
  您可以設定 SWIFT 組合器會使用 SWIFT 組合器的自訂傳送管線的開發階段期間。  
  
  BizTalk 管線設計師會在開發期間的自訂傳送管線設定 SWIFT 組合器。  
  
  若要新增至自訂傳送管線的 「 組合 」 階段之後，請設定 SWIFT 組合器，選取管線設計工具畫布上的 SWIFT 組合器元件。 SWIFT 組合器則會收到焦點，而且您可以設定它使用在 Microsoft [屬性] 視窗的組態屬性[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。  
  
  可用的設定屬性及其描述和使用方式詳細資料的資料表，請參閱[SWIFT 組合器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)。  
  
  針對不同的案例使用 SWIFT 組合器和設定組態屬性的相關資訊，請參閱[使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。  
  
  自訂管線的二進位檔編譯時，它以靜態方式的組態設定寫入至自訂的管線。 因此，您無法變更在部署期間的組態屬性，或執行階段。  
  
> [!NOTE]
>  設定、 編譯及部署自訂的管線之後，在組態中的變更會需要重新編譯並重新部署自訂的管線。  
  
 如需建立、 建置和部署自訂的管線資訊，請參閱 BizTalk Server 說明。  
  
 此部分包含：  
  
-   [SWIFT 組合器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)