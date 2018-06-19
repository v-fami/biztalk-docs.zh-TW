---
title: 如何選取即時或封存資料來源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Management database, archived data
- Management database, real-time data
- HAT, real-time data
- archived data, Management database
- HAT, archived data
- real-time data, HAT
- real-time data, Management database
- archived data, HAT
ms.assetid: e2325823-22e1-4a1a-865b-15757b215b29
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7172a822a71e2b0d7dc621e6c1e11b055b723bd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255286"
---
# <a name="how-to-select-a-live-or-archived-data-source"></a>如何選取即時或封存的資料來源
BizTalktracking 可讓您存取封存資料和即時資料。 您可以選取即時或封存資料來源從主要**BizTalk Server 管理**節點 BizTalk Server 管理主控台。  預設來源是從「BizTalk 管理」資料庫擷取的即時資料。 若您選擇使用封存的資料，則必須選取要使用的適當伺服器與資料庫。  
  
-   封存資料：分析封存資料可讓您檢查商務及系統這兩者中的趨勢，因為您可以視需要回溯以前的資料。 若選取封存資料，則也必須選取包含封存資料的適當 SQL Server 和 SQL 資料庫。  
  
     封存的資料由所選取指定**連接至現有的追蹤資料庫...**.  
  
-   即時資料：分析即時資料可讓您監控協調流程和管線，這樣就能找出及修正開發或執行環境中的問題。 監控即時資料也可以校正系統中的問題，像是訊息遭到擱置的原因。  
  
     藉由選取指定即時資料**連接至現有的群組...**.  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。  
  
### <a name="to-select-live-data"></a>選取即時資料  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  按一下主要**BizTalk Server 管理**節點。  
  
3.  按一下**連接至現有的群組...**  
  
4.  在**SQL Server 名稱**方塊中，輸入裝載 BizTalk 管理資料庫伺服器的名稱。  
  
5.  在**資料庫名稱**下拉式清單方塊中，選取**BizTalkMgmtDb**。  
  
6.  按一下 **[確定]**。  
  
### <a name="to-select-archived-data"></a>選取封存的資料  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  按一下主要**BizTalk Server 管理**節點。  
  
3.  按一下**連接至現有的追蹤資料庫...**  
  
4.  在**SQL Server 名稱**方塊中，輸入裝載 BizTalk 管理資料庫伺服器的名稱。  
  
5.  在**資料庫名稱**下拉式清單方塊中，選取**BizTalkMgmtDb**。  
  
6.  按一下 **[確定]**。