---
title: 系統管理角色的存取控制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- roles, administrative
- administrator accounts, administrative roles
- administrative roles
- access control, administrative roles
ms.assetid: 328e049b-921d-4057-85f0-7d008ec308bb
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfc7b1891cd266457af97c18f2ad6220145e00ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225814"
---
# <a name="access-control-for-administrative-roles"></a>系統管理角色的存取控制
當使用者在開啟的任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]需要存取資料庫或 Windows 資源的工具，此工具的互動式使用者必須有適當的 SQL Server 和 Windows 使用者權限才能執行的工具支援的各種工作。  
  
 一或多個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工具存取[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 因此，BizTalk Server 必須授與存取每個資料庫中的某個層級[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員。 此外，基於安全性理由，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員不應該有多個使用者執行權限超過必要工作。 使用 SQL Server 資料庫角色，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]即可符合上述兩項需求。 每當您建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]完成安裝的資料庫或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會自動建立該資料庫中的 SQL Server 資料庫角色，這兩個系統管理角色。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]授與每個角色，以及指派給角色，任何 SQL Server 登入上的 SQL Server 物件 （資料表、 檢視、 預存程序等等） 來執行管理工作在該資料庫上的系統管理員所需的最低使用者權限。  
  
> [!NOTE]
>  必須讓 BizTalk 系統管理員擁有更大權限才能執行的管理工作中，有一部分是透過 SQL Server 角色所授與，如建立主控件執行個體。 如需有關這些額外的權限的詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。  
  
 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，有兩個系統管理角色：[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員，而[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]運算子。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員是一個極高權限的角色組態和追蹤資料的存取。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]運算子是低權限角色，只能存取監視和疑難排解動作。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作員 」 群組：  
  
-   是權限較低的系統管理角色，無法存取訊息資料。  
  
-   允許成員監控[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]為錯誤; 查詢擱置 messages\instances，檢視設定。  
  
-   禁止成員變更[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。 例如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]運算子不能變更傳送埠、 接收位置、 連接埠篩選器、 部署新成品。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]建立預設[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員角色，當您第一次安裝產品。 根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]呼叫這個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員，雖然您可以選擇不同的名稱。  
  
 同樣地，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫中建立每個使用者群組的 SQL Server 資料庫角色的每個主機，並授與此角色的最低使用者權限它需要的使用者群組，該主機執行工作。 您必須新增[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]單一登入分支機構系統管理員群組的系統管理員。 如需企業單一登入的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。  
  
> [!CAUTION]
>  BizTalk 系統管理員必須確定自己可以信任即將部署於系統之組件的來源。 如果所部署的組件中包含無法取信於您的程式碼，則可能會讓 BizTalk 環境遭受潛在攻擊的威脅。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會強制執行的動作，當 BizTalk 引擎叫用它們時，可以執行自訂程式碼元件的任何限制。  
  
## <a name="see-also"></a>另請參閱  
 [存取控制和資料安全性](../core/access-control-and-data-security.md)   
 [BizTalk Server 中的 Windows 群組和使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)