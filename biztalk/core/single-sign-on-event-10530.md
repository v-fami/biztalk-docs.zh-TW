---
title: 單一登入： 事件 10530 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bb37305-26fe-46a7-958d-3ed7f6876a7b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38eb770f795d23286b2a057a428e3bfec73e1674
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974879"
---
# <a name="single-sign-on-event-10530"></a>單一登入： 事件 10530
## <a name="details"></a>詳細資料  

|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                             企業單一登入                                              |
| 產品版本 |                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    事件識別碼     |                                                       10530                                                        |
|  事件來源   |                                                       ENTSSO                                                       |
|    元件    |                                                        N\A                                                         |
|  符號名稱  |                                            SSO_INFO_GOT_PREVIOUS_SECRET                                            |
|  訊息文字   | 從主要密碼伺服器取得先前的密碼。%r<br /><br /> 祕密伺服器名稱: %1 %r<br /><br /> MSID: %2 |

## <a name="explanation"></a>說明  
 這個資訊事件表示 SSO 具有先前的主要密碼。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  

- [管理主要密碼](../core/managing-the-master-secret.md)
