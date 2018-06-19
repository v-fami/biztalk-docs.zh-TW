---
title: 動態 MLLP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e22fabb-0edf-4931-b8b2-74a5daccee4a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7d1d7046135de1dc1837d1fb8961ef440b5009
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204726"
---
# <a name="dynamic-mllp-adapter"></a>動態 MLLP 配接器
從開始[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]，MLLP 配接器屬性，可以在執行階段使用單向或雙向 （要求-回應） 傳送埠設定。  
  
## <a name="dynamic-properties"></a>動態屬性  
 下列屬性處於**GlobalPropertySchemas**命名空間：  
  
|屬性|Description|  
|--------------|-----------------|  
|訊息 (MLLP.acceptableACKCodes) = 「 所有通知代碼 」。|數值包括：<br /><br /> -所有通知代碼<br />-AA 和 CA<br />-AA、 CA、 AE 和 CE<br />-AA、 CA、 AR 和 CR<br /><br /> 這是類似於**接受通知碼**靜態 MLLP 傳送埠中的屬性。|  
|訊息 (MLLP。CarriageReturn) ="0 d"。|ASCII 歸位字元|  
|訊息 (MLLP.endBlockDelimiter) ="1 c";|ASCII 結束區塊字元|  
|訊息 (MLLP.startBlockDelimiter) ="0b";|開始區塊的 ASCII 字元|  
|訊息 (MLLP.timeout) ="60000";|後的非作用中的傳送通訊端上 BTAHL7 伺服器將會逾時期間內 （0 為不會逾時）|  
|SendPortName(Microsoft.XLANGs.BaseTypes.Address) ="127.0.0.1:11000";|位址和連接埠將訊息路由傳送|  
|SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) ="MLLP";|類型的配接器 (MLLP)|  
  
## <a name="additional"></a>其他  
  
-   當 HL7 協調流程中建立多部分訊息，訊息部分在建立此順序：  
  
    1.  MSH 區段  
  
    2.  BodySegments  
  
    3.  ZSegments  
  
     如果您以不同順序指定的訊息部分，就會發生下列錯誤：  
  
     WrongBodyPartException  
  
-   若要支援動態路由協調流程上，可以指定配接器路由屬性。  
  
## <a name="see-also"></a>另請參閱  
 [組態參數傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP 的接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)