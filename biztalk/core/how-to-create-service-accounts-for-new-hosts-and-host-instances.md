---
title: 如何建立服務帳戶新主控件和主控件執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Configuration Manager, service accounts
- Windows groups, service accounts
- Configuration Manager
- service accounts, Windows groups
- hosts, service accounts
- service accounts, hosts
- service accounts, Configuration Manager
- service accounts, creating
- creating, service accounts
ms.assetid: cef97f4a-8db1-41b6-9614-608c2fbf59a9
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d4887d78466340b12b95ed43d27523955ab0689
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969373"
---
# <a name="how-to-create-service-accounts-for-new-hosts-and-host-instances"></a>如何建立新主控件和主控件執行個體的服務帳戶
當您在單一電腦上安裝及設定 BizTalk Server 時，「組態管理員」會設定必要的 Windows 群組和使用者帳戶。  
  
 執行「組態管理員」前，必須先手動建立 Windows 群組和使用者帳戶，並將使用者帳戶新增到網域環境中的 Windows 群組。 如需詳細資訊，請參閱[網域群組](../core/domain-groups.md)。  
  
 您必須執行下列程序，才能建立新的主控件和主控件執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 Administrators 或 Domain Admins 群組成員的身分登入，才能執行此程序。  
  
### <a name="to-create-service-accounts-for-new-hosts-or-host-instances"></a>建立新主控件和主控件執行個體的服務帳戶  
  
1.  為您將建立的新主控件建立主控件 Windows 群組。 如需建立新的主控件的詳細資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。  
  
2.  為您要新增到新主控件的每個主控件執行個體建立服務帳戶。 如需有關如何建立新的主控件執行個體的詳細資訊，請參閱[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。  
  
3.  視需要將服務帳戶新增到主控件 Windows 群組。 如需 Windows 群組，您必須新增服務帳戶資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
4.  在建立主控件和主控件執行個體時，使用 Windows 群組和服務帳戶。  
  
    > [!NOTE]
    >  未指定\<*電腦名稱*\>\ 為使用本機群組的單一電腦安裝中的前置詞。  
  
    > [!NOTE]
    >  如果您使用網域群組，您必須指定\<*網域 NetBIOS 名稱*\>\ 做為主控件 Windows 群組名稱前置詞。 例如 CONTOSO\btssvc。  
  
## <a name="see-also"></a>請參閱  
 [管理主控件和服務帳戶](../core/managing-hosts-and-service-accounts.md)   
 [管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)   
 [如何管理 BizTalk Server 系統管理員群組](../core/how-to-manage-the-biztalk-server-administrators-group.md)   
 [管理 Windows 群組和使用者帳戶的最佳做法](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)