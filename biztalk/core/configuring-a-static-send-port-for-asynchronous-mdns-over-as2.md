---
title: "設定透過 AS2 之非同步 Mdn 的靜態傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc43e767-d9d7-4b02-b3fc-0cfdfd6e61c4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ccae5741ada6db57538289911a97e2ad3d9dfce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-static-send-port-for-asynchronous-mdns-over-as2"></a>設定透過 AS2 之非同步 MDN 的靜態傳送埠
本主題說明如何設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，使其透過靜態傳送埠傳送非同步 EDIINT/AS2 編碼 MDN 訊息。 進行這項設定時必須建立靜態傳送埠，若有必要，也須設定供傳送埠使用的加密憑證。  
  
> [!NOTE]
>  您可以設定動態傳送埠傳送 MDN 訊息，而不使用靜態傳送埠。 如需詳細資訊，請參閱[設定透過 AS2 之非同步 Mdn 的動態傳送埠](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)。  
  
 若要傳送 MDN 訊息，請以下列組態建立單向 HTTP 傳送埠：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|靜態單向傳送埠|  
|**傳送埠屬性： 一般**|傳輸類型|HTTP**附註：**只有 HTTP 配接器可以用於傳輸 EDIINT/AS2 編碼訊息。 這種傳輸無法搭配 HTTP 配接器以外的配接器運作。|  
|**傳送埠屬性： 一般**|傳送處理常式|BizTalkServerApplication|  
|**傳送埠屬性： 一般**|傳送管線|AS2Send|  
|**HTTP 傳輸屬性**|目的地 URL|\<目的地 URL 字串 >|  
|**HTTP 傳輸屬性**|啟用區塊編碼|已清除|  
|**傳送埠屬性： 篩選**|屬性|EdiIntAS.IsAS2AsynchronousMdn**附註：**您也應該指定額外的篩選運算式，以確保只有中指定之位址為目標的 MDN 訊息傳送埠所拾取此訂用帳戶篩選。|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|True|  
|**傳送埠屬性： 憑證**|一般名稱和指紋|如果對外寄 MDN 訊息使用加密憑證，請輸入憑證名稱和指紋。|  
  
 非同步 MDN 應傳送至中指定的位址**回條傳遞選項**收到的 AS2 訊息的標頭。 動態傳送埠將會自動執行這個動作，而靜態傳送埠將訊息傳送到**目的地 URL**的傳送埠屬性中。 使用靜態傳送埠傳送非同步 MDN 時，請確定要傳送的目標 URL 正確無誤。  
  
## <a name="functionality"></a>功能  
 傳送埠和管線必須執行下列動作，才能傳送 MDN：  
  
-   根據 `EdiIntAS.IsAS2AsynchronousMdn==True` 屬性進行篩選，以便收取該 MDN。  
  
-   建置 AS2 訊息。 如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
-   將 MDN 路由傳送至傳送埠中定義的位址。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 方案的連接埠](../core/configuring-ports-for-an-as2-solution.md)