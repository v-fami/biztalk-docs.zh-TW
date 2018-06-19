---
title: 開發組合管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IComponentUI interface, assembling
- IBaseComponent interface, assembling
- pipeline interfaces, IBaseComponent
- pipeline components [custom], interfaces
- pipeline interfaces, IComponentUI
- IAssemblerComponent interface, assembling
- pipeline interfaces, IAssemblerComponent
- pipeline components [custom], assembling
ms.assetid: 2f85421d-2010-4a36-82b5-ea8016f8aa99
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de06a815e1c5a6bf71700ad373ae3f278b3a9a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239614"
---
# <a name="developing-an-assembling-pipeline-component"></a>開發組合管線元件
組合管線元件是一種 .NET 或 COM 元件，會接收數個輸入訊息，並產生一個輸出訊息。 組合元件的用途是將個別文件收集到訊息交換批次中。  
  
> [!NOTE]
>  因為並沒有使用組件功能，所以 BizTalk Server 永遠都會將一份文件傳遞給元件輸入。  
  
 組合元件必須實作下列介面：  
  
-   `IBaseComponent`  
  
-   `IAssemblerComponent`
  
-   `IComponentUI`
  
-   **IPersistPropertyBag。** 如需此介面的詳細資訊，請參閱 .NET Framework SDK 文件。  
  
> [!NOTE]
>  自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。 其用意是要將這些部分保留到管線中做進一步處理。  
  
## <a name="see-also"></a>另請參閱  
 [開發一般管線元件](../core/developing-a-general-pipeline-component.md)   
 [開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)   
 [開發探查管線元件](../core/developing-a-probing-pipeline-component.md)   
 [報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [部署管線元件](../core/deploying-pipeline-components.md)   
 [CustomComponent （BizTalk Server 範例）](../core/customcomponent-biztalk-server-sample.md)