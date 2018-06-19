---
title: 執行身分設定檔 |Microsoft 文件
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
ms.openlocfilehash: 69fa6c9401f606619b2fb8d22d95ded48c18a092
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301974"
---
# <a name="run-as-profiles"></a>執行身分設定檔
第一次匯入 BizTalk Server 核心程式庫管理組件時，它會建立兩個新執行身分設定檔：  
  
-   **BizTalk Server 探索帳戶**。 此設定檔是與 BizTalk Server 角色元件的所有探索相關聯。  
  
-   **BizTalk Server 監視帳戶**。 此設定檔與所有監視器和工作有關聯。  
  
 根據預設，所有探索、 監視器和 BizTalk Server 管理組件預設都會使用 「 預設動作帳戶 」 執行身分設定檔中定義的帳戶中定義的工作。  如果給定系統的預設動作帳戶沒有探索或監視 BizTalk 的必要權限，這些系統可以結合到 BizTalk Server 執行身分設定檔中確實具備存取 BizTalk Server 中的更為專屬認證。  
  
 若要設定 BizTalk Server 的執行身分設定檔的一般步驟如下：  
  
### <a name="to-configure-run-as-profiles"></a>若要設定執行身分設定檔  
  
1.  識別預設動作帳戶沒有足夠的權限，來監控 BizTalk Server 的位置的目標電腦的名稱。  
  
2.  針對每一個系統建立或使用現有的一組認證至少擁有中討論的 BizTalk Server 權限[低權限環境](../technical-guides/low-privilege-environments.md)本管理組件指南 > 一節。  
  
3.  針對每個步驟 2 中識別的認證集，請確定對應執行身分帳戶存在於管理群組。 如果有必要，請建立執行身分帳戶。  
  
4.  設定目標與執行身分帳戶之間的對應上**執行身分帳戶**的每個執行身分設定檔 索引標籤。