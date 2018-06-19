---
title: 資料類型轉換的屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, data type conversion
- MQBYTE property [MQSeries adapters]
- MQLONG property [MQSeries adapters]
- MQCHAR property [MQSeries adapters]
- configuring [MQSeries adapters], data type conversion
ms.assetid: 5b81eab0-f7a1-42f3-b212-a211b2893fd5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3705f1d0a20a48f0683a15588891ef3fe60889cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238662"
---
# <a name="data-type-conversion-of-properties"></a>屬性的資料類型轉換
MQSeries 訊息中的標頭屬性是包含在訊息本身的資料結構。 MQSeries 配接器在傳送和接收訊息時，會自動驗證和轉換 MQSeries 訊息標頭中的特定值。  
  
 下表描述 MQSeries 資料型別及其驗證和轉換。  
  
|MQSeries 資料型別|驗證和轉換|  
|------------------------|-------------------------------|  
|MQLONG|MQSeries 會執行驗證。 轉換為長整數。 無法有效避免訊息移至 MQSeries 佇列的值。|  
|MQCHAR|轉換為字串。|  
|MQBYTE|轉換為包含字元 0-9 和 a-f 或 A-F 的字串，代表數字的十六進位值。|  
  
 許多 MQSeries 屬性都是 32 位元 (4 位元組) 不帶正負號的整數。 因為**uint**不是 Common Language Specification (CLS)-標準的類型，您必須將它們指派給**物件**型別才能在.NET 方法中使用它們。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)   
 [與 BizTalk Server 相關的屬性](../core/properties-related-to-biztalk-server.md)   
 [MQSeries 內容屬性](../core/mqseries-context-properties.md)