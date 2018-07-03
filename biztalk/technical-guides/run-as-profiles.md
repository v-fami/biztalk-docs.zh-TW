---
title: 執行身分設定檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98ac0a0c-91d8-4d12-aa40-2ad2e29ec784
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a1281fa77956d96e4461a91fffb737499327ef2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982087"
---
# <a name="run-as-profiles"></a>執行身分設定檔
第一次匯入 BizTalk Server 核心程式庫管理組件時，它會建立兩個新執行身分設定檔：  
  
- **BizTalk Server 探索帳戶**。 此設定檔是與 BizTalk Server 角色元件的所有探索相關聯。  
  
- **BizTalk Server 監視帳戶**。 此設定檔與所有監視器和工作有關聯。  
  
  根據預設，所有探索、 監視器和 BizTalk Server 管理組件預設都會使用 「 預設動作帳戶 」 執行身分設定檔中定義的帳戶中定義的工作。  如果指定系統的預設動作帳戶沒有探索或監視 BizTalk 的必要權限，然後這些系統可以繫結到 BizTalk Server 執行身分設定檔中確實具備存取 BizTalk Server 的更為專屬認證。  
  
  若要設定 BizTalk server 的執行身分設定檔的一般步驟如下：  
  
### <a name="to-configure-run-as-profiles"></a>若要設定執行身分設定檔  
  
1.  識別預設動作帳戶沒有足夠的權限，來監控 BizTalk Server 的其中的目標電腦的名稱。  
  
2.  每個系統建立或使用現有的一組認證至少具有中所討論的 BizTalk Server 權限[低權限環境](../technical-guides/low-privilege-environments.md)區段，此管理組件指南。  
  
3.  每一組步驟 2 中識別的認證，請確定管理群組中存在對應的執行身分帳戶。 如有必要，請建立執行身分帳戶。  
  
4.  在 [設定目標和執行身分帳戶之間的對應**執行身分帳戶**的每個執行身分設定檔] 索引標籤。