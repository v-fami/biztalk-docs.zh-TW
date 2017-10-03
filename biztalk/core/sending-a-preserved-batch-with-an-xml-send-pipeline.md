---
title: "傳送保留批次與 XML 傳送管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6765576a-134f-4856-911c-2f603b6479bd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14bd61538398bb11967cbbe750a4fadc016a5168
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sending-a-preserved-batch-with-an-xml-send-pipeline"></a>透過 XML 傳送管線來傳送保留批次
通常保留批次會透過 EDI 傳送管線來傳送。 但是，您也可以使用 XML 傳送管線來傳送保留批次。 因為 EDI 接收管線所產生和放入 MessageBox 中的保留批次具有 XML 格式，所以 XML 傳送管線可以逐一處理 XML 格式的批次。  
  
 若要透過 XML 傳送管線來傳送保留批次，您必須針對交換中的每種訊息類型，部署具有適用之批次結構描述和文件結構描述的專案。 此外，您也需要針對您在專案中所部署的批次結構描述變更其命名空間。 若沒有這樣做，在保留批次 XML 檔案中的命名空間就無法對應到該批次結構描述的命名空間。 您必須依據下表方式來變更該批次結構描述的命名空間：  
  
|對於這種編碼類型：|變更在批次結構描述中的這個命名空間：|對於下列命名空間：|  
|-----------------------------|------------------------------------------------|---------------------------------|  
|EDIFACT|`http://schemas.microsoft.com/Edi/Edifact`|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML`|  
|X12|`http://schemas.microsoft.com/Edi/X12_BatchSchema`|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`|  
  
 這些變更作業與 EDI 組合器無關。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 批次](../core/configuring-edi-batches.md)