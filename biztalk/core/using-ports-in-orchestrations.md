---
title: 協調流程中使用連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, receiving
- ports, configuring manually
- send ports, messages
- ports, creating
- ports, messages
- creating, ports
- send ports, sending
- ports, operations
- configuring, ports
- ports, deleting
- deleting, ports
- orchestrations, ports
- Port Configuration Wizard [Orchestration Designer]
- ports
- ports, about ports
- ports, configuring
ms.assetid: 968b2d1b-e233-4eb0-8254-9ec6b7642cdf
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7f48c1c070e3a3a3e7ebe7e86618a4fd9ebc90d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287414"
---
# <a name="using-ports-in-orchestrations"></a>在協調流程中使用連接埠
連接埠指定您的協調流程和其他商務程序之間傳送和接收訊息的方式。 每個連接埠都具有類型、方向和繫結，由這些決定通訊的方向、通訊的模式、傳送和接受訊息的位置，以及通訊進行的方式。  
  
> [!NOTE]
>  連接埠和連接埠類型不同。 連接埠是連接埠類型的執行個體；數個不同的連接埠可以具有相同的連接埠類型。  
  
 基於這些因素，連接埠可能會有關聯的 URI (實體位置)、傳輸 (可能是 FILE、HTTP、SOAP、SMTP 或 BizTalk 訊息佇列)、準備訊息以供傳送的傳送管線 (例如，透過組合、加密、壓縮或對其執行某些其他動作)，以及準備接收訊息以供處理的接收管線 (例如透過解譯、解密或解壓縮)。  
  
 新增連接埠到協調流程的方式，和新增控制項到 Web Form 或 Windows Form 的方式類似。 您也可以使用 [協調流程檢視] 視窗來新增連接埠。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [通訊模式](../core/communication-pattern.md)  
  
-   [通訊方向](../core/communication-direction.md)  
  
-   [連接埠繫結](../core/port-bindings.md)  
  
-   [如何在協調流程中使用連接埠](../core/how-to-use-ports-in-orchestrations.md)  
  
-   [如何使用連接埠類型](../core/how-to-work-with-port-types.md)  
  
-   [如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)  
  
-   [使用 協調流程中的直接繫結連接埠](../core/working-with-direct-bound-ports-in-orchestrations.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)   
 [協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)