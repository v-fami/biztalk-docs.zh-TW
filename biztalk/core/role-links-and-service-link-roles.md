---
title: 角色連結和服務連結角色 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, orchestrations
- service link roles
- role links
- roles, orchestrations
- roles
- roles, about roles
- service link roles, about service link roles
- orchestrations, roles
- role links, about role links
- orchestrations, deleting
ms.assetid: 23b4ca34-a1a5-44d4-a50d-661277681c72
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6630b1ad22ba86f3efe8a19409f3b731880c8a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268678"
---
# <a name="role-links-and-service-link-roles"></a>角色連結和服務連結角色
A*角色*是使用服務或實作服務的連接埠類型的集合。 角色代表合作對象可擁有一或多個協調流程的互動類型。 當合作對象的數目增加時，角色提供彈性與簡易管理。 例如，協調流程可能使用託運商的角色。 託運商可能有一或多個合作對象與它關聯。 協調流程決定要僱用哪家託運公司運送項目時，它會比較託運商角色中合作對象的價格。  
  
 A*角色連結類型*是確定兩個服務或協調流程之間關係特徵的屬性。 它定義了關係中每個服務所扮演的部分，並指定每個角色提供的連接埠類型。  
  
 合作對象或組織單位代表 BizTalk Server 外部與協調流程互動的實體。 在 BizTalk Server 中，與您交換訊息的每個組織都以合作對象來表示。 藉由在角色中登錄，您可以定義合作對象互動的方式。  
  
 角色連結類型與協調流程關聯時，可以部署或移除該角色連結類型。  
  
## <a name="orchestrations-and-roles"></a>協調流程和角色  
 部署使用角色連結類型的協調流程時，「組態」資料庫會儲存角色。 因為角色可以由一個以上的協調流程使用，所以「管理」資料庫僅會儲存一個角色連結類型複本。  
  
 若您的 BizTalk 專案在名稱及命名空間相同的不同協調流程 (.odx) 檔案中包含兩個角色連結類型，則該 BizTalk 專案不會編譯。  
  
### <a name="orchestration-removals-that-use-roles"></a>移除使用角色的協調流程  
 由於角色連結類型可供多個協調流程使用，因此解除部署包含使用角色之協調流程的組件時，只有在沒有其他協調流程使用角色時，「管理」資料庫才能移除角色。  
  
 此外，若是沒有合作對象在角色中登錄，「管理」資料庫也會移除角色。 就好像您無法覆寫有登錄合作對象的角色，也不能移除有登錄合作對象的角色。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)   
 [成品](../core/artifacts.md)