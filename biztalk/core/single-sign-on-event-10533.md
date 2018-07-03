---
title: 單一登入： 事件 10533 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31abd828-5f10-43f7-b99e-f3195250130c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2fd77728e459c544a9934e5d27f28a9ea092c67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008879"
---
# <a name="single-sign-on-event-10533"></a>單一登入： 事件 10533
## <a name="details"></a>詳細資料  

|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                             企業單一登入                                             |
| 產品版本 |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    事件識別碼     |                                                       10533                                                       |
|  事件來源   |                                                      ENTSSO                                                       |
|    元件    |                                                        N\A                                                        |
|  符號名稱  |                                            SSO_INFO_GOT_CURRENT_SECRET                                            |
|  訊息文字   | 從主要祕密 server.%r 取得目前的祕密<br /><br /> 祕密伺服器名稱: %1 %r<br /><br /> MSID: %2 |

## <a name="explanation"></a>說明  
 這個資訊事件表示 SSO 具有目前的主要祕密。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  

- [管理主要密碼](../core/managing-the-master-secret.md)
