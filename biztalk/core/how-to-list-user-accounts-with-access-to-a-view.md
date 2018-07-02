---
title: 如何列出使用者帳戶具有存取權的檢視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user accounts, BAM
- managing [BAM], user accounts
- Get-Accounts utility [BAM]
ms.assetid: 690fb45a-6de0-489e-9ddd-e88e29413c16
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b8e27f1f48846c1eb134c2ee71bf9c00c72d4a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981703"
---
# <a name="how-to-list-user-accounts-with-access-to-a-view"></a>如何列出具有檢視之存取權限的使用者帳戶
系統管理員可以使用**取得帳戶**BAM 管理公用程式命令，以取得某個檢視角色，這表示指定的檢視存取的所有使用者帳戶清單的所有使用者帳戶。  
  
 如需檢視 BAM 檢視的資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。  
  
### <a name="to-list-user-accounts-with-access-to-a-view"></a>列出具有檢視之存取權限的使用者帳戶  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤  
  
3. 型別**bm get 帳戶-檢視：\<檢視表名稱\>**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
4. 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)