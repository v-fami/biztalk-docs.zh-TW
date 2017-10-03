---
title: "手動設定的實體連接埠繫結至 Oracle E-business 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07369428-7b54-4d90-8c63-ba14e67fdbdd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24ea54009ba97732cbcf6f248127b078c1c9ed05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter"></a>手動設定 Oracle E-business 配接器的實體連接埠繫結
本節提供有關設定資訊[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]當作 WCF 自訂繫結或利用 Wcf-oracleebs 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署之後，配接器，您將能夠傳送和接收 Oracle E-business Suite 中的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署配接器的步驟而異：  
  
-   之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 您可以選擇設定傳送埠、 接收、 傳送接收或接收-傳送埠。 下表摘要說明您的選擇。  
  
    |連接埠方向|通訊模式|若要從選擇的通訊方向|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |Send|單向|我將總是在此連接埠傳送訊息。|  
    |Receive|單向|我將總是在此連接埠接收訊息。|  
    |傳送接收|要求-回應|我將會傳送要求並接收回應。|  
    |接收傳送|請求-回應|我將會接收要求並傳送回應。|  
  
     如需詳細資訊，請參閱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協助文件，網址[http://go.microsoft.com/fwlink/?LinkID=101130](http://go.microsoft.com/fwlink/?LinkID=101130)。  
  
-   是否將配接器傳送的訊息，或從 Oracle E-business Suite 接收訊息。 根據您要傳送或接收訊息，您將會建立傳送或接收埠，分別。  
  
    > [!NOTE]
    >  您也可以設定傳送，或藉由匯入繫結的組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]做為中繼資料產生的一部分。 如需設定使用此繫結檔案的連接埠的指示，請參閱[設定實體的連接埠繫結使用連接埠繫結檔案至 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定連接埠使用 Wcf-custom 配接器和 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-custom-adapter-and-oracle-e-business-suite.md)  
  
-   [設定使用 Wcf-oracleebs 配接器的連接埠](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-oracleebs-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [若要建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)