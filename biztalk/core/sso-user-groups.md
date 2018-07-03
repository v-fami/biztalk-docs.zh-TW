---
title: SSO 使用者群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- groups, SSO
- user accounts, administrators
- service accounts, SSO
- SSO, user groups
- SSO, service accounts
- SSO, administrator accounts
ms.assetid: e279001e-c724-4a2d-8939-0ba9dd08a19c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cee8780b645cc6f58c0a75526a695e2148893023
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017286"
---
# <a name="sso-user-groups"></a>SSO 使用者群組
若要設定及管理「企業單一登入」(SSO) 系統，您必須為其中每個角色建立 Windows 群組與帳戶。 設定企業 SSO 中的存取帳戶時，您可以為其中每個角色指定多個帳戶。 本節描述這些角色。  
  
> [!IMPORTANT]
>  強烈建議您在設定 SSO 時使用網域群組。  
  
> [!NOTE]
>  基於安全起見，SSO 系統不允許使用內建帳戶。  
  
## <a name="single-sign-on-administrators"></a>單一登入系統管理員  
 SSO 系統管理員擁有 SSO 系統中最高層級的使用者權限。 他們可以：  
  
- 建立及管理 SSO 資料庫  
  
- 建立及管理主要密碼  
  
- 啟用及停用 SSO 系統。  
  
- 建立密碼同步配接器  
  
- 啟用及停用 SSO 系統中的密碼同步  
  
- 啟用及停用主控件初始化的 SSO  
  
- 執行所有管理工作  
  
  SSO 系統管理員帳戶可以是 Windows 群組或個人帳戶。 SSO 系統管理員帳戶也可以是網域或本機群組，或是個人帳戶。 若使用個人帳戶，您無法將此帳戶改為另一個個人帳戶。 因此，建議您不要使用個人帳戶。 只要原始帳戶是新帳戶的成員，您就可以將此帳戶改為群組帳戶。  
  
> [!IMPORTANT]
>  執行「企業單一登入」服務的服務帳戶需為此帳戶的成員。 為保護環境的安全，請確定沒有其他服務正在使用同一個服務帳戶。  
  
## <a name="single-sign-on-affiliate-administrators"></a>單一登入分支機構管理員  
 SSO 分支機構系統管理員定義 SSO 系統所包含的分支機構應用程式。 分支機構應用程式是一種邏輯實體，其代表您使用 SSO 連線的後端系統。 SSO 分支機構系統管理員可以：  
  
- 建立、管理及刪除分支機構應用程式  
  
- 指定每個分支機構應用程式的應用程式系統管理員帳戶  
  
- 執行應用程式系統管理員與應用程式使用者可執行的所有管理工作  
  
  SSO 分支機構應用程式帳戶可以是 Windows 群組或個人帳戶。 SSO 分支機構系統管理員帳戶也可以是網域或本機群組或帳戶。  
  
## <a name="application-administrators"></a>應用程式系統管理員  
 每個分支機構應用程式都有一個應用程式系統管理員群組。  
  
 此群組的成員可以：  
  
-   變更應用程式使用者群組帳戶  
  
-   建立、刪除及管理特定分支機構應用程式所有使用者的認證對應  
  
-   為特定分支機構應用程式使用者群組帳戶中的任何使用者設定認證  
  
-   執行應用程式使用者可執行的所有管理工作  
  
## <a name="application-users"></a>應用程式使用者  
 每個分支機構應用程式都有一個應用程式使用者群組帳戶。 此帳戶包含「企業單一登入」環境中一般使用者的清單。 此帳戶的成員可以：  
  
-   在分支機構應用程式中尋查自己的認證  
  
-   在分支機構應用程式中管理自己的認證對應  
  
> [!NOTE]
>  指派群組時記得保持警戒。 例如，可以在 SSO 應用程式使用者群組中使用 BizTalk Server 安全性使用者群組。 在這麼做之前，請確定是否所有使用者都需要他們即將可用的所有存取權。  
  
## <a name="see-also"></a>另請參閱  
 [如何更新分支機構應用程式屬性](../core/how-to-update-the-properties-of-an-affiliate-application.md)   
 [如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [了解 SSO](../core/understanding-sso.md)