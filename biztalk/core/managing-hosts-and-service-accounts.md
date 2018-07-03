---
title: 管理主機和服務帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, managing
- managing [user accounts]
- service accounts, security
- managing [hosts], security
- security, hosts
- managing [Windows groups]
- hosts, security
- security, service accounts
- Windows groups, managing
- user accounts, managing
ms.assetid: 25797571-f1f9-42a4-8fff-5b03076bbe36
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0f33a484d67981bb72908243b82e7835e0390e3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016112"
---
# <a name="managing-hosts-and-service-accounts"></a>管理主控件和服務帳戶
在設定 BizTalk Server 之後，您必須管理 Windows 群組和使用者帳戶。 本節提供有關管理這些 BizTalk Server 帳戶的資訊。  
  
> [!NOTE]
>  如果是多伺服器安裝 BizTalk Server，您必須使用網域全域群組。 如果是單一伺服器安裝 BizTalk Server，您可以使用網域全域群組或本機群組。  
  
 您必須具備 Windows 系統管理員的身分，才能執行下列工作：  
  
- 建立主控件 Windows 群組  
  
- 建立每個主控件執行個體的服務帳戶  
  
- 將服務帳戶新增到主控件 Windows 群組  
  
- 修改與主控件關聯的 Windows 群組  
  
  如需完整清單和群組和 BizTalk server 及其附屬的使用者帳戶的說明，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
  最小安全性使用者權限的系統管理工作的詳細資訊，請參閱[最小安全性使用者權限](../core/minimum-security-user-rights.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何建立服務帳戶的新主控件和主控件執行個體](../core/how-to-create-service-accounts-for-new-hosts-and-host-instances.md)  
  
-   [如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)