---
title: "開發協調流程的安全性考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, orchestrations
- messages, subscriptions
- orchestrations, security
- messages, security
ms.assetid: a29b2018-4a8f-49ad-a817-6f279db3f801
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e020759a8d389461978a4de4138bcc139d527539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-developing-orchestrations"></a>開發協調流程的安全性考量
設計協調流程時，您應該考量可能的安全性問題。  
  
## <a name="avoid-subscriptions-based-on-content-from-untrusted-messages"></a>避免訂閱來自不信任之訊息的內容  
 為確保低權限訊息不會起始可能依據訊息內容建立訂閱的協調流程執行個體，強烈建議您，請勿讓您的協調流程依據不信任之訊息內容建立訊息訂閱。  
  
 如需中的安全性資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[保護 BizTalk Server](../core/securing-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立協調流程](../core/creating-orchestrations.md)   
 [關於協調流程](../core/about-orchestrations.md)