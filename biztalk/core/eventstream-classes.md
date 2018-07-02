---
title: EventStream 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3e7a6b3-69cc-4312-9074-acccd1175d37
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c4cb000d479a51d2215bda6349adfa6df39338a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973559"
---
# <a name="eventstream-classes"></a>EventStream 類別
BAM 的 EventStream API 位於 Microsoft.BizTalk.BAM.EventObservation 命名空間中。 若要針對這些 API 撰寫程式碼，您必須在開發電腦上安裝下列 DLL：  
  
- Microsoft.BizTalk.BAM.EventObservation.dll  
  
- Microsoft.biztalk.bam.xlangs.dll 新增： 此 DLL 時需要撰寫程式碼的協調流程事件資料流。  
  
- Microsoft.BizTalk.Pipeline.dll： 使用訊息事件資料流的編碼管線內容時需要這個 DLL。  
  
  將此 DLL 加入到專案參考中，並利用下列 using 陳述式在您的程式碼中包含命名空間：  
  
```  
using Microsoft.BizTalk.Bam.EventObservation;  
```  
  
 **類別**  
  
|[屬性]|描述|  
|----------|-----------------|  
|DirectEventStream (DES)|同步、無延遲|  
|BufferedEventStream (BES)|非同步、高輸送量、一些延遲|  
|OrchestrationEventStream (OES)|非同步、參與 BizTalk 協調流程交易|  
|IPipelineContext 介面|非同步、參與 BizTalk Server 管線交易。 用來建立訊息事件資料流 (MES)。|  
  
 您應該根據下列因素來選擇 API：  
  
- 如果您擔心延遲，請選擇 DES，此時會使用與 BAM 主要匯入資料庫同步的方式來保存資料。 除 DES 外的所有其他 EventStream 類別都是非同步類別，因而會有一些延遲 。 資料會先保存在 MessageBox 中，接著再由 TDDS 進行處理，將資料移到 BAMPrimaryImport 資料庫中。  
  
- 如果您擔心事件插入的效能和輸送量，請選擇非同步 API。  
  
- 如果您撰寫的應用程式在未安裝 BizTalk Server 的電腦上執行，請使用 DES 和 BES (換句話說，這些 API 可用於非 BizTalk 應用程式)。  
  
- 如果您的應用程式要在已安裝 BizTalk Server 的電腦上執行，請使用 MES 和 OES (這些 API 只能從 BizTalk 應用程式使用)。  
  
  -   如果您希望 BAM 事件持續性會與管線交易同步，您應該使用訊息事件資料流。  
  
  -   OES 相當於 MES，但它適用於 BizTalk 協調流程。  
  
  您可能會在一些情況下想要混合 EventStream 類型。 例如在管線處理中，您可能會想要擷取 BAM 中的特定資料，而不論管線是否回復其交易。 特別是，您可能會想要擷取在管線處理期間有多少訊息失敗及多少重試次數的相關資料。 若要在這種情況下擷取資料，您應該使用 BES。  
  
  所有的非同步 EventStream (BES、MES 和 OES) 都會先將資料保存在 BizTalk MessageBox 資料庫中。 然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。  
  
> [!NOTE]
>  為了確保 EventStream 呼叫不會從 BizTalk 應用程式產生瓶頸，建議您最好使用非同步 API。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [OrchestrationEventStream](../core/orchestrationeventstream.md)  
  
-   [訊息事件資料流](../core/messaging-event-streams.md)