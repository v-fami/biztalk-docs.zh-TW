---
title: 單一登入： 事件 10555 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8af9c663-4aa8-4ca5-be63-d4461a2a8517
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a44b3c72659cec8295e7a6625e7b6d94259283c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000303"
---
# <a name="single-sign-on-event-10555"></a>單一登入： 事件 10555
## <a name="details"></a>詳細資料  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10555                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            不適用                             |
|  符號名稱  |          SSO_ERROR_SECRET_CALLBACK_ACCESS_DENIED           |
|  訊息文字   | 祕密伺服器存取 denied.%r<br /><br /> 用戶端使用者： %1 |
  
## <a name="explanation"></a>說明  
 訊息已傳送至伺服器，但回覆遭到封鎖。 原因可能是由數項不同的原因，例如不正確的通訊協定或在伺服器上沒有足夠的安全性權限。  
  
## <a name="user-action"></a>使用者動作  
 請注意錯誤記錄檔中的資訊，請連絡產品支援服務。