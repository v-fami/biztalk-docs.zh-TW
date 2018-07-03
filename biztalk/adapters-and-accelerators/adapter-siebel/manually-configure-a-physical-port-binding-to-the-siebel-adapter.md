---
title: 手動設定 Siebel 配接器的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- physical port binding, manually configuring
- how to, manually configure adapters for sending messages to a Siebel system
ms.assetid: a1445b8a-440f-45e8-96e9-a13142ca87c6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25afdeaf544cddb67440d050690ca8ca08df4547
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020030"
---
# <a name="manually-configure-a-physical-port-binding-to-the-siebel-adapter"></a>手動設定 Siebel 配接器的實體連接埠繫結
本節提供設定的相關資訊[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]為 WCF 自訂繫結使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 在部署之後，配接器，您將能夠傳送和接收來自 Siebel 系統的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署配接器的步驟而異的之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 您可以選擇設定 傳送 或 傳送接收埠。 您選擇的項目摘要如下表：  
  
|連接埠方向|通訊模式|可從中選擇的通訊方向|  
|---|---|---|  
|Send|單向|我將總是在此連接埠傳送訊息。|  
|傳送-接收|要求-回應|我將會傳送要求並接收回應。|  
  
 如需詳細資訊，請參閱 <<c0> [ 建立和設定傳送埠](../../core/creating-and-configuring-send-ports.md)。
  
> [!NOTE]
>  收到不支援連接埠，因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不會啟用來自 Siebel 系統的輸入的操作。  
> 
> [!NOTE]
>  您也可以藉由匯入所建立的繫結組態檔來設定 Wcf-custom 傳送埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中繼資料產生的一部分。 如需有關設定連接埠使用此繫結檔案的指示，請參閱[設定的實體連接埠繫結使用的連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。
  
 
  
## <a name="see-also"></a>另請參閱  
[若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)