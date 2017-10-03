---
title: "訊息部分 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- messages, message parts
- segments, messages
ms.assetid: 2bb6557e-cd4a-42b7-8bc2-f8b53a59517e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b6b02096a0cc75460552a6cd1dd56ef9e6c4e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-parts"></a>訊息部分
HL7 訊息包含下列部分： 區段、 資料欄位、 元件和選擇性子元件。 HL7 訊息有下列的階層式結構：  
  
 區段  
  
 資料欄位  
  
 元件  
  
 子元件 （選擇性）  
  
 **區段**  
  
 區段是資料欄位的邏輯群組。 區段位於最高的層級 （深度 1） 訊息階層。 每個區段具有包含三個字元常值的名稱。 下表顯示 ADT 訊息類型所包含的區段名稱的範例。  
  
|區段程式碼|Description|  
|------------------|-----------------|  
|MSH|訊息標頭|  
|EVN|事件類型|  
|PID|病患資訊|  
  
 HL7 訊息有*訊息標頭*和*主體*。 MSH 區段會定義訊息的標頭，且所有其他類型的區段構成訊息的本文。  
  
 **資料欄位**  
  
 資料欄位是發生訊息階層的深度 2 個字元的字串。 資料型別定義資料欄位： 簡單與複雜。  
  
 下列範例示範的 MSH 和 EVN 區段包含 MSH.1 和 EVN.1 資料欄位的階層式的訊息結構：  
  
 MSH  
  
 MSH.1  
  
 EVN  
  
 EVN.1  
  
 **元件和子元件**  
  
 元件和子元件進一步包含資料欄位內的資料。 元件和子元件可以重複相同的欄位中。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)