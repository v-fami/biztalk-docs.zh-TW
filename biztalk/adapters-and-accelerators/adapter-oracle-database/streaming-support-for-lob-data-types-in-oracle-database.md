---
title: 資料流的 Oracle 資料庫中的 LOB 資料類型支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- streaming, node-value
- streaming
- LOB data
- streaming, node
ms.assetid: a4943cdf-8336-48ac-b592-52ec514e7300
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3f052b5051e511179ed0a3b371a619b315a16af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214646"
---
# <a name="streaming-support-for-lob-data-types-in-oracle-database"></a>Oracle 資料庫中的 LOB 資料類型的串流支援
Oracle 資料庫支援資料流處理大型物件 (LOB) 資料類型。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援訊息資料流處理，這樣就能 LOB 資料端對端 Oracle 資料庫與配接器用戶端之間傳送資料流。 不過，資料流不支援相同的方式跨所有的程式撰寫模型時使用配接器。  
  
 下列示範如何端對端 LOB 資料類型的資料流配接器支援在不同的程式設計模型。  
  
|作業|WCF 通道模型|WCF 服務模型|BizTalk Server|  
|---------------|-----------------------|-----------------------|--------------------|  
|資料表/檢視表的 Insert 作業|不支援|不支援|不支援|  
|資料表/檢視表選取作業|支援|不支援|支援|  
|資料表/檢視表更新作業|不支援|不支援|不支援|  
|資料表/檢視表刪除作業|不支援|不支援|不支援|  
|資料表/檢視表 ReadLOB 作業|支援;不過，ReadLOB 作業會顯示主要是為了支援資料流 WCF 服務模型中，不建議以供 WCF 通道模型。 相反地，請使用選取的作業或 SQLEXECUTE 操作。|支援|BizTalk Server 不支援 ReadLOB 作業。 請改用選取作業。|  
|資料表/檢視表 UpdateLOB 作業|支援|不支援|支援|  
|SQLEXECUTE 操作|在回應中支援|不支援|在回應中支援|  
|預存程序和函式的作業|在回應中支援|不支援|在回應中支援|  
|POLLINGSTMT 作業|支援|不支援|支援|  
  
 更完整如何支援資料流的 LOB 資料類型的配接器和如何加以支援當您使用各種程式設計模型與配接器的詳細資訊，請參閱[串流處理大型物件資料類型](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle 資料庫的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)