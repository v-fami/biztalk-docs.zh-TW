---
title: 監視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7effa38f-f9f2-40b7-8d8b-fa13cf94aa4f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c45bb70e3f92f4c85def07add4390a0451cb87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298902"
---
# <a name="monitoring"></a>監視
根據預設，所有的 BizTalk Server 監控和工作使用的預設動作帳戶沒有任何特定執行身分帳戶定義的執行身分設定檔的 BizTalk Server 監視帳戶中的目標時。 若要設定執行身分帳戶與權限所需的監控 BizTalk Server 的最小集合，則需要下列的權限：  
  
-   帳戶必須是受監視的電腦內建 Administrators 群組和效能監視器使用者群組的成員。  
  
-   帳戶必須是在 SQL 執行個體或裝載資料庫及 BizTalk 群組所監視的工作的執行個體的 SysAdmin 角色的成員。  
  
-   監控 BizTalk server，帳戶必須是 BizTalk 操作員 」 群組的一部分。  
  
-   為了透過 SCOM 主控台中執行工作，帳戶必須是 BizTalk 應用程式使用者群組的一部分。  
  
-   執行系統管理工作，帳戶必須是 BizTalk 系統管理員群組的一部分。