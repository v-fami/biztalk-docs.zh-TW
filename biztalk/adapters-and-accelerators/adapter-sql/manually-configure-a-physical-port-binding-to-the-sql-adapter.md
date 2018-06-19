---
title: 手動設定 SQL 配接器的實體連接埠繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3f0bb78-c85f-4629-9e2d-cce180ff78ae
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac72d914539eabc9b129985c2b9335270e561d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222662"
---
# <a name="manually-configure-a-physical-port-binding-to-the-sql-adapter"></a>手動設定 SQL 配接器的實體連接埠繫結
本節提供有關設定資訊[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]當作 WCF 自訂繫結或利用 WCF SQL 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署之後，配接器，您將能夠傳送和接收訊息從 SQL Server，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 部署配接器的步驟而異：  
  
-   之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以選擇設定傳送、 接收或傳送-接收埠。 下表摘要說明您的選擇。  
  
    |連接埠方向|通訊模式|若要從選擇的通訊方向|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |Send|單向|我將總是在此連接埠傳送訊息。|  
    |Receive|單向|我將總是在此連接埠接收訊息。|  
    |傳送接收|要求-回應|我將會傳送要求並接收回應。|  
  
    > [!NOTE]
    >  雙向接收埠不會受到[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
     如需詳細資訊，請參閱[如何建立傳送埠](../../core/how-to-create-a-send-port2.md)，或[如何建立接收埠](../../core/how-to-create-a-receive-port.md)。 
  
-   無論配接器將訊息傳送至 SQL Server （輸出作業），或從 SQL Server （輸入操作） 接收訊息。 根據您要傳送或接收訊息，您將會建立傳送或接收埠，分別。  
  
    > [!NOTE]
    >  您也可以設定傳送，或藉由匯入繫結的組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]做為中繼資料產生的一部分。 如需設定使用此繫結檔案的連接埠的指示，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)  
  
-   [設定使用 WCF-SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-sql-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)