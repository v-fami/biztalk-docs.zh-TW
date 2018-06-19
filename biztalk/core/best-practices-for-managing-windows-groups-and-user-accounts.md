---
title: 管理 Windows 群組和使用者帳戶的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, Windows groups
- authenticating, best practices
- Windows groups, security
- best practices, user accounts
- best practices, security
- security, best practices
- user accounts, security
- authenticating, security
- Windows groups, best practices
- best practices, authenticating
- user accounts, best practices
- hosts, security
- hosts, best practices
- best practices, hosts
ms.assetid: 0c4a141e-97ce-434a-8e45-a56c634bbd6c
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f7560e3867bf290f20e0f2f49a740d7298131b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231222"
---
# <a name="best-practices-for-managing-windows-groups-and-user-accounts"></a>管理 Windows 群組和使用者帳戶的最佳作法
本節包含管理 Windows 群組和使用者帳戶安全性的最佳作法和秘訣。  
  
-   **使用服務帳戶與主控件執行個體所需的最小權限**  
  
     為協助保障 BizTalk Server 環境的安全性，建議您使用只具備執行主控件執行個體所需之最小權限的服務帳戶。 如需有關服務帳戶需要的最低權限的詳細資訊，請參閱[存取控制與資料安全性](../core/access-control-and-data-security.md)。  
  
-   **信任的驗證和非信任的主控件使用不同的使用者群組**  
  
     為確保非驗證信任之主控件的權限比驗證信任之主控件的權限小，您必須針對每個主控件使用不同的服務帳戶。  
  
-   **針對每個 BizTalk 主控件使用不同的使用者群組**  
  
     為最大化主控件間的安全範圍，建議您針對 BizTalk 群組中的每個 BizTalk 主控件使用不同的 Windows 使用者群組。  
  
-   **從 BizTalk Server 系統管理員群組中移除安裝使用者**  
  
     當您在具備本機群組的單一電腦上安裝 BizTalk Server 時，會自動將執行 BizTalk Server 互動式安裝的使用者新增到 BizTalk Server 系統管理員群組。 這可讓該使用者以組態管理員來設定 BizTalk Server。  
  
     如果安裝 BizTalk Server 的使用者將不會管理 BizTalk Server，建議您在設定 BizTalk Server 後將這位使用者從 BizTalk Server 系統管理員群組移除。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)