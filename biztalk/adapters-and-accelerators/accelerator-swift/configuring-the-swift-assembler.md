---
title: "設定 SWIFT 組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, configuring
- configuring, assembler
ms.assetid: 76944226-e29b-4a7f-a4ab-3c3d5f13ec51
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f77d47b2b3ab687f2fd72242f4ddbbc68ae8530c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-the-swift-assembler"></a>設定 SWIFT 組譯工具
SWIFT 組譯工具執行下列工作，當您叫用在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送管線：  
  
-   動態探索訊息類型，並解析文件結構描述  
  
-   剖析的 XML 序列化 SWIFT 的一般檔案  
  
 您可以設定編碼使用的字元集編碼方式 （例如，若要使用 ASCII 或 Unicode 編碼） 序列化的輸出。  
  
 您的自訂傳送管線，使用 SWIFT 組合器的開發期間設定 SWIFT 組譯工具。  
  
 BizTalk 管線設計師 」 的自訂傳送管線開發期間設定 SWIFT 組譯工具。  
  
 若要加入自訂傳送管線的組合階段後，請設定 SWIFT 組譯工具，選取管線設計工具畫布上的 SWIFT 組合器元件。 SWIFT 組譯工具就會接收焦點，因此您可以設定其組態屬性，使用 [屬性] 視窗內[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。  
  
 可用的設定屬性及其描述和使用方式詳細資料的資料表，請參閱[SWIFT 組合器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)。  
  
 針對不同的案例使用 SWIFT 組譯工具，以及設定組態屬性的相關資訊，請參閱[SWIFT 解譯器和組合器使用](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。  
  
 自訂管線二進位編譯時，它以靜態方式寫入組態設定自訂的管線。 因此，您無法在部署期間變更的組態屬性，或執行階段。  
  
> [!NOTE]
>  設定、 編譯及部署自訂的管線之後，組態中的變更需要重新編譯和重新部署自訂管線。  
  
 建立、 建置和部署自訂管線的相關資訊，請參閱 BizTalk Server 說明。  
  
 此部分包含：  
  
-   [SWIFT 組合器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)