---
title: 協調流程變數類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
ms.assetid: 34990be2-35b6-40ec-b107-42a1c7b45aca
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f388cf112a84d1e6ace00d3930cd6d815d728d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264574"
---
# <a name="orchestration-variable-types"></a>協調流程變數類型
您可以宣告下列預先定義型別的變數：  
  
|||||  
|-|-|-|-|  
|boolean|byte|char|datetime|  
|decimal|double|int16|int32|  
|int64|long|sbyte|single|  
|string|timespan|uint16|uint32|  
|uint64||||  
  
 您也可以宣告在專案中參考之任何 NET 架構型別的變數。  
  
## <a name="considerations-for-declare-orchestration-variables"></a>宣告協調流程變數的考量  
 在宣告協調流程變數時，請考慮下列項目：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 對某些以內容為基礎的路由案例支援多值內容屬性，不過您無法在協調流程中使用這類屬性。  
  
-   為了支援協調流程的擱置和解除凍結，所有的協調流程變數都必須能夠使其狀態持續。  通常，這點會由變數型別或類別的可序列化或可資料流化來達成。  
  
-   這些 .NET 架構的型別 (類別) 必須是可序列化的類別。  它們可能會以 "[Serializable]” 屬性宣告，或是明確實作 ISerializable .NET 介面 (在 System.Runtime.Serialization 命名空間中)，以便進行實作。  
  
-   如果 .NET 架構型別實際上是基礎 COM 元件的執行階段可呼叫包裝函式 (RCW)，則該 COM 元件就必須實作 RCW 所需要的介面，以便成為可序列化的 .NET 類別 (例如，IpersistStream、IPersistStreamInit)。  
  
-   由於任何 .NET 架構 (或基礎 COM) 型別都是在協調流程的流程內執行，這些型別的方法都不能延遲協調流程的執行 (例如，透過資源的爭用等等)。  而且這些型別實作的任何資源消耗，都會影響到呼叫之協調流程在其中執行的主控件執行個體。