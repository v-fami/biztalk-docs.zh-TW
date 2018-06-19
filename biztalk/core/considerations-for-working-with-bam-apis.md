---
title: 使用 BAM Api 的考量事項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd8ccf63-6989-4ad6-a193-cf3043e9a466
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b00eb00013fefde42e1972b89a661d0a2ba0de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237838"
---
# <a name="considerations-for-working-with-bam-apis"></a>使用 BAM API 的考量
在使用 "Microsoft.BizTalk.Bam.EventObservation.EventStream" 物件時，例如 DirectEventStream、BufferedEventStream、MessagingEventStream，或者是 OrchestrationEventStream，BAM 會在擷取里程碑時自動採用國際標準時間 (Coordinated Universal Time，UTC) 格式加以記錄 (亦稱為格林威治標準時間)。 當您使用 API 將日期/時間傳送給 BAM 時，所收到的格式在傳送時尚未轉換為 UTC 格式。 在開發 BAM 方案時，請將以下事項列入考量：  
  
-   追蹤自 BizTalk Server 的資料是以 UTC 格式接收。 這可能與來自事件資料流的其他資料格式不一致。  
  
-   如果您使用事件資料流 API 以本地時間格式來提供日期與時間追蹤資料，則 BAM 入口網站的資料會有錯誤，因為預期的 BAM 資料中，所有的時間都應為 UTC 格式。  
  
 如果您現有的應用程式是使用本地時間，而您現在正打算升級並計畫使用 BAM 入口網站，則請務必將資料修改為符合 UTC 格式要求。 同時，您需要修改自訂應用程式以轉換成 UTC 格式。  
  
## <a name="see-also"></a>另請參閱  
 [實作 BAM 解決方案](../core/implementing-bam-solutions.md)