---
title: 單一登入： 事件 10610 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6a400eb-7cf2-49df-befb-caf76e845fdf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c90855c1f136dc8204afe718ea4456c834ab667
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024404"
---
# <a name="single-sign-on-event-10610"></a>單一登入： 事件 10610
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                       企業單一登入                                                       |
| 產品版本 |                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    事件識別碼     |                                                                 10610                                                                 |
|  事件來源   |                                                                ENTSSO                                                                 |
|    元件    |                                                                  不適用                                                                  |
|  符號名稱  |                                                      SSO_WARN_CRED_CACHE_FAILED                                                       |
|  訊息文字   | 認證快取發生未預期的錯誤，並且已關閉。 這可能會影響 performance.%r<br /><br /> 錯誤碼： %1 |
  
## <a name="explanation"></a>說明  
 認證快取發生未預期的錯誤，並且已關閉。 雖然這可能會影響效能，它不會影響功能。  
  
## <a name="user-action"></a>使用者動作  
 重新啟動 SSO 服務時很方便。