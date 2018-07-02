---
title: 連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, warnings
- ports, bindings
- bindings, Web ports
- bindings, design time
- Web ports, port bindings
- bindings, ports
- bindings, direct
- bindings, warnings
- bindings, deployment
- bindings, dynamic
ms.assetid: b61c725a-0082-42d3-b88a-533583161734
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f74e60db9b3a5994ff04f13fe2f242792cf2dcc7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972535"
---
# <a name="port-bindings"></a>連接埠繫結
連接埠繫結是組態資訊，用來決定傳送或接收訊息的位置與方式。 根據其類型，連接埠繫結可以指實體位置、管線或其他協調流程。  
  
 接收訊息之連接埠的連接埠繫結有三種類型：  
  
- 立即指定  
  
- 稍後指定  
  
- 直接  
  
  傳送訊息之連接埠的連接埠繫結有四種類型：  
  
- 立即指定  
  
- 稍後指定  
  
- 直接  
  
- 動態  
  
## <a name="binding-at-deployment-time"></a>部署階段的繫結  
 您可以將您的連接埠繫結至接收位置或傳送埠。 如果您沒有所有您要指定實體位置的資訊，您可以選取**稍後指定**連接埠繫結選項，在協調流程設計師 」，您只需要指定描述該連接埠的連接埠類型。 當部署應用程式之後，您可以使用 BizTalk Server 管理主控台來指定此位置的相關資訊，或是可以透過程式設計方式來設定位置資訊。  
  
## <a name="binding-at-design-time"></a>設計階段的繫結  
 您可以選取**立即指定**連接埠在協調流程設計工具中的繫結選項，以在設計階段指定的傳輸和管線。 當您指定要用於接收訊息的連接埠時，下拉式清單中只會提供 HTTP、SOAP 和 FILE 傳輸。 當您指定要用於傳送訊息的連接埠時，下拉式清單中只會提供 HTTP、FILE 和 SMTP 傳輸。 若您事先知道傳輸訊息的來源或目的地，這個選項會很有用。  
  
## <a name="direct-binding"></a>直接繫結  
 直接繫結連接埠是協調流程中未明確繫結至任何實體連接埠的邏輯單向或雙向連接埠。 直接繫結連接埠可讓您在服務中有不同的通訊模式。 若要實作直接繫結，請選取**直接**連接埠在協調流程設計師在設計階段的繫結選項。  
  
 有三種類型的直接繫結連接埠：  
  
- MessageBox 直接繫結連接埠  
  
- 自我相互關聯的直接繫結連接埠  
  
- 夥伴協調流程直接繫結連接埠  
  
  如需如何使用直接繫結的連接埠的詳細資訊，請參閱[使用直接繫結連接埠在協調流程中](../core/working-with-direct-bound-ports-in-orchestrations.md)。  
  
> [!NOTE]
>  使用直接繫結時，您無法在一個要求-回應連接埠和兩個單向連接埠間交換訊息。  
  
> [!NOTE]
>  直接繫結和「Web 服務商務程序工程語言」(BPEL4WS) 的標準不相容。 若您需要 BPEL4WS 相容規範，請使用另一種繫結。  
  
## <a name="dynamic-binding"></a>動態繫結  
 若您要到執行階段才會知道通訊的目的地，您可以針對傳送埠使用動態繫結。 位置可能，比方說，是決定從傳入訊息上的屬性，並指定在**運算式**圖形，如下列程式碼所示：  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
```  
  
 如需有關如何以動態方式將值指派給連接埠的資訊，請參閱[如何將值指派給動態連接埠](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)。  
  
## <a name="web-ports"></a>Web 連接埠  
 若您的專案包含 Web 服務的參考，「協調流程設計師」會偵測它，並提供可用的對應 Web 連接埠類型。 若要建立 Web 連接埠，您只要新增連接埠到您的協調流程，並為它指派現有的 Web 連接埠類型即可。 如需詳細資訊，請參閱 <<c0> [ 建立 Web 連接埠](../core/creating-web-ports.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用連接埠類型](../core/how-to-work-with-port-types.md)   
 [通訊模式](../core/communication-pattern.md)   
 [通訊方向](../core/communication-direction.md)   
 [使用協調流程中的連接埠](../core/using-ports-in-orchestrations.md)   
 [如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)   
 [使用 Web 服務](../core/consuming-web-services.md)