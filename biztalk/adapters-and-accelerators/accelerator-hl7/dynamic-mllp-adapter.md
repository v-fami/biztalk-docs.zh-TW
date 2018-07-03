---
title: 動態 MLLP 配接器 |Microsoft Docs
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
ms.openlocfilehash: 0b1ad131716f5b1bb1b5abdfb7985fa93f2ae41c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999807"
---
# <a name="dynamic-mllp-adapter"></a>動態 MLLP 配接器
從開始[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]，MLLP 配接器屬性可以設定在執行階段使用單向或雙向 （要求-回應） 傳送埠。  
  
## <a name="dynamic-properties"></a>動態屬性  
 下列屬性位於**GlobalPropertySchemas**命名空間：  
  
|屬性|描述|  
|--------------|-----------------|  
|訊息 (MLLP.acceptableACKCodes) ="所有通知程式碼 」，|數值包括：<br /><br /> -所有通知代碼<br />-AA 和 CA<br />-AA、 CA、 AE 和 CE<br />-AA、 CA、 AR 及 CR<br /><br /> 這是類似**接受通知碼**靜態 MLLP 傳送埠中的屬性。|  
|訊息 (MLLP。CarriageReturn) ="0 d";|ASCII 換行字元|  
|訊息 (MLLP.endBlockDelimiter) ="1 c";|結束區塊的 ASCII 字元|  
|訊息 (MLLP.startBlockDelimiter) ="0b";|開始區塊的 ASCII 字元|  
|訊息 (MLLP.timeout) ="60000";|之後的非作用中的傳送通訊端上 BTAHL7 伺服器將會逾時期限 （0 為不會逾時）|  
|SendPortName(Microsoft.XLANGs.BaseTypes.Address) ="127.0.0.1:11000";|位址和連接埠將訊息路由傳送|  
|SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) ="MLLP";|類型的配接器 (MLLP)|  
  
## <a name="additional"></a>其他  
  
- HL7 協調流程中建立多部分訊息，請時，建立訊息組件在此順序：  
  
  1. MSH 區段  
  
  2. BodySegments  
  
  3. ZSegments  
  
     如果您在不同的順序指定的訊息部分，就會發生下列錯誤：  
  
     WrongBodyPartException  
  
- 若要支援動態路由協調流程上，可以指定配接器路由屬性。  
  
## <a name="see-also"></a>另請參閱  
 [組態參數，傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP 接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)