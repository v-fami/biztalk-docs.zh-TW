---
title: 設定接收埠內送 mdn |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d156beae-e145-48de-9f02-37457073ef97
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8585ae946e15d2677e225d42f6c123d5dd5e8e49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968308"
---
# <a name="configuring-a-receive-port-for-incoming-mdns"></a>設定內送 MDN 的接收埠
若要接收 AS2 MDN，請針對接收此訊息並將回應傳回給合作對象的作業，建立單向 HTTP 接收埠。  
  
 用來接收 AS2 訊息的雙向要求-回應接收埠，不應用來接收 MDN 訊息。 針對 MDN 使用要求-回應接收埠，將導致 200OK 訊息無法在回應內送 MDN 時傳回，進而產生不必要的 MDN 傳輸嘗試作業。  
  
 您可以使用 AS2Receive 或 AS2EdiReceive 管線來處理收到的 MDN。 不過，如果您使用 AS2EdiReceive，您無法將 MDN 路由至 MessageBox 設定**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性**通知**頁面單向協議索引標籤。嘗試這樣做，將會造成 EDI 錯誤。因為 MSN 將會傳遞至 EDI 解碼器，但該解碼器並不能處理 MDN。 如果 MDN 沒有傳送至 MessageBox，AS2Decoder 便會使用 MDN，這樣 MDN 便不會傳遞至 EDI 解碼器。  
  
 請使用下列組態來建立接收埠：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**接收埠屬性： 一般**|連接埠類型|單向|  
|**接收位置屬性： 一般**|傳輸類型|HTTP<br /><br /> **請注意**只有 HTTP 配接器可以用於傳輸 Mdn，也就是 EDIINT/AS2 編碼訊息。 這種傳輸無法搭配 HTTP 配接器以外的配接器運作。|  
|**接收位置屬性： 一般**|接收處理常式|BizTalkServerIsolatedHost|  
|**接收位置屬性： 一般**|接收管線|AS2Receive 或 AS2EdiReceive|  
|**HTTP 傳輸屬性**|虛擬目錄加 ISAPI 延伸模組|/\<虛擬目錄名稱\>/BTSHTTPReceive.dll|  
  
## <a name="see-also"></a>請參閱  
 [設定 AS2 解決方案的連接埠](../core/configuring-ports-for-an-as2-solution.md)