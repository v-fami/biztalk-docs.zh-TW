---
title: 單一登入： 事件 11052 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c797ed19-7613-4e0f-8867-9258ec3776a4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4e7779dff83b3abd5b0714445638b46cdd393e4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009727"
---
# <a name="single-sign-on-event-11052"></a>單一登入： 事件 11052
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                                    企業單一登入                                                                                                                                                                     |
| 產品版本 |                                                                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                    |
|    事件識別碼     |                                                                                                                                                                              11052                                                                                                                                                                               |
|  事件來源   |                                                                                                                                                                              ENTSSO                                                                                                                                                                              |
|    元件    |                                                                                                                                                                               不適用                                                                                                                                                                                |
|  符號名稱  |                                                                                                                                                                 SSO_WARN_SSO_AFF_ADMIN_NOT_GROUP                                                                                                                                                                 |
|  訊息文字   | SSO 分支機構系統管理員帳戶包含一或多個個別 （非群組） 帳戶。 如果從 Active Directory 或本機電腦中刪除這些個別的帳戶必須立即移除這些 SSO 系統，或可能會成為安全性 risk.%r<br /><br /> SSO 分支機構系統管理員: %1 %r<br /><br /> 個別帳戶： %2 |
  
## <a name="explanation"></a>說明  
 從 Active Directory 或本機電腦中刪除個別的帳戶不會自動刪除該帳戶從 SSO 系統。 這表示，如果 USER1 已在本機刪除的帳戶，然後以不同的使用者 （比方說，新的員工） 已加入系統，請使用該相同的名稱，SSO 系統會授與新的 USER1 所有原始 USER1 所擁有的安全性權限。 這會造成安全性風險。  
  
 最佳做法，建議您使用 SSO 管理帳戶使用 Active Directory 群組 （不是個別的） 帳戶。  
  
## <a name="user-action"></a>使用者動作  
 從 Active Directory 或本機電腦刪除個別的帳戶之前，不不需要任何動作。 此時，您必須刪除個別的帳戶從 SSO 系統儘速。