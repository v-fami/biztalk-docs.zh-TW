---
title: 單一登入： 事件 10757 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24765a25-560b-4391-9839-a325894c679f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08a75a95a3804ee429baaf24c6b89bbb68a0ce6a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008143"
---
# <a name="single-sign-on-event-10757"></a>單一登入： 事件 10757
## <a name="details"></a>詳細資料  
  
|                 |                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------|
|  產品名稱   |                                  企業單一登入                                   |
| 產品版本 |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                  |
|    事件識別碼     |                                            10757                                             |
|  事件來源   |                                            ENTSSO                                            |
|    元件    |                                             不適用                                              |
|  符號名稱  |                                     ENTSSO_E_NO_MAPPING                                      |
|  訊息文字   | 對應不存在。 針對組態存放區應用程式中，尚未設定組態資訊。 |
  
## <a name="explanation"></a>說明  
 如果這是個人或群組類型應用程式，然後對應不存在。  
  
 如果這是組態存放區應用程式，然後將組態資料尚未設定。 這可能是在 SSO 資料庫已經重新初始化，但 「 BizTalk 管理 」 資料庫具有不是，反之亦然。  
  
## <a name="user-action"></a>使用者動作  
 如果這是個人或群組類型應用程式，建立所需之對應。 如需詳細資訊，請參閱 <<c0> [ 如何建立使用者對應](../core/how-to-create-user-mappings.md)。