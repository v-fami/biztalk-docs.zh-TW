---
title: 觸發事件與訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- health care organizations, HL7 messages
- trigger events
- messages, trigger events
- messages, about messages
ms.assetid: e93b397c-8cbe-4589-aa88-e474d7722174
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 309d420d97cdc22c4f0eaca30bb6426e295cbe33
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971607"
---
# <a name="trigger-events-and-messages"></a>觸發程序事件和訊息
在數位醫療保健系統中，應用程式會建立 HL7 訊息，因為現實世界的事件，例如實驗室順序或藥物順序放置。 HL7 組織已寫入 HL7 標準根據健康照護真實世界中的事件會建立資料流在應用程式，即使這些應用程式橫跨異質系統需要的假設。 HL7 標準呼叫真實世界本項*觸發程序事件*。 自動化的系統必須有系統地識別觸發程序事件。  
  
 若要擴充這個概念，請考慮下列案例。 在醫院抵達，病患註冊在醫院中使用的病患的系統管理軟體應用程式。 在認可的病患記錄，應用程式需要通知其他醫院的應用程式 （例如會計、 實驗室和等等） 有關病患的註冊。 在 應用程式之間共用這項資訊是必要的以便使用這些應用程式的實體可以提供所需的服務與病患。 註冊病患的動作是一種觸發程序事件。 Web 應用程式通常會藉由建立 HL7 訊息，其中包含的病患記錄的資料建立此觸發程序事件。  
  
 觸發程序事件永遠會導致建立一或多個觸發動作處理訊息的應用程式中的訊息。 觸發程序事件都有關，IT 人員有內嵌 Microsoft BizTalk Accelerator for HL7 的部署案例中 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 在醫院特定業務應用程式中。 即使在這種部署案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不需要留意的觸發程序事件，觸發程序事件產生的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [使用 HL7 2.xml 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [HL7 傳訊](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)