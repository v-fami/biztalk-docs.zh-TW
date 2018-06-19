---
title: 開發解譯管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDisassemblerComponent interface, disassembling
- pipeline components [custom], IDisassemblerComponent
- pipeline components [custom], IBaseComponent
- IBaseComponent interface, disassembling
- pipeline components [custom], disassembling
ms.assetid: 77c0aa7d-4d1b-4a8f-bef8-d38e7e4045c6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc4e831561f9940ad7e8ee91479a2fada1fcd910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239702"
---
# <a name="developing-a-disassembling-pipeline-component"></a>開發解譯管線元件
解譯管線元件會接收單一輸入訊息，並產生零個或多個輸出訊息。 解譯元件的用途是將交換的訊息分割成個別的文件。 解譯器元件必須實作下列介面：  
  
-   `IBaseComponent`
  
-   `IDisassemblerComponent`
  
-   `IComponentUI`
  
-   **IPersistPropertyBag。** 如需此介面的詳細資訊，請參閱 .NET Framework SDK 文件。  
  
 您可以建立自己的反組譯的元件擴充**FFDasmComp**或**XMLDasmComp**類別。  
  
> [!WARNING]
>  如果自訂解譯器的 MessageDestination 內容屬性設定為 SuspendQueue，解譯器傳回的資料流就必須支援 Seek(0)，否則無法擱置訊息。  
  
> [!NOTE]
>  自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。 其用意是要將這些部分保留到管線中做進一步處理。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [管線元件中處理內送資料流](../core/handling-incoming-data-streams-in-pipeline-components.md)  
  
-   [處理解譯器管線元件中的編碼](../core/handling-encoding-in-a-disassembler-pipeline-component.md)  
  
-   [延伸一般檔案解譯器管線元件](../core/extending-the-flat-file-disassembler-pipeline-component.md)