---
title: "字元編碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a0c21c8-3318-4533-9734-89302527cb67
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 319ddd649e47e053fe2896d577f28b72602593e3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="character-encoding"></a>字元編碼
對於從 BizTalk Adapter for TIBCO EMS 傳輸到 EMS 的訊息，TIBCO Enterprise Message Service (EMS) 支援許多字元編碼方式。 訊息是使用預設的 UTF-8 編碼方式所編碼的。 接收訊息時，配接器會先判斷訊息的編碼方式並轉換適當的字串為 UTF-8 後，才將訊息提供給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 所有的字元轉換是使用 Microsoft .NET Framework 類別，因此配接器支援這個相同架構所提供的字元轉換。  
  
## <a name="running-in-a-clustered-environment"></a>在叢集環境中執行  
 發佈到佇列中的訊息，會以 EMS 伺服器預先決定的順序，讓取用者使用，所以在叢集 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中，只會有一個配接器收到該訊息。 佇列可以設定為*獨佔*。 這代表只有對佇列自行註冊為訊息取用者的第一個配接器，會接收到訊息。 只有在獨佔取用者不認可訊息接收時，EMS 伺服器才會傳送訊息給其他取用者。 獨佔佇列組態是由 EMS 組態執行的，用戶端無法進行這項設定。  
  
> [!NOTE]
>  關於主題訂閱： 因為中的所有介面卡[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組的設定都相同，它們都會一起訂閱訊息，每個主題訂閱接收訊息。  
  
## <a name="transaction-support"></a>交易支援  
 在協調流程傳送埠需要時，配接器提供交易支援。 配接器聆聽訊息時不提供 EMS 伺服器的交易支援，然而，當在訊息成功提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 後，配接器就會認可所有訊息的接收。 EMS 會重寄未認可的訊息給配接器。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for TIBCO EMS 中的安全性](../core/security-in-biztalk-adapter-for-tibco-ems.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)