---
title: "如何啟動 「 商務規則編輯器 」 和載入原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, loading
- opening, Busines Rule Composer
- Business Rule Composer, policies
- Business Rule Composer, opening
ms.assetid: 34a6034d-90b3-4ce0-9770-3790763affe3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 420517c51fd6c7a6c854afe161a11a58f952db83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-the-business-rule-composer-and-load-a-policy"></a>如何啟動 「 商務規則編輯器 」 和載入原則
本節描述如何啟動「商務規則編輯器」和載入原則。  
  
### <a name="to-start-the-business-rule-composer"></a>啟動商務規則編輯器  
  
-   在**啟動**功能表上，指向**所有程式**，指向 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後按一下 **商務規則編輯器 」**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
### <a name="to-load-a-policy"></a>載入原則  
  
1.  在 「 商務規則編輯器 」 中，在**規則存放區**功能表上，按一下 **負載**。  
  
2.  在**規則存放區**對話方塊中，於**SQL Server**下拉式清單中，選取您要連接的 SQL Server™ 電腦。  
  
3.  在**資料庫**下拉式清單中，選取包含您想要開啟規則存放區的資料庫。  
  
> [!NOTE]
>  規則存放區所安裝的預設資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是**BizTalkRuleEngineDb**。  
  
> [!NOTE]
>  如果您使用新建立的 SQL Server 帳戶有**強制執行密碼逾期**和**使用者必須變更密碼，在下次登入時**選項設定商務規則編輯器 」 將無法連接到規則引擎 」 資料庫。