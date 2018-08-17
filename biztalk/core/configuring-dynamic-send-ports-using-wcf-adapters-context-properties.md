---
title: 設定動態傳送埠使用 WCF 配接器內容屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF services, send ports
- send ports, WCF services
- dynamic send ports, WCF services
- send ports, dynamic
ms.assetid: 2a7e2cd2-fa2d-45da-bb8e-eb8bab21bfa3
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca781dc1d101e3eef0976229b3d1b986c2f4498d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995271"
---
# <a name="configuring-dynamic-send-ports-using-wcf-adapters-context-properties"></a>使用 WCF 配接器內容屬性設定動態傳送埠
您可以為 WCF 配接器設定動態傳送埠。 URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後指定 在**運算式**圖形，如下列 Wcf-nettcp 配接器中所示：  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.SecurityMode)="Transport";  
MessageOut(WCF.TransportClientCredentialType)="Windows";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/netTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-NetTcp";  
```  
  
 下列程式碼顯示如何指定 WCF 內容屬性中的範例**運算式**Wcf-custom 配接器的圖形：  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.BindingType)="customBinding";  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.BindingConfiguration)=@"<binding name=""customBinding""><binaryMessageEncoding /><tcpTransport /></binding>";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/customNetTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
 指定 WCF 內容屬性時的考量如下：  
  
- 有些位址可對應至多個配接器。 例如，http:// 或 https:// 開頭的位址可以由 HTTP 配接器和 WCF-BasicHttp、WCF-WsHttp 或 WCF-Custom 配接器處理。 上方範例程式碼的另一個範例為：這兩種配接器都使用開頭為 net.tcp:// 的位址，不過因為第二個範例程式碼使用自訂繫結，所以應該使用 WCF-Custom 處理位址。 因此，若要識別正確的配接器，您必須設定選擇性**Microsoft.XLANGs.BaseTypes.TransportType**欄位中**運算式**您想要使用的配接器的圖形。  
  
  > [!NOTE]
  >  如果位址開頭為 http:// 或 https:// , 而且如果您未指定 **Microsoft.XLANGs.BaseTypes.TransportType**  欄位中，根據預設，BizTalk 引擎會使用 HTTP 配接器。  
  
- **WCF。BindingType**依名稱識別繫結。 可以是下列其中一項：  
  
  - basicHttpBinding  
  
  - customBinding  
  
  - netMsmqBinding  
  
  - netNamedPipeBinding  
  
  - netTcpBinding  
  
  - wsFederationHttpBinding  
  
  - wsHttpBinding  
  
    上方的清單可以擴充。 例如，您可以將自己的繫結新增至清單中，例如 FtpBinding。  
  
- **WCF。BindingConfiguration**指定繫結類型的繫結組態。 它會採用在電腦組態檔中註冊的任何繫結。 此外還會以與 WCF 組態檔的繫結組態中使用的相同格式採用 XML 組態。  
  
- 您可能需要指定額外的 WCF 屬性。 您可以輸入**WCF**中運算式編輯器中和 IntelliSense 功能應該會列出所有可用的內容屬性。 如需有關 WCF 內容屬性的詳細資訊，請參閱 < [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。  
  
  上述範例示範如何設定**WCF。動作**以單一動作。 在多個動作對應實例中，WCF 配接器不支援使用多個動作對應搭配動態傳送埠。 您只可以在設定的實際動作**WCF。動作**與上述中顯示的內容屬性。  
  
## <a name="see-also"></a>另請參閱  
 [指定的 SOAP 動作，wcf 傳送配接器](../core/specifying-soap-actions-for-wcf-send-adapters.md)   
 [如何使用運算式來將值指派給動態連接埠](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)   
 [連接埠繫結](../core/port-bindings.md)