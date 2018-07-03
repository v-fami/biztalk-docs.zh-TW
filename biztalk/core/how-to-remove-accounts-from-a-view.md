---
title: 如何從檢視移除帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- managing [BAM], deleting accounts from views
- Remove-Account command [BAM]
ms.assetid: b74a64a0-ddb3-45d2-add7-6261c31be0f0
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 243c7ee549aea06acb199f718c6eef55e578f91f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995391"
---
# <a name="how-to-remove-accounts-from-a-view"></a>如何從檢視移除帳戶
系統管理員可以使用**移除帳戶**命令來移除 BAM 檢視中的使用者，並保護 BAM Excel 試算表檢視未經授權的存取。  
  
 如需檢視 BAM 檢視的資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。  
  
### <a name="to-remove-an-account-from-a-view"></a>從檢視移除帳戶  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤  
  
3. 型別**bm 移除帳戶-AccountName:\<帳戶名稱\>-檢視：\<檢視表名稱\>**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
4. 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)