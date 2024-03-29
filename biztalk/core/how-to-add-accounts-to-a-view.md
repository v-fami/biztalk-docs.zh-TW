---
title: 如何將帳戶新增至檢視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- Add-Account command [BAM]
- managing [BAM], adding accounts to views
ms.assetid: 0875796c-82a4-4165-9bed-88e8ba466548
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39d1d6b29c7f0b2b7704d6634b49b93a0aede738
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985439"
---
# <a name="how-to-add-accounts-to-a-view"></a>如何新增帳戶至檢視
系統管理員可以使用**新增帳戶**命令來將使用者與 BAM 檢視產生關聯，並保護 BAM Excel 試算表檢視未經授權的存取。 當使用者儲存 BAM 檢視時，檢視會參照隱藏在活頁簿內的 SQL 連接字串。 活頁簿已受到保護，但是您必須確保文件也受到保護。  
  
 當使用者與 BAM 檢視產生關聯時，便只有您授與存取權限的使用者和群組，才能存取檢視。  
  
> [!IMPORTANT]
>  如果您使用的即時彙總 (Rta)，使用者加上**新增帳戶**不會自動授與執行 SQL Server 的電腦登入權限。 如果您使用 RTA，請考慮建立一個 Windows 使用者群組，並在該群組中加入所有需要查看 RTA 檢視的使用者。 然後，將裝載 BAM 主要匯入資料庫之 SQL Server 的 SQL Server 登入權限，明確授與該群組。  
  
 如需檢視 BAM 檢視的資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。  
  
### <a name="to-add-an-account-to-a-view"></a>將帳戶新增至檢視  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。 按 ENTER 鍵。  
  
3. 型別**bm 新增帳戶-AccountName:\<帳戶名稱\>-檢視：\<檢視表名稱\>**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
4. 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)