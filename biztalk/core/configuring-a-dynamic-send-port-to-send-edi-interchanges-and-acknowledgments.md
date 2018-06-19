---
title: 設定動態傳送埠以傳送 EDI 交換和通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a124059c-c29c-4a7f-a8a3-13dffc09ae5c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a793fc22394c2b4d294bcd48fae1f9403ae9278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232814"
---
# <a name="configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments"></a>將動態傳送埠設定為傳送 EDI 交換和通知
若要傳送 EDI 交換或通知，您可以使用靜態傳送埠或動態傳送埠。 動態傳送埠可讓您交換傳送至多個目的地，其中，因為它以解析協議，並決定目的地址根據 DestinationPartyName 內容屬性中的值。  
  
> [!NOTE]
>  如果您要傳送 EDI 交換接收，XML 訊息為基礎，而且您使用通過接收管線接收該應用程式，您就必須升級 DestinationPartyName 內容屬性。 如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
> [!NOTE]
>  如果動態傳送埠會傳送通知，表示 DestinationPartyName 內容屬性已經升級，因為接收交換之連接埠中的 EDI 解譯器會填入通知上的 DestinationPartyName 屬性。  
  
 若要建立單向動態傳送埠，請使用下列組態：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|動態單向|  
|**傳送埠屬性： 一般**|傳送處理常式|BizTalkServerApplication|  
|**傳送埠屬性： 一般**|傳送管線|EdiSend|  
|**檔案傳輸屬性： 驗證**|當主控件沒有存取網路共用的權限時，即使用這些認證 (使用使用者名稱和密碼)|如果需要驗證則予以設定。|  
|**傳送埠屬性： 篩選**|屬性|BTS.MessageType|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|**交換**:<br /><br /> - `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`或<br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`或<br /><br /> **針對通知**:<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_997_Root`或<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`或<br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="setting-agreement-properties"></a>設定協議屬性  
 建立傳送埠之後，您需要設定所需的函式的傳送管線的協議屬性。 這些屬性會設定各種頁面中**協議屬性** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 解決方案的連接埠](../core/configuring-ports-for-an-edi-solution.md)