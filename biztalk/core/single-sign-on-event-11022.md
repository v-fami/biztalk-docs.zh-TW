---
title: 單一登入： 事件 11022 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c65ca12b-dda8-408b-9512-39df6f8e035b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c21128bb7804eae88eacc87cffb0fd0d2c0490c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966783"
---
# <a name="single-sign-on-event-11022"></a>單一登入： 事件 11022
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                                                   企業單一登入                                                                                                                                                                                    |
| 產品版本 |                                                                                                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                   |
|    事件識別碼     |                                                                                                                                                                                             11022                                                                                                                                                                                              |
|  事件來源   |                                                                                                                                                                                             ENTSSO                                                                                                                                                                                             |
|    元件    |                                                                                                                                                                                              不適用                                                                                                                                                                                               |
|  符號名稱  |                                                                                                                                                                   SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED                                                                                                                                                                   |
|  訊息文字   | 外部密碼變更可能已造成不同的外部帳戶是 changed.%r<br /><br /> 這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶: %3 %r<br /><br /> 外部帳戶 1: %4 %r<br /><br /> 外部帳戶 2: %5 |
  
## <a name="explanation"></a>說明  
 這是參考用訊息報告可能已造成不同的外部帳戶變更外部密碼變更失敗。  
  
## <a name="user-action"></a>使用者動作  
 雖然 （因為此系統設定為允許對應衝突），未不進行任何變更，您應該確認立即，此嘗試使用您的知識和授權。 如果是的話，則不不需要任何動作。 如果沒有，找出其中變更起始，並確認它已在系統中安全的位置。