---
title: 單一登入： 事件 10666 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 103947bb-e843-4427-a28a-1cceec90e2ae
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a82308e721f53f9d4eb81fdbdad771b69a1cade5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018268"
---
# <a name="single-sign-on-event-10666"></a>單一登入： 事件 10666
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                         企業單一登入                                                                          |
| 產品版本 |                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                         |
|    事件識別碼     |                                                                                   10666                                                                                    |
|  事件來源   |                                                                                   ENTSSO                                                                                   |
|    元件    |                                                                                    N\A                                                                                     |
|  符號名稱  |                                                                  SSO_INFO_DAMPED_EXTERNAL_PASSWORD_CHANGE                                                                  |
|  訊息文字   | 外部密碼變更已禁止 （偵測到重複的和 discarded).%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶： %3 |

## <a name="explanation"></a>說明  
 這個資訊事件表示外部密碼變更已判定為重複，並捨棄。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [密碼同步](../core/password-synchronization2.md)
