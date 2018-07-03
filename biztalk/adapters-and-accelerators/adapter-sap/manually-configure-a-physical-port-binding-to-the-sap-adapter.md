---
title: 以手動方式設定 SAP 配接器的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, sending messages to the SAP system
- physical port binding, manually configuring
- deploying, receiving messages from the SAP system
ms.assetid: c4f547aa-5514-4ca9-809b-d8d395de419c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14aea45a1032a2e01e9560d9ab47e85e75506836
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994607"
---
# <a name="manually-configure-a-physical-port-binding-to-the-sap-adapter"></a>以手動方式設定 SAP 配接器的實體連接埠繫結
設定[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]為 WCF 自訂繫結使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 

## <a name="port-overview"></a>連接埠概觀
部署之後，配接器，您將能夠傳送和接收來自 SAP 系統的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署配接器的步驟而異：  
  
- 之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您可以選擇設定傳送、 接收、 傳送-接收 」 或 「 接收-傳送埠。 您選擇的項目摘要如下表：  
  
  |連接埠方向|通訊模式|可從中選擇的通訊方向|  
  |---|---|---|  
  |Send|單向|我將總是在此連接埠傳送訊息。|  
  |Receive|單向|我將總是在此連接埠接收訊息。|  
  |傳送-接收|要求-回應|我將會傳送要求並接收回應。|  
  |傳送-接收|請求-回應|我將會接收要求並傳送回應。|  
  
   如需詳細資訊，請參閱 <<c0> [ 建立傳送埠](../../core/how-to-create-a-send-port2.md)，或[建立接收埠](../../core/how-to-create-a-receive-port.md)。
  
- 無論配接器將訊息傳送至 SAP 系統，或從 SAP 系統接收訊息。 根據您要傳送或接收訊息，您將會建立傳送或接收埠。  
  
  > [!NOTE]
  >  您也可以設定傳送，或藉由匯入繫結組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中繼資料產生的一部分。 如需有關設定連接埠使用此繫結檔案的指示，請參閱[設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定使用 wcf-custom 配接器和 Oracle 資料庫配接器的連接埠](../../adapters-and-accelerators/adapter-oracle-database/configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter.md)  
  
-   [使用 WCF-SAP 配接器設定連接埠](../../adapters-and-accelerators/adapter-sap/configure-a-port-using-the-wcf-sap-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
[建立 SAP 應用程式的建構元素](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)