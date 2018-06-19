---
title: BizTalk 群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Management database, groups
- groups
- groups, Management database
- groups, about groups
ms.assetid: 197cbcf6-c722-4cbb-9642-3cb8a34757e2
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9cd38012f0e2a7ba5f4cfcb56ae63678aacbf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231278"
---
# <a name="biztalk-groups"></a>BizTalk 群組

## <a name="overview"></a>概觀
*BizTalk 群組*是通常代表企業、 部門、 集線器或需要包含的 BizTalk Server 實作其他業務單位的組織單位。 BizTalk 群組與 BizTalk Server 管理資料庫 (在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是為 BizTalk Server 組態資料庫) 有一對一的關係。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組可包含多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦，但任一部指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦只能與單一 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組關聯。  
  
 「BizTalk 管理」資料庫會儲存 BizTalk 群組及該群組中 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的組態資訊。 此組態資訊指定伺服器的訊息處理邏輯部分以及該邏輯將實際執行的地方。 如需有關 BizTalk Server 管理資料庫的詳細資訊，請參閱[BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。  
  
 對群組中每個伺服器安裝必須指定相同的 BizTalk Server 管理資料庫，如此即可從管理主控台管理每個伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [管理群組](../core/managing-groups.md)   
 [實體](../core/entities.md)