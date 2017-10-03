---
title: "設定 WCF 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetTcpBinding [WCF adapters]
- configuring [WCF adapters]
- WCF adapters, pre-defined bindings
- configuring [WCF adapters], about configuring WCF adapters
- WsHttpBinding [WCF adapters]
- BasicHttpBinding [WCF adapters]
- NetNamedPipeBinding [WCF adapters]
- NetMsmqBinding [WCF adapters]
- bindings, pre-defined [WCF adapters]
- WCF adapters, configuring
ms.assetid: af01e2d4-303d-407a-b853-dd90b0246a8a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dde69bb5b2014a20509778e27230840e47c0b36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-wcf-adapters"></a>設定 WCF 配接器
適用於 Windows Communication Foundation (WCF) 的 BizTalk 配接器讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 能與 WCF 應用程式通訊。 BizTalk WCF 配接器包括表示 WCF 預先定義繫結的五個實體配接器 —**BasicHttpBinding**， **WsHttpBinding**， **NetTcpBinding**， **NetNamedPipeBinding**，和**NetMsmqBinding**。 提供這些表示預先定義繫結之 WCF 配接器的目的，是要讓您能夠輕鬆設定多數應用程式需求的必要資訊。  
  
 BizTalk WCF 配接器也包括兩個配接器，可讓您針對接收位置和傳送埠，自由設定 WCF 繫結和行為資訊。  
  
 所有 WCF 配接器都會提供類似的傳輸屬性對話方塊來設定傳送埠和接收位置。 不過，視實體配接器而定，設定 WCF 配接器的詳細工作會不同。 與配接器繫結沒有直接相關的工作 (例如安裝憑證)，對所有 WCF 配接器來說都是相同的。 本節將探討所有 WCF 配接器的一般工作。 每個介面卡不同工作的詳細資訊，請參閱中的配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)  
  
-   [WCF 配接器安全性建議](../core/wcf-adapters-security-recommendations.md)  
  
-   [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)  
  
-   [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [如何啟用 WCF 擴充性點，WCF 配接器](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)  
  
-   [WCF 配接器效能計數器](../core/wcf-adapters-performance-counters.md)  
  
-   [WCF 配接器的單一登入支援](../core/single-sign-on-support-for-the-wcf-adapters.md)  
  
## <a name="see-also"></a>另請參閱  
 [WCF 配接器](../core/wcf-adapters.md)