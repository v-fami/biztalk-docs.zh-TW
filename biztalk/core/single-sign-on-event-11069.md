---
title: 單一登入： 事件 11069 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1accfe68-000c-4b5e-909c-244e18eba110
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e9df27e7a5ac5f4fcedb10935fb8e63a6e0bea0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986159"
---
# <a name="single-sign-on-event-11069"></a>單一登入： 事件 11069
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                               企業單一登入                                                                                               |
| 產品版本 |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    事件識別碼     |                                                                                                         11069                                                                                                         |
|  事件來源   |                                                                                                        ENTSSO                                                                                                         |
|    元件    |                                                                                                          不適用                                                                                                          |
|  符號名稱  |                                                                                             SSO_WARN_PS_PCNS_NOT_ALLOWED                                                                                              |
|  訊息文字   | 此 SSO 伺服器目前未設定為允許從 PCNS 進行 Windows 密碼變更。 使用 'ssoconfig-allowPS PCNS yes' 或 SSO 管理 MMC.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者： %2 |
  
## <a name="explanation"></a>說明  
 此 SSO 伺服器目前未設定為允許從 PCNS 進行 Windows 密碼變更。  
  
## <a name="user-action"></a>使用者動作  
 若要允許來自 PCNS 的 Windows 密碼變更，在**伺服器嵌入式管理單元**，**密碼同步屬性**索引標籤上，選取**允許從 PCNS 進行密碼同步。**  
  
 如需詳細資訊，請參閱 <<c0> [ 如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。