---
title: 開發一般管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63f5d8d1-30fb-4a1e-b4bd-2be07b618b20
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ca387b139a32606dea89f7c931c86245d151dcb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966687"
---
# <a name="developing-a-general-pipeline-component"></a>開發一般管線元件

## <a name="interfaces"></a>介面
一般管線元件是實作下列介面的 .NET 或 COM 元件：  
  
- IBaseComponent 介面 (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
- IComponent 介面 (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
- IComponentUI 介面 (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
- [IPersistPropertyBag](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.ipersistpropertybag)
  
  一般管線元件會從 BizTalk「傳訊引擎」取得一個訊息、處理該訊息，接著將它傳回 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎。 一般元件也可以經過實作，使其不將訊息傳回至伺服器。 這種元件稱為耗用元件，因為元件會接收訊息但不會產生任何結果訊息。  
  
> [!NOTE]
>  自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。 其用意是要將這些部分保留到管線中做進一步處理。  
  
## <a name="more-pipeline-resources"></a>更多管線資源
 [開發組合管線元件](../core/developing-an-assembling-pipeline-component.md)   
 [開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)   
 [開發探查管線元件](../core/developing-a-probing-pipeline-component.md)   
 [報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [部署管線元件](../core/deploying-pipeline-components.md)   
 [CustomComponent (BizTalk Server 範例)](../core/customcomponent-biztalk-server-sample.md)