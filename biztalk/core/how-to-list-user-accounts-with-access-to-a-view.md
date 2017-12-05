---
title: "如何列出使用者帳戶具有存取權新增至 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, BAM
- managing [BAM], user accounts
- Get-Accounts utility [BAM]
ms.assetid: 690fb45a-6de0-489e-9ddd-e88e29413c16
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80a01aa9b4bd19581cb97f7fee127fc244322d4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-user-accounts-with-access-to-a-view"></a>如何列出具有檢視之存取權限的使用者帳戶
系統管理員使用**get 帳戶**BAM 管理公用程式命令，以取得清單檢視角色，這表示所有使用者帳戶存取特定檢視的所有使用者帳戶。  
  
 如需檢視 BAM 檢視的相關資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。  
  
### <a name="to-list-user-accounts-with-access-to-a-view"></a>列出具有檢視之存取權限的使用者帳戶  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤  
  
3.  型別**bm get 帳戶-檢視：\<檢視名稱\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)