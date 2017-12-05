---
title: "MSMQT 過時 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 007d65ce-d2a2-4602-80c8-55b26617f397
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f869dde7cb4c793e1e36beee6a20bc89d19272e8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="msmqt-deprecation"></a>MSMQT 過時
MSMQT 功能已經自 BizTalk Server 移除。 在協調流程設計師中，MSMQT 傳輸選項仍然可在設計階段連接埠組態精靈中下當您選擇的映像中所示**現在指定**選項**連接埠繫結**.  
  
 **顯示 MSMQT 傳輸的連接埠組態精靈**  
  
 ![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")  
  
## <a name="biztalk-server-projects"></a>BizTalk Server 專案  
 新的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案不應該使用 MSMQT 傳輸選項。 應用程式部署至 BizTalk Server 將會失敗並出現錯誤**通訊協定類型"MSMQT"找不到**。  
  
## <a name="migrated-biztalk-server-projects"></a>移轉的 BizTalk Server 專案  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案可以移轉至 BizTalk Server 使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]如中所述的轉換精靈[移轉 BizTalk Server 專案](../core/migrating-a-biztalk-server-project.md)。 必須在部署至 BizTalk Server 之前手動重新設定包含通訊埠設定為使用 MSMQT 傳輸專案。 建議的重新設定是使用 MSMQ 配接器。  如需 MSMQ 配接器的詳細資訊，請參閱[什麼是 MSMQ 配接器？](../core/what-is-the-msmq-adapter.md)。  
  
## <a name="see-also"></a>請參閱  
 [從 MSMQT 配接器移轉至 MSMQ 配接器](../core/migrating-from-the-msmqt-adapter-to-the-msmq-adapter.md)