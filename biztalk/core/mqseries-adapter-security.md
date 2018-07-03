---
title: MQSeries 配接器安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, MQSeries adapters
- MQSeries adapters, security
ms.assetid: 0bd82c21-6b77-4a66-a4e9-4a91ba4a56c4
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca3ef0bf698515d00b60e7ffb8b2124576e9a001
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019515"
---
# <a name="security-with-the-mqseries-adapter"></a>使用 MQSeries 配接器安全性

MQSeries 配接器安全性是從保護 BizTalk 與 MQSeries 伺服器的安全開始。 如需保護 BizTalk Server 的資訊，請參閱[安全和保護您的資料](secure-and-protect-your-biztalk-messages.md)。 如需 MQSeries Server 安全性的詳細資訊，請參閱 IBM MQSeries Server 文件。  
  
> [!NOTE]
>  配接器會自動為 BizTalk Server 與 MQSeries Server 之間傳送和接收的訊息使用封包私密性。  

## <a name="adapter-security"></a>配接器安全性  
 安全地使用配接器本身需要注意四個部分：  
  
- 選擇 MQSAgent 的應用程式識別與成員  
  
- 使用配接器控制 BizTalk Server 帳戶  
  
- 保護佇列建立指令碼的安全  
  
- 適當地使用**SSO 分支機構應用程式**屬性  
  
  在組態期間指派給應用程式識別的帳戶不能是系統管理員帳戶。 此帳戶應該具備基本的必要權限—MQSeries 佇列的讀取和寫入權限。  
  
  請確定您只指派使用該配接器的 BizTalk Server 帳戶給 MQSAgent 角色。  
  
  當使用在佇列定義程序期間建立的匯出指令碼時，將指令碼保存在安全的區域。 只有使用指令碼的系統管理員才能擁有存取權。  
  
  如果您的應用程式使用 MQCIH 與 MQIIH 標頭屬性，將使用者認證放在輸出訊息，使用**SSO 分支機構應用程式**屬性上的**傳輸屬性**頁面。 如需有關這個屬性的詳細資訊，請參閱 <<c0> [ 如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器的結構](../core/structure-of-the-mqseries-adapter.md)   
 [何謂 MQSeries 配接器？](../core/what-is-the-mqseries-adapter.md)