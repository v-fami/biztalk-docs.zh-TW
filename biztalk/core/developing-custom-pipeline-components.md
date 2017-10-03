---
title: "開發自訂管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom]
- pipeline components [custom], about pipeline components
- pipeline components [custom], creating
- customizing, pipeline components
- pipeline interfaces
- IDisassemblerComponent
- pipeline interfaces, about pipeline interfaces
- creating, pipeline components [custom]
- IAssemblerComponent
- IComponent
- pipeline components [custom], customizing
- pipeline interfaces, interface types
- pipeline components [custom], interfaces
- pipeline components [custom], component types
ms.assetid: cce61e0d-f1e3-4ec2-b38c-7c6eaf83ac10
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723cd04a2a907fdb5d770975c27d47e1752d08ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-pipeline-components"></a>開發自訂管線元件
本節描述如何開發管線元件。 您可建立三種管線元件類型：一般、組譯和反組譯。 這三種類型都可額外實作探查功能。 管線元件的每種類型有關聯的介面必須實作才能插入 「 BizTalk 傳訊引擎; 元件區分的元件類型的管線介面為**IComponent**， **IAssemblerComponent**，和**IDisassemblerComponent**。 對於探查元件，您必須實作**IProbeMessage**介面。  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含您在建立自己的元件時可參考的範例管線元件。 此範例元件示範如何將資料附加至訊息結尾，以及如何在訊息開頭新增資料。 如需範例管線元件的詳細資訊，請參閱[CustomComponent （BizTalk Server 範例）](../core/customcomponent-biztalk-server-sample.md)。  
  
> [!CAUTION]
>  如果您從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的管線參考自訂管線元件，可能會發生編譯階段錯誤。 若要修正這個錯誤，請關閉管線設計師，並在編譯之前重新開啟它。 或者，您也可以移除此元件，然後再新增它。  
  
> [!IMPORTANT]
>  升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，請確認現有自訂管線元件中的任何字串變數並未包含任何新行字元，例如 '\n'。 否則，在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中編譯這個元件時，將會出現「常數中包含新行字元」錯誤。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用管線介面](../core/using-pipeline-interfaces.md)  
  
-   [開發一般管線元件](../core/developing-a-general-pipeline-component.md)  
  
-   [開發組合管線元件](../core/developing-an-assembling-pipeline-component.md)  
  
-   [開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)  
  
-   [開發探查管線元件](../core/developing-a-probing-pipeline-component.md)  
  
-   [實作搜尋方法的 Managed 資料流管線元件中](../core/implementing-a-seek-method-in-a-managed-streaming-pipeline-component.md)  
  
-   [使用剖析和序列化引擎](../core/using-the-parsing-and-serializing-engines.md)  
  
-   [報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md)  
  
-   [部署管線元件](../core/deploying-pipeline-components.md)  
  
-   [偵錯自訂管線](../core/debugging-custom-pipelines.md)