---
title: "設定靜態傳送埠以傳送 EDI 交換和通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b432c5e-ea0c-4174-bb4a-958b061c1827
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8645cd36447c814a5c43534e6c01de51e4be52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments"></a>設定靜態傳送埠以傳送 EDI 交換和通知
若要傳送 EDI 通知或交換，您可以使用靜態單向傳送埠或靜態請求-回應 (雙向) 傳送埠。  
  
-   如果您也將建立單向接收埠來接收 EDI 通知 (如果啟用此功能的話)，請建立單向傳送埠。  
  
-   建立請求-回應傳送埠，以透過相關聯的接收管線傳送 EDI 交換和接收 EDI 通知 (如果啟用此功能的話)。  
  
## <a name="configuring-a-static-one-way-send-port"></a>設定靜態單向傳送埠  
 若要建立靜態單向傳送埠來傳送 EDI 交換和通知，請使用下列組態：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|靜態單向|  
|**傳送埠屬性： 一般**|傳輸類型|可以是許多類型，包括 FILE、FTP、HTTP、MQSeries、MSMQ、SMTP、SOAP、SQL、WCF 類型以及 Windows SharePoint Services。|  
|**傳送埠屬性： 一般**|傳送處理常式|BizTalkServerApplication|  
|**傳送埠屬性： 一般**|傳送管線|EdiSend|  
|**傳輸屬性： 驗證 （針對 FILE 傳輸類型）**|當主控件沒有存取網路共用的權限時，即使用這些認證 (使用使用者名稱和密碼)|如果需要驗證則予以設定。|  
|**傳送埠屬性： 篩選**|屬性|BTS.MessageType<br /><br /> 注意：<br /><br /> 您也可以使用 BTS.ReceivePortName 或其他升級屬性。|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|**使用 BTS。交換的訊息類型：**<br /><br /> - **對於 X12**: `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`，或<br /><br /> - **對於 EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`<br /><br /> **使用 BTS。MessageType 的認可**:<br /><br /> -                     **對於 X12**: `http://schemas.microsoft.com/Edi/X12#X12_997_Root`，或<br /><br /> -                     **對於 X12**: `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`，或<br /><br /> -                     **對於 EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="configuring-a-static-solicit-response-send-port"></a>設定靜態請求-回應傳送埠  
 若要建立靜態請求-回應 (雙向) 傳送埠來傳送 EDI 交換和通知，請使用下列組態：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|靜態請求-回應|  
|**傳送埠屬性： 一般**|傳輸類型|可以是許多類型，包括 HTTP、MQSeries、MSMQ、SOAP、SQL 和 WCF 類型。 不能是 FILE、FTP、SMTP 或 Windows SharePoint Services。|  
|**傳送埠屬性： 一般**|傳送處理常式|BizTalkServerApplication|  
|**傳送埠屬性： 一般**|傳送管線|EdiSend|  
|**傳送埠屬性： 一般**|接收管線|EdiReceive|  
|**傳輸屬性： 驗證 （針對 HTTP 傳輸類型）**|當主控件沒有存取網路共用的權限時，即使用這些認證 (使用使用者名稱和密碼)|如果需要驗證則予以設定。|  
|**傳送埠屬性： 篩選**|屬性|BTS.MessageType<br /><br /> 注意：<br /><br /> 您也可以使用 BTS.ReceivePortName 或其他升級屬性。|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|**使用 BTS。交換的訊息類型：**<br /><br /> -                     **對於 X12**: `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`，或<br /><br /> -                     **對於 EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`<br /><br /> **使用 BTS。MessageType 的認可**:<br /><br /> -                     **對於 X12**: `http://schemas.microsoft.com/Edi/X12#X12_997_Root`，或<br /><br /> -                     **對於 X12**: `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`，或<br /><br /> -                     **對於 EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="setting-agreement-properties"></a>設定協議屬性  
 建立傳送埠之後，您需要設定所需的函式的傳送管線的協議屬性。 這些屬性會設定各種頁面中**協議屬性** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 解決方案的連接埠](../core/configuring-ports-for-an-edi-solution.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)