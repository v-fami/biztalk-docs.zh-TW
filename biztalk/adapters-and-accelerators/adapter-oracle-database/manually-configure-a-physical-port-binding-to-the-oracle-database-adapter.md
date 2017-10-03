---
title: "手動設定 Oracle 資料庫配接器的實體連接埠繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, sending to an Oracle database
- messages, receiving from an Oracle database
- physical port binding, manually configuring
ms.assetid: 6b118236-e9eb-494e-96b2-969c7064943d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2a64223485cf83fb214055cb1e11b44fb6bc7c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-database-adapter"></a>手動設定 Oracle 資料庫配接器的實體連接埠繫結
本節提供有關設定資訊[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]做為 WCF 自訂繫結或利用 Wcf-oracledb 繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署之後，配接器，您將能夠傳送和接收訊息從 Oracle 資料庫，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署配接器的步驟而異：  
  
-   BizTalk Server 之間的通訊方向和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您可以選擇設定傳送埠、 接收、 傳送接收或接收-傳送埠。 下表摘要說明您的選擇。  
  
    |連接埠方向|通訊模式|若要從選擇的通訊方向|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |Send|單向|我將總是在此連接埠傳送訊息。|  
    |Receive|單向|我將總是在此連接埠接收訊息。|  
    |傳送接收|要求-回應|我將會傳送要求並接收回應。|  
    |接收傳送|請求-回應|我將會接收要求並傳送回應。|  
  
     如需詳細資訊，請參閱[建立傳送埠](../../core/how-to-create-a-send-port2.md)，或[建立接收埠](../../core/how-to-create-a-receive-port.md)。 
  
-   無論配接器將訊息傳送至 Oracle 資料庫，或從 Oracle 資料庫接收訊息。 根據您要傳送或接收訊息，您將會建立傳送或接收埠，分別。  
  
    > [!NOTE]
    >  您也可以設定傳送，或藉由匯入繫結的組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]做為中繼資料產生的一部分。 如需設定使用此繫結檔案的連接埠的指示，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
 
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../core/develop-your-biztalk-applications.md)