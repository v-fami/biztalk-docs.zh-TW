---
title: 使用 Siebel 配接器設定動態連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
- configuring, dynamic ports
ms.assetid: a3516c2c-d40e-426b-bf3f-f9dc3de105ef
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b036bf772e3e9580c84616f74786d4908aca7515
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221910"
---
# <a name="configure-dynamic-ports-with-the-siebel-adapter"></a>使用 Siebel 配接器設定動態連接埠
在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。 因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 架構的配接器，您可以動態設定的連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用訊息內容屬性。  
  
 如[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後以指定**運算式**圖形，如下列範例所示：  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert";  
Request2(WCF.BindingType)="siebelBinding";  
Request2(WCF.UserName)="YourUserName";  
Request2(WCF.Password)="YourPassword";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="siebel://mySiebelServer:1234?SiebelObjectManager=SSEObjMgr&SiebelEnterpriseServer=myEnterpriseServer&Language=enu";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  如果您使用的 WCF Siebel 介面卡[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SiebelAdapter"`，其中**SiebelAdapter**名稱新增 Wcf-siebel 配接器在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 在上述範例中：  
  
-   正在從 Request1 訊息建立 Request2 訊息。 兩個訊息對應到作業結構描述，產生使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
-   傳送埠是 BizTalk 協調流程中的邏輯傳送埠的名稱。  
  
 「 運算式 」 圖形是 BizTalk 協調流程的一部分。 當您部署協調流程時，也會建立 Wcf-custom 傳送埠。  
  
 如需設定動態連接埠的詳細資訊，請參閱[設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。
  
## <a name="see-also"></a>另請參閱  
[若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)