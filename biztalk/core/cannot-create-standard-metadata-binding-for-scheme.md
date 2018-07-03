---
title: 無法建立標準中繼資料繫結配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce441c3e-0f6e-46ed-90cf-825dbf89d910
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fd4a91535c7872bb5be7328755808eb91758db6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989311"
---
# <a name="cannot-create-standard-metadata-binding-for-scheme"></a>無法為配置建立標準中繼資料繫結
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| 產品版本 |                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                             |
|    事件識別碼     |                                                         0                                                          |
|  事件來源   |                                                         0                                                          |
|    元件    |                                                         0                                                          |
|  符號名稱  |                                                         0                                                          |
|  訊息文字   | 無法建立標準中繼資料繫結配置 」{0}"。 支援的配置為 http、https、net.pipe 和 net.tcp |
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試從中使用中繼資料的服務不是支援的結構描述。  
  
## <a name="user-action"></a>使用者動作  
 發行具有有效的配置的中繼資料，然後再次執行精靈，對新的中繼資料位置。  
  
 如需其他有關配接器和繫結的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [WCF 配接器](../core/wcf-adapters.md)