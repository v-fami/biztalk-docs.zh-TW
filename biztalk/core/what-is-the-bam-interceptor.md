---
title: 何謂 BAM 攔截器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM Interceptor object
- BAM, collecting data
- BAM, Interceptor object
- data, collecting [BAM]
ms.assetid: e0213c4e-e2f4-4bb0-bd27-e5810f7e39d9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9400e80a2f8e8acfdeb12e3d6e61a046151d1e7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289798"
---
# <a name="what-is-the-bam-interceptor"></a>何謂 BAM 攔截器？
## <a name="overview"></a>概觀 

BAM 攔截器是可讓您檢測應用程式以擷取感興趣的資料的物件。 下圖顯示 BAM 攔截器的角色以及與其他 BAM 元件的互動：  
  
 ![](../core/media/bam-config-api.gif "bam_config_api")  
BAM 攔截器  
  
 在可能有感興趣資料的每個應用程式步驟中，您呼叫攔截器 OnStep、提供步驟的識別碼，以及提供您在應用程式中使用的某些資料或任意物件。  
  
 您必須實作回呼函式，如此，當回呼發生時，回呼程序便會取得目前的步驟識別碼和資料物件。 基本上 BAM 攔截器只是將資料物件傳播至回呼。 擷取資料的實際邏輯存在於應用程式中。 例如，如果資料使用 XML 訊息的形式，則回呼將使用 XPath。 如需有關 Xpath 的詳細資訊，請參閱[訊息指派中使用的 Xpath](../core/using-xpaths-in-message-assignments.md)。  
  
 BAM 攔截器會根據以程式設計方式建立的組態，決定要在每個步驟要求哪些資料。 然後，BAM 攔截器會使用取得的資料呼叫所需的 DirectEventStream 或 BufferedEventStream，以便持續執行並將每次的時間當做引數傳遞給 OnStep。  
  
 呼叫每個步驟的攔截器並不是需要大量資源的作業。 如果您發出呼叫且此步驟沒有註冊任何資料，攔截器就會立即返回。 這表示沒有磁碟作業、沒有交易，甚至沒有記憶體配置，因此，幾乎不會對效能造成影響。 同時，您有機會擷取 BAM 的任何資料 (如果需要的話)。 受到的效能影響牽涉到資料擷取和資料的可用性的步驟將取決於您的實作`IBAMDataExtractor Interface`。  
  
 下列程式碼範例示範如何在組態和執行階段期間使用攔截器。  
  
## <a name="configuration-time"></a>組態階段  
 下列程式碼示範如何設定攔截器停止在應用程式的步驟 recvPO，並且要求「客戶名稱」和「客戶 SSN」：  
  
```  
ActivityInterceptorConfiguration cfg= new ActivityInterceptorConfiguration ("PurchaseOrder");  
...  
cfg.RegisterDataExtraction("CustomerName",recvPO,XpathName);  
cfg.RegisterDataExtraction("CustomerSSN",recvPO,XpathSSN);  
...  
BAMInterceptor interceptor=new BAMInterceptor();  
cfg.UpdateInterceptor(interceptor);  
...  
// The interceptor instance is ready.  
```  
  
 建立攔截器執行個體之後，您就可以儲存攔截器執行個體，以便稍後在執行階段使用。  
  
 您可以保留預先建立的不同攔截器，那些攔截器代表 BAM 資料和里程碑的不同喜好設定。 為了得到最佳效能，請使用 BinaryFormatter 類別序列化攔截器執行個體。  
  
## <a name="run-time"></a>執行階段  
 使用下列程式碼，以便在實際執行環境中的執行階段使用攔截器：  
  
```  
// Deserialize the Interceptor that was prepared before  
...  
es=new DirectEventStream(...)  
...  
Interceptor.OnStep(recvPO, data1, es, callback)  
...  
Interceptor.OnStep(approvePO, data2, es, callback)  
...  
```  
  
 其中：  
  
-   *recvPO*和*approvePO*是任意的物件，您用來識別您的應用程式中的步驟。  
  
-   *data1*和*data2*是任意的物件，您已在該點，並可能包含感興趣的資料 – 例如訂單的 XML 文件。  
  
-   *es*是 DirectEventStream 或 BufferedEvent 資料流，視效能需求而定。  
  
-   *回呼*是實作`IBAMDataExtractor Interface`。  
  
 Sdk > 範例[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)，示範如何使用攔截器，其中包含這兩種組態工具和範例執行階段應用程式。  
  
 BizTalk 協調流程引擎會配合攔截，以允許在執行階段使用追蹤設定檔編輯器變更為 BAM 收集的資料。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何判斷和設定活動事件寫入者角色](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)  
  
## <a name="see-also"></a>另請參閱  
 [BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)