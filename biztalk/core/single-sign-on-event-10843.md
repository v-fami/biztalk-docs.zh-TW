---
title: 單一登入： 事件 10843 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 847e464e-5733-4703-905f-d44a4c4f5cc3
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40b7e03f54d4c4ac2b7074d2aa13d771ce20a9e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012999"
---
# <a name="single-sign-on-event-10843"></a>單一登入： 事件 10843
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                      企業單一登入                                                                      |
| 產品版本 |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    事件識別碼     |                                                                                10843                                                                                |
|  事件來源   |                                                                               ENTSSO                                                                                |
|    元件    |                                                                                 不適用                                                                                 |
|  符號名稱  |                                                                         ENTSSO_E_NO_SECRET2                                                                         |
|  訊息文字   | 無法執行加密或解密，因為無法從主要密碼伺服器可用的祕密。 請參閱事件日誌 (在電腦 ‘%1’ 上) 中的相關錯誤。 |
  
## <a name="explanation"></a>說明  
 存取遭到拒絕。  
  
## <a name="user-action"></a>使用者動作  
 主要密碼伺服器離線，或在主要密碼伺服器缺少必要的主要祕密。 在指定電腦的相關錯誤，請參閱事件記錄檔。