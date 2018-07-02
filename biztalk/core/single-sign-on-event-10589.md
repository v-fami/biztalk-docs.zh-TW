---
title: 單一登入： 事件 10589 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fe962bb-e9bb-4107-a5fb-21c180d54e21
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1f8dd6c8a6045f9e4e1678aa06faec8bb783c1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986183"
---
# <a name="single-sign-on-event-10589"></a>單一登入： 事件 10589
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                     企業單一登入                                                                                                                     |
| 產品版本 |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    事件識別碼     |                                                                                                                               10589                                                                                                                               |
|  事件來源   |                                                                                                                              ENTSSO                                                                                                                               |
|    元件    |                                                                                                                                不適用                                                                                                                                |
|  符號名稱  |                                                                                                                 SSO_ERROR_BACKUP_SECRET_REQUIRED                                                                                                                  |
|  訊息文字   | 主要祕密尚未備份。 如果您遺失主要祕密儲存在 SSO 系統中的所有資訊將都會永久遺失，和您的系統可能無法正確運作。 請使用 SSO 管理工具來備份您的主要祕密。 |
  
## <a name="explanation"></a>說明  
 主要祕密尚未備份。 如果您遺失主要祕密儲存在 SSO 系統中的所有資訊將都會永久遺失，和您的系統可能無法正確運作。  
  
## <a name="user-action"></a>使用者動作  
 如需備份主要祕密的資訊，請參閱 <<c0> [ 管理主要密碼](../core/managing-the-master-secret.md)。